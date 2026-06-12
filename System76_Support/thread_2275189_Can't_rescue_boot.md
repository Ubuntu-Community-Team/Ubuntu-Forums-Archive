---
title: "Can't rescue boot"
date: 2015-04-24
forum: System76 Support
---

### Post by grizdog on 2015-04-24
I wiped out /etc, and then lost the session.  So I need to boot from some sort of rescue media.

A friend gave me two things - a thumb drive, and a CD, both with a fedora live CD on them.  Neither one seems to work.  I hold down F8 and get a list of possible boot devices, but none of them will boot the system.  They all seem to fail in different ways,   The thumb drive sends up a screen full of messages and freezes, the last message singularly uninformative, saying:
[   2.194536   sd 1:0:0:0: sdb 4096-byte physical blocks

I can't tell which device is the CD, the list of options isn't clear, but most of them claim not to be able to find a kernel.

Really, all I want to do is bring this thing up and copy over the etc directory from backup, but is this system (it's a Ratel, by the way, I think about 3 years old) unable to boot off of anything other than an Ubuntu  rescue CD?

Thanks for any help.  These low level problems always beat me up.

---

### Post by grizdog on 2015-04-24
OK, well, after about a dozen attempts I got a rescue kernel running and got my backup directory in place.  What didn't work: two fedora systems, an Ubuntu 12.04, and the Ubuntu rescue remix 12.04  The only thing that worked was an Ubuntu 14.04 DVD.  In fairness, it was the obvious thing to try, it's just that I had the other media available to me and doing a dvd burn was a bit of trouble.  But it does seem a little odd that nothing else would even boot off a live cd.  I guess my Ratel is a little too up-to-date.

I'm marking this as solved since I can use my computer again, but any insights as to exactly what happened would be appreciated.

Thanks to all who took a moment to think about this.

---

