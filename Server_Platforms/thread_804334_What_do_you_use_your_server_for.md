---
title: "What do you use your server for?"
date: 2008-05-23
forum: Server Platforms
---

### Post by samosamo on 2008-05-23
Lets see what we can come up with.  I need more apps to play with.

My server's duty is a little bit of everything.   everything except email and routing (i have a real host for web/email and my WRT54G+Tomato takes care of routing).  it does backups to an mdadm raid5 array, ipv6 routing, logging, VOIP, and more.  in addition to the basics like samba, cups, apache2, it has:

webmin - for administration
samba - for windows sharing
netatalk - for mac AFP sharing and TimeMachine server
mt-daapd - for an itunes daap server
avahi - bonjour services for daap and afp
rdiff-backup - for incremental backups on network machines.  also use the webmin slbackup-php module to go along with it
syslog-ng - for a log server
openvpn - for remote access to my home lan
znc - for IRC bouncing
asterisk - for VOIP
glftpd - for FTP, dead project, one day i may change to wzdftpd
radvd - announces ipv6
squid - proxy service and cacher

and on apache, i run:
ampache - music cataloging, streaming, and more
php-syslog-ng - web GUI for syslog-ng
torrentflux-b4rt - web GUI for tornado/transmission
wtorrent - web GUI for libtorrent/rtorrent
slbackup-php - web GUI front end for slbackup, also use the webmin module

and thats it.  it runs hardy server and everything listed is installed from repo except the torrent GUI's and php-syslog-ng.

---

### Post by MJN on 2008-05-23
Do you mean just for fun? For experimentation?

A couple of areas you haven't touched on are web proxying e.g. [Squid]("http://www.squid-cache.org/"), or security/surveillance tasks such as [Zoneminder]("http://www.zoneminder.com/").

Mathew

---

### Post by jonabyte on 2008-05-23
I have a few I use for web, storage, testing, etc.

---

### Post by samosamo on 2008-05-23
> **MJN said:**
> Do you mean just for fun? For experimentation?

A couple of areas you haven't touched on are web proxying e.g. [Squid]("http://www.squid-cache.org/"), or security/surveillance tasks such as [Zoneminder]("http://www.zoneminder.com/").

Mathew

yah i suppose you can say "for fun."  my server, it makes life easier.  and more organized.  i can access anything from anywhere, and its all automated.

what is the purpose of using squid ?

that zoneminder looks rediculous.  it costs money to buy cameras though.  i have a wifi webcam i'm gonna get that set up.  thanks :)

---

### Post by MJN on 2008-05-23
The link tells you everything there is to know about Squid, however I use it specifically to provide me with access to various geographically-restricted web content whilst I'm working abroad e.g accessing the BBC iPlayer TV-on-demand service whilst out of the UK - for licensing reasons it restricts access to UK-only IP addresses hence I proxy my laptop's web surfing through my UK-based server (running Squid).

As for Zoneminder, I'm not sure what you mean about it being 'ridiculous' ... in my book that sounds like a negative but I'm not sure how you meant it! It works well, very well, and I use it to keep on eye on various parts of my house through four wired-IP cameras and a locally-attached USB cam. It detects motion and automatically records it (locally and offsite) and alerts me via SMS if it thinks I'm being robbed. It's arguably the most useful server app I have - and perfect for checking up on things (including the cats) whilst away on business/holiday etc.

You may have mixed success using ZM with a wireless webcam as they are not best known for their long-term stability in terms of providing an uninterrupted video stream. 

Mathew

---

### Post by NateMan on 2008-05-23
I use mine as a webserver, streaming music server, nas, and a few other minor things. I'd like to get my mail server configured to work properly, but I just haven't had the motivation or need to mess with it. What do you think about amapache vs gnump3d? I've looked into zoneminder and it seems like an interesting piece of software. Have you tried going out and trying some of the different server setup guides on the internet? An old P2 or P3 is great to experiment on so you don't break your daily driver. Have you tried learning a little bit of javascript and html to setup your own webpage? That side of it can be quite fun as well. How do you like using asterisk for voip? A firewall box is also a great experiment. I like bsd a little better for it than linux though...

---

### Post by peterbrewer on 2008-05-23
My server is designed with the single purpose of managing a custom made sound desk.

---

### Post by artesvida on 2008-05-23
My server does...
[LIST][*]ZABBIX!  For network monitoring and trending.
[*](This seems a bit silly for a server platform) I've set it up to play the hold music for our phone system.
[*]NTP server for my local network.[/LIST]
Another one (in a VM) runs Plone.  Sort of just for testing at this point.

---

### Post by FakeOutdoorsman on 2008-05-23
I use an ancient PII to remotely retreive mySQL databases as an offsite backup for another server.  At different times in the past I've used it as a honeypot, torrent machine, and web dev box.

---

### Post by samosamo on 2008-05-24
> **NateMan said:**
> What do you think about amapache vs gnump3d? 

