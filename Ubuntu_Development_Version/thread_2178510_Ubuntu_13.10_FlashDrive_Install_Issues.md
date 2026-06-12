---
title: "Ubuntu 13.10 FlashDrive Install Issues"
date: 2013-10-03
forum: Ubuntu Development Version
---

### Post by trever2 on 2013-10-03
Hello all, I am 2 days new to this community and could use a lot of help figuring out how to install Ubuntu to my flash drive. I'll do my best to explain everything, and please be simple with terms since I am new. I'd rather know why something works/ doesn't work instead of just being told how to do it.

From the Beginning:
Okay, so my laptop's hard drive recently died =( so I decided that in the meantime until i can pick up another one, I'd just install ubuntu on to a flash drive. So I went on my desktop, downloaded bootice to partition my flash drive. I made two partitions because that's what it said I needed, so the first one was 2gb big for my 13.10iso file that I downloaded, and was fat32 I believe. The second one had the remaining 30gb and I ended up making it ext4.

After putting the iso on to my flash drive, I stuck it into my laptop, and began the process. Grub booted up, and I clicked install. The installation process began and everything was going fine. As I said, I had the one partition that was 30gb and ext4, and so this is where I installed the program. It took rather longer to finish installing, so I took a quick nap, and when I woke up, it said installation complete, restart. So i clicked restart, and then the screen went black and nothing happened. I decided to reboot the laptop, and when I did it jumped right into the grub. From here, it still had the 4 default options as before, run without install, install, defective, and the third one that is slipping my mind. Either way though, I was not sure if this was right because I thought it would have booted straight to the installed OS or at least given me an option on the grub.

From this point, I restarted and went to my bios and and chose which item to boot from. There were three listed. Two were the USB, i'm assuming because I had two partitions? I'm not sure. And then the last was what I believe to be individual files on the USB? But anyway, the first one would bring me back to the grub where I was confused, the second would open the files and no matter which file I chose, it would either: not work, give me a black screen,or connect me to the grub. The third option would seem like it tried to boot an OS but a message on a whole black screen would pop up saying "no OS found, please install boot disk to continue. Press any button to continue." and whatever button I pressed would just present the same message, so I'd have to shut off my computer.

If anyone could help point me to where I went wrong and how to fix it, that would be great. I've tried some other tutorials with unmounting and mounting and stuff like that, but didn't really understand what I was doing. I've tried reinstalling grub I believe, but when I typed the command in the terminal, it would say command not found.

Currently, I am on the "use without install" option, which runs just fine, except that every time I come on it's just default and doesn't save any of my changes, wireless, passwords, files, etc.

Any amount of help would be appreciated. Thanks in advance.

---

### Post by Frogs Hair on 2013-10-03
***&#8203;Moved Ubuntu +1***

---

### Post by coldraven on 2013-10-03
You cannot "just put" the .iso file onto your USB memory stick, it has to be made bootable.
In Ubuntu you can use "Startup Disk Creator" or on Mac/Windows/Linux you can use Unetbootin.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
Just today I installed 13.10 from a 1GB SD card, very handy if your PC has a card reader.
Make sure that when booting that you do not have any other USB cards/sticks or drives attached other than the one you're trying to boot from, it will probably fail to "see" the correct one.

---

### Post by hansdown on 2013-10-03
Welcome to the forum, trever2.

Could you please post which version of ubuntu you are using?

If the live usb is working, you should find 

> parted, or gparted

and take a look at your hd, to see what partions are present.

---

### Post by cariboo on 2013-10-03
Depending on how big your flash drive is, you can also install Ubuntu on it, just like you would a regular hard drive install.To do this you would need to boot from the the iso either a DVD or another flash drive, then choose the flash drive to install to.

---

### Post by trever2 on 2013-10-03
I'm sorry, I forgot to mention that I did use the startup disk creator. It extracted and all of that, and then I disconnected. If it was that anyway, wouldn't that have caused a problem right at the beginning?

And i'm not sure what else past 13.10 to say about the version I'm going with. I believe it said amd64 something or another along with it. I figured that one would work for my system since it's amd cpu 64-bit? and where do i go to see the parted or gparted?

As for devices that are showing up, there is only the 30gb partition present, which is /dev/sda2, whereas /dev/sda1 is the 2gb of fat32 that I installed the iso onto

My partition tool says Gparted i believe.

---

### Post by hansdown on 2013-10-03
> And i'm not sure what else past 13.10 to say about the version I'm going with. I believe it said amd64 something or another along with it. I figured that one would work for my system since it's amd cpu 64-bit? 



My bad.

Sometimes I don't see the forest because of all the darn trees.

I apologize in advance, but there is one thing I'm a bit thick on:

Are you attempting to install on the same HD, that you stated is failing, or did you install a new one?

---

### Post by trever2 on 2013-10-03
No, I am trying to install all of it to a usb flash drive for now until I get another hard drive.

---

### Post by hansdown on 2013-10-03
> Currently, I am on the "use without install" option, which runs just fine, except that every time I come on it's just default and doesn't save any of my changes, wireless, passwords, files, etc.

O.K.

To make it pesistant, I would advise using 

> unetbootin

as opposed to  startup disk creator

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by skidschool on 2013-10-03
I installed the 12.04 updates this morning & lost my Wireless & Graphic drivers, I had to reinstall 12.01 to get back online. I've been using Ubuntu for 5 or 6 years on 3 laptops & never had any issues. Will this be an issue with 13.01 ??

---

