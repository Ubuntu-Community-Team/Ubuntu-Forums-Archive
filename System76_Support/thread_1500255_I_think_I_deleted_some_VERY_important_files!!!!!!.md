---
title: "I think I deleted some VERY important files!!!!!!"
date: 2010-06-02
forum: System76 Support
---

### Post by bix15 on 2010-06-02
I am the proud owner of a system76 Pangolin Performance. I've owned it since around November of 2009. It shipped with Ubuntu 9.10 installed.

Just today I decided to upgrade to 10.04 using the update manager. I was prompted through a few simple things. After everything was done and installed it asked me if I wanted to remove some out-of-date files and packages, so I just thought "Well if they are removed, naturally, up-to-date versions of those files and packages should be installed in place of them."..... I believe I was wrong because...

#1 These files I believe made up the kernel or Grub (with names such as 'Linux image       2.36-Generic')

#2 When I restarted my computer it ran a memory test and it kept repeating itself

#3 I get a screen that says "Operating system not found"

So here I am, a brand new Linux user, and I have no clue what to do next. I didn't make a backup of anything because I figured if I really screwed up bad enough I would just do a clean install of 10.04. 
Is there any way that I could possibly fix this without having to do a clean install myself and configure a bunch of drivers!! System 76 shipped it with drivers already installed which was REALLY nice!!! 

Any help would be greatly appreciated!

---

### Post by Ozymandias_117 on 2010-06-02
Drivers are all in the Kernel. The only ones you'd have to get are Graphics and sometimes Wireless.

You can boot up to a liveCD to make sure there isn't any hardware that doesn't work properly without some weird module, but coming from System76, I would expect everything to work well. (If it's not an Intel graphics card, you will have to get Kernel modules for it... But other than that, you're good.)

If you get a liveCD you can try the following procedure to possibly fix your current installation.

Boot to a liveCD, then do this:

Please note you will have to use ```
sudo fdisk -l
``` (That is a lowercase L) to figure out the correct /dev/sd* for the second command.

```

sudo -i
mkdir /mnt/root
mount -t ext4 /dev/sd* /mnt/root
mount --bind /proc /mnt/root/proc
mount --bind /dev /mnt/root/dev
chroot /mnt/root
aptitude update
aptitude full-upgrade
update-grub
exit

```
then reboot

---

### Post by bix15 on 2010-06-02
Yeah thanks! I'll try that...
To correct myself earlier...when I boot from my hard drive, I get a blue screen that tests my memory. I waited for about 30 minutes until it was done and it appeared to be going in a loop so I can't get past it.

I will probably end up doing what you said I should do.
Thanks a LOT!! I was geekin' out there for awhile but I'm 99% sure I'll be able to fix it

---

### Post by drewbenn on 2010-06-03
> **bix15 said:**
> Is there any way that I could possibly fix this without having to do a clean install myself and configure a bunch of drivers!! System 76 shipped it with drivers already installed which was REALLY nice!!!

I don't have any advice for restoring your system, but if you do a clean install of 10.04, you should know that it is trivial to reinstall the System76 drivers!  Go read [http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System) .  You'll just need to download and run one file to install them, then go to the driver and click 'Restore', and you'll have everything System76 provides.

---

### Post by betrunkenaffe on 2010-06-03
> **bix15 said:**
> Yeah thanks! I'll try that...
To correct myself earlier...when I boot from my hard drive, I get a blue screen that tests my memory. I waited for about 30 minutes until it was done and it appeared to be going in a loop so I can't get past it.

I will probably end up doing what you said I should do.
Thanks a LOT!! I was geekin' out there for awhile but I'm 99% sure I'll be able to fix it

As stated, best bet would be a restore, make sure you set your /home partition and **DO NOT** format it during the install.

That memcheck is always looping and will never go anywhere except to perform memchecks.

---

### Post by re1d on 2010-06-16
> **betrunkenaffe said:**
> As stated, best bet would be a restore, make sure you set your /home partition and **DO NOT** format it during the install.

That memcheck is always looping and will never go anywhere except to perform memchecks.

I'd agree that restoring is the best solution. Just after I purchased my Pangolin, I hosed it due to a dumb mistake. Turned out the best solution was to restore to a fresh system. It was easy, didn't take long, and as noted restoring the System76 drivers is trivial. It's a nice system they've worked out here.

So if you haven't solved the problem yet, restore - I think you'll be a pretty happy camper. It's a new set of brains!

---

### Post by Bluebearbevis on 2010-06-16
Hello,

I too purchased my Pangolin in Nov. of 2009.  I don't know if you noticed but even though it came with 9.10 it still had the old ext3 file system.  I would recommend a fresh install of 10.04.  Then there are earlier threads about having to enable proposed and backport repositories, which I did.  6 weeks now and this Lynx runs like a Cheetah and purrs like a kitten.  I don't know if the proposed and backport thing is still necessary because it delt with a kernel we have moved beyond now anyway.  I left mine enabled as it makes me feel bold and adventurous, but I digress...if you do a fresh install make sure to completely replace the old one.  Anyway, hope that helps.

Richard

---

