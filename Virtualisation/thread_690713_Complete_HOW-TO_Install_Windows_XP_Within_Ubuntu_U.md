---
title: "Complete HOW-TO Install Windows XP Within Ubuntu Using Virtual Box"
date: 2008-02-07
forum: Virtualisation
---

### Post by Colemanvt on 2008-02-07
Setting up Windows XP in Virtual Box

Using Ubuntu 7.10 Gutsy 
Virtual Box v 1.5.4 (normal release personal edition)
Windows XP Professional edition

Good little thing to set up on your box for people that are in the transition stage from windows (like myself)

Lets add the repository for the Open Source version the one already in is ok but this one is better hehe :-D

```
gksu gedit /etc/apt/sources.list
```

Paste in the following 2 lines

```
##Virtual Box Repository
deb http://www.virtualbox.org/debian gutsy non-free
```

ok now to get the public key.. go to this website and it'll have the key there just right click anywhere in the page and go to save page as then save it to your home directory preferably.

[http://www.virtualbox.org/debian/innotek.asc](http://www.virtualbox.org/debian/innotek.asc)

Now to add that key run...

```
sudo apt-key add innotek.asc
```

Now update your sources list...

```
sudo apt-get update
```

And install...

```
sudo apt-get install virtualbox
```

when there is ever a new version of Vbox it should update along with your system updates (fun huh?)

Now you need to add yourself to the vboxusers group... (you should get a message about it while installing)

System>Administration>Users and Groups

Click on your user name
click the manage groups button>add group &#8211; vboxusers
then double click on vboxusers when it shows up and check the box next to your name and log out and then back in to take effect.
Also you'll possibly need to check on the USB support (disabled in Gutsy for some reason shrugs) to fend off problems later down the road.

```
gksu gedit /etc/udev/rules.d/40-permissions.rules
```

Change...

```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",		MODE="0664"
```

to...

```
# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",		MODE="0666"
```

also you'll want to edit another file.

```
gksu gedit /etc/init.d/mountdevsubfs.sh
```

Change...
```

#mkdir -p /dev/bus/usb/.usbfs 
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644 
#ln -s .usbfs/devices /dev/bus/usb/devices 
#mount --rbind /dev/bus/usb /proc/bus/usb
```

to...

```
mkdir -p /dev/bus/usb/.usbfs 
domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644 
ln -s .usbfs/devices /dev/bus/usb/devices 
mount --rbind /dev/bus/usb /proc/bus/usb
```

Save and exit both of the files and most likely you'll have to reboot your system so you don't get error messages in Vbox when you try and change USB / DVD-ROM settings.
Alright lets start her up! <3

Applications>System Tools>Innotek Virtual Box

Click New> next etc etc etc.

Personally I like naming the name WindowsXP with no spaces it might save you grief in the future..

Select XP in the drop down menu. > Next

Base Memory. shrugs what ever on this one it will really use what it needs when it needs is but split off about half of your ram to it to give you peace of mind if it seems to grog your system you can mess with your settings after you get your guest XP installed.

Just to throw out some terminology also the OS running the vbox (ubuntu in this case) is referred to as the Host where as the OS that you are running in the vbox (XP in this case) is referred to as the guest. 

Make your selection >Next

Now to make your drive...

Click New > Select Dynamically expanding disk > leave the image size at 10 GB (it is irrelevant I will explain in a moment) > Finish

Your new WindowsXP.vdi should show up in the drop down menu now so click next and keep on trukin'

To Backtrack: The reason that the disk size was left at 10GB is because with a Dynamically Expanding Image (as you probably guessed) it doesn't actually allocate that exact amount of space. What happens is there is a folder that is created that everything you install in your vbox goes to for that OS you've installed so it just expands as it needs to so you don't have to chop up your HD space in lumps. Someone over at innotek is a genius am I right? 

Ok so now we're back on the main screen you'll see you have your Audio, DVD-ROM, USB, etc. etc. over on the right pane. We'll deal with all that later but for now all we want to do is mount the XP disc you want to install from....


Click on &#8220;CD/DVD-ROM&#8221;
 
Here you can do two things.
1.Mount the drive you have your xp disc in if you have a physical copy of the disc.
2.Mount an image of an xp disc if you happen to have one backed up on a hard drive

Once mounted double click on WindowsXP in the left pane and your system should boot up.

This should look very familiar if you've ever installed windows just go through the motions like normal to install your new copy of windows xp in ubuntu. :-D

Note at any time you want to get your mouse out of the Vbox and go to something else use the right Ctrl (Which is referred to as your &#8220;home&#8221; key) and your courser will disassociated with the Vbox window.
The Home key can be used to carry out nice little short cuts one you get your XP OS installed.

Once you have windows installed and boot in go ahead and shut down your XP guest like you would normally shut down a windows computer.

Now head back to your Vbox Settings and click on the CD/DVD-ROM setting (the same as when you mounted your DVD-ROM drive to install XP.

Now you'll want to select ISO Image File.

Click the Folder icon to the right of the drop down menu.

And Select: VboxGuestAdditions.iso

Now boot back into your XP guest and go to My computer. There you will see the image mounted. Double click and install it. Guest Additions add a lot more usability to all guests so if you try your hand at installing Vista or something like that you will be able to install guest additions for any OS in the same way.
Guest additions let you do things like...
not having to hit the Home key before being able to get your courser out of your Guest OS
(And my favorite) by hitting your Home key + F your guest will take up the entire workspace you have it opened on which makes it look as if you were actually running the OS as it would normally look. (no window)
Home Key + L puts your system into seamless mode which integrates Host and Guest windows

That's about it to get you going enjoy.

---

### Post by wayfarer51 on 2008-02-09
I follow the directions, but shortly after the "sudo apt-get install virtualbox" I get a problem having to do with the kernel.  I'm using  2.6.20-16-server.  I don't want to have to move back to -14...I have a few apps that only run in -16.  I don't want to have to keep rebooting every time I reach for a particular app.  I've already had to give up having TVtime and a webcam on the same boot. 

Anway, here's what I get directly after being notified that I need to add myself to the user group:

===========================================
 Unable to find a precompiled module for the current kernel!                 
                                                                             
 Without a suitable kernel module you will never be able to start VMs. It    
 is strongly recommended to compile a kernel module now. The kernel          
 headers and the tools to build kernel modules (gcc, make, binutils, ...)    
 are required. However, in case a suitable kernel module already exists      
 at another place you might want to override the default position by         
 setting KDIR=<full_path_to_vboxdrv_module> in /etc/default/virtualbox.      
 The compilation can also be done later by executing                         
                                                                             
   /etc/init.d/vboxdrv setup                                                 
                                                                             
 as root. 
===========================================                        

and then:

===========================================

 Should the vboxdrv kernel module be compiled now?               
                                                                 
                         <Yes>                <No>     
===========================================

selecting Yes produces:

===========================================
 Compilation of the kernel module FAILED!                                   
                                                                              
   VirtualBox will not start until this problem is fixed. Please consult      
   /var/log/vbox-install.log to find out why the kernel module does not       
   compile. Most probably the kernel sources were not found. Install them     
   and execute                                                                
                                                                              
     /etc/init.d/vboxdrv setup                                                
                                                                              
   as root.                                                                   
                                                                              
                                    <Ok>                                      
===========================================                                                                              

and in /var/log/vbox-install.log: 

"Makefile:70: Warning: using /usr/src/linux as the source directory of your Linux kernel. If this is not correct, specify KERN_DIR=<directory> and run Make again.
Makefile:76: *** Error: /usr/src/linux (version 2.6.22-14-server) does not match the current kernel (version 2.6.20-16-server).  Stop."

Anyway, I have a similar prob in -16 with VMWare.  What's up with this anyway?  We're not supposed to be using -16?  I'm the victim of bad karma?  There's a hidden repository of -16 headers I need a secret decoder ring to find?

Can anyone help?  I've been doing Ubuntu for only about 4 months, so go easy on me.  I'm a noob.

Thanks.

---

### Post by kcav45 on 2008-02-09
Why should I use Virtual Box?  Why not use VMware server?  

:confused:

KC

---

### Post by wayfarer51 on 2008-02-10
[http://www.techthrob.com/tech/linux_virtualization.php]("http://www.techthrob.com/tech/linux_virtualization.php")

---

### Post by RudolfMDLT on 2008-02-12
Thanks Bud! :P

---

### Post by 5735guy on 2008-02-17
AWESOME Thankyou very much.:):):):):)

