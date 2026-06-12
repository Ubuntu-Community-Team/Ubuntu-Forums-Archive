---
title: "cut-paste from Windows 7 host does not work to Ubuntu 16.04 on VirtualBox"
date: 2016-05-13
forum: Virtualisation
---

### Post by Ron_Barak on 2016-05-13
I've installed Ubuntu 16.04 on VirtualBox 4.1.10 running on Windows 7.

Managed to get Guest Additions to work. 
Shared clipboard is set to bidirectional.

All seems to work fine besides cut-and-paste, which does not work, namely, none of the following works on a terminal window:
[LIST=1]
[*]Ctrl-V
[*]Shift-Ins
[*]Paste from terminal's menu.
[/LIST]

Is this a known bug, or do I need to do something special to get cut-and-paste to work?

---

### Post by jim_deadlock on 2016-05-14
This can be flakey. Sometimes you have to copy/paste one way before the other way will work, also try rebooting the guest. If the problem persists then you might try upgrading to the latest version 5.0, a fresh install might help. Shared clipboard is reliant on the Guest Additions so it's important you have it installed properly.

---

### Post by Ron_Barak on 2016-05-14
Thanks, Jim, for taking the time to answer.
> **jim_deadlock said:**
> This can be flakey. Sometimes you have to copy/paste one way before the other way will work, 
Alas, none of the cut-and-paste methods work.
> **jim_deadlock said:**
> also try rebooting the guest.
Did that.
> **jim_deadlock said:**
> If the problem persists then you might try upgrading to the latest version 5.0, 
Unfortunately, googling indicates that the versions of VirtualBox older than my current one seem to break Guest Additions, so I'm averse to upgrading.
> **jim_deadlock said:**
> a fresh install might help. Shared clipboard is reliant on the Guest Additions so it's important you have it installed properly.
Mounting local directories works just fine, which indicates that the correct version of Guest Additions is employed.

Thing is, previous Ubuntu versions installed in the same VirtualBox cut-and-paste without a hitch. It's only this latest version of Ubuntu that gives me grief.

---

### Post by jim_deadlock on 2016-05-14
The latest version is 5.0 not 4.1.10. As I said, shared clipboard can be temperamental, I've had trouble with it myself from time to time. Reinstall/upgrade would be my next step.

By the way, I'm pretty sure your Ubuntu version is irrelevant, this is an issue with either VB itself, the Guest Additions, the VB settings for the guest or a combination of these.

When you said VB versions older than your current one, did you mean NEWER?

---

### Post by MAFoElffen on 2016-05-17
And Guest Additions was replaced in VirtualBox 4.3 and later with the Extension Pack, which now is a single instance install to VirtualBox itself. You no longer have to use it on each VM Guest as the Guest Additions did.

---

### Post by Ron_Barak on 2016-05-17
> **jim_deadlock said:**
> When you said VB versions older than your current one, did you mean NEWER?
Yes, mea culpa: I meant newer.

---

### Post by Ron_Barak on 2016-05-17
> **MAFoElffen said:**
> And Guest Additions was replaced in VirtualBox 4.3 and later with the Extension Pack, which now is a single instance install to VirtualBox itself. You no longer have to use it on each VM Guest as the Guest Additions did.
It's tempting to be rid of the Guest Additions. 
However, as I wrote above, google results don't really encourage such an upgrade (maybe as opposed to a clean upgrade which will erase all existing hosts): e.g. [https://forums.virtualbox.org/viewtopic.php?f=6&t=68858](https://forums.virtualbox.org/viewtopic.php?f=6&t=68858).

---

### Post by MAFoElffen on 2016-05-19
> **Ron_Barak said:**
> It's tempting to be rid of the Guest Additions. 
However, as I wrote above, google results don't really encourage such an upgrade (maybe as opposed to a clean upgrade which will erase all existing hosts): e.g. [https://forums.virtualbox.org/viewtopic.php?f=6&t=68858](https://forums.virtualbox.org/viewtopic.php?f=6&t=68858).
??? What Google results?

Do you mean where you will need to uninstall old versions to install a new version? Yes, that is so. But, uninstalling VirtualBox does not do anything with the old VM's. You do not lose any of your VM guests. You uninstall the "program," which leaves the VM's as they are. So your comment:
> 
a clean upgrade which will erase all existing hosts

I think maybe you are a bit confused(?), as you do not lose VM Hosts. You are correct in that you cannot upgrade, in a tradition sense, where the program stays in place. while changing versions. As menetioned aboveY (You have to uninistall old/ install new, but just the program itself.). 

After install, insure you install the Extension Pack of the matching version. Otherwise, if they previously had Guesr Additions, then those VM's will complain about needing USB 2.0 support,.until you install the Extension Pack.

---

### Post by Ron_Barak on 2016-05-19
> **MAFoElffen said:**
> ??? What Google results?

Do you mean where you will need to uninstall old versions to install a new version? Yes, that is so. But, uninstalling VirtualBox does not do anything with the old VM's. You do not lose any of your VM guests. You uninstall the "program," which leaves the VM's as they are. So your comment:

I think maybe you are a bit confused(?), as you do not lose VM Hosts. You are correct in that you cannot upgrade, in a tradition sense, where the program stays in place. while changing versions. As menetioned aboveY (You have to uninistall old/ install new, but just the program itself.). 

After install, insure you install the Extension Pack of the matching version. Otherwise, if they previously had Guesr Additions, then those VM's will complain about needing USB 2.0 support,.until you install the Extension Pack.

I took a deep breath, put a neckless of garlic around my neck, chased my black cat to the street, and upgraded to VirtualBox 5.0.20.

Lo and behold, my existing guests managed to boot, and cut-and-paste work.

Yay.

---

