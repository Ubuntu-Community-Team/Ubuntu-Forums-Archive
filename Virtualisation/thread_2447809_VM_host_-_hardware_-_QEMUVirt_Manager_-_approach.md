---
title: "VM host - hardware - QEMU/Virt Manager - approach"
date: 2020-07-26
forum: Virtualisation
---

### Post by aljames2 on 2020-07-26
I have a i5 - quad core with 24 gigs of Ram.  I'd like some recommendations on which version of Ubuntu to serve as host for virtualization.  While at it, I'm thinking may need to switch the hardware to a low power, Ryzen with more cores since the VM host needs to run 24/7.  Part of my scheme would be to create a VM desktop for my wife to use for her stuff, (she likes to click on things & fill out surveys ](*,)), so she doesn't accidentally mess up the host machine.  I have other ideas for VM, such as using a VM to run the Unifi controller on, and another to play around with some other Linux distros.  I cold use some ideas to think about before getting started.  Thanks!

---

### Post by Dennis N on 2020-07-26
For my personal use, I have QEMU/KVM with Ubuntu MATE 18.04 host and QEMU/KVM with Fedora Workstation host. Both using virt-manager. Both on the same computer. This computer has Intel i3-8100 processor (4 cores) and 16 GB ram.  

Fedora was easy to setup since it has one command to install all the needed packages on the host. Ubuntu didn't offer that when I installed on the Ubuntu MATE host; it was necessary to find a guide online to see what packages to install.

The end result: not much difference between the two. Fedora handles inserted USBs better - it automatically passes through to the guest when using the guest OS. Ubuntu requires a manual redirect.  I would be satisfied using either, and much prefer either to VirtualBox application that I tried years ago.

---

### Post by TheFu on 2020-08-01
I have 3 systems all running 16.04 + KVM + libvirt with a lite GUI - usually openbox or fvwm.  I haven't logged into 2 of them directly on the console in months, but I ssh in routinely. Those others are mostly storage servers.

There are hundreds of things you can "self-host", just comes down to having the CPU, RAM, and storage.

[LIST=1]
[*]Core i5-750 (1st Gen) It was supposed to be retired, but getting everything moved somewhere else will need to wait until another Ryzen gets installed.  
[LIST]
[*]All VMs have been migrated off this system as of about a month ago.
[/LIST]
Web server; all internal things like photo galleries, webapps I've written for work/fun, but access is through a reverse proxy server below
Print server
Scanning server
NFS server
[*]Pentium G3258 
[LIST]
[*] Plex Server
[*] Kodi (seldom used) - Kodi runs on Raspberry Pi hw near viewing rooms.
[*] Translation server
[*] Calibre ebooks
[*]Nextcloud VM w/ Wallabag, ZNC, and a few other tiny things. These are LAN-only systems.
[/LIST]
TV Recording Server (controlled by some custom bash/perl scripts)
NFS server
[*]Ryzen 5 2600
[LIST]
[*]Blog
[*]Main Desktop (20.04)
[*]Reverse Proxy (and probably 20 non-DBMS websites); All web traffic goes through this machine which filters the bad guys and terminates all SSL traffic, including for internal-only systems
[*]Email gateway (spam blocker)
[*]Zimbra Email (communications, calendar, LDAP, Addressbooks)
[*]VPN
[*]Old Desktop (16.04)
[*]Windows desktop for financial programs - used to be a media center that recorded TV
[*]LAN Router (opnSense)
[/LIST]
Transcoding directly on the HW.
Translation server.
[/LIST]

All systems are monitored.

Look have the "sovereign project" for more ideas. [https://github.com/sovereign/sovereign](https://github.com/sovereign/sovereign)

Saw a Ryzen 3600 + MB combo for $214 last week at a local computer retailer.  Sadly, the MB they include isn't one I'd ever buy.  They sell a MB just like my other Ryzen has, which would be acceptable, but the "bundle" deal doesn't work then. The cheap MB I want + that 3600 is $280 - not a great deal.  Too bad I missed out on the $80 1600 AF deals last fall. I'm kicking myself over that.  Well, all CPUs get cheaper over time, until they get really expensive as used parts for businesses who cannot upgrade.

Stuff I would miss if it were gone. ZNC, Wallabag, Nextcloud-News, Plex, email gateway+Zimbra and the NFS servers. The OS drive for the pentium box failed in June. That system and all those services on it were unavailable for a few days.  "News" is an RSS feed puller. Basically, stuff to read on the web. Anything I don't read immediately gets sent to Wallabag to be read later.  Both provide a centralized view of world news so regardless of the client I'm using, I never see any articles/stories that I've already seen.  That is huge.  My tablet, desktop, laptop, phone all have the same view.  

Stuff to read later - wallabag - which lets me pull those articles without junk, to the phone/tablet to read while in relaxing outside, in waiting rooms or sitting in the park on a sunny day. Of course, the tablet also has plenty of novels from the Calibre server, but that isn't a "need now" thing. That's a update with a new book when the current 10 books on the tablet are done.

Nextcloud would be handy for many families, but we were already well-organized due to my work in document management for 2 prior employers. While nextcloud here has read-only access to some stuff - photos, music, selected documents, I've found the search capability to such and prefer to use **recoll**.  Recoll indexes everything on my NFS server daily early in the morning. It is like having my own google for all files here.

$ recoll -b -t -q "$@"
Recoll has a GUI too, if that's needed, and a way to generate HTML output. Through helpers, it can index all sorts of files and file metadata.

Anyway, that should give you some ideas.

---

