---
title: "what is mac OSX based off of?"
date: 2007-06-03
forum: The Cafe
---

### Post by Redlance on 2007-06-03
reason I am asking is 2 reasons.
1) isnt BSD alot like debian in most respects (though not all)
2) could this [URL="http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9022742&source=NLT_PM&nlid=8"[/URL]
be ported to linux?
or am i just clueless as to macs?

---

### Post by BoyOfDestiny on 2007-06-03
> **Redlance said:**
> reason I am asking is 2 reasons.
1) isnt BSD alot like debian in most respects (though not all)
2) could this [URL="http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9022742&source=NLT_PM&nlid=8"[/URL]
be ported to linux?
or am i just clueless as to macs?

I think this post explains it best
> 
A *huge* part of Mac OS X essential core software is used by Apple from freeloading (legally, since the respective licenses do grant this) from Free and Open Source Software stack:

* their Kernel: it is taken from BSD.

* their Compiler: it is GCC (GNU Compiler Collection).

* their User Authentication: it is taken from MIT Kerberos/krb5.

* their Encryption; it is taken from OpenSSH.

* their Directory Service: it is taken from OpenLDAP.

* their Print Spool Server: it is taken from CUPS.

* their non-PS Printer Drivers: they are taken from Gimp-Print/Gutenprint.

* their Windows Interoperability: it is taken from Samba.

* their Web Server: it is taken from Apache.

* their Web Browser Safari and WebCore: it is built around KHTML and KJS, taken from KDE.

* and further, they are happy to take advantage of X11, of OpenOffice, of Mozilla and lots of other Open Source Software if it fits them. They do use many thousand of man-years worth of Free Software for free in their OS.


[http://www.digg.com/linux_unix/Apple_dis_invites_Samba_talk_by_Jeremy_Allison_talk_fearing_SUSE_3D_desktop#c6735250](http://www.digg.com/linux_unix/Apple_dis_invites_Samba_talk_by_Jeremy_Allison_talk_fearing_SUSE_3D_desktop#c6735250)

Here is a link with more specifics from Apple (googled for it)

[http://images.apple.com/macosx/pdf/MacOSX_UNIX_TB.pdf](http://images.apple.com/macosx/pdf/MacOSX_UNIX_TB.pdf)

Anyway, as such, unless some of it's closed components are cloned, or they release the code, I wouldn't expect a port...

---

### Post by 3rdalbum on 2007-06-03
BSD is like Linux in a way, so there are BSD distributions. Debian is a distribution.

Mac OS X is based off NeXtStep, which does contain some code from FreeBSD and apparantly from NetBSD too. It is NOT a BSD kernel though, and is not licensed under the BSD license.

The virtualiser that you're talking about is made by a 3rd-party company. It is proprietry software. They did used to make their virtualiser for Linux, but I think they're focusing on OS X now. The interesting part of their virtualiser that allows that particular feature to work is dependent on OS X's kernel and the Finder, both of which are not free-as-in-speech.

---

### Post by hardyn on 2007-06-03
there are parts of Mach's micro kernel and pseudo realtime in there too.

---

### Post by Redlance on 2007-06-03
ah well poo..
I was hoping another entrant to windows porting 3d stuff to linux was in the works.
wine needs some more help/support. as it is i am stuck with windows for everquest 2.
Just wish windows wasnt so difficult to tweak and the wga makes me feel like the gestapo is always checking my papers evertime i wanna do an update :(
But i have Ubuntu on a partition for when im doing other things. And it really is nicer than windows for me in many ways that i just can't express enough in simple words. (pride in the amount of customizing *I* did plus other peoples tweaks) but im rambling again :)

---

### Post by bonzodog on 2007-06-03
Underneath the Aqua windowing system that OSX runs on is something called Darwin Unix.

The Darwin kernel is a BSD kernel but heavily tweaked. It is known fact that many apps that compile on fBSD will also run on Darwin, and thus OSX. The thing with the GUI progs is that they have been written for Aqua/OSX, and are written in cocoa/Obj C, and thus are not easy to port to linux unless you install all the Linux Obj C libs.

---

