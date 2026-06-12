---
title: "What OS to use with i686 server?"
date: 2009-09-11
forum: Server Platforms
---

### Post by CFulcrum on 2009-09-11
My server cpu is an i686.  Is there a Linux server OS that I can use on it?  It didn't like the 64bit version of Ubuntu server, but I don't think the 32bit will work either...

Suggestions?

---

### Post by Udayakiran on 2009-09-12
> **CFulcrum said:**
> My server cpu is an i686.  Is there a Linux server OS that I can use on it?  It didn't like the 64bit version of Ubuntu server, but I don't think the 32bit will work either...

Suggestions?

i686 is something like an upgrade to i386 and hence belong to the x86 (32 bit) processor family. i686 has a few extra instructions than i386, but it is backwards compatible.

So, the 32 bit version of Ubuntu should run fine on your server. But it will run slow compared to an OS optimized for i686. Ubuntu does not have i686-optimized build. I know that Arch Linux and Gentoo have i686 builds. And with a bit of work, you should be able to turn them into server oriented systems. I think Red Hat linux has i686-optimized build too, but it may be commercial.

BTW, i'm just an amateur user of linux and u might need the opinion of an expert.

---

### Post by Wim Sturkenboom on 2009-09-12
> **CFulcrum said:**
> My server cpu is an i686.  Is there a Linux server OS that I can use on it?  It didn't like the 64bit version of Ubuntu server, but I don't think the 32bit will work either...

Suggestions?

i686 is not a 64-bit architecture. So get the 32 bit version of any distro and it will work.

---

### Post by ugm6hr on 2009-09-12
> **CFulcrum said:**
> but I don't think the 32bit will work either...


It will work.  Unless there is a non-CPU related hardware conflict.

---

