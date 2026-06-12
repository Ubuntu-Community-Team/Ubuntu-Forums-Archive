---
title: "Switch off fglrx driver for virtualized physical Ubuntu partition"
date: 2015-08-22
forum: Virtualisation
---

### Post by daharn on 2015-08-22
[COLOR=#333333]I have set up a combined dual boot/Virtualbox system with Windows 8.1 as my main OS and a Ubuntu 14.04 LTS hard drive which can also be accessed as a virtual machine by VirtualBox using [/COLOR][this guide]("http://lifehacker.com/how-to-dual-boot-and-virtualize-the-same-partition-on-y-493223329")[COLOR=#333333][FONT=Lucida Grande]. 

[/FONT][/COLOR][FONT=verdana][COLOR=#333333]I would like to use the proprietary fglrx drivers for my ATI Radeon R9 285x when I actually boot into Ubuntu because I expect better performance, and even more for the most trivial reason that the fan of my VGA is running much louder when using the open source driver. But when I install them, I am no longer able to access my Ubuntu desktop via VirtualBox and get stuck in Login-loop, most likely because it can't load the proper drivers.

Is it possible to let the system switch between the fglrx driver and the Virtualbox-guest-addition-driver, depending on whether it is booted regularly or in a virtual machine?[/COLOR][/FONT]

---

### Post by TheFu on 2015-08-22
This is just a guess, 
Try reinstalling virtualbox drivers for the hostOS and then when booting into the guestOS, reinstall the guest-additions.

Don't know if this will help or not, but video drivers are tied into the kernel and so are vbox drivers.  Would be worth having a snapshot of the system before doing this.

Just reread your 1st post.  You have the same OS install available by dual boot AND through virtualbox?  I haven't a clue how to solve the GPU driver issue - since when dual booting, it sees real hardware and the real GPU, but inside virtualbox it only see the vboxGPU driver. I wouldn't think that was possible.

---

### Post by daharn on 2015-08-23
> **TheFu said:**
> Try reinstalling virtualbox drivers for the hostOS

I'm not sure what you mean by this. However, reinstalling guest addations via tty (since I doesn't let me start Xserver) fails, regardless if I try to mount the iso or install them via apt-get.

You might be on the right track considering certain kernel modules not being loaded or being overwritten, although ```
lsmod
``` inside the virtual ubuntu yields the following:

[ATTACH=CONFIG]264008[/ATTACH]

So it seems the virtualbox kernel modules like vboxvideo are loaded but can not be used.

EDIT: Yes, it is possible, apart from the driver issue, it works surprisingly well and is not too hard to accomplish (see the provided link). 

You are of course right that the hardware is different in both cases. Originally, I was thinking of detecting which hardware is used during boot and then choosing the corresponding driver / blacklisting the other one. But this seems hard to achieve...

---

### Post by daharn on 2015-08-27
I managed to solve it, although it took me some time:

When I was booting my virtual machine, the corresponding virtualbox kernel modules and graphic drivers were loaded. However, it turned out that the libraries for GLX were still AMD-related. Fortunately, the fglrx driver software provides an easy switch command from amd to intel, so all that needed to be done was executing

```
sudo /usr/lib/fglrx/switchlibglx intel
```  

and restart lightdm.

To have this executed automatically during boot, I created a file named "checkvga.conf" in /etc/init/ reading

```
# Checks if VGA belongs to virtual machine

description      "Checks if VGA belongs to virtual machine"


start on starting lightdm


script
    if test -f /proc/modules &&  grep -q vboxguest /proc/modules 2>/dev/null; then
    /usr/lib/fglrx/switchlibglx intel
    restart lightdm
    fi
end script
``` 

I had to put in the "restart lightdm" command to get it to work reliable, although I originally had assumed that "start on starting lightdm" would have been enough to have this command executed before lightdm was launched the first time. The reason might be that actually, X is required to be restarted, since there might have  already been an instance of it to display the splash screen during boot. If someone knows, please enlighten me.

---

