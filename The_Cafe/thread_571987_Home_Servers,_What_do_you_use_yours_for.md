---
title: "Home Servers, What do you use yours for?"
date: 2007-10-09
forum: The Cafe
---

### Post by Rupertronco on 2007-10-09
Just out of curiosity, those of you who have home servers setup, what are their functions? Primary and secondary. Right now I'm just using mine for file storage/sharing and I'm interested in seeing what others use theirs for.

---

### Post by notwen on 2007-10-09
debian etch minimal install running nfs, ftp and apache. =]

---

### Post by Frak on 2007-10-09
Gentoo/Debian - Gentoo is a Xen server and Debian is a personal FTP/HTTP/etc. share.

---

### Post by steveneddy on 2007-10-09
File server, apache2, storage, etc....

---

### Post by nickburns on 2007-10-10
Raid 1, Tape backup.  Storage mostly (Pics, Family Videos, books on tape), but also running mediawiki with mysql for some personal / family history / genealogy.

---

### Post by toupeiro on 2007-10-10
SunOS 5.11 (Nexenta) running NIS/NFS/SSH/FTP/CIFS

---

### Post by p_quarles on 2007-10-10
Backup files (all heavily encrypted) as well as my "please employ me" web site:
[http://ghosttown.dnsalias.net](http://ghosttown.dnsalias.net)

---

### Post by shad0w_walker on 2007-10-10
Feisty fawn - Mythtv combined backend/frontend, apache2 server (Mythweb, other bits and pieces), NFS/Samba server

---

### Post by kvonb on 2007-10-10
Ubuntu 7.04

Mail server (including webmail)
Web server (not doing much right now)
File server (SMB)
IRC server (UnrealIRCD)
DHCP server
DNS server
Internet gateway for whole internal network
Router for wireless access
Game server: Enemy Territory - (Noquarter with bots)
Teamspeak server

...not bad for a 6 gig hard disk ;)

---

### Post by DDuong on 2007-10-10
I don't use Ubuntu for my home server.  However, I use Debian.

First PC, I'm using as a DNS, DHCP, and firewall.

Second PC, fileserver and mail server.

---

### Post by qpieus on 2007-10-10
ubuntu 6.06 set up as a file server and print server. This one is for family use, everyone can write to it and print through it. I'm also setting up a debian etch server as my personal backup/storage server.

---

### Post by Sporkman on 2007-10-10
Ubuntu Server 7.04. Serves a couple of personal websites, adds file system capacity. and does CUPS for our printer.

---

### Post by koenn on 2007-10-10
debian stable, doing
network infrastructure - dns, dhcp, ntp, ... so that it's easy to add hosts to the home network 
some caching (squid, apt-proxy)
a web server cause I needed it to set up proxy autodetection, and to serve some packages and configuration scripts when I experiment with linux.
file server (samba), mainly  downloaded software / install files for windows, some backups, ... 
it used to also run a wiki once but that got lost in a crash. for the wiki, it also ran mysql.

---

### Post by boast on 2007-10-10
Debian etch on an old compaq deskpro.

It serves as a file/backup sever, web server, torrentflux, NTP, DNS, WINS server, FTP server, and teamspeak server

---

### Post by Rupertronco on 2007-10-10
I wish my ISP would let me run a web server without asking for my soul and a ludicrous amount of cash.

---

### Post by Sporkman on 2007-10-10
> **Rupertronco said:**
> I wish my ISP would let me run a web server without asking for my soul and a ludicrous amount of cash.

Can you run it out of a port other than port 80? That's what I do.

---

### Post by MetalMusicAddict on 2007-10-10
Gutsy CLI install. File/print/Apache/Tremulous server. Some bittorrent sharing.

---

### Post by AndyCooll on 2007-10-10
Running Ubuntu 7.04 on my server. Mainly used as a file server. I also use it to store the /home partitions on it.
also acts as a gateway print and scanner server.

:cool:

---

### Post by Dr Small on 2007-10-10
I have Openssh-server on this pc, but on my old installation, I had HTTP (which I plan to get again).

Dr Small

---

### Post by Dragonbite on 2007-10-10
I'm currently setting up my Edubuntu as an LSTP (thin client) server.  I hope to be able to remove the hard drive from the other 2 computers and have the kids (and myself) hook up to the LSTP server for everything.

