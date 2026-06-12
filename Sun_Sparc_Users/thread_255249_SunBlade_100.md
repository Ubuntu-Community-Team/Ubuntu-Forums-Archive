---
title: "SunBlade 100"
date: 2006-09-11
forum: Sun Sparc Users
---

### Post by Franjo Kumer on 2006-09-11
Hi, everybody

I'm using SunBlade 100 workstation and would like to instal ubuntu sever 6.06.1 sparc.

After command 

ok boot cdrom

comes answer :

Alocated 8 Meg of memory ...
Loaded kernel version 2.6.15
Loading inital ram disk ...
Ilegal instruction

ok

My sparc workstation has processor
500-MHz UltraSPARC[tm]-IIe, 64-bit
with 256 Megs of ram and two IDE disks with 90 Megs to use.

Is it possible to install ubuntu on that machine ????

Have nice day

:)

---

### Post by netztier on 2006-09-11
> **Franjo Kumer said:**
> 
Is it possible to install ubuntu on that machine ????


Yes it is possible by

[LIST]
[*]typing less question marks
[*]searching this forum for "sunblade" or "Blade 100"
[*]searching the archives of the Dapper Beta forums
[*]reading what is given as advice in these posts
[*]actually trying what is suggested in these posts
[*]indicating *in your forum question* what you have *actually* tried to make it work
[*]reporting back to the forum what has actually helped to solve the problem
[/LIST]

But of course you have done - or will do- all of this , haven't you? :evil: 

And before anyone blames me for not contributing, a list of forum threads:

[LIST]
[*][Failure to install on a "Sun Blade 100"]("http://www.ubuntuforums.org/showthread.php?t=209831&highlight=SunBlade")
[*][Dapper on Sun Blade 100]("http://www.ubuntuforums.org/showthread.php?t=210630&highlight=SunBlade")
[*][SunBlade100 install hangs]("http://http://www.ubuntuforums.org/showthread.php?t=229572&highlight=SunBlade")
[*][Sunblade 100 and 150 -- ide=nodma]("http://www.ubuntuforums.org/showthread.php?t=240420&highlight=SunBlade")
[/LIST]

kind regards

Marc

---

### Post by rimtech on 2006-09-11
Hi Franjo, I only today got ubuntu onto my sun blade 100. 

**This may be the most comprehensive guide to getting a working install of ubuntu on a sun blade 100 by netbooting so listen up...**

The cdrom drive in my ubuntu machine is dead, and all other replacements I have tried don't work either. And yes, i have the most recent OBP installed.

I have read similar issues with others having this problem that you are aswell. Since I did not have this problem I can only recommend you follow my steps to get a working install, as it worked for me. 

Before we begin i should note that I am primarily a windows user so this will reference some windows apps assuming you are using windows also, if you are not using windows if you do a little digging you can also find the linux equivilent.

I chose to "netboot" install ubuntu, as none of the cdrom drives i have tried really worked.

Things you will need:

