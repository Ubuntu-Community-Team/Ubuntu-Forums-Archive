---
title: "Historical bypasses"
date: 2012-05-06
forum: Security
---

### Post by Hungry Man on 2012-05-06
Anyone have info on past exploits that got through an apparmor/selinux/MAC profile?

---

### Post by unspawn on 2012-05-06
One word for you to look up: *spender*.

---

### Post by rookcifer on 2012-05-06
> **unspawn said:**
> One word for you to look up: *spender*.

Yeah Brad Spengler (spender) has found a few here and there (you can Google his name and find articles). He is one of the main guys behind grsecurity (a competing MAC system).  People like Tavis Ormandy (who works for Google) also specializes in finding exploits like these.  Both Spengler and Ormandy have been "controversial" because they like to publicly release the exploits before they contact the kernel devs (I personally have no issue with this, as it is often the only way to get people to listen).  

Ormandy himself has brought the ire of Microsoft because he loves to attack their products and release the exploits before they fix it (no doubt they are mostly angry because he works for Google).  Again, sometimes these massive vendors like M$ move slow as molasses, so sometimes it is best to go ahead and publish it. 

As for SELinux, you have to remember that it runs at the kernel level (Ring 0).  If someone finds a way to exploit the kernel (and a SELinux policy is not in place for that specific access point), they can simply get root and disable SELinux.  This is a gross oversimplification, but that's the gist of it.  Unless you have a MAC system somehow running at Ring -1 (hardware level) it will always be possible to crack the software.  However, a properly implemented MAC should make it much more difficult.

As far as I know all of these exploits work because there wasn't a proper SELinux policy in place, but there may be exceptions where SELinux wouldn't have made a difference at all.  You would have to ask an expert about that.

---

### Post by Hungry Man on 2012-05-06
Thanks, I'll give those names a look and see what I can find.

---

