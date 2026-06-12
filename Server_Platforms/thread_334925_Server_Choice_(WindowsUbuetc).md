---
title: "Server Choice (Windows/Ubu/etc/)"
date: 2007-01-09
forum: Server Platforms
---

### Post by netbotix on 2007-01-09
I am looking into setting up a dedicated file/maybe routing server for my home network.  Currently the Set up is as such: a pppoe ethernet modem connected to a netgear wire less router.  On the wireless network there are two laptops and a PC.  On the wired network there is 2 pcs (one of which I hope to turn into the 'server').
My needs are as follows:
Share files between computers (mp3s mainly)
Basic server needs (LAMP, mainly for just for my testing, not necessarily public usage)
Maybe have the PC act as router (firewall pppoe) and my current wireless router just do the 'routing'

My main concern if I use ubuntu or any linux flavor at that is different types of file systems (all computers currently run XP) and being able to share files over the network with windows clients.

I hope I was able to address my needs clearly through this post if there are any more things I need to add please let me know.

Currently I use Ubuntu 6.10 as a dual boot on my main PC.

---

### Post by loserboy on 2007-01-09
just make large fat32 partitions for all your sharing

---

### Post by netbotix on 2007-01-09
Does Linux play nice with fat32? ie. sharing, maybe a network drive etc.?

---

### Post by loserboy on 2007-01-09
yea i dual boot ubuntu/xp  and i keep all my files on a fat32 partition and it works perfect.
i did some research and i think there was some disadvantage but i havent noticed anything... google it maybe.

---

### Post by Jussi Kukkonen on 2007-01-09
Mostly that stuff is going to be a whole lot easier on linux (in my opinion). The file server part may be a problem, depending on your intended use: I've had problems with streaming music over samba (Ubuntu server - Ubuntu client) and I've noticed on these forums that I'm not the only one. You might want to test this before spending a lot of hours on other things...

As a sidenote, all my streaming problems went away after I changed to NFS (not to mention the increase in file transfer speeds).

---

### Post by loserboy on 2007-01-09
oh also, theres something you can do so that linux can read/write on ntfs, i forget what the program is though and ive never used it, i like the idea of having seperate partitions anyway

---

### Post by Jussi Kukkonen on 2007-01-09
loserboy, your situation is different: netbotix intends to save stuff on the server then access that with a client machine.

