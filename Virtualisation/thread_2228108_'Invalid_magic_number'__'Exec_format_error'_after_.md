---
title: "'Invalid magic number' / 'Exec format error' after sudden shutdown"
date: 2014-06-05
forum: Virtualisation
---

### Post by apollovy on 2014-06-05
Hello, community!

Here's my story:
01. Windows 7 host + VMware 6 player + Ubuntu inside.
02. Put Windows into sleep mode.
03. Power cord jumped out of the socket.
04. Windows boot.
05. chkdsk C: /f
06. 'Invalid magic number' message when loading Ubuntu under VMware.
07. Boot other x86 system with virtual drive with subject Ubuntu attached.
08. fsck.ext4 -f /dev/sdb1 && mkdir /tmp/sdb1 && mount -t ext4 /dev/sdb1 /tmp/sdb1 && chroot /tmp/sdb1
09. 'Exec format error' - OK, really, it was x64 system!
10. Boot other x64 system with virtual drive with subject Ubuntu attached.
11. fsck.ext4 -f /dev/sdb1 && mkdir /tmp/sdb1 && mount -t ext4 /dev/sdb1 /tmp/sdb1 && chroot /tmp/sdb1
12. 'Exec format error' - well, that's weird!

So, can anybody (try) to:
01. Explain what could happen.
02. What to do to reanimate my system. I'm missing it!

Thanks in advance :)

---

### Post by kira_belka2 on 2014-06-11
well ext4 doesn't depend on what kind of OS you use.. I mean 32bit or x64 :)
So create vmware machine and attach disk from your old ubuntu machine (as boot disk)
It should work.

---

### Post by apollovy on 2014-06-11
Nope, it's not working. Some files gone bad, seems like forever :(
For example, /etc/hosts file is corrupt and contains binary data %)
Well, by this time I resqued all that I need and deleted virtual drive from HDD, so, guess, topic is closed, but a question remains unanswered...

---

