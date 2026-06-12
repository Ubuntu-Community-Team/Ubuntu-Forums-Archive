---
title: "Home Server Software Ideas"
date: 2009-02-20
forum: Server Platforms
---

### Post by quietas on 2009-02-20
What al are you using on your headless home server?

I'm not necessarily wondering about Gnome/KDE apps since Ubuntu server is a CLI driven headless server. CLI or web based and available in the repositories would be best.

Here's my system I have setup recently and am using now:
[B]
Ubuntu Server 8.10 Intrepid[/B] (8.04 Hardy upgraded, headless troll which lives in my closet)
**[Ebox]("http://www.ebox-platform.com")** - Web GUI, Samba, Squid, Dan's Guardian, DNS, DHCP, PDC (essentially home router/gateway management)
**[Firefly Media Server]("http://www.fireflymediaserver.org/")** - Itunes compatible DAAP server for network MP3 sharing
**[TorrentFlux]("http://www.torrentflux.com/")** - Web based torrent downloading

What else is out there which would be useful? Chime in and out it out there. I have seen plenty of people asking about home servers, so we might as well let everyone know what we can actually do.

One thing I thought of, but not yet found, is some web based stats page to act as a home page. Also a web based file manager, something like AjaXplorer ([http://www.ajaxplorer.info]("http://www.ajaxplorer.info")) would be useful.

---

### Post by E_K on 2009-02-20
not sure what kind of stats your looking for but check out cacti, I have a web based php file manager that you could use, but that is not from repos

---

### Post by insineratehymn on 2009-02-20
On Ubuntu 7.10 900mhz 256mb 540gb hd:

Twonky Media Server: HD over hardline to wireless to xBox 360
rTorrent: CLI based torrent program (and anti-ISP shaping)
webmin: If Im lazy.
Apache2
OpenSSH
sshfs

---

### Post by quietas on 2009-02-20
> **E_K said:**
> not sure what kind of stats your looking for but check out cacti, I have a web based php file manager that you could use, but that is not from repos

I set up a quick index.html to link to ebox, firefly, torrentflux. I'd like make that a bit more functional with cpu temp, load, drive usage, network speed. Similar to something like Rainlender or Samurize or Conky, but as a web front end to my server with a section for links.

---

### Post by E_K on 2009-02-20
well heres something i wrote to monitor some of those things on my server

first you need to install 2 things

```
apt-get install hddtemp
```

then follow this to install and setup lm-sensors

[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

and heres what i use to post it to the web, you will have to adapt the script for yourself it should be fairly neatly set out, i didnt plan on sharing it, but you can change whatever you want and remove my name, but if you earn money with it i want 50% hehehe

```
nano output.sh
```

then paste this in

```

#!/bin/bash
TERM=linux
#
# Server Stats 2 Html v2
#
# @Paddy.Net

# user variables
export LOGFILE=/var/www/temp.html;
export SCRATCHFILE=/var/spool/temp;
export HDD0=/dev/sda;
export HDD1=/dev/sdb;

# main routine
clear;
touch $LOGFILE;
touch $SCRATCHFILE;
echo "<html>" > $LOGFILE;
echo "<head>" >> $LOGFILE;
echo "<meta http-equiv="refresh" content="300">" >> $LOGFILE;
# echo "<span style="color:#00CC00">" >> $LOGFILE;
echo "</head>" >> $LOGFILE;
echo "<BODY BGCOLOR="#000000" TEXT="#00CC00">" >> $LOGFILE;
echo "Server Hardware Status Capture V2";
echo "";
echo "<h1>Server Hardware Status Capture V2</h1>" >> $LOGFILE;
echo "<br>" >> $LOGFILE;
echo "Designed, Created & Developed By @Paddy.Net";
echo "";
echo "<h2>Designed, Created & Developed By @Paddy.Net</h2>" >> $LOGFILE;
echo "<br>" >> $LOGFILE;
echo "Creating HTML Formated Document";
echo "";
echo "Outputing Hard Drive Temperature Statistic Readouts";
echo "";
echo "<h3>Hard Drive Temperature Statistic Readouts:</h3>" >> $LOGFILE;
echo "<h4>First Hard Disk Temperature</h4>" >> $LOGFILE;

# temperature displayed in local console will be lower than in the web view
hddtemp $HDD0;
hddtemp $HDD0 >> $LOGFILE;
echo "<br>" >> $LOGFILE;
echo "<h4>Second Hard Drive Temperature</h4>" >> $LOGFILE;
hddtemp $HDD1;
hddtemp $HDD1 >> $LOGFILE;
echo "<br>" >> $LOGFILE;
echo "<br>" >> $LOGFILE;
echo "";
echo "Outputing Hardware Statistics Readouts";
echo "";
echo "<h3>Hardware Statistics Readouts:</h3>" >> $LOGFILE;
sensors;
sensors > $SCRATCHFILE;
sed -i 's/$/<br>/' $SCRATCHFILE;
cat $SCRATCHFILE >> $LOGFILE && echo "</html>"  >> $LOGFILE && rm -vf $SCRATCHFILE;
echo "";
echo "HTML created. All temporary files have been cleaned";
echo "";

# clear environment variables
export LOGFILE=
export SCRATCHFILE=
export HDD0=
export HDD1=

exit;



```

then make it executable
```

chmod +x output.sh
```

and you can run by

```
./output.sh
```

or

```
/directory/output.sh
```

have fun :)

and as you keep it local theres webmin, but read up on the security risks ;)

---

### Post by jamesrfla on 2009-02-20
I run apache2, Citadel mail server, Terminal server, samba, mysql, and SSH server. I am using Ubuntu 8.04 Desktop edition so I use it as a home server and a desktop.

---

### Post by CrucifiedEgo on 2009-02-20
I hate blogspam, but, I did a post awhile back on this.  The project it was regarding is stalled for the time being, but maybe it will give you some ideas:

[http://diffra.com/2008/11/home-linux-server-why/](http://diffra.com/2008/11/home-linux-server-why/)

---

### Post by quietas on 2009-02-20
> **CrucifiedEgo said:**
> I hate blogspam, but, I did a post awhile back on this.  The project it was regarding is stalled for the time being, but maybe it will give you some ideas:

[http://diffra.com/2008/11/home-linux-server-why/](http://diffra.com/2008/11/home-linux-server-why/)

I like your ideas and have already implemented most of them. I did not see Jinzora in the repos, but I'm going to look for something similar. I thought of setting up a Shoutcast/Icecast server and a few playlists to rotate through as another option.

---

### Post by rhcm123 on 2009-02-20
This is gonna make you all laugh :)

1997 IBM Desktop
90 Mhz AMD Processor
85 MB RAM
PC bus 100 mbps network card
250 GB Hdd (i just installed that)

Running:
Ubuntu 8.04/8.10 (depends on if i've reinstalled it again :) )
-Apache2 and SSL (All webpages are over HTTPS)
-SSH/SSHFS for remote administration/data tranfer
-Webmin for remote monitoring
-Jinzora for music/video sharing
-CUPS (all computers print to it, and i can print to it from the net).
-Postfix/Courrier integrated with SquirrelMail and by BlackBerry (!)
-DHCP3 for the entire house
-SAMBA Share (1 folder in the /share directory for each user)

I think i have enough, am i rite?

---

### Post by quietas on 2009-02-20
Lol, on a 90mhz processor. I'd say that is plenty, but also shows the power of Linux. I'd hazard to guess the web traffic is not extreme and is not serving up fancy pages?

---

### Post by 3L33T on 2009-02-20
Running 8.04 Hardy Server Edition:  apache, menalto gallery, s9y blog, ssh, vnc, ftp, ibm ids 11.5, and looking into vBulletin currently :)

---

### Post by rhcm123 on 2009-02-20
> **quietas said:**
> Lol, on a 90mhz processor. I'd say that is plenty, but also shows the power of Linux. I'd hazard to guess the web traffic is not extreme and is not serving up fancy pages?

well, it does serve jinzora, which is web 2.0
but no, not heavy traffic. I go on it about twice daily

remember the guy who made the web server out of the 880 intel or whatever it was?
Running slackware!

---

### Post by quietas on 2009-02-20
I added a quick and dirty page to the front. I removed the index.html I had and replaced it with an updated index.php so I could run some CLI scripting.

index.php
```

<?php
// ==================================================================
// Basic server infomation and links to internal webpages.
// ==================================================================
?>

<html>
<head>
<title>Home Server</title>
<center><h1>Local Admin Pages</h1></center><br>
<center><a href=https://server>Ebox-Platform</a> - <a href=http://www.ebox-platform.com>Home</a><br></center>
<center><a href=http://server:3689>Firefly Media Server</a> - <a href=http://www.fireflymediaserver.org>Home</a><br></center>
<center><a href=http://server/torrentflux>Torrent Flux</a> - <a href=http://www.torrentflux.com/>Home</a><br></center>
<br>
<STYLE type=text/css>
BODY { FONT-SIZE: 8pt; COLOR: black; FONT-FAMILY: Verdana,arial, helvetica, serif; margin : 0 0 0 0;}
</STYLE>
</head>
<body>
<center><table><tr><td>
<pre>
<b>Uptime:</b> 
<?php system("uptime"); ?>

<b>Kernel Information:</b>
<?php system("uname -a"); ?>

<b>System Information:</b>
<?php system("lsb_release -a"); ?>

<b>Memory Usage (MB):</b> 
<?php system("free -t -m"); ?>

<b>Disk Usage:</b> 
<?php system("df -h | grep /dev/sd"); ?>

<b>CPU Information:</b> 
<?php system("cat /proc/cpuinfo | grep \"vendor_id\\|\model name\\|cpu MHz\\|bogomips\""); ?>
</pre>
</td></tr></table></center>

</body>
</html>
```

It gives me a page which looks like this:
```
[COLOR="Black"][B][SIZE="5"]
Local Admin Pages[/SIZE][/B][/COLOR]

_Ebox-Platform_ - Home
_Firefly Media Server_ - Home
_Torrent Flux_ - Home
[B]
Uptime:[/B] 
 14:14:50 up 15:54,  1 user,  load average: 0.31, 0.19, 0.13

**System Information:**
Linux server 2.6.27-11-server #1 SMP Thu Jan 29 20:19:41 UTC 2009 i686 GNU/Linux

**Memory Usage (MB):**  
             total       used       free     shared    buffers     cached
Mem:          2016       1963         52          0         41       1666
-/+ buffers/cache:        255       1760
Swap:         5906          3       5903
Total:        7922       1966       5955

**Disk Usage:** 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1             227G  2.6G  213G   2% /
/dev/sda1             917G   77G  795G   9% /home/share/1tb-1
/dev/sdb1             917G   93G  779G  11% /home/share/1tb-2
/dev/sdd1             226G   37G  177G  18% /home/share/250gb-2

**CPU Information: **
vendor_id	: AuthenticAMD
model name	: AMD Athlon(tm) XP 2000+
cpu MHz		: 1666.366
bogomips	: 3332.73
```

---

### Post by quietas on 2009-02-20
I also thought I would add in **WinSCP** since I have yet to find a decent web baed file manager with a deb in the repos and does not seem like it is from the 80's.

---

### Post by rhcm123 on 2009-02-20
> **quietas said:**
> I added a quick and dirty page to the front. I removed the index.html I had and replaced it with an updated index.php so I could run some CLI scripting.


Mind if I steal your script?

---

### Post by quietas on 2009-02-21
> **rhcm123 said:**
> Mind if I steal your script?

Go for it. I'm seeing what other commands might be nifty to add in there.

I set it up for the normal port 80 so I can have a simple table of contents for my admin pages for each bit of software.

---

### Post by rhcm123 on 2009-02-21
> **quietas said:**
> Go for it. I'm seeing what other commands might be nifty to add in there.

I set it up for the normal port 80 so I can have a simple table of contents for my admin pages for each bit of software.

Alright, i'll have to configure that for https, but it should (read: should) work :)

---

### Post by E_K on 2009-02-22
Nice!!!

I like you took your own individual turn on what i showed on previous page,

its good, I will also add some of that to mine:)

Though 2/3 things you shoud add ;)

