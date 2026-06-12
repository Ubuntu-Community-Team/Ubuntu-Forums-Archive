---
title: "What programs do you run on your personal home server?"
date: 2006-11-21
forum: The Cafe
---

### Post by themikeflynn on 2006-11-21
Recently I setup an Ubuntu home server to backup files, and sort of just as an experiment. Right now it's only useful for using webapps since I haven't sorted out Samba, but I was wondering what else would be cool to have on there. All I have now is TorrentFlux, MediaWiki, phpMyAdmin, and SWAT. 

I'd like to make use of more things on here. It's only for personal use so it can handle the load. What kind of things do you guys use on your server? :D

---

### Post by Sam on 2006-11-21
mldonkey
torrentflux
courier, postfix & co.
apache, mysql
nfs
sshd

---

### Post by darkhatter on 2006-11-21
firewall/router

---

### Post by scrooge_74 on 2006-11-21
Firewall/router
SAMBA
CUPS
Backup
SSH

Try to make it into a fax server, but the darn modem was to hard to setup so I gave up on that

---

### Post by adamkane on 2006-11-21
NFS.

I use a $200 appliance for my router/firewall. Set it and forget it.

---

### Post by Sam on 2006-11-21
If you use/want VoIP telephony, you can also install asterisk.

---

### Post by adamkane on 2006-11-21
Nice!

---

### Post by scrooge_74 on 2006-11-21
> **Sam said:**
> If you use/want VoIP telephony, you can also install asterisk.


I am curious about asterisk, but I am not sure if I understand it well.  Does your server becomes like a telephone central of sorts?  Do I make calls into it from VoIp device when outside the country (for example) and it dials local numbers for me?

---

### Post by Sam on 2006-11-21
> **scrooge_74 said:**
> I am curious about asterisk, but I am not sure if I understand it well.  Does your server becomes like a telephone central of sorts?  Do I make calls into it from VoIp device when outside the country (for example) and it dials local numbers for me?

I don't have it myself. I'm planning to have it soon, but for now I have not a lot of info about it. Have a look on their [website](http://www.asterisk.org/), maybe you'll find what you need.

I have a friend who has asterisk on its server, and he knows it well. If you need more info ask me and I'll contact him tomorrow (it's 3:30 AM here).

---

### Post by scrooge_74 on 2006-11-21
> **Sam said:**
> I don't have it myself. I'm planning to have it soon, but for now I have not a lot of info about it. Have a look on their [website](http://www.asterisk.org/), maybe you'll find what you need.

I have a friend who has asterisk on its server, and he knows it well. If you need more info ask me and I'll contact him tomorrow (it's 3:30 AM here).

It sounds like something one should know about, but I can't make heads from tails of the info in the website.

If you manage to talk to your friend let me know a practical example of its use. Who knows maybe is something I can use at work one day.

Cheers!

---

### Post by adamkane on 2006-11-22
Asterix can be run from a live CD.

---

### Post by Falconix on 2006-11-23
Apache, PHP, mySQL, FreeNX, Samba, X-chat, Gaim

---

### Post by basketcase on 2006-11-24
when I had my server up and running, it was basically a LAMP server for local testing for php/mysql websites I had developed at the time.  It was also a place for testing beta forum software and had a gallery setup to store photos for friends.  

Haven't had a server up in a while, might need to put one up.

---

### Post by burek on 2006-11-24
> **themikeflynn said:**
> Recently I setup an Ubuntu home server to backup files, and sort of just as an experiment. Right now it's only useful for using webapps since I haven't sorted out Samba, but I was wondering what else would be cool to have on there. All I have now is TorrentFlux, MediaWiki, phpMyAdmin, and SWAT. 

I'd like to make use of more things on here. It's only for personal use so it can handle the load. What kind of things do you guys use on your server? :D


for your samba prb ; last post is explained howyo

---

### Post by beercz on 2006-11-24
Samba (for backing up our one windows machine)
SSH
Web/Apache
ftp/Proftp
rsync/[rsnapshot]("http://rsnapshot.org/") (for backing up our linux clients)

Server runs on Debian Sarge - brilliant server software :-)

---

### Post by dca on 2006-11-24
You could also try [FreeNAS]("http://www.freenas.org") if the next server ends up being a place to b/u files..  It's a light-weight BSD-based dealie...

---

### Post by Aualin on 2006-12-03
mysql, apache (2.2), php5 (5.2.0), php6, wildfire, proftpd, samba, nfs, (dont ask why i use both). Running a personal little site on my network, mostly for testing, php, css, html and javascript. And then i run 4 forums on my personal network: phpBB2, phpBB2 modded into near destruction, phpBB3 and punBB.

---

### Post by Johnsie on 2006-12-03
I'm running

Xampp(Apache,php,perl,mysql,proftd)
Postfix
Samba
An IRC server... possible ngircd but I cant remember
a Jabber server (which i never use)
And a chat server for the game HoverRace which I wish someone would port to Linux :-)

---

### Post by ragnar_123 on 2006-12-03
apache, php, mysql, ssh, samba, torrentflux, Web.GET (a wget web app) and i was going to set up team speak, but haven't had any time, yet.

I mostly use it for testing my php scripts.

---

### Post by atoponce on 2006-12-03
Apache
MySQL
PHP
Irssi
Srceen
OpenSSH
print server

Used to run:
GnuMP3d
Bitlbee

---

### Post by RandomJoe on 2006-12-03
Firewall/router on a separate older machine.

The server is primarily for NFS shares, I have all my CDs and DVDs ripped to it (1TB RAID5) and stream them to all the other computers in the house, including the "projector PC" in the living room.

Since it's otherwise idle, over time I've added:
TikiWiki - random thoughts I dump from time to time!

rsync - backup all the other computers to the unused space on the RAID

MEncoder - found it easier to rip the DVDs on the projector PC then just ship all the VOBs to the server, set up a script, and let it churn for hours/days making my smaller files.  (I target 2GB/movie.)  This way the projector PC can get back to _playing_ movies.

ZoneMinder - I have three network cameras, peeking out various windows of the house.  Need to eventually get some that can see at night... :rolleyes: 

Tried an IMAP server, wanted to basically have my own "webmail" that would suck down mail from my various accounts.  Haven't gotten there yet...

OpenVPN - I can fire up my laptop anywhere else, and get a reasonably secure Inet connection by proxying everything back through a VPN to the house.  As well as access to my home stuff.

---

### Post by Jose Catre-Vandis on 2006-12-03
Similar to random joe. but without the luxury of cameras!

Apache, Mysql, PHP, gnump3d, NFS (which is accessed from Windows machines too!), D4X (downloads while I and the rest of the house PC's sleep), Mencoder (encodes while I sleep), VLC (for broadcast streaming),gFTP, and its an Edubuntu server which also provides LTSP, so that house PC's can network boot Edubuntu for central file storage, SSH and VNC for remote access to it.

---

### Post by luca.b on 2006-12-04
I have a small home built router/firewall that runs several things. Among them samba+LDAP as a domain controller, amule-server, ssh, ftp, a DHCP server and DNS cache (thanks to the great program dnsmasq),cups and other things I forgot.

---

### Post by feest on 2006-12-04
LAMPP (Linux+Apache+Mysql+Php+Perl)

---

### Post by magicfab on 2007-01-29
apt-cacher

---