---

### Post by linfidel on 2008-03-08
I've got xp running with VirtualBox, and it works very well.  I like it a lot better than the VMWare player.

I'm trying to get my Canon S750 USB printer to work, since it won't work with Linux.  But I can't get XP to see it.  

VirtualBox sees it OK, and added it to the list of USB devices, and it's checked.  I also tried disabling the printer service in Ubuntu so it would stop getting installed there.

I did all the modifications everyone recommends.  I also made an addition to fstab that was recommended - is this needed?
usbfs /proc/bus/usb usbfs auto 0 0

I've been searching, trying things, rebooting, etc.  I just can't get the Canon setup to recognize the printer.  

I did check Windows' device manager to see if USB is there, and it seems to be.

Any ideas?

---

### Post by Colemanvt on 2008-03-08
Tch it's a problem I've toyed with as well with mine. I've been too busy to fix it. I know it's not anything great but what I do if I need to print a file I've just been either emailing it to myself and printing it or more handy... Set up your ubuntu home folder as a shared folder to your vbox xp guest. But my guess is whatever you're trying to print can't be printed in ubuntu? (due to file type) if that's not the fact maybe those 2 suggestions can tide you over until one of us figures out the solution.

---

### Post by linfidel on 2008-03-08
Well, wouldn't you know it - I deleted the line from my fstab that I was unsure of, then I restarted everything, and tried again.  I got a new error for USB connection from VirtualBox itself; when I went to the devices menu, clicked on the USB connection for the printer to check it, it suddenly got recognized and the installation finished successfully.

