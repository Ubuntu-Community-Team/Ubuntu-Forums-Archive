---
title: "Question about burning open source and free software."
date: 2009-07-10
forum: The Cafe
---

### Post by LinuxFox on 2009-07-10
I understand the GPL allows copying, so I'm thinking about burning a copy of a open source game I like to a CD for myself.  I'm thinking about burning the Linux version, the Windows version, and the source code to one CD.  My question is about the source code.  If I was to ever use another operating system like MacOS X or Free BSD, would I be able to compile the source code so I can play it?

I have no intention of leaving Linux or Windows, but I'd like to know if I ever use a new computer or OS.  Please answer and thanks.

---

### Post by JDShu on 2009-07-10
My limited programming knowledge tells me that it depends on what libraries are needed for the game. Other operating systems might not have the things you need to compile so you probably would need to check that.

---

### Post by lswest on 2009-07-10
The source code will compile as long as:

a) the compiler is present
b) the libraries are present
c) the directories/filepaths within the program aren't hard-coded, and are flexible for other systems (Mac OS X, etc.)

It will compile if the above points are covered, but it may not necessarily run, since there are some things that may have been taken into account for Windows and Linux, but are lacking in Mac (for example that user folders are under /Users/ and not /home/ or C:\Documents and Settings\, though, to be fair, that is in point c)).

I think those are the most important factors, there may be a few others I missed out though.

---

### Post by LinuxFox on 2009-07-10
Thanks, one more question.  If I placed the binary versions on the CD, would it load up on the correct OS?

For example if I place an open source program's binary for MacOS on a CD, would a Mac read it without problems?

---

### Post by BoyOfDestiny on 2009-07-10
It also depends how portable the code itself is. Will it work on big endian as well as little? etc. 
In some cases it may require a small change, or no change at all. 

Anyway, as it is open source, there will likely be ports to all sorts of architectures and platforms (look at VLC or scummvm for example), so you shouldn't have to worry too much. Not to mention Ubuntu has a sparc and arm port (that includes 99% of packages too!)

---

### Post by lswest on 2009-07-10
> **LinuxFox said:**
> Thanks, one more question.  If I placed the binary versions on the CD, would it load up on the correct OS?

For example if I place an open source program's binary for MacOS on a CD, would a Mac read it without problems?

It may not auto-execute (depends what the autorun for the CD is like), but if you execute the right file manually, it should launch correctly (unless libraries are missing from the CD, but I doubt that would be the case), as long as it's a binary (the source code would, of course, needs to be compiled before using).

---

### Post by LinuxFox on 2009-07-10
> **lswest said:**
> It may not auto-execute (depends what the autorun for the CD is like), but if you execute the right file manually, it should launch correctly (unless libraries are missing from the CD, but I doubt that would be the case), as long as it's a binary (the source code would, of course, needs to be compiled before using).In that case, it's perfectly fine.  I do prefer manual for running some things anyway.  Thanks again.

---

### Post by lisati on 2009-07-10
> **lswest said:**
> It may not auto-execute (depends what the autorun for the CD is like), but if you execute the right file manually, it should launch correctly (unless libraries are missing from the CD, but I doubt that would be the case), as long as it's a binary (the source code would, of course, needs to be compiled before using).

I concur: one piece of software I checked out a year or two back made a basic set of "autorun" files for a CD. Trouble was, it caused the autorun feature to try to load up a Windows EXE file, which would be useless on most *nix installations, and which would be unnecessary if all you wanted to do was to display a HTML file.

---