### Post by trever2 on 2013-10-04
> **hansdown said:**
> O.K.

To make it pesistant, I would advise using 



as opposed to  startup disk creator

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)


Startup disk creator gave me the option to make it persistent though? and I assigned 3gb for it. Are you saying use that one because you didn't think the other had the option or because you're doubting that it worked correctly?

---

### Post by kurt18947 on 2013-10-04
If you're doing a 'real' install on a USB drive, you don't want anything to do with persistence.  Persistence is used as part of a live install so a live install 'remembers' things like networks, data files and such.  I believe the O.P. want to install to a flash drive just as it's a hard drive.  I've done it and you don't use either Startup Disk Creator or Unetbootin.  Startup Disk Creator and Unetbootin are used to created a live CD/DVD/USB.  As others have said, you do need to boot a live install device, either CD/DVD or USB.  If you're using a desktop and want to make sure you don't bugger your hard drive up, you could unplug any hard drives.  Then boot a live install, insert the target USB drive and click the 'install' button on the live session.  The installer should see the target flash drive.  I don't know that it's necessary to first partition the target flash drive, I suspect the installer would do that for you once you tell it where to install and which file system to use.  You're going to install to the target USB drive just as if it were a hard drive.  Yes, it takes quite some time; writing to USB drives generally  takes much longer than reading from them.  

I don't generally install a swap partition on a flash drive - or a hard drive for that matter.  My understanding is that swap partitions 'wear' flash memory cells quite a lot and if your target machine has 2 GB. RAM or more, you can probably get along without a swap partition unless you have large or several programs open simultaneously.  I don't have one on a laptop with 2GB. RAM and so far haven't had an issue.  If your intended machine has 1.5 GB. RAM or less, you probably should have swap.  You could consider a swap FILE rather than a swap partition if you feel like it.  As far as I know (no expert here) a swap file will function very similarly to a swap partition except a swap file won't support hibernation.  To hibernate a system, you need a separate swap partition.  Suspend should work fine though, it doesn't write memory contents to a separate partition like hibernate does.  

The only real potential "Oh Crap!" opportunity is either installing to a hard drive you didn't intend or install to the proper flash drive but install GRUB to the hard drive.  If the hard drive(s) are unplugged that risk is eliminated.  One real benefit to a 'real' install over a live install is the ability to update.  I've tried updating live USBs and it may appear to work once or twice.  Eventually though, updating has killed every LiveUSB I've tried it with.  Good luck, it's pretty simple if you're familiar with Ubuntu's installer.

Oh, one other thought.  There used to be a bug with Unetbootin at least.  If you booted a live device created with Unetbootin (don't know about USB Creator) expecting it to install, it wouldn't.  You had to select 'try without installing' then once loaded, select the 'install' desktop icon.  Then it would install.  I don't know if this bug was ever squashed or not.

---

### Post by trever2 on 2013-10-04
> **kurt18947 said:**
> If you're doing a 'real' install on a USB drive, you don't want anything to do with persistence.  Persistence is used as part of a live install so a live install 'remembers' things like networks, data files and such.  I believe the O.P. want to install to a flash drive just as it's a hard drive.  I've done it and you don't use either Startup Disk Creator or Unetbootin.  Startup Disk Creator and Unetbootin are used to created a live CD/DVD/USB.  As others have said, you do need to boot a live install device, either CD/DVD or USB.  If you're using a desktop and want to make sure you don't bugger your hard drive up, you could unplug any hard drives.  Then boot a live install, insert the target USB drive and click the 'install' button on the live session.  The installer should see the target flash drive.  I don't know that it's necessary to first partition the target flash drive, I suspect the installer would do that for you once you tell it where to install and which file system to use.  You're going to install to the target USB drive just as if it were a hard drive.  Yes, it takes quite some time; writing to USB drives generally  takes much longer than reading from them.  

I don't generally install a swap partition on a flash drive - or a hard drive for that matter.  My understanding is that swap partitions 'wear' flash memory cells quite a lot and if your target machine has 2 GB. RAM or more, you can probably get along without a swap partition unless you have large or several programs open simultaneously.  I don't have one on a laptop with 2GB. RAM and so far haven't had an issue.  If your intended machine has 1.5 GB. RAM or less, you probably should have swap.  You could consider a swap FILE rather than a swap partition if you feel like it.  As far as I know (no expert here) a swap file will function very similarly to a swap partition except a swap file won't support hibernation.  To hibernate a system, you need a separate swap partition.  Suspend should work fine though, it doesn't write memory contents to a separate partition like hibernate does.  

The only real potential "Oh Crap!" opportunity is either installing to a hard drive you didn't intend or install to the proper flash drive but install GRUB to the hard drive.  If the hard drive(s) are unplugged that risk is eliminated.  One real benefit to a 'real' install over a live install is the ability to update.  I've tried updating live USBs and it may appear to work once or twice.  Eventually though, updating has killed every LiveUSB I've tried it with.  Good luck, it's pretty simple if you're familiar with Ubuntu's installer.

Oh, one other thought.  There used to be a bug with Unetbootin at least.  If you booted a live device created with Unetbootin (don't know about USB Creator) expecting it to install, it wouldn't.  You had to select 'try without installing' then once loaded, select the 'install' desktop icon.  Then it would install.  I don't know if this bug was ever squashed or not.

Thank you so much for your detailed response and time. I was beginning to think that there was no real way around it besides using two flash drives like you mentioned. I just got a hold of a second one and I trust that it will work when I get around to using it. I +1'ed your post and will mark this thread as solved.

---

