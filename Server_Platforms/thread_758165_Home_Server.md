---
title: "Home Server"
date: 2008-04-17
forum: Server Platforms
---

### Post by championchap on 2008-04-17
Howdy guys, just realised I have a bit of a conflict on my hands here.
I want to build a server.
Not a problem right?

Well, I'm picky. 

I want to build a home server to act as both a web server, and a file server for a personal website. 
It needs to be as quiet as possible, and preferably in a micro-atx box style case. This is where problems may arise! hehe
Since it's a file server, I'm going to need a fair ol' chunk of HDD space.
I'd say either 1 or 2 TB seeing as it's going to be shared between 5 users. 
Then there is backups to think of! EUGH!

3 of us will be connecting to it exclusivley using Windows. 2 on XP (32) and 1 on Vista (64)
Another of us on both XP (32) and Ubuntu Linux
The last of us will be connecting to it using a Mac.

Cost is also an issue. I don't want to break the bank on this thing. 

Any ideas?

Help with setting up a web/file server for a ubunto n00b would be greatly appreciated too!

haha, looking back.. this may all be a bit much to ask. But I guess I'm in the right place?

---

### Post by madjr on 2008-04-17
i don't know if this help, but i read somewhere that mythbuntu has some tools so it can act very well as a file/home server.

then a web server can be easily done on any linux distro by installing php/mysql i guess. I also believe mythbuntu has mysql pre-installed....

you may want to wait for the hardy based release thou.. it's an official release in a week or so

---

### Post by jcwmoore on 2008-04-17
if you are not going to run any apps on it and only use it as a web host/file server the you don't need much horse power, but you will need a big hard drive.  I have this set up, i'm running web site/file server on a 500 MHz 92 RAM machine.  I have a 20 GB hard drive for the system files, but I use a 120 GB external HD for the home folder.  There is lots of space and the web site runs quickly and reliably.  I would suggest you get the cheapest machine you can find (wal-mart sell a $200 PC online) and then get a big HD.  You may even spend more on the drive than the PC it self.  Use samba to let you windows boxes to connect, but i'm not sure how to connect OS X to a linux server.  so get a dirt cheap PC and then plug a second big HD to it and you should be good to go

---

### Post by freebeer on 2008-04-17
You're also probably better off posting in the Server forum.  :D

---

### Post by Sef on 2008-04-17
Moved to server platforms.

Are you going to use the command line?  If so, your requirements will be lower.

You should check out [Useful Links on Servers, System Administration, and Security]("http://ubuntuforums.org/showthread.php?t=681267").

---

### Post by analoog on 2008-04-17
> **championchap said:**
> 
Help with setting up a web/file server for a ubunto n00b would be greatly appreciated too!


[https://help.ubuntu.com/](https://help.ubuntu.com/) and [www.google.com](www.google.com) are your friend.
There are many guides out there, make good use of them :)
If you run into trouble then first search for the question on the forums and google, then post a topic.
good luck with your server.

---

### Post by freebeer on 2008-04-18
Are the clients connecting through a LAN or through the Internet?

---

### Post by seepage87 on 2008-04-18
Right now 500GB drives are the cheapest per GB.  You can get a maxtor one for $90 at newegg.com.  1TB ones are $200.  You may want to consider RAID (5 probably, since cost is an issue) so you don't lose anything.  Also, your small case is going to be a problem for fitting that much storage; why not use a bigger case and stick it in the basement or a closet somewhere?  Don't have to worry about noise then either.

I built my server off of a mythbuntu install (though it's also a mythTV backend, so...).  A typical ubuntu server install will get you what you need though (i.e. LAMP, mdadm if you want RAID, etc).

---

### Post by Dr Small on 2008-04-18
I installed my server from the Ubuntu alternate CD as a command line install and build the thing from the ground up. It gave me some expirence, and allowed me to install what I want.

For a simple fileserver, I would go with Apache, MySQL, SSH (and maybe FTP). It depends though really, if the other clients will be connecting from outside the network. If so, the FTP is definately a bad option.

---

### Post by Tux+ on 2008-04-18
A motherboard with as much SATA connectors as possible and some cheap RAM and CPU will do. A motherboard with RAID will help with some of your backup but it's not a 100% complete solution.

As for the Ubuntu setup. A server CD will do but you can install the desktop version if your not familiar with command line.

I sugest a LAMP setup (Apache, Mysql, PHP), Samba for file sharing and webmin for a browser based remote setup. SSH will also be need if your running a headless server.

All the programs mentioned above can be easiy installed using the "apt-get" method. I think the installation is easy but the configuration is the hard part. I'm sure the linux community will help you with that.

Good luck.

---

