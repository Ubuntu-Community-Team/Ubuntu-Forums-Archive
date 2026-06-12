---
title: "Switching from Dual Boot to Virtualization"
date: 2008-09-11
forum: Virtualisation
---

### Post by idrailgag on 2008-09-11
I have been using Ubuntu for about 3 years.  Currently I still dual boot between Ubuntu and Vista.  I only use Windows for Dreamweaver, Photoshop, and Illustrator.  Contrary to many GIMP fans, there are no alternatives to these programs.

I am thinking of switching to virtualizing Windows with VirtualBox.  Does anyone have experience with this?  Is it a good idea?  Will my laptop be able to handle running Photoshop & Dreamweaver through virtualization?  I'm running a 1.6Ghz, Turion X2 with 2GB of ram.

---

### Post by Howler9443 on 2008-09-11
Hi idrailgag,

I use VirtualBox without any real issues. I use it for all of the "normal" office apps along with Visual Studio 2008 for another project that I just inherited support for.

My machine is a bit beefier than yours though so I really can't say how well that it will run on your machine. However, on the laptop I use for work, I have a Core 2 Duo (2.2Ghz) w/4Gb of RAM. I use Ubuntu 8.04 LTS 64-bit and VituralBox XP. I allow access to 1.5Gb of ram from VirtualBox and all seems to be right in the world. So yes, I would say its a great solution.

With your current system specs and wanting to run Vista, I am not really sure its going to work all that great to be honest. But I've been wrong before.

I'd be glad to answer any questions you may have if I can.

Best of luck!

---

### Post by doorman on 2008-09-11
Hy!

Same situation here, although I'm running it in VMware, not VirtualBox...

If you cut down all those visual effects in vista, it should work just fine. Be aware, though, that all of the applications you mentioned are memory eaters, so you should be careful when creating the virtual machine. My suggestion would be to create a VM with 1 GB of RAM, although I'm not so sure you'll get away with it... The actual problem is that if you assign it too much RAM, you'll have swap issues, which are, as you probably know, big performance killers.

To sum up, IMHO, if you clean & reinstall the Vista VM on regular basis, you should be fine. ;)

btw, did you give wine a try?

---

### Post by veloce on 2008-09-11
If possible, I'd try to switch to running virtual XP machine rather than vista.  Will this work for the software you're wanting to run?

I run XP under vmware on a centrino duo with 1Gb ram and it gives better-than-native performance.  (mainly because I haven't installed a whole lot of rubbish on the XP vm but also because linux does smp much better than windows).

---

### Post by MystaMax on 2008-09-11
I've got a  similar setup to idrailgag. I've got a Dell D620 w/ a 1.8 Core Duo, and 2GB of RAM. I'm not sure how much faster mine is,  but it can't be that big of a difference.

I would definitely recommend you give VirtualBox a try. I've been virtualizing WinXP for some time now. Its a great piece of software. I use it to run a slimmed down version of WinXP Pro (I used [nlite]("http://www.nliteos.com/") to remove a lot of extraneous software and services, I didn't need, saving memory and HD space. My XP install CD is only 250 MBs).

I made a post about this very topic back in June:

