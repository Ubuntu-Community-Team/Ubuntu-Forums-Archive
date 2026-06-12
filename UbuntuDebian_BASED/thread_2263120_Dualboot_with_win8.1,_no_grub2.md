---
title: "Dualboot with win8.1, no grub2"
date: 2015-01-29
forum: Ubuntu/Debian BASED
---

### Post by washichi on 2015-01-29
Hi,
I know this question is asked many times, but I can't solve it with the given answers 
(and if I try too much without knowing what I'm doing I will make it worse :P)
I hope you guys can help me now I post my own grub-repair log.

I have windows 8.1 installed, and want to dualboot it with elementeryos,
I created a, logical partition (50gb), then install elementeryOS from my usb, I selected "install alongside"
so far no problems, a installation without any problems.
but when I reboot my laptop I'm not seeing the grub2 bootloader.
with grub boot repair liveCD I can't install it.

here is the log from the ubuntu-repair-cd: [http://paste.ubuntu.com/9938930/](http://paste.ubuntu.com/9938930/)
and here a screenshot of my partitions (gparted): [http://i.imgur.com/ZedKvyS.jpg](http://i.imgur.com/ZedKvyS.jpg)

---

### Post by yancek on 2015-01-29
The boot repair output shows you are using the Legacy MBR BIOS rather than UEFI/GPT.  You have 2 windows partitions at the beginning of the drive.  The first might be your boot partition and the second much larger probably contains the windows system files.  The reason you can't boot Elementary is because you have windows boot code in the master boot record of your hard drive.  A default windows installation is incapable of recognizing much less booting a Linux operating system.  Your options are to either obtain some third party software to install on windows which will enable booting Linux, or install the Grub bootloader to the master boot record of the drive which you can do with the boot repair medium.

---

### Post by washichi on 2015-01-29
Thank you yancek!
with the ubuntu boot-repair cd I could only install grub2 to sda5.
and what you said is right:
sda1 = windows boot
sda2 = windows8.1 installation + data
sda3 = elementeryOS (sda5 = elementeryOS sda6 = swap partition)

so I have to install Grub to my sda1 I guess? but I can't do that with boot-repair :(.
is there another tool that might work?

---

### Post by oldfred on 2015-01-29
Moved to Other OS sub-forum.

You install to sda, or the MBR of sda which is not any partition. Partitions are sda1, sda2 etc. 
And you never install grub to a NTFS partition as that breaks Windows.

---

### Post by ajgreeny on 2015-01-29
No, you do not put grub into sda1, nor into any partition, you need it in the root of a disk, in your case /dev/sda.  See if you can do that with Boot-Repair.

Is your ElementaryOS based on Ubuntu 12.04 as it appears from your pastebin link?  It may be better to use 14.04 as it seems to work much better with Win 8.1, or it does with UEFI, though that may not be so when using legacy BIOS and MBR.

---

### Post by washichi on 2015-01-29
> **oldfred said:**
> Moved to Other OS sub-forum.

You install to sda, or the MBR of sda which is not any partition. Partitions are sda1, sda2 etc. 
And you never install grub to a NTFS partition as that breaks Windows.

thanks for moving.
I tried dualbooting win8.1 with official ubuntu, but that had the exact same result.

I think my laptop is using the windowsbootloader, but it should use the grub2 bootloader,
but I can't install my grub2 with ubuntu-boot-repair.
If I look in the ubuntu pastebin I see that grub2 is installed on sda5.
How can I get sda5 as my bootloader?


edit:
thanks for the advice , I will try it again with the latest ubuntu version: 14.04.

---

### Post by yancek on 2015-01-29
Your windows installation seems to be using Legacy MBR to boot rather than the UEFI/GPT standard with windows 8.  In that case, you need to install Grub2 to /dev/sda which will put it on the master boot record.  The link below explains several method including using the boot repair.  Almost all the Grub files will be on your partition which is sda5 but you need some of the code in the mbr which your boot repair output specifically indicates is windows code. 

 [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by washichi on 2015-01-30
> **yancek said:**
> Your windows installation seems to be using Legacy MBR to boot rather than the UEFI/GPT standard with windows 8.  In that case, you need to install Grub2 to /dev/sda which will put it on the master boot record.  The link below explains several method including using the boot repair.  Almost all the Grub files will be on your partition which is sda5 but you need some of the code in the mbr which your boot repair output specifically indicates is windows code. 

 [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

I tried to install elementeryOS again, and now I could choose where I want to install the bootloader.
here you can see my 4 options (where my mouse is) : [http://i.imgur.com/nPRwiH5.jpg](http://i.imgur.com/nPRwiH5.jpg)
this is how I installed it: [http://i.imgur.com/yhSyN2o.jpg](http://i.imgur.com/yhSyN2o.jpg)
but still no grub bootloader.

I also tried to add it manually to my mbr bootloader with easyBCD, but that didn't work.

---

### Post by oldfred on 2015-01-30
Grub2 does not recommend installing to a partition boot sector. It is designed to boot from MBR if using BIOS. Again the MBR is sda, boot sector of the drive sda, not sda5 or any other partition's boot sector.
EasyBCD is a a work around for Windows as Windows will only boot Windows. It requires grub to be installed to a partition boot sector and then you set BCD to load grub4dos to chain load to grub2 in partition boot sector.

---

### Post by washichi on 2015-01-30
I installed ubuntu 14.04 , it installed correctly, on the same partitions as elementaryOS, the bootloader on SDA
and it booted with grub!
but my pc booted directly to ubuntu, no dualboot screen.
It's more than with elementaryOS, but still no dualboot :(

---

### Post by washichi on 2015-01-30
UPDATE

It's kinda working now.
I installed the latest ubuntu version, like I did every time:
50gb logical ext4, mount as /
It installed good, and I booted into ubuntu with grub, but no option to choose windows.
inside ubuntu I downloaded boot-repair, I did the recommended repair and followed the steps 
(it deleted the installed grub2 and installed it again on SDA)
then I did a reboot and I booted into grub2 with windows/ubuntu option :).
strange thing: 
in grub2 i have a windows bootloader on /sda1 and /sda2

the problem was that my boot-repair cd didn't work (maybe older version)
when installing boot-repair in ubuntu it solved my problem.

now I need to install elementery os instead of ubuntu.
I will post my result here.

---

### Post by Cavsfan on 2015-01-30
> **oldfred said:**
> Grub2 does not recommend installing to a partition boot sector. It is designed to boot from MBR if using BIOS. Again the MBR is sda, boot sector of the drive sda, not sda5 or any other partition's boot sector.
EasyBCD is a a work around for Windows as Windows will only boot Windows. It requires grub to be installed to a partition boot sector and then you set BCD to load grub4dos to chain load to grub2 in partition boot sector.

But, what about this: [http://ubuntuforums.org/showthread.php?t=2262516&page=2&p=13216857#post13216857](http://ubuntuforums.org/showthread.php?t=2262516&page=2&p=13216857#post13216857) ?

I was hoping you would see that thread Oldfred, although I know you are quite busy. :)

---

### Post by oldfred on 2015-01-30
If installing more than one Linux with grub2, you have to keep track of which install is in MBR. With BIOS you only have one MBR per hard drive, so if more than one install, only one controls boot. Grub2 will boot all other Linux installs, so second grub can be installed to a partition only as a throw away, if you want first install in control. Installer seems to not have an option to not install grub to MBR or partition.

I normally boot sdc, so I just let every test install default to sda. But that is part of the advantage of multiple drives.

---

### Post by Cavsfan on 2015-01-30
> **oldfred said:**
> If installing more than one Linux with grub2, you have to keep track of which install is in MBR. With BIOS you only have one MBR per hard drive, so if more than one install, only one controls boot. Grub2 will boot all other Linux installs, so second grub can be installed to a partition only as a throw away, if you want first install in control. Installer seems to not have an option to not install grub to MBR or partition.

I normally boot sdc, so I just let every test install default to sda. But that is part of the advantage of multiple drives.

My mind is a haze today so forgive my ineptitude. I only have one drive so I would install to the MBR as I have always done?
Precise with grub 1.99 is on a physical partition but I use Trusty for my grub which is on /dev/sda6. 
So when I install another system I boot into there and do **sudo grub-install /dev/sda** and it's done.

That's the way Ranch Hand taught me and I was confused with installing to a partition vs the drive.

---

### Post by oldfred on 2015-01-30
The only disadvantage of installing grub to MBR for every install is that on major grub updates it will reinstall to the MBR. So you have to reboot into your main install and reinstall that copy to grub to MBR. Not really a big deal, but you can avoid that if grub is not set to reinstall into MBR.

You can also do this:
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

Then if your second install is also installing to the MBR and you do not want it to reinstall. Just uncheck everything. Then the above command will show a blank for drive to install into.


        
 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

---

### Post by Cavsfan on 2015-01-30
> **oldfred said:**
> The only disadvantage of installing grub to MBR for every install is that on major grub updates it will reinstall to the MBR. So you have to reboot into your main install and reinstall that copy to grub to MBR. Not really a big deal, but you can avoid that if grub is not set to reinstall into MBR.

You can also do this:
 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

Then if your second install is also installing to the MBR and you do not want it to reinstall. Just uncheck everything. Then the above command will show a blank for drive to install into.


        
 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

Thanks you for that clear explanation! 
I think I am beginning to understand it a little better. 
So, If I install my grub on /dev/sda6 with the sudo dpkg-reconfigure grub-pc command it will stay on that partitition I'm guessing?

I see at the bottom of that thread I did not pay attention to the part about sudo dpkg-reconfigure grub-pc like I should have.

I might have known how to do this by now if I had.

Thanks again!

Edit: Thanks for mentioning the dpkg-reconfigure grub-efi-amd64 command too as I hope to one day have a newer system with windows 8.1 or maybe 10 by the time I get there.

---

### Post by washichi on 2015-01-31
Thank you all for your help and information,
I have it working now.

after I had win8.1 + ubuntu 14.04 dualboot, I deleted ubuntu and installed Elementatery OS again 
(at this point my laptop isnt booting with grub, so It boots to windows or grubresque)
I booted into a livecd session of elementaryOS, used this command: sudo grub-install /dev/sda  
but that wasnt working cause I was in a live session, so I used this tutorial to mount the right things:
[community.linuxmint.com/tutorial/view/245]("http://community.linuxmint.com/tutorial/view/245")
then I did a reboot and it worked.

conclusion:
- Ubuntu 14.04 could write grub to dev/sda with boot-repair
- ElementaryOS cant write grub to dev/sda with boot-repair, you have to do it manually

This is proberbly not the best way to dualboot, but I dont have that much experience with ubuntu,
so for now Im happy with the result :p.
thanks to all of you!

---

