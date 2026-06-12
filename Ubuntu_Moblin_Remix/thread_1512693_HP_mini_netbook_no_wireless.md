---
title: "HP mini netbook no wireless"
date: 2010-06-18
forum: Ubuntu Moblin Remix
---

### Post by mudeye on 2010-06-18
I downloaded the Ubuntu Netbook i386 Remix to a USB and installed on my HP mini netbook (1000?).  All works fine except there is no wireless internet connection. (Also note that the web switch on the front of the HP is “off”; the blue light does not show when I push the switch).  I see suggestions for editing the /etc/modules file; perhaps there is an edit for the HP mini?

---

### Post by 11hjpphty76lkjj on 2010-06-18
Hey there.

I also have a HP Mini 1000 with the Netbook remix. To get the wifi working run:

```
sudo apt-get install bcmwl-kernel-source
```

Then reboot. and you should be good to go.

A

---

### Post by mudeye on 2010-06-18
Sorry, but I got back an error message: "E: Couldn't find package bcmwl-kernel-source"

(and, as background info for me, how would it work for me to have received the package while I am not online?)

Thanks both for your post and in advance.

---

### Post by 11hjpphty76lkjj on 2010-06-18
Ahh not online eh. That could make it a little more interesting. You might be able to load the ISO onto a USB flash drive, then boot from the mini, plug in the flash drive, add the flash drive to the synaptic sources, then apt-get update, apt-get install.

Putting the ISO onto my flash drive is how I installed Ubuntu remix onto my mini..so hopefully you'll already have the boot-able flashdrive.  If, I believe there are specific instructions on how to do that or someone else may have specific steps on how to do the above.  Sorry--I'm still working and I don't have the time to write it down step by step. :(

Hope this points you in the right direction at least!

A

---

### Post by kerry_s on 2010-06-18
> **mudeye said:**
> Sorry, but I got back an error message: "E: Couldn't find package bcmwl-kernel-source"

(and, as background info for me, how would it work for me to have received the package while I am not online?)

Thanks both for your post and in advance.

you need to plug in, it's the easiest way.

---

### Post by mudeye on 2010-06-19
Re "plug in": The HP does not accept a phone line; the internet switch on the front of the mini no longer works in that it remains in the off position.

