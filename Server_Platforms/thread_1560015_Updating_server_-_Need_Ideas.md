---
title: "Updating server - Need Ideas"
date: 2010-08-24
forum: Server Platforms
---

### Post by TheIndecisive1 on 2010-08-24
Alright so I have a computer running Ubuntu Server 7.10 and this weekend I've decided to wipe the computer clean and install Ubuntu Server 10.04. Currently the server's main purpose is a file and print server, which it will continue to be after the upgrade. However I'm looking to expand it's features and I need some ideas on what software and techniques to use. Here is what functions I would like it to have:

File/Print server - going to use Samba
Torrent downloads - have used rTorrent in the past but would like to find one with a graphic interface
Backups - automatically backup to an external hard drive
Network/Server Monitoring - was thinking about Zenoss?

Any software that has a remote interface that can be accessed through a web browser is a big plus for me. At the very least I need to be able to use the software via an ssh connection.

Thanks for any advice.

---

### Post by CharlesA on 2010-08-24
Webmin would work. I used to use it but after I got everything set up, I found that just using SSH was easier for me.

I use rsync to do backups to an external drive every day. If you want to script, I can post it for you.

---

### Post by LightningCrash on 2010-08-24
for backups, BackupPC has a nice web interface

---

### Post by arrrghhh on 2010-08-24
+1 to webmin.

I use rtorrent - for an interface, look at [rutorrent](http://code.google.com/p/rutorrent/).  Web-based UI so it can be accessed anywhere.

---

### Post by imbjr on 2010-08-24
apt-cacher

I have various machines now contacting the server for s/w updates. Once the server has the deb file it no longer has to be downloaded again.

---

### Post by stlsaint on 2010-08-24
Go with nagios for the network monitoring. 
The [nagios2]("https://help.ubuntu.com/community/Nagios2") doc has help with configurations.
The [nagios3]("https://help.ubuntu.com/community/Nagios3") doc is more up to date but it just shows how to install so i suggest you use the [site]("http://nagios.org/documentation") for most helpful info.

---

### Post by TheIndecisive1 on 2010-08-25
Thank you everyone. These programs are exactly what I was looking for.

---

### Post by TheFuturian on 2010-08-25
If you like the look of Nagios, Opsview is definately worth a gander! Same result, simpler configuration ;)

---

### Post by arrrghhh on 2010-08-25
> **TheFuturian said:**
> If you like the look of Nagios, Opsview is definately worth a gander! Same result, simpler configuration ;)

What about Zenoss?  I didn't realize he was looking for a network monitoring solution tho ;)

---

### Post by quietas on 2010-08-25
A good start is [this thread]("http://ubuntuforums.org/showthread.php?t=1075599"). It's loaded with Home Server software ideas. For a Linux torrent server I'd recommend Torrent Flux or Transmission.

I'd watch out for Zenoss though, it's a real hog for resources. If you need perfomance monitoring it works well, PanadoraFMS is another good option. If you only need fault monitoring, Nagios works great.

---

### Post by BkkBonanza on 2010-08-26
For torrents Deluge is nice. It's can be setup client/server with both a web interface and a gnome client option. So it can run on your server d/l files 24/7 and you can either control it with your browser or with the Deluge client on any desktop. I prefer the client app to the web panel but to each their own.

---

### Post by arrrghhh on 2010-08-26
> **quietas said:**
> A good start is [this thread]("http://ubuntuforums.org/showthread.php?t=1075599"). It's loaded with Home Server software ideas. For a Linux torrent server I'd recommend Torrent Flux or Transmission.

I'd watch out for Zenoss though, it's a real hog for resources. If you need perfomance monitoring it works well, PanadoraFMS is another good option. If you only need fault monitoring, Nagios works great.

Well it depends on what you're monitoring... Large networks, or small.  Zenoss is really scalable, but if you're only monitoring 3 servers it may not be worth it :P

But torrentflux?  Transmission?  Deluge?  Really?

rtorrent spanks all of 'em, hands down.  Runs with very little footprint, and I've always had blazing speeds with it.  Torrentflux I felt way too disconnected from the processes, and each new torrent would spawn a new process... not a very good client.

---

