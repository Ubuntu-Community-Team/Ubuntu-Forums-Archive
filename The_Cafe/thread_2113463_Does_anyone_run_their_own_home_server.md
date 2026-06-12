---
title: "Does anyone run their own home server?"
date: 2013-02-07
forum: The Cafe
---

### Post by u-noob-tu on 2013-02-07
I'm thinking of turning one of my family's old PCs into a media and file server, just for kicks. I haven't been able to get it setup yet (won't boot to the CD for some reason, but Lubuntu installed just fine :confused:). I was just curious if anyone else has tried the same and what their experience has been. 

P.S. The server OS I'm aiming to use is called Zentyal, an Ubuntu-based server distro I have a little experience with.

---

### Post by ACubed10 on 2013-02-07
I turned this box into a Plex server so that I could stream movies, videos, music from my Ubuntu box to my Roku in my living room.  So in a way, yes I have

---

### Post by tgalati4 on 2013-02-07
I started with a Dapper Drake install in June 2006 and never turned it off--and it is still running today.  Then I kept adding services, so it became a home server.  I purchased a couple of used Dell PowerEdge rack servers a few years ago.  Big difference in performance:  1GHz Celeron versus 2CPU Xenon Dual-Core at 2.8GHz.  

I also built a freenas server ([http://nas4free.org](http://nas4free.org)) on a Pentium I 188MHz (overclock from 166MHz); 256MB RAM (maximum), whitebox, curbside PC.  I put in a SATA PCI card and a few terabytes of storage running ZFS.

---

### Post by Dragonbite on 2013-02-07
I run Zentyal, though not the latest one, on a Pentium 4 desktop.  It is based off of Ubuntu 10.04, not 12.04.  

Depending on the system you are trying to run this on, you may be running into the PAE kernel issue I have with my IBM Thinkpad.

Ubuntu 12.04 uses a kernel that requires PAE, while Lubuntu and Xubuntu, in 12.04, uses a non-PAE kernel and so can be booted on these systems without issue.

---

### Post by Dragonbite on 2013-02-07
An idea around this is to use the alternat install for Ubuntu 12.04 (it's a non-PAE kernel), and then install Zentyal on the existing installation (there are instructions somewhere there or in the Ubuntu wiki).

Unfortunately the non-PAE kernels are removed for 12.10 from even the alternate or mini or Lubuntu or Xubuntu installation. So after 12.04, you may have to look at other distributions but that really isn't necessary until 2017 (5 years support for servers).

---

### Post by Jakin on 2013-02-07
Absolutely, its not a complex server though. My router has a network HDD (320gb) i store backups there via SMB, and also share files with family, the "server" is always on for access, though all our computers maynot be- so it comes in handy.

---

### Post by Erik1984 on 2013-02-07
I briefly tried Ubuntu Server on a poor old Dell Optiplex the owner had dumped. Installation was very easy and with SSH I was able to manage it from both Windows (Putty) and Linux desktop. I only used it for torrents (deluge on server with web interface to manage it) and backup.

---

### Post by |{urse on 2013-02-07
I run a couple websites and a media server, mythbuntu and ubuntu-server/LAMPP. 0 downtime on either in 4 years, through no fault of my own lol.

---

### Post by CharlesA on 2013-02-07
I run mine as a file server/VM host.

Ubuntu 12.04.

---

### Post by naano on 2013-02-07
> **CharlesA said:**
> I run mine as a file server/VM host.

Ubuntu 12.04.

Same here! VM servers are especially useful when you need to work with multiple OS's and don't want to quintuple boot or whatnot;). I've also tried Plex, ncmpcpp, and a few other apps. All of this from a 3 year old desktop.

---

### Post by papibe on 2013-02-07
I have a IBM refurbish PC running 10.04. It serves as a home server and it runs:
[LIST]
[*]Backup server.
[*]DDNS client.
[*]File server (Samba and NFS shares).
[*]Media repository for XBMC and music clients.
[*]Torrent client (transmission-daemon).
[*]Webcast downloader (using by own scripts).
[*]DHCP server (dhcp3-server).
[*]DNS (bind9)
[/LIST]
Regards.

---

### Post by CharlesA on 2013-02-07
> **naano said:**
> Same here! VM servers are especially useful when you need to work with multiple OS's and don't want to quintuple boot or whatnot;). I've also tried Plex, ncmpcpp, and a few other apps. All of this from a 3 year old desktop.

Indeed. I've been running a Windows 2008 R2 machine for some documentation I am working on. Super fun stuff. Easier to deal with than having it set up on a physical box.

---

### Post by bfmetcalf on 2013-02-07
I'm running ArchLinuxArm on a Raspberry Pi to host a DLNA/Samba/Torrent server.  It has gone pretty well, now I just need to find a drive larger than 500GB for storing all my stuff.

---

### Post by ugm6hr on 2013-02-07
> **tgalati4 said:**
> I also built a freenas server ([http://nas4free.org](http://nas4free.org)) on a Pentium I 188MHz (overclock from 166MHz); 256MB RAM (maximum), whitebox, curbside PC.  I put in a SATA PCI card and a few terabytes of storage running ZFS.

If you just want a media / file server, I will second FreeNAS 7 (now NAS4Free). I have a similarly specced setup, although it was decommisioned last year in favour of a "nettop" media centre with XBMC and FTP server combined.

Zentyal is a small business server, so perhaps overkill for your needs? Though if this is more journey than destination - go for it!

---

### Post by collisionystm on 2013-02-07
I just run a Plex server on a 9 year old Compaq Presario laptop. Amd Sempron... 512mb of ram. 60GB Hard drive and a 1TB usb hard drive. Its a beast!

---

### Post by Roasted on 2013-02-07
> **tgalati4 said:**
> 

I also built a freenas server ([http://nas4free.org](http://nas4free.org)) on a Pentium I 188MHz (overclock from 166MHz); 256MB RAM (maximum), whitebox, curbside PC.  I put in a SATA PCI card and a few terabytes of storage running ZFS.

How on earth did you pull that off? Last I ran freenas zfs ate every little bit of CPU my quad core could throw at it...

On topic - I run a home server. It runs Ubuntu server on an i3 3220t with a 1tb hard drive for video surveillance and a mirror sized at 3tb with everything else. Everything else includes backups, subsonic, owncloud, videos which streams to the htpc, etc. I absolutely love it and use it heavily.

---

### Post by cariboo on 2013-02-08
I bought an inexpensive MSI Intel motherboard and E5400 CPU with 2GiB ram, I've added various hard drives as I need them, so far 2X400GiB 2X500GiB 2X1TiB, and a 120GiB for the os and /home directories. The MB has 6 SATA ports, and I added a cheap 4 port SATA PCI card for extra drives.

I currently run 12.04.1 server with NFS, Samba, MYSQL, Apache2, PHP5 and Minidlna servers, all administration is done via ssh and sftp.

---

### Post by lisati on 2013-02-08
I have an older machine, about 14 years old, can't remember the exact specs beyond its having a 3Gb hard drive, 64Mb RAM and a cpu speed of 133MHz. For a while I was using it as a backup machine for my web site, using 6.06. Haven't used it for a while. Not the flahsest of setups but better than nothing. (Good grief: is the machine I currently use for a server approaching 10 years old?)

---

### Post by andrew.46 on 2013-02-08
Running a proxy caching NNTP server here (leafnode -2)....

---

### Post by ssam on 2013-02-08
yes currently have a beagleboard (low power is nice for something on all the time (each Watt a device uses costs about 1$£€ per year)) with a 1TB usb harddrive. Also have it connected to hifi and running MPD.

Planning to get a mini-itx atom board because I need to bump the storage up to a few TB and would like raid, so need sata ports. thinking one of these [http://www.jetwaycomputer.com/NF9I.html](http://www.jetwaycomputer.com/NF9I.html) (note it has the dreaded Poulsbo GPU, so only suitable for a headless machine).

---

### Post by Lars Noodén on 2013-02-08
> **Roasted said:**
> How on earth did you pull that off? Last I ran freenas zfs ate every little bit of CPU my quad core could throw at it...

I heard in an interview that it's become much, much heavier in recent versions.  If you want something light, you can try building your own NAS with FreeBSD or OpenBSD.  If I recall correctly the interview I heard about the changes to [FreeNAS was on FLOSS Weekly](http://twit.tv/show/floss-weekly/198).

---

### Post by Dry Lips on 2013-02-08
I've got a secondary computer where I have windows 8 and Ubuntu 12.04 server on different HDD's. I don't need a server running 24/7, as I only use it for web development, etc. 

Got yet another box that I'm not using at the moment, which I could use as a server if I wanted to.

---

### Post by |{urse on 2013-02-08
> **ssam said:**
> yes currently have a beagleboard (low power is nice for something on all the time (each Watt a device uses costs about 1$£&#8364; per year)) with a 1TB usb harddrive. Also have it connected to hifi and running MPD.

Planning to get a mini-itx atom board because I need to bump the storage up to a few TB and would like raid, so need sata ports. thinking one of these [http://www.jetwaycomputer.com/NF9I.html](http://www.jetwaycomputer.com/NF9I.html) (note it has the dreaded Poulsbo GPU, so only suitable for a headless machine).

Ssam I just built a few (endian) firewalls with that board, very nice (as you said, for something headless)! Now that I look closer, the boards I used were exactly the same model but had 2 nics.. Weird! Same model & rev number..

---

