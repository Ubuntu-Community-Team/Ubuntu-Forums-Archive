---
title: "The Virtual Box Experience Thread"
date: 2009-12-22
forum: Virtualisation
---

### Post by joes7 on 2009-12-22
So, I switched back to XP as my master OS, and I will install Xubuntu on Virtual Box. I wanted to know about your experiences. Is it recommended or not?

Cheers, and:

[COLOR=Red]**Merry[COLOR=SeaGreen]Christmas![/COLOR]**[/COLOR]

---

### Post by memilanuk on 2009-12-22
I'm liking it so far... I have a basic file/back-up server running 8.04.3 LTS on an old PC connected to an ethernet port on my wifi router.  Everything else I do via Virtualbox running on my HP desktop PC running Vista as the host OS.

So far, most everything on Ubuntu seems to work pretty much flawlessly inside Virtualbox... but I haven't tried really pushing the system very hard yet either.  i.e. no movies or flash or wine or compiz, etc.  Basic web browser (Firefox) to surf the web and check my Gmail account, X-Chat for IRC, and Wesnoth for a bit of gaming.  Actually, both Debian 5.0.3 and Ubuntu 8.04-9.10 pretty much work 'out of the box' on this setup - but thats kind of the idea of a virtualization setup like this... they choose very solid, mainstream, run-of-the-mill components to emulate.

HTH,

Monte

---

### Post by lmarmisa on 2009-12-22
My experience has been very positive. I like everything in VirtualBox except USB.

Only two recommendations:

[LIST=1]
[*]Install the GuestAdditions.
[*]Define the Brigde mode (not NAT) in your network interface.
[/LIST]
Best regards,

Luis

---

### Post by Chrisco66 on 2009-12-23
Im running xp pro in 9.10.  Virtualbox is great except for USB.  I set the filters like they said, no help.  I think the problem is allowing my group to use VB.  I added it in user privileges, but usb devices are still greyed out in VB. Oh well, keep looking..

---

### Post by VastOne on 2009-12-25
> **lmarmisa said:**
> My experience has been very positive. I like everything in VirtualBox except USB.

Only two recommendations:

[LIST=1]
[*]Install the GuestAdditions.
[*]Define the Brigde mode (not NAT) in your network interface.
[/LIST]
Best regards,

Luis

I have just setup Vbox today with Win 7 on my 9.10 box and am quite impressed, except that I had to use 32 bit Win 7 instead of 64 even though I have virtualize setup in the Bios but for some reason Vbox would not accept it. Scouring the net it seems to be a major issue...I can live with 32 bit as it is very fast and doing what I need. One other thing, it took all of 12 minutes to completely install Win 7 and have Firefox loaded and on the net. I dloaded a 90 meg file in incredible speed from within the Vbox session....so, now...

To my question, 

Why are you suggesting to use the Bridge mode and how do I setup or install these guest additions?


Appreciate the input and suggestions...

Thank you

---

### Post by lmarmisa on 2009-12-26
> **VastOne said:**
> 
To my question, 

Why are you suggesting to use the Bridge mode and how do I setup or install these guest additions?


Bridge mode allows the complete integration of the VM in the LAN. The VM will be able to communicate with any other computer of your LAN (including the host system) and with Internet without any limitation. Using the default NAT mode, the VM is limited to communications with Internet. The set up is very simple: shutdown the VM, select its profile in the VB menu and click on **Network**. Finally change **Attached to** field to **Bridged Apadter**.

The GuestAdditions offer a great improvement in the management of the mouse and the screen of the guest system. You will not need to push the Right Ctrl key for releasing the mouse when you are working in the guest system. Additionally, the screen of the VM will be automatically resized to the size of its window. A very interesting feature is that you will be able to select the full screen mode (Right-Ctrl+F) for your guest system. This is really fine.

GuestAdditions are installed running a shell script of a built-in virtual CD of VirtualBox. Root privileges are required for the installation. 

