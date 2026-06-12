---
title: "Attempting to install bootable Windows 7 OS on secondary harddrive w/ Virtual box"
date: 2015-05-30
forum: Virtualisation
---

### Post by jackechanprime on 2015-05-30
Hey all,

I am (or... was) running a 2-OS system, and recently had to nuke my Windows drive. I used shred to wipe the affected drive completely clean, and now am trying to reinstall windows and "start over" as usual. Normally I would just boot into the disk and do it "the easy way" -- but that isn't working at the moment because apparently the windows install disk I got doesn&#8217;t have the USB drivers for my mouse/keyboard, and I only have 1 USB-2-ps/2 converter. Even that isn't detecting properly for god knows what reason. Long story short, I have no input devices when booting straight into the disk, which might I add, is about the most frustrating and inane problem I've ever had.

So while thinking of alternate solutions (running it in WINE went nowhere...) I had an interesting idea, that APPARENTLY is possible, but I can't figure out quite how to do it. Since my mouse and keyboard still work fine on the Ubuntu OS side, I thought I'd fire up virtual box and run the windows 7 installer in it and let it create a full bootable system instead of a VM. Turns out that's a bit more complicated than I anticipated.

What little I've turned up on the topic seems to suggest that it is possible, but again, I cant quite figure out which settings and options I need to flip where to get it to work. I found some references to using the raw disk access functionality, but at the moment the Vitrualbox website is down for maintenance, so I couldn't get any more info on how to work that.

So, the question in its simplest form is this:

While running Ubuntu 14.04 LTS, and running a Windows 7 x64 install CD through Virtualbox, how do I install a full fledged, bootable, Windows 7 OS on a secondary 1TB and utterly empty hard-drive (designated /sda, believe it or not my bootable ubuntu drive is /sdb)? (and/or is this even possible?)

---

### Post by jackechanprime on 2015-05-30
While tinkering around waiting for a response I made a VM with the Windows 7 disk, and have been trying to plop it onto the terabyte drive I want to "Raw-disk" it on to. I tried this command:

> VBoxManage internalcommands converttoraw "Windows 7.vdi" /dev/sda1

and got this error back:

>  VBoxManage: error: Cannot create destination file "/dev/sda1": VERR_ACCESS_DENIED 

So I tried the obvious solution:

>  Sudo VBoxManage internalcommands converttoraw "Windows 7.vdi" /dev/sda1 

And I got this perplexing bit of nonsense back:

> No command 'Sudo' found, did you mean:
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
 Command 'udo' from package 'udo' (universe)
Sudo: command not found

My only response to that is: what the....?

Help??

---

### Post by jackechanprime on 2015-05-30
[deleted -- accidental doublepost]

---

### Post by jackechanprime on 2015-05-30
For some reason the system decided to cooperate a little more after a break... but this time I get a blatantly false error:

> VBoxManage: error: Cannot copy image data: VERR_DISK_FULL

Here's a screenshot of the situation. The displayed disk is the one I’m trying to install onto. As you can see, it's 1 TB of freespace and nothing else.

[ATTACH=CONFIG]262329[/ATTACH]

I tried to set a partition on the drive and it made the problem revert to the previous error:

> VBoxManage: error: Cannot create destination file "/dev/sda1": VERR_ALREADY_EXISTS


I'm officially stumped.

---

### Post by KillerKelvUK on 2015-06-01
From your 2nd post (#2) the error in the final command is because you were using a CAPITAL 'S' for 'Sudo' which is incorrect...all lower case.

Can't really help with VB queries though although I've previously used KVM to pass a hard disk through for the VM OS to use, my reasoning was to pass lots of hard drives through for RAID...Why do you want to use this method instead of the disk image default?

---

### Post by gordintoronto on 2015-06-02
Can you run Windows 7 from within the VM? If so, could you use, for example, Macrium Reflect to make an image of the Windows installation, then restore that onto the empty drive?

---