A windows box, i used xp.
a working network infrastructure
a RARP server [http://www.panix.com/~perin/rarpd.zip](http://www.panix.com/~perin/rarpd.zip)
a TFTP server [http://tftpd32.jounin.net/](http://tftpd32.jounin.net/)
a web server, which im not going to explain as you could use anything from a free host, to IIS, to apache, whatever.
a sparc install cd for ubuntu

the ubuntu netboot image which can be found here:
[http://ports.ubuntu.com/ubuntu-ports/dists/dapper/main/installer-sparc/current/images/sparc64/netboot/2.6/boot.img](http://ports.ubuntu.com/ubuntu-ports/dists/dapper/main/installer-sparc/current/images/sparc64/netboot/2.6/boot.img)



Now what happens with a netboot to my understanding is this:

1. The Sun Blade 100 attempts to find an IP using it's MAC address.
2. The sun blade 100 then attempts to download through tftp a boot file to run. This will be our ubuntu netboot image.

Now my network is 192.168.1.XXX, so we have to assign our sun box an ip address, i chose 192.168.1.110 out of randomness, 

so extract the RARP server and install it and set it up to assign whatever ip you chose. with the software I have listed and linked to here all you gotta do is make a new file inside of the main software directory, called rarpd.tbl and insert the following into rarpd.tbl:
```
00.03.BA.08.61.50 192.168.1.110
```
You will note that the MAC address of my sun machine is 00.03.BA.08.61.50. If you need to figure out your mac address on the sun machine try booting from network, type "boot net" from the OBP and it will show you the mac address.

Next you need to set up your tftp server, so extract it.
Using the tftpd i provided click on "settings" at the bottom and set up the "Base directory". This can be any directory of your choosing. Place the boot image file boot.img inside of this "base directory". So, we have the sun machine getting an IP from our RARP server, next it is going to look for a netboot file... in a very specific format. You have to convert the IP address into hexadecimal and remove the dots...

It's really easy to do, there's even a tool here that can do it for you:
[http://www.kloth.net/services/iplocate.php]("http://www.kloth.net/services/iplocate.php")

My result for 192.168.1.110 was **C0A8016E**.
So, inside of your tftp "base directory" you must insert the boot.img file and RENAME IT to C0A8016E or whatever you hex result was on the IP address.

Once you have completed these steps, you are good to go. 
launch rarpd.exe
launch tftpd32.exe

Your windows machine is now ready.
Next, you have to tell your sun machine to boot it.

There are 2 problems here.
The sun blade 100's IDE controller is very buggy, so we need the kernel argument ide=nodma to disable udma modes. This is easy

The default install on the netboot image is a desktop install, with full blown x and everything, which always failed for me.

You gotta tell it to do a server only install.

inside of your cd is a folder called preseed, inside of the preseed folder is a file called ubuntu-server.seed

place ubuntu-server.seed onto a web server, i had a local server running on 192.168.1.50, which is also my xp machine.

**OK.**

So far we have followed all of the steps I had to take to get everything to a workable point.

The only thing you have to do now is on the sun blade 100...
doing "boot net" simply was not enough on this machine. We need to pass a few arguments, the first to tell the kernel to disable dma and the second is to tell the installer to install the server template, not desktop. 

boot net ide=nodma preseed/url=http://192.168.1.50/ubuntu-server.seed 

Follow the steps on your screen, and you should get a working install.

When it reboots, it will fail to load linux.

from the silo boot prompt on the first reboot from the silo prompt you must do ide=nodma again... the command to enter at the silo prompt is "Linux ide=nodma"

```
SILO> Linux ide=nodma
```

your linux box will then boot, you will log in, and to prevent linux from failing to load every time inside of your silo config file you will put append="ide=nodma"

so open up your silo config file with an editor, i used nano...

**sudo nano -w /boot/silo.conf**

and add [COLOR="Red"]append="ide=nodma"[/COLOR]

```
image=/vmlinuz
label=Linux
append="ide=nodma"
initrd=/initrd.img
```

now do the same thing to /etc/silo.conf aswell...

**sudo nano -w /etc/silo.conf**

Press Control+X to exit nano, it will ask you to save changes, press y to save changed.

You are now finished and if you want to get a gui (desktop version of ubuntu) installed on your machine just type "sudo apt-get install ubuntu-desktop"

I had so many problems getting ubuntu onto this machine, but it's not ubuntu's fault. Other linux distros have similar issues getting onto the sun blade 100.

I know it seems like alot of work, but it only takes about 5 or 10 mins to set up the netboot and once it's done it's done. Good luck and god speed.

---

### Post by rimtech on 2006-09-11
P.S. if you can't find ubuntu-server.seed the just copy and paste this into a text file and save it as ubuntu-server.seed:


```
# Don't install usplash.
d-i	base-installer/kernel/linux/extra-packages-2.6	string
# Desktop system not installed; don't waste time and disk space copying it.
d-i	archive-copier/desktop-task	string ubuntu-standard
d-i	archive-copier/ship-task	string
# Only install the standard system and language packs.
d-i	pkgsel/install-pattern	string ~t^ubuntu-standard$
d-i	pkgsel/language-pack-patterns	string
# No language support packages.
d-i	pkgsel/install-language-support	boolean false

```

---

### Post by rimtech on 2006-09-11
if you are going to desktop route and installing the GUI (ie by running apt-get install ubuntu-desktop), you will have to manually edit /etc/X11/xorg.conf and add

```
Option "ReferenceClock" "29.500"
```

into the Device section.

---

### Post by switlikbob on 2007-12-13
I just want to update this:

Option "ReferenceClock" "29.500"

I have been trying to get my X running on a SunBlade 100 for 2 weeks now.  I finally ran across a thread that has the correct entry that actually works!

Option "ReferenceClock" "29.500MHz"

Without the MHz at the end of the line, this would not work for me.

---

### Post by soosh on 2007-12-14
> **switlikbob said:**
> I just want to update this:

Option "ReferenceClock" "29.500"

I have been trying to get my X running on a SunBlade 100 for 2 weeks now.  I finally ran across a thread that has the correct entry that actually works!

Option "ReferenceClock" "29.500MHz"

Without the MHz at the end of the line, this would not work for me.


I don't know if it matters, but for my Sun Blade 100, 29.500 didn't seem to work.  I found another suggestion to try **28.636 Mhz** and that seems to work better.

---

