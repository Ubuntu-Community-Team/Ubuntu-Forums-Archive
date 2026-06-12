---
title: "Ubuntu let me down 3x"
date: 2010-05-31
forum: Testimonials &amp; Experiences
---

### Post by bluec10 on 2010-05-31
Don't get me wrong, I really like Linux and particularly Ubuntu.  I use it more and more and my kids are getting into it too.

But - I've gone through 3 Ubuntu upgrades and EACH time I'm left unable to boot into Windows Vista.  I've tried to fix the problem and haven't had any luck so I've had to reinstall Windows 2x.  I've just upgraded to the latest Ubuntu and, once again, Vista won't load.

Some of you will say "Good, who needs Windows anyway?", but I do need Windows for a bunch of things, as do other members of my family.  Why does this happen every time and why is it so difficult to get answers about how to fix it simply?

:mad:

---

### Post by bcbc on 2010-05-31
Did you perhaps install grub to the windows bootsector? The fix is easy using testdisk [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If it's not that problem, just post the bootinfoscript results back here and someone will help.

EDIT: I see this is your 'testimonial thread' and you have a request for help thread somewhere else, so please ignore the above. If you just want to vent, then I hear you. This has been a very frustrating upgrade for a lot of users who've made the same mistake as you, and I'm sure I would have made it too if it wasn't for the work I'd done before getting to understand grub2.

---

### Post by Shazzam6999 on 2010-05-31
Eh, I pretty much screw it up every time I try and dual boot. I do a little better when I manually partition, but I completely feel you.

---

### Post by WinterRain on 2010-05-31
> **bluec10 said:**
> Why does this happen every time and why is it so difficult to get answers about how to fix it simply?

:mad:

Do clean installs.

---

### Post by za.zen on 2010-06-01
> **bluec10 said:**
> Don't get me wrong, I really like Linux and particularly Ubuntu.  I use it more and more and my kids are getting into it too.

But - I've gone through 3 Ubuntu upgrades and EACH time I'm left unable to boot into Windows Vista.  I've tried to fix the problem and haven't had any luck so I've had to reinstall Windows 2x.  I've just upgraded to the latest Ubuntu and, once again, Vista won't load.

Some of you will say "Good, who needs Windows anyway?", but I do need Windows for a bunch of things, as do other members of my family.  Why does this happen every time and why is it so difficult to get answers about how to fix it simply?

:mad:

I think probably Grub is overwriting NTLDR.  Why Grub isn't recognizing Windows, who knows?  

Hang in there.  Difficulties now are balanced by a great OS once you work out the bugs.  

Much luck.

---

### Post by ugm6hr on 2010-06-01
Unfortunately, no computers have yet been developed that behave quite as intuitively as you (or I) would like.

---

### Post by za.zen on 2010-06-01
> **ugm6hr said:**
> Unfortunately, no computers have yet been developed that behave quite as intuitively as you (or I) would like.

Who do we complain to about that?  :P

---

### Post by bcbc on 2010-06-01
> **za.zen said:**
> Who do we complain to about that?  :P

You complain to the developers. This particular bug is really, really unnecessary. Yes it's nice to smell the roses and get philosophical about it, but really it's just dumb coding.

Try and install grub2 from command line to a partition. Please do it. This is what you get:
```
$ sudo grub-install /dev/sda6
/usr/sbin/grub-setup: error: unable to identify a filesystem in hd0,6; safety check can't be performed.
$ sudo grub-install /dev/sda5
/usr/sbin/grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea..
/usr/sbin/grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.

```

So why would the install and upgrade that every 'normal' user has to do, bypass this safety mechanism?

---

### Post by philinux on 2010-06-02
OP has opened a support thread for this.
[http://ubuntuforums.org/showthread.php?p=9390996#post9390996](http://ubuntuforums.org/showthread.php?p=9390996#post9390996)

Thread closed.

---

