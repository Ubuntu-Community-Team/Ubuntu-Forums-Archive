---
title: "Xp from VB from live ubuntu"
date: 2011-12-13
forum: Virtualisation
---

### Post by x-tend on 2011-12-13
Hi

I'd like to run windows xp from VirtualBox from live (persistent) ubuntu usb.

Is it feasible, and would the setup performances be acceptable?
Could some better machine run this setup?
Is live ubuntu usb possible on USB3?

Thanks a lot in advance

---

### Post by CharlesA on 2011-12-15
It's probably possible if you used a persistent live usb. Might be a bit slow tho.

---

### Post by x-tend on 2011-12-16
> **CharlesA said:**
> It's probably possible if you used a persistent live usb. Might be a bit slow tho.

Thanks for the reply.

Could i make it reasonable fast (say around 70% of the static OS speed) with a faster hardware (mb, ddr3 ram, usb3) ?

---

### Post by CharlesA on 2011-12-16
> **x-tend said:**
> Thanks for the reply.

Could i make it reasonable fast (say around 70% of the static OS speed) with a faster hardware (mb, ddr3 ram, usb3) ?
Well running it live via USB will be a bit slower then running from a normal hard drive, but if you are using USB3, the speed difference shouldn't be too bad.

---

### Post by x-tend on 2011-12-18
Could someone with usb3 persistent live ubuntu, test this setup (xp from virtualbox).

It'd be greatly appreciated.

Thanks in advance.

---

### Post by Rebelli0us on 2011-12-22
Ubuntu runs fine on USB flash, though a little slow. I haven't seen any **bootable** USB3. OSes in Virtual Box don't know where they are hardware-wise, so XP should run fine, but it's a disk hog, I'd run Windows 2000, it's leaner, meaner and has fewer bugs.

---

### Post by x-tend on 2011-12-23
Thanks for the suggestion, maybe i'll try w2000 instead of xp, but slow (usb2) is not an option. And i expect for liveOS-VB-OS-App setup to be really slow with usb2.

Anyone with usb3 live persistent ubuntu ?

---

### Post by collisionystm on 2011-12-23
> **x-tend said:**
> Thanks for the suggestion, maybe i'll try w2000 instead of xp, but slow (usb2) is not an option. And i expect for liveOS-VB-OS-App setup to be really slow with usb2.

Anyone with usb3 live persistent ubuntu ?



Do you not have a USB to test it with?

It would work fine. 
The only delay you would have is the initial load of the program. Once the services for virtualbox are running it will work fine. You can only make a 4gb persistent partition (or so I have found ). However instead of this method, why dont you just make a live-windows xp disc?

