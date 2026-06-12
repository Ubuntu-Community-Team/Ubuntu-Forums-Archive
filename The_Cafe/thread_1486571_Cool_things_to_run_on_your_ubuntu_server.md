---
title: "Cool things to run on your ubuntu server"
date: 2010-05-18
forum: The Cafe
---

### Post by markbahnman on 2010-05-18
For those who have servers running ubuntu, what are some cool, interesting or just useful things to run or use your server as? Thinking along the lines of your own XMarks server to a just a VPN.

---

### Post by consindo on 2010-05-18
I guess you could just do a standed LAMP server or if you like a specific game you could probably set a server up for that game :)

---

### Post by phrostbyte on 2010-05-18
IRC server, Mail server, LAMP web server running Drupal, web forums

File server, BitTorrent downloader/seedbox (for seeding those Linux ISOs of course)

OpenLDAP/Domain services

Fried chicken dispenser

---

### Post by The Real Dave on 2010-05-18
Have a look at the [Show us Your Server]("http://ubuntuforums.org/showthread.php?t=334293") thread for some interesting servers :)

---

### Post by Bachstelze on 2010-05-18
Not really "cool" but very useful: a NTP server that is part of the NTP pools. Also a TOR node if your ISP doesn't forbid it.

---

### Post by kpholmes on 2010-05-18
Check out the link below, it might have what your looking for.

---

### Post by kevdog on 2010-05-18
Ive always wanted to run an IRC server, however could never find any good information how to set this up!!

---

### Post by Dragonbite on 2010-05-18
Right now, my server is primarily a file server, but I plan on making another server a heavier LAMP server as well as domain controls (LDAP?).

I ultimately want to set up one box as a backup server and set all of the desktops to automatically backup to it once in a while.  Then have that server backup onto a cloud-based backup site such as Mozy or Crash Plan.

This way I have a local (instant-accessible) backup for "opps!" and an offsite location for house-wide catastrophe (fire, flood, etc.)

---

### Post by PartisanEntity on 2010-05-18
I am not running anything spectacular:

minidlna - media server
firefly - an audio media server that serves to iTunes
file server - supporting both smb for windows, and afp for OSX
time machine - backup server for OSX

---

### Post by NCLI on 2010-05-18
I use my server for:

Deluge for bit-torrent, as it allows disconnecting the daemon  from the client, and easily adding new torrents from afar.

Rsnapshot for backups of a remote server I manage

Fileserver

On-the-fly transcoding of video for my PS3 around the house using PS3MS

Folding@Home

---

### Post by cartman640 on 2010-05-18
I have VirtualBox running on my server, so from there the possibilities are endless for server fun. Currently only running two VMs, one for VPN and one which is a LAMP server. Previously had 6+ VMs running doing all sorts of things (DNS, proxies, domain controllers, etc).

Next task I'd like to try is building my own mini elastic cloud, probably only with two nodes, would be more an experiment to see if I could actually do it than anything.

---

### Post by samalex on 2010-05-18
If you like the old-school way of computing, download [Synchronet]("http://www.synchro.net/") and setup your own BBS.  Syncronet has a built-in IRC, Telnet, RLogin, Web, NNTP, Gopher, Email, and FTP server (am I missing anything?)  and the support is great!

You'll instantly have access to lots of message forums through DoveNet and if you want to go the extra mile you can contact someone on FidoNet (or one of the [other echo networks]("http://www.bbscorner.com/bbsnetworks/")) and pull in content from them as well or even connect to a Usenet newsgroups or other NNTP server to bring in content from there.  And if you're not much into Telnet or text-based apps you can access all the content via your browser through the web server.

Pretty cool stuff to play with, and it has full Linux support!  I setup one for my personal use, but there are lots of boards that do exist for all users.  Also there are lots of other BBS apps that support Linux besides Syncronet, and using DosEMU or DosBox you can run any MS-DOS BBS which there are TONS of.  But honesty Synchronet leaves nothing to be desired.  It even supports POTS lines for true modem users, and it's been around since the haydays of BBSing in the 90's.

