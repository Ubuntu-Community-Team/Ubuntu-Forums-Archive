---
title: "Help developing strategy for home network"
date: 2009-05-03
forum: The Cafe
---

### Post by davidmigl on 2009-05-03
I need your input in order to develop an overall strategy/gameplan for implementing a home network. I need your recommendations on both hardware and software.

Usage scenario is 2-3 computers; web browsing, documents, and photos/photo editing. The existing "infrastructure" is two aging PCs (4-5+ yrs old) running Windows XP connected through a dsl modem/router combo.

I would like to replace this with a more robust "business class solution." By that I mean a server to centralize photos, music, and documents, share a printer, and perform backups of all the computers, with business class workstations. I need this to be remotely administrable (I am a college student/designated family IT nerd).

For hardware, I am thinking about buying used Dell business-class hardware. Specifically, a power edge tower server (server) and optiplex/vostro (for the workstations). However, I am open to recommendations for whatever will get me the most Ubuntu compatibility.

Thanks for your help!!
David

---

### Post by gn2 on 2009-05-03
Sounds a bit unecessary when all you might need is to buy a NAS for central storage.

I have a Linksys NSLU2 and it's great.

---

### Post by mr.propre on 2009-05-03
Sounds fun, but a little bit overkill if you ask me.
The hardware is to expensive for just a few PC's and the upkeep in energy is High.

Trust me on this, you are better of with 'basic' consumer/geek hardware than with HBA controllers of &#8364;250/p (for example). A small low-energy micro-atx with 2 lan card, an unmanaged switch and a NAS will do the trick as long as you don't need a media server.

The atx can handle as firewall, DHCP, backup, cronjobs, bittorent ...

---

### Post by RandomJoe on 2009-05-03
If you can get the used hardware for free (or at least VERY cheap) then that could be a nice deal.  I used to get "old" 2-3 year old machines from a previous employer as they replaced with newer kit.  But I sure wouldn't pay much for it.

"Business class" especially for desktop PCs generally isn't saying much.  They are good for data-entry and other basic duties but usually don't have very fancy hardware - especially video cards.  Be sure that's really what you want!  One of the main reasons businesses like them so much is the hardware is kept the same through the life of a given model - much easier to support an entire building of machines.  This can mean it's well behind the leading edge of technology, too.

I bought a Dell PowerEdge a while back for home.  Gawd, what a noisy beast!  I have replaced the worst of the cooling fans in it, but it's still quite noticeable when running.  Knowing what I know now, I'd definitely go a different route!  Now, if you desire something with the removable drives in caddies, that might be different - I don't consider it worth the expense though.  I like being able to just get something from Newegg to upgrade / fix the system.  Opening the case to change a drive just doesn't take that long.  My server just has a standard SATA four-port card in it, four regular SATA drives from Newegg, and I use software RAID.

Now, I'm looking at the lowest-power system that would do what I want.  I've been pretty impressed with what the Atom-based systems can do, although I haven't tried pushing one very hard as a server yet.

If you really do just want to share files and a printer, then one of the NAS boxes may be perfect.  You can share a printer the same way, no need for a dedicated server.  My only concern with the NAS boxes is heat - some that I've come across run awfully warm or even hot, which makes me wonder about the life expectancy of the hard drive.

---

### Post by Roasted on 2009-05-03
Why not just get a system rigged up for NAS like the others suggested? When I ran into this issue, I just slapped 2 more SATA drives in my own personal computer and fired up Samba. Now everybody has auto-synchronize programs to back their stuff up to the one SATA drive I put in here, and the 2nd SATA drive I put in gets rsync'd to twice a day so I have a redundant copy of the network data.

It was a simple solution for me considering I simply utilized existing hardware, with the exception of the two 250gb SATA drives I bought to add into it.

---

### Post by davidmigl on 2009-05-04
Thanks for the input. Sounds like I *was* going a bit overkill. I just want something that's going to run fine for a long time without a lot of attention.

Do you have any specific product recommendations for the following?
[LIST]
[*]NAS
[*]Remote administration solutions (vnc over ssh?)
[*]backup/restore software
[/LIST]

Thanks in advance.

---

