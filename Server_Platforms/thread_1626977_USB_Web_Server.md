---
title: "USB Web Server"
date: 2010-11-20
forum: Server Platforms
---

### Post by xtiano77 on 2010-11-20
Just like the title says, I am trying to find out how to setup a web server in a USB flash or portable drive. The intent is so I can take it to work and plug it into a Windows machine and run it from there, then come home and plug it into my Ubuntu machine and run it from there also. This is sort of a new concept to me so please forgive the ignorance.

System:

Intel Motherboard
Intel Processor: Dual Core 2 Quad
2GB Memory
500GB Hard Drive
Ubuntu 10.10 32 bit

---

### Post by arrrghhh on 2010-11-21
> **xtiano77 said:**
> Just like the title says, I am trying to find out how to setup a web server in a USB flash or portable drive. The intent is so I can take it to work and plug it into a Windows machine and run it from there, then come home and plug it into my Ubuntu machine and run it from there also. This is sort of a new concept to me so please forgive the ignorance.

Well that is an interesting concept.  Not sure if there's any "out-of-the-box" solutions for this or not.

However, you said you'd like to be able to just plug it into a Windows machine and it'll "just work" - that won't "just work" unfortunately, at least not in the manner that I'm assuming you envision :p

What you could do is have a bootable USB key with Ubuntu on it, and make it persistent - so your data is saved.  Then install your apache server, whatever else you need, and then you'd have a web server on a USB key - but wherever you take it you'll have to reboot the machine and that computer will have to be able to boot via USB - most modern machines can, but for example my Alienware laptop from 2004 strangely cannot boot via USB, but our crappy Dell PC's at work from 2003 can.  So if the machine is older, you may (or may not) run into issues with not being able to boot from USB.  Plus, you may have to muck with their BIOS settings if it doesn't try to boot from USB by default.

With all of that said, it's certainly doable - but it'll probably be very slow.  Booting from a USB key is kinda painful - if you have a lot of RAM and a fast system, it's not quite as bad... but still not like booting natively from a hdd.  Hope that helps!

---

### Post by craigp84 on 2010-11-21
Was there not a distro, puppy linux or something like that, did exactly this.

You could boot natively from the USB.

You could double click a .bat on the USB from windows and it would launch the same image in a QEMU virtual machine.

You could ./launch.sh or whatever and it would do the same from an already booted Linux host.

Was a while back, probably dead by now (since it hasn't taken over the world and those are the only 2 possible outcomes with free software ;-) )

---

### Post by tristan on 2010-11-21
Check out Abyss Webserver. Windows/Linux. Very full featured,small and fast and the windows version will run portably from a usb stick (the default install is only a few Mb IIRC).

It's free from [http://www.aprelium.com/abyssws/](http://www.aprelium.com/abyssws/)

---

### Post by xtiano77 on 2010-11-24
First of all I want to express my gratitude to those who viewed my original posting and especially to those who took the time to entertain my question[s]. That being said, I found a portable web server, USBWebserver, which I am currently running on a Windows machine of a USB drive. I also managed to install XAMPP for Linux (LAMP) on both of my Linux machines at home; however, the only draw back I have noticed so far is that I have to go to as in root user in order to start the server every time I turn on my machine. Now, while looking around for an NAS drive/enclosure I saw the following on the Tigerdirect site:

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2532995&CatId=2670](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2532995&CatId=2670)

Would it be possible to install XAMPP in a NAS drive like this so once started every computer in the network can access it without the need of restarting every time? Thanks in advance for your help and advice.

---

### Post by richardelima on 2012-01-27
As much as I know there´s no portable version of any webserver in linux, so whatever version u use, u need to install it in your distro.

What u can do if u dual boot windows and linux is share databases, mysql share same structure and folders, so you can "copy" files of database into another system and they will work.  I´ve heard this is only true for myisam databases and not for innodb, so check it out.

PD: I use dropbox to sync those folders and works OK.

---

### Post by Lars Noodén on 2012-01-27
One thing you might do is to install a minimal server distro to your USB drive.  If the machine can then boot from USB, you have your web server.  Most recently made machines can boot from the USB drive. 

Apache is more or less the default web server around the net, but you might also be interested in trying nginx.  The basic features are the same but it consumes a lot fewer system resources.

---