Re reboot:  
  	 	 	 	 	 	  I booted from the USB and still cannot get online.  Perhaps I should try an earlier version of Ubuntu rather than another version of a remix?
 If so, then which OS should I use?  Perhaps an early stable U that will “fit” into my HP mini.
 How do I download these files to my desktop and move them to a flash drive, then upload to my HP mini?
 (As you may have noticed, I need to take time to think these things over.  I have been around computers since the mid-60's, but not worked with Op Systems until now).  Thanks in advance to all.

---

### Post by bananafishbones on 2010-07-20
Well this just sucks! No ethernet connection to install what I need. so I went out and grabbed the pool folder from the ISO and started installing all of the dependencies by hand to get the broadcom driver loaded. After what seemed like an age, I installed all of the dependencies and tried to install the broadcom driver and you guessed it; the source won't compile and it fails!

Now there are a whole slew of posts regarding this I didn't catch first. What a royal pain in the a$$!

I don't understand why all the packages are apparently within the pool folder, yet they didn't get installed. Broadcom is not exactly and obscure wireless chipset maker!

Sorry but I had to vent! Especially since I'm screwed!
B

---

### Post by bananafishbones on 2010-07-20
An apology is in order. I've never used my HP Mini that often. It came with XP and got slower and slower. Slow as an old dog in fact.

So I just noticed that on the left-hand side of my Mini, there is a deep and quite well hidden Ethernet plug. I had no idea that I had one.

I plugged it in, update Synaptic and installed all of the Broadcom drivers, rebooted and my wireless is now working.

I go back under my rock.

b

---

### Post by cariboo on 2010-07-22
All the files you need are on the Live CD/USB in the /pool directory, make sure you have build-essential installed before trying to install the STA driver.

---

### Post by agentstewie on 2010-07-23
I just got my HP mini 1030nr setup and i couldnt find any guides to do it. Here's what i did using a live usb:
-Boot into liveusb (enable persistence, i did but i do not know if its necessary)
-Toggle the wifi with the physical switch... lol yes surprisingly it worked for me on liveusb but not on the actual installed version
-install operating system
Note what partition you installed the OS on. this can be done using the gparted tool. Mine for example is "/dev/sda1"
Activate all your sources for your new netbook by going to System-> Software Sources. Check all the boxes for internet sources and uncheck the cdrom source
for simplicity open up gedit and paste this code:
```

sudo mkdir /mnt/installer
sudo mount $1 /mnt/installer
#Copy the sources from the one you just configured
sudo cp /etc/apt/sources.list /mnt/installer/etc/apt/
sudo mount --bind /dev /mnt/installer/dev
sudo mount -t proc /proc /mnt/installer/proc
sudo chroot /mnt/installer
apt-get update
apt-get install -y bcmwl-kernel-source

```
save this as wifi.sh
now run this script and pass your newly installed ubuntu installation partition with it
sh wifi.sh /dev/sda1
reboot
all should be working now!

---

### Post by triwave on 2010-07-27
> **agentstewie said:**
> I just got my HP mini 1030nr setup and i couldnt find any guides to do it. Here's what i did using a live usb:
-Boot into liveusb (enable persistence, i did but i do not know if its necessary)
-Toggle the wifi with the physical switch... lol yes surprisingly it worked for me on liveusb but not on the actual installed version
-install operating system

Note what partition you installed the OS on. this can be done using the gparted tool. Mine for example is "/dev/sda1"
Activate all your sources for your new netbook by going to System-> Software Sources. Check all the boxes for internet sources and uncheck the cdrom source
for simplicity open up gedit and paste this code:
```

sudo mkdir /mnt/installer
sudo mount $1 /mnt/installer
#Copy the sources from the one you just configured
sudo cp /etc/apt/sources.list /mnt/installer/etc/apt/
sudo mount --bind /dev /mnt/installer/dev
sudo mount -t proc /proc /mnt/installer/proc
sudo chroot /mnt/installer
apt-get update
apt-get install -y bcmwl-kernel-source

```
save this as wifi.sh
now run this script and pass your newly installed ubuntu installation partition with it
sh wifi.sh /dev/sda1
reboot
all should be working now!

Mudeye : while I belive this work, I think the easiest method is to find an ethernet connection (your mini should have an ethernet port correct?) while you **install** the OS. I could never get persistence to work right on a live USB so the required re-boot to get the broadcom drivers installed creates a problem; once installed however there is no issue to re-boot.

Plug into ethernet and install OS. Follow earlier directions on getting the broadcom driver and system updates while your at it (which will all be downloaded via your ethernet) and perform the re-boot. All should work fine.

I've installed ubuntu netbook 10.04 on a couple machines (including an HP mini 1084NR) with Broadcom cards and having wired ethernet available to install the driver makes it go really smooth. For what it's worth the button for wireless (with F12 on my mini 210-1084NR) doesn't work. The light indicates the status properly (blue when wifi is on) but to physically turn it on/off I need to enable/disable it through the network applet. Easy enough ...

---

### Post by htseb on 2010-08-03
[COLOR=Indigo][COLOR=Black]Here is a description of a  successful installation of Ubuntu 10.04 Lucid Lynx Desktop Edition on an  
HP Mini (HP1120NR 16GB SSD)[/COLOR]
[/COLOR]
Beware of the following bug. 
   
[U]You must install the OS with a live ethernet cable connected to you  HP Mini, otherwise, the ethernet (eth0)
connection will not be detected.[/U] 

       see:     [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/559026](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/559026)

[Prior to installation, I remove the battery and power cable, push the  power switch to the On position for a second. Users of other brands of  netbook have reported problems with stale states in their machines if  the battery is left connected and this procedure will kill any static  memory. I haven't confirmed this on the HP Mini and it may be  superstition, but takes less time than changing configurations. ]  

Reconnect the power cable (but not the battery).   Connect a live, known  good ethernet cable from your router to the netbook.  Install Ubuntu.

Turn power off. Reconnect the battery.  Turn on the netbook.
Wired networking should be running.

 -to restore wireless networking (WiFi), 
  use the menu:  System/ Administration/Synaptic Package Manager  (upper  left corner)
    a. Click Reload first.
    b. Double-click and mark  'bcmwl-kernel-source' for installation.  Apply.    

Shutdown and Reboot.

---

### Post by Plumtreed on 2010-08-06
> **kalosaurusrex said:**
> Hey there.

I also have a HP Mini 1000 with the Netbook remix. To get the wifi working run:

```
sudo apt-get install bcmwl-kernel-source
```

Then reboot. and you should be good to go.

A


Many thanks, this worked for me, appreciate it!

---

### Post by nuwave on 2011-04-13
> **kalosaurusrex said:**
> Hey there.

I also have a HP Mini 1000 with the Netbook remix. To get the wifi working run:

```
sudo apt-get install bcmwl-kernel-source
```

Then reboot. and you should be good to go.

A

This worked for me when installing Ubuntu 10.04 though I had to enter the command several times and several restarts and it finally worked after 3 or 4 tries but it worked!

---