Some sites to check out if you want to get into this:
BBS Corner - [http://www.bbscorner.com/](http://www.bbscorner.com/) 
Synchronet BBS List - [http://www.synchro.net/sbbslist.html](http://www.synchro.net/sbbslist.html) (maybe there's one in your area)
Telnet BBS List - [http://www.telnetbbsguide.com/](http://www.telnetbbsguide.com/) 
BBS Documentary - [http://www.bbsdocumentary.com/](http://www.bbsdocumentary.com/) (history of BBSing)
SyncTerm - [http://syncterm.bbsdev.net/](http://syncterm.bbsdev.net/) - Terminal program (similar to Telix) for about any OS out there (runs great on Linux)

Unfortunately Telneting to a BBS from Shell in Linux is generally a horrible experience since the ANSI graphics aren't interpreted very well. I'd recommend downloading SyncTerm (see link above) before visiting the BBSes.

Take care --

Sam

---

### Post by BrokenKingpin on 2010-05-18
My Ubuntu server has the following:
 - Network storage: Raid 1 (2 TB of usable space)
 - Web server
 - UPnP server (for streaming to my xbox 360)
 - Media center with XBMC (server is plugged directly into my TV)
 - Bittorent with Transmission (web front end enabled)
 - Virtual Machines of Windows - For development application testing

---

### Post by markbahnman on 2010-05-18
Awesome responses! I'm actually looking to get my own dedicated server (remote server, cause bandwidth and DL/UL speeds are more expensive than I like and I'll be going back to University in a while) and want to look at all the options I have for using it. This gives me some great ideas for making the most out of my server.

---

### Post by phrostbyte on 2010-05-18
> **kevdog said:**
> Ive always wanted to run an IRC server, however could never find any good information how to set this up!!

There is a wide selection of ircds in the Ubuntu repository.

---

### Post by markp1989 on 2010-05-18
on my server i run 

NFS server 3tb of space 
Samba server for windows/mac pcs
UNPN server for xbox 
firefly for streaming to itunes 
media pc running xbmc
rtorrent running in screen  
flexget for auto downloading my shows 
esniper running in screen for auto bidding on ebay auctions
got it to send text messages using a spare 3g dongle i have for notifications etc. also working on a script that will check incoming messages and perform actions/respond depending on the message content 

Probably a few more things, i will write them as i remember them 

here is a pic [http://i246.photobucket.com/albums/gg102/markp1989/DSC_0004.jpg](http://i246.photobucket.com/albums/gg102/markp1989/DSC_0004.jpg)

Specs:
Zotac GeForce 9300-ITX-I-E (i never installed the wifi board)
Intel E5200*
mini ninja heat sink
4gb ddr2 800
2*samsung 1.5tb f2 3.5" drives
Pico PSU 150xt + dell Da2 220w power block
[http://www.ebuyer.com/product/174463](http://www.ebuyer.com/product/174463) case
ipazzport hand held keyboard and track pad
Artic cooling 12025 pwm fan as exaust

---

### Post by snova on 2010-05-18
> **kevdog said:**
> Ive always wanted to run an IRC server, however could never find any good information how to set this up!!

> **phrostbyte said:**
> There is a wide selection of ircds in the Ubuntu repository.

I like [InspIRCd]("http://inspircd.org/"); alternatively I might put Charybdis forward. I also generally prefer/suggest building IRCd's from source.

InspIRCd's [documentation]("http://wiki.inspircd.org/Introduction") is pretty helpful; possibly the main disadvantage of this IRCd is that it's very... vanilla until you edit the template config files substantially. And they are quite long. (But there's lots of nice features once you do, so it's quite possibly worth taking some time.)

---

### Post by juancarlospaco on 2010-05-18
***Da Electric Sheepz***

---

