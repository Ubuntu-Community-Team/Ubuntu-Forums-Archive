---
title: "love ubuntu but windows xp is still far better !"
date: 2008-06-14
forum: Testimonials &amp; Experiences
---

### Post by lman_271860 on 2008-06-14
i know this post will be a red rag to a bull but it is designed to GET A RESPONSE !

i have one and only one problem with UBUNTU and it is that my USB hard dive does not work and many other people have the same problem which appears to be falling on deaf ears.

if this operating system is going to be a contender against microsoft then basic things have to work out of the box and this is very basic.

i have now reloaded xp back only laptop and have a dual boot with ubuntu
my usb hard drive works with xp with no problems at all even without any service packs

it also used to work with gutsy with no problems at all

i have only been playing with linux for a couple of months and initially thought it was i viable alternative to windows but at the moment, for me, i consider it as a bit of a play thing and when serious work needs to be done i go back to xp

here is the kernel log, as if it is required !
and obviously lsusb sees the drive

i think for the operating system to fulfill it's destiny as the natural operating system on every machine in the world the a bloody usb hard drive should work !

thanks in advance





Jun 13 17:55:17 victor-laptop kernel: [  478.079888] USB Mass Storage support registered.
Jun 13 17:55:17 victor-laptop kernel: [  478.080128] usb-storage: device found at 3
Jun 13 17:55:17 victor-laptop kernel: [  478.080131] usb-storage: waiting for device to settle before scanning
Jun 13 17:55:23 victor-laptop kernel: [ 1202.660543] usb-storage: device scan complete
Jun 13 17:55:29 victor-laptop kernel: [ 1208.272579] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Jun 13 17:55:39 victor-laptop kernel: [ 1227.965007] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Jun 13 17:55:39 victor-laptop kernel: [ 1228.213048] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Jun 13 17:55:50 victor-laptop kernel: [ 1238.457555] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Jun 13 17:55:50 victor-laptop kernel: [ 1238.590079] scsi 0:0:0:0: Device offlined - not ready after error recovery

---

### Post by ChameleonDave on 2008-06-14
Your title is just trolling.  I won't be helping you until you change it to something relevant to your query.

---

### Post by ad_267 on 2008-06-14
> i know this post will be a red rag to a bull but it is designed to GET A RESPONSE !

I think you're less likely to get a response with this attitude. I can't help you much but I would recommend rewording your post so that others feel like helping you. I hope you realise that 99.9% of the time a USB drive should work without any fuss and without requiring you to "restart your computer to take advantage of the new hardware."

---

### Post by lman_271860 on 2008-06-14
unfortunately the title will remain, from my perspective as beginner it is true

i plug in my usb hard drive and it works !

you are obviously and expert and will probably be able to solve the problem with some terminal incantation, but this is just a usb hard drive why should it not work ?

DAVE if you are willing to help great, let work together to solve the problem

i have seen numerous posts about this and it's still does not work

the problem needs to be solved for all users

as the usb drive is working under xp SO I CAN POST THE FOLLOWING INFORMATION

---

### Post by lswest on 2008-06-14
i agree with the others, this is no way to get a response to your problems.  Descriptive titles of the problems and not trolling titles will provoke users to respond, as they can judge if they can offer help or not without having to read all the posts.

That being said:

run ```
sudo fdisk -l
``` and see what your device is called then do ```
sudo mkdir /media/USB\ Drive
```
then
```
sudo chown $USER:root /media/USB\ Drive
```
**replace $USER with your username**
lastly:
```
sudo ntfs-3g /dev/sd?? /media/USB\ Drive
``` should mount the device.  Remember to replace /dev/sd?? with the device name you found using sudo fdisk -l

This should all be run in the terminal.  You said yourself it was working fine before, so the error may **not** lie with Ubuntu, but with some setting that was changed.  Post back if it works.

---

### Post by ad_267 on 2008-06-14
I'm nowhere near an expert on this sort of thing but I have heard of problems with ntfs drives being marked as in use by windows. I don't know if that could be what's happening here but you could try "safely removing" the drive in windows before booting into Ubuntu. Someone else might know better and this might be useless but it could be worth a try.

---

### Post by ChameleonDave on 2008-06-14
I can't begin to tell you how many problems I've had with Windows over the years, from the memory leak on Windows ME to the viruses on XP.  But you just carry on with your idea that your problem with USB (which will probably be immediately fixed) makes Windows better than Linux.



You do realise that NTFS is a trade secret of Microsoft's, don't you?  It's only through painstaking reverse-engineering that Linux is ever able to use it at all.

Format it with Ext3 or ReiserFS, then see how XP deals with it.  Despite these being open standards, and by far superior to NTFS, Windows will not even recognise there is anything there at all.  Format it with FAT, and anything can open it.

---

### Post by lman_271860 on 2008-06-14
i am very disappointed this has been removed from beginners talk

i feel that because i have criticized ubuntu community for not addressing problems and i have posted information that may be helpful in addressing the problem rather than just slagging it off, the post has been kicked into the long grass

censorship of differing opinions is a dangerous path ........

never mind back to xp

---

### Post by ChameleonDave on 2008-06-14
> **lman_271860 said:**
> i am very disappointed this has been removed from beginners talk

i feel that because i have criticized ubuntu community for not addressing problems and i have posted information that may be helpful in addressing the problem rather than just slagging it off, the post has been kicked into the long grass

censorship of differing opinions is a dangerous path ........

never mind back to xp

Stop whining.  You've had a quick response and you whine that it's not quicker.

If you want support, ask for support properly.  If you want to express your opinion, post in Testimonials, where this thread now is.  You just tried a cheap trick.

---

### Post by bruce89 on 2008-06-14
> **lman_271860 said:**
> never mind back to xp

