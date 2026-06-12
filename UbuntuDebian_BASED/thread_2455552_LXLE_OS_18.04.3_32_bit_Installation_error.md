---
title: "LXLE OS 18.04.3 32 bit Installation error"
date: 2020-12-22
forum: Ubuntu/Debian BASED
---

### Post by linuxwow on 2020-12-22
Hello everybody,
I recently found out about LXLE Linux and I decided to revive my old desktop pc with it.
lxle-18043-32.iso . I have successfully verified the integrity of the downloaded file.
I have burnt the DVD in slow speed with a max speed of 4x(used Roxio Creator Small Business on Windows 7 Home Premium 32 bit OS laptop).
I am trying to do erase entire disk and install lxle
__________________________________________________________________________________________________
Hardware Configuration:-


ASUS K8S-MX motherboard
CPU:-AMD Athlon 64 bit 2800+ (speed:- 1.8 Ghz)
RAM:- 2GB DDR400 (PC3200, 1st generation RAM, new RAM modules installed)
Storage:- SATA HDD 160GB (new disk installed)
BIOS is updated (not UEFI,it is the old type)
__________________________________________________________________________________________________
When I boot from the installation disk of an external usb dvd drive, I get this error:-


Error 1:-


/init: line3: can't open /dev/sr0: No medium found 
/init: line3: can't open /dev/sr0: No medium found 
dbus-daemon: fatal error setting up standard fds: Failed to open /dev/null: Permission denied
dbus-run-session: EOF reading address from bus daemon


If I boot from internal Dvd drive, I still get the same error without the first two lines which is 


dbus-daemon: fatal error setting up standard fds: Failed to open /dev/null: Permission denied
dbus-run-session: EOF reading address from bus daemon


Then installation proceeds without any errors asking me to restart to use the new installation.
When I click on "Restart now", once again errors appear :- 


Error 2:-


Online.


    Starting Message of the Day...


                    Starting /etc/rc.local Co
mpatibility...


    Starting LSB: disk temperature monitoring daemon...
    
 Starting  Daily apt download activities...
                    [121. 520181] rc.local[1000]: dbus-
daemn[1011]: [sessio uid=990 pid = 1011] Activating service name='org.gtk.vfs.Da
emon' reqested by ':1.0' (uid=990 pid=1024 comm="gio set /home/bodhi/Desktop/ub
iqity.desktop metad" label="unconfined")
                    [122.086427] rc.local[1000]:yes:sta
ndard output: Broken pipe


            [ 125.201282]. rc.local[1000]: dbus-daemon[1011]: [sess
ion uid=990 pid=1011] Successfully activated service 'org.gtk.vfs.Daemon'
                                [ 125.
614747] rc.local[1000]: dbus-daemon[1011]: [session uid=990 pid=1011] Activating
service name='org.gtk.vfs.Metadata' requested by ':1.0' (uid=990 pid=1024 comm=
"gio set /home/bodhi/Desktop/ubiquity.desktop meta" label="unconfined")
                                [ 125.7
25664] rc.local[1000]: dbus-daemon[1011]: [session uid=990 pid=1011] Successfull 
y activated service 'org.gtk.vfs.Metadata'
                      [ 125.737725] rc.local[1000]: A connec
ction to the bus can't be made


So, I manually restart the system and I come to the login screen where I enter
username and password. Afterwards , when everything seems to working normally I get logged 
out suddenly with the error:-




Error 3:- 


[ 63.179960] rc.local[1105]: sudo: unknown user: qwerty
                            [ 63.180604] rc.local
[1105]: sudo: unable to initialize policy plugin
                            [ 66.776894] rc.local[1105]: y
es: standard output: Broken pipe 


After this, I keep getting logged out, making me go through a login loop.
__________________________________________________________________________________________________
If I boot from bootable usb drive(used balenaEtcher), I get the error:-


[ 55.647496] usb 1-2: device descriptor read/64, error -110
[ 71.263469] usb 1-2: device descriptor read/64, error -110
[ 76.639497] usb 1-2: device descriptor read/64, error -110


after which the installation hangs.


__________________________________________________________________________________________________
Please help.

---

### Post by howefield on 2020-12-22
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

### Post by CelticWarrior on 2020-12-22
Welcome.

First of all, LXLE isn't an official Ubuntu derivative therefore you can't use the main sections of this forum for support. You don't have to do anything right now, it'll will be moved to the appropriate section soon.

