---
title: "How to remote unlocking a fully encrypted ubuntu 16.04 server?"
date: 2016-05-18
forum: Server Platforms
---

### Post by papapig on 2016-05-18
Hi all.


I want to remote unlock a fully encrypted server using dropbear in the initramfs process.


My procedure that has worked from ubuntu 10.04 to ubuntu 14.04, does not work on ubuntu 16.04.


I noticed that it does not reply to ping in initramfs stage.


Is there a procedure for remote unlocking a 16.04 ubuntu server?


Thanks to all.

---

### Post by aljos on 2016-07-30
This is also a concern of mine.  I have done some quick searching, and it appears that this is fixed in Debian, but not in Ubuntu.  I'm VERY glad that I found out about this issue before attempting an upgrade on my servers.

I'm actually quite shocked that this was overlooked.  Considering how many headless servers are out there, and hoping that at least a fair amount of those servers are using full disk encryption, I can't imagine we are the only ones running into this problem.

I look forward to hearing about a solution to this.  Until then, my current servers will stay on Trusty, and the server i'm putting together next month will have to be Debian.

[https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/595648](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/595648)
[https://superuser.com/questions/919751/automatically-unlock-luks-partition-using-a-key-on-an-usb-drive-on-debian-jessie](https://superuser.com/questions/919751/automatically-unlock-luks-partition-using-a-key-on-an-usb-drive-on-debian-jessie)

---

