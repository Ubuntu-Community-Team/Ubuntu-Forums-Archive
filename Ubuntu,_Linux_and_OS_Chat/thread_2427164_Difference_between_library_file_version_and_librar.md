---
title: "Difference between library file version and library version?"
date: 2019-09-18
forum: Ubuntu, Linux and OS Chat
---

### Post by jwdonal on 2019-09-18
Hopefully this is not the dumbest question ever asked on this board. :/  I have been using linux for ages but I don't know the answer to this question and Google was not being helpful (possibly because I'm not using the proper terminology).

I'm running 18.04 LTS. I was dealing with a library dependency issue for a program and came up with the following question.

What is the difference between the library version number appended to the .so files and the version of the library itself? Why do they not match?

For one example, I have libfreetype6 library installed. The .so file is:

/usr/lib/x86_64-linux-gnu/libfreetype.so.6.15.0

So the version is 6.15.0......but it's really not. Because the actual version of libfreetype that was installed is actually 2.8.1 which came from package libfreetype6_2.8.1-2ubuntu2_amd64.deb.

There is no libfreetype version 6.15.0 on the freetype.org website. The latest on the website is 2.10.1.

So will someone please tell me why there are two different version numbers for the same library?

Why wouldn't the .so file just be named libfreetype.so.2.8.1??? That would make much more sense to me.

And this is not specific to the freetype library either, it seems to be prevalent across many (all?) libraries.

I really hope this isn't a super dumb question...

---

### Post by #&amp;thj^% on 2019-09-18
There is no Dumb questions, just sometimes the reply is a bit long in the tooth.
As I understand it, Binaries themselves know which version of a shared library they depend on, and request it specifically.
Example:
```

    example.so.1
    example.so.2

```
the idea is to have two distinct files such that two versions of a library can exist on a system (as opposed to "DLL Hell" on Windows).
The numbers in the shared libraries are convention used in Linux to identify the API of a library. Typically the format is:
```

libFOO.so.MAJOR.MINOR
```

And as you noticed usually there is a symbolic link from libFOO.so to libFOO.so.MAJOR.MINOR. ldconfig is responsible for updating this link to the newest version.
A more extensive discussion (A bit old but still relevant) can be found here: [https://www.ibm.com/developerworks/linux/library/l-shlibs/index.html](https://www.ibm.com/developerworks/linux/library/l-shlibs/index.html)

config maintains a table of what shared libraries are available on a system and where the path to that library exists. You can verify this by running:
```

ldconfig -p
```

---

### Post by jwdonal on 2019-09-18
> **1fallen said:**
> the idea is to have two distinct files such that two versions of a library can exist on a system. OK, fair enough, but then why not just have the following:

libfreetype.so
libfreetype.so.2.8.1
libfreetype.so.2.7.1
libfreetype.so.2.6.1

And with libfreetype.so symlinked to either 2.8.1 or 2.7.1 or 2.6.1 (whichever is needed).

The thing I still don't understand is where the 6.15.0 major/minor numbers come from. Does it signify which gcc version the library was compiled with or something? How does 6.15.0 relate (if at all) to the actual library version of 2.8.1?

Or maybe the people that package these libraries for Ubuntu just pick their own arbitrary version numbers for libraries and disregard the actual version numbers? But why do that? Seems silly...

My question is less about why the .so files have version numbers at all, but more about why the .so file version number doesn't match the actually library version. Maybe I'm just not making any sense...lol.

---

### Post by #&amp;thj^% on 2019-09-18
I'm not in charge of major/minor numbers and where they come from. (Devs only) Just an ordinary user much like yourself.
But here might help to see why:
```
libADM_audioParser6.so (libc6,x86-64) => /usr/lib/libADM_audioParser6.so
	libADM_UI_Cli6.so (libc6,x86-64) => /usr/lib/libADM_UI_Cli6.so
	libADM_UIQT56.so (libc6,x86-64) => /usr/lib/libADM_UIQT56.so
	ld-linux-x86-64.so.2 (libc6,x86-64) => /usr/lib/ld-linux-x86-64.so.2


```
This is a real reply from the terminal on my system.
Forgot to add:
```
ldconfig -p
**_3133 libs found in cache `/etc/ld.so.cache'_**

```

---

### Post by jwdonal on 2019-09-18
For those who are interested I finally got the answer I was looking for here:
[https://forums.gentoo.org/viewtopic-p-8371530.html](https://forums.gentoo.org/viewtopic-p-8371530.html)

TL;DR:
There is ABI (binary compatbility is 6.15.0) and API (source code compatibility is 2.8.1)

---

### Post by #&amp;thj^% on 2019-09-19
Glad to hear. ;)
Did I not not say that? "_Binaries themselves know which version of a shared library they depend on, and request it specifically._"
All is good. :)

---

