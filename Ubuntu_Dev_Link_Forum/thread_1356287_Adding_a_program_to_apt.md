---
title: "Adding a program to apt?"
date: 2009-12-15
forum: Ubuntu Dev Link Forum
---

### Post by AlphaWhelp on 2009-12-15
Greetings!  I have a program of mine that I was considering entering into the apt repository and I have a few questions.

1. Do I require a free software license?  Is my program required to be open source?
2. The program itself is written in Java so it doesn't need any installing per se, but rather, does GNU/Linux come with Sun's JRE pre-installed or not?  If not, is the command line needed to execute a class file the same as Sun's JRE?  Or does everyone have to go out of their way to install the JRE from Sun to run anything Java at all? (I don't really know this since as a Java programmer, installing Java from Sun is almost the first thing I do on any system.)
3. Does the apt require the program to be in a jar file or can it be run in its class files?
4. How would I even go about creating the proper protocol to "install" the program when using apt-get?

Any other information I might need to know but didn't think to ask would be appreciated as well.

---

### Post by Ben Wright on 2009-12-28
If your application is Free/open source software it means it can be placed in the universe repository if your application is not I believe you must either use a third party repository or you can use multiverse (in special cases). In terms of the dependencies apt resolves dependencies but in order to do so you have to package your program into a .deb file format. You can find more information about packaging at: [https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide) . Thanks.

---

