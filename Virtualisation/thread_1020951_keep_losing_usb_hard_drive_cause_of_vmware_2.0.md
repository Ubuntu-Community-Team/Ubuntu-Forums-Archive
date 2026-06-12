---
title: "keep losing usb hard drive cause of vmware 2.0?"
date: 2008-12-24
forum: Virtualisation
---

### Post by evilbuntu on 2008-12-24
hi all

i recently installed vmware 2.0 on my ubuntu 8.04 server tower. everytime i boot the vmware it knocks out my external usb hard drive. now i can just as easily unplug the drive and put it back in to remount it when i finish in vm ware but is there an easier way to do this?

is there a way to scan my system for mountable usb devices without cutting the cords?

thanks all

update: no longer works just pulling the plugs. now i have to reboot
evilbuntu is online now Report Post   	

also does anyone know how to get the VM ware to use my ipod touch. the windows sees and installs drivers; but it doesnt show in my explorer and it seems the itunes doesnt want to.....


K figured out that i have to dismount the hard drive in windows and then shut it off in the usb VMWare settings before i shut down windows.

guess the vmware will share all usb things except a hard drive. once i totally removed it from windows it reappeared in ubunutu 1-2-3.

thanks

also i think my ipod may be messed up :(

---

### Post by dcstar on 2008-12-25
> **evilbuntu said:**
> hi all

i recently installed vmware 2.0 on my ubuntu 8.04 server tower. everytime i boot the vmware it knocks out my external usb hard drive. now i can just as easily unplug the drive and put it back in to remount it when i finish in vm ware but is there an easier way to do this?
.......

All USB devices are set in the particular VM's "Removable Devices" area, if you have them ticked from a previous use I believe that as soon as you start the VM they will be "grabbed" by the VM.

Simply untick them and they will remain available to the host O/S.

---

### Post by evilbuntu on 2008-12-26
yeah i figured that out. i dont remember having to do that with the last vmware dist lol, so it had me confused a bit for a while. 

if you dont untick them before you shut it down the host OS wont regrab them.

well luckily my ipod is not messed up. for some reason though the vmware and XP will actually see my ipod but it wont show up in itunes.........

---