Sort of the infinite monkeys theory - you mess around randomly with something for enough time, and eventually you hit upon a new version of linux.  :)

Well, onward and upward, I guess.

---

### Post by kidux on 2008-03-09
Wow, thanks! I got it setup and I cannot believe how much speedier and responsive it is being virtualized!

---

### Post by Colemanvt on 2008-03-10
Glad you're enjoying it it seems virtual box seems to be the easiest and most stable way to go. the only other virtualization program I would want to go with right now would be vmware-workstation but it was kinda buggy when I used it and not as easy to install an os. the only thing it has virtualbox beat in is the fact that it has mild 3d acceleration support (which is extremely limited no pixel shading support etc; thus alot of games won't run). just my 2c

---

### Post by linfidel on 2008-03-13
I've used VMWare's offering a lot, both server and player, in addition to workstation on Windows and infrastructure at work, where we have various Linux flavors, and Vista.  For personal use, I think Virtual Box on Linux is better than VMWare.  No problems, and more features than VMWare player by far.

I can run Windows XP full screen on one virtual desktop, and switch to Linux full screen on another.  Wish I had more memory on my Linux box (I only have 1GB, and it's the old-style memory, so it's not worth upgrading).  Maybe a new motherboard is in order soon.

---

### Post by DamonChyld on 2008-03-13
I have tried to install VB quite a few times today but always get stuck on the "Press F8 if you accept" part of the XP EULA. When I click in the VB screen it says that it is capturing, but I can still move my mouse outside VB.

I have looked high and low on the net but can not find a solution to this, I need a little help here please!

---

