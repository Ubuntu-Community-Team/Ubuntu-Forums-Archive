---
title: "New to Linux. Questions with Server configuration"
date: 2010-01-14
forum: Server Platforms
---

### Post by M-ManLA on 2010-01-14
Hi. I have been looking to build a Linux system for a while, and have  finally decided to start planning one. What I am looking for is a  personal  multipurpose server that can do multiple functions. First off here is  the planned system specs (some items might change in the future) Let me  know if this will work or not with Ubuntu 9.10 Server Edition;

Intel E6500 CPU
Asus P5G41T-M LE Motherboard Intel G4 Chipset
G.Skill 2GB DDR3 1333
WD  1TB Green Drives (In RAID 1, will get up to four drives)
1U NORCO  Server Chassis
iStarUSA 350w 1U PSU

This server will be  connected to a router, behind a firewall.
So this is what I would  need from my server (please let me know if these options are available.  If there is a different option or links, please post them);

**Interoperability  with Windows 7 Ultimate 64 bit ** 
I will need this to work with my Windows 7 client  workstation. I will be exchanging files frequently between the  workstation and the server. 

**GUI/Console on client machine**
Since  this server will either be in the closet or in a rack, it will be best I  have some way of interacting with the server since there will be no  screen, mouse, or keyboard will be connected to it. It would be nice to  tell the server to perform certain task listed below on my workstation  with a app,GUI, or something similar. 

**File/Backup Server**
I  need the server to store files over the network to the server. Also  perform automatic backups to the server with certain files that I choose  from my workstation (possibly wake the workstation out of sleep mode to  back up as well, and go to drive R: and back up file "X", then set the  workstation back to sleep. I might can set Windows 7 for this, but if  there is a program out there let me know). 

**FTP/Mail Server**
There  might be times that I will need to send a recorded session file over  the net if I can not deliver the session in person. Therefore the sever  will have to be able to send a huge file (could be even 4GB+ depending  on the session) overnight to the client. I would also prefer the  transfer to be "secure" as well. 

**Relay FTP/Mail service**
This  would be a Godsend if I can add this feature. Pretty much, I might make  multiple servers for some of my buddies and clients to use. In that  case, a "Relay" option will be used. Say both of us have a server, but I  don't want to tie up my or my recipient's workstation to receive the  files. I would set the server to "relay" to the other server without the  recipient having to open up an email to download the file (like  auto-downloading to the recipient's server). They can choose to transfer  it or delete it.   

[B]Hot-Swamping
[/B]I migh need to hot swamp while the server is on in the future. Can I do this?

**Playstation 3 server**
I might want to stream files from the server to the PS3. Such as music, videos, and pictures. I heard there is certain programs for that, so let me know please. 

[B]Remote server access
[/B]I might from time to time need to access data from a outside computer. I would like to have this option, but will want to "hide" the server as well. Might can also do this with the router. 

[B]Power Management
[/B]I want this server to spin down the hard drives, as well as go on standby mode when not in use. 


I also want to know what file system it  loads on there. Is there an option. I hear about XFS and JFS.  I need it  to talk to my W7 NTFS drives. If there is anything else I would have to  follow, let me know. I am not going to set it too soon, but sometime in  the summer I will start getting parts. I might have further questions in the future. Thank you in advance.

---

### Post by Cheesemill on 2010-01-14
> **M-ManLA said:**
> 
Intel E6500 CPU
Asus P5G41T-M LE Motherboard Intel G4 Chipset
G.Skill 2GB DDR3 1333
WD  1TB Green Drives (In RAID 1, will get up to four drives)
1U NORCO  Server Chassis
iStarUSA 350w 1U PSU

Your hardware specs sound fine, I have a server with an old Celeron and 512MB that runs the sort of file sharing duties you're talking about as well as networking and routing services and 2 VM's (a mail server and a LAMP server)

As far as RAID goes you may want to do a bit more research. RAID1 is simple mirroring and is usually only used with 2 drives, each contains an identical copy of the data. For more than 2 drives you probably want to use RAID5, each drive contains an amount of data plus parity information for data on one of the other drives. With a RAID5 you get a capacity equal to (n-1), for example 3x1TB drives would give you 2TB of usable space, 4x1TB would give you 3TB etc.

Also bear in mind that RAID is not a backup solution, it doesn't protect against user/application error or hardware failure. It only protects you against failure of a single HD. For any critical data (I'm assuming your talking about recording sessions) it is good practice to have off-site, off-line backups as well.

