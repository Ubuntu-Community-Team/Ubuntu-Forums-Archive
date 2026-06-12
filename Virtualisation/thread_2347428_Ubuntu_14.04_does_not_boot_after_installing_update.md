---
title: "Ubuntu 14.04 does not boot after installing updates"
date: 2016-12-24
forum: Virtualisation
---

### Post by tbsflk on 2016-12-24
Hi,

I have an Ubuntu 14.04 installation running in VirtualBox on a Windows 10 machine. I've been using it for over a year now and never had any problems with it.

Today, Ubuntu installed a couple of software updates, which failed with an error I cannot remember. I tried to restart the machine and since then, I see the following when trying to start the system:
```
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

I'm not a regular Linux user and the message doesn't tell me anything. So far, I tried to use Boot-Repair to solve that issue, but the Recommended Repair did not help. Here's the [BootInfo]("http://paste.ubuntu.com/23680299/").

What should I do to get the system running again?

EDIT:
I remember that after the failed software updates, I got "file system is read-only"-errors in the terminal, e.g. when using ls. That's why I tried to restart then.

---

### Post by Irihapeti on 2016-12-25
*Thread moved to **Virtualisation**.*

---

### Post by DuckHook on 2016-12-25
Welcome to the forums, tbsflk

The easiest way to solve any VM issue in VB is to roll back to a known good snapshot. Do you have any such snapshot of your VM?

Do you have important data in the VM? If so, do you have good backups of that data? If no backup, then I strongly advise you to copy the whole VM to either external storage or a NAS.

The following assumes you are now backed up.

If you used boot repair, then you must know how to boot to a LiveDVD ISO within VBox. Please do so again and post output of:```
df -hi
```&#8230;to show inodes used. This should be less than 100%. You do have a lot of old kernels hanging around and may have exhausted your inodes. If so, then deleting some files to free up inodes should at least allow you to boot. You can then:```
sudo apt-get autoremove && sudo apt-get clean
```&#8230;to purge old kernels and packages from your system.

If inodes are okay (you are less than 100%), you might have a corrupted file table in your VM. In the same LiveDVD session, bring up a terminal and do:```
sudo fsck -t ext4 UUID=2a0186e3-635a-4903-9261-6b95a4fc1dbc
```While I have particularized this command to check only a very specific virtual disk (the one in your Bootinfo report), it is still important to note that you must not run fsck from Windows (not really possible anyway) and especially not from a LiveDVD session on your host (your physical computer). It must *only* be run inside your VM.

The fsck command is interactive. You will have to decide on your course of action as and when it pops up a question. If you have taken all of the precautions outlined above, especially copying your VM to a safe location, then it is fine to just proceed with all fsck's recommended actions.

Let us know how it goes.

---

### Post by tbsflk on 2016-12-25
Thanks a lot for the detailed instructions, I tried the following now:

Booted with the Boot Repair ISO and opened a terminal. The output of ```
df -hi
``` is

```

Filesystem  Inodes  IUsed   IFree   IUse%   Mounted on
...
/dev/sda1   3.0M    850K    2.2M    29%     /media/lubuntu/2a0186e3-635a-4903-9261-6b95a4fc1dbc

```

So I guess the number of inodes are not the problem. I also ran the other suggested commands, which removed a few packages, but that didn't change the previous output.

Next, I ran ```
sudo fsck -t ext4 UUID=2a0186e3-635a-4903-9261-6b95a4fc1dbc
``` and it found a couple of issues (orphaned inodes and wrong inode counts), I always chose the recommend action for them. If I boot from the ISO again and rerun fsck, I can see that it is now clean, so all issues are resolved.

However, if I boot the VM normally, the see the original issue again. Any other ideas?

---

### Post by DuckHook on 2016-12-25
Try booting from the VM. But just after the VM starts, hold the <Shift> key down to bring up GRUB. Choose "Advanced options for Ubuntu" and select an earlier kernel. See if this succeeds. If not, repeat process to see if even earlier kernels will work.

If the menu comes up, also try recovery mode with the latest kernel (and earlier ones if none of above work).

If you can boot properly with an older kernel, adjust your GRUB for the time being to always show at boot and permit you the chance to select older kernel:```
sudo nano /etc/default/grub
```Change the line:```
GRUB_HIDDEN_TIMEOUT_QUIET=true
```…to…```
GRUB_HIDDEN_TIMEOUT_QUIET=**false**
```…then…```
sudo update-grub
```Every time you reboot, GRUB should now show up without having to press <Shift>.

I will be visiting the forums only occasionally through the holiday season, so hopefully, the above will at least allow you to work around the issue for the time being.

---

### Post by tbsflk on 2016-12-26
Thanks, that actually helped.

I was able to boot in recovery mode with the oldest kernel available in GRUB. Then, I ran dpkg, which I guess fixed those things that failed during the update. It generated new initrd for all kernels and I think that's what fixed my issue. I can now boot with the most recent kernel without any issues.

---

### Post by DuckHook on 2016-12-26
Congratulations. Especially on figuring out dpkg. If you don't mind, please describe your fix in detail for the future benefit of searchers and those who find themselves in a similar spot. It would really help out the community. 

I would also just note two more things:

Taking a snapshot of your current working system will save you all this heartache in the future. If anything breaks again, you just roll back to this snapshot and everything is right again with the world. It's one of the best advantages of a VM and one that you should use. 

You may also wish to clean out your old kernels and cruft now that your system is okay again by running the autoremove/clean dual command described earlier. You really don't need *that* many old kernels laying around and their associated headers take up a lot of system resources too. Once successfully purged, take another snapshot and you will have a nice efficient system to roll back to. 

Good luck and happy Ubuntu-ing!

---