### Post by Jamie Jackson on 2008-03-13
Where's the guest additions ISO? I can't find it on my system. Did you download it or something?

Update: Never mind, I found it. It just isn't quite where the original post stated. While the Guest is running, go to the surrounding virtualbox window, and it's under Devices >> Install Guest Additions. Note: It didn't work for me until I ejected the XP installer disc that was in my CDROM drive.

---

### Post by Colemanvt on 2008-03-14
yeah you're right there's a couple different ways you can mount that guest on addons

---

### Post by LeeU on 2008-03-14
OK, I have it up and running, and it's great! However, I'm not getting the "seamless" thing. I switch to seamless mode, and then I can alt-tab TO the guest (XP)  but I can't alt-tab not BACK to the host (Ubuntu). Am I missing something?

---

### Post by styrofoam cup on 2008-03-15
> **Jamie Jackson said:**
> Where's the guest additions ISO? I can't find it on my system. Did you download it or something?

Update: Never mind, I found it. It just isn't quite where the original post stated. While the Guest is running, go to the surrounding virtualbox window, and it's under Devices >> Install Guest Additions. Note: It didn't work for me until I ejected the XP installer disc that was in my CDROM drive.

I had to use that method too. :confused:

A few questions,
Security. Should I be taking all the old precautions that I needed when I was a windows user? E.g firewall, anti virus, and so on.

Is snapshot kind of like roll back? so if I get the virtual windows running just right, I should take a snapshot incase windows breaks.

I have only played with it for five minutes, is there a guide, or website that can give me a few tips without going into to much depth at this early stage??

Thanks for any replies,
and thanks for the how to.

:KS

---

### Post by mrblondeisback on 2008-03-16
Is anyone else having a problem with 3d acceleration?  The only reason I need windows is for gaming, and Virtualbox doesn't seem to recognize my video card.  I tried to install the drivers for my geforce 7300 but the software said I didn't have a compatible card.  Is there any way I can get it to recognize it?

---

### Post by dm6257 on 2008-03-16
Thanks.  Great instructions. Worked fine. One question. What is the PGP key for? I have installed Virtual Box on other machines and didn't need a key.  

Thanks again,
Dale

---

### Post by linfidel on 2008-03-17
> **styrofoam cup said:**
> I had to use that method too. :confused:

A few questions,
Security. Should I be taking all the old precautions that I needed when I was a windows user? E.g firewall, anti virus, and so on.

Is snapshot kind of like roll back? so if I get the virtual windows running just right, I should take a snapshot incase windows breaks.

I have only played with it for five minutes, is there a guide, or website that can give me a few tips witho

ut going into to much depth at this early stage??

Thanks for any replies,
and thanks for the how to.

:KS
Security:  You can get a virus, etc in the VM, so you do need to treat it just like a normal Windows installation.

Yes, the snapshot is exactly that - it gives you the ability to set checkpoints, and you can revert to any one of them at any time.  So, you can have one with clean Windows, one with Windows + all updates, or whatever.  Also, if you want to try some questionable modification, you can take a snapshot, then revert if it doesn't work out.

Have you tried the Virtual Box website?  I never needed much once I got it running.  Their website did help get the USB working for Ubuntul with Windows guest.

---

### Post by linfidel on 2008-03-17
> **mrblondeisback said:**
> Is anyone else having a problem with 3d acceleration?  The only reason I need windows is for gaming, and Virtualbox doesn't seem to recognize my video card.  I tried to install the drivers for my geforce 7300 but the software said I didn't have a compatible card.  Is there any way I can get it to recognize it?
I'm sorry to say this, but I don't think there is such a thing.  I've heard that VMWare has rudimentary support for some advanced graphics in one of their products, but I don't thing any VM is suitable for 3d graphics.  That's why most gamers use WINE instead.

---

### Post by mrblondeisback on 2008-03-18
> **linfidel said:**
> I'm sorry to say this, but I don't think there is such a thing.  I've heard that VMWare has rudimentary support for some advanced graphics in one of their products, but I don't thing any VM is suitable for 3d graphics.  That's why most gamers use WINE instead.

