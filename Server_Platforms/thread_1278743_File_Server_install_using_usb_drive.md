---
title: "File Server install using usb drive"
date: 2009-09-29
forum: Server Platforms
---

### Post by snuffy47 on 2009-09-29
Looking for some help and advice
 
I would like to build a file server(samba) using 2 x 1T hardrives in a RAID 0 I think
 
Is it possible to load the server os on a usb drive and then have all storage on the 1T drives.
 
Or am I better off to use an older 16 or 20G HD for the server OS?
 
After I get this setup I would like to also have a webpage setup using likely PHP but that will be down the road.

---

### Post by undecim on 2009-09-29
You can do that, yes, but I don't see why you couldn't put the OS on the 1T drives with the storage. USB drives are slow, and having to pull OS information from a USB drive would slow you down a lot. Also, if you mean a flash drive, you should know that flash drives can only take so many writes before they give out.

Another thing I'd like to mention: RAID 0 is designed to increase speed, but it decreases reliability. If one drive goes out, then you lose all data from both drives. It would be better to go with a RAID 1, which increases reliability with a small decrease to speed and half the storage. The speed decrease shouldn't be noticeable if all your file transactions are being done over the network (unless you have  gigabit lan on both sending and recieving computers on the same network)

Also, a lamp stack (linux, apache, mysql, php) is easily setup by installing "lamp-server". I think the server install even lets you create it during the install process.

---

### Post by Lars Noodén on 2009-09-30
Yes, it's possible to run the system off a USB drive.  Just have it plugged in when you do your installation.  As to speed, it's going to be slower, but most of the processes will have been loaded in RAM, so the speed of the USB drive should not matter that much unless swap starts to get used.  

If what you are doing is very specific, and you have everything configured the way you like it, and you have whittled away every single app you are not using, and there is RAM left over, you could roll your system into busybox and boot that from a usb flash drive.  But that might not give the returns on your time that you want.

---

### Post by snuffy47 on 2009-09-30
Well I from the 2 replies I will not go with a usb drive.
 
As for the storage on the computer.  I would still like to keep the OS separate from the storage drives.  Likey use a older 16G drive I have.
 
I would like to touch on the cofiguration of the drives.  I will be using external USB drives to back up my pictures so through other forums it was mentioned that I would not need a RAID setup.  My original plan was linux software raid 5.
I was hoping I could make the 2 x 1T drives so as a 2T drive with expandablity.
 
Once my harddrive wishes are figured out is there a good how too for setting up samba up.

---

### Post by Mighty_Joe on 2009-09-30
> **snuffy47 said:**
> Well I from the 2 replies I will not go with a usb drive.


I don't see why not.  Speed is relative. Is a USB install "slower" than a hard drive install? Sure, but a file server isn't an interactive device, so you'd probably never notice. I run Jaunty from a 8GB USB drive ([see my posts here]("http://ubuntuforums.org/showthread.php?t=1193680")) and it runs fine.  
I've also built a low-power [network storage "appliance"]("http://ubuntuforums.org/showthread.php?t=1244304&highlight=nas").  I ended up putting the OS and the data on the same drive. My primary concern was power consumption, so having only one drive was the most efficient setup.
As for samba howto, [look here]("https://help.ubuntu.com/community/SettingUpSamba")

---

### Post by snuffy47 on 2009-09-30
Joe I will read over our posts thanx for the info.
 
What would you recommend to a hardrive setup. I currently have 2x1T drives but I could buy another if required.

---

### Post by Mighty_Joe on 2009-09-30
If your file server were strictly for files alone, I'd be pretty comfortable with a flash drive as the OS drive.  Flash drives can wear out, so when you start installing things like Apache that can do lots of logging, you are increasing the writes (reads don't count) on the drive and increasing the chance of failure.  
Of course, you can mitigate the wear by moving high-use files (cache, logs) into memory or onto your non-flash drives and using a larger flash drive (flash drives use wear-leveling to spread around the memory use. The larger the drive, the longer it will last).

---

### Post by KillaB7 on 2009-10-07
I'd also like to run Ubuntu Server from USB/RAM allowing my storage HD's to spin down when not in use.

I built an Intel D945GCLF2D based system to replace a D-Link DNS-323 and amalgamate PBX, OpenVPN, and DLNA (for PS3) into one box, similar to the following:
[http://www.isyougeekedup.com/intel-d945gclf2-dual-core-atom-server-performance/](http://www.isyougeekedup.com/intel-d945gclf2-dual-core-atom-server-performance/)

Does anyone know of a more up to date guide for running off of a USB thumbdrive and RamDrive?  I'm trying to piece things together using various links, but there seem to be multiple methods (as expected).
[http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/822001690931](http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/822001690931)
[https://wiki.ubuntu.com/BootToRAM](https://wiki.ubuntu.com/BootToRAM)
[https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash](https://help.ubuntu.com/community/aufsRootFileSystemOnUsbFlash)

---

### Post by Mighty_Joe on 2009-10-08
> **KillaB7 said:**
> Does anyone know of a more up to date guide for running off of a USB thumbdrive and RamDrive?  

I just run it off the flash drive like a normal hard drive.  The link (to a post to a link. . .) I posted earlier has tweaks like moving caching and logging to tmpfs, but nothing fancy like running directly from RAM.

---

### Post by KillaB7 on 2009-10-10
Here's a recent howto (using AUFS) for anyone else that's interested:
[http://xercestech.com/custom-ubuntu-server-usb-stick-part1.geek](http://xercestech.com/custom-ubuntu-server-usb-stick-part1.geek)
[http://xercestech.com/custom-ubuntu-server-usb-stick-part2.geek](http://xercestech.com/custom-ubuntu-server-usb-stick-part2.geek)

---

