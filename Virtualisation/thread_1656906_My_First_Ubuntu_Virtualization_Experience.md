---
title: "My First Ubuntu Virtualization Experience"
date: 2010-12-31
forum: Virtualisation
---

### Post by xathras1982 on 2010-12-31
Hi,
Just thought I'd post my comments on my first Virtualization Project using Ubuntu and VirtualBox. I have to say I am impressed

I am using a 64-Bit, Quad Core AMD Phenom 9750 2.4 GHz, 8Gb RAM and Host Machine sits on a Windows 7 Premium Install.

I set my machine with the following options:
Base Memory: 2500MB
Video Memory: 128MB
ISO Attached: Ubuntu 10.10 Server 64 Bit (Default install of SSH and LAMP)
Disabled Audio, USB
Network Card Options: 4x Bridged Intel Pro 1000

The install was extremely quick, the fastest I've seen for OS Installation, approx 10-15 mins. 

Pros: Speed, Security, Flexability
Cons: I've been unable to succesfully rebuild a linux kernel on the virtualized box. However, I think this maybe the idiot tapping the keys more than anything else ;-)

Post Install Options:

[LIST]
[*]Spamassassin
[*]ClamAV
[*]ClamAV Daemon
[*]Postfix
[*]Apache SSL
[*]Squirrelmail
[*]NMAP
[/LIST]

Current utlisation of disk 6% out of a 22GB SCSI disk made available

Top shows:

> top - 18:18:10 up 19:04,  1 user,  load average: 0.06, 0.02, 0.00
Tasks: 128 total,   1 running, 114 sleeping,  13 stopped,   0 zombie
Cpu(s):  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2526800k total,   865996k used,  1660804k free,    67452k buffers
Swap:  1134588k total,        0k used,  1134588k free,   224768k cached

Thumbs up from me :)

---

### Post by HermanAB on 2011-01-01
Howdy,

I've run WinXP in a VM on an EEE PC701 running at about 500 MHz and it worked fine.  So yes, Vbox is rather incredible.

---