Lame.  Well, I guess I'll continue to use a dual boot setup, because WINE just kills my gaming.  I really do wish I could just get rid of windows.

---

### Post by linfidel on 2008-03-19
> **mrblondeisback said:**
> Lame.  Well, I guess I'll continue to use a dual boot setup, because WINE just kills my gaming.  I really do wish I could just get rid of windows.Me too, but I don't think I will anytime soon.  But I have 2 computers connected by a KVM switch, so I can use both at the same time, and instantly switch from one to the other.  Maybe if VirtualBox proves to be reliable enough, I'll eventually move my windows apps to it.  Fortunately, I don't play action games.  To me, the computer is entertainment enough. 

I think I'd just get a game console if I wanted to play games.

---

### Post by scottc992004 on 2008-03-22
I typed in terminal: 
gksu gedit /etc/udev/rules.d/40-permissions.rules

and this is my 40-permission.rules

I cant find where to change the usb you had in the first post.


# This file establishes permissions and ownership of devices according
# to Ubuntu policy.  See udev(7) for syntax.
#
# The names of the devices must not be set here, but in 20-names.rules;
# user-friendly symlinks (which need no permissions or ownership) should
# be set in 60-symlinks.rules.

# Block devices
SUBSYSTEM!="block", GOTO="block_end"
ATTRS{removable}!="1",			GROUP="disk"
ATTRS{removable}=="1",			GROUP="floppy"
SUBSYSTEMS=="usb",			GROUP="plugdev"
SUBSYSTEMS=="ieee1394",			GROUP="plugdev"
SUBSYSTEMS=="mmc",			GROUP="plugdev"
SUBSYSTEMS=="pcmcia",			GROUP="plugdev"
LABEL="block_end"

# IDE devices
ENV{ID_CDROM}=="?*",			GROUP="cdrom"
KERNEL=="ht[0-9]*",			GROUP="tape"
KERNEL=="nht[0-9]*",			GROUP="tape"

# IEEE1394 (firewire) devices
# Please note that raw1394 gives unrestricted, raw access to every single
# device on the bus and those devices may do anything as root on your system.
# Yes, I know it also happens to be the only way to rewind your video camera,
# but it's not going to be group "video", okay?
KERNEL=="raw1394",			GROUP="disk"
KERNEL=="dv1394*",			GROUP="video"
KERNEL=="video1394*",			GROUP="video"

# Packet CD devices, group under /dev/pktcdvd
KERNEL=="pktcdvd",			MODE="0644"
KERNEL=="pktcdvd[0-9]*",		GROUP="cdrom"

# Printers and Parallel devices
SUBSYSTEM=="printer",			GROUP="lp"
SUBSYSTEM=="ppdev",			GROUP="lp"
SUBSYSTEM=="usb", KERNEL=="lp[0-9]*",	GROUP="lp"
KERNEL=="pt[0-9]*",			GROUP="tape"
KERNEL=="pht[0-9]*",			GROUP="tape"

# SCSI devices
SUBSYSTEMS=="scsi", GOTO="scsi_start"
GOTO="scsi_end"
LABEL="scsi_start"
ATTRS{type}=="1",			GROUP="tape"
ATTRS{type}=="5",			GROUP="cdrom"
ATTRS{type}=="6",			GROUP="scanner"
ATTRS{type}=="8",			GROUP="tape"
ATTRS{type}=="3", ATTRS{vendor}=="HP",	GROUP="scanner"
ATTRS{type}=="3", ATTRS{vendor}=="Epson", GROUP="scanner"
ATTRS{type}=="3", ATTRS{vendor}=="EPSON", GROUP="scanner"
LABEL="scsi_end"

