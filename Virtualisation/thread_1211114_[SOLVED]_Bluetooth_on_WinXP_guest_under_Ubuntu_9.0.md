---
title: "[SOLVED] Bluetooth on WinXP guest under Ubuntu 9.04 Jaunty host"
date: 2009-07-12
forum: Virtualisation
---

### Post by zivley on 2009-07-12
Hi all,
I've been trying to make this work for a long time, I've tried so many things but only a combination of bits from here and there brought me to be successfully able to use Nokia PC Suite on my Win XP guest under the VirtualBox Ubuntu Jaunty host.
First of all I'll list my setup, perhaps your needs or hardware might be different, but the solution will match on most cases, adapting to the differences.
I have a Lenovo Thinkpad X61 Laptop with Ubuntu 9.04 Jaunty Jackalope 64Bit, which has an internal "Broadcom Corp BCM2045B" Bluetooth adaptor.
I installed the Sun VirtualBox 3.0.0 r49315 (Not OSE, but full version, recommended)
So after installing Win XP SP3 I didn't see any bluetooth devices detected and then the saga started, long story short, here's how I've made it work, step by step. Please make sure the VirtualBox program and its guests are closed during this whole procedure!

Open a terminal window for the following shell commands
Make sure your username is a member of the "vboxusers" group (this should have been already taken care by the VirtualBox installer, but we make sure)
```
sudo usermod -aG vboxusers <your username>
```

Now check what is the group ID of the "vboxuser" group, remember the number
```
grep vboxusers /etc/group | awk -F ":" '{print $3}'
```

Now we need to search for the "usbfs" file, it's better to do while a USB device is plugged in, in my case it was at '/sys/bus/usb/drivers' and it will be most probably there for you too, remember this path too, we'll need this and the previous GID number for the next step

Open/Edit the '/etc/fstab' file

```
gksu gedit /etc/fstab &
```

Add this lines to the end, replacing the path to 'usbfs' and the group ID with yours (devgid=XXX)
```

# For USB access with Virtualbox
none /sys/bus/usb/drivers usbfs devgid=129,devmode=664 0 0

```
Now we need to remount the filesystem
```
sudo mount -a
```
Running ```
cat /etc/mtab | grep usbfs
``` should give you something like this:
```
none /sys/bus/usb/drivers usbfs rw,devgid=129,devmode=664 0 0

```
which means the filesystem is mounted, now is time to see if it works, open VirtualBox, start the guest OS and you will hopefully see the new hardware detected wizard pops up, the automatic install will take care of the rest!
Hope this helps!

---

### Post by lavadisco on 2009-10-15
Thanks for the tutorial, but this did not work for me. Any idea why?

EDIT: Nevermind, it works! Thanks!

---

### Post by nvikram on 2009-10-15
Wow, I really wanted to find out how to get USB support working in virtualbox. Great step-by-step tutorial. I will definetly be trying this out soon.:D

Thanks.

---

### Post by AlexanderV on 2009-10-23
All the steps went smooth, but my Bluetooth had not appeared in WinXP guest...
Any suggestions where to dig for solution?

WinXP+SP3 under Virtualbox 3.0.8 r53138, host - Kubuntu 9.04, HW: DELL XPS M1210, Bluetooth internal...

---

### Post by zivley on 2009-10-23
Any USB device you want to use on the guest should be detected first by the host.
When you open the virtual machine usb settings and click the button to add a device, what do you have in the list of detected devices available to add?
Perhaps you didn't select the right one, so paste here the list of devices names and I'll try to help you chose the right one.

---

### Post by AlexanderV on 2009-10-26
Ah, yes! It's (Broadcom Corp BCM2045) appeared in the list of USB devices I can add in my virtual machine.
Thanks for tipping!
[SOLVED]

---

### Post by jl2035 on 2010-03-10
I can connect usb devices with virtual machine, but not bluetooth. This tutorial didn't change anything for me. I want bluetooth to work in virtual macines...

---

### Post by zivley on 2010-03-10
For now, please forget the guest and let's try to focus on the host first.
Is the bluetooth device you're trying to use connected to the computer?
Is it a portable device or is it onboard?
If it's portable, such as a dongle stick, run this in command line first

```
tail -f /var/log/messages
```

and then plug the device, it should run a few lines with the detected device and some info, paste the info here please.

To stop the command line capture just do Ctrl+C

---

