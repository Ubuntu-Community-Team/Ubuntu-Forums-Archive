---
title: "Every time new grub version is installed(update)-grub auto-installed in /dev/sda MBR"
date: 2013-11-23
forum: Ubuntu Development Version
---

### Post by NikTh on 2013-11-23
This is the second time. First time I wasn't sure, but now I think I am. 

**Problem **

Every time when a new version of grub is installed through the update procedure (sudo apt-get update; sudo apt-get dist-upgrade) , then grub is auto-installed in the MBR of /dev/sda.

**What I expected **

I have another version of GRUB installed in /dev/sda, that relies in Ubuntu 13.04 (13.04 is installed in a partition of /dev/sdb). I expected that this version of GRUB will remain after a 14.04 system update. Ubuntu 14.04 is installed in a partition of /dev/sda. 

**How to reproduce it**

I understand that this can be a bit difficult to reproduce, as is only happens when a new version of GRUB is available and installed through the system update procedure. 
Install another grub of another Linux distribution (in my case is Ubuntu 13.04) in MBR of /dev/sda and update the Trusty Tahr. If a GRUB update is available, probably in next reboot you will see this issue. 

Maybe after all this is not an issue, but a normal behavior that I didn't know about ? 

Any logs/or commands output/ you might want to examine, let me know.

Thanks in advance.

---

### Post by kansasnoob on 2013-11-23
When you installed Trusty you probably chose to install grub to /dev/sda, or if you used any installation method other than "Something else" the installer just automatically does that. So now every time update-grub is run grub-pc is once again restored to it's original location.

To fix that run this command:

```
sudo dpkg-reconfigure grub-pc
```

Then use the tab and enter keys to select OK on these 3 screens:

[ATTACH=CONFIG]248022[/ATTACH]

[ATTACH=CONFIG]248023[/ATTACH]

[ATTACH=CONFIG]248024[/ATTACH]

Then you'll see a screen similar to this:

[ATTACH=CONFIG]248025[/ATTACH]

Use the space bar to select or deselect the appropriate devices, then tab and enter to select OK. Then it should be fixed :)

---

### Post by grahammechanical on 2013-11-23
The Ubiquity installer defaults to installing Grub into the MBR of sda. I have been caught out by this. Also keep in mind that the last version of Linux to be installed will overwrite any existing MBR.

I have two hard disks with multiple versions of Ubuntu so I frequently have to put my preferred Ubuntu back in charge of the MBR and the Grub boot menu. I do this by loading into my preferred Ubuntu and running

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

or

```
sudo grub-install /dev/sdb
```

Depending upon which hard disk has boot priority at the time and which disk the Ubuntu I am running is loaded on. And when I put in another install of Ubuntu I make sure at the partitioning screen that Grub is going to be installed into the MBR of the hard disk that I want it to.

I also found out recently that Windows 8 will put its boot loader into the MBR of every hard disk. This is worse as the Microsoft Boot loader will never offer an option to boot into Linux.

Regards.

---

### Post by NikTh on 2013-11-23
> **grahammechanical said:**
> 

I have two hard disks with multiple versions of Ubuntu so I frequently have to put my preferred Ubuntu back in charge of the MBR and the Grub boot menu. I do this by loading into my preferred Ubuntu and running

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```
or
```
sudo grub-install /dev/sdb
```

Depending upon which hard disk has boot priority at the time and which disk the Ubuntu I am running is loaded on. And when I put in another install of Ubuntu I make sure at the partitioning screen that Grub is going to be installed into the MBR of the hard disk that I want it to.

I also found out recently that Windows 8 will put its boot loader into the MBR of every hard disk. This is worse as the Microsoft Boot loader will never offer an option to boot into Linux.

Regards.

That is exactly what I did. Specifically I installed my preferred GRUB with this command 
```
sudo grub-install --recheck /dev/sda
``` 

Probably is what @kansasnoob says here. 

> **kansasnoob said:**
> When you installed Trusty you probably chose to install grub to /dev/sda, or if you used any installation method other than "Something else" the installer just automatically does that. So now every time update-grub is run grub-pc is once again restored to it's original location.
Yes that is correct. 
> **kansasnoob said:**
> To fix that run this command:
```
sudo dpkg-reconfigure grub-pc
```
........
Use the space bar to select or deselect the appropriate devices, then tab and enter to select OK. Then it should be fixed :)

So I have to reconfigure grub and make it like.. unusable. I have to select to install it on some partition(number) rather to a disk. So next time that GRUB will be installed through the update procedure it will not replace my preferred GRUB. 

But I didn't know that it was an expected behavior. 

Thanks for the help. 

:)

---

### Post by Cavsfan on 2013-11-23
I don't think there is any way to prevent this from happening. Everytime I install a new ISO I have to turn my 1TB USB drive /dev/sdb off or else it will just hang during installation I believe even before it asks where I want to install.
(I believe the need to turn off my USB drive started with Quantal or maybe before that, but it is a neccessity.)
Then it installs on /dev/sda just fine.
I have 6 Linux systems installed and when any of them get an update to grub, grub-install /dev/sda gets executed installing the grub on that partition.

I then have to boot into the partition that I want it on and re-install it there. I believe that is a normal function of a grub update. One of the things it does is install grub on the partition it is being updated on.
I installed Trusty, customized the grub menu, rebooted and everything looked good. So I went to Raring and installed my grub there and then came back to Trusty. So, what happens? Trusty gets a grub update to 2.00-20 and it gets installed on the Trusty partition again.
This time I just left it there because I *believe* I know how to fix it if I need to if something should go seriously wrong on Trusty.

It will do that every time. Or at least that has been my experience.

---