# Serial devices
SUBSYSTEM=="tty",			GROUP="dialout"
SUBSYSTEM=="capi",			GROUP="dialout"
SUBSYSTEM=="slamr",			GROUP="dialout"
SUBSYSTEM=="zaptel",			GROUP="dialout"
KERNEL=="ttyLTM[0-9]*",			GROUP="dialout", MODE="0660"

# Sound devices
SUBSYSTEM=="sound",			GROUP="audio"

# USB devices (usbfs replacement)
SUBSYSTEM=="usb_device",		MODE="0664"

# vc (virtual console) devices
SUBSYSTEM!="tty", GOTO="vc_end"
KERNEL=="console",			GROUP="root", MODE="0600"
KERNEL=="ptmx",				GROUP="root", MODE="0666"
KERNEL=="pty*",				GROUP="tty", MODE="0666"
KERNEL=="tty",				GROUP="root", MODE="0666"
KERNEL=="tty[0-9]*",			GROUP="root"
KERNEL=="vcs*",				GROUP="root"
LABEL="vc_end"

# Video devices
SUBSYSTEM=="drm",			GROUP="video"
SUBSYSTEM=="dvb",			GROUP="video"
SUBSYSTEM=="graphics",			GROUP="video"
SUBSYSTEM=="video4linux",		GROUP="video"
KERNEL=="agpgart",			GROUP="video"
KERNEL=="nvidia*",			GROUP="video"

# Other devices, by name
KERNEL=="null",				MODE="0666"
KERNEL=="zero",				MODE="0666"
KERNEL=="full",				MODE="0666"
KERNEL=="random",			MODE="0666"
KERNEL=="urandom",			MODE="0666"
KERNEL=="mem",				GROUP="kmem", MODE="0640"
KERNEL=="kmem",				GROUP="kmem", MODE="0640"
KERNEL=="port",				GROUP="kmem", MODE="0640"
KERNEL=="nvram",			GROUP="nvram"
KERNEL=="rtc",				GROUP="audio"
KERNEL=="inotify",			MODE="0666"
KERNEL=="js[0-9]*",			GROUP="plugdev"

---

### Post by scottc992004 on 2008-03-22
Sorry found it

---

### Post by kiasteve on 2008-03-24
Just wanted to say thanks Colemanvt, my virtualbox is running XP perfectly. Now I can finally remove (very slow) vista from my laptop!

---

### Post by ShelJ on 2008-03-25
Awesome thanks a lot, now I'm going to try to see if AutoCAD can work in this setup.  Thanks a lot!

---

### Post by ShelJ on 2008-03-25
WinXP is still not recognizing my USB ports, it would appear.

Just upgraded to Ubuntu 8.04, getting a kernel issue now, just working it out.

---

### Post by amrith on 2008-03-26
How to enable Microphone in ur Virtual XP and how to see the physical NTFS partitions in XP ?

---

### Post by SneakyBooBoo on 2008-03-28
you can add your ntfs partition and even ur linux partition i think as network drives in the guest OS. i managed to do it with my ex-windows partition, now just a big partition for downloads and whatever.

when your in Vbox, go to the settings of the guest OS u want to run, then click on the shared folders option in the panel on the left. click the little button with a blue + (add folder button) and put in the path where your partition or folder is. or just click the button next to the "folder path" field. once you've got your folder, change the name (if necessary, but remember it because you will need it later. i just used "external" or "hdd" or "disk") and press ok.

save your settings, and boot up your guest OS. I assume your using XP so first thing to do once its booted up is to go to Start > Run, and then type in "command" in the command line.

once you got DOS prompt on your screen, type in the following, assuming you used "disk" as the drive name.

```
net use x: \\vboxsvr\disk
```

Note: You need Guest Additions installed in your GuestOS for this to work.

---

### Post by SneakyBooBoo on 2008-03-28
oh yeah, i almost forgot why i came here. Im having problems with the USB options. I did all the things said on the first post, but when i run Vbox and go to the settings for my GuestOS, i dont see any USB option. Just General, Hard Disk, CD/DVD-ROM, Floppys, etc.

