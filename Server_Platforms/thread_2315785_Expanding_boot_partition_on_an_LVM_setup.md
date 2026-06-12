---
title: "Expanding boot partition on an LVM setup?"
date: 2016-03-02
forum: Server Platforms
---

### Post by cincibluer6 on 2016-03-02
So apparently my /boot partition is full. This is preventing me from upgrading, removing, etc. There are plenty of linux-images in there that I would like to get rid of but apt-get/dpkg complains when I even try to do that. I can't do apt-get -f install to fix the unmet dependencies, etc. Nor does apt-get autoremove solve my issues.

So I'm kinda stuck since nothing else seems to work. I was going to just resize boot to be bigger which would allow it to install what is needed and then I could remove unnecessary kernels, etc. But on an LVM platform, booting into a live CD doesn't let me just use gparted to manage it.
I found this- [https://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume](https://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume) which might work.

My question is- am I looking at this all wrong? Is there an easier way to get where I'm going? Just need to get boot some more space so I can do what I need to or somehow remove those excess kernel images.
On that point too- is it normal to have it stack all those images? I thought it always kept at max like 3. I'm not sure if I set this up with unattended upgrades or not if that makes a difference.

---

### Post by darkod on 2016-03-02
I agree you should expand /boot because if you used the guided method to install with LVM it creates very very small /boot. Maybe that was warranted in the early years when disks were much smaller, but these days I am surprised no one has modified this guided install behavior to create at least 1GB /boot.

Anyway, if you want to get apt-get working first and create some empty space, you can. Check all the kernels you have installed, go into the /boot folder and delete with sudo rm the files you need to delete to create free space. When you have about 75-100MB free you can try the apt-get install -f and it will work. After that standard apt-get will work too.

Just be careful not to delete the current running kernel. :)

As for expanding /boot, that really depends on your layout and usage. I assume you have sufficient free space into the LVM. But the process would be risky. You will need to create unpartitioned space right after the /boot partition. That means moving the start point of the second partition which is the PV for the LVM.

I suggest you only clean up /boot right now, and continue doing that regularly. And then take your time investigating and planning how to expand /boot.

---

### Post by cincibluer6 on 2016-03-02
Sounds good. I didn't know I could just remove the kernels using the terminal. Figured the system (apt-get or other) would throw a fit.
I'll try that and let you know. Thanks mate.

---

### Post by darkod on 2016-03-02
It's not the recommended way to remove kernels, but it's the only way in your situation. :)

Actually, some months ago I was helping a friend in exactly the same situation. If I remember it correctly, instead of risking messing up the server by repartitioning, I think I only copied the /boot content into the LVM and disabled the /boot entry in /etc/fstab. The risk was bigger because I was doing it remotely over ssh and there was no way to go and sit in front of the server if it doesn't boot.

If your server is at home/work, you can at least sit in front of it in an emergency.

The thing is that years ago LVM needed the boot files to be outside so it can boot. Now days that is no longer a requirement. But the ubuntu server guided method still installs separate /boot, and a very small one. So I think you can try what I explained above.

But you have to be careful when copying, don't forget that /boot is separate. The procedure would basically be:
1. Unmount /boot (yes, you can do that with the OS running)
2. There will be an empty folder already in your / partition named boot. If not, create it. Mount your separate partition to any temp mount point (like /mnt).
3. Copy/rsync the content of that temp mount point to /boot (because you unmounted the separate /boot, now /boot will mean the folder on /)
4. Edit /etc/fstab so that the separate /boot doesn't get mounted on boot. Reboot and keep fingers crossed. :)

As I said, if you have the server accessible the risk is smaller because you can work on it directly with keyboard and monitor. But if it's important production server be careful and it wouldn't hurt to test the approach in a test VM first. And have next to you a Desktop Live DVD or USB stick, so you can boot in live mode and work if necessary. :)

---

### Post by cincibluer6 on 2016-03-02
I see exactly what you're saying. I like how you approached it. And this is production (just IPAM but production nonetheless) but it is a VM so even "sitting in front of it" isn't in front of it. Haha
Removing the kernel images (and associated files for each) worked like a charm. I upgraded to the latest kernel and booted and since that's good, I went ahead and cleared the rest out as well (I know, I know, I should leave at least one backup kernel image.)

I will probably make a snap of the machine and then try to move boot to the LVM. If it doesn't go to plan, I can revert without pain. I assume too that you edited fstab to point to the new location? Or does it find it automatically since it's on root?
Thanks so much for your help. Nice to have everything working again.

---

### Post by darkod on 2016-03-02
Yes, because boot will be standard folder on / and you already have a mount point for root, no need to do any action. Just to prevent the /dev/sdXX partition mounting as /boot because then the files on that partition (you current boot) and the files in the root (the new boot) will clash. That's why you only need to comment out the existing /boot mount entry.

---

### Post by oldfred on 2016-03-02
There are a couple of bug reports on issue.

[https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1357093](https://bugs.launchpad.net/ubuntu/+source/unattended-upgrades/+bug/1357093)
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1054927](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1054927)
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1389620](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1389620)

And part of issue is with UEFI and secure boot, you may get multiple versions of same kernel, signed & unsigned. So then it fills up twice as fast.

---

### Post by darkod on 2016-03-02
In general I don't think it's bug related. At least not the cases I've seen, there were no multiple files, etc... The main problem is that the guided LVM method during installation creates approx 270MB separate /boot partition. Which is silly small compared to today's HDD sizes.

That would barely fit 4-5 kernels and since most people are not cleaning up the kernels too much, and are not even aware of this /boot size (they selected guided method and it gives no info on the partition size during install), this is what happens...

The method shuold be modified to create at least 1GB or 2GB /boot, if any...

---

### Post by ian-weisser on 2016-03-02
Accumulating kernels is fixed in 16.04. Unattended-upgrades will automatically remove old kernels...unless headers or some other dependecy ineligible for autoremove is installed.

---

### Post by cincibluer6 on 2016-03-03
Awesome. That is great news. Only a month or so to go too.

---

### Post by darkod on 2016-03-03
For clean installs yes, but if you are doing online upgrade note that you will not receive the message for do-release-upgrade until 16.04.1 which is expected sometime August. You could upgrade sooner but people usually tend to wait until the .1 anyway, and the automatic message shows up then.

---