Start your VM and login. Click on **Devices -> Install Guest Additions**. Open a terminal and type:

```

sudo /media/cdrom/autorun.sh

```When the shell script is completed, unmount the VBOXADDITIONS device (clicking on the righ button of the mouse over the icon) and finally click on Devices -> Unmount CD/DVD-ROM.

The installation will be finished when you restart your guest system.

You will need to repeat this procedure when a new kernel version is released.

---

### Post by VastOne on 2009-12-26
> **lmarmisa said:**
> Bridge mode allows the complete integration of the VM in the LAN. The VM will be able to communicate with any other computer of your LAN (including the host system) and with Internet without any limitation. Using the default NAT mode, the VM is limited to communications with Internet. The set up is very simple: shutdown the VM, select its profile in the VB menu and click on **Network**. Finally change **Attached to** field to **Bridged Apadter**.

The GuestAdditions offer a great improvement in the management of the mouse and the screen of the guest system. You will not need to push the Right Ctrl key for releasing the mouse when you are working in the guest system. Additionally, the screen of the VM will be automatically resized to the size of its window. A very interesting feature is that you will be able to select the full screen mode (Right-Ctrl+F) for your guest system. This is really fine.

GuestAdditions are installed running a shell script of a built-in virtual CD of VirtualBox. Root privileges are required for the installation. 

Start your VM and login. Click on **Devices -> Install Guest Additions**. Open a terminal and type:

```

sudo /media/cdrom/autorun.sh

```When the shell script is completed, unmount the VBOXADDITIONS device (clicking on the righ button of the mouse over the icon) and finally click on Devices -> Unmount CD/DVD-ROM.

The installation will be finished when you restart your guest system.

You will need to repeat this procedure when a new kernel version is released.

Hey Lmarmisa,

Thanks for the feedback.  In the time that I first ask you I have installed the Guest Additions and agree they are a great asset.  I tried and succeeded in get the Bridged network going but went back to NAT because I did not like how the Bridge affected my Shoutcast streams on my host, under NAT I get fast speeds on the Win7 setup and still maintain the music I listen to.

I have also successfully gotten Win7 64 bit loaded but went back to Win7 32 as the 64 was sluggish.  

In a short period of time I feel I have become quite proficient on VBox and I think that speaks to the ease of use of VBox, suffice it to say that I am very impressed.

Next I am going to try and get Os/2 Warp 4 loaded as I miss that more than anything in my 20 + years in this tech world.

One other question, I pulled VBox 3.1.2 from the Sun site, I am assuming that I have the OSE version.  Is there value of going to the closed source version?  Since I have shared folders now between the host and guest I am not that worried about no USB connection.

Thanks for your help! 

Happy New Year

---

### Post by VastOne on 2009-12-26
Here is a screen shot of my new Vbox setup

---

### Post by pricetech on 2010-01-12
> **VastOne said:**
> I pulled VBox 3.1.2 from the Sun site, I am assuming that I have the OSE version.

If I'm not mistaken that is the closed source version.  The Open Source version is the one in the repos.

Please correct me if I'm wrong.

---

### Post by howefield on 2010-01-12
> **pricetech said:**
> If I'm not mistaken that is the closed source version.  The Open Source version is the one in the repos.

Please correct me if I'm wrong.

You are correct. The features that keep the PUEL version closed source are...

> Remote Display Protocol (RDP) Server
This component implements a complete RDP server on top of the virtual hardware and allows users to connect to a virtual machine remotely using any RDP compatible client.

USB support
VirtualBox implements a virtual USB controller and supports passing through USB 1.1 and USB 2.0 devices to virtual machines.

USB over RDP
This is a combination of the RDP server and USB support allowing users to make USB devices available to virtual machines running remotely.

---

