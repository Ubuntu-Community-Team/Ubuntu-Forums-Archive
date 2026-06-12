---
title: "Add to the 'megathread'?:  USB hack for VirtualBox OSE"
date: 2009-04-21
forum: Virtualisation
---

### Post by andrew.46 on 2009-04-21
Hi,

Can a suggest a small addition to the Virtualization 'mega-thread'? I am running VirtualBox OSE which of course does not offer USB support as stated in this guide. However there is a small trick I came across a while back that I use to access my USB drive which is to place a symbolic link to that drive in the 'shared' folder. This enables access to the USB drive from *within* the guest system even when using the OSE version.

Is this worth a footnote in the USB section of the mega-thread? Not suitable for syncing software etc but perfect for usb sticks, drives etc and you get the moral high ground of using the Open Source version :-).

Andrew

---

### Post by bodhi.zazen on 2009-04-21
PM me the "hack" and I will add it ;)

---

### Post by bunty on 2010-11-23
Is a more explicit description of exactly what the "symlink" needs to be?

This sounds like **very useful information ** . If it got added , a link?

TIA.

---

### Post by bodhi.zazen on 2010-11-23
> **bunty said:**
> Is a more explicit description of exactly what the "symlink" needs to be?

This sounds like **very useful information ** . If it got added , a link?

TIA.

This is a very old thread and your question is a bit off topic.

I will answer, but in the future, I suggest you start a new thread.

A "symlink" is a link, and you can make one from teh command line or graphically (with nautilus).

```
ln -s /foo /bar
```

See man ln fo rdetails

See also:

[http://www.cyberciti.biz/faq/creating-soft-link-or-symbolic-link/](http://www.cyberciti.biz/faq/creating-soft-link-or-symbolic-link/)

[http://lowfatlinux.com/linux-link-files-ln.html](http://lowfatlinux.com/linux-link-files-ln.html)

---

