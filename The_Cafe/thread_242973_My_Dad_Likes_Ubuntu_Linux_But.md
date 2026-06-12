---
title: "My Dad Likes Ubuntu Linux But"
date: 2006-08-24
forum: The Cafe
---

### Post by Omnios on 2006-08-24
Hi I managed to talk my dad into trying Ubuntu 6.06 and he realy likes it but has a slight problem with the modem port. Anyways even last night he told me he had it with windows as yet another virus has trashed his XP install. 

 Anyways the problem he is having is that before a big update his modem port was 14 and after the upgrade the modem port changed to 4. Now the problem is that the config file seems to be set up for port 14 so everytim he wants to connect to the internet he has to go through the network manager to reset his modem port to 4. Because of this he is still using XP for the web. Any suggestions on how to change the config to port 4?

---

### Post by Brunellus on 2006-08-24
wait, back up. "modem port"?

---

### Post by Omnios on 2006-08-24
> **Brunellus said:**
> wait, back up. "modem port"?

Modem port in /sytem/admin/networking. Modem connection properties modem and there is a modem port thing there.

 Basicly his dial up modem works out of the box the onlything sticking is the port problem he now has. He sets the post and it does not seem to save the new port number

---

### Post by IYY on 2006-08-26
And what's port 14 used for now? If it's nothing, maybe you could just link port 14 to port 4.

---

### Post by peabody on 2006-08-26
Port 14???  Last I remember about modems and comm ports, most comm ports stop around COMM4.

Just what kind of modem be running on that rig?

---

### Post by _simon_ on 2006-08-26
I thought there was only 3 com ports? Com 1 and 2 external, com 3 internal.

---

### Post by ComplexNumber on 2006-08-26
> **peabody said:**
> Port 14???  Last I remember about modems and comm ports, most comm ports stop around COMM4.

Just what kind of modem be running on that rig?
nope. there is usually no limit on the number of comm ports. all a comm port is is an arbitrary communication channel. apart form the first 2 or 3 that are usually of fixed use, the rest can be assigned to anything. whether something is assigned to comm 14 or comm 2452 or whateever, they are all the same.

---

### Post by peabody on 2006-08-26
> **ComplexNumber said:**
> nope. there is no limit on the number of comm ports. all a comm port is is an arbitrary communication channel.

In theory, but c'mon, in practice?  I have never seen a modem on COMM 14 on PC hardware.  Not saying it's impossible or can't happen, but I haven never seen it before in my life.

---

### Post by ComplexNumber on 2006-08-26
> I have never seen a modem on COMM 14 on PC hardware. actually, its quite likely. a new device or application is usually assigned to the next free comm port. for example, if you install the drivers to enable the pc to communicate with a mobile phone, for example, that may be assigned to comm 8. then if you buy a new mobile phone to a different manufacturer, but want to keep the old set up, then a new comm port must be used for the new mobile phone to communicate with your pc. it goes on like that. you'll be surprised just how many comm ports can be assigned. its also the case that previously  used comm ports aren't reused, so it can end up having (say) ports 5, 7, 8, 9, 10, 11, and 13 all unused because they used to be used for something else but aren't any more.

---

### Post by .t. on 2006-08-26
Err. On Linux, serial ports are not named. They have a file in /dev, like all other devices. On one of these serial ports will be your modem; there can be any number you like. Usually, /dev/modem is symlinked to one of these "files", which is named /dev/ttySn, where "n" is a number, and the first port starting at n=0. An update to udev probably changed this, and you can use udev's configuration to change it.

For instance, if your modem is at /dev/ttyS13 (COMM 14 in Windows), you could create a udev rule to change it to /dev/ttyS3, I think. Create a file in /etc/udev/rules.d/ called 010_modem.rules, with the below content:```
KERNEL="ttyS*", SYSFS{dev}=="x:xx", NAME="ttyS3"
```.
However, the SYSFS{dev} value of "x:xx" is non-existant, and you will have to find a value correct for your system to replace it with. Do that by running ```
udevinfo -ap /class/tty/ttyS13
``` Look where it says, "SYSFS{dev}==" and take the value that follows.

---

### Post by ComplexNumber on 2006-08-26
> Err. On Linux, serial ports are not named.
comm ports are a windows thing. i was just clarifying for a previous poster about them.

---

