---
title: "Will my system specs work for a web server?"
date: 2012-02-16
forum: Server Platforms
---

### Post by helios16v on 2012-02-16
I received a free Windows 95 PC from a friend of mine because it would no longer start, so I changed the power supply it started up like a charm. I later installed Windows Server 2003.. But let's be real here.. I want an open-source server.

Now the problem hottie age of the computer, I don't know what distro of the Ubuntu family to use that iwill be resource lite enough to run on a 533MHz Intel Celeron with only 128MB of RAM. I removed the CD-ROM in place of a 4th hard drive for optimal web storage.

This is only going to be used for my personal builds for old computers I bring back to life so I'm trying to make it happen without spending much. The most I was willing to go would be a bigger heatsink and maybe over lock the CPU a bit.

I'm really lost on what distro to use though, I wanted to stick with the Ubuntu family of distros as I had some trouble with Mint and Debian distros in the past, Ubuntu just kinda works out of the box.. Or rather, out of the Internet :P

Please post some distros that will be kind to my dinosaur PC! Posting the recommended system specs for each distro would also be greatly appreciated!

---

### Post by helios16v on 2012-02-17
OH BOY!! I feel like a huge idiot lol!

I just realized I was looking at the Ubuntu Desktop System Requirements, I didn't even notice that they were much smaller for Ubuntu Server, it only needs 300MHz *check* and 128MB of RAM *check*

Solved my own problem lol

---

### Post by brent1975 on 2012-02-17
after doing a little search it looks like the minimum for server edition is 


[LIST]
[*]300 MHz x86 processor 
[*]128 MiB of system memory (RAM) 
[*]1 GB of disk space 
[*]Graphics card and monitor capable of 640x480
[/LIST]
Are you comfortable with SSH or command line administering? If so then You would be able to run ubuntu server. I would recommend getting the 10.04 LTS for the long term support. However the 12.04 LTS will be coming out hear real soon.  


I would say for a simple little site (not trying to reinvent google :D) and samba shares which is what you mentioned that you want to do this would be fine. 



Install it and login and run top and watch the load and memory usage.. If anything you may want to get some more ram for the system. 



Just curious how did server 2003 run on that system?

---

### Post by lisati on 2012-02-17
A year or two back I managed to put a basic Ubuntu server system on a machine running @ 133MHz, with a 3Gb hard drive and 64Mb of RAM, so a server should be do-able on your system.

---

### Post by Lars Noodén on 2012-02-17
For lower system requirements than Apache 2, you might look at the web server [nginx](http://nginx.org/en/).

---

### Post by helios16v on 2012-02-17
> **brent1975 said:**
> Just curious how did server 2003 run on that system?

It was okay I guess, not well enough to keep it but it did have a GUI to work off of which was nice. It was a hefty resource hog though! It ran fine on my 533mhz as it requires 550mhz so the difference wasn't huge but it's recommended to have 256MB of RAM and I only have half of that.

---

### Post by Dry Lips on 2012-02-19
> **lisati said:**
> A year or two back I managed to put a basic Ubuntu server system on a machine running @ 133MHz, with a 3Gb hard drive and 64Mb of RAM, so a server should be do-able on your system.

I had Ubuntu server 8.04 installed on a machine with a 230mhz CPU (I think), 64mb ram and 6 gig hdd. I even managed installing phpBB on it, but it really struggled with Joomla.

---

