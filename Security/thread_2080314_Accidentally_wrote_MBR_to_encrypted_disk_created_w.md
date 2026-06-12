---
title: "Accidentally wrote MBR to encrypted disk created with Ubuntu 10.04,urgent help needed"
date: 2012-11-03
forum: Security
---

### Post by aonir on 2012-11-03
Hey, I have a pretty big problem.

I accidentally answered windows drive managers question to initialize my disk with yes, but it was my encrypted backup drive instead of the disk I wanted to initialize.

So it wrote a new mbr to the disk, but on that disk was an encrypted partition created with ubuntu 10.04 integrated drive manager. It offered to do a full disk encryption, so I choose that.

Am I correct in the assumption that it used cryptsetup with luks?
I did a backup of the header some time ago with cryptsetup -luksHeaderBackup. I restored this backup to /dev/sdd,
but I still cant access my data. I am really really desperate right now, what can I do?

Gparted shows an unformatted drive.

Thank you very very much,
aonir

Edit: solved my problem, I did not restore the header I had, I failed to type yes in uppercase, so no operation was committed. Restoring the header worked.

---

### Post by claracc on 2012-11-04
Instead of editing post to mark as solved, you had to use the "thread tools" in the upper right part of the page, in order to mark as [solved] in the title of the post.

---