Secondly, you have a 64-bit CPU. Why are you using 32-bit OSes? That it came with 32-bit Windows doesn't mean you can't use another 64-bit OS.
32-bit is being phased out faster then ever, even LXLE no longer supports it. Debian still does but the amount of options that once were are dwindling very fast.
Surely your 2GB of RAM are very tight for any comfortable usage nowadays but a 64-bit OS with a very light desktop environment is still doable.

---

### Post by gdesilva on 2020-12-22
I can vaguely remember seeing a similar error message with LXLE 18.04 recently. Unfortunately, I cannot recall how I fixed it but it may have been either using Etcher to burn the ISO (I used a USB not a DVD) or it was just by using a different USB drive (the first one was faulty - sorry cannot be definite on this. So, in your case you may want to try to burn a new DVD or try burning on a different machine or alternatively try the LiveUSB option instead.

As pointed out by CelticWarrior, if you have a 64bit CPU it is far better to use the 64bit version.


EDIT: Oops....did not see that you have already tried the USB option - so  above comment probably is of no use!

---

### Post by linuxwow on 2020-12-23
> **CelticWarrior said:**
> Welcome.

First of all, LXLE isn't an official Ubuntu derivative therefore you can't use the main sections of this forum for support. You don't have to do anything right now, it'll will be moved to the appropriate section soon.

Secondly, you have a 64-bit CPU. Why are you using 32-bit OSes? That it came with 32-bit Windows doesn't mean you can't use another 64-bit OS.
32-bit is being phased out faster then ever, even LXLE no longer supports it. Debian still does but the amount of options that once were are dwindling very fast.
Surely your 2GB of RAM are very tight for any comfortable usage nowadays but a 64-bit OS with a very light desktop environment is still doable.


Ok, I didn't know how to post this in a different section. I actually tried to post this in LXLE forum but they required that I apply for their membership. So I thought I will try here first.

I will try to install the 64 bit version then. I assumed the 32 bit version of the OS will run faster on the given hardware. I have also tried to install Zorin 32 bit and 64 bit, Linux Bodhi 64 bit on the same PC.
Zorin 32 bit and 64 bit OS get into a login loop before installation. I have to enter "zorin" as the username and leave password blank to continue. However, I get the "ubi-partman" crashed error after I proceed. Installation does not proceed even
to the extend of copying files.

Linux Bodhi 64 bit :- Hangs up in between the installation during copying files without any error and I will have manually shutdown and restart the system. I very much want to revive this PC with any Linux variant. Thank you

---

### Post by linuxwow on 2020-12-23
Can you suggest any other Linux variants similar to LXLE or lighter than LXLE? I will want to run some office based applications and browse the internet, that's all. Thanks

---

### Post by CelticWarrior on 2020-12-23
I suggest you check the HDD's health before anything else.

---

### Post by linuxwow on 2020-12-23
> **CelticWarrior said:**
> I suggest you check the HDD's health before anything else.


That is meaningful but I didn't do it because Windows Xp and Windows 7 install on the same HDD without any problems and also it is a new HDD. If I still checked it's health , what would be the best way to do it?
Will running the command :- 

[COLOR=#8F9699][FONT=Lato][I]sudo smartctl -a /dev/sdX

[/I][/FONT][/COLOR]from a live linux terminal/Gparted live cd check the health of the HDD ? If not, what is the best way to do it? 
Thanks

---

### Post by ajgreeny on 2020-12-24
The error you saw about the USB ***device descriptor read/64, error -110*** is because the power supply to the USB port is not sufficient enough for what it has been asked to do.

If you have, or can perhaps borrow, a separately powered USB hub it might overcome the problem you see at present when trying to use a USB live system.

---

### Post by linuxwow on 2020-12-25
> **ajgreeny said:**
> The error you saw about the USB ***device descriptor read/64, error -110*** is because the power supply to the USB port is not sufficient enough for what it has been asked to do.

If you have, or can perhaps borrow, a separately powered USB hub it might overcome the problem you see at present when trying to use a USB live system.

That is a good idea but I doubt if the BIOS of my motherboard will be able to detect a bootable usb drive connected to a self powered usb hub. I have updated the BIOS but it is still a very old motherboard. Also since I am able to install LXLE 32 bit with dvd drive (both internal and external usb dvd drive) I don't think it is necessary to continue to install using bootable usb drive. So I am trying is to make sure that the installation happens from the dvd without the post installation error that I mentioned. I am having a hard time trying to single out the faulty part of the process. As far as I can tell there is nothing wrong with the dvd, dvd drive or installation file. According to CelticWarrior HDD could be faulty but I have reasons to think otherwise as I previously mentioned. I will try to install the 64 bit version from dvd and see what happens. Thanks

---