### Post by studmf on 2010-01-12
> **VastOne said:**
> I have just setup Vbox today with Win 7 on my 9.10 box and am quite impressed, except that I had to use 32 bit Win 7 instead of 64 even though I have virtualize setup in the Bios but for some reason Vbox would not accept it. Scouring the net it seems to be a major issue...I can live with 32 bit as it is very fast and doing what I need. One other thing, it took all of 12 minutes to completely install Win 7 and have Firefox loaded and on the net. I dloaded a 90 meg file in incredible speed from within the Vbox session....so, now...
 
To my question, 
 
Why are you suggesting to use the Bridge mode and how do I setup or install these guest additions?
 
 
Appreciate the input and suggestions...
 
Thank you
 
Is your processor a Core 2 Duo P7450?  Mine is and apparantly it will not run 64 bit in VB.  The other part to that is I have Win7 Pro as my guest on 9.10 and the XP compatability will not run on it either due to the processor.

---

### Post by coldraven on 2010-01-12
Hi, I'm new to VMs but I just installed XP Pro as guest under Ubuntu 9.10 in VirtualBox 3.1.2 (the latest).
I did not need to run a script to install the guest additions, I just clicked on "Add guest addittions".
Xp now will resize to any shape screen and "Host F" gives fullscreen.
Press "Host F" to toggle through options.
I just checked the USB, I switched on my Samsung Story external hard drive and five seconds later it was available to the guest (XP was running at the time).
Move the mouse to "Devices/USB Devices" and click the check box.
Cool!

---

### Post by pricetech on 2010-01-12
I've been running the OSE version with Hardy as the host and XP as the guest.  For the most part everything is fine, but I may have to switch over to the closed source version since I can't seem to get the guest to run with the network set for anything except NAT.  I don't have a "bridged" option.  Mine says "Host Interface".

Otherwise, no complaints.

---

### Post by coldraven on 2010-01-13
If it helps, here is a screenshot of my Network options

---

### Post by jocampo on 2010-01-13
I like VBox but I also try to stay 1 version below! Why? two times I've tried to upgrade to most recent version, I've found issues and some bugs so I had to downgrade to 1 version below. In real life, you can do the same unless you are missing or need one of the new features really bad. 3.01 works like a charm for me on an Ubuntu Jaunty Headless server.

---

### Post by iburry on 2010-01-14
> **lmarmisa said:**
> My experience has been very positive. I like everything in VirtualBox except USB.

Only two recommendations:

[LIST=1]
[*]Install the GuestAdditions.
[*]Define the Brigde mode (not NAT) in your network interface.
[/LIST]
Best regards,

Luis

I have never been able to get 2. here to work.  Got it to work fine with OpenSolaris, but not with the two versions of Ubuntu I've tried (9.04 and 9.1).

---

### Post by Dmck23 on 2010-01-22
> **coldraven said:**
> Hi, I'm new to VMs but I just installed XP Pro as guest under Ubuntu 9.10 in VirtualBox 3.1.2 (the latest).
I did not need to run a script to install the guest additions, I just clicked on "Add guest addittions".
Xp now will resize to any shape screen and "Host F" gives fullscreen.
Press "Host F" to toggle through options.
I just checked the USB, I switched on my Samsung Story external hard drive and five seconds later it was available to the guest (XP was running at the time).
Move the mouse to "Devices/USB Devices" and click the check box.
Cool!

Hi coldraven,

I was interested in getting the Samsung Story and i was wondering have you any issues with the Story on Ubuntu 9.10

---

### Post by Thomas Garman on 2010-01-22
I have a dual boot system:  Vista Ultimate and Karmic 9.10.  I was using the Vista system for editing sound files in Magix, streaming video with Netflix, syncing my iPod Touch, and watching cable tv with my Pinnacle PCTV HD USB stcik.
 
I started to get annoyed with switching to Vista to watch tv or stream videos from Netflix or put a song on my iPod touch.  And anyway I can use my laptop for those things most of the time.
 
The idea of running a windows OS in a virtualbox in Ubuntu 9.10 seemed like an interesting challenge.  So...  
 
