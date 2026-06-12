---
title: "bittorrent server"
date: 2006-08-20
forum: Server Platforms
---

### Post by Thomas Bowie on 2006-08-20
I have an old K6-2/500 with 384mb ram, 120gb hdd, running 6.06 "server".  At the moment, all it is doing is running samba for filesharing/backup.  

I would like to set up a transparent bittorrent server, which all requests for bittorrent downloads are sent to, via my router.  

The machine can then download in the background, without the "desktop" machine(s) being on.  This would also get round the problem of not being able to open up router ports 6881-6885 for more than one machine, which is an annoyance.

If this is possible, how do I set up the graphical "client" machines, which run Ubuntu 6.06, Win98 and WinXP?

Thanks for any help,
Tom

---

### Post by it.henrik on 2006-08-20
you want to send all BT traffic initiated by one machine on your LAN to another machine on your LAN by routing the packets there, and then have that machine do something usefull with the BT packets?

I think it can be done .. but sounds quite complex and would involve a lot of "non standard solutions" :) 

(If im wrong then please informa me because I would love to know how this can be done)

If you want to initiate BT downloads from another machine then the one you are sitting on atm I would recommend something in the way of AZUREUS with its web-control-plugin. I dont remember the specific name of it but have a look at the descriptions of their plugins and you will know which one I mean.

Theres also the possibility to just DL the .torrent-files to a folder which you tell AZUREUS to keep an eye on. AZUREUS will then start downloading every torrent you put in that folder.

AZUREUS is a BT power tool.

---

### Post by Kurt` on 2006-08-20
I read your post over a few times, and I'm not sure I know exactly what you mean, but here goes...

You don't even need to install a "server" to do that. There are command-line bittorrent clients that you can install. SSH into your server, start up a "screen", wget the torrent file (or copy it across the network), start the bittorrent client, and then you can detach.

You can reattach later and bring the torrent client to the foreground to check on its progress.

Not sure what to recommend for a command-line client though. Maybe others have some recommendations.

---

### Post by jamerson on 2006-08-20
I will soon try to install torrentflux for this exact setup...

[www.torrentflux.com](www.torrentflux.com).

Have a look at it!

---

### Post by Thomas Bowie on 2006-08-21
had a look at torrentflux, looks great, might be the solution ive been looking for.

Found a debian package, i presume this is the one i should use...

Never installed apache before, so no idea how difficult it is, i'll try it all out sometime soon & keep people posted :)

Tom

---

### Post by jamerson on 2006-08-21
Found a debian package, did you?!

Please tell me where!

---

### Post by sinaen on 2006-08-22
> **jamerson said:**
> Found a debian package, did you?!

Please tell me where!
yeah me too...
i have a a**load of trouble installing torrentflux and btlauncurses and bittornado is bugging out all the time shutting down.. :(

do you have any means of installing ubuntu server? do you know what packages is installed at ubuntu server?

Edit: btw azureus has a http-server-client-plugin that you can use also :) (was that to tricky to understand.) if thats interesting. but for me? i dont have x installed on a server..:twisted:

---

### Post by sshetye on 2007-02-23
I know what you're getting at, I have a setup on my Windows XP machine which does what you're trying to do. So while I can't really offer you a Linux solution, here is my Windows based solution (MAYBE it benefits you if you dual boot).

My XP machine servers out files (Windows File Sharing, SMB in linux world) and also has a "writeable" shared drive. So any lan client can write a .torrent file there.

In the meantime, using srvany from the MS utils disk, I'm running uTorrent as a system service (aka daemon). uTorrent checks that folder every 60 seconds for a new torrent and start downloading it. After download is complete, uTorrent moves it to another folder which is again shared :) !!

So I'm using uTorrent to get most of my work. Anyway, after seeing Beryl, ubuntu's ease of setup and Windows Vista's retail price, I'm thinking of ditching XP's successors.

So I'm in your boat now trying to create the same functionality as my Windows machine. .... I'll post back how it goes :)

Cheers!
Sid

---

### Post by GoBieN on 2007-02-24
I use torrentflux, i installed it from a how-to here somewhere here on the forums (use the search ;)) and it works great, easy to use trough the browser with a nice interface !

---

### Post by esaym on 2007-02-25
Torrent flux is very easy to install.  It installed fineon ubuntu 6.06 lamp.  All you have to do is make a mysql database for it and then copy the directory over to a directory on your webserver.  See the readme in the source file

---

### Post by kjacks on 2007-02-25
I agree with the other posts that TorrentFlux is probably your best bet.  There is a great tutorial by Jon Peck on how to set it up.  If you already have  a server up and running just take the pieces you need.  

Here's the link I followed:

[http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html](http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html)

---