That will leave only 2 systems to maintain.. my wife's Windows and the Edubuntu LTSP server :)

After that, I'm looking at setting it up to be a Web (custom web apps) and File (for easy backup from both machines) server.

If I ever get broadband, I'd like to set up an IMAP server (internal only).

But currently I've got one old dell (Dimension 4100) that will hook up as a thin client, but not the other machine (Sony Vaio). Plus I'm just trying to get the computers to see each other on the network so I can move files over from my (stand alone) Edubuntu workstation installation to the server.

If anybody is willing to help with Networking basics (I mean basic... I've got it hooked up and that's about it.. don't know what to do next!!) please, PM me!

---

### Post by rjs82vette on 2007-10-10
myth backend
webmin
groupware
torrentflux
backup
mythweb
cups
apache
zoneminder
ftp
files
mapped user directories linux and windows
email
web

---

### Post by Frak on 2007-10-10
> **MetalMusicAddict said:**
> Gutsy CLI install. File/print/Apache/Tremulous server. Some bittorrent sharing.
Whats your server name (on the heartbeat), Trem has to be one of the best games for *NIX. ;)

---

### Post by MetalMusicAddict on 2007-10-14
> **Frak said:**
> Whats your server name (on the heartbeat), Trem has to be one of the best games for *NIX. ;)

ATM its a private one for Ubuntu Studio developers. It won't be up much longer as we're putting it in a data-center.

---

### Post by Frak on 2007-10-14
> **MetalMusicAddict said:**
> ATM its a private one for Ubuntu Studio developers. It won't be up much longer as we're putting it in a data-center.
Awww :(

Oh well, back to SST+ ;)

---

### Post by eriqk on 2007-10-14
Feisty server install, mainly for Samba stuff. Secondary, it's a LAMP for testing sites.

Groet, Erik

---

### Post by RandomJoe on 2007-10-14
I have two at the moment.

First one is a Slackware box doing firewall duty.  Three NICs - Inet, wired LAN, wireless LAN.  It also runs dnsmasq for DHCP and DNS.

The big one is running Dapper.  Has just shy of 1TB RAID5, mostly for my movie and music collection, shared via NFS to the rest of the network.  I also back up my other systems there.  Apache is running, just for me to play with.  ZoneMinder is watching three cameras placed around the house.  I also recently installed Icecast so I can stream my scanner or ham radios - in case I get bored while at work, I can at least listen.

---

### Post by jgrabham on 2007-10-14
Setting up a PC to store my files, keep all my music on, as well as to play my music and DVDs (so I dont have to boot up my main PC), and possibly set up some form of web server to store some stuff on, which I might need anywhere.

---

### Post by Baka no Kami on 2007-10-14
I have two.

My little one is an older Shuttle running Fiesty.  It used to be postfix/LAMP until I realized I'll proably never really teach myself PHP.  Now it's my MythTV front/backend so I don't have to leave my power sucking desktop on all the time.

My other one is mostly left over parts I didn't think my roommates would miss. It's got a 1 TB RAID5 on it for file sharing. It's running XP because linux support for the raid card is sketchy.

---

### Post by Baka no Kami on 2007-10-14
I have two.

My little one is an older Shuttle running Fiesty.  It used to be postfix/LAMP until I realized I'll proably never really teach myself PHP.  Now it's my MythTV front/backend so I don't have to leave my power sucking desktop on all the time.

My other one is mostly left over parts I didn't think my roommates would miss. It's got a 1 TB RAID5 on it for file sharing. It's running XP because linux support for the raid card is sketchy.

---

