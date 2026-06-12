---
title: "VM problems on Core2Quad cpuhttps://ubuntuforums.org/showthread.php?t=2383213"
date: 2018-04-16
forum: Virtualisation
---

### Post by sp40140 on 2018-04-16
I have a multipurpose server running Core2Quad cpu and 8 gig ram. 
Until last version of Ubuntu (17.04), I was able to run VMWare player (version 12) to run couple of guest vms. And was running android studio without any problems.
I did in-place upgrade to 17.10 and most of hell broke loose.

1]VMware 12 doesn't launch
So, I got version 14 and installed it. No problems with install.
However, VMWare 14 says that my cpu is not compatible.
I uninstall 14 as I know version 12 works. I install 12 back and same problem. Can't launch it.

2] KVM: /dev/kvm not found!
Since VMWare was a no go, I tried to give a shot to kvm. 
Installation (re-install) went fine. I get the message saying "qemu-kvm is already latest version.
However, I can't do anything with KVM. And I can't see /dev/kvm. (I looked for it because of Android Studio. Details below)
But I know that KVM was fine in 17.04 as I was able to run Android Studio

3]Android Studio
After upgrading to 17.10, I launch Android Studio it launches but when I try to launch "Virtual Device Manager" I get message saying "/dev/kvm" not found. And That's it, it doesn't start.

4] VirtualBox 5.0.2
This works in 17.10. I am able to run the existing VMs using VBox.

The problem is Android Studio. I need it working.

I did post a thread a while back ([https://ubuntuforums.org/showthread.php?t=2383213](https://ubuntuforums.org/showthread.php?t=2383213)) and someone had same issue and found a bug (which is confirmed but not fixed). 
Here :[COLOR=#000000] [/COLOR][https://patchwork.kernel.org/patch/9646589/](https://patchwork.kernel.org/patch/9646589/)

So, The question:
Is there anyway for me to run Android Studio (actually "Virtual Device Manager" from Studio as studio itself works).
Since, I can VMs in VBox, that is not big concern. 
I provided background because I think it's relevant.

---

### Post by cruzer001 on 2018-04-16
According to launchpad the fix has been release in kernel 4.13.0-38.43

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1741655](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1741655)

---

### Post by sp40140 on 2018-04-16
Thank you for the heads up. I didn't see that reported on launchpad.
I am currently running the latest mainline kernel which is 4.13.0.38.41. So hopefully I will receive the patch in the next update.

I will mark the thread closed once I get the update.


Cheers,

---

### Post by sp40140 on 2018-04-16
OK.
So, I got Android Studio working!
VMWare 14: still unsupported cpu. But I think this is on VMWare. There are quite a few older cpus which have this issue, some are even xenon chips.
VMWare 12: I had to uninstall and  re-install. Now I am getting different error. It still doesn't launch. But I am ok with VBox for now.

Marking it closed.

Cheers

---