### Post by Helios1276 on 2009-05-04
There was a massive home server thread around here but I haven't the energy to look, I'm personally using a Qnap TS- 109 pro ii, runs on linux out of the box so that is nice. Power consumption is very low also.

---

### Post by MaxIBoy on 2009-05-04
First off, your server should be capable of sharing files and printers between multiple clients over a LAN and over the Internet. There's a specific kind of hardware which is perfect for this. The name for this hardware is "cheap." There is probably some event near your place of residence, where people drop off unused computers, and at the end of the week, they all go to the [s]landfill[/s] e-waste disposal facility. Those computers are fair game, and I guarantee you that most of them will handle this job admirably. A 486 with 64 MB RAM will probably do, but see if you can hold out for a Pentium MMX with 128 MB. Even the computers that don't work might still have extra parts you can use.

A word of warning: don't use old hard drives! They have a habit of failing on you. Buy an 80-gig model for $34, you'll thank yourself later.




If you are sharing a printer on a Linux computer with a Windows computer: Sure, you could set up Samba on the print server, but it's actually much easier to setup CUPS on Windows.
[http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html](http://www.owlfish.com/thoughts/winipp-cups-2003-07-20.html)



Sharing files between Linux and Windows: Either install Samba on the server and set it up for filesharing (one days work) or get NFS working on Windows (I honestly have no idea how hard this is, I've never tried.)



See if you can do this with only Ubuntu computers for the workstations, as Ubuntu makes it really easy to set up home networks like this, and taking Windows out of the picture reduces the amount of pain and suffering involved.



You don't need "business class" workstations for image editing, unless you plan to edit 25-megapixel shots (you don't.) Maybe some moderate CPU "juice" for some of the more-advanced distortions and filters in the GIMP. One of [these]("http://system76.com/product_info.php?cPath=27&products_id=80") (pick the Core 2 Duo, 2 gigs RAM, and Radeon 4350, brings the price tag up to $550) will be perfect for image editing, basic 3D stuff, and low-end gaming. You could probably get an equivalent used system (I.E. was a monster machine three years ago) on the cheap.

---

### Post by davidmigl on 2009-05-05
Yeah, I understand what you're saying about the server not needing to be anything too powerful. Fortunately I have a couple spare systems laying around (433 mhz and 2ghz) that I could easily make a server out of.

What about remote administration? I.e. me, on college campus, being able to view mom's desktop at home to do administrative/troubleshooting tasks. It would be great if I could VNC into my home network and remotely administer any box on it. I'd like to have something where I don't have to worry about it getting hacked into.

So what's the best option? VNC over SSH onto the server and then what? I can tell already this is going to get complicated....

---

### Post by gtr32 on 2009-05-05
> **davidmigl said:**
> So what's the best option? VNC over SSH onto the server and then what? I can tell already this is going to get complicated....

All *nix boxes or Windows as well? If *nix then SSH and, if necessary, X Windows. From Win to *nix machine, use XMing as X client. It's not really that complicated, I can connect from work to home and also to my wife's work.

---

### Post by MaxIBoy on 2009-05-05
[img]http://img516.imageshack.us/img516/8617/supdawgencryption.jpg[/img]

---

### Post by steev182 on 2009-05-05
Sounds a bit like my network...

Me
-Dell SC440 (dual core xeon, 3GB Ram, 250GB system, 1tb data) ubuntu 9.04
-Apple MacBook dual booting OSX 10.5.6 and ubuntu 9.04
-xbox360 in Lounge
-iPhone

Mum
-Apple MacBook OSX 10.5.6

What I would say first is that it's loud! After that, it functions as my main PC and when I come to replacing my phone it'll be with something powered by android.
If I did it again, I would still have the Dell SC440 but I'd have a Samsung Q210, an HTC Magic, and most importantly a self built server using a dual core atom, in a large chassis, with plenty of hard disk bays, probably using opensolaris or bsd and ZFS for storage.

---

### Post by thisllub on 2009-05-05
It is a resource pig (Java apps usually are) but there are some extremely good features for document management via WEB / DAV /CIFS / NFS.

It has built in integration with OpenOffice and many more features.

A very interesting project that could be to open source what SharePoint is to Windows.
[http://www.alfresco.com/](http://www.alfresco.com/)

---

