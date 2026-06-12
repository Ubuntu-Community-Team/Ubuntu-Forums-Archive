---
title: "Looking for a ebook or guide for administering a web server"
date: 2007-03-04
forum: Server Platforms
---

### Post by mikestefff on 2007-03-04
Hey,

I am developing a site on a VPS. I have a few years of linux experience but I have never ran a public web server before and I know there are tons and tons of things I do not know. I was wondering if anyone of you knew any good ebooks, articles, guides, or anything comprehensive related to administering a linux web server in terms of security, efficiency, maintenance, etc. The site is php/mysql based so information regarding would help also..

Thanks

---

### Post by Mr. C. on 2007-03-04
Hi Mikestefff,

First, did you get those peculiar files resolved ?  If so, what turned out to be the problem?

As a starter book, you can try here:

[http://www.oreilly.com/catalog/bssrvrlnx/](http://www.oreilly.com/catalog/bssrvrlnx/)

I've been working with Unix for a *long* time, and it is my humble opinion that it is first paramount to have a solid understanding of the Unix/Linux system's core layers, security infrastructure, and the system's strengths and weaknesses.  Only then can one appreciate the weaknesses or threats an application may impose upon the system.  For example, one should thoroughly understand issues behind setuid shell scripts, setuid in general, chroot environments, issues with symlinks, etc.

Anway, give the book(s) above a look, and see if that's at all on target.

MrC

---

### Post by mikestefff on 2007-03-04
Hey..gotta thank you for all the help...

First off - the problem with the server ended up being a problem on the host side. The tech said there was an error with my vz template on my node only for my vps. It took a while for them to fix it - then we had to reconfigure and reinstall some of the php modules. It is all back to normal now - thanks again..

I will check out some of those books - they seem really good at first glance.

---

### Post by Mr. C. on 2007-03-04
You're welcome.  Glad you got it all worked out.

Best of Luck,
MrC

---

