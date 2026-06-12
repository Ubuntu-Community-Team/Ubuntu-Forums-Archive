---
title: "Ubuntu sucks as a development platorm"
date: 2007-11-21
forum: Testimonials &amp; Experiences
---

### Post by 999alfred on 2007-11-21
I just installed Ubuntu 7.1 and I have discovered that Ubuntu does not want people to do anything or install anything unless the Ubuntu gods have released the package,

The biggest problem is that the Ubuntu staff left out a lot of .pc files from /usr/lib/pkgconfig directory. Like libz and libpng12. So, when you run configure scripts, which rely heavily on these files to check version numbers of dependencies the ./configure fails even tho you have the dependencies.

Plus even after atp-get install build-essentials  I try 
cc -lpng12 -lm test.c

The linker says no libpng or libm, and they both exist in /usr/lib and in the ld cache.
This worked correctly on Feisty 7.04

And don't even get me started on spending the time to find out how to disable ipv6 when I wanted a static ip for this machine. Who uses ipv6 anyway?

Hell, the reason I upgraded at all to 7.1 is because 7.04 broke my scanner.
The only good thing about Ubuntu 7.1 is my scanner works again.

So, I guess Ubuntu greedo for new releases is, "Lets fix this, but break this"

IMHO 7.1 has seriously  tarnished Ubuntu's reputation.

I guess its back to Slackware.

999alfred

---

### Post by elctb on 2007-11-21
I know what you're talking about. I've been there myself. Ubuntu has most if not all the packages you need to compile anything. However, it seems by default only the run time version of the packages are installed. To compile much anything you need the development version. This is what I do to find out which package I need:

. Find the package that contains the file you need:
  . sudo apt-file update
  . apt-file search <filename>
    <filename> is the file that can't be found when compiling.
. Install the package

Post the error you get when compiling "cc -lpng12 -lm test.c". Someone might be able to help.

---

### Post by jespdj on 2007-11-21
First of all, it is version 7.**10**, not 7.1. The "7" is for 2007, and the "10" for October.

I see that you're frustrated. Ubuntu does not suck at all for development - you just don't know what you need to do.

When you want to develop programs using libraries such as libpng12, then you not only need to install the binaries of the library itself, but also the development package for that library. So for libpng12 you need to install the package libpng12-dev:
```
sudo apt-get install libpng12-dev
```
It makes perfect sense that headers etc. for a library are not installed by default, since most users won't need them. In Ubuntu 7.04 this worked in the same way as in 7.10.

---

### Post by 999alfred on 2007-11-21
And what about the cc command NOT finding the libraries???

999alfred

---

### Post by Arthur Archnix on 2007-11-21
This might be better suited to the testimonials tab. You might want to try Debian as well, perhaps before going back to slack. Ubuntu seems to change a lot of things in an effort to make linux easier for the new user. Customization is possible, but perhaps not as easy "out of the box" as other distros. I suspect this was a decision made on the part of the Ubuntu development team, and not some failure of thinking or massive mistake, as your original post seems to suggest.

---

### Post by Pumalite on 2007-11-21
Ubuntu offers a choice. If you think Feisty works better, stick to it. It beats me that people happy with an OS feels compelled to upgrade.

---

### Post by elctb on 2007-11-21
> **999alfred said:**
> And what about the cc command NOT finding the libraries???

999alfred

Can you try specifying the path to the library to the cc command "-L<lib-path>" and post the exact error you get ?

---

### Post by kellemes on 2007-11-21
> **Pumalite said:**
> Ubuntu offers a choice. If you think Feisty works better, stick to it. It beats me that people happy with an OS feels compelled to upgrade.

+1

By the way, since you're going "back to Slackware".. isn't the lesson learned you're not the *buntu kind of user? I mean.. *buntu is not the most transparent distro out there..

---

### Post by 999alfred on 2007-11-21
I could be happier if I could just get the cc/ld command to find the libraries. I've never seen this problem in 12 years of using Linux.
Like I said 7.04 worked correctly, but not 7.10 and like I said I only upgraded because 7.04 broke my scanner. Sounds like a Catch-22.

999alfred

---

### Post by elctb on 2007-11-21
I wrote a quick test program that links with the math library. Could you try it and let me know what you get ? Also, Can you post your test.c file so I can try it too ?

This is what I get when I compile/run it:

~/tmp$ gcc -o test -lm test.c 
~/tmp$ ./test 
This is the cosine=1.000000
This is the sine=0.000000

```
#include <math.h>
#include <stdio.h>

main()
{
	printf("This is the cosine=%f\n", cos(0.0));
	printf("This is the sine=%f\n", sin(0.0));
}

```

---

