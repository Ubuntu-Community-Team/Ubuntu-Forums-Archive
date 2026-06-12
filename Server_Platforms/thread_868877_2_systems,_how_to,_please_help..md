---
title: "2 systems, how to, please help."
date: 2008-07-24
forum: Server Platforms
---

### Post by thecircusb0y on 2008-07-24
If you don't mind I'll be quick and too the point. I have 2 systems. 

System 1-
Athlon 64 X2 3800+
4gb DDR2-667 Ram
10/100 and a 10/100/1000 nics. 
This box is built in a small form factor case. My idea is to install linux to a 2gb SD Card in the memory card reader. I will also end up putting a 200 gb and/or 400 gb ide harddrive in this. 
The idea is for this box to be a gateway for my school network connection, because we use Cisco Clean Access, which requires a machine to login. This means no routers or switches that cannot login using a broswer or cisco's software. Now it won't just be a gateway. Other functions will include light desktop and server functionality as needed. I'd like to run synergy, Instant messaging, email, firefox, apache, ssh, mysql, ventrillo server,media serving(mp3's, divx), and possibly a srcds of goldeneye source.
the main OS has to fit and boot from the 2gb flash card, and I really don't think I need that big of a swap file, maybe like 64 meg. I'll let you be the judge on how I would go about doing that. 
In retrospect, I guess I could use one of the articles/tutorials on booting from a flash drive, but I'm looking for input as well.

System 2
This one is a bit trickier. 
486- 75mhz, floppy drive boot, cdrom noboot, 20mb of ram. 4gb harddrive
I guess my question here is, which gui would be the least draining on the ram. I was able to use the debian network install floppy to get the latest debian on it, but I'd like to know what  you would do to get a gui going on this machine. 
Actually, is there a way to run gui programs full screen without the use of a window manager? I really just want this box up to be a gadget. I'm hooking up a cmos camera to the serial port, and doing pwm out the parrallel port to a board to control pan and tilt of a platform based on camera input and image analysis. (its gonna be a sentry gun eventually). 
Once again, I'm interested in your input.

---

### Post by Lord DarkPat on 2008-07-24
First of all, using such a good system for a gateway...is just silly.
And, I really don't get what you're trying to do with this thing....please explain properly

---

### Post by markjensen on 2008-07-24
System #1: You don't specify whether or not this has a CDROM drive.  If so, boot the Ubuntu CD, and see if it can detect your SD card slot (with card inserted) as an available target.  That would be the first step I would take, since it seems that SD card boot is your priority there.

System #2: Yes, you can run a GUI on a 486/75 with 20MB RAM.  But it will be dog-slow.  Might want one of the *boxes to try.  Openbox or Fluxbox.   X is going to consume quite a bit.    If you want to try something like DSL (DamnSmallLinux) does, and use a reduced X implementation (DSL does not use a full xorg), that might help trim some resource usage.

Sounds interesting, and good luck!

---

### Post by thecircusb0y on 2008-07-24
First off, thanks for the quick reply. 

> First of all, using such a good system for a gateway...is just silly.
And, I really don't get what you're trying to do with this thing....please explain properly

Its not JUST a gateway. going to hold many functions. Which I clearly typed in the first post. What you have to understand is that my college uses Cisco Clean Access, and I need a javascript enabled browser and gui to access and login to the network at school for the dorms. This machine is also going to stay on for many other purproses, I agree it would be "silly" to be just a gateway, but it will hold many more services then just that. Hell I'd use my wrt54gl with open wrt if I could, but I can't get it to login to cisco clean access through LYNX, because lynx doesn't support javascript.

Yes, it has a DVD Rom. Right now I have a base ubuntu server installation running on the SD Card. 
I've toyed with the idea of installing ESX server or Ubuntu Server with XEN to do virtualization. but I think thats an overkill. 

The 486, I only need x, to run a program I wrote to interface with a cmos camera on the serial port, and display jpeg's of what the camera sees in rapid progression of each frame. 

> System #1: You don't specify whether or not this has a CDROM drive. If so, boot the Ubuntu CD, and see if it can detect your SD card slot (with card inserted) as an available target. That would be the first step I would take, since it seems that SD card boot is your priority there.