I just looked at gnump3d and i didn't even bother downloading it.  jinzora and subsonic are comparable to ampache but i used them all and prefer ampache.  ampache has very active development right now and they are working on interfacing amarok2 with it.

---

### Post by windependence on 2008-05-25
I use my servers for hosting virtual machines using VMware server. This way I can have multiple web servers for different clients instead of using virtual hosting (not that there is anything wrong with that) and I can also have mail servers, SQL servers, etc, and each one has their own "machine" without using more hardware. All of my guest OSs are some sort of *BSD, but mostly FreeBSD because it is the lightest platform I can use for serving the web, and it's rock solid, even more so than Linux. 

I currently have two similar boxes. The main one is a dual Opteron 2.8 GHz machine with 8 Gigs of RAM, and 1.1 TB of storage. the second box is the backup box right now but it will become the production server after I test it for about a month. This one is a real screamer. Dual Quad core opterons with 12 gigs of RAM and 1.5 TB of storage. I will probably be running 8-10 VMs on this box.

-Tim

---

### Post by windependence on 2008-05-25
> **artesvida said:**
> My server does...
[LIST][*]ZABBIX!  For network monitoring and trending.
[*](This seems a bit silly for a server platform) I've set it up to play the hold music for our phone system.
[*]NTP server for my local network.[/LIST]
Another one (in a VM) runs Plone.  Sort of just for testing at this point.

I'm curious about ZABBIX. Tell me what you can do with it. Also, how do you like Plone so far and how was it to install? I almost tried it last year but went with something else.

-Tim

---

### Post by pedromartins on 2008-05-25
I took an old Compaq Deskpro EN450 with a PII 450MHz, 128Mb RAM and a 120Gb Hdd, no CD-Rom.
I just installed Ubuntu 8.04 LTS Server Edition (with LAMP).
It's intended to be used as intranet webserver.
I'm developing some kind of ERP/CMS to be used by about 10 users.
I have it working with WinXP (WAMP) but I want to give up because it always hangs!
Of course, it's Windows...
And I really need an 'always on, always available' service.
For what I read here, Ubuntu Server is good enough for me.
 
I have a lot of questions regarding FTP server configuration, but I'll ask it in the proper place.

---

### Post by Der_Idiot on 2008-05-25
8.04 Server.
3800+ X2
2gb DDR500
DFI SLI-DR
1x 250g boot drive
6x 250g data drives (will swap for 1tb drives when price is >200)

Webmin
Cacti
Apache2
PHP5
DHCP
Linux Firewall
IP Masq.

I am using the server as a network data dump, router, webhost, and testbed. I'll be using software raid5 for further tinkering.

---

### Post by molotov00 on 2008-05-25
I haven't heard people mention FireFly. This could be an interesting choice for people wanting to stream to iTunes, as I do.

Also, although it's not a *nix solution, I use TVersity to serve my video files to an xbox360.

M

---

### Post by jayson.rowe on 2008-05-25
Which server? I have two at home, and 200+ at work :-)

At home, I have a AMD64 box I use as a VMWare Host server running Ubuntu as the host OS, and many others as guests (including other "virtual" servers), and my Laptop is a pseudo server, running Win Server 2k3 and is my web server and "file transfer location" at home.

---

### Post by artesvida on 2008-05-27
> **windependence said:**
> I'm curious about ZABBIX. Tell me what you can do with it. Also, how do you like Plone so far and how was it to install? I almost tried it last year but went with something else.


