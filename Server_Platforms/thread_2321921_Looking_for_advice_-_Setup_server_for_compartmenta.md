---
title: "Looking for advice - Setup server for compartmentalized development and hosting"
date: 2016-04-25
forum: Server Platforms
---

### Post by roderick on 2016-04-25
I have recently purchased a new server for development and hosting. specs are:

CPU: i7-6700 3.4-4 GHz 4-core, 8 threads (Intel HD 530)
RAM:	16 GB DDR4-2133
Storage: 3x500 GB 7200rpm HD
Networking: 2x Gigabit Ethernet ports

I want to have a base install and everything else in a container (compartmentalized).

I plan to do packaging and will require a container for development, packaging, etc. to keep things separate from the underlying server (ease of portability later).

I also plan to host some services like a wiki, blog, webpage, and these should be easy to move to another server or cloud should I choose to do so.

I think I should be looking at LXD for the containers.

My first main question is for the base system, should I do LVM and/or RAID (5) to protect the underlying server platform? How will this impact any "containers" I build later? Should I use Ext4 or Zfs?

Second, once I have the main server established, I want to have a dedicated virtual machine environment to develop, package, build, code, etc. In the past, i would simply use virt-manager and KVM to build a vm and do my work in it. do I still do that or would I use LXD to achieve similar result and how?

Cheers,
Rod

---

### Post by TheFu on 2016-04-25
Most of your questions ask for opinions, not facts.  What follows are my opinions, with which others may not agree.

Containers are great for non-production, non-internet, uses.  That means internal use only. They simply haven't been around long enough to be trusted to be secure.  IMHO.  If you are hosting cat-videos, internally, fine.  If you have end-user logins, nope. Don't trust any containers at this point. Maybe around 2020 and after 1,000,000 breaches of container systems has happened AND been fixed, I'll change my mind.  New and shinny doesn't mean secure.  People pushing containers are like the handsome, ex-sports-star, home security system sales guy who comes to your door on a nice Saturday afternoon promising that your family will be safe, but only if you buy this system and monthly monitoring for $29.95.  Video cameras can be added for just $10/month more!  [http://www.wired.com/2016/01/xfinitys-security-system-flaws-open-homes-to-thieves/](http://www.wired.com/2016/01/xfinitys-security-system-flaws-open-homes-to-thieves/)  and [http://www.dslreports.com/shownews/Comcasts-Xfinity-Home-Security-System-Trivial-to-Hack-136007](http://www.dslreports.com/shownews/Comcasts-Xfinity-Home-Security-System-Trivial-to-Hack-136007) .... just sayin'.  OTOH, someone needs to be in that first group running containers.  Thank you for living on the bleeding edge.  Watch out for pretty people, smiling, pushing containers.  There are many things about containers and the processes around them that are just scary - like the fact that people can post complete containers with whatever settings they like and 100 other people will download and use those from untrustworthy sources. I'm still amazed this is even a thing. TANSTAAFL [https://en.wikipedia.org/wiki/There_ain't_no_such_thing_as_a_free_lunch](https://en.wikipedia.org/wiki/There_ain't_no_such_thing_as_a_free_lunch)

I always use LVM on physical disks. ALWAYS.  It is about convenience and flexibility and snapshots for backups.

RAID anything usually isn't worth while. RAID is for 1 purpose - HA. Nothing else.  You still must have backups even if you have RAID.  There are times when RAID storage gets messed up and there is only 1 way to recover - from backups.  Actually, automatic, versioned, backups are critical - 30-120 days worth.  However, the 1 time I'm inclined to use RAID at home is for virtual machines.  I use mdadm (Linux software RAID) for that. Those areas are still backed up. Backups are 1000x more important than RAID.  Ok - think I've pushed that enough. ;)

Which file system? Depends on your needs. There are many other choices that you haven't listed.  If you don't have a compelling reason to use any of the non-standard file systems, I'd stick with ext4.  ZFS is cool, but ... there are trade-offs. Definitely do lots of research about ZFS before choosing it.  Ext4 is fine, IMHO.  I use it, but wasn't an early adopter of ext4.  I have run systems with ZFS on Solaris for years.  With just 3 drives, ZFS doesn't make sense.  I think 6 disks is the sweet spot for ZFS and you'll want 2G of RAM for every 1TB of storage managed if you use most of the ZFS features.  There are low-RAM setups.  Also ECC RAM is basically mandatory for ZFS to ensure no corruption.

I don't understand the last question, but that is probably just my ignorance about lxd/lxc showing.
For the greatest stability, keep the hostOS minimal.
* no GUI
* only VM and container tools - bridge utils ; It is handy to have 4 NICs and only let the hostOS use 1. The others are for the VMs.
* storage management - LVM, mdadm
* Backup tool of choice
Nothing else.
Don't install anything extra - nothing extra beyond the base systems perl,  python, ruby stuff.  When the container is broken out from into the hostOS, don't want to provide any extra tools. 

Sorry for sharing so many opinions. Didn't mean to. Honest.

---

### Post by roderick on 2016-04-25
I dont mind bleeding edge. I was a MOTU developer circa 2008-2011, and just been out of the game a few years. This is all for personal learning and getting up to speed on new technologies.

I do want to setup the base system as stable as possible and that means a stable file system and base OS and yep - backups. The containers vs. VM's are more about putting things into a compartment and keeping the base system pristine and clean and secure from the toybox I want to play in. 

The blog, wiki, webpage are more form my proof of concept and playing. These will all be behind a separate physical firewall and only have the minimal ports/proxy enabled to expose the specific service (e.g. port 80).

Thanks for the opinion and warning about the new and shiny, but Im not too scared of those bits.

---