System #2: Yes, you can run a GUI on a 486/75 with 20MB RAM. But it will be dog-slow. Might want one of the *boxes to try. Openbox or Fluxbox. X is going to consume quite a bit. If you want to try something like DSL (DamnSmallLinux) does, and use a reduced X implementation (DSL does not use a full xorg), that might help trim some resource usage.

Sounds interesting, and good luck!

1.) Already ahead of you, this bad boy can boot from my usb card reader, and the dvd rom functions. For the love of my organizational skillls, I wish I could find my 4gb compact flash microdrive, because I would use that over the 2gb secure digital card, for the space, and the fact that I don't own a device any longer that uses compact flash. 

What irritates me is that ubuntu doesn't have an installation options menu when doing an installation off the live cd. The Live cd booted beautifully, and I stress tested the hardware to make sure it all ran without error. (I was alittle worried, using a 250 watt psu, with a motherboard that wants 350...damn Jetway.)

If you want more hardware specs...
Motherboard: Jetway M26GT3-SVP (Cheap Microatx mobo I picked up on Ebay for $10)
CPU:             Athlon X2 3800+ (My old Desktop CPU, I upgraded to an Athlon X2 6000+)
Memory:       4GB Corsair DDR667 (4 1gb sticks) ($20 at newegg :-) !!! )
Case: Antex Minuet Microatx case ($10 on ebay, not a scratch, great for a small box/HTPC)
Lite-On DVD Drive (IDE)
3.5'' USB hub, multicard reader.
Waiting for a 1tb harddrive to be RMA'ed, so I can back up my 200 gb SATA drive, and throw it in this box, but as storage, not for the main OS. 


2.) My problem is I have trouble trying to figure out how I'm going to boot a cdrom from the floppy drive, because this laptop doesn't support boot from cdrom. Do you know how I could use a floppy to boot the ubuntu linux minimal cd? then I could at least get a base system of like... 400 mb install? its still alittle big, but I have 4gb right now. 
I just like the idea of some sorta of gui for applications. I have a few of these laptops siting around, and multiple ideas for them. I was gonna try turning one into a picture frame, mount it on the outside of the door to my room, and hook up an electronic lock to my door, so that you have to enter in a password into the keyboard, to unlock the door to my room. (if you haven't figured it out, I'm a computer engineering college student geek,nerd,dork, whatever)
Hmm, thats all I can spew into ascii at the moment.

---

### Post by markjensen on 2008-07-24
If it is of any assistance, I have had great success in installing Linux onto a laptop's hard drive that I removed and put into an enclosure to fit a standard desktop PC (and the accompanying 40-pin IDE cable).

Then I installed Linux from CD on that desktop onto the laptop drive that was temporarily installed.

Not the most elegant solution, perhaps, as it requires a bit of extra hardware (enclosure) and the use (abuse?) of another PC to do the dirty work of installing.   But the drive transferred and booted just fine when placed back into the laptop.

---

### Post by philinux on 2008-07-24
These might help.

[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by thecircusb0y on 2008-07-24
Won't that cause driver conflicts? Or does it automatically detect all the new (in this case OLD) hardware.

---

### Post by markjensen on 2008-07-24
> **thecircusb0y said:**
> Won't that cause driver conflicts? Or does it automatically detect all the new (in this case OLD) hardware.
Linux does much better at this than Windows does.   My experience is limited, but I have never seen a Windows-like refusal to boot when transferring a drive.

I think that this has a lot to do how Ubuntu/Fedora/etc install their Linux with a large number of modules already included.

If you, for example, did a LFS, and included only the modules needed for the particular hardware you installed on, I would not be confident that it would boot when transferred.

---

### Post by thecircusb0y on 2008-07-24
I'll try that out, I just have to find my damn 2.5 - 3.5'' harddrive adapter. 

Just in case someone else is monitoring this thread for a similiar situation, I just took a look at phsycocats website, and this was interesting -> [http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

Are there any good guides to stripping down ubuntu server?

---

### Post by cariboo on 2008-07-24
No one has suggested the minimal install cd, using it you can control what goes on the sd card. It is available here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Jim

---

