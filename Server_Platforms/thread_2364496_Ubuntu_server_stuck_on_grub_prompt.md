---
title: "Ubuntu server stuck on grub prompt"
date: 2017-06-24
forum: Server Platforms
---

### Post by tdphorth on 2017-06-24
**Background**
I setup an an old computer as a media server and it's been working well for the past few months, but recently I lost ssh access and when I connected locally the server is stuck at the grub prompt.

**Experience**
I'm not *that* unexperienced with ubuntu, but I am very unexperienced with grub, so I'm pretty lost.
[B]
Setup[/B]
The server has two, 3 terabyte drives setup as a software raid-0 array. I installed ubuntu server 16 in EFI mode: one partition for EFI on one drive, an empty sibling partition on the other, and one large raid 0 partition spanning the rest of the space on the two drives.

[B]Cause
[/B]I wasn't doing anything on the server when it went caput. My brother mentioned that he could no longer access the computer, and when I tried to ssh in, neither could I. It's possible auto-updates were enabled, but unlikely. 

[B]What I've tried
[/B]I installed boot-repair-disk and ran through it. It reported that I was using raid (as I am) and prompted me to install mdadm. I installed it using the command it gave me -- mdadm showed an error during the installation process ([COLOR=#111111][FONT=Consolas]/usr/sbin/grub-probe:error:failed to get canonical path of /cow[/FONT][/COLOR]), but otherwise seemed to install correctly. When boot-repair finished doing it's thing it prompted me to choose the recommended repair process, and I accepted. It reported that the repair was successful and produced this log: [http://paste.ubuntu.com/24945220/](http://paste.ubuntu.com/24945220/)

The repair was not successful. Upon rebooting I was back at the grub prompt and nothing had changed. 

[B]Grub info 
[/B]```

GNU GRUB  version 2.02~beta2-36ubuntu3.8

Minimal Bash-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else
TAB lists possible device or file completions.


grub> ls
(md/1) (md/0) (hd0) (hd0,gpt3) (hd0,gpt2) (hd0,gpt1)
grub> ls (hd0,gpt1)
(hd0,gpt1): Filesystem is fat.
grub> ls (hd0,gpt1)/
efi/
grub> ls (hd0,gpt1)/efi
./ ../ ubuntu/
grub> ls (hd0,gpt1)/efi/ubuntu
./ ../ shimx64.efi grubx64.efi MokManager.efi grub.cfg
grub> ls (hd0,gpt2)
(hd0,gpt2): Filesystem is unknown.
grub> ls (md/0)
error: no server is specified.

```



I wanted to ask the experts before I proceeded any further and risk doing more harm than good. I am way out of my depth, so I'd appreciate any advice you're prepared to give me.  
Thanks for reading (:

*edit: *Fixed paste link, sorry!

---

### Post by TheFu on 2017-06-24
Advice: RAID0 is a terrible idea. Only use it when you can afford to loose all the data on those disks.  RAID is never a replacement for backups.

This is NOT an x86 install folks. It is on an ARM system. I don't know anything about ARM except Raspberry Pis. I've never seen Grub on any ARM systems.  Cannot help, sorry.

---

### Post by deadflowr on 2017-06-24
The paste link has zero to do with the boot repair output.
Wrong log.
Or so it would seem.
It brings up a link for a kodi log.
Perhaps re-try boot-repair and post a good boot-repair paste link.

(Or am I the only one who's getting directed to the wrong page?)

---

### Post by TheFu on 2017-06-24
garbage in = garbage out.
Wrong link posted = confused replies / wasted time.

---

### Post by tdphorth on 2017-06-24
I thought the link looked strange, I must have copied it down incorrectly. I'll run it again and get a proper link, sorry for the confusion!

It's definitely x86, and I did raid0 to maximize storage space. It's just a media server, all the data is reproducible. It's just the setup time that's wasted.

---

### Post by tdphorth on 2017-06-24
Okay here is the new log file: [http://paste.ubuntu.com/24945220/](http://paste.ubuntu.com/24945220/)
Sorry again for wasting your time with the first!

I also took some pictures of the process:
After the first stage, it instructed me to run a command, this is the output:
[http://i.imgur.com/XM2i2sx.jpg](http://i.imgur.com/XM2i2sx.jpg)
I clicked OK, an got this warning:
[http://imgur.com/Mj0wajq.jpg](http://imgur.com/Mj0wajq.jpg)

---

