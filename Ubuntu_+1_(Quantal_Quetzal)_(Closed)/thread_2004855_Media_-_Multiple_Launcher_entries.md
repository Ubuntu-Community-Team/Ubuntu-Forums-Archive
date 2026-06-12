---
title: "Media - Multiple Launcher entries"
date: 2012-06-16
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by 3vi1 on 2012-06-16
Has anyone else noticed multiple entries in the Unity launcher for some of their removable (and not removable - but manually added to fstab) drives?

I see this on both of my test systems, so it would be very coincidental if it were just me.  I did check launchpad a couple of days back though, and couldn't find anyone else reporting the issue.

So, I'm just looking for confirmation or a link to an existing bug if someone knows of one (before I file one myself).

---

### Post by SpaceCeph on 2012-06-16
I have the same. But only with removable drives and drives not in fstab.

---

### Post by effenberg0x0 on 2012-06-18
Same here. I have two 8GB Sandisk USB attached. I can see two units on /run/media, but Unity's Launcher shows 4 entries. The USB units have single partitions. See screenshot. 

[ATTACH]219885[/ATTACH]

Have you created a bug report? I'd like to +1 on it.

Regards,
Effenberg

---

### Post by fjgaude on 2012-06-18
> **effenberg0x0 said:**
> Same here. I have two 8GB Sandisk USB attached. I can see two units on /run/media, but Unity's Launcher shows 4 entries. The USB units have single partitions. See screenshot. 

[ATTACH]219885[/ATTACH]

Have you created a bug report? I'd like to +1 on it.

Regards,
Effenberg

Same here, doubles... couldn't help but notice VMware installed on your box. Anything you care to share with us how you did it? Thanks!

---

### Post by mc4man on 2012-06-18
This has been going on for a few weeks, ever since gvfs* upgraded to monitor udisks2
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1010714](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1010714)

The other side effect of gvfs/udisk2 (intended I suspect), is removable media can no longer be 'safely removed' (powered down), only ejected or unmounted
(& flash media can get 2 different icons depending on whether flash drive is 'direct access' or not

---

### Post by effenberg0x0 on 2012-06-18
> **fjgaude said:**
> Same here, doubles... couldn't help but notice VMware installed on your box. Anything you care to share with us how you did it? Thanks!
Hi fjgaude, I can't remember when I patched it, but I'm sure I haven't patched it again recently. I think I patched it about two months ago or something. It's working fine.
```
[21:40:19]  ahsl@AL-DESK01:[/run/media/ahsl]: vmplayer --version
VMware Player 4.0.3 build-703057
[21:40:23] ahsl@AL-DESK01:[/run/media/ahsl]: uname -a
Linux AL-DESK01 3.4.0-5-generic #11-Ubuntu SMP Tue Jun 5 17:33:27 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```
I'll download the latest vmware-player and diff the original /usr/lib/vmware/modules/source/* from mine, to a .patch file.

This is probably the last version of vmware I'll use, as I am moving to having all VMs at a server (probably KVM or VirtualBox) running 24/7 and will access them from clients via rdp.

> **mc4man said:**
> This has been going on for a few weeks, ever since gvfs* upgraded to monitor udisks2
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1010714](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1010714)

The other side effect of gvfs/udisk2 (intended I suspect), is removable media can no longer be 'safely removed' (powered down), only ejected or unmounted
(& flash media can get 2 different icons depending on whether flash drive is 'direct access' or not
Thanks for the explanation mc4man! I never use USB flash drives in the desktop, which is why I just saw this bug.

Regards,
Effenberg

---

### Post by mc4man on 2012-06-18
The  'odd' thing is how some flash drives are seen differently than others. When the gvfs/udisks2 change first took place direct access drives like SanDisk were getting the different icon & only a unmount option 
Now they still get the diff icon but  back to an eject only option.

I don't think the loss of safe remove on usb hdd's is a big deal though I've some that have no power switch so only power off when unplugged. In that case the SR was handy

(Did burn me just after the switch though more user idiocy. I'd logged out in with a usb hdd (500GB) that normally I'd SR (power down), instead of unmount

After logging in went to make a start up disk with a flash drive & from 'muscle memory' just proceeded, not realizing disk creator had picked my usb HDD which was powered on till a bit too late. It's likely salvageable though haven't gotten around to trying

---

### Post by effenberg0x0 on 2012-06-18
> **mc4man said:**
> The  'odd' thing is how some flash drives are seen differently than others. When the gvfs/udisks2 change first took place direct access drives like SanDisk were getting the different icon & only a unmount option 
Now they still get the diff icon but  back to an eject only option.

I don't think the loss of safe remove on usb hdd's is a big deal though I've some that have no power switch so only power off when unplugged. In that case the SR was handy

(Did burn me just after the switch though more user idiocy. I'd logged out in with a usb hdd (500GB) that normally I'd SR (power down), instead of unmount

After logging in went to make a start up disk with a flash drive & from 'muscle memory' just proceeded, not realizing disk creator had picked my usb HDD which was powered on till a bit too late. It's likely salvageable though haven't gotten around to trying

I have a drawer of USBs here: Samples, promotional giveaways, original and "brandless" units. I'd say 95% of them have no on/off switch or any button at all. I'll be doing some tests with them and external HDD too. In parallel: I wonder if the current status presents a risk for the quality of media produced via Startup Disk Creator, for example. I believe it has great chances of failing. We had a phase of broken SDC in the past and it was not cool...

Regards,
Effenberg

---

### Post by fjgaude on 2012-06-19
> I'll download the latest vmware-player and diff the original /usr/lib/vmware/modules/source/* from mine, to a .patch file.

Thanks, Effenberg for the tip. I've done it and it works!

---

