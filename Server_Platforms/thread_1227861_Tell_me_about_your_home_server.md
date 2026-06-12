---
title: "Tell me about your home server"
date: 2009-07-31
forum: Server Platforms
---

### Post by nuseryame on 2009-07-31
Hi,

I want to know why people have home servers and what servers that are and what they are used for. Also if you virtualize them.

In Microsoft you have Exchange Server which manages emails for a large number of users. Why have an email server if there are 3 users at home?

You can have your own webserver, this is to host your own website right? does that mean you don't need to pay a company to host it and don't have to pay for a domain name?

Samba is an equivalent to Active Directory? allowing you to share files on the network.

What other types of servers are there? SQL is for databases? but only large databases, for small one's you can just use Access.

---

### Post by wojox on 2009-07-31
Bottom line for me is cost. Why pay all that money for licences and software when I can get it for free.

---

### Post by TwiceOver on 2009-07-31
Tell me about your home server...

Well, it is a 2u Rackmount with ~2tb of drive space, 3gb, ram, sempron 1.9ghz processor.  All tucked away in my wiring closet in the basement.

It does the following:
Hosts my own website
Streaming Music
File Shares
Automatic Backups of all systems.
House Radio Station
Hosts 1 XP Virtual Machine (For XBox, TiVo, MS Money)
Newsgroup Downloads
Hosts picture gallery
Hosts Internal Website for our home

I set it and forget it.  The server is fairly low powered so the electricity costs per month are very small.

Samba is NOT Active Directory.  You should look those two up.  Samba allows for Windows file sharing.

There's a thread around here where people discuss what they do with their home servers.

---

### Post by lykwydchykyn on 2009-07-31
My home server is a crusty old pentium 2 that somebody gave me.  In spite of that, it does all the following:

 - DNS (for caching and so I can access other machines in the house by name)
 - File sharing (so all those family photos are in one place)
 - SSH (so I can access the home network from work)
 - Apache/MySQL/PHP (family wiki, a few web apps I wrote to make life easier, etc).
 - saned, to share our one scanner to all machines in the house
 - CUPS, to share our one printer to all machines in the house
 - Dansguardian/Squid, for the kids
 - dictd service.  I don't know why, just because it's easy to set up...
 - On rare occasions, I fire up the icecast service which plays a radio station of the kids' favorite songs.  Slows the poor thing to a crawl, though.  

Given its specs, I naturally don't do any virtualizing on it.

---

### Post by kustomjs on 2009-07-31
well the reason why I host mine and my friend website is because of cost of hosting.

then I have couple internal servers for testing only like:

printer server
media server
mail server
network monitoring server


there will be more to come soon.

---

### Post by andrew.46 on 2009-07-31
Hi,

I would dearly love to get a dedicated server at home as my temporary solution is to leave my laptop plugged in all the time :-). I run an ssh server to allow access from work and also the proxy NNTP server leafnode 2. love to get a mail server + apache running though...

Andrew

---

### Post by R.Bucky on 2009-08-01
I use my server box as a UPnP server for my PS3, hosting of 10 websites, streaming media server, VMware Server2, DNS server, and mail server. I have a tower server with a Xeon 3000 series processor, 4GB RAM, and RAID1 w/hot spare and a separate hdd for file storage. I use a 1TB external for daily backups.

Hosting through a 3rd party is a pain in the... and insecure (ftp). I enjoy the challenge and development of my server box. Free and easy to use!

---

### Post by nuseryame on 2009-08-01
For no other reason than that I'd find it interesting, I think I'm going to set up Ubuntu Server in Virtual Box and create:
-Mail server
-Web server
-DNS server

I'm going to do it so that I can access my own domain name email from anywhere using webmail, that's what apache will be for.

I'll use DynDNS and get a free domain.

Anyone recommend some good books for this? also is the official ubuntu server book out yet?

---

### Post by ugm6hr on 2009-08-01
FreeNAS Home Server (see link below).

For file storage from any computer in house and Media sever, as well as backup.  Have 2 HDs in the device; 1 purely for backup reasons..  Don't use the web server function; have a paid host which is more sensible for most people.

---

### Post by BDNiner on 2009-08-01
I don't have a home server yet. I have a Buffalo Linkstation NAS, 1TB storage. It servers all of my needs for now except you cannot use shh unless you hack the device and install a custom firmware. I am still trying to decide if I want to do that yet. If i do i will go ahead and turn it into a full blown debian server.

---

