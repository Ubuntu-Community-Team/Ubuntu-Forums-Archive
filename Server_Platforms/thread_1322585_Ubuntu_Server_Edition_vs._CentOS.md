---
title: "Ubuntu Server Edition vs. CentOS?"
date: 2009-11-11
forum: Server Platforms
---

### Post by Monarchist on 2009-11-11
Hello.

I've had dedicated servers hosting my websites for years now, though I admit I have no server administration or management experience. My dedicated servers are currently run off of CentOS 64-bit, though I am interested in using Ubuntu Server Edition 64-bit.

I'd like to compare and contrast the two, in terms of performance, ease of use, stability, and security. I know they are both Linux distributions but the two are based off of two different ones: Red Hat & Debian.

One day I would love to learn how to fully administer and manage my server myself. That's one of the reasons I'm leaning towards Ubuntu, because of its documentation and large community support forum. I just don't want to lose performance, security, or stability by switching from CentOS to Ubuntu Server Edition.

Can anyone really compare and contrast the two in a server environment? I've used Ubuntu as a desktop OS before, though I really didn't like it as much as openSUSE. Not only that but Ubuntu didn't support my PC hardware, yet openSUSE did.

Well, hoping to hear from someone soon. I hope someone here has tried both CentOS and Ubuntu Server Edition for their server(s) and can tell me their experience with both of them as well.

---

### Post by scorp123 on 2009-11-11
> **Justice McCay said:**
>  I admit I have no server administration or management experience. ... I am interested in using Ubuntu Server Edition 64-bit.  If you have no experience, then Ubuntu Server might be a bit over your head. For starters there is no GUI. You're supposed to do everything on the command line. Sure, you could install the desktop packages ... But if you do that, why even bother with the server version? In that case you could just as well install the desktop version and install the few server daemons you need on top of it.

> **Justice McCay said:**
>  I'd like to compare and contrast the two There is only one way: Download both and try both for yourself.

> **Justice McCay said:**
>  ease of use CentOS is definitely easier for the beginner.

> **Justice McCay said:**
>  Can anyone really compare and contrast the two in a server environment?  Did you try Google? There are plenty of reviews out there. I'd start with Phoronix ... they regularly compare distros and their features against each other and post reliable benchmark results.

> **Justice McCay said:**
>  I really didn't like it as much as openSUSE. Not only that but Ubuntu didn't support my PC hardware, yet openSUSE did.  Not only that but OpenSUSE also clearly has a lot more polish than Ubuntu. And I am tired of the many bugs and regressions in each release. Stuff that works tip top in the previous Ubuntu release is all of a sudden broken beyond repair in the next. I am tired of this and I am considering going back to OpenSUSE after having used Ubuntu in the past 5 years.

> **Justice McCay said:**
>  has tried both CentOS and Ubuntu Server Edition for their server(s) and can tell me their experience with both of them as well. If you have to use commercial packages then you might have better luck with CentOS. I myself have to use many commercial packages from SUN Microsystems/Oracle and those simply won't work on Ubuntu servers ... And even if you use "alien" and somehow --after lots of hassles and frustration-- manage to get those commercial packages to work on Ubuntu then you usually won't get support for that from your vendor. But such packages usually work tip top on CentOS, thanks to CentOS being 100% compatible with RHEL which most commercial vendors support and release commercial products for.

So if you are considering to use commercial software from vendors such as SUN Microsystems, Oracle, and many others ... CentOS.

If however you have no such plans and doing most things on a command line is no problem for you ..... Ubuntu.

---

### Post by rshol on 2009-11-11
For a home server either will work well, I find Ubuntu to be faster and more responsive but that is entirely subjective.  The comment regarding commercial packages and Centos is right on.  However, there are certain "home server" type packages, like firefly and simplify media that are much easier to run on Ubuntu.

With regard to the GUI, I install server and then add the GUI with

```
sudo aptitude install x-window-system-core gnome-core gdm
```

then a quick ```
/etc/init.d/gdm start 
``` to make it run.  I find this gives me a barebones GUI without a lot of the cruft the desktop iso installs.

---

### Post by Claus7 on 2009-11-11
Hello,

I hope you the best to your system administrating ambitions. 

This link might give you a small insight on the comparison you would like to have:
[http://www.phoronix.com/scan.php?page=article&item=centos_54_comparison&num=1](http://www.phoronix.com/scan.php?page=article&item=centos_54_comparison&num=1)

Regards!

---