do i have to install something else? I got the PUEL version of Vbox i think.

---

### Post by Browser_ice on 2008-04-16
created a thread of its own with the old content of this reply since it was going unnotice.

---

### Post by teknorah on 2008-04-17
> **DamonChyld said:**
> I have tried to install VB quite a few times today but always get stuck on the "Press F8 if you accept" part of the XP EULA. When I click in the VB screen it says that it is capturing, but I can still move my mouse outside VB.

I have looked high and low on the net but can not find a solution to this, I need a little help here please!


I was encountering the same issue.  There is a downward facing arrow in the bottom right of the virtual window that represents if you keyboard is/is not "captured" by the virtual machine.  You may have to click on it to by able to press keys in the virtual window. This is especially true when you are installing the guest OS.  Once you get it installed and have Guest Additions installed you won't really have that problem anylonger because clicking the mouse in the window automagically captures your mouse clicks and key strokes.

Hope this helps! :)

---

### Post by teknorah on 2008-04-17
I love these forums!  Thanks so much for this how-to!  I was encountering some glitches with the version of virtualbox in the ubuntu gutsy repos and wasn't able to compile the newer version from source easily.

This is great! Thanks!

---

### Post by Bobrm2 on 2008-04-18
I have a partition with the old XP pro files installed on this linux; thinking that I could just use VBox(?). Is that the case? Also, I wonder if VB will allow me to connect to the XPpro box wirelessly?

That would solve the problem, and as you suggested I am emailing doc's and jpg's to this Linux box.

The install was sooth as silk, thanks to your instructions.

Bob

---

### Post by ginovation on 2008-05-27
I just have a doubt in installation process of ubuntu 8.04 hardy. As it gives me problem of (initramfs)shell problem. Is there is any solution for that.

---

### Post by Caes08 on 2008-07-29
Alright, so I followed the instructions at the beginning of this thread exactly as it was described, however when I go to start up my virtual machine  I get an error message that says: 



VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


 as I am relatively new to ubuntu I'm not sure as to what needs to be done to fix this. Any help is greatly appreciated.

---

### Post by SneakyBooBoo on 2008-07-30
i think i used to get that error message when i ran it to. have you tried running VBox as root? That used to work for me. but there is another solution i used to fix it and run normally.....just trying to remember.

---

### Post by Caes08 on 2008-07-30
I just tried to run it as root, when i got home today and i got this in terminal:

WARNING: The character device /dev/vboxdrv does not exist.
         Please install the virtualbox-ose-modules package for your kernel.

         You will not be able to start VMs until this problem is fixed.
Qt WARNING: Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed


could this have something to do with the fact im running 64-bit ubuntu?

---

### Post by SneakyBooBoo on 2008-07-30
hmmm...i'll set up my 64-bit tomorrow and test out Vbox and get back to you on that one. i was using 32-bit Gutsy. But it looks like u need to install something. I think look in synaptics package manager for virtualbox-ose-modules package and install it. If its not there, check the homepage because you might need to add the repository that contains it to your package manager. I'll set up my system and check too.

---

### Post by Caes08 on 2008-07-30
i went through synaptec and installed the packages that it said i needed, but  im still getting the same error. Also i havent seen anything about a new repository needing to be added anywhere

---

### Post by SneakyBooBoo on 2008-08-01
i have your solution. i just set up my 64-bit and ran virtual box. got the same error. what i did was get into synaptics and install any ose-modules package. the one i chose was virtualbox-ose-modules-generic.

once that was done, i rebooted, and logged back in. next thing you have to do is enable you user account to work with VBox. So go to System menu, Administration -> Users and Groups.

Once you have that open, unlock it (if you need to, i think thats how 8.04 is now), click on Manage Groups. Scroll down to where it says vboxusers, click on it, click properties, and make sure your user is checked. After that, close everything, log out, log back in, and run VBox again. worked for me.

---

