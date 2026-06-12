---
title: "Backports not working, what does &quot;Bad header line&quot; mean?"
date: 2005-12-13
forum: Ubuntu Backports
---

### Post by brynjarh on 2005-12-13
I just installed Ubuntu 5.10, added *deb [http://is.archive.ubuntu.com/ubuntu](http://is.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse* to my sources.list, did sudo apt-get update and then sudo apt-get dist-upgrade and got this:

```
The following packages will be upgraded:
  evms evms-ncurses iptables libevms-2.5 libgnutls11 xkeyboard-config
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1729kB of archives.
After unpacking 77.8kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err http://is.archive.ubuntu.com breezy-updates/main xkeyboard-config 0.6-5breezy1
  Bad header line
Err http://is.archive.ubuntu.com breezy-updates/main libgnutls11 1.0.16-13.1ubuntu1
  Bad header line
Err http://is.archive.ubuntu.com breezy-backports/main libevms-2.5 2.5.3-7ubuntu1~breezy1
  Got a single header line over 360 chars
Err http://is.archive.ubuntu.com breezy-backports/main evms 2.5.3-7ubuntu1~breezy1
  Bad header line
Err http://is.archive.ubuntu.com breezy-backports/main evms-ncurses 2.5.3-7ubuntu1~breezy1
  Got a single header line over 360 chars
Err http://is.archive.ubuntu.com breezy-updates/main iptables 1.3.1-2ubuntu1.1
  Bad header line
Failed to fetch http://is.archive.ubuntu.com/ubuntu/pool/main/x/xkeyboard-config/xkeyboard-config_0.6-5breezy1_all.deb  Bad header line
Failed to fetch http://is.archive.ubuntu.com/ubuntu/pool/main/g/gnutls11/libgnutls11_1.0.16-13.1ubuntu1_i386.deb  Bad header line
Failed to fetch http://is.archive.ubuntu.com/ubuntu/pool/main/e/evms/libevms-2.5_2.5.3-7ubuntu1~breezy1_i386.deb  Got a single header line over 360 chars
Failed to fetch http://is.archive.ubuntu.com/ubuntu/pool/main/e/evms/evms_2.5.3-7ubuntu1~breezy1_i386.deb  Bad header line
Failed to fetch http://is.archive.ubuntu.com/ubuntu/pool/main/e/evms/evms-ncurses_2.5.3-7ubuntu1~breezy1_i386.deb  Got a single header line over 360 chars
Failed to fetch http://is.archive.ubuntu.com/ubuntu/pool/main/i/iptables/iptables_1.3.1-2ubuntu1.1_i386.deb  Bad header line
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

"Bad header line"?
"Got a single header line over 360 chars"?

What does it mean?
Is it a problem with my operating system or is it a problem with the Ubuntu Backport repository?
Is this a common problem with APT?
Does this problem usually get fixed or is it left there for some time?
How long can I expect to have to wait?

---

### Post by carlosqueso on 2005-12-13
I dunno what all of that means, but try taking the "is" out out of the address....I know the us mirrors were screwed, maybe the is ones are too?

---

### Post by brynjarh on 2005-12-13
Worked, thanks man.

---

### Post by carlosqueso on 2005-12-13
no problem, I don't know what's with their national mirrors...anyway...happy upgrading.

---