### Post by happysmileman on 2007-10-14
> **p_quarles said:**
> Backup files (all heavily encrypted) as well as my "please employ me" web site:
[http://ghosttown.dnsalias.net](http://ghosttown.dnsalias.net)

I'd say you should make that site look a bit better designed, center it, get rid of the repeating background and maybe round of the edges with transparent images. Sorry if it seems like I'm insulting it or anything, just first impressions can mean a lot

---

### Post by Dalmaris on 2007-10-14
I use my main Linux Desktop pc as my "server" atm.

Core 2 Duo 4300 1.8Ghz
768MB ram
2TB Harddrives
Running Opensuse 10.3

Samba Fileserving for the rest of my network
DNS
Squid Cache
Apache
iTunes sharing
SSH
OpenVPN

Gonna put in more ram and seperate most services into seperate virtual machines.

Mike

---

### Post by DrNick on 2007-10-25
Its a 450Mhz PIII, 280M/B (ish) RAM, 4gig sys disk, 2 data disks 330GB total. (I really should set them up again with LVM at some point...)

It does routing, NAT and IP firewalling.  Its a DHCP and DNS server.  It has a LAMP stack installed, runs one or 2 websites, and webalizer.  

It also runs openssh, and does file-sharing through that too via sftp.  It's a CUPS print server.  It runs a download program called mldonkey, which connects to various networks and allows central downloading controled via a web interface.  It also runs the net-top traffic monitoring and analysis software which provides stats and really quite detailed info of traffic in and out - again via web interface.

Lastly, when its not busy doing any one of those things, it runs folding@home, to put its un-used CPU to a good cause :)

All in all a pretty handy little box!

Oh yes, and its running Ubuntu Server 7.04.  In terms of uptime, only time it was down was when there was a powercut.

---

### Post by Calash on 2007-10-25
Mythbuntu with SAMBA shares for remote watching of programs, MP3 storage for house music collection, and backup data.

Apache allows me to access Mythweb for program data ans stuff like that.

Had it running an open SSH server for a while but I never used it outside of my firewall so I  closed up the port.

---

### Post by MethodOne on 2007-10-26
I have a print and SSH server on my system running Arch.  I'm going to replace the system with a more powerful one I'm getting from an upcoming college computer sale.

---

### Post by eric.rost on 2007-10-26
Well, I have 2 vm's running, and will soon switch to 3 vm's:

My new setup:

VM1: router/dhcp/dns/proxy/firewall
VM2: Zimbra (public facing)
VM3: Wordpress (public facing)
Base Machine hosting VM1 & VM3: ftp/print server and mt-daapd server

All running feisty-server under vmware with feisty-server as base.

---

### Post by Retrograde77 on 2007-10-26
Yesterday just finished building mine, Gutsy 7.10 server / 120gb / PIII 933 as a file share.
Will also LAMP it as well so I can play around with some PHP. :)

---

### Post by habrys on 2007-10-28
I bought a debian mini-server with 750 GB disk called "bubba". It's running Debian Sarge right now (but I'm going to upgrade to Etch soon), is small, fanless, not very fast (200 MHz ARM9 CPU, 64MB RAM), but fast enough for a server.

I use it for:
- storage of movies, music, pictures etc. (samba, ftp),
- as a print server,
- as a mail server,
- as a "download server" (there is a daemon called ftd installed out of the box, which is able to download files over ftp, http and torrents as well :-) ),
- cataloguing my media collection in a mysql database with frontend running on the main pc (gutsy),
- it has also an UPnP media server installed out of the box (MediaTomb), but I don't use it, since it cannot stream subtitels.

It plays pretty well with a network media player (Ziova CS-505), so I can access my media without turning on the main PC. Just a silent, fanless bubba, the media player, TV, AV-Receiver and me on a couch :-D