<meta http-equiv="refresh" content="300">

to refresh the page automatically(nice for the mem part)

make the backgroud black and text green

<BODY BGCOLOR="#000000" TEXT="#00CC00">

I think it looks way kooler :)

---

### Post by TwiceOver on 2009-02-22
My home server (currently being redone)
Dual Xeon 1.6ghz 2gb ram 4 hard drives
Ubuntu 8.04 server LAMP/SSH/Samba

What I run:
DNS - For local name resolution
Samba/NFS shares for my linux desktop/laptop and wife's Windows Laptop
pyTivo - for Sharing media with my Tivos
Subsonic - Internet audio streamer to stream my music to wherever I am
Gallery2 - Host images for the web in a nice templated format
Drupal - Intranet page for wife and I to keep track of calendar dates/tasks/etc
phpmp2 - PHP frontend for MPD to play music out of the server box to an FM transmitter to listen to music on any radio and change songs via a web browser.
ProFTPD - FTP access

Still looking for an XBox 360 streamer, but all the Linux solutions suck except Twonky, which I will not pay for.  Might end up putting vmware server on just for this (and maybe to replace pyTivo with the Tivo windows server).

---

### Post by rhcm123 on 2009-02-22
> **TwiceOver said:**
> My home server (currently being redone)
Dual Xeon 1.6ghz 2gb ram 4 hard drives
Ubuntu 8.04 server LAMP/SSH/Samba

What I run:
DNS - For local name resolution
Samba/NFS shares for my linux desktop/laptop and wife's Windows Laptop
pyTivo - for Sharing media with my Tivos
Subsonic - Internet audio streamer to stream my music to wherever I am
Gallery2 - Host images for the web in a nice templated format
Drupal - Intranet page for wife and I to keep track of calendar dates/tasks/etc
phpmp2 - PHP frontend for MPD to play music out of the server box to an FM transmitter to listen to music on any radio and change songs via a web browser.
ProFTPD - FTP access

Still looking for an XBox 360 streamer, but all the Linux solutions suck except Twonky, which I will not pay for.  Might end up putting vmware server on just for this (and maybe to replace pyTivo with the Tivo windows server).

I heard jinzora is a good solution for 360 streaming, but my install aparently can't do that. :(
The most ingenious solution i ever heard of was some guy setup a virtual machine running windows media center. worked like a charm :)

---

### Post by TwiceOver on 2009-02-22
> **rhcm123 said:**
> I heard jinzora is a good solution for 360 streaming, but my install aparently can't do that. :(
The most ingenious solution i ever heard of was some guy setup a virtual machine running windows media center. worked like a charm :)

Yeah, I've never been able to get Jinzora to do that.  Also was never able to get Jinzora to pick up album art, so I gave up on it.

I'll probably do the VM + XP to serve my 360.  I'd love to find a FOSS way to do it but Fruppes and ushare were always wonky at best.  Twonky is $50 I think which is about $40 more than I'm willing to pay for it.

I need a VM anyway to run Microsoft Money (sorry there still isn't a good linux money management program...  And no GnuCash, KMyMoney, etc are not good)

---

### Post by rhcm123 on 2009-02-23
> **TwiceOver said:**
> Yeah, I've never been able to get Jinzora to do that.  Also was never able to get Jinzora to pick up album art, so I gave up on it.

I'll probably do the VM + XP to serve my 360.  I'd love to find a FOSS way to do it but Fruppes and ushare were always wonky at best.  Twonky is $50 I think which is about $40 more than I'm willing to pay for it.

I need a VM anyway to run Microsoft Money (sorry there still isn't a good linux money management program...  And no GnuCash, KMyMoney, etc are not good)

I might ditch jinzora for somthing integrated with flash as it has no HTTPS support. I don't want my login going transmitted over HTTP across this broad interweb. Besides, I might just shell out for twonky. I'm getting an SSL certificate in a few months (when i finally get annoyed about my self-signed one) and i might just use that as an excuse to waste another $50.

and yes, there are no good linux accounting programs. I must say microsoft does office best

---

### Post by Thirtysixway on 2009-02-24
Running Ubuntu 8.04 server

xycom industrial node
1.2 GHz processor
512 MB ram (I could really use some more :))
39GB harddrive (I want something like 300 GB but I'm not sure how to transfer everything over from the old one if I bought a new one)

_Running:_
Apache2
mysql
Torrentflux
Samba
Folding@Home (go team Ubuntu :))
vmware - virtual w2k for my old vb6 server application
vnstat - monitor bandwidth (using php frontend to view stats)
uprecords

I use it mostly for file sharing, printer sharing, torrents, and web development.  One day when I buy a long enough USB extender, I want to have a webcam setup at the back door so I can see if my dog wants inside.

---

### Post by rhcm123 on 2009-02-24
> **Thirtysixway said:**
> One day when I buy a long enough USB extender, I want to have a webcam setup at the back door so I can see if my dog wants inside.

you can get wi-fi USB systems

EDIT: Oh, quietas! I used your script on my server. I modified it a little and added a few extra thingys. I omitted my domain name (it has my last name) but added in a few goodies like an auto refresh tag, file system, info, and bug reporter (as my parents/grandparents use the server alot)

```
<?php
// ==================================================================
// Script written by quietas (http://ubuntuforums.org/member.php?u=300503)
// Script Modified 24 Feb 2009 by ussr - CHANGE THIS WHEN YOU MOD THIS
// Make sure this is all good for running over SSL.
// ==================================================================
?>

<html>
<head>
<BODY BGCOLOR="#000000" TEXT="#00CC00">
<title>USSR-MOSCOW MAIN SERVER PAGE</title>

<br>
<STYLE type=text/css>
BODY { FONT-SIZE: 8pt; FONT-FAMILY: Verdana,arial, helvetica, serif; margin : 0$
</STYLE>
</head>

<center><h1>ADMINISTRATION PAGE FOR USSR-MOSCOW</h1></center><br>
<center>AUTHORIZED ACCESS ONLY. SERVER LOGS ARE MONITORED</center<br>

<h1>
<center><a href=https://(omit).dyndns.org/jinzora2> Jinzora2 Music Server </a><br></center>
<center><a href=https://(omit).dyndns.org/squirrelmail> SquirrelMail Email System </a><br></center>
<center><a href=https://(omit).dyndns.org:10000/> Webmin Online Administration Console </a><br></center>
</h1>


<body>
<center><table><tr><td>
<pre>
<b>Uptime:</b> 
<?php system("uptime"); ?>

<b>Kernel Information:</b>
<?php system("uname -a"); ?>

<b>System Information:</b>
<?php system("lsb_release -a"); ?>

<b>Memory Usage (MB):</b> 
<?php system("free -t -m"); ?>

<b>Disk Usage:</b> 
<?php system("df -h | grep /dev/sd"); ?>

<b>Mounted Filesystems:</b>
<?php system("di"); ?>

<b>CPU Information:</b> 
<?php system("cat /proc/cpuinfo | grep \"vendor_id\\|\model name\\|cpu MHz\\|bogomips\""); ?>
</pre>
</td></tr></table></center>

<center><h3>Report bugs <a href="mailto:ussr@(omit).dyndns.org"> here </a></h3></center>

<meta http-equiv="refresh" content="30">
</body>
</html>


```

---

### Post by quietas on 2009-02-24
Nifty. I also added a meta refresh to mine.

I also thought about adding in a web cam, possibly wifi with, or in, an exterior housing so I could make it accessible for my relatives down south to see the wonders of Alaska they are missing by moving out of state. =)

---

### Post by rhcm123 on 2009-02-24
> **quietas said:**
> Nifty. I also added a meta refresh to mine.

I also thought about adding in a web cam, possibly wifi with, or in, an exterior housing so I could make it accessible for my relatives down south to see the wonders of Alaska they are missing by moving out of state. =)