[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

---

### Post by x-tend on 2011-12-23
> **collisionystm said:**
> Do you not have a USB to test it with?

It would work fine. 
The only delay you would have is the initial load of the program. Once the services for virtualbox are running it will work fine. You can only make a 4gb persistent partition (or so I have found ). However instead of this method, why dont you just make a live-windows xp disc?

[http://www.nu2.nu/pebuilder/](http://www.nu2.nu/pebuilder/)

I don't have a pci-usb3 controller at the moment (i put it in another comp which is not here). Anyway i even doubt that boot would be possible through pci controller (because of the driver).
If reports from guys here would be positive, i'd get a newer machine with usb3 board.

As for live xp, it is actually one of the 2 options, and probably much faster one.
But it's not possible to install apps directly with windows installer.. plugins must be made for each app you want to run (if plugin for the app doesnt exist already).

So, the solution with live windows is faster but harder to implement.

If you have usb3 live persistent ubuntu, would you mind to test the setup? :popcorn:

---

### Post by collisionystm on 2011-12-24
> **x-tend said:**
> I don't have a pci-usb3 controller at the moment (i put it in another comp which is not here). Anyway i even doubt that boot would be possible through pci controller (because of the driver).
If reports from guys here would be positive, i'd get a newer machine with usb3 board.

As for live xp, it is actually one of the 2 options, and probably much faster one.
But it's not possible to install apps directly with windows installer.. plugins must be made for each app you want to run (if plugin for the app doesnt exist already).

So, the solution with live windows is faster but harder to implement.

If you have usb3 live persistent ubuntu, would you mind to test the setup? :popcorn:

Ill try it and let you know what happens.

---

### Post by collisionystm on 2011-12-24
Its going to be 11.10 64bit LIVE 4gb persistent on SanDisk Cruzer in a USB 3.0 slot and XP 32bit SP3. Should have it up in about an hour or so.

---

### Post by collisionystm on 2011-12-24
well my xp iso was corrupt and i guess ill download it again later.

I booted a persistant ubuntu 11.10 64bit. Installed fglrx drivers, rebooted, worked.

installed virtualbox. also survived reboot.

ran ubuntu in vbox on live usb. i am sure it will install just fine.

screenshot included

---

### Post by x-tend on 2011-12-25
Thank you so much =D>

If you could test virtual xp from live usb3 ubuntu host, it'd be great.

By test i mean to run some heavier app like msaccess (or openoffice db), illustrator, photoshop, cad or alike (maybe some light game), if you have it of course. I'm interested in how responsive larger apps are.
Maybe you could run ATTO benchmark from virtual xp (especially small files would be interesting).

Thank you for your help and time.
Merry Christmas  ):P

edit:
pls ignore this about illustrator, ps and cad.. they're no doubt too large to install on this setup.

---

### Post by collisionystm on 2011-12-27
> **x-tend said:**
> Thank you so much =D>

If you could test virtual xp from live usb3 ubuntu host, it'd be great.

By test i mean to run some heavier app like msaccess (or openoffice db), illustrator, photoshop, cad or alike (maybe some light game), if you have it of course. I'm interested in how responsive larger apps are.
Maybe you could run ATTO benchmark from virtual xp (especially small files would be interesting).

Thank you for your help and time.
Merry Christmas  ):P

edit:
pls ignore this about illustrator, ps and cad.. they're no doubt too large to install on this setup.


Ill see what I can do! It was hard to find the time for this around the holidays lol

---

### Post by routed on 2011-12-27
If you had two reasonable sized flash drives you could have Ubuntu on one and the Virtualbox disk image on the other. Might work better than just one.

---

### Post by x-tend on 2011-12-27
@[collisionystm]("http://ubuntuforums.org/member.php?u=1249225") 
Of course, no prob, when (and if) you have time.

@[routed]("http://ubuntuforums.org/member.php?u=1512664")
A very interesting idea. The only way to find out how much (and whether) faster this approach would be, is to compare the two.
But i don't even think about suggesting it to [collisionystm.]("http://ubuntuforums.org/member.php?u=1249225") :-#

---

### Post by collisionystm on 2011-12-27
> **x-tend said:**
> @[collisionystm]("http://ubuntuforums.org/member.php?u=1249225") 
Of course, no prob, when (and if) you have time.

@[routed]("http://ubuntuforums.org/member.php?u=1512664")
A very interesting idea. The only way to find out how much (and whether) faster this approach would be, is to compare the two.
But i don't even think about suggesting it to [collisionystm.]("http://ubuntuforums.org/member.php?u=1249225") :-#

Let me see... I think I have a win 7 iso. Ill try that and quake 3d.

Also, if you have windows, you can use [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

It can create a usb drive with a portable virtualbox to run on any computer.

---

### Post by x-tend on 2011-12-27
> **collisionystm said:**
> Let me see... I think I have a win 7 iso. Ill try that and quake 3d.
Well i think quake 3d is way too heavy for that setup. One can't be expecting any performances with that game. I'd try something much lighter (comparable to a db).

I have already tried live usb2 persistent ubuntu and i had VB manually installed in it, but didnt install virtual OS, as i was quite sure with USB2 it'd be too slow.

Thanks

---

### Post by collisionystm on 2011-12-27
> **x-tend said:**
> Well i think quake 3d is way too heavy for that setup. One can't be expecting any performances with that game. I'd try something much lighter (comparable to a db).

I have already tried live usb2 persistent ubuntu and i had VB manually installed in it, but didnt install virtual OS, as i was quite sure with USB2 it'd be too slow.

Thanks

quake 3d is from the windows 98 days. it takes almost nothing to run it... but we will seee.................

---