I disagree with the fat recommendation. If the server is not going to be dual boot, do not use fat. It's not nearly as fault tolerant as e.g. ext3. If you share the files with e.g. samba, the underlying file system shouldn't matter (and if it did, I'd expect a native linux FS to fare better). Feel free to correct me though.

---

### Post by loserboy on 2007-01-09
yea i see that now, i thought he was talking about a home network and storing files not actually streaming them.

---

### Post by loserboy on 2007-01-09
in that case im kinda interested in seeing how this turns out i kinda wanna do the same.

so lemme clarify, do you plan to make you storage server linux and all the clients windows/linux? 
and is it just going to be for LAN or are you also trying to access remotely?

---

### Post by netbotix on 2007-01-09
> **loserboy said:**
> in that case im kinda interested in seeing how this turns out i kinda wanna do the same.

so lemme clarify, do you plan to make you storage server linux and all the clients windows/linux? 
and is it just going to be for LAN or are you also trying to access remotely?


All windows and one dual boot

---

### Post by Brazen on 2007-01-09
> **netbotix said:**
> All windows and one dual boot

Why would you dual boot the one?  If you are going to have a file server, you are going to want it to be running all the time otherwise you will not be able to get to those files while you are booted into the other OS.  Either set up your file server as Windows or as Linux, don't mess with dual boot on a server.  If you want a dual boot set up just to play around on, then forget about using it as a server.

---

### Post by netbotix on 2007-01-09
> **Brazen said:**
> Why would you dual boot the one?  If you are going to have a file server, you are going to want it to be running all the time otherwise you will not be able to get to those files while you are booted into the other OS.  Either set up your file server as Windows or as Linux, don't mess with dual boot on a server.  If you want a dual boot set up just to play around on, then forget about using it as a server.


no the one that would be dual booting is one of the other desktops...not the server, one pc will be a dedicated server... just trying to decide on os

---

### Post by Brazen on 2007-01-09
> **netbotix said:**
> no the one that would be dual booting is one of the other desktops...not the server, one pc will be a dedicated server... just trying to decide on os

For the server:  Well, of course, use Ubuntu (you do know where you are don't you? :D )  You will want to use Samba for the file share, and Apache/Mysql/PHP for the web server.

As for the file system, on the server, it won't really matter.  Samba takes care of making sure  your Windows boxen can talk to the file server; the underlying file system makes not difference in that regard.  I will say though, using fat for your server file system is the worst choice you could make.  Best thing for you is to just let the Ubuntu automatic partitioning do it's thing.  Personally, I manually partition and use XFS file system whenever I can, but there are other issues with that (and worthwhile benefits, of course, too).

---

### Post by netbotix on 2007-01-09
> **Brazen said:**
> For the server:  Well, of course, use Ubuntu (you do know where you are don't you? :D )  You will want to use Samba for the file share, and Apache/Mysql/PHP for the web server.

As for the file system, on the server, it won't really matter.  Samba takes care of making sure  your Windows boxen can talk to the file server; the underlying file system makes not difference in that regard.  I will say though, using fat for your server file system is the worst choice you could make.  Best thing for you is to just let the Ubuntu automatic partitioning do it's thing.  Personally, I manually partition and use XFS file system whenever I can, but there are other issues with that (and worthwhile benefits, of course, too).


Does Samba allow for network drives?
That would be my only hesitation on using ext3

---

### Post by Brazen on 2007-01-09
> **netbotix said:**
> Does Samba allow for network drives?
That would be my only hesitation on using ext3

Yes, network drives is the ONLY thing samba allows for (well also printers and logins, but in regards to files).  Samba does nothing for local access to files.  Samba's purpose is to share files over the network, to Windows clients.  The file system used under Samba, does not affect this at all.

---

### Post by netbotix on 2007-01-09
> **Brazen said:**
> Yes, network drives is the ONLY thing samba allows for (well also printers and logins, but in regards to files).  Samba does nothing for local access to files.  Samba's purpose is to share files over the network, to Windows clients.  The file system used under Samba, does not affect this at all.

So using Samba I would not notice performance hits (depending on the file system)

---

### Post by PetePete on 2007-01-10
i found samba to be quite slow compared to reading/writting files on winxp shares.

if its just to access files from other windows computers then i'd say use win2k or xp pro. should be much quicker than samba..... (im going to get raped for saying that lol)

---

### Post by Brazen on 2007-01-10
> **PetePete said:**
> i found samba to be quite slow compared to reading/writting files on winxp shares.

if its just to access files from other windows computers then i'd say use win2k or xp pro. should be much quicker than samba..... (im going to get raped for saying that lol)

Did you use the Ubuntu Server to set up your file server (ie NO GUI).  Also, did you set the "socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192" in your smb.conf?  This is supposed to make a huge difference, although I've never tried NOT using it.

I can tell you though, when we switched from a Windows 2000 file server to a Samba file server at work, our GIS department said their software was opening files in half the time (they complained a lot about the speed of our old file server - a 2.0 ghz Opteron/ 2G Ram server).

I would also say my 500 mhz Celeron file/web/sql server at home flies along just fine, too.  My home server is much faster than my work server, but then it's usually only being accessed by one person at a time.  Even on a 500 mhz Celeron I would say the limiting factor for my home server is the network bandwidth (100mbit).

To the OP, I use XFS at home and Ext3 on the work server.  I would have preferred to use XFS all around, but at work there were other reasons that necessitated Ext3.  XFS is a faster file system, but really, the bottleneck in a home file server is going to be network bandwidth either way.  One thing I do when I use XFS is I create a 100 MB /boot partition and format it as Ext3 because Grub does not play nice with XFS.

---