### Post by Meatshield on 2009-08-01
I have two servers currently. The Linux one is.. well, I don't even remember the stats, got it off a friend, but it hosts a website so I can share links with my friends of files they might like (software, video tutorials I do, etc) and I have a free domain from No-IP.com to link them to. It's also a wonderful local testing box for web sites since it has everything from Apache2 to MySQL, PHP, Ruby, Perl, etc. I upload files via SSH(SFTP). It's also the home DNS server since our Internet here can be a little wonky.

Since it's not powerful enough to do virtualization (and I do that a lot to review Linux distributions and test software) I have another server running Windows Server 2003 (I'm a student, I got it for free :P) that hosts my ISO files and virtual machines. Technically it's an ftp server as well, but that's just for me to upload files with remotely. That one's a quad core, 4 gb RAM, 500 GB hard drive monstrosity that I give all my resource-intensive tasks (including Orb.com's streaming, which uses a core alone to transcode)

But then again I'm far from an average user. Right now I have an ssh to my Linux box, a RDP session with the Windows Server, and a virtualized version of Ubuntu running on my desktop with a browser and about a dozen other applications.

---

### Post by noway2 on 2009-08-01
I use my server to host my own private email with virtual users in a MYSQL database, I host my own web page that I use for squirrelmail and a lot of other functions, such as myadmin, postfix admin.  I maintain a subversion repository that I store software development files on.  I have a domain for my wifes business and host the web and email for that.  I also run a DNS and DHCP server that are linked so that any device on my lan is addressable by name or IP number.  I use SAMBA to allow Windows users to access shared resources and networked printers. I use the SSH to log into my LAN remotely.  Recently, I have gotten more interested in network security and have included Snort and OSSEC into the mix.

For hardware, until recently, I was running all of this on a Pentium 3 based system that I built in 1997, but it started having a lot of hard drive errors and I replaced it with a el-cheapo desktop PC that I haggled down to $250 USD that has an AMD-64 bit (using Ubuntu server 64 bit).  I don't keep a mouse, keyboard, or monitor attached and I log access it almost entirely via remote.

My plan is to get a second hard drive and a RAID controller for redundancy as I have become both quite fond of and dependent on my system.

---

### Post by tobiness on 2009-08-01
My Home Server; (im on it right now xD)
Ubuntu 8.10 (Gnome Installed)
Its A Dual Core 2.0 Ghz With 2 GB Ram and 250 Gb Disk Space.
It Does The Following:
DNS : Not Working Still In Configuration
Php : Php 5 Is Running XD
Apache 2.2.9 (Running My Network Intranet Website)
Im About To Install Php And MySql Then Configure DNS To Just Need Names For The Hole Network 
Although my main computer its a crappy old pentium 3 with 40 GB Harddrive Running Win xp And SuSE 
So Im Prtobs Gonns  Start Useing This As Main And Move The Server Over Onto That (If Ghost Runs Under Wine xD) It Better LOL!

---

### Post by cariboo on 2009-08-01
@tobiness instead of going through the hassle of setting up a DNS server just for your local network, have a look at [dnsmasq]("http://www.thekelleys.org.uk/dnsmasq/doc.html") it is in the repositories.

[apt://dnsmasq](apt://dnsmasq)

---

### Post by jamesrfla on 2009-08-02
I have a Intel P4 2.8Ghz, 1GB of RAM, and a 250GB hard drive. I run apache2, mysql, citadel mail server, samba, SSH server and a terminal server.

---

### Post by nerr on 2009-08-02
I run my home server on an Acer easystore H340 box.  It runs Ubuntu Server 9.04 x86 with a 1.6GHz Intel Atom 230, 2GB DDR2 RAM, two 1TB HDDs, and gigabit ethernet.  It's also got a single low-profile PCI-E x1 slot which I have not quite figured out a use for yet.  Possibly a network card or TV tuner?  Who knows.

Software includes:
OpenSSH - SSH/SFTP (headless box with no video out, this is my lifeline)
Samba - Serves files 24/7 to five Windows machines (three XP x86, two Vista x64)
CUPS - Share an HP Deskjet 5650 printer to the same five machines
Apache2 - Running a very basic webserver that uses PHP to output some system information, in case I'm out and about and SSH is not an option.
rTorrent - Manages BitTorrent downloads.  I actually seed the x86 and x64 variants of Ubuntu Server 9.04 on this 24/7. :)
rsync - Backups of the five Windows machines

I think that's actually about it for now.  I'm always looking for more cool software, since this box doesn't do a whole lot at the moment.  If anybody's got something cool, let me know!

---

