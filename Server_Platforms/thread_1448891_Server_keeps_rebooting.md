---
title: "Server keeps rebooting"
date: 2010-04-07
forum: Server Platforms
---

### Post by yukomato on 2010-04-07
I have a compaq ML370 G3 server with 2 SCSI 73G and 2 SCSI 146G. I am trying to install server 9.10, on this server. Installation went OK. Got some problem with RAID configuring but passed after X retry installation. I have spend lots og hour configuring web and mail, but suddentlig yesterday my server start rebooting automatic nad keeps rebooting. I have to shut it down. 
I wonder that there is another way to fix it do i have to installed it again. 

I also wonder that maybe i can installer this server as Windows 2003 with virtual pc or vmware, so i can installed ubuntu server on virtual. Is that a good thing do ?? I can always backup the hole ubuntu server, that i don't need to reinstall all the time. 

I also wonder install ubuntu on PC with sata disk without RAID, because the server make a lots of noice. It that a good way to do.

It's lots of question. I hope someone can help me with this. Thanks a lots.

---

### Post by tgalati4 on 2010-04-07
Sounds like older hardware that has developed a problem.  Could be  RAID/disk problem.  Try pulling drives and only install on one drive.  See if it's stable.

Running ubuntu on top of windows server makes little sense if you have a hardware problem.

Servers are noisy by design.  Put in a closet.

---

### Post by KB1JWQ on 2010-04-07
I'd boot into recovery mode and check the logs in /var/log/ and dmesg.


It should be giving some indication as to what's dying.

---

### Post by deracled on 2010-04-08
Proliant servers usually come with ASR, that will reboot (reset) the machine if it detects a hang due to hardware malfunction. Make sure your hardware is sane perhaps by running HP diagnostics or check if memory is seated properly and it's contacts are clean.

Here's a related post that says to update the machine BIOS to fix it!

[https://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1270720363548+28353475&threadId=803534](https://forums11.itrc.hp.com/service/forums/questionanswer.do?admit=109447626+1270720363548+28353475&threadId=803534)

Doros

---

