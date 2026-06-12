---
title: "How would you deploy Ubuntu to a lot of schools?"
date: 2012-05-21
forum: The Cafe
---

### Post by ZarathustraDK on 2012-05-21
Looking for some guidance on a reasonable deployment/administration-setup.

The scenario is as follows:
- You got a bunch of schools, way more than you'd care to support manually.
- You've got the infrastructure to deliver and set up the boxes, so no worries there.
- All schools are members of the same domain.
- All PC's use the same student-oriented image.
- No on-site people have admin-rights.
- Schools may request install of repo-available software.

How would you deploy the pc's/What would you use for imaging? How would you administrate the pc's, and what would you use?
Create my own repos, or use the official ones?
Remote desktop-solution?

Basically I'm looking for the optimal deployment/admin-setup given the above circumstances. I have my own rudimentary setup in mind, but I'd like to hear your take on how you'd setup the above and what systems you'd use. It's easy to think of a solution; but transitioning from one deployment system to another can be messy, so I'd like to be armed with as much info as possible before I make any (hopefully not bad) choices.

---

### Post by Lucradia on 2012-05-21
There's a remote imaging program for Linux if I recall. You can also use WAKE ON LAN for each PC so that you can wake them up for imaging. Novell used a special desktop-seeing software that allowed the class teacher to see what the users were doing on the desktop (Windows though.) I did a silly thing one day though and booted Ubuntu on the machine, and of course, he couldn't see what I was doing via the program, as I bypassed Novell login.

You should probably lock the BIOS down with a password after setting it so it can boot from network first, then harddrive second. BIOS Password should be something tieable to each machine so that you don't have the same password for each one.

novell also has it so that when you logout of the computer, it will clear everything instantly that you put on the computer, effectively, re-imaging it as soon as you logout (to a degree.) In linux, you can call a script to do a diff search on the local machine, and see what files have been changed, added and removed, then undo all said changes. You can also do this by calling the diff script to base its search off of a file / folder on a network computer (IE: The image server) and have it look in a specific folder and then diff search the local machine based on that. (IE: META-INFO Folders in Java)

---

### Post by Lars Noodén on 2012-05-21
In addition to locking the BIOS, you should also consider locking Grub so that it is not possible for people to easily enter recovery mode.  It might be a good idea to disable booting from CD, floppy (if there is one) and USB.  Some of the older BIOS don't give you that flexibility.

Once you have the hard drives imaged, you could keep them in sync with Puppet or Radmind.  To get them to that point you might want a custom CD image or serve one over PXE.  I used to use a PXE server in the lab and it was a fast way to install from a CD image without the slowness and unreliableness of an actual CD.

---

### Post by ZarathustraDK on 2012-05-21
Nice info, especially on the puppet and radmind-part.

I don't think we'll be doing any remote imaging anytime soon, the bandwidth can't handle it (or rather the bandwidth of the recipients). That's not a problem though as we have a dedicated room for imaging. It's also the reason why I'm interested in your opinion on letting the boxes update from the official repositories instead of custom repos on our own network.

---

### Post by Lynceus on 2012-05-21
My dad is  principal of a school, here in Belgium. 
He installed Linux on almost all the computers using an installation cd.
He said it took a lot of time but he likes to work with computers.

I think you just have to reach the people in charge of the school or the people that handle the computers on that school, and show them that is is safer and better to use Linux.
Then they have to have the drive and knowhow to install and configure it on all the pc's.

Edit: i haven't read your post correctly so my comment is rather irrelevant  :)

---

### Post by Dr. C on 2012-05-21
I would suggest [FOG]("http://www.fogproject.org/") for imaging and image managmenet. One can easilly set this up on a virtual machine on Ubuntu using Virtualbox. 

One can also mirror the offical repos locally or more likly a subset of all the applcations. This really depends on how many computers there are in one location. The tradeoff is the work of setting this up vs the bandwith of repeatedly downloading the same application for multiple machines.

You may also wish to contact Canonical directly [http://www.ubuntu.com/business/services/overview]("http://www.ubuntu.com/business/services/overview"). One of the advantages of Ubuntu is one can use as much or as little paid support and one needs. For a large depolyment this is well worth considering as paid support may well end up saving time and money in the long run.

---

### Post by Purplerob on 2012-05-21
Or set up a central server that handles every account and connect to it with thin clients. You can use ltsp and then the students can switch computers and keep all their data, plus you only have to manage one computer.

---

### Post by Lars Noodén on 2012-05-21
> **ZarathustraDK said:**
> Nice info, especially on the puppet and radmind-part.

I don't think we'll be doing any remote imaging anytime soon, the bandwidth can't handle it (or rather the bandwidth of the recipients). That's not a problem though as we have a dedicated room for imaging. It's also the reason why I'm interested in your opinion on letting the boxes update from the official repositories instead of custom repos on our own network.

Some things you can do to save bandwidth include running web traffic through a cache like Squid or Varnish inside the lab network.  Apt can be set to use the cache.  That's set in /etc/apt/apt.conf when you do the installation.  For best results, update one machine and then when that is finished, then update the others.  They'll use the cache and will go quickly.  Be sure to allocate enough space in the cache.  With this scenario, the external repository gets used only once, thus saving bandwidth.  

[http://www.debian-administration.org/articles/177](http://www.debian-administration.org/articles/177)

Another to consider, in addition to the cache, might be Apt-P2P.  It should also improve performance.

YMMV.

---

### Post by KiwiNZ on 2012-05-21
In the past I have used boot servers and jump start to deploy .

---

### Post by Lars Noodén on 2012-05-21
> **KiwiNZ said:**
> In the past I have used boot servers and jump start to deploy .

What is jump start?  Is it like [Kickstart](https://help.ubuntu.com/community/KickstartCompatibility)/preseed?  I've used kickstart plus post-install scripts to populate lab computers.  It worked ok but was tedious to arrive at just the configurations I needed.

---

### Post by KiwiNZ on 2012-05-21
This will give you some idea

[http://aput.net/~jheiss/js/jumpstart_disk.html](http://aput.net/~jheiss/js/jumpstart_disk.html)

---

### Post by mips on 2012-05-21
See [http://mybroadband.co.za/vb/showthread.php/395247-Large-desktop-installation-base-management](http://mybroadband.co.za/vb/showthread.php/395247-Large-desktop-installation-base-management) for some good info.

---

### Post by ZarathustraDK on 2012-05-22
Landscape would be a perfect solution, but it's just darn expensive. $100 a year per node quickly eats up the Windows-tax-saving, and makes it harder to propose to management as a viable solution.

---

