---
title: "Starting over - home server help"
date: 2019-02-07
forum: Server Platforms
---

### Post by aljames2 on 2019-02-07
New to Ubuntu but learning...I could use some guidance from a planning standpoint.  I’ve done a lot of Googl’ing & probably worse, Youtubing!  Now I’m turning to more reliable sources which is where I should have started: Ubuntu forums, Ubuntu server guide, and a few books that I’m studying.

My goals:
-Home storage network with Ubuntu Server as OS.
-Music file serving for local and remote access.
-Photo serving (I don’t like iCloud)
-Ability to access storage files from anywhere, like a Dropbox cloud account works.
-Eventually, host a Drupal website that I currently run using a paid VPS provider (this goal is not a must have at first).
-RAID1 mirroring (have 2 brand new WD Red HDDs never partitioned or used yet).
-Ubuntu Server 18.04.1(or 2) running on it’s own 250Gb SSD
-Remote access for configuration after install.
-Securing everything.
-Regular Backups to USB drives for offsite storage.

Currently all devices that would be accessing the server are Windows based and IOS mobile devices.  I don’t want to use Windows Server.

Hardware is built and ready to go:
Gigabyte MD with onboard Realtek ethernet, i3-4330 CPU, 8 Gb ram stick, no video or sound cards, no monitor or keyboard after install.

I’ve read a lot about these topics but unclear of the best approach to implement my goals:
-Partitioning portions of the OS (seems to be more relevant when storage is on the same drive as the OS)
-Local remote access (SSH, Webmin, VPN tunneling)
-Offsite remote access options
-SAMBA (Is it required for Windows clients to access the files)
-Backup tools (rsync or other methods)
-Server version 18.04.1.0 (does give error when running check disk for defects during USB install.  I understand this is due to a md5sum issue in the November release.  I’m assuming I can proceed past this without trouble, or I could wait for 18.04.2 which fixes this false pisitive?).

I appreciate any suggestions or roadmap so I can get better organized (and study) how to properly implement.

---

### Post by TheFu on 2019-02-07
Wow.  You don't want to crawl first, do you?  ;)   To setup all that AND have it be secured is a multi-year amount of knowledge to get, digest, and understand.  If you have an CCNA cert, then a few months can be removed.

Security architecture begins BEFORE and server is installed.  It begins with networking, compartmentalization for different risk factors.  Security architecture also needs to consider which programs are used.

You have shown some knowledge in this post, but it would be helpful to know your networking skills.  Also, many residential ISPs do not allow running "servers" at home, so you'll probably need a few VPSs to do what you want.

There are many different opinions about much of what you've mentioned / asked.  Just to get you started with some ideas:

* ssh/sftp/sync are for local and remote system management and file access. Don't allow passwords, only allow ssh-key or ssh-certs for authentication.  When you setup the key(s), use an elliptical cipher.  ssh-keygen and ssh-copy-id are the tools. Windows has WinSCP and Putty to access ssh and SFTP servers.  Any Linux/Unix desktop can use their normal file manager with sftp:// in the URL.

* For automatic sync of files and many other things, including web-access, check out nextcloud, seafile,  There are others. I use nextcloud, but only over a VPN or using an ssh-SOCKs proxy. My nextcloud server is not directly available on the internet due to personal security considerations.  I've never used dropbox. Never saw the point when I can self-host everything.  In general, you'll want a dedicated server for this.

* CIFS/Samba isn't suitable for use over the internet. Stick with sftp.

* Media access (video/music/photos) has lots of different options, but if you aren't too tied to F/LOSS-only solutions, there is **Plex Media Server**.  In general, you'll want a dedicated server for this.  There are many other options besides Plex. It is mainly for TV and Movies. 
Nextcloud clients now how to playback music, so that is an option.  mpd is a daemon that lots of people like for a music server. There must be 20+ mpd clients across all platforms.  Lots of different music options.  Sometimes I just use sshfs and remotely mount the storage over the internet and use a local music player like Clementine or xmms or mpv or mplayer or ... whatever plays files from the local file system.  
For photos, nextcloud works, so does plex's web interface (or DLNA if you prefer). I've been using a perl-cgi script for my huge photo collection (130K photos). I used to let it be available over the internet, but had some privacy issues, so that ended quickly about 15 yrs ago.  Now it is only available via VPN or ssh-proxy.

