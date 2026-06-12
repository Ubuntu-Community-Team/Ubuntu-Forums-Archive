---
title: "Compiling packages on other OS (such as Windows)"
date: 2014-08-24
forum: The Cafe
---

### Post by Tristan_Williams on 2014-08-24
The way I understand it, source code is not OS specific. Please correct me if I'm wrong.

With that assumption, couldn't I download the source for any basic Linux program, and compile it under Windows, and have a Windows version of that package?

Say I wanted to have Bash in Windows. Couldn't I just compile Bash with all of its dependencies under Windows?



Yeah I know the answer is no... I just want to know why

---

### Post by mastablasta on 2014-08-25
Once I compiled in windows some source code. I think the issue might be dependencies. in my case I could compile it and create an installer. I forgot what the program was. something small.

anyway if source is open you can modify it to work in windows.

---

### Post by JKyleOKC on 2014-08-25
> **Tristan_Williams said:**
> Yeah I know the answer is no... I just want to know whyIf the source were written in pure assembly language, with absolutely no library or system calls, and if your final CPU chip were the same as that for which the source was written, your premise would work. It would NOT be a Windows program, though, and you might not be able to run it on any Windows machine that included security features.

The real "why" of your question is the simple fact that Linux is not Windows, and essentially all of the system calls are completely different. As a very over-simplified example, a Linux program might call the "read" system function, passing to it on the stack the file descriptor, the address of the buffer into which to place the result, and the maximum size of the buffer. That call would be completely meaningless to Windows, which instead would expect a call to INT 0x21 (its system interface) with the parameters being passed in specific registers, although this call itself might be inside a wrapper named "read" and the parameters might be in a different sequence.

In any event the action of Windows would not be the same as that in Linux.

The whole basis of WINE's design is to create an environment that has the same system-calling conventions used by Windows, to create the same result as Windows, and thus permit Windows programs to be run in a Linux system. Since those conventions vary somewhat from one version of Windows to another, and their use varies quite widely from one program to another, the environment can work quite well for some programs and not at all for others.

Your assumption that source is not OS-specific, unfortunately, is incorrect. Any program that expects input and generates output **MUST** be OS-specific; the main purpose of an OS in the first place is to standardize input and output, but that standardization does not exist at the very highest level! It exists only within each OS family itself. While they are similar and have a common ancestor (MIT's *Project MAC* back in the 60s), Unix, Linux, and BSD are not **totally** compatible with each other, much less with Windows at any version!

---

### Post by HermanAB on 2014-08-29
Yes, you can compile FOSS on Windows and it will run if the program is exceedingly simple.  Anything more than 'hello world' will require a ton of other dependencies.  

Most FOSS tools are indeed cross compiled on Windows by multiple groups such as DJ De Lorie (DJGPP) and Cygwin.  Some googling will find them for you.

---