At first I just installed the Virtualbox OSE from Ubuntu's package manager, but I couldn't get the virtual machine running XP to detect shared folders on my host harddrive nor could I get my virtual machine to detect USB.  After searching for solutions online I realized that actually I needed the PUEL version.I downloaded the Virtualbox PUEL version from the virtualbox site and added the add ons so that now I connect to usb in the virtual machine and use shared folders.  I can watch netflix just fine.  The iPod touch works with iTunes.  (I still haven't figured out how to connect the USB Pinnacle PCTV to the virtual machine and get a picture).
 
The question I have now is this:  what else can one do with the VIRTUALBOX?
 
I am asking: what do you use a virtual machine in virtualbox for?  I am basically just using it to avoid the hassle of rebooting into Vista.

---

### Post by tipiglen on 2010-01-22
Namaste

Just to relate my experience with VirtualBox in a Karmic host running on an asus netbook:

1. I established a successful karmic UNR guest (installed via flash usb) with guest additions.  Runs fine, but has difficulty accessing samba shared files.

2. Set up XPPro guest using a gifted iso.  install went ok, and worked fine, except whenever I installed the guest additions, I started getting blue screens!  Was only able to read them by pressing f8 during re-boots and choosing 'disable re-boot on failure'.  The blue screen said the problem 'seemed to be caused by intelppm.sys'  So I booted in 'safe mode', renamed \windows\system32\drivers\intelppm.sys to intelppm.bak  Works fine now with guest additions, full screen or seamless, etc, and samba shares are easily accessible, including host /media folder, and thus the external hdd or anything else on usb.

Cut and paste works fine between all three machines, and mouse integration is transparent.  Firefox instances run in all three machines simultaneously, all using copies of the same profile, though this won't be synchronised....With all three machines running, youtube vids seem to be slowed down a bit, but no real other signs of strain. (Host has 2GB RAM total, and each VM has 512)  

I'm a satisfied VirtualBox user!

[http://home2.btconnect.com/tipiglen/loveandpeace3.gif](http://home2.btconnect.com/tipiglen/loveandpeace3.gif)
Salaam/Shalom/Shanthi/Peace
 -ed

---

### Post by Ginsu543 on 2010-01-24
> **Thomas Garman said:**
> The question I have now is this:  what else can one do with the VIRTUALBOX?
 
I am asking: what do you use a virtual machine in virtualbox for?  I am basically just using it to avoid the hassle of rebooting into Vista.
I too have a dual-boot system with Ubuntu 9.04 and Windows XP Pro SP3. I decided to run Windows as a VM in VirtualBox primarily for the same reason that you did: I didn't want to have to constantly boot into Windows to use Windows software and then have to reboot to get back to Ubuntu.

Since then, I have steadily weaned myself from Windows software altogether, replacing them with Linux equivalents. However, there are still a few occasions when I *have* to use the Windows version (e.g., Microsoft Office because for whatever reason OpenOffice won't handle a particular Greek font I need, and Internet Explorer because content on a Korean news website I need won't work on Firefox). That's when VirtualBox comes in!

I guess the other use of VirtualBox is to have the ability to try out/run many different types of OSes without having to physically install them.

---

### Post by Thomas Garman on 2010-01-24
I am happy with the way Virtualbox works with windows XP running a virtual machine.  I have been streaming Netfilx constantly and therefore using Ubuntu more.

I also use Quick Time Pro and Magix in Vista (dual boot).  My hope was that in my virtualbox I would be able to run Magix and thereby edit sound files without having to boot into Vista (I have never gotten and kind of sound editor to actually work in Ubuntu)... and I know already that it would be pointless to try to edit a video in my virtual machine version of XP because it is only getting about 1 GB of my host system's RAM.

So, the virtual machine works well for using XP to manage my iPod Touch and stream Netflix.  But using it is a lot like using a netbook...

The irony is that I already have a netbook.  So, while I was using my "big" computer I could have just booted up my netbook into XP and steamed netflix.

---