[http://ubuntuforums.org/showpost.php?p=5118169&postcount=27](http://ubuntuforums.org/showpost.php?p=5118169&postcount=27)

It includes a screenshot of my virtual XP session running in seamless mode. Sweetness!

While I use VMware Server @ work extensively, I don't use it for home use. I found Virtualbox to be a much better product for what I needed. VMware Server was a hassle to deal w/ everytime a kernel update came out (you do have to do the same thing w/ VirtualBox, but not as troublesome), and it was pain to get vmware tools installed (hopefully this goes away w/ VMware Server 2, which I like). There are guides for it all over the forums, but I didn't want to deal w/ it, as I already had to on the many servers @ work. At home, I want ease of use, and VirtualBox definitely offered that.

I agree w/ veloce as well. While Vista worked perfectly fine for me in a VM, it used a lot more memory off a fresh boot, and sitting idle. I will say I didn't slim my Vista VM like I did my XP VM. Regardless you'll have to allot 1 GIG of memory to the VM as CS3 won't install w/o it.

In the end, I say GO FOR IT! I'd hate to reboot to just use CS3 :) I'm waiting for CS3 to work in Wine!

Good luck!

---

### Post by wgarider on 2008-09-12
FWIW, I made the move to Ubuntu as the primary OS a month ago and I run two Windows VM's in VMWare player - One XP and one Vista. I actually created the VM's under Microsoft's Virtual PC, converted them to VMWare VM's and then moved them over to my Ubuntu machine and run them under Player.

It was the simplest, quickest solution for me - I needed access to the apps/utils installed on the VM's and rather than go through whole bunch of uninstall and reinstall, I converted and moved them.

I gave them each a GB of RAM and they run fine......

---

### Post by harrow on 2008-09-14
How well do VirtualBox and VMware Player work for graphics applications like Dreamweaver, Photoshop, and Illustrator? I've just installed VMware Server, but can't do any graphics work or run Windows Media Center given it's meager graphics capabilities when running Vista. Could anyone please tell of their experiences here?

---

### Post by idrailgag on 2008-09-15
I will definatley use XP.  I am so sick of Vista, it's a resource hog.

---

### Post by idrailgag on 2008-09-15
My HP Laptop did not come with a physical XP cd.  Rather, there is a os restore partition on my hard drive.  It is terribley annoying and as far as I know, unusable for VirtualBox.

Does anyone know if I can use my legal XP cd key on a bootlegged copy of XP?

---

### Post by hiyaegagagm1 on 2008-09-16
[size=2][font=Times New Roman][size=3]hi,everyone,need guitar effects pedals? take a look at [guitar effects pedals shop](http://www.myguitarpedals.com/), may be u will find ur favorite...This is an excellent thread!**The good:** The optional Bowers and Wilkins audio system in the 2009 Jaguar XF offers exceptional separation and clarity for music playback. We like the interior materials in the XF, along with the tech touches. The engine offers a good amount of power for the car while delivering acceptable fuel economy.[runescape gold](http://www.runescapecoin.net/) **The bad:** The touch-screen interface for audio, navigation, and other car systems is too slow, and it is not well organized. The navigation system is unremarkable.[age of conan gold](http://www.buy-age-of-conan-gold.com/)**The bottom line:** The 2009 Jaguar XF offers a lot of luxury for the money, with many unique high-tech touches and an exceptional audio system. But it doesn't always deliver on its apparent promise, [color=#008000][age of conan money](http://www.ageofconanmoney.net/) [/color]with a run-of-the-mill suspension and navigation system.[runescape money](http://www.runescapemoney.ws/). [/size][/font][/size]

---

### Post by MystaMax on 2008-09-30
> **harrow said:**
> How well do VirtualBox and VMware Player work for graphics applications like Dreamweaver, Photoshop, and Illustrator? I've just installed VMware Server, but can't do any graphics work or run Windows Media Center given it's meager graphics capabilities when running Vista. Could anyone please tell of their experiences here?

Photoshop, Dreamweaver, & Illustrator should run fine. They do on my machine. I'm not using VMware Server, but VirtualBox. Windows Media Center will run, but you do not have 3D acceleration in a virtual Machine w/ VMware Server or VirtualBox. So, its rather pointless to run in a VM.

The only virtualization products I know of to have 3D acceleration are VMware Fusion (mac) & VMware Workstation (3D acceleration is still beta).

---

### Post by jameswhite15 on 2008-10-29
I am also thinking of switching to virtualbox to run Photoshop and Dreamweaver. 

1) Is it safe ( like if something were to go wrong would I be able to recovered my files )

2) Are you all then removing your dual boot copy of Windows, if so how did you do this ?

