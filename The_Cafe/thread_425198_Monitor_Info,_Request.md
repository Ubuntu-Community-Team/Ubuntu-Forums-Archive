---
title: "Monitor Info, Request"
date: 2007-04-27
forum: The Cafe
---

### Post by DoctorMO on 2007-04-27
Hello again,

I'm after a few people to send me information about their monitors, if they sent me information before (through the hardware profiles request) then I can add this info to that; but more importantly I need to understand how dual monitors effect the output, so anyone with more than one monitor, even 2 different monitors connected to the same machine run this:

sudo apt-get install ddccontrol
sudo ddcprobe > ~/Desktop/monitor.txt

and simply email me the monitor.txt file on your desktop.

Thanks everybody.

---

### Post by DoctorMO on 2007-04-27
Apologies, someone pointed out that dccprobe is in the xresprobe package not the dcccontrol package.

Do please run this if you have dual or triple monitors, it would help an awful lot.

---

### Post by DoctorMO on 2007-04-27
Oh please, pretty please with sugar on top?

---

### Post by jiminycricket on 2007-04-27
Hi Doctor Mo, does it matter if we're using Twinview (nVidia's) or Xinerama?

---

### Post by DoctorMO on 2007-04-27
Not at all, the way in which the monitors are being used is not as important as is the fact that the computer knows they exist and knows to send a I2C request to find out what they are.

---

### Post by PatrickMay16 on 2007-04-27
Whoops! Ah! My nuts.

patrick@ubuntu:~$ sudo apt-get install ddccontrol
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ddccontrol

---

### Post by maniacmusician on 2007-04-27
> **PatrickMay16 said:**
> Whoops! Ah! My nuts.

patrick@ubuntu:~$ sudo apt-get install ddccontrol
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ddccontrol
it's in universe...do you have that enabled? also, if you're still using Dapper, it might not be in those repositories.

---

### Post by DoctorMO on 2007-04-27
You might want to try 'sudo apt-get install xresprobe' anyway and as far as I know it's installed by default.

---

### Post by PatrickMay16 on 2007-04-27
Oh, yeah. Seems like the program "ddcprobe" is already installed. I've emailed you the resulting file now.

---

### Post by DoctorMO on 2007-04-28
Thanks to those who sent info, I'm going to have to talk to the developers and try and reconcile a number of points since all their programs are built to show the user a very slim amount of information, when all I need is an id. so hopefully they can provide a switch of some kind.

---

### Post by slimdog360 on 2007-04-28
Do you want only people with dual monitors to do this?

---

### Post by DoctorMO on 2007-04-28
I don't need anyone else to do this just yet. I'll be posting an update in time. for the moment some will and some won't detect,

---

### Post by DoctorMO on 2007-05-02
OK anyone with a monitor, both CRTs, Flat-screens, via vesa or visa digital or even laptop screens run the following:

sudo ddccontrol -p -vv > ~/Desktop/monitor.txt; sudo ddcprobe > ~/Desktop/monitor2.txt

Oh and let me know if you sent me a hardware profile before and what your computer name was (it ties together so I can tell what video card the monitor is plugged into)

---

