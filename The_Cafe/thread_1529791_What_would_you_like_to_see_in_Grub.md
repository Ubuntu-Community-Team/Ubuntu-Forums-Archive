---
title: "What would you like to see in Grub?"
date: 2010-07-12
forum: The Cafe
---

### Post by themarker0 on 2010-07-12
I'd like to see grub more adapted into the OS. Like i could click the shutoff menu, and say "Restart into Gentoo, or Restart into windows." 

What improvements would you like to see in Grub?

---

### Post by marshmallow1304 on 2010-07-12
That feature is supposed to be available (see 'man grub-reboot'), but it isn't working in the current Ubuntu version.  It's been [fixed upstream]("https://bugs.launchpad.net/ubuntu/karmic/+source/grub2/+bug/497326/comments/4") though.

---

### Post by themarker0 on 2010-07-12
> **marshmallow1304 said:**
> That feature is supposed to be available (see 'man grub-reboot'), but it isn't working in the current Ubuntu version.  It's been [fixed upstream]("https://bugs.launchpad.net/ubuntu/karmic/+source/grub2/+bug/497326/comments/4") though.

Didn't know you could do that. O.o So like my name, then restart and to what? thats fing cool.

---

### Post by NightwishFan on 2010-07-12
Something similar to OpenSUSE, with a nice theme and and an easy bar (no key commands to access it) to add/view boot options.

---

### Post by libssd on 2010-07-12
Something *like* Burg Manager to provide a GUI to grub configuration. The *status quo* is awfully primitive, and GRUB2 did nothing to improve things -- if anything, I think it made maintenance more difficult, although it may just be a matter of my unlearning legacy grub habits. But not Burg, which seems to be a kludge; intuitive GRUB2 configuration needs to be integral, not an add-on developed by someone else. 

Gordon Matzigkeit writes in the GRUB2 manual: *"I, personally, believe that... the boot loader is the most important software of all."* Without a functioning boot loader, you don't have a functioning OS, and it's far too easy to screw things up without a decent configuration UI, or to recover from installation problems (*viz*., [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)). 

I delayed upgrading to Ubuntu 9.10 or 10.04 for probably 6 months, because I was getting -15 error messages after several trial installations -- especially frustrating when GRUB2 decided to update (and make unbootable) a disk that Ubuntu wasn't even being installed to. GRUB2 installation problems were easily the worst experience that I have had with Ubuntu in the past year, and I suspect that they turned off a lot of potential Ubuntu users.

---

### Post by NightwishFan on 2010-07-12
I think it is easier in grub2 to manage custom boot options when installing new kernels.

---

