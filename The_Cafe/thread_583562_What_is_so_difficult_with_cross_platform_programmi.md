---
title: "What is so difficult with cross platform programming?"
date: 2007-10-20
forum: The Cafe
---

### Post by Biochem on 2007-10-20
On one hand there are those big corporation like MS and Adobe with tons of money that can't port their software on Linux et al.

On the other hand there are tons of FOSS software like Open office, pidgin, gaim... that are free and often supported by volunteers. And they run on Windows, Mac and Linux.

What makes it so difficult for the big corporation that charges an eye to buy their product to port their software on new platform whereas community project with no money can?

I'm no programmer and have no intention of becoming one but I find this fact very intriguing.

---

### Post by Xanatos Craven on 2007-10-20
Greed. It tells large corporations that something isn't worth doing if they think they'll make barely any money on it or lose a little from it, despite how much it may benefit everyone (including themselves) in the future.

---

### Post by saulgoode on 2007-10-20
That is the "secret" of Open Source. 

When you compile a program, you can specify what processor, memory configuration, hardware access, --- well ... everything --- and produce a binary which will run on that machine. 

The problem that MS and Adobe have is that they don't want anyone to see their code, so a different version must be created for every different set of circumstances. It would not be much harder for them to make a Linux version (or a Solaris, or a BSD, etc), but then they have to weigh the cost of distributing and maintaining those extra binary versions against the income they might expect. 

With an Open Source system such as GNU/Linux, just one version is necessary; there will be a bunch of "IF" statements which change the outputted binary based upon what the target system is (for example, "IF target=Windows THEN output SYSTEMCALL#7", "IF target=Linux THEN output syscall 4"). Only the system-dependent code needs to be handled this way, the vast majority of a program is identical regardless of the target. 

It is also difficult for closed, proprietary vendors to write for GNU/Linux because Open Source systems change more rapidly than proprietary ones. 

For example, when USB 2.0 came out with additional functionality over of USB 1.1, Linux modified its drivers to handle the new functions. Any source code which used the previous driver was recompiled to call the newly written driver. At the source code level this could be done without the original program being rewritten. However, binaries which called the old driver would not work with the new one unless they were recompiled. This means that a proprietary company would be required to release a new version of their program to run on Linux.

Windows, on the other hand, keeps the old driver around and adds another driver which is basically the same but includes any new functionality. This allows older programs to continue working even without being recompiled (I have heard that Windows XP's kernel has four different USB drivers -- each time USB is enhanced, a new driver has been added).

Hopefully it can be seen, despite my terrible description, that from a programming standpoint Linux is not "friendly" with proprietary software. It is not trying to be "unfriendly", it is just that Linux is not worried about maintaining support for outdated binary programs*. To do so would require that Linux become the same bloated, crippled dinosaur which Windows has become.


* Note: at the source code level, Linux is great at support for old programs: I am currently running [a five-year old desktop environment]("http://udeproject.sourceforge.net/") which compiles with no problems on the latest Linux.

---

### Post by koenn on 2007-10-20
> **saulgoode said:**
> 
With an Open Source system such as GNU/Linux, just one version is necessary; there will be a bunch of "IF" statements which change the outputted binary based upon what the target system is (for example, "IF target=Windows THEN output SYSTEMCALL#7", "IF target=Linux THEN output syscall 4"). Only the system-dependent code needs to be handled this way, the vast majority of a program is identical regardless of the target. 
lots of languages / development environments hide system calls behind an API, an application programming interface. It gives the programmer easy (easier) access to OS functions (access to the file system, network connections, ....) but make porting to other operating systems harder. You can not simply recompile (not even with conditional statements) a program that hinges on Windows  "Filesystem Objects" or Windows-specific extensions in, say, a winsock.dll. 
Apparently, this way of programming is more common in a Windows environment, so it's not always easy to port Windows applications to other systems. 
If, on the other hand, you write code with portability in mind, creating the same application for different platforms (eg the way Mozilla and OpenOffice.org do) is a lot easier.

---

### Post by popch on 2007-10-20
> **Biochem said:**
> On one hand there are those big corporation like MS and Adobe with tons of money that can't port their software on Linux et al.

I don't think that they can not port their software. In the case of MS, it is quite clear that they do not want to do so. Actually, they did port their office suite to the Mac platform.

Adobe just might be to cheap to incur the added cost of writing their applications in a way which made porting to other platforms attractive.

> **Biochem said:**
> On the other hand there are tons of FOSS software like Open office, pidgin, gaim... that are free and often supported by volunteers. And they run on Windows, Mac and Linux.

They do that, indeed. However, the people who write those programs are employed to do just that. It is not true that Open Office is written by housewives and hobbyists after hours when the children are in bed.

---

### Post by samjh on 2007-10-20
It's largely cost, followed by the need to support legacy code and environments.

MS and Adobe don't produce Linux software because they can't.  They just don't want to, because the market is too limited.

Linux did not, and still does not, have a significant presence on the desktop.  If you narrow that down to desktops that run ONLY LInux, then the numbers get even smaller.  Unless the market for Linux-only software is big enough to generate a profit, it's not really worth the effort.

Unless software companies write software with cross-platform portability as a design goal, the work involved in porting software from Windows to Linux is not trivial.  Most companies have written their software to work only on Windows, and depend on Windows-specific libraries, especially Win32, MFC, and now the .NET frameworks.  Once you commit to those libraries, it's difficult to escape them, because the software needs to be rewritten almost entirely.  The time and money spent on that effort means damaged reputation, lost sales, and lost features against competing products.

> It is also difficult for closed, proprietary vendors to write for GNU/Linux because Open Source systems change more rapidly than proprietary ones.This is true for small and medium-sized projects, but not for larger or technically demanding projects.

Games are the most obvious example of the sheer speed of development in proprietary software projects.  No modern FOSS game has ever been developed faster with matching quality as commercial AAA games.  The effort is there (see Nexius, Sauberbraten, Battle for Wesnoth, etc.), but it just doesn't happen.  We've yet to see a FOSS equivalent of Warcraft III or Half Life 2 with comparable development times.

---

### Post by p_quarles on 2007-10-20
FYI, Adobe is in fact moving to cross-platform development. Not in the way that everyone might like, but it is in the cards:
[Link]("http://today.reuters.com/news/articlenews.aspx?type=technologyNews&storyid=2007-10-18T130541Z_01_N17292526_RTRUKOC_0_US-ADOBE-SERVICES.xml") [Reuters]

---

### Post by Frak on 2007-10-20
It can be difficult to cope with a different API, but once you spend 5 minutes slaving to understand it, you can have worry of someone figuring out how to reverse engineer it.

Because if it can run natively on your system, you can reverse engineer it. If it can run on EVERY system, a monkey can reverse engineer it.

---

