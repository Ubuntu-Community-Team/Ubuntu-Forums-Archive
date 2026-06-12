---
title: "no /etc/fstab file"
date: 2007-12-07
forum: Virtualisation
---

### Post by erdley on 2007-12-07
Need to add a line to my etc/fstab location to enable USB operation in guest Win XP Pro on my Gutsy host.

When I look for etc/fstab I don't find it.  Is it possibly some kind of hidden file?

---

### Post by njparton on 2007-12-07
try doing the following in a terminal:

```
sudo gedit /etc/fstab
```

hidden or not that should bring it up.

You must have an fstab file somewhere!

You have installed ubuntu and aren't just running from the live CD aren't you?

---

### Post by erdley on 2007-12-07
Many thanks for setting a Linux beginner straight!

Your suggested terminal command line did the trick, and no, I am not working with a live CD, but with an installed Gutsy.

I can only assume I was faked out by some kind of hidden file situation.

Thanks again!:)

---

### Post by bodhi.zazen on 2007-12-07
The problem was either :

1. you did not open the file as root.

2. wrong path. etc/fstab is not the same as /ect/fstab

The first is the relative path and starts in your home directory (ie /home/<you>/etc/fstab

The second is absolute and start at root / ie /etc/fstab

---

### Post by erdley on 2007-12-07
Thanks for the info.  I'm not sure I originally searched for this file properly -- I opened the file system, and worked my way down to /etc/, observing a large number of files under /etc/, but no fstab.  Opening the file with gedit, however, gave me access to /etc/fstab to add the necessary line, and the change produced the desired result..

---

