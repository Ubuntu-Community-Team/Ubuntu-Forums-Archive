---
title: "Booting 8.04 LTS kernel on 10.04 LTS does not work"
date: 2010-08-10
forum: Server Platforms
---

### Post by Fludizz on 2010-08-10
Hi,

Little over a week ago I upgraded my perfectly healthy Ubuntu 8.04LTS server to 10.04LTS. Since this upgrade my raid5 array (using mdadm) keeps breaking after any given random time and forces me to boot the system with a rescue CD in order to reassemble the drives. I've had the same issue with this system using Debian Lenny last year on the old 2.6.26 kernel. This prompted me to go back to an older kernel thus Ubuntu 8.04LTS since that one was using 2.6.24 kernel. Since 10.04 LTS is now a few months old, I figured it would be safe and since the 2.6.32 kernel is a lot more recent, I figured the bugs I experienced under Debian would've been solved. (I've filed a bug in launchpad, #613872)

How wrong I was... However, I did leave the old 2.6.24 linux image in place on the server but I cannot boot this image. It reports it cannot find /dev/md0 at boot and dumps me into the boot prompt. I checked the /proc/modules and the md modules all have been loaded, however a ls on /dev/ in this environment did not show any hard drives nor my raid set /dev/md0

Configuration of the disks:
/dev/sda1 through /dev/sdd1 as a RAID1 volume /dev/md0
/dev/sda2 through /dev/sdd2 as a RAID5 volume swap
/dev/sda3 through /dev/sdd3 as a RAID5 volume /var/


How can I get the old Ubuntu 8.04 LTS kernel to boot without being forced to downgrade the system completely to 8.04LTS ?

---

### Post by arrrghhh on 2010-08-10
I don't know if you can downgrade to 8.04... you'll probably have to do a fresh install of 8.04.

I wish I could provide some help as to how to boot this old kernel on 10.04, but it doesn't sound like a very good idea... I get why you're trying to do it tho, good luck!

---

### Post by Fludizz on 2010-08-10
A fresh install would take days due to the extend at which I configured the server... Hence being able to run the old kernel would be the quickest solution. It's not clean but it's only temporary as I arrange for the current raid set + sata controller to be replaced with a different (redundant) disk system...

I talked to someone and he suggests that I need to downgrade udev in order to get the old kernel to work again. Is this true? If I check the packages demands for the linux-image-2.6.24-28-server it does not tell me that I need a specific version, just a certain version or newer...

---

### Post by arrrghhh on 2010-08-10
It's worth a shot, just be prepared to cripple the system even futher (if that's possible).

For whatever reason, downgrading is a serious 4-letter word in the Linux world.  I've never had a clean/good downgrade experience.  I just avoid it like the plague.

With that being said, I'm not sure what would be required to get that older kernel to work.  I'll probably bow out unless I see a question I can answer :D

It may sound crazy, but have you tried a newer kernel at all?  May be easier and cause less damage...

---

### Post by Fludizz on 2010-08-10
No I haven't. This bug has been present for my system since the 2.6.26 kernel (the onde Debian Lenny used) and since it is not fixed in this kernel, I'm not really ready to believe it is fixed in a newer one as well. This bug is over a year old now (!!).

I checked the backports repository but dont seem to be able to find a newer kernel to try... The newest kernel release in there is 2.6.32 as well. (It does have 308-ec2 image version there)

---

### Post by Fludizz on 2010-08-16
No longer needed. I am no longer using mdadm so no need to downgrade the kernel anymore.

---