Here some links if anybody is interested:
bubba: [http://www.excito.com/products.html]("http://www.excito.com/products.html")
Ziova: [http://www.ziova.com/cs505.php]("http://www.ziova.com/cs505.php")

---

### Post by Choc_Salties on 2007-11-10
in my case i have 3 sitting here, and depending on mood of myself and my fellows, they are either running Ubuntu of some sort (now server on the one Xeon) or Win* , running servers for games at a local LAN i help run.

---

### Post by svtfmook on 2007-11-10
ubuntu 6.06, movies on main tv, music through out the house.

---

### Post by rowanparker on 2007-11-10
Debian Etch, storage (extra + backup of /home), lamp (for devel + fun), and in its spare time it folds at home.

---

### Post by Christmas on 2007-11-10
I have Apache 2 installed and use it only for files which I want to share. For example wallpapers, ET maps, pictures and all that kind of stuff.

---

### Post by isecore on 2007-11-10
Sempron 2500+ with half a gig RAM. Runs 24/7 and does a multitude of services. 

Primarily it's a complete LAMP-server running Apache2 with PHP5/MySQL5, everything off of Debian Stable (currently that is Etch). It hosts various homepages for me, my friends, my family (currently 7 domains each with about 6-7 subdomains). These include blogs, galleries as well as a few static pages and sandbox/developer-subdomains for me and my girlfriend.

It's also doing email-related duties for these domains, running on postfix with spamassassin. Other duties involve samba-shares and data-storage to me and my girlfriends Ubuntu-machines, SSH shell access for us as well since it's always on (running irssi in various screens, usually :) ).

Finally it also acts as ftp-server for when we're travelling and need to unload pictures from our digital cameras. And it uses any spare CPU-time to crunch Seti@home :) In fact, despite sounding heavily loaded it has plenty CPU to spare for other duties.

All of this running on my 100/100 LAN connection, with gigabit internally between the various computers. I was thinking about posting a picture of it just for fun, but it's not very pretty to look at (being housed in an ancient big-tower that has been severely modified to function as I want it. Functionality before form, you know)

---

### Post by xaco1234 on 2007-11-10
i actually use my old dell inspirion 6400 (know it's a laptop, but the screen is broken, runs  ubuntu 7.04) to host 2-3 irc bots, download and storage for files i use on both my linux box and windows box.

servises:

mysql
apache
vsftp
samba
sshserver(don't remember what it's called)

---

### Post by zach12 on 2007-11-10
I've been trying to set up a web server but haven't been to get it to install 
when it's up will use as a web server/email server

but need a new hard drive first:sad:

---

### Post by Sporkman on 2007-11-11
> **xaco1234 said:**
> 
sshserver(don't remember what it's called)

openssh-server

---

### Post by JetskiDude911 on 2007-11-11
I use to have a home server that ran Novell 4, which of course was just a file server. It stayed up for about 5 years just mainly being my music server. It still works too, but I don't use it too often.

I've got another old computer just sitting around collecting dust, so I'm thinking about installing Ubuntu on it and using it as a file server.

---

### Post by stalker145 on 2007-11-11
I think I'll finally chime in here since I now have something to add ;)

My Athlon 2600+ with 512MB RAM, a 256MB NVidia card, and 800GB of storage is running:

> Apache2 for my personal web site
EGroupware for calendar sharing
Simple Machines Forum for family communications
Jinzora for media streaming
MySQL to database the above junk
Samba for file sharing

I also use this server for backing up my DVD's (I have a 6 year-old and NEED to) and will use it as a print server once I can get my wife to stop buying Lexmark printers ](*,)

I'd also like to set up an e-mail server so I would no longer have to rely on RoadRunner or GMail, but either I'm flubbing it or RoadRunner is continuing to block mail servers for residential customers.

I set up EGroupware and Jinzora just this afternoon after scouring the forums for collaborative software. They were both very easy to set up and rather intuitive to run. EGroupware does everything I need it for... for now ;)

---

### Post by Rupertronco on 2007-11-13
> **stalker145 said:**
> I think I'll finally chime in here since I now have something to add ;)

My Athlon 2600+ with 512MB RAM, a 256MB NVidia card, and 800GB of storage is running:



I also use this server for backing up my DVD's (I have a 6 year-old and NEED to) and will use it as a print server once I can get my wife to stop buying Lexmark printers ](*,)

I'd also like to set up an e-mail server so I would no longer have to rely on RoadRunner or GMail, but either I'm flubbing it or RoadRunner is continuing to block mail servers for residential customers.

I set up EGroupware and Jinzora just this afternoon after scouring the forums for collaborative software. They were both very easy to set up and rather intuitive to run. EGroupware does everything I need it for... for now ;)

I'm a fairly decent programmer (given it's a hobby, I study biochemistry) and I'm very good with hardware, my weak point is networking, just because I haven't spent the time required to really develop a good grasp of it. Does anyone have some insight as to how I'd go about setting up a mail server, or a tutorial that would get me off the ground?

My file server now has an el cheapo core 2 duo, and I'd like it to do something other than folding@home. (

---

### Post by boast on 2007-11-13
> **Rupertronco said:**
>  or a tutorial that would get me off the ground?
(

try [http://www.howtoforge.com/howtos/email](http://www.howtoforge.com/howtos/email)

---