I use Zabbix for network monitoring and trends.  I get a page/e-mail if a server goes down, starts running out of disk space, etc.  For Windows & Linux servers it uses an active agent (on the monitored system) to get its data.  It also uses SNMP (both gets and traps), and with SNMP I'm watching the temp/humidity in the server room, network usage across our firewall, power status (on battery or not).  And finally, it supports server-side scripts, and I'm using one to monitor the latency across our WAN links.  So, not only do you get pages when things are out of whack, but it keeps historical data as well.  I can see how much the server room temperature spikes on weekends when the building A/C goes out (yes, I'm working on a dedicated one).  I can see how much Internet bandwidth we're using throughout the day, and how it has increased over the last X months.  I love it, and have found it easy to install and configure.

Plone.  I found it easy to install.  Getting the basics configured was relatively easy.  Putting together a completely custom site?  I think it would take some work.  I would prefer if Plone used MySQL or Postgres rather than Zope.  I would like to change some of the out-of-the-box functionality, but this has proven to be non-trivial.  Overall, my experience has been OK, and for my limited needs it has worked out well.  If it was going to host my company's web page, I would want a Plone/Zope bootcamp.

---

### Post by windependence on 2008-05-27
Thanks for the info. I am still evaluating cms software and I had looked at Plone and thought it might be a good solution but I have never loaded it. I appeciate your insight.

-Tim

---

### Post by rjs82vette on 2008-06-24
p4 1.8, 1g ram, terabyte hard drive x4

ssh (remote access)
vnc (remote access w/gui)
mythtv-backend (movies)
mythweb (remote access to movies)
file server (file stoarage)
squid (watch the kids)
dansguardian (control the kids access)
apache2 (website)
apache tomcat (for subsonic)
subsonic (streaming music)
xoop (cms)
drupal (to be removed in favor of xoop)
jinzora (to be removed in favor of subsonic)
ftp (remote file access)
zoneminder (watch the house and kids)
torrentflux (torrents)
egroupware (calender and more)
webmin (remote gui admin)
samba (windows file share)
nfs (linux file share)

Ummm that it for now, looking for more stuff to do......

---

### Post by samosamo on 2008-10-22
i updated it!

---

### Post by thefekete on 2008-10-23
**Home Server:**

P4 3GHz, 1G Ram, 6x500G HDs, 4x320G HDs
[LIST]
[*]3.15TB RAID-5+LVM Fileserver (sftp, samba - 83% used!)
[*]Subversion
[*]MySQL
[*]PostgreSQL
[*]Apache
[*]5 virtual hosts
[*]DokuWiki
[*]phpmyadmin
[*]pgmyadmin
[*]php
[*]bookshelf (for the important ones)
[/LIST]

**Work:**

2xAMD 2.4GHz dual core 64 bit, 4G RAM, 4x250G HDs, 1u rack mount
[LIST]
[*]sftp
[*]samba
[*]SVN
[*]Apache
[*]DokuWiki
[*]TinyERP
[*]IP Masq.
[*]Firewall (IP tables FTW)
[*]PostreSQL
[*]rtorrent(couldn't pass it up on a bonded T1!)
[*]adding more each day...
[/LIST]

Also have a low powered Asterisk server at work for VoIP and SIP phones (3 VoIP lines, 6 phones)

---

### Post by simonn on 2008-10-23
My home server...

Koolu Net Appliance
AMD Geode 500Mhz/512Mb
80Gb Internal IDE
160Gb External 2.5" USB/IDE
2 x Twinhan USB2.0 DVB-T recivers
Canon LiDE 20 scanner
APC Back-UPS CS 650 UPS

Uses only 7 watts in idle and 12 watts max!

Runs...
Apache
Webmin
Squeezecenter, to serve our Squeeze Box.
transmission-daemon
Saned (scanner server)
And the usual dnsmasq, ssh, samba and ntpd

Apache:
serves 3 ports, 80, 81 and 443.
Port 443 is where most stuff goes on and is password protected. My work only allows SSL access to external sites which use port 443 for SSL, so I proxy or run almost everything I need to access externally using SSL on this port:
- webmin
- squeezecenter
- mediawiki
- Home written php dvb recorder front end which uses the at command for scheduling and shell scripts using mencoder to actually record.
- Home written php front end for transmission-remote and to do mininova searches. I could not get apache to proxy the html interface properly.
Port 80 runs an externally accessable http server. Not really used much. Just a couple of videos of our vacation escapades of higher quality than facebook video/youtube.
Port 81 runs an internally accessable web server to stream dvb recordings from.
Webmin, squeezecenter are also accessible on their native ports in our "intranet" :).

Have also started experimenting with the idea of setting up vlc (using vlc-nox) to stream dtv to our laptops, so we can watch tv wherever (in our two bedroom unit/flat/apartment :)). However, wireless seems to be a bit too slow for the DTV recievers stream  - which is odd as recordings are ok(?) - and the koolu is not fast enough to transcode. Luckily TV in Oz is crap so we hardly ever watch it anyway :).

My ADSL plan, like most in Oz, has a monthly download limit, so I have written shell scripts to check my current usage and then determine whether to stop or start bittorrent. All works automatically.

---

### Post by Thirtysixway on 2008-11-16
I use my server for

Web development/testing (lighttpd/mysql/php)
Virtualization (VMWare)
Torrents (torrentflux)
File sharing/backups (samba)

I used to run quake 3 arena server on it and I'm looking around for more things to squeeze onto my machine :)

---

### Post by handy on 2008-12-21
***Hardware:***

Dell Optiplex GX150 (Cost $5- at the rubbish dump)
PIII 731Mhz
256Mb PC133 SDRAM
10Gb HDD

It's setup as a headless IPCop box, including the benefits of the wonderful Copfilter add-on.

***I'm using the following of IPCop's services:***
CRON Server
DHCP Server
DNS Proxy Server
Kernel Logging Server
Logging Server
Secure Shell Server
Web Proxy
Web Server

***I'm using the following Copfilter services:***
Monitoring Utility
HAVP - HTTP Proxy
Privoxy
Frox - FTP Proxy
ClamAV

The CPU rarely does more than idle.  Even with the Privoxy & ClamAV running they are totally transparent & don't slow down the surfing experience.

I'm watching the rubbish dump to find 2 machines suitable for the jobs I want done.  1 is to be an rtorrent slave, the other will be a NAS box, for our data & movies.

Really nothing exciting here, but it is fun to learn about & set up. :-)

---