Thanks :)

---

### Post by fjgaude on 2008-10-29
All the Adobe programs run fine in VMware server under Ubuntu. See my signature.

---

### Post by idrailgag on 2008-10-30
Thanks for all of the replies.  I will be setting all of this up over the next week using Ubuntu 8.10.

Here is what I'm doing:
- Clearing my current (Dual Boot) partitions and making 2 partitions: 1 15gb partition for Ubuntu's core and the rest of the space for my home directory (everyone preaches that this is the good way to go)
- Installing Ubuntu 8.10
- Creating a special slimmed down Windows XP ISO using nLite (hope that works well)
- Installing Windows using VirtualBox, giving it 1.3gb (out of 2gb) of system memory and probably 7gb or so of hard drive space.

I'll be sure to reply when this is all over with my results.

---

### Post by lvirden on 2008-10-31
I am hoping that someone reading this thread might have some pointers for me. 

I recently became the owner of a new Sony Vaio laptop (so new an owner I've not figured out what model it is, etc.).

I was asking around about the best way to get Ubuntu up on this machine and one person suggested that Sun's VirtualBox, running on Vista, would work great for such a thing.

So I downloaded and installed VirtualBox. My problem, however, comes in what to do next. When I tell VirtualBox to create a new virtual machine, it asks me how much memory to allocate, how much disk to allocate, etc. My first time through, I believe I gave the machine 512 meg of memory (it's my understanding that I have 3 gig on this laptop) as well as 8 gig of disk (the drive is around 200 gig). I then pointed VirtualBox at a CD I was given with Ubuntu 8.0.5 (I believe that's the version - I don't have the disk handy right this moment). The ubuntu disk spun, I got a few screens ... then the VirtualBox screen just went blank. No warnings or errors, no responding to clicks, etc.

I've been a user of a wide variety of operating systems in the past. However, I've not really had many system administrator opportunities. So I probably am overlooking something simple.

I've read messages here that talk about people building VirtualBox machines for windows xp and I think someone said they had VB'd vista as well. I don't know that I've actually seen anyone trying this route of running VirtualBox on Vista and then running Ubuntu in the virtual machine.

Is anyone aware of a howto, tutorial, or guide to setting this up? I just downloaded ubuntu 8.10, with the hope that, since this is a newer laptop the various drivers, etc. would be more likely to be supported than on a version that was a bit older.

However, if anyone can point me to a hand-holding page, that would really be appreciated...

Thank you all!

---

### Post by idrailgag on 2008-10-31
Ivirden,

I know with Ubuntu 8.04, all you had to do to virutalize Ubuntu was stick the Ubuntu CD in your computer in Windows.  It came with a setup to virtualize itself all on the CD.  It is as easy as installing Microsoft Word or Firefox.  I'm sure the new version also has it.  Give that a try first before bothering with all of the confusion of VirtualBox or VMWare.

However, dual boot is a nice option that will really give you the full Ubuntu experience.  If you like virtualizing Ubuntu, you should try the real thing. To install Ubuntu that way:
- Insert the Ubuntu CD into your laptop and restart.
- When the first screen shows up on your computer, press the appropriate button to "select boot device".  It is probably Esc, Tab, or F2.
- Select CD and just follow the instructions from there.  It is very straight forward and will make it so that when you turn on your machine, you choose Windows or Ubuntu to boot into.

---

### Post by idrailgag on 2008-10-31
Ivirden,

I know with Ubuntu 8.04, all you had to do to virutalize Ubuntu was stick the Ubuntu CD in your computer in Windows.  It came with a setup to virtualize itself all on the CD.  It is as easy as installing Microsoft Word or Firefox.  I'm sure the new version also has it.  Give that a try first before bothering with all of the confusion of VirtualBox or VMWare.

However, dual boot is a nice option that will really give you the full Ubuntu experience.  If you like virtualizing Ubuntu, you should try the real thing. To install Ubuntu that way:
- Insert the Ubuntu CD into your laptop and restart.
- When the first screen shows up on your computer, press the appropriate button to "select boot device".  It is probably Esc, Tab, or F2.
- Select CD and just follow the instructions from there.  It is very straight forward and will make it so that when you turn on your machine, you choose Windows or Ubuntu to boot into.

---

### Post by lvirden on 2008-10-31
Thanks for the tip. Since I'm just getting started, and I have went to the effort of downloading ubuntu 8.10 as an iso image, is there a way to do the virtualizing of Ubuntu with the .iso image? I am such a newbie that I haven't learned whether I have the ability of creating CDs on my machine yet <blush>

---

### Post by fjgaude on 2008-10-31
To create a bootable CD from the .iso all you have to do is right-click the .iso file with a blank CD in your drive and then click extract. You will then see your CD drive and it all goes automatically.

---

### Post by lvirden on 2008-10-31
so, after falling for Vista's helpful offer to format my blank CD, and ruining it, I was able to get what appears to be Ubuntu on a CD.

Then, I rebooted the system with that CD in the drive, and it appears that Ubuntu is trying to start.

What I don't see is any obvious step to create a Windows virtualization.

I hate to sound so clueless... but that's where I am unfortunately.

Anyone have time to tell me what during the initial ubuntu configuration screen I need to hit to set ubuntu up as a virtualized image in Vista?

---

### Post by fjgaude on 2008-11-01
Have you read, studied the Sticky notes at the top of this forum?

---

### Post by idrailgag on 2008-11-05
If you would like to install Ubuntu in Windows, you should insert the CD into your computer *while* you are in Windows.  A menu should pop up with directions.

---

### Post by sdowney717 on 2008-11-06
bootleg copies of XP wont likely work with legal xp key codes.
but you can use the bootleg keycode to install the bootleg copy.

I was reading that MS in China is now blacking the screen of bootleg copies that have the WGA software on them, I read you have to change the screen background to restore the desktop once per hour.

[http://www.neowin.net/forum/index.php?showtopic=684070](http://www.neowin.net/forum/index.php?showtopic=684070)

---

### Post by jdpearson on 2008-12-19
What **I'd** like to do is to make an image of my existing Vista PC.  Wipe the disk.  Load Ubuntu as my primary OS and run Vista in a VirtualBox.

So, is it possible to make a VirtualBox readable image of my Vista PC?  I've seen some posts about virtualizing my existing installation and running it natively at the same time, but I want to completely remove it.

---

### Post by MystaMax on 2008-12-20
HI jdpearson. kudos to you for wanting to make the switch!

You could try and use [VMware Converter 3.02]("http://bit.ly/NDDS"), which has experimental support for Vista to convert your desktop to a VM. [Virtualbox 2.1]("http://bit.ly/Bh98") just introduced full VMDK/VHD support (VMware uses the VMDK file format, instead of VDI used by Virtualbox), so your converted VM will now run in VirtualBox.

I say give it a try. Let us know how it works.

---

### Post by Shazaam on 2008-12-21
+1 for VMWare Converter per MystaMax. I did this for an XP install and it worked. Some of the problems you will have is with pre-installed drivers (motherboard, video, sound etc which CAN cause the vm to not boot); you will have to re-authenticate your virtual Windows (invalidating the real install); and 3d is iffy at best.
You also need hard drive free space that is equal to or greater than the actual (real) Windows installation to convert it. So if you have a real Windows installed size of 25 gigs you will need at least a 60gig hard drive. The reason is that Converter uses the extra space as a temporary container while it is working. When it is done it will shrink back down in size but it will still be quite large compared to a virtual install.

---

### Post by itendo on 2009-03-31
> **idrailgag said:**
> Ivirden,

It is as easy as installing Microsoft Word or Firefox.  

probably *less *hassle than word

---

