---
title: "[SOLVED] usb-printing on XP using virtualbox"
date: 2008-04-03
forum: Virtualisation
---

### Post by larsdk on 2008-04-03
Hi there,

I have a virtualbox running XP and it works fine. I have uncommented the default USB settings in Gutsy and I seem to have USB access, but when I want to install the driver in XP virtualbox complaints that it "failed to attach the USB device Canon CAPT USB Printer [0100] to the virtual machine" and further "Failed to create a proxy device for the USB device (Error: VERR_FILE_NOT_FOUND)

Any suggestions as to solve to this (very annoying) problem of mine would be very much appreciated :)

Lars

---

### Post by linuxbeatswin on 2008-04-03
> **larsdk said:**
> Hi there,

I have a virtualbox running XP and it works fine. I have uncommented the default USB settings in Gutsy and I seem to have USB access, but when I want to install the driver in XP virtualbox complaints that it "failed to attach the USB device Canon CAPT USB Printer [0100] to the virtual machine" and further "Failed to create a proxy device for the USB device (Error: VERR_FILE_NOT_FOUND)

Any suggestions as to solve to this (very annoying) problem of mine would be very much appreciated :)

Lars

This is the same problem that I am dealing with. I'm currently looking at a book, "Hacking Linux", plus some of my other Linux textbooks from school. If I find something, I will definitely post it.
Hopefully, someone will be able to solve this problem for us, eh?

---

### Post by jml75 on 2008-04-06
Hi all,

Here is how I did it in Hardy (8.04).

1 - Create a group named "usbusers" and put yourself in it.
```

sudo groupadd usbusers
sudo gpasswd -a <yourusername> usbusers

```

2 - Modify the rules in file "/etc/udev/rules.d/40-permissions.rules"

```

Change the lines :

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device",	MODE="0664"

To :

# USB devices (usbfs replacement)
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GROUP="usbusers", MODE="0664"
SUBSYSTEM=="usb_device",	MODE="0664"

```

3 - Then reboot the computer.

4 - Open Virtualbox and select in the list on the left pane the VM you want to print from.

5 - Click on the "USB" item in the right pane to edit the USB prefs.

6 - Click on the "Add device" button to add a filter and select your printer from the list and click on the "Ok" button.

7 - Start your VM and Windows should detect your printer.

---

### Post by larsdk on 2008-04-07
@jm75 

In 7.10 the line in the file is

SUBSYSTEM=="usb_device",	MODE="0664"

to which I had already added the groub vboxusers, but now I will give it a try with the additional 

SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", GROUP="usbusers", MODE="0664"

I'll post it here if it works :)

---

### Post by adric22 on 2008-04-07
i am having the same problem with a little Brother P-Touch thermal label printer.   I have done all of the things mentioned in this forum.  But my XP running inside of virtualbox does not see any USB devices.

I have also installed the closed-source version of virtualbox that does support USB.

On the virtualbox menu while running a session, when I click devices, usb-devices, it shows a list of all of the USB devices connected to my PC but they are all gray and cannot be clicked on.  When I go into the settings of a virtual machine that is not currently running, I do get a list and I can add the filter for the device I need.  But it is still not seen in my XP session once I start it.

What am I doing wrong here?

---

### Post by larsdk on 2008-04-07
:lolflag:

now, the very easies solution of them all did the trick (for me at least)

add this line

```
none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0
```

to your /etc/fstab file. Just make sure that 1002 is your vboxusers group (or your usbusers group).

Lars

---

### Post by adric22 on 2008-04-08
> now, the very easies solution of them all did the trick (for me at least)

add this line

Code:

none /proc/bus/usb usbfs devgid=1002,devmode=664 0 0

to your /etc/fstab file. Just make sure that 1002 is your vboxusers group (or your usbusers group).

YEAH BABY!  That did it.  Funny thing is, I had seen a similar post to this before and tried it and it did not work.  But where you told me to use the number of the group (in this case, 1001 was my vbox group) the other post I had read actually had me putting the name of the group in there, which apparently does not work.

So.. thanks!

---

### Post by Mr Mookie on 2008-04-22
I wish I could say this worked for me...

I've tried editing /etc/fstab with no luck..

I've tried:

sudo gedit /etc/init.d/mountdevsubfs.sh

#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs  /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

I've even tried:

sudo gedit /etc/init.d/mountdevsubfs.sh

and replacing 0666 for 0664 under the USB subsystem..


I still cannot see the USB settings in virtualbox..

I was hoping that upgrading to 8.04 would help but nothing changed as far as vbox goes. I'm pretty sure I've just messed up more things now. Any help would be appreciated.

---

### Post by theZoid on 2008-04-22
> **Mr Mookie said:**
> I wish I could say this worked for me...

I've tried editing /etc/fstab with no luck..

I've tried:

sudo gedit /etc/init.d/mountdevsubfs.sh

#
# Magic to make /proc/bus/usb work
#
mkdir -p /dev/bus/usb/.usbfs
domount usbfs  /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
ln -s .usbfs/devices /dev/bus/usb/devices
mount --rbind /dev/bus/usb /proc/bus/usb

I've even tried:

sudo gedit /etc/init.d/mountdevsubfs.sh

and replacing 0666 for 0664 under the USB subsystem..


I still cannot see the USB settings in virtualbox..

I was hoping that upgrading to 8.04 would help but nothing changed as far as vbox goes. I'm pretty sure I've just messed up more things now. Any help would be appreciated.

Start over, it works in Hardy Heron.  Do everything on this page...I had a situation where my scanner was working, but it wouldn't recognize the printer.  All is well now.  Just make sure you dot your i's etc properly.  BTW, I uncommented the "magic" section per you above in addtion as I did that in gutsy.

---

### Post by alexrichardson on 2008-04-29
> **Mr Mookie said:**
> I wish I could say this worked for me...


I still cannot see the USB settings in virtualbox..

I was hoping that upgrading to 8.04 would help but nothing changed as far as vbox goes. I'm pretty sure I've just messed up more things now. Any help would be appreciated.

Sounds to me like you might be running the Open Source Edition of Virtualbox.  It does not currently support USB - which I found out after trying those other steps first.

---

### Post by theZoid on 2008-04-29
> **alexrichardson said:**
> Sounds to me like you might be running the Open Source Edition of Virtualbox.  It does not currently support USB - which I found out after trying those other steps first.

I've written a guide to using usb with non-free VB in Gutsy/Hardy here:

[http://forum.notebookreview.com/showthread.php?t=242936](http://forum.notebookreview.com/showthread.php?t=242936)

---

### Post by Mr Mookie on 2008-05-07
Thanks for the reply on this. You were correct about the OSE Version. I thought these fixes made the OSE version able to use the USB. 

I've now installed the new "Sun xVMVirtualbox" 1.6 in Hardy; followed the same instructions and my USB is working great. Thanks again.

---