Also I would suggest having a separate drive for the OS, it can be a bit of a pain getting Ubuntu to boot off a RAID array. You can use either a small HD or an SSD, you can easily get away with 10GB for a server installation (I actually use a Compact Flash memory card with an IDE adapter for my system drive).

Here's a link for one of the best tutorials I've found for setting up RAID5 on a Ubuntu server:
[http://cobraftp.serveftp.com/pub/raid.pdf](http://cobraftp.serveftp.com/pub/raid.pdf)
*Edit - Seems like this link is down, I've attached the file.*

You might also want to check out Wikipedia for more info about RAID:
[http://en.wikipedia.org/wiki/Standard_RAID_levels](http://en.wikipedia.org/wiki/Standard_RAID_levels)

> 
**Interoperability  with Windows 7 Ultimate 64 bit ** 
I will need this to work with my Windows 7 client  workstation. I will be exchanging files frequently between the  workstation and the server. 
For sharing with Windows machines you need to set up Samba on your server. There are plenty of guides out there and it's also covered in the above RAID how-to.

> [B]
GUI/Console on client machine[/B]
Since  this server will either be in the closet or in a rack, it will be best I  have some way of interacting with the server since there will be no  screen, mouse, or keyboard will be connected to it. It would be nice to  tell the server to perform certain task listed below on my workstation  with a app,GUI, or something similar.
Ubuntu Server doesn't come with a GUI installed, it's command line only on a default install.
It is possible to install a GUI on the server but IMHO it's a bad idea, it uses up unneccasary resources and creates a larger surface area for attack. Also there are very few GUI apps for administrating a Ubuntu server, all of the configuration is done by editing text files. I also think it's better to get a good understanding of using the shell, if for some reason your GUI wont start then troubleshooting is almost impossible without this knowledge, if you're already comfortable with the shell then it's not so much of a problem.

For remote shell access you just need to install the openssh-server package, you can then connect using the ssh command from any Linux box or by using [PuTTY]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/") from a Windows box. You can set up external access by just forwarding the ssh port to your server using your router. If you want to do this (more on this below) you can change the default ssh port and set up rate limiting with UFW (the firewall that comes installed on Ubuntu Server), these 2 things will stop 99% of the script-kiddie attacks that are inevitable on any pubic facing ssh server.

> 
**File/Backup Server**
I  need the server to store files over the network to the server. Also  perform automatic backups to the server with certain files that I choose  from my workstation (possibly wake the workstation out of sleep mode to  back up as well, and go to drive R: and back up file "X", then set the  workstation back to sleep. I might can set Windows 7 for this, but if  there is a program out there let me know). 
Once you have Samba set up then you can just use the Windows 'map network drive' feature to give your shares a drive letter. Then just use whatever method you want on the Windows machine for scheduling backups.

> 
**FTP/Mail Server**
There  might be times that I will need to send a recorded session file over  the net if I can not deliver the session in person. Therefore the sever  will have to be able to send a huge file (could be even 4GB+ depending  on the session) overnight to the client. I would also prefer the  transfer to be "secure" as well. 
You don't want to use FTP as it sends all user credentials and data in clear text, you can either set up an SFTP (Secure FTP) server, or just use the SSH server you already have installed. You can use the scp command from Linux or [WinSCP]("http://winscp.net/") from a Windows box to transfer files using the ssh protocol.
One thing to think about is your internet connection, if it's just a standard DSL then you probably have an upload bandwidth of around 0.5Mb/s (you can check on [Speedtest]("http://speedtest.net/")). If that's the case then your upload speed will be around 225MB/hour, or about 4 hours for each GB.
Another thing to consider is resuming. The last thing you want in the middle of a massive transfer is for one of the connections to blink and having to start the whole thing again. SCP doesn't handle resuming so for large transfers you may want to consider using rsync. This transfers data over an SSH tunnel so has all the security but it will also handle resuming partly downloaded files.

> 
**Relay FTP/Mail service**
This  would be a Godsend if I can add this feature. Pretty much, I might make  multiple servers for some of my buddies and clients to use. In that  case, a "Relay" option will be used. Say both of us have a server, but I  don't want to tie up my or my recipient's workstation to receive the  files. I would set the server to "relay" to the other server without the  recipient having to open up an email to download the file (like  auto-downloading to the recipient's server). They can choose to transfer  it or delete it.   
Again you can use SSH, just remotely log onto one of the servers and use ssh/rsync to transfer data to the other server.

> 
[B]Hot-Swamping
[/B]I might need to hot swamp while the server is on in the future. Can I do this?
Not with the hardware you've suggested. You really need high end server motherboards and drives for hot-swap capability.

> 
**Playstation 3 server**
I might want to stream files from the server to the PS3. Such as music, videos, and pictures. I heard there is certain programs for that, so let me know please. 
I've no experience of this myself but all you need is a DLNA server installed, googling for 'DLNA Ubuntu' throws up some promising looking results.

> 
[B]Remote server access
[/B]I might from time to time need to access data from a outside computer. I would like to have this option, but will want to "hide" the server as well. Might can also do this with the router. 
Again, just use SSH.

> 
[B]Power Management
[/B]I want this server to spin down the hard drives, as well as go on standby mode when not in use. 
You can set up the drives to spin down when not being used. Standby is a different matter though, if your server is on standby then it wont respond to any incoming requests for files.

> 
I also want to know what file system it  loads on there. Is there an option. I hear about XFS and JFS.  I need it  to talk to my W7 NTFS drives.
By default it will use the ext4 filesystem, but you can use XFS or JFS if you want (I use ext4 for all my drives). The filesystem you use has no impact on sharing files to the Windows machines, they just use the Samba protocol and have no knowledge of the underlying file structure.


To get a head start before you get your hardware, and also because it's your first time setting up a server (and you will make mistakes) I'd recommend practising first with a virtual machine.

Just install VirtualBox on your computer then you can have a play about with a server install, just make sure you set up the machine with bridged networking so it gets its own IP address.

I think the best advice I can give you is to document everything you do, it's all to easy to forget what configuration changes you've made. This way when you get your hardware you'll already know what your doing.

Also if you can hold off until the end of April when Lucid Lynx (10.04) is released I would do so. Lucid is the next LTS (long term support) release and as such will be supported for 5 years as a server, whereas support for 9.10 runs out in April next year. The last thing you want to be doing with a production server is upgrading it every 18 months.

---

### Post by M-ManLA on 2010-01-14
> 

Thank you. That is  a lot of info. 

I was considering a RAID5 Configuration. I just want to be able to have another disk keep data just in case one of the disk was to fail. I will still do backups to disc as well. Does Linux allow you to burn from the server itself?

You also must have been reading my mind about the OS drive. Was considering a small SSD to boot off of. 

As far as the the GUI, it would actually be set up on the Windows machine. It would just give me visual information on what is on the server. I see this as something I would need to research some more. Any readings on this?

I have already been reading about SSH. So there is a program called "RSync" that will be good to use. I'll check up on it. 

I might not do hotswamp. I know some of the motherboards use it, but is worthless if the program supports it. Especially since I am putting no less than a TB HDD in there. 

Power management, I might just spin down the hard drives. Have to save on the electric bills you know. 

I'll will defintely use the regular ext4 File system. I will most likely try the virtual machine (or see if I can revive a old machine). Thanks for the heads up on the LTS. That is the last thing I want is some software that will go out of style in a year.

---

### Post by Cheesemill on 2010-01-14
If you want some sort of graphical interface take a look at [Webmin]("http://www.webmin.com"), it will allow you to administrate your server from a web page.

If you're not set on Ubuntu and just want a simple RAID storage server without having to learn any CLI then another option is [FreeNAS]("http://freenas.org/freenas"), although it may not have all the features you're after.

---

### Post by M-ManLA on 2010-01-14
I check it out. 

I do want to use Ubuntu. I have heard some good things about it. I don't mind learning command lines if I need to. FreeNAS might not have all the functions I am looking for, but will keep it in mind for other builds.

---

### Post by lisati on 2010-01-15
> **M-ManLA said:**
> I check it out. 

I do want to use Ubuntu. I have heard some good things about it. I don't mind learning command lines if I need to. FreeNAS might not have all the functions I am looking for, but will keep it in mind for other builds.

Ditto for checking out webmin

---

### Post by M-ManLA on 2010-01-28
> **lisati said:**
> Ditto for checking out webmin

So you can configure webmin to work with Ubuntu server in a web browser?

---

### Post by lisati on 2010-01-28
> **M-ManLA said:**
> So you can configure webmin to work with Ubuntu server in a web browser?

That's the idea. I have webmin on my server, and access it using a browser (I use firefox)  on my laptop. Whenever I'm online I usually have one tab open for webmin, and one or more tabs for whatever I'm looking at online. I don't even need a GUI on my server to be able to use it through another machine via a browser.

---

### Post by lykwydchykyn on 2010-01-28
> **M-ManLA said:**
> So you can configure webmin to work with Ubuntu server in a web browser?

yep.  It gives you a web-based interface to administer just about anything -- network services, system administration, hardware, software update/install, burning CD's and DVD's, etc.

---

### Post by M-ManLA on 2010-01-28
> **Cheesemill said:**
> If you want some sort of graphical interface take a look at [Webmin]("http://www.webmin.com"), it will allow you to administrate your server from a web page.

If you're not set on Ubuntu and just want a simple RAID storage server without having to learn any CLI then another option is [FreeNAS]("http://freenas.org/freenas"), although it may not have all the features you're after.

Actually FreeNAS looks like It might fulfill my needs as well. I will also check this out. Something tells me though Ubuntu is a better route. Anyone else wants to chime in? Any pages where I can start learning CLI? I am using it in a virtual machine right now.

---

### Post by M-ManLA on 2010-01-28
> **lisati said:**
> That's the idea. I have webmin on my server, and access it using a browser (I use firefox)  on my laptop. Whenever I'm online I usually have one tab open for webmin, and one or more tabs for whatever I'm looking at online. I don't even need a GUI on my server to be able to use it through another machine via a browser.

> **lykwydchykyn said:**
> yep.  It gives you a web-based interface to administer just about anything -- network services, system administration, hardware, software update/install, burning CD's and DVD's, etc.

That is exactly what I want. I want my server to be "headless". I might have to put it in the closet, but have to clean it out, and most likely bring in a power cord. I might also install it in my rack if I can get some cool 'n' quiet fans installed.

---

### Post by M-ManLA on 2010-01-28
Ok so now I am trying to map the server in windows (I have it in a virtual machine), but It is not finding it. I'm reading the manual right now, but is there something I have to install? Samba is already installed.

---

### Post by howlingmadhowie on 2010-01-28
The first thing to try would be pinging the server on the ip address it got.  in the virtual machine, enter 'ifconfig' after you've logged on. then open a dos box on windows (providing windows 7 still has one of those, i dunno) and ping the virtual machine's ip address. if this doesn't work, there is a high chance that the firewall on you windows 7 installation is blocking you.

after that works, trying installing ssh on the server vm ('sudo apt-get install ssh', then enter your password, then you'll probably have to press enter again). then install PuTTY on the windows 7 installation and try to connect over ssh with the server vm. 

Btw, one more thing to consider later would be to install a program called denyhosts on your server. this will automatically blacklist ip addresses used repeatedly unsuccessfully to log in via ssh to the server.

Another thing you could do is check the bios on your server motherboard to see if it supports wake-on-lan. Enabling this might be a bad idea for a computer connected directly to the internet however.

---

### Post by trentscott4 on 2010-01-28
I just recently built a similar custom PC for running Ubuntu Server that I purchased thru Rockpoint Systems at [http://rockpointsys.com](http://rockpointsys.com).  They've got quite a few different builds and also will order custom parts.  I'm really happy with my machine, it runs fast and the price was right.

I found a coupon online for 10% off too: K402MX3

---

### Post by lykwydchykyn on 2010-01-28
> **M-ManLA said:**
> Ok so now I am trying to map the server in windows (I have it in a virtual machine), but It is not finding it. I'm reading the manual right now, but is there something I have to install? Samba is already installed.

I don't think it creates any shares by default; you need to set up some shares first.

---

### Post by M-ManLA on 2010-01-29
> **lykwydchykyn said:**
> I don't think it creates any shares by default; you need to set up some shares first.

Yes this is the part I am stuck on. It seems to see my network adaptor, but I'm running it on a VM right now. I want to see if I can backup from a file on a hard drive.

---

### Post by lykwydchykyn on 2010-01-30
> **M-ManLA said:**
> Yes this is the part I am stuck on. It seems to see my network adaptor, but I'm running it on a VM right now. I want to see if I can backup from a file on a hard drive.

Did you install webmin on it, or do you want to set it up the command line way?

Not to push you off on a manual, but there is a lot of good documentation out there on SAMBA, much better written than what I'd tell you here.

Try this one: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by samosamo on 2010-01-30
did um... did he say Hot Swamp?

---

### Post by M-ManLA on 2010-02-02
> **lykwydchykyn said:**
> Did you install webmin on it, or do you want to set it up the command line way?

Not to push you off on a manual, but there is a lot of good documentation out there on SAMBA, much better written than what I'd tell you here.

Try this one: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

No I don't mind reading. If there is anything that will help me out would be welcomed. Thank you I'll read it over the next couple of days. 

> **samosamo said:**
> did um... did he say Hot Swamp?

Just a thought. Especially if a drive runs out of space. Most likely won't happen for a while, but might as well know now than later. 


Also, is it better to run my motherboard as IDE or AHCI mode?

---