This is the best solution TBH.

---

### Post by Sef on 2008-06-14
Moved to absolute beginners as the OP wanted help.

---

### Post by ChameleonDave on 2008-06-14
> **Sef said:**
> Moved to absolute beginners as the OP wanted help.

No, he wanted to troll.  You ought not to facilitate it.

He probably just needed to do "sudo mount -t ntfs-3g -o force /dev/**DRIVE** /home/**MOUNTPOINT**" to fix the problem that Windows caused, but that got lost in the trolling.

---

### Post by balagosa on 2008-06-14
In my own experience with just months of Ubuntu, It is Lovely! Ubuntu is not Windows wherein mostly everything will work out of the box. It is like 75% of your stuffs will work right of the box for Ubuntu. The joy and pride why I still stick to Ubuntu is my **passion to learn**. A point to ponder on: **Ubuntu will require hours of research and trials. It is an OS which you have to dedicate some time to enjoy your Ubuntu experience.** 

PS: i can not help you with your current problem because i have no know-how regarding it. Just do not loose hope, I am sure someone out there will have the right answer.

---

### Post by lman_271860 on 2008-06-14
i am investing my time and effort trying to progress this problem for everyone and others are also doing the same

---

### Post by Tomatz on 2008-06-14
> **lman_271860 said:**
> i know this post will be a red rag to a bull but it is designed to GET A RESPONSE !

i have one and only one problem with UBUNTU and it is that my USB hard dive does not work and many other people have the same problem which appears to be falling on deaf ears.

if this operating system is going to be a contender against microsoft then basic things have to work out of the box and this is very basic.

i have now reloaded xp back only laptop and have a dual boot with ubuntu
my usb hard drive works with xp with no problems at all even without any service packs

it also used to work with gutsy with no problems at all

i have only been playing with linux for a couple of months and initially thought it was i viable alternative to windows but at the moment, for me, i consider it as a bit of a play thing and when serious work needs to be done i go back to xp

here is the kernel log, as if it is required !
and obviously lsusb sees the drive

i think for the operating system to fulfill it's destiny as the natural operating system on every machine in the world the a bloody usb hard drive should work !

thanks in advance





Jun 13 17:55:17 victor-laptop kernel: [  478.079888] USB Mass Storage support registered.
Jun 13 17:55:17 victor-laptop kernel: [  478.080128] usb-storage: device found at 3
Jun 13 17:55:17 victor-laptop kernel: [  478.080131] usb-storage: waiting for device to settle before scanning
Jun 13 17:55:23 victor-laptop kernel: [ 1202.660543] usb-storage: device scan complete
Jun 13 17:55:29 victor-laptop kernel: [ 1208.272579] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Jun 13 17:55:39 victor-laptop kernel: [ 1227.965007] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Jun 13 17:55:39 victor-laptop kernel: [ 1228.213048] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Jun 13 17:55:50 victor-laptop kernel: [ 1238.457555] usb 3-1: reset high speed USB device using ehci_hcd and address 3
Jun 13 17:55:50 victor-laptop kernel: [ 1238.590079] scsi 0:0:0:0: Device offlined - not ready after error recovery

I love these flamebait posts.

:lolflag:

---

### Post by Canis familiaris on 2008-06-14
I do not like this thread title. I mean say if you are in a meeting you say "Hello How Do you do?" NOT "Hello Dudes! Wazzup!", in the same way there is a time and place for everything.
@OP
Coming back to your question:
(1) Do other USB drives like pen drive,etc. work?
(2) Did you try copying all data from USB Drive to internal HDD reformat the USB HDD, prefarably in FAT32 and then copy back all contents and try again?
(3) Did this USB drive work when you booted say Knoppix?

Most probably your USB hard disk partition is corrupt or  USB hard disk is damaged. In that case Windows surely will be better to use it with NTFS because NTFS is its own native file system. 

P.S. : Look at my post heading

---

### Post by Canis familiaris on 2008-06-14
> **lman_271860 said:**
> i know this post will be a red rag to a bull but it is designed to GET A RESPONSE !

i have one and only one problem with UBUNTU and it is that my USB hard dive does not work and many other people have the same problem which appears to be falling on deaf ears.

if this operating system is going to be a contender against microsoft then basic things have to work out of the box and this is very basic.

i have now reloaded xp back only laptop and have a dual boot with ubuntu
my usb hard drive works with xp with no problems at all even without any service packs

it also used to work with gutsy with no problems at all

i have only been playing with linux for a couple of months and initially thought it was i viable alternative to windows but at the moment, for me, i consider it as a bit of a play thing and when serious work needs to be done i go back to xp

here is the kernel log, as if it is required !
and obviously lsusb sees the drive

i think for the operating system to fulfill it's destiny as the natural operating system on every machine in the world the a bloody usb hard drive should work !

thanks in advance


If it worked with Gutsy then wait for 8.04.1 and it may solve the problem.

---

### Post by SunnyRabbiera on 2008-06-14
Seriously the attitude of the OP needs to go, if you cant respect others and be patient then bloody leave...
Enjoy XP while you still can.

---

### Post by aysiu on 2008-06-14
This parasitic behavior has to stop.

Ubuntu community, shame on you. Seriously.

lman_271860 posted this same problem four weeks ago with the subject heading *usb hdd mount problem under hardy*, and nobody answered.

Now with the flamebait heading, you all come out of the woodwork. Shame on you.

Please read [A Plea to the Community: Don't Reward Bad Behavior](http://ubuntuforums.org/showthread.php?t=634322)

The message you've sent to this OP is "Ask nicely, and no one will help you. Post flamebait, and people will fall all over themselves trying to help you."

Awful. Shameful.

I've moved all the helpful posts to the original support thread.

---