### Post by raymondvillain on 2009-08-02
I have an old desktop abandoned by a spoiled child.  It is a pentium 4.  I put 4 G ram in it and a 250 Gb pata hard drive.

Installed Ubuntu server so I could "learn" what a server really is.  My home network is an XP box, an Ubuntu Jaunty desktop machine and a laptop that dual boots vista and Jaunty.

How does one launch a browser from the server?  I have not (yet) installed a GUI on the thing and I'm reading several books with configuration chores explained.  They all say ".. to find out, launch a browser and go to ..." but how to do it from the command line is beyond my meager knowledge of Ubuntu server.

---

### Post by cariboo on 2009-08-02
There are several text based browser in the repositories, give elinks a try. I you want a gui browser, just install firefox and use x forwarding to run it:

```
ssh -X user@server
```

Then at the prompt type firefox.

---

### Post by Thirtysixway on 2009-08-02
My home server is pretty small, 1.2 GHz 512MB ram and 1 harddrive about 38 GB I believe.  Xycom industrial node 1507

I'm running it on two static IP addresses, one is dedicated to a lan project I'm working on.

I currently use it for web development/testing, running virtual machines, sharing printer via cups to windows/linux network, samba for file sharing/backups (although it's hard to do backups with 38GB drive...).  Also I use my ssh as a socks proxy when I'm browsing on public networks for security reasons.  And I run my torrents on it so I can shutdown my desktop at night.

I used to run my websites from my home server, but I started having issues both with dns and bandwidth (my upload speed isn't great enough) so I no longer run production sites from it.  Eventually I want to expand it to a bigger harddrive for real backups and possibly a media server.

Probably the most productive thing I have on there is Folding@Home (running for team Ubuntu :)).  I figured that my server isn't always handing files or prints, so why not put the cpu cycles to good use?

---

### Post by raymondvillain on 2009-08-02
Thanks, cariboo907.

I'm trying that now.```
ssh -X user@server
```

But it doesn't do what I expected.  Do I need to install a graphics package before I try that?  When I type in the code above, all I get is a few lines of boilerplate about Ubuntu and then the system load, memory usage, processes, etc.

---

### Post by finite9 on 2009-09-17
I was using an old laptop as a home server with a couple of external 500GB SATA discs in a raid-1 config, but the thing was always dying due to problems with the pcmcia sata controller, so I decided to invest in a real server:

Lian Li PC-A10B aluminium mid-tower case (best case I ever owned)
Enermax 301W PSU (old but do not need more power)
ASUS PQ5e MB
Intel Core2Quad Q9550
4GB Corair XMS DDR3
ATI Radeon HD3450 passive cooling
No monitor (headless)

1 x 160GB SATA boot disc
2 x 1TB WD RE3 in RAID-1 array with mdadm
will soon buy 2x1TB RE3 in RAID-1
1 x SATA DVD+-RW
APC BackUPS ES 550VA

Server draws 120W power during idle (FAH running on 1 core).  Not brilliant, but I can live with it.

Server auto power on 09:00 via BIOS, auto shutdown via cron 22:30
Server chassis padlocked, front door to chassis is locked.


I use it for:

Ubuntu 9.04 amd64 server
NFSv3 file server
SSH server remote access from work
rtorrent server (service active all day scans for torrents)
FAH client active all day
movie/music/photo/TV show repository
transcoding server (mencoder custom script for my camcorder DV files to x264)
backup server for backups of Ubuntu 9.04 laptop
Oracle11gR2 test server (APEX)
KVM image WinXP SP3 for configuring my Logitech Harmony and TomTom and browsing those sites that refuse to work in Linux (manual startup)

When I get a new laptop with 802.11n, I will move my home directory to the servers raid-0 and NFS mount it during login so that I don't have any data on my laptop, and then I can create unattended incremental Tar backups on the server to raid-1 array, scheduled with cron.  At the moment, I do incremental backups of my laptop, but have to connect it to router via ethernet cable and run backup script, and im a bit lazy with doing that once every sunday.

Only current issues are web server and broadband speeds.  I want to access my server from anywhere, but my 24Mbit/1.3Mbit link is not fast enough for delivering content to the net.  It's not possible to get a consumer line with higher than 1,3Mbit upspeed.

I want to have a website with Apache to deliver content to friends and family that are not tech savvy and don't know how to run SSH/SCP, so I can post videos and photos but have not gotten around to it yet.

---

### Post by Bachstelze on 2009-09-17
Antec Sonata III case
Athlon 64 FX-62 CPU
2 GiB of RAM
MSI K9N SLI Platinum mobo
1x36 GiB WD Raptor
9x1 TiB drives of various brands in software RAID-5

it's a Xen setup, dom0 is OpenSuse and I have two domU's (Windows Server 2k8 and NetBSD). Win I use as a file server (FTP only, no fancy things like Samba or whatnot), and NetBSD for everything else (Web, SSH, DNS, NTP)

---

### Post by grantemsley on 2009-09-17
> **nuseryame said:**
> Hi,

I want to know why people have home servers and what servers that are and what they are used for. Also if you virtualize them.


Some of my servers are virtualized.  I run linux on the hardware the the free vmware server for windows VMs.
> 
In Microsoft you have Exchange Server which manages emails for a large number of users. Why have an email server if there are 3 users at home?

Having your own email server means it's under your control.  You don't have to worry about the company your email is at raising prices or shutting down.  Running exchange for 3 users is a bit excessive, I used postfix+courier, but when I had a free licence for exchange through school I used it because it syncs with my phone so much better.
> 
You can have your own webserver, this is to host your own website right? does that mean you don't need to pay a company to host it and don't have to pay for a domain name?

You don't have to pay for hosting, but you do still have to pay for a domain name if you want one.  Or you can use something like dyndns.org for a free subdomain.
> 
Samba is an equivalent to Active Directory? allowing you to share files on the network.

Samba is more like windows file shares than active directory.  It does have some active directory features, but if you want the control over every computer that a domain gives you, windows server still works much better than samba.
> 
What other types of servers are there? SQL is for databases? but only large databases, for small one's you can just use Access.
If you design it with Access, when it eventually grows you have to redo your work.

---

### Post by Sporkman on 2009-09-17
I have two home servers.

One to host my website, the other (which I just bought & is not setup yet) as a fileserver, serving my ubuntu laptop & my wife's Macbook.

---

### Post by wesg on 2009-09-17
I purposely built a server for my network to share files and stream media to my PS3. 

Services
- Apache/PHP/MySQL for web development
- Mediatomb for PS3 streaming
- Netatalk for Apple file sharing
- SAMBA server for Windows
- SSH for remote administration (no monitors connected)

I also use it for heavy lifting to free up my laptop (video conversion, compiling, etc.)

Hardware
- M135 case (4 SATA bays)
- Intel E5200 2.5GHz processor
- 2 GB RAM
- 1 x 500 GB boot drive
- 1 x 750 GB storage drive
- 1 x 1 TB storage drive
- ASUS P5K mobo (4 sata plugs)

---

### Post by openfly on 2009-09-18
Well I just had a HP dl585 G1 shipped to NYCResistor. 

I plan to deploy ESX on it, then use it to test datacenter automation software on it, as well as use it to spin off development machines for NYCResistor members as they need them.

I have a 3TB SATA Disk array which uses SATA -> SCSI conversion on the disks to allow it to use hardware raid controllers.  It's a promise VTRAK 15100.  I'll wire that to one 585.

Through a weird shipping error I now have 2 more 585s.  I probably will just get rid of them though since I probably can't power them all at the same time.

---

### Post by computerwiz_222 on 2009-10-02
My server is a headless mid-size case.

Specs:

AMD Athlon 1800+
2 gigs DDR RAM
1tb storage (2 tb hard drives raided for good measure)
gigabit LAN
lots of fans
Power Consumption: ~40 watts (less than $5.00/month)


I use my server for all kinds of things. To be honest, I am a complete Linux newbie. I store all of my movies, TV Shows and Music among other things on it.

My main computer is a Macbook connected to a nice 22" display. What I was doing before I built this server was downloading things until the small 160gb hard drive was full then dumping watched TV shows and Movies to an external hard drive. This got slightly annoying, so I created the best server I could with some old parts and some new.

I am a big Apple user, so I use my server as a "Time Machine". 

I host a couple websites on it.

I have a UPS connected to it via USB. When the hydro goes out, the server will run for approximately half an hour and then gracefully shutdown when the batteries get low. When the power comes back on, the server turns back on.

I am currently looking into a way of using it to record CCTV cameras, but I am not sure how that will affect the performance of the machine since I am already taxing the PCI bus as it is.

---

### Post by ikt on 2009-10-02
Hardware:

AMD Athlon64 3000+
2GB RAM
Cant' remember much else :/

Services
- Apache/PHP/MySQL
- SAMBA file server for Windows
- SSH for remote administration
- wtorrent as my torrent client of choice
- wordpress

and that's about it.

---

