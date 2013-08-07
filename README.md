SAMWeak
=======

Obj-C macro for easy creating weak references.

No more retain cycles within blocks.

# Usage

There is only two macros, that creates another weak reference or strong reference.

- `WEAK(__self)`
- `STRONG(__self)`


```objective-c
WEAK(self);
void (^ block)() = ^{
	// now you can use _self variable as weak reference
};
```

```objective-c
WEAK(self);
void (^ block)() = ^{
	STRONG(_self);
 	// now you can use s_self variable as strong reference that is created from weak reference
};
```

# Example

## Simple weak reference:

```objective-c
WEAK(self);
[UIView animateWithDuration:0.25 animations:^{
		_self.frame = CGRectMake(0.0f, 0.0f, 10.0f, 10.0f);
}];
```

## Complex weak and strong referencing:

```objective-c
WEAK(self);
[UIView animateWithDuration:0.25 animations:^{
		STRONG(_self);
		s_self->variable = 0;
}];
```


# CocoaPods is of course supported.
	
	pod 'SAMWeak'
	


# License

The MIT License (MIT)

Copyright (c) 2013 Roman Kříž

Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of
the Software, and to permit persons to whom the Software is furnished to do so,
subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS
FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR
COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER
IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN
CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.