* Backups - rsync has some issues as a backup tool. It looses permission changes over time and only works with Unix file systems for storage when versioning is needed. It can use hardlinking to make the backups more efficient.  Also, from a security standpoint, having the backups "pulled" by a different machine is an important aspect and using a backup tool that supports versioned backups is critical.  Duplicity or rdiff-backup is what I'd use. Actually, I use rdiff-backup to backup everything except media files.  For media files, a simple rsync mirror is used.

* RAID isn't something I'd recommend to someone new to Linux.  Better to learn to use LVM, IMHO.

* To compartmentalize everything, use virtual machines.  If you don't care about security much, you might try to use containers, but container management isn't something people new-to-Unix should attempt.  There are just too many subtle considerations.  FYI, I don't trust pre-built containers or VMs. Who knows what might have been added or how smart the builder was?  Nobody.

I don't have a clue about iOS, but if the system follows standards, then client should be possible.  I know there are great, F/LOSS, sftp and ssh clients for Android and OSX. I don't use Apple stuff, so cannot say for certain about iOS, since Apple forced all GPL software from their app-store. [https://news.ycombinator.com/item?id=12894721](https://news.ycombinator.com/item?id=12894721)

ssh can do 50 more things than most people know.  If you want to connect systems together, in an authenticated, secure way, ssh is one of the easiest answers that works.

Lastly, I would not setup webmin.  It is not recommended for Ubuntu systems. If you choose to ignore that advice, please, only allow localhost, authenticated, access, never access from the LAN or WAN.

Many of these things work 1000x easier from Linux clients than from any other.  Consider that when getting frustrated on Windows.

If the installation media fails validation, don't use it.  Get it from a different, trusted, resource.  Many local Universities will have a mirror that is very fast.  

Not sure if this link is helpful to you or not, but here's what I do in the 1st 5 minutes on a new server: [http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](http://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)

As for partitioning, I'd responded to others about that in these forums, this week.  The OS partition should be 25G or less. Swap should be 4.1G pretty much regardless of anything else. If you split out HOME or /var or /boot is dependent on other aspects like whether you use LVM or encryption. There isn't 1 answer.

It really would be good if you picked 1-2 topics and stayed with just those as you learn more.  Crawl first, then stand, walk, walk fast, jog, run, sprint.  Jumping to expert skills too early is asking to be hacked. Unix security knowledge requires time to digest, think over, and understand.  Having a mentor would be good too.

---

### Post by aljames2 on 2019-02-07
Thanks!! for your time, ideas, and advice.  A tremendous post that helps me a lot.  Definitely brought me down to earth a bit, but with some narrower focus.

My networking experience is shallow but I do understand what I read and willing to do the work.  I take a slow/cautious approach with lots of personal notes before setting anything up.  I want a good base server set up first, proper housekeeping, permissions, static IP, stay away from /root, etc. and then will add on when I know I'm ready (back-up first).

I like the NextCloud idea with VPN.  Do you recomm. any particular VPN services (I've read some on DigitalOcean)?

I'm wondering if a VPS is really needed if I'm only serving up content to myself & other household family members when remote.

LVM - I've read more on LVM and like it as a place to start vs. RAID.  I probably have overkill in my HDDs for now but perhaps I could use the extra HDD for system backup.

I forgot to bring up file systems originally...given that my client machines are Windows (for now), should I specify a particular file system that will share nicely across platforms (Ext4, XFS, ZFS, Btrfs)?

Thanks again!

---

### Post by TheFu on 2019-02-08
VPN service? No, you need to run the VPN server at the same location (house?), so you can access nextcloud, or anything else inside your LAN, from remote locations.  I use the VPN to the house mainly from Android tablets or phones.  Generally don't do it from my laptop, since starting an ssh-proxy is much easier. 
The reason to have a paid VPN service is to hide where you are or from the network provider you are inside (cafe, hotel). None allow you access back into you home when you are remote, that I am aware.  Don't use PPTP - ever.

Do you need a VPS?  Depends on your ISP contract and how nasty they are. 

File systems ... this gets into opinions quickly.  Every file system has pros and cons.  If you don't have a specific reason to use a specific file system, then stick with ext4 for most of them.  I avoid btrfs because it lies to df and du commands.

If you care about security, the network architecture has to come first.  Most home networks aren't setup for any security at all.  I see 10K+ attacks daily, mostly from Chinese (90+%), Brazilian and Argentina Universities.  The internet is the wild west.  If you run a service, expect to be hacked.  There are over 2M wordpress sites that are hacked right now.   Can WP be run securely?  Probably, but it isn't point-n-click, like the way most of those hacked sites do it.

Hopefully, some other people will post too, so you get some different opinions.  Most of the long-time, active, members here have blogs or information links to their personal sites. Those are worth a look.  On my blog, I write about the "why", not the "how." I figure someone can lookup what to type, once they know why.

Good luck.

---

### Post by aljames2 on 2019-03-13
For the VPN server at home, is it better to use my Pfsense edge router/firewall that I built to handle the OpenVPN, or should the VPN server run on an additional appliance like a Rasberry Pi?

..and to clarify, a paid VPN service, is used for www data encryption/privacy?

---

### Post by mastablasta on 2019-03-14
i have a similar setup except for music and well the CPU is weaker and instead of SSD i use a USB stick for the OS. your's is overkill for these tasks anyway.

Nextcloud or Owncloud will serve photos and data to family. There is also Seafile.
To serve photos to other people with additional data etc. or if you want to sell them, it is worth looking into *piwigo *photo gallery. it's a webserver for photos.

Drupal i installed in webserver (e.g. apache, ngnix). i don't have it at home server, but use a host for website.

i use raid1 with ext4 (mdadm). 

for server administration i use SSH and Ajenti which offers a webgui for server, to access files easily i use filezilla and sFTP protocol. 

for all the stuff you plan to store you will also need a database so you can find it. there are a few option in that arena such as PostgreSQL, MariaDB or MySQL, SQLlite... but these depend on the service you want to install.

i also use fail2ban on server and unattended-upgrades, along with server sending me emails of various breach attempts, reports and anomalies.

overall server uses max about 20% CPU and usually less than 500 MB ram, but mostly it idles on well below 5%. like i said the stuff i have is not really that demanding. i imagine some streaming can be more demanding.


looking back - i wouldn't setup raid if built it again. raid only protects against disk failure. in case one disk dies the server continues to function. it does not protect your data. errors on data simply get mirrored. and if server is down due to disk failure... i mean it's not like mission critical stuff is there and family can wait a bit. it is a lot more important to have proper backups made, so if i did it again i would use separate disk setup and do backups to each of them separately. that was if one backup was bad and if one disk failed i could still use the other one.

---

### Post by aljames2 on 2019-03-14
Thanks masta.  I am not excited about using Raid either.  At first I was going to use a Raid 1 but I plan instead to focus on a reliable backup process.

I am going to leave my Drupal website on my host’s hybrid VPS for now instead of hosting from home...at least for now.

For VPN, I am looking at using Pfsense firewall/router (that I built) as the VPN server for remote access to my home network?  Wondering if others have done/tried this?

---

### Post by wnmnkh on 2019-03-15
I see you have running a pfsense router computer. That is very good start and pretty much most important part, security.

I use opnsense instead of pfsense, but I believe pfsense should also have some basic Intruction Detection Service with IPS. It is probably not enabled by default. You should enable it and download some blacklists.


I strongly do not recommend to run a webserver at home. Even with proper reverse proxy setup it is hard to secure and there are a lot of ways to screw up.

And yes, running OpenVPN server on pfsense for remotely access your home network is the best bet. It is hard to crack open pfsense/opnsense, and you only have to open just one port (for OpenVPN) for that. Make sure enable TLS.

I am not sure about pfsense, but opnsense does support 2-factor auth with auth apps if you want extra layer of security.

For my case FreeNAS file server + Plex on a single computer (FreeNAS does not react well in VM environment. Better to run as a sole), Rasp Pi with Pi-hole, and a cheap minipc which has Ubuntu server installed. All protected by an opnsense router computer.

I run docker on my Ubuntu server and currently running mariaDB, my personal wiki and Subsonic music streaming server.

However none of these docker containers are exposed to WAN. Plex and Subsonic do have remote access feature, but then I have to open additional ports and far more vulnerabilities because I have to rely on those services to be secure.

What I do is keep them at my home network. From outside I connect to my home network using VPN server from the opnsense system, then I connect to Plex and Subsonic.

---

### Post by aljames2 on 2019-03-15
Thanks!  all this helps clarify some things.  I hadn’t heard of Opnsense but looks like a well established alternative to PF.  I’ll stick with Pfsense for now since I’ve studied it more.  I appreciate the configuration tips.

I’m learning there is much to do to properly set up the network infrastructure before even starting with everything behind it?  Don’t want to be exposed before clamping down some security measures...at least this is the approach I’m taking.

Thanks again all!

---

