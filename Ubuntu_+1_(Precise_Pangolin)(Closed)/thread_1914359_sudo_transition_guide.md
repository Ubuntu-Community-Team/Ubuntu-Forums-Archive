---
title: "sudo transition guide?"
date: 2012-01-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by nutznboltz on 2012-01-24
We have a customized /etc/sudoers file which works fine on a number of platforms such as Red Hat Enterprise Linux 5 and 6 and Solaris 10.  It also works on Ubuntu 10.04 but when I tried it this morning on 12.04 it fails.

I imagine other people with customized sudoers files will also run into this issue.

Is there a sudo transition guide for converting sudo 1.7.x configuration files into sudo 1.8.x ones?

Thanks.

---

### Post by nutznboltz on 2012-01-24
My problems with sudo are probably related to these Debian bug reports:

Debian bugs:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=640671](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=640671)
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=566351](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=566351)

Ubuntu 12.04 is still using libgcrypt11 1.5.0-3 while in Debian bug 566351 a comment by Daniel Kahn Gillmor says:
> the development head of gnutls (2.99.2) just dropped
libgcrypt support in favor of nettle

This appears to be a serious regression in the form of sudo 1.8.x and ldap not playing well together the way that sudo 1.7.x did.

---

### Post by nutznboltz on 2012-01-24
Back when Ubuntu 9.10 Karmic was released it became necessary to use nscd as a work-around for this issue.  Now on 12.04 using nscd doesn't even help anymore.

See [https://bugs.launchpad.net/bugs/423252](https://bugs.launchpad.net/bugs/423252) for the Ubuntu 9.10 ticket that was never fixed.

---

### Post by nutznboltz on 2012-01-24
> **[Howard Chu (OpenLDAP project lead) in April 2010 wrote](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/423252/comments/73)**

Probably the best fix: don't call global_init when setting the thread callbacks.

```

Index: libgcrypt/trunk/src/global.c
===================================================================
--- libgcrypt/trunk/src/global.c	(revision 1432)
+++ libgcrypt/trunk/src/global.c	(working copy)
@@ -440,8 +440,6 @@
 
     case GCRYCTL_SET_THREAD_CBS:
       err = ath_install (va_arg (arg_ptr, void *), any_init_done);
-      if (! err)
-	global_init ();
       break;
 
     case GCRYCTL_FAST_POLL:

```
I will investigate applying this to 12.04.

---

### Post by dino99 on 2012-01-24
file a bug & join the previous links & comments history

---

### Post by nutznboltz on 2012-01-24
No, LP: #423252 has already been submitted on November 2, 2009 (813 days ago.)

The correct answer is create a branch proposal for 12.04 and I just did that:

[https://code.launchpad.net/~nutznboltz/ubuntu/precise/libgcrypt11/fix-lp423252/+merge/89971](https://code.launchpad.net/~nutznboltz/ubuntu/precise/libgcrypt11/fix-lp423252/+merge/89971)

---

### Post by dino99 on 2012-01-24
> **nutznboltz said:**
> No, LP: #423252 has already been submitted on November 2, 2009 (813 days ago.)

The correct answer is create a branch proposal for 12.04 and I just did that:

[https://code.launchpad.net/~nutznboltz/ubuntu/precise/libgcrypt11/fix-lp423252/+merge/89971](https://code.launchpad.net/~nutznboltz/ubuntu/precise/libgcrypt11/fix-lp423252/+merge/89971)

Very clean job :)

Thanks for doing that.

---

