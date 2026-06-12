---
title: "Fastest way to install 8.04 on two machines?"
date: 2008-06-26
forum: Server Platforms
---

### Post by auphil on 2008-06-26
Hey Guys,

I was wondering what you all thought about the fastest way to install Ubuntu 8.04 onto 2 identical servers (not counting Ghost for Linux, systemimager, etc.) ??

The servers are Sun Fire x2200's - they have two disks each and will be configured as mirrors by the LSI RAID card.

I was thinking, get one server configured then pull one disk out of Server A, put it into Server B and begin a rebuild - would that work?

Then I would just go into Server B and set /etc/hosts, etc.

Please let me know if this is a bad idea.

Thanks,
Phil

---

### Post by hyper_ch on 2008-06-27
that should work - but I never tried it...

(1) install on server a
(2) pull out the disk, put it into server b, make it as primary boot device
(3) dd the "server a" disk to "server b" disk

IMHO that should work... only thing is you'll need to chnage the hostname afterwards to have different ones ;)

---

### Post by skunkbad on 2008-06-28
install OS on first server
install drive from second server as second drive in first server
verify the device files before proceding (sda, sdb, hda, hdc, ...)
From terminal type:
cat /dev/sda > /dev/sdb
(make sure that your OS is on sda before doing this, and that sdb is the second empty drive or you will do bad things)

---

### Post by Chayak on 2008-06-29
In the time it takes you to install the first server and then transfer the disk to the second server and rebuild it you could have already installed it faster by just popping a second install disk in the second unit and installing them both at the same time.

---

### Post by promodus on 2008-06-29
I would think the fastest way to deploy two identical machines would be to install them both at the same time.

Most of my installs are all virtual, and it gets tiring answering those questions over and over...

I did a quick post on using preseed:
[http://ubuntuforums.org/showthread.php?t=829482&highlight=unattended]("http://ubuntuforums.org/showthread.php?t=829482&highlight=unattended")

Cheers,
Rich.

---