dosen't linksys make an external web cam that runs on batteries and connects via wi-fi?

---

### Post by rhcm123 on 2009-02-24
> **quietas said:**
> Also a web based file manager, something like AjaXplorer ([http://www.ajaxplorer.info]("http://www.ajaxplorer.info")) would be useful.

I reccomend, actually, webmin for this. One of the default installed modules is a java-based file management app. Careful though, as it runs with root priviliges (which is bad if you don't know what you are doing.)

---

### Post by alek66 on 2009-04-21
What do you recommend for a server without a head and use remote desktop?

---

### Post by quietas on 2009-04-21
Ebox works great for most management tools. Webmin has more features, but can be a pain the ***. FreeNAS is a great non-Ubuntu home server also.

I use Ebox for my management since it's very user friendly and my wife can deal with it just fine. It's very similar to most commercial home routers.

As for remote desktop, VNC works, but I like NoMachine's FreeNX much more. It's faster and natively runs over SSH port 22. VNC needs additional plugins for encrypted connections which is annoying in this day and age of security. [https://help.ubuntu.com/community/FreeNX]("https://help.ubuntu.com/community/FreeNX")

I know, I know, headless purists say no desktop. Bad, bad, bad. My server is headless in a closet, I installed ubuntu-desktop on it so I could play around, it's my home server I can do what I want =)

Also since I started this thread, I have moved over to 9.0 Jaunty and all is working well. I also swapped to Transmission rather than Fluxbox for better speed and easy of use.

Current config:
Ubuntu 9.04 Jaunty Server - Headless
ASUS P5ND2-SLI Deluxe
P4 3.0 Prescott HT x64
6gb PC6400 RAM
1x 146gb WD Raptor SATA2, 2x 500gb Seagate SATA2, 2x 1tb WD SATA2
Transmission
Firefly media Server
Jinzora
Ebox (webmin loaded, but soon to be removed)
PHPMyAdmin
Wordpress

---

### Post by scottuss on 2009-04-21
I used to run Webmin on my server until I switched over to an Astaro Security Gateway. It's much easier to configure if you're just after a Security Gateway / Router.

Obviously it's no good if you need other services like file / print sharing..

---

### Post by jamesrfla on 2009-04-21
> **quietas said:**
> 
It gives me a page which looks like this:
```
[COLOR="Black"][B][SIZE="5"]
Local Admin Pages[/SIZE][/B][/COLOR]

_Ebox-Platform_ - Home
_Firefly Media Server_ - Home
_Torrent Flux_ - Home
[B]
Uptime:[/B] 
 14:14:50 up 15:54,  1 user,  load average: 0.31, 0.19, 0.13

**System Information:**
Linux server 2.6.27-11-server #1 SMP Thu Jan 29 20:19:41 UTC 2009 i686 GNU/Linux

**Memory Usage (MB):**  
             total       used       free     shared    buffers     cached
Mem:          2016       1963         52          0         41       1666
-/+ buffers/cache:        255       1760
Swap:         5906          3       5903
Total:        7922       1966       5955

**Disk Usage:** 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1             227G  2.6G  213G   2% /
/dev/sda1             917G   77G  795G   9% /home/share/1tb-1
/dev/sdb1             917G   93G  779G  11% /home/share/1tb-2
/dev/sdd1             226G   37G  177G  18% /home/share/250gb-2

**CPU Information: **
vendor_id	: AuthenticAMD
model name	: AMD Athlon(tm) XP 2000+
cpu MHz		: 1666.366
bogomips	: 3332.73
```

It kind of looks like the information you would get from phpsysinfo.

---

### Post by alek66 on 2009-04-22
A simple clarification:

Webmin is a web interface to "regular" console dutys.
AjaXplorer: just a file explorer y can use with my users.

---

### Post by daboroe on 2009-04-22
> **TwiceOver said:**
> My home server (currently being redone)
Dual Xeon 1.6ghz 2gb ram 4 hard drives
Ubuntu 8.04 server LAMP/SSH/Samba

What I run:
DNS - For local name resolution
Samba/NFS shares for my linux desktop/laptop and wife's Windows Laptop
pyTivo - for Sharing media with my Tivos
Subsonic - Internet audio streamer to stream my music to wherever I am
Gallery2 - Host images for the web in a nice templated format
Drupal - Intranet page for wife and I to keep track of calendar dates/tasks/etc
phpmp2 - PHP frontend for MPD to play music out of the server box to an FM transmitter to listen to music on any radio and change songs via a web browser.
ProFTPD - FTP access

Still looking for an XBox 360 streamer, but all the Linux solutions suck except Twonky, which I will not pay for.  Might end up putting vmware server on just for this (and maybe to replace pyTivo with the Tivo windows server).

how much was the FM transmitter that you are using? Love your set up

---

### Post by quietas on 2009-04-22
> **jamesrfla said:**
> It kind of looks like the information you would get from phpsysinfo.

I like that.

---

### Post by jongers on 2009-05-08
I think someone mentioned this before.  
But if your using your server as a gateway, Y not use it as a Proxy server, cache external web pages using Squid3 and potentially increase your network requests upto about 100x

I have also used a script called adzapper with squid3 proxy server that removes any unwanted adverts from cached web-pages, reducing not only bandwidth load.  But also increasing screen real estate in Firefox.

Its worth looking into and is not only a very usful and practical example of what a home server should be doing, it gives you an oppertinity to learn more about web protocalls and how it all works.

---

### Post by jongers on 2009-05-08
I have tried to set up my Ubuntu as a wireless router.  Although its using a generic wireless card, it can work as one.  Just as long as the card is master-mode compatible.  
This give you the flexability of sing all the DHCP and DNS functions as well as ll the others such as proxy and file shares.

Just an idea - I know it's possible but can't find anyone who has managed it sucsessfully.

---

### Post by jongers on 2009-05-08
I use Ushare for my Xbox streaming.  support is slightly limited to 50 tracks, but video works great.  think i got over 70 video files accessible.

It's not the perfect solution but does work well.

---

### Post by TwiceOver on 2009-05-08
> **daboroe said:**
> how much was the FM transmitter that you are using? Love your set up

Not really sure.  It was a kit that my dad handed down to me.  Not the greatest most easily configurable system, but plenty powerful enough to cover my property.

I'll also be looking into phpsysinfo.

---

### Post by alek66 on 2009-05-14
> **quietas said:**
> I added a quick and dirty page to the front. I removed the index.html I had and replaced it with an updated index.php so I could run some CLI scripting.

index.php
```

<?php
// ==================================================================
// Basic server infomation and links to internal webpages.
// ==================================================================
?>

<html>
<head>
<title>Home Server</title>
<center><h1>Local Admin Pages</h1></center><br>
<center><a href=https://server>Ebox-Platform</a> - <a href=http://www.ebox-platform.com>Home</a><br></center>
<center><a href=http://server:3689>Firefly Media Server</a> - <a href=http://www.fireflymediaserver.org>Home</a><br></center>
<center><a href=http://server/torrentflux>Torrent Flux</a> - <a href=http://www.torrentflux.com/>Home</a><br></center>
<br>
<STYLE type=text/css>
BODY { FONT-SIZE: 8pt; COLOR: black; FONT-FAMILY: Verdana,arial, helvetica, serif; margin : 0 0 0 0;}
</STYLE>
</head>
<body>
<center><table><tr><td>
<pre>
<b>Uptime:</b> 
<?php system("uptime"); ?>

<b>Kernel Information:</b>
<?php system("uname -a"); ?>

<b>System Information:</b>
<?php system("lsb_release -a"); ?>

<b>Memory Usage (MB):</b> 
<?php system("free -t -m"); ?>

<b>Disk Usage:</b> 
<?php system("df -h | grep /dev/sd"); ?>

<b>CPU Information:</b> 
<?php system("cat /proc/cpuinfo | grep \"vendor_id\\|\model name\\|cpu MHz\\|bogomips\""); ?>
</pre>
</td></tr></table></center>

</body>
</html>
```

It gives me a page which looks like this:
```
[COLOR="Black"][B][SIZE="5"]
Local Admin Pages[/SIZE][/B][/COLOR]

_Ebox-Platform_ - Home
_Firefly Media Server_ - Home
_Torrent Flux_ - Home
[B]
Uptime:[/B] 
 14:14:50 up 15:54,  1 user,  load average: 0.31, 0.19, 0.13

**System Information:**
Linux server 2.6.27-11-server #1 SMP Thu Jan 29 20:19:41 UTC 2009 i686 GNU/Linux

**Memory Usage (MB):**  
             total       used       free     shared    buffers     cached
Mem:          2016       1963         52          0         41       1666
-/+ buffers/cache:        255       1760
Swap:         5906          3       5903
Total:        7922       1966       5955

**Disk Usage:** 
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc1             227G  2.6G  213G   2% /
/dev/sda1             917G   77G  795G   9% /home/share/1tb-1
/dev/sdb1             917G   93G  779G  11% /home/share/1tb-2
/dev/sdd1             226G   37G  177G  18% /home/share/250gb-2

**CPU Information: **
vendor_id	: AuthenticAMD
model name	: AMD Athlon(tm) XP 2000+
cpu MHz		: 1666.366
bogomips	: 3332.73
```
I tried to use your code.... but it didnt worked.... no data is showed... on the status part.

Do i have to make something extra?

Firefly comes with streaming using the webpage?

Is there a way to enter [http://myserver:3689](http://myserver:3689) and have a player to be accesed from the internet??

---

### Post by Serangan on 2009-05-15
> **rhcm123 said:**
> you can get wi-fi USB systems

EDIT: Oh, quietas! I used your script on my server. I modified it a little and added a few extra thingys. I omitted my domain name (it has my last name) but added in a few goodies like an auto refresh tag, file system, info, and bug reporter (as my parents/grandparents use the server alot)

```
<?php
// ==================================================================
// Script written by quietas (http://ubuntuforums.org/member.php?u=300503)
// Script Modified 24 Feb 2009 by ussr - CHANGE THIS WHEN YOU MOD THIS
// Make sure this is all good for running over SSL.
// ==================================================================
?>

<html>
<head>
<BODY BGCOLOR="#000000" TEXT="#00CC00">
<title>USSR-MOSCOW MAIN SERVER PAGE</title>

<br>
<STYLE type=text/css>
BODY { FONT-SIZE: 8pt; FONT-FAMILY: Verdana,arial, helvetica, serif; margin : 0$
</STYLE>
</head>

<center><h1>ADMINISTRATION PAGE FOR USSR-MOSCOW</h1></center><br>
<center>AUTHORIZED ACCESS ONLY. SERVER LOGS ARE MONITORED</center<br>

<h1>
<center><a href=https://(omit).dyndns.org/jinzora2> Jinzora2 Music Server </a><br></center>
<center><a href=https://(omit).dyndns.org/squirrelmail> SquirrelMail Email System </a><br></center>
<center><a href=https://(omit).dyndns.org:10000/> Webmin Online Administration Console </a><br></center>
</h1>


<body>
<center><table><tr><td>
<pre>
<b>Uptime:</b> 
<?php system("uptime"); ?>

<b>Kernel Information:</b>
<?php system("uname -a"); ?>

<b>System Information:</b>
<?php system("lsb_release -a"); ?>

<b>Memory Usage (MB):</b> 
<?php system("free -t -m"); ?>

<b>Disk Usage:</b> 
<?php system("df -h | grep /dev/sd"); ?>

<b>Mounted Filesystems:</b>
<?php system("di"); ?>

<b>CPU Information:</b> 
<?php system("cat /proc/cpuinfo | grep \"vendor_id\\|\model name\\|cpu MHz\\|bogomips\""); ?>
</pre>
</td></tr></table></center>

<center><h3>Report bugs <a href="mailto:ussr@(omit).dyndns.org"> here </a></h3></center>

<meta http-equiv="refresh" content="30">
</body>
</html>


```

Love this page. Gives a good look to the server :P

My server:
1ghz P3
512mb ram
2x100mb NIC (thinking of bonding them, if it's worth it)
total of 770gig total hdd space

Makes a great server that runs:
Samba
Webmin
torrentflux-b4rt
ssh
proxy (planned)
Apache2+Mysql5
Jinzora
CUPS

Im planning weekly backups, but im still not sure what to use for this. Any ideas? I think there's Amanda and Baracula?

---

### Post by quietas on 2009-05-15
> **alek66 said:**
> I tried to use your code.... but it didnt worked.... no data is showed... on the status part.

Do i have to make something extra?

Firefly comes with streaming using the webpage?

Is there a way to enter [http://myserver:3689](http://myserver:3689) and have a player to be accesed from the internet??

It's a php system call, you'll need PHP5 isntalled, but I am not sure what else is needed in the way of dependencies.

Firefly is great for LAN based streaming through Itunes. Jinsora or something like that is probably what you want if you wish to stream audio via a internet connection.

If you want to use Firefly and Itunes, look into OpenVPN and set up a VPN connection back to your home network. I do this so I can access my files remotely as well.

---

### Post by quietas on 2009-05-15
> **Serangan said:**
> Love this page. Gives a good look to the server :P

My server:
1ghz P3
512mb ram
2x100mb NIC (thinking of bonding them, if it's worth it)
total of 770gig total hdd space

Makes a great server that runs:
Samba
Webmin
torrentflux-b4rt
ssh
proxy (planned)
Apache2+Mysql5
Jinzora
CUPS

Im planning weekly backups, but im still not sure what to use for this. Any ideas? I think there's Amanda and Baracula?

What do you think of torrentflux-b4rt? I was running the mainstream torrentflux and it was really bothering me with the slowness. It worked though. Currently I've moved my torrents over to Transmission (decent Web UI, great .NET remote client), but I don't like that it does not have the ability to place incomplete and finished downloads in different directories.

---

### Post by Serangan on 2009-05-15
> **quietas said:**
> What do you think of torrentflux-b4rt? I was running the mainstream torrentflux and it was really bothering me with the slowness. It worked though. Currently I've moved my torrents over to Transmission (decent Web UI, great .NET remote client), but I don't like that it does not have the ability to place incomplete and finished downloads in different directories.

I did try the original torrentflux at first. I didn't find it slow, but i can't say i remember much as it was a while ago. Torrentflux-b4rt is quite fast, with many more options.

Also, i use Bit-tornado as the torrent client, no idea why. Transmission is the default client for torrentflux (all variants), but for some reason I decided on Bit-tornado.

When you say slowness, do you mean, downloads, or the webUI?

---

### Post by jasonsjunk on 2009-05-15
My home server sits in my garage and isn't actually headless , I do have the ubuntu-desktop installed on it.  

Specs are P4 3.6 Ghz 1 gig ram 160 gig HD.  

Running Ubuntu 9.04 server edition (with gui)

Software:
Webmin - best free tool I have used for server administration
SSH
ProFtp
Apache2
Drupal - website 1 runs on this
WordPress- website 2 runs on this
Folding @ Home - Go Team Ubuntu!!! Server doesn't have much traffic so I installed this to make me feel better about the wasted electricity.
MythTv FrontEnd- So I can watch TV or stream tunes from the media server when working on things in the garage.

---

### Post by evermooingcow on 2009-05-15
I got a nice 1U system for a home server. A bit loud but rackmount hardware is by default cooler than any pedestal form factor.

Its internal only as I don't really have a need for it when I'm out.

Routing/IP forwarding/firewall via shorewall/iptables
SSH (internal)
Xen
NFS (the extent of my media serving)
deluge
DHCP
BIND

---

### Post by Cheesemill on 2009-05-16
> **quietas said:**
> What do you think of torrentflux-b4rt? I was running the mainstream torrentflux and it was really bothering me with the slowness. It worked though. Currently I've moved my torrents over to Transmission (decent Web UI, great .NET remote client), but I don't like that it does not have the ability to place incomplete and finished downloads in different directories.

The latest versions of Deluge allow you to install different parts of the application on different machines. I used this guide
[http://ubuntuforums.org/showthread.php?t=1114965](http://ubuntuforums.org/showthread.php?t=1114965)
with a couple of changes so I now have the Deluge daemon running on my headless 8.04 server, the WebUI running on my virtual LAMP server, and the Gnome GUI running on my Jaunty desktop and laptop.

This lets me connect to my server via my Jaunty machines if they're close to hand or use the WebUI if I'm on someone else's machine to manage my torrents. This is the best solution I've come across because I only have to fall back to the WebUI when absolutely necessary unlike other headless clients.

Cheesemill

---

### Post by www.pjstemplates.com on 2009-05-16
I also thought I would add in **WinSCP** since I have yet to find a decent web baed file manager with a deb in the repos and does not seem like it is from the 80's.

---

### Post by alek66 on 2009-05-16
I made it work!
I am running
ajax
Transsmision on web interface
Firefly
Cups
phpsysinfo
and ebox

Still trying to understand ebox... and cant upload .torrent using ajax... any ideas?

---

### Post by Serangan on 2009-05-18
> **alek66 said:**
> I made it work!
I am running
ajax
Transsmision on web interface
Firefly
Cups
phpsysinfo
and ebox

Still trying to understand ebox... and cant upload .torrent using ajax... any ideas?

Samba maybe?

Or even a php upload script? [http://php.about.com/od/advancedphp/ss/php_file_upload.htm](http://php.about.com/od/advancedphp/ss/php_file_upload.htm)

I would of though that the transmission WebUI had away of uploading .torrent?

---

### Post by alek66 on 2009-05-18
> **Serangan said:**
> Samba maybe?

Or even a php upload script? [http://php.about.com/od/advancedphp/ss/php_file_upload.htm](http://php.about.com/od/advancedphp/ss/php_file_upload.htm)

I would of though that the transmission WebUI had away of uploading .torrent?

Yes I can use samba and the Transmission WebUI, from inside my LAN. From internet, y only access jinzora anda Ajax.

But usign ajax... which lets me upload any kind of file to my folders.... .torrent...are faded and cant be selected.

Any ideas on why does ajax do that?

thanks

---

### Post by Serangan on 2009-05-22
> **alek66 said:**
> Yes I can use samba and the Transmission WebUI, from inside my LAN. From internet, y only access jinzora anda Ajax.

But usign ajax... which lets me upload any kind of file to my folders.... .torrent...are faded and cant be selected.

Any ideas on why does ajax do that?

thanks

PHP upload script would work, if you allowed it access to the outside, and limited the file size/type.

Ill install ajax on my server and have a look around with it.

---

### Post by alek66 on 2009-05-26
Is there a way using mt-daapd, if i have a mac with itunes to sinc my ipod with songs from firefly, or even so have the possibility to rated them?


thanks

---

### Post by bgammill on 2009-05-30
I just bought two nice decommissioned computers from my employer today for $30 each, you can see the specs in my signature. I really enjoy seeing all of your ideas for things to run on your servers. Keep them coming!

---

### Post by Serangan on 2009-06-01
> **alek66 said:**
> Yes I can use samba and the Transmission WebUI, from inside my LAN. From internet, y only access jinzora anda Ajax.

But usign ajax... which lets me upload any kind of file to my folders.... .torrent...are faded and cant be selected.

Any ideas on why does ajax do that?

thanks

Regarding Ajax, I take it your using this? [http://www.ajaxplorer.info/](http://www.ajaxplorer.info/)

With that, I was able to upload a torrent file with no problems. So i have no idea what would be wrong with your copy.

@alek66

I've used firefly on WHS and I gave up as I couldn't delete/rate music via itunes. So, I have no idea what other program could be used to do this.

*Edit*
Quick Google search and you could use "iTunes Folder Watch". It's not anything like firefly but it could be used to monitor the music folder

*Edit2*
Also, there is Jinzora, but it's a web browser media manager, which can be used to stream music. Could be a different approach.

@@bgammill

I know what it's like. My server is an x-desktop from a company. It's getting old, but it makes a wonderful homeserver

---

### Post by quietas on 2009-06-01
Unfortunately I ran into this as well. Firefly doesn't have a way to sync an ipod/iphone against it. You can't even use the share to make playlists directly in Itunes. The best method I have come up with so far is to share it via samba and point my library at it.

---

### Post by synd7 on 2009-07-01
Just set up my first server yesterday, a file server for the house:

2.4GHz P4
256mb RAM
80gb HDD

Jaunty 9.04 Server - Headless
Apache
Mysql
PHP
SSH
Torrentflux-b4rt
phpmyadmin
Samba
Folding@Home

Going pretty well at the moment but i'm keen to add some fun things to it.
I dont really have any need for jinzora or firefly, my upload speed is pretty slow and  i've got an ipod for music on the go.

Any ideas?

---

### Post by TwiceOver on 2009-07-01
> **TwiceOver said:**
> My home server 
Sempron 1.9ghz/3gb DDR2/1.4tb total space/2u rackmount
Ubuntu 9.04 server LAMP/SSH/Samba

What I run:
DNS - For local name resolution
Samba/NFS shares for my linux desktop/laptop and wife's Windows Laptop
Subsonic - Internet audio streamer to stream my music to wherever I am
Gallery2 - Host images for the web in a nice templated format
Drupal - Intranet page for wife and I to keep track of calendar dates/tasks/etc
phpmp2 - PHP frontend for MPD to play music out of the server box to an FM transmitter to listen to music on any radio and change songs via a web browser.
ProFTPD - FTP access
VMWare Server - Hosts an XP session that has Tivo Desktop and streaming for the xbox360, also runs Microsoft Money.
BackupPC - Backs up various PCs around the house
HellaNZB - To download "articles" from newsgroups using the Zussa web frontend
PHPSysInfo - Basic Sysinfo listing
Webmin - Web administration



Figured I would update my listing since the post is back toward the top...

---

### Post by rbishop on 2009-07-01
Glad to see all of these posts about your servers....  Giving me a number of ideas to work with and update my own server.

I'm currently running:


[LIST]
[*]VMWare Server 2 - Learning VM stuff (Got 2 VM's running now looking for more)
[*]Webmin - Best app for a linux noob
[*]Nagios - Monitoring some remote sites
[*]NagiosQL - Configuring Nagios
[*]Torrent Flux
[*]2x Net Camera's image repositories
[*]Apache
[*]PHP
[/LIST]
On a 2x Dual Core AMD Opteron 2.0Ghz with 4GB RAM and 2x500GB drives

---

### Post by tgalati4 on 2009-07-01
[http://getontracks.org](http://getontracks.org)

---

### Post by alek66 on 2009-07-25
Any suggestion for a replacemente for jinzora?

---

### Post by bartos on 2009-07-25
> Any suggestion for a replacemente for jinzora? 

Ampache - in Ubuntu repositories
Subsonic -Pretty Good
Kplaylist - Simple

Google streaming media player- there are more

software i also use on my server

eyeOS - Opensource cloud computing.

---

### Post by Serangan on 2009-07-26
[http://www.subsonicproject.com/Download](http://www.subsonicproject.com/Download)
or
[http://ampache.org/](http://ampache.org/)


Haven't tried either yet.

---

### Post by alek66 on 2009-07-26
> **bartos said:**
> Ampache - in Ubuntu repositories
Subsonic -Pretty Good
Kplaylist - Simple

Google streaming media player- there are more

software i also use on my server

eyeOS - Opensource cloud computing.

Im stuck on the AMPACHE demo page, and i cant get it to play the songs, i added the song to a playlist i hit play.... and nothing happens (im running safari)

---

### Post by bartos on 2009-07-26
> Im stuck on the AMPACHE demo page, and i cant get it to play the songs, i added the song to a playlist i hit play.... and nothing happens (im running safari) 

The Ampache demo website is just to demostrate what Ampache looks like and the see features.Install it to your server to stream your own music.

---

### Post by midwesterndirt on 2009-07-29
firefly (mt-daapd) is pretty cool. There is a flash player called [FirePlay]("http://www.mellberg.org/FirePlay.zip") which works well with it and lets you listen to streaming audio when you don't have an available DAAP client.

I run VirtualBox in headless mode with several separate Ubuntu server VMs to make process management, backup and disaster recovery easier. I back-up each VM whole instead of backing up individual configuration directories for each server program. Just a few weeks ago, my main server wouldn't start when I rebooted it after a kernel upgrade. I managed to recover with a live CD, but I didn't have to rebuild everything because I had my various server programs consolidated in their own VMs. I have the following setup going:

-Main hardware server runs VirtualBox in headless mode, NFS for sharing my home directory across all linux servers (this makes moving quickly between them much easier than using SCP). Uses rsync and a separate hard drive to back up all its VMs twice a month.
-Apache web server with web portal, Nagios monitoring server, DokuWiki documentation software, MySQL, PHP
-File backup server (which automatically backs up several computers with rsync and crontab) with AutoIndex PHP script
-Firefly streaming audio server with automatic synchronization of the Music directory on my desktop.
-Dummy server for testing and playing with various programs like Webmin, Bind and NTOP
-Windows XP pro for whenever I need it (which is extremely rare since I ditched iTunes for Rhythmbox when they finally got iPod art syncing working)

I'm trying to find more cool server software to play with all the time.

I also highly recommend getting a WRT54GL with Tomato firmware (or some other firmware I guess, but Tomato has been solid as a rock for me).

---

### Post by DaveAK on 2009-07-30
> **midwesterndirt said:**
> firefly (mt-daapd) is pretty cool. There is a flash player called [FirePlay]("http://www.mellberg.org/FirePlay.zip") which works well with it and lets you listen to streaming audio when you don't have an available DAAP client.

I run VirtualBox in headless mode with several separate Ubuntu server VMs to make process management, backup and disaster recovery easier. I back-up each VM whole instead of backing up individual configuration directories for each server program. Just a few weeks ago, my main server wouldn't start when I rebooted it after a kernel upgrade. I managed to recover with a live CD, but I didn't have to rebuild everything because I had my various server programs consolidated in their own VMs. I have the following setup going:

-Main hardware server runs VirtualBox in headless mode, NFS for sharing my home directory across all linux servers (this makes moving quickly between them much easier than using SCP). Uses rsync and a separate hard drive to back up all its VMs twice a month.
-Apache web server with web portal, Nagios monitoring server, DokuWiki documentation software, MySQL, PHP
-File backup server (which automatically backs up several computers with rsync and crontab) with AutoIndex PHP script
-Firefly streaming audio server with automatic synchronization of the Music directory on my desktop.
-Dummy server for testing and playing with various programs like Webmin, Bind and NTOP
-Windows XP pro for whenever I need it (which is extremely rare since I ditched iTunes for Rhythmbox when they finally got iPod art syncing working)

I'm trying to find more cool server software to play with all the time.

I also highly recommend getting a WRT54GL with Tomato firmware (or some other firmware I guess, but Tomato has been solid as a rock for me).
This is what I plan to do.  What hardware are you running and how many servers?

I've just set up an Ubuntu mail server under a VM on my Mac OS X machine and I'm getting ready to set it up on its own hardware.  I then got the idea that I'd probably want to mess around with some other stuff, and thought a VM setup would be the way to go.  Any suggestions or tips for the configuration?

---

### Post by midwesterndirt on 2009-08-03
> **DaveAK said:**
> This is what I plan to do.  What hardware are you running and how many servers?

I've just set up an Ubuntu mail server under a VM on my Mac OS X machine and I'm getting ready to set it up on its own hardware.  I then got the idea that I'd probably want to mess around with some other stuff, and thought a VM setup would be the way to go.  Any suggestions or tips for the configuration?

All these VMs are running on one severely underutilized Core2 Duo desktop with 4GB or RAM. Here, RAM is more important that processor speed.

One suggestion I have (if you are planning on building a VM server) is to put your VMs on their own partition, and then network mount that partition on a separate system so you can modify them using the VirtualBox GUI. VirtualBox is much faster and stable than VMware in my opinion, but its lack of a GUI when running in server mode is a slight obstacle. Once you get everything up and running the way you want it, theres no real need to modify it anymore. Although if you are running these VMs on your primary workstation, then I guess that's all unnecessary since you should have the GUI right there.

Also, if you know shell scripting, writing scripts to handle backups, as well as VM auto-startup scripts make things easier as well.

---

### Post by alek66 on 2009-08-05
webmin is no longer supported? what do you recommend to use instead?

I been trying to un install jinzora; using the unistall scrip provided::: and i get no response from it.

---

### Post by mande01 on 2009-08-28
This is the business.
I know I'm going to spend days reading and researching this stuff.

My system:
IBM thinkpad T30
w/ PCMCIA USB 2.0
w/ 2 TB external hard drive
FreeNAS

Can't wait to change to Ubuntu, but will miss the GUI it's beautiful.
Is is possible for me (I lie only started using Linux about 3 weeks ago) to port the GUI from freeNAS?
The layout is perfect, all it needs is the Home server stuff, ie simple content management, calendar, etc.
i am new to linux so i may find my self going back.

Thanks,
Der

P.S. That system is usually running at 400 Mhz it has a 1.6 Ghz. Pretty cool (!).

---

### Post by quietas on 2009-08-29
@mande01

You may be able to move the GUI from FreeNAS, though it would take some work and I have never seen a post here where someone has tried. FreeNAS runs a stripped version of FreeBSD so everything would need to be recompiled from scratch.

Take a look at Ebox, it's fairly decent as a web front end to most things needed on a home server.

---

### Post by epsolon77 on 2009-10-16
> **midwesterndirt said:**
> 

I run VirtualBox in headless mode with several separate Ubuntu server VMs to make process management, backup and disaster recovery easier. I back-up each VM whole instead of backing up individual configuration directories for each server program. Just a few weeks ago, my main server wouldn't start when I rebooted it after a kernel upgrade. I managed to recover with a live CD, but I didn't have to rebuild everything because I had my various server programs consolidated in their own VMs. I have the following setup going:

-Main hardware server runs VirtualBox in headless mode, NFS for sharing my home directory across all linux servers (this makes moving quickly between them much easier than using SCP). Uses rsync and a separate hard drive to back up all its VMs twice a month.
-Apache web server with web portal, Nagios monitoring server, DokuWiki documentation software, MySQL, PHP
-File backup server (which automatically backs up several computers with rsync and crontab) with AutoIndex PHP script
-Firefly streaming audio server with automatic synchronization of the Music directory on my desktop.
-Dummy server for testing and playing with various programs like Webmin, Bind and NTOP
-Windows XP pro for whenever I need it (which is extremely rare since I ditched iTunes for Rhythmbox when they finally got iPod art syncing working)

I'm trying to find more cool server software to play with all the time.

I am using my home server to test a config for work.

I'm setting up LTSP to boot to thin clients, and running virtualbox in headless mode to run desktops.  The whole system will intergrate with AD and upon logon each user would be automatcially pushed in to their desktop instance.

---

### Post by samosamo on 2009-10-17
> **midwesterndirt said:**
> firefly (mt-daapd) is pretty cool. There is a flash player called [FirePlay]("http://www.mellberg.org/FirePlay.zip") which works well with it and lets you listen to streaming audio when you don't have an available DAAP client.

I run VirtualBox in headless mode with several separate Ubuntu server VMs to make process management, backup and disaster recovery easier. I back-up each VM whole instead of backing up individual configuration directories for each server program. Just a few weeks ago, my main server wouldn't start when I rebooted it after a kernel upgrade. I managed to recover with a live CD, but I didn't have to rebuild everything because I had my various server programs consolidated in their own VMs. I have the following setup going:

-Main hardware server runs VirtualBox in headless mode, NFS for sharing my home directory across all linux servers (this makes moving quickly between them much easier than using SCP). Uses rsync and a separate hard drive to back up all its VMs twice a month.
-Apache web server with web portal, Nagios monitoring server, DokuWiki documentation software, MySQL, PHP
-File backup server (which automatically backs up several computers with rsync and crontab) with AutoIndex PHP script
-Firefly streaming audio server with automatic synchronization of the Music directory on my desktop.
-Dummy server for testing and playing with various programs like Webmin, Bind and NTOP
-Windows XP pro for whenever I need it (which is extremely rare since I ditched iTunes for Rhythmbox when they finally got iPod art syncing working)

I'm trying to find more cool server software to play with all the time.

I also highly recommend getting a WRT54GL with Tomato firmware (or some other firmware I guess, but Tomato has been solid as a rock for me).

I do the same thing as this guy except I chose VMWare Server 2.0.  The physical machine runs VMWare and NFS server, and also has "ubuntu-vm-builder" installed for building/deploying the VMs and "vmbackup" for backing them up.  Nothing else.  All the ~20 or so network services on my LAN (virtual hosting server, VPN, proxy, directory server, file server, monitoring, etc etc) are all hosted by about 10 virtual machines running on this box.  To manage all of these machines I use Webmin to distribute configurations to each server, NFS for a central datastore, and LDAP/Kerberos for single sign on authentication.

---

### Post by virtuoosi on 2009-10-17
My home server is located in my walk-in closet. It used to be a HP Pavilion t3000, but it has had some components replaced and the case modded. 

I bought <10dB Noctua coolers and an passively cooled GPU because it was going to serve as an headless server. It's almost too quiet now. I've had the server for about one and a half month now. 

Services run on the server:

[LIST]
[*]2 irssi IRC -clients on separate screens for me and my brother
[*]Apache2
[*]PHP5
[*]MySQL
[*]rsyncd for backups
[*]rTorrent
[*]Samba
[*]CUPS
[*]Ventrilo server
[*]Webmin (I barely use it...)
[/LIST]
And here are the specs:

[LIST]
[*]AMD Athlon 64 3200+ 2,0 GHz
[*]1536 MB PC3200 MB/sec 184 pin, DDR SDRAM
[*]200 GB SATA 7200RPM Seagate
[*] Club 3D 7200GS Silent
[/LIST]
I am going to replace the Seagate HDD with a quiet 1TB HDD.

I am very happy with my hardware setup; I made some mods to the case to improve the cooling with the Noctua coolers and it works like a charm! CPU temperatures hang around 25 - 30 degrees celsius.

---

### Post by fooluser on 2009-10-20
hi, every one!
glad to meet you!

---

### Post by PANNY on 2009-10-25
Here is my home server/workstation/computer-good-for-all

Intel Pentium 4 DualCore CPU 3.00GHz overcloked at 3.9GHz
1 GB of RAM
nVidia GeForce 6600
2 Western Digital HDD: 80GB & 250GB (yeah, I know, out of time)

Ubuntu 9.04
Apache2 with mod_userdir, PHP5, MySQL+phpMyAdmin, squid (+calamaris)
Oracle Database 10g Express Edition (for school) - a pain to install and configure
Webmin & Usermin
SSH, telnet (local only), FTP(ftps, ssh internal ftp server)
Samba
CUPS with 2 multifunction printers
*Transmission BitTorrent with WebUI (temporary solution, having problems with Deluge)* **Problems solved, back to Deluge.** :)
vnstat, phpsysinfo, cacti
... and in search for other ideas :)

---

### Post by jamesrfla on 2009-10-25
If you are looking for a BitTorrent client that can be controlled via the web browser I recommend clutch. It works great. There is also TorrentFlux if you don't like clutch.

---

### Post by PANNY on 2009-10-26
Clutch is already built into Transmission :) I've used TorrentFlux, but it's just that I'm used to Deluge.

---

### Post by buchan on 2009-10-26
I've got a server in the basement...not much but it does the job nicely
Its an AMD Athlon(tm) 64 Processor 3000+ with a Gig of ram
2x40GB disks in a RAID 1 for the OS
4 1TB drives in a RAID5 (software)

Running samba for filesharing, SubSonic for tunes and Sabnzbd for downloading all on 9.04 for now.  

I've also written a script that monitors the system, it checks HD space & temp, the RAID status and the system load.  I created a cron to run every 10 minutes and send me an email using ssmtp if something goes wrong.  I use a slightly modified version of the script at work to watch remote servers running rsnapshot backups as well.

---

### Post by roundhay on 2009-11-07
I have recently rebuilt my server after my old xeon system died...R.I.P.

Intel(R) Celeron(R) CPU E1500 @ 2.20GHz
2GB RAM
80GB System Drive
160GB, 250GB & 1TB storage drives

I have installed
LAMP
CUPS
Gallery2
phpmyadmin
phpsysinfo
torrentflux
backupPC - Not figured this out yet but looks like useful backup software with web GUI

I also want to install a media server that I can access over the web outside of my LAN. I had ampache installed on my old system but I want to know if there is anything better.

I have heard of Subsonic, Jinzora, mediatomb and others any suggestions on which one might be the best one to go for?

---

### Post by hankinator on 2009-11-07
Quad core Xeon 3.2 ghz
3 Gigs of ram
Ubuntu 8.10 server 32-bit

apache2, SSH, mysql, torrentflux, vmware server, 500 gig HDD (there are 2 HD's in raid), vsftpd, and samba.

---

### Post by quietas on 2009-11-07
I liked subsonic last I tried one.

---

### Post by The Real Dave on 2009-11-09
I've 3 servers running at the moment, though only 2 are 24/7 servers.

Main Server (24/7)
Hostname - An-Lar
OS - FreeNAS 0.69.2
CPU - 1.7Ghz PIV
RAM - 512Mb DDR
HDDs - 2^320Gb Samsung Spinpoint F1 Software RAID0
Services - SSH, NFS, Samba, Web Server, Rsync, Unison

Backup Server 
Hostname - Knox 
OS - FreeNAS 0.69.2
CPU - 2Ghz PIV
RAM - 384Mb DDR
HDDs - 3^320 Samsung Spinpoint F1 Software RAID1
Services - SSH, NFS, Samba, Rsync, Unison

Torrent Server (24/7)
Hostname - Karmic
OS - Ubuntu Server 9.10 Karmic Koala
CPU - 451Mhz PIII Katami
RAM - 128Mb PC-100 SD-RAM
HDDs - 1^6Gb IDE, 1^9Gb IDE, 2^2Gb Flash (Going to be in Software RAID0 if I can)
Services - SSH, Samba, rTorrent

The torrent server automatically loads whatever torrents are placed in a certain directory and seeds them until it reaches a certain upload amount :) Means my sister doesn't have to mess around with bittorent, just drop a file onto the server and wait till it finishes :)

---

### Post by karmakowski on 2009-11-10
Some old iPaq with FreeBSD 7.2, I use it for:
-- file storage (sftp with sshfs on the clients' side and samba for windows machines and to store logs from my router);
-- torrenting (rTorrent, nothing better :)
-- local DNS server (BIND, local tld added for convenience);
-- nntp/news server (Leafnode);
-- RSS attachments downloading (castget, for all my podcasts);
-- www (AMP);
-- downloading backups and other files from multiple servers I need to keep alive (lftp, the ultimate ftp client) 
-- sshd, obviously, access and administration;

-- Freenet proxy/gateway (under its own domain and proper port, not using it anymore though, nothing interesting there);
-- xmpp server (local jabber conferences, also defunct);
-- mail server (postfix, another inactive service);
-- VPN server (openvpn inside ssh tunnel as I don't have a public IP, not used anymore, ssh turned out to be enough).

---

### Post by beniwtv on 2009-11-10
Well, there are two (!) "servers" now at my place with Ubuntu.

Router: This one is a 7W power only box, so it stays on 24/7. This one acts as a router. Services:

  - IPTables: For controlling net access for the wired and wireless networks.
  - DCHP with Dynamic DNS: Will add a DNS entry for each DHCP request.
  - DNS: Caching name server pointed to OpenDNS with some settings there to block malicious pages. Also hosts the (internal) DNS.
   - Transmission: Downloads Linux CD's for me even when I'm not at home :lolflag:
   - Squid and dansguardian as transparent proxy (port 80 is automatically redirected to Squid's port) for caching web pages and stuff (though I wouldn't dare caching https).
   - OpenSSH for administration
   - OpenVPN to authenticate WiFi sessions and for external access to the network
   - CUPS for the printer (it automatically gets detected by other Linuxes in the house, how awesome is that?)
   - XSANE for network scanning
   - Apache with a nice start page and links

   Plans: Asterisk for the SIP VoIP adaptor to add some nifty features to the telephony system.


Media Center: This one is a good machine: Phenom X4, 8GB RAM, 2x500GB HDD's, space for more. Services:

    - Moovida as a media center application
    - KVM for virtual machines
    - Backup server for all other machines on the network
    - Lirc for the remote control unit
    - OpenSSH for administration, of course
    - Mediatomb for streaming
    - Apache with mod_userdir so everyone can try out some scripts there
    - FreeNX for remote desktop access (I like the power of it when it comes to convert videos...)

   Plans: This one needs a complete rebuild when the next LTS is here, some things are missing and/or hacks put together. Want to get the LCD on the case working,  _without_ compiling much stuff... Also has leftovers from older things I used to do there (ftp, cups...) I want to get rid of.

Cheers,

---

### Post by kpholmes on 2009-11-17
> **beniwtv said:**
> 
   - Transmission: Downloads Linux CD's for me even when I'm not at home :lolflag:
  

do you mean that your add the torrent file your self and just let it be, or that transmissions subscribes to some linux-torrent-rss feed or something and will download the torrent automatically?

---

### Post by beniwtv on 2009-11-17
> **kpholmes said:**
> do you mean that your add the torrent file your self and just let it be, or that transmissions subscribes to some linux-torrent-rss feed or something and will download the torrent automatically?

I add the torrents I want to the web GUI (it even can download the torrents for you if you provide the URL!), and let it download. I also have a bandwidth cap set when I'm at home so it doesn't take all of my bandwidth. When I'm at work, I usually remove the bandwidth cap.

---

### Post by alek66 on 2009-12-19
IS there something like firefly, but for videos.
I want to see them using "front row". usign front row, I can see all the music choosing firefly&#347; server as source.

or can I add the file descriptor to firefly's configuration fly??
In one place it asks for the kind of file I want firefly to search.

thanks

---

### Post by Groodles on 2010-05-18
My box is as follows:

_Hardware:_
Intel Atom 330 (1.6GHz) CPU
2GB RAM (Major overkill - I know!)
2x 1TB Samsung SATA HDD (RAID1)
2x 500GB Hitachi SATA HDD (RAID1)
2x 120GB Hitachi IDE HDD (JBoD)

_Services:_
Proxy (Squid)
FTP Server (ProFTPd)
Media/File Share (Samba)
Web Server (Apache2)
DNS
DHCP
SSH
PPtP & OpenVPN

---

### Post by Zeosa on 2010-05-18
My setup:

Server 1

Hardware:
AMD Athlon X2 245 2.9GHz (65W)
8GB Ram
5x 1TB drives configured in Raid10 (4 active, 1 spare)
1x 500GB drive for OS (overkill, but it's what I had)
Intel PCI express 10/100/1000 dual NIC
Services/Software
SSH
Samba (PDC)
OpenLDAP (central authentication)
NFS (sharing home directories and parts of the raid array)
Netatalk (gotta have something my mac can play with lol)
Postfix
courier IMAPS
squid+dansguardian
dhclient
Bind9 (local DNS for LAN + forwarding)
DHCP (updating Bind for DHCP clients)
BackupPC (backups for all computers in the house)
MySQL
Apache
Virtualbox 3.1 (headless)
Munin

Virtual Machines on Server 1:
#1 
Software/Services
SSH
Apache 
Torrentflux-b4rt
Moblock
NFS Client
LDAP Auth Client
MySQL

#2
Software/Services
SSH
LDAP Client
Mediatomb CVS (serves video/picture/music to uPnP devices on the LAN)
VLC/ffmpeg custom compiled to work optimally with mediatomb
NFS client

#3
Windows XP VM
PlayOn Media Server (Serves cbs.com and Hulu to uPnP devices on LAN) - Haven't found an elegant solution for this under Linux, so I keep this VM running just for this.

#4
OpenSolaris VM - Just to play with ZFS ;)


Server 2
HP Proliant ML150G6
Intel Xeon E5504 - 2.0GHz 4x cores
2GB ECC Ram
Main Drive - 250GB 
Storage 2x1.5TB configured as Raid 1 with backuppc data mirrored from server 1 daily
Software/Services
SSH
NFS Server
NFS Client
LDAP Client
Bind9 (slave to server #1 - backup DNS for LAN)
Apache
Samba - Storage for home security Cams
VirtualBox 3.1

Virtual Machines on Server 2:

#1
Software
OpenVPN
SSH
LDAP Client
NFS Client
FreeRadius (Auth wireless clients)
MySQL

#2
SSH
OpenSSL (CA for self signed certificates for my network)
LDAP Client
NFS Client

#3
Testbed - VM For testing new software/configurations - Can clone a vm disk and attach it to this machine in a few minutes for testing.



I Also have a 2 bay qnap NAS with 2 2tb drives set up as Raid1 as well as a spare drive. I backup important data to this machine daily and swap out one drive every week (allowing the array to rebuild), taking the removed drive to work with me and storing it in my office.

And Yes, I like my VM's it makes testing new software/configs so much easier, allows me to run minimal services on the machines, and makes backing up important stuff a snap (backup snapshots/VM Harddisks/Machines - if something breaks, I can simply shut down the VM, restore the latest snapshot - which takes less than a minute - and power on the machine ...just like nothing ever happened)

---

### Post by nuclear216 on 2010-11-19
I've used homeservers a lot, since a lot of years, there's a lot of them, usually the best thing for home use is a DEDICATED distro, I've tried clarkconnect (which I recommend too), astaro, FreeNAS, selfmade based on suse (back when suse was the ubuntu of the day), redhat, ubuntu, etc- etc-

So far the best one I've found is this one (currently based on fedora but being ported to ubuntu, they need developers to do that so if someone sees this please help them!): Amahi.
[http://www.amahi.org/](http://www.amahi.org/)

Basically it's a set of package that one puts in the distro during ISO install, those package configure the system, install dependancies, start webbased configuration interface, and that's it, one takes away the monitor and the system is ready, all user and services configured (apache! vpn!) and everything's ready. 

Even network config is automatically configured, and in a very clever way because they had the idea to have you tell them on their website your router and desired IP address (ie 192.168.0.1 for the router, 192.168.0.20 for the server, not your IPS given internet address) BEFORE actually installing anything, it generates a code that one insert in the web interface AFTER the system is installed and this takes care of network config. 

This automatic network config is astonishing because it configures (based on the code) the DHCP server, local DNS (already configured to use OpenDNS for internet host resolution, so you reach your LAN computer with DNS resolution and internet address with openDNS without configuring anything), VPN server, SAMBA shares, and registering your dinamic Internet IP with their dyamic DNS service, so total time to have the url username.yourhda.com point to your home network server with all the service up and ready (user being configured too) is the fedora install time +10 minutes, cherry on the cake they have a windows .exe that install a preconfigured vpn client to a windows machine that needs only ip or username.yourhda.com to connect (of course u can use any vpn client, even from a phone and they have flash streaming server compatible with iphone)
Believe me after years of searching I think I've found the best Home server ever, if only it was available to ubuntu too (see their wiki [http://wiki.amahi.org/index.php/Ubuntu](http://wiki.amahi.org/index.php/Ubuntu)) :(

The second great and unique innovation of amahi is that you install apps like jinzora and ampache (the list is incredibly rich and growing, xbox and itunes compatible mediaserver, torrentflux, see link) from within the dashboard "repackaged" specifically for amahi, hasslefree onclick automated install and user and databases are already configured.
Here's the list:
[http://www.amahi.org/apps?category=soho](http://www.amahi.org/apps?category=soho)

The nicest thing I do with it is downloading torrent with torrentflux-b4rt directly to the appropriate folder (video/music, shared on samba too as directory) and once they finished they are automatically available to the xbox or banshee or itunes via the mediaserver or in the webapps like ampache as streaming (flash too) available to the internet and/or (depending on firewall config) to any local network device with just a browser.

another recent (still needs polishing) incredibly useful feature is greyhole, basically once you run out of disk space you just add a USB or internal disk and tell thru the webinterface to add it to the storage pool and it is being transparently added to the available space.


The only drawback of amahi isn't really a drawback as they actually thinked thru network topology due diligence so they didn't designed it as a firewall too, hence it uses only ONE ethernet interface (eth0) so one needs a separate firewall distro for the network (I don't like home router firewall but one could use them too).
My personal solution to that was to use my atom home server with two ethernet as an all in one solution with virtualization.

I've installed Citrix Xen Server (free), put amahi on one VM that sees only one ethernet and a firewall distro (there are many around) on another VM that sees both ethernet.

so one ethernet is connected to the router and the second one to a switch which connects to all machine, xbox and a wireless AP, so amahi servers DHCP to all (firewall is static of course) over wired and wireless and a separated firewall takes care of security, all in one Atom box.

---

### Post by NJC on 2010-12-12
I have a headless IBM Thinkcentre A50-8084 2.8GHz Northwood P4 running Ubuntu Server 10.0.4LTS. It's strictly a file server accessible via SSH/Nautilus over a router. I use rsync to run backups.

---

### Post by sjhupp on 2010-12-12
Headless box with 10.04LTS on for me.
P4 2.8GHz, 4GB ram, GA-4MXSV board, DTV1000T tuner (and PlayTV shortly) with 3x1.5TB samsungs in RAID5 (1 more soon), dual GE on board, and another dual GE card and quad FE.
Aiming to be my main gateway and media box for all devices connected throughout the house.
- Zentyal/ebox 2.0
- HTS TVheadend (to stream tv to XBMC)
- Deluge + flexget
- Virtualbox
- wine 
- Handbrake & WinFF
- k9copy & k3b
- webmin
- SSH & VNC servers
- upnp streamer *tbc*
Flexget rocks. It has a list of RSS feeds, and goes and fetches recent files hourly (or whenever you want), downloads them, and creates a nice directory for them on my media share if required, sorted logically based on file naming conventions etc. 
With Deluge, can use a web gui for it, but have set up clients on windows and ubuntu desktops also. Load a torrent and connects to deluge daemon backend to download on server, just looks like local for desktop user. Sweet!
Media streamer is a pain - I need something to transcode on the fly and present nicely to xbox 360.  Mediatomb won't support 360, ushare no transcoding, fuppes config is killing me to get 
working, ps3mediaserver might be an option (?) and twonky isn't free (?).  
Who can transcode/stream from server to xbox 360? What with??

---

### Post by Hex on 2011-01-07
Hey, folks, here's my home server:

**Kagura**
[LIST]
[*]CPU: Pentium II 333mHz Deschutes
[*]RAM: 160 MB
[*]HDD: 10 GB
[*]OS: Debian Lenny (Ubuntu Server uses more system resources)
[/LIST]

[INDENT]Running:[/INDENT]

[LIST]
[*]Apache2
[*]MySQL
[*]SSH
[*]Munin
[*]PHP Shell
[*]AJAX Chat
[*]A PHP system stats script I kindly borrowed from users on this thread (and modified a bit)
[*]A Perl script for recording IP camera data in mjpeg format. A bash script makes sure recorded files are 15 minutes long and deletes the oldest file. (main purpose of the server)
[/LIST]

Check [her]("http://kagura.no-ip.org/") out! I'm also looking for an mjpeg web player, anyone heard of one?

---

### Post by The Real Dave on 2011-01-08
> **Hex said:**
> Hey, folks, here's my home server:

**Kagura**
[LIST]
[*]CPU: Pentium II 333mHz Deschutes
[*]RAM: 160 MB
[*]HDD: 10 GB
[*]OS: Debian Lenny (Ubuntu Server uses more system resources)
[/LIST]

[INDENT]Running:[/INDENT]

[LIST]
[*]Apache2
[*]MySQL
[*]SSH
[*]Munin
[*]PHP Shell
[*]AJAX Chat
[*]A PHP system stats script I kindly borrowed from users on this thread (and modified a bit)
[*]A Perl script for recording IP camera data in mjpeg format. A bash script makes sure recorded files are 15 minutes long and deletes the oldest file. (main purpose of the server)
[/LIST]

Check [her]("http://kagura.no-ip.org/") out! I'm also looking for an mjpeg web player, anyone heard of one?

Would you mind sharing that PHP script? I'm currently just monitoring my servers through hacked bash scripts that output to the web directory >.<

I've two headless servers, more info and pictures of which can be found [here]("http://linuxexpresso.wordpress.com/hardware/").

[[img]http://linuxexpresso.files.wordpress.com/2009/11/an-lar_08-jan-2011_1.jpg?w=150&h=112[/img]]("http://linuxexpresso.wordpress.com/hardware/#An-Lar") [[img]http://linuxexpresso.files.wordpress.com/2010/10/ubuntu_vnc_encoding_server-17-oct-201.png?w=150&h=100[/img]]("http://linuxexpresso.wordpress.com/hardware/#Encode")

An-Lar > Main Server

    1.7GHz Pentium IV &#8211; 256KB L2
    384MB PC-2700
    8.4GB Seagate Series 5 5400RPM &#8211; IDE OS drive
    500Gb Seagate 7200.12 (7200RPM, 16MB Cache, SATAII)
    1TB Western Digital Caviar (7200RPM, 64MB Cache, SATAII)
    VIA 4 port SATA RAID PCI card
    Ubuntu 9.10 Karmic Server

    Samba
    Squid Proxy and Squint
    LAMP
    NFS
    rTorrent
    Apt-Cacher-NG
    mt-daapd
    Daily rsync backups

Encode > Torrent and Media Server

    2.6GHzIntel Celeron (Socket 478, 128KB L2)
    256MB DDR (333Mhz)
    100GB RAID0 Array
    Ubuntu 10.04 Lucid Lynx Server (i386)

    Transmission GTk (Via WebUI)
    Folding@Home (Origami)
    Handbrake GTk
    DeVeDe
    UShare

---

### Post by CharlesA on 2011-01-08
The original script was in [post 13]("http://ubuntuforums.org/showpost.php?p=6770587&postcount=13").

My machine is sitting in the corner and acting as:

Samba
SSH
VM Host
Apache2

---

### Post by Hex on 2011-01-08
@CharlesA, yes, the that's the original script, thanks for linking. Where are the hardware specs of your server?

@The Real Dave, I can still send you my modified script, if you so wish.

---

### Post by CharlesA on 2011-01-08
> **Hex said:**
> @CharlesA, yes, the that's the original script, thanks for linking. Where are the hardware specs of your server?

It's not really all that powerful, but considering what it's doing, I think it's doing a pretty good job. :)

2.93Ghz Pentium Dual-Core E6500
6GB DDR2 800 RAM
500GB OS Drive
4TB RAID-5 Array (data drive)

You can find a picture of it [here]("http://art.ubuntuforums.org/showpost.php?p=9320820&postcount=404").

I've rebuilt it recently (upgraded the OS drive), but for now it's still running Samba, SSH, Apache, VirtualBox, backup slave.

---

### Post by The Real Dave on 2011-01-09
> **CharlesA said:**
> It's not really all that powerful, but considering what it's doing, I think it's doing a pretty good job. :)

2.93Ghz Pentium Dual-Core E6500
6GB DDR2 800 RAM
500GB OS Drive
4TB RAID-5 Array (data drive)

You can find a picture of it [here]("http://art.ubuntuforums.org/showpost.php?p=9320820&postcount=404").

I've rebuilt it recently (upgraded the OS drive), but for now it's still running Samba, SSH, Apache, VirtualBox, backup slave.

Thats a nice looking server :) I wonder, how much of that 320GB OS drive are you using? You often see people with massive OS drives, and I often wonder if it's not a waste :( Of course, it's probably just what you had lying around at the time :)

> **Hex said:**
> @CharlesA, yes, the that's the original script, thanks for linking. Where are the hardware specs of your server?

@The Real Dave, I can still send you my modified script, if you so wish.

No, that one should do perfectly :) Cheers

---

### Post by CharlesA on 2011-01-09
> **The Real Dave said:**
> Thats a nice looking server :) I wonder, how much of that 320GB OS drive are you using? You often see people with massive OS drives, and I often wonder if it's not a waste :( Of course, it's probably just what you had lying around at the time :)


Yeah, it was one I had sitting around. I think I used around 75 or 100GB on it, but that was mostly due to running VMs with snapshots on the machine.

Currently using about 20% of the 500GB one now.

Even my desktop PCs have tiny drives in them, ones got a 320GB OS drive with 500GB data drive and the other has 2 x 250GB drives. Everything is backed up to the server, so what's the point of having a gigantic data drive?

---

### Post by kg4cna on 2011-01-11
Just rebuilt my server. I use it to serve up a website I maintain for my local high school alumni. Old server was a six yr old Red Hat 9 machine and served me well during it's life. This will be my first Ubuntu server machine. I use Ubuntu 10.04.1 LTS on my laptop and 8.04 LTS on the main desktop.

Server Info:
MSI mainboard/AMD 1.4ghz proc (mobo/proc donated from used machine)
512mb RAM
20gb Western Digital HDD

Ubuntu 10.04.1 LTS server-headless
LAMP server using:
Apache2 / PHP / MySQL
Postfix + Dovecot + Squirrelmail
SSH w/SFTP
Webmin (local LAN use only)

Box serves up a website for my local high school alumni. Use email server to send/receive for me ONLY, for website member updates, etc. POP server is accessible from the local LAN only. Squirrelmail covers email access from the outside, again for me only.  I also added the fine PHPBB3 software forum for the users to enjoy. The old server had an earlier version of the same forum.

I ssh in to maintain as necessary from local LAN or outside. I upload website content using SFTP, mostly from the local LAN only.

I'm sure to find other uses for it in time.

A~

---

### Post by donniezazen on 2011-04-12
What do you guys use for Video on demand server?

---

### Post by SquALeD on 2011-04-13
Hmm, 

Core2Duo sitting in my workshop, about 2 gig ram with 2 1TB storage drives, a 250G torrent/usenet drive and a 250G OS drive.

A file server, media server, CCTV, FTP and torrent box

10.04 server, headless..

Runs:

Zoneminder - CCTV client, 2 cams at present and can view live stream via iPhone

VsFTPd - FTP client

Samba - shares to various windows, linux and macs round the house

Transmission - Torrents

Is set up for webserving but nothing on it yet.

WDTVLive boxes handle the audio/video round the house

Airvideo via an iMac to stream movies to iPhone over 3G.

Fancy adding more stuff tho...

---

### Post by expatCM on 2011-04-13
hmmmm  and you saved your set up as an iso and uploaded it some place?

---

### Post by SquALeD on 2011-04-13
?? me?

Are you saying I have saved it or asking if i do?? ;)

---

### Post by expatCM on 2011-04-13
yes ... you :)   

Asking if you did upload it since it sounds like such a nice setup with many common elements that such a lot of people would find to be useful :)

---

### Post by rubylaser on 2011-08-31
You could use any of Linux's free solutions like rsync, rsnapshot, Amanda, Bacula, etc.  Or, you could use [Crashplan's]("http://www.crashplan.com/consumer/crashplan.html") free plan to setup your machines to backup important data.  I'd never spend money on such a simple task.

---

### Post by The Real Dave on 2011-08-31
I'd agree totally with rubylaser. Spending money on a backup client is a waste. 

Read the rsync man pages, get familiar with it's options and facilities, and you'll find that it'll do all you'll need and far more thereafter.

```
man rsync
```

---

