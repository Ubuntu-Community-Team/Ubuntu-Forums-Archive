---
title: "Home Server Possibility"
date: 2008-02-05
forum: Server Platforms
---

### Post by SMix on 2008-02-05
Ok so I don't necessarily want an answer to how to do all the following things, but more so to see if this is possible and makes sense.  Basically I am looking to setup a Home Server.  Until the Ubuntu Home Server project is finished I will have to dive into the technical aspect of it all and setup an Ubuntu Server (7.10) how I want it to work.  Honestly I have been an avid user of Windows, but have learned basics in Linux and played with Linux a lot lately to expand my horizons in the computing field.  I won't lie, Windows Home Server (WHS) was a great product for me.  My trial is over though and I either have to spoon out the $$ or find an alternative.  I am leaning toward an alternative since I don't feel like paying Bill Gates.  So here is my setup:

2 Vista Desktops (Soon to be XP Dark Edition), 1 Mac Desktop, 1 Vista Laptop (Tablet), XBOX (Running XBMC for media sharing), DSL internet running into Netgear 4Port Wireless G, Netgear 16Port Switch, Linksys 4Port Wireless B, and Server System.  May be adding one more system in the kitchen running gOS for the basics - mostly just internet.

What I want to achieve out of my server:

1. File Server - basically a storage system that can use all 3 250GB drives I have.  Also want to be able to mount these shares as drives on my desktops.  IE - Software folder mounted as G: on desktops.  If I am correct LVM is basically the same idea as WHS was using where it would take multiple drives and show it as one big drive.  This would also allow the removal and addition of hard drives w/o having to manually move all the data?

2. Backup Server - server will backup all systems on the network at set times.  Also compression on those backups to save space.

3. Media Server - want to have some service running that basically will show up like iTunes shared libraries.  That way the server music, movies, pics will show up in iTunes/WindowsMedia/Etc

4. Remote Access - want to be able to access the server remotely.  Make changes, remote desktop, that sort of thing.

5. FTP Server - I want the same idea like an FTP server, but not actually an FTP server.  WHS had basically has a web access page that would show the shares on the server that I allowed them to see based off a username given to them to login with.  So I want to have the same sort of thing, with a login page, and then access to certain files/folders based off permissions of that username.

6. Download/Torrent - want to have a web accessible management for downloading torrents/monitor torrents downloading.  I'm guessing this would just be uTorrent with webui running.  Also want to have a download manager that will allow me to web access and be able to say add a link to a download and it will just download for me.  Basically like remote access to add/remove/manage torrents and downloads.

7. Printer Server - I want to be able to have the server offer up the share to all the printers on the network and allow anyone to print to any printer w/o any complications of drivers etc.  Drop down and choose which printer.  There are currently only 2 - 1 Laser/1 Inkjet.

I think that is about it.  So like I said, any links or information that could help is greatly appreciated.  Overall I just want to be sure I'm not going to waste all the time and effort that I put into trying to get this up and running within the next 28 days before my WHS beta stops working on me.  Thanks!

---

### Post by gaten on 2008-02-06
I don't have experience with everything you want to do, but here are my suggestions for those that I do know:

>  1. File Server
Samba is your friend. It will look just like Windows shares to all your other PCs (although I don't know about Vista, i've heard bad rumors about it).

>  4. Remote Access
Look into FreeNX. I've been using it for a couple weeks now and am throughly impressed. You will simply install the server on your home server, and the client software to all your other computers (client software comes for Linux, Windows and Mac). If you don't want something graphical, SSH works great (which is what FreeNX uses anyway).

As far as the rest go, I'm sure you can find some FOSS solution, I simply don't know them off-hand.

---

### Post by AndyCooll on 2008-02-06
> 1. File Server - basically a storage system that can use all 3 250GB drives I have.  Also want to be able to mount these shares as drives on my desktops.  IE - Software folder mounted as G: on desktops.  If I am correct LVM is basically the same idea as WHS was using where it would take multiple drives and show it as one big drive.  This would also allow the removal and addition of hard drives w/o having to manually move all the data?
This is easily possible. I use LVM on my server. As mentioned Samba is the way to go for accessing using Windows PC's

> 2. Backup Server - server will backup all systems on the network at set times.  Also compression on those backups to save space.
Rsync is a standard tool for Linux (and there are plenty of other choices too)

> 3. Media Server - want to have some service running that basically will show up like iTunes shared libraries.  That way the server music, movies, pics will show up in iTunes/WindowsMedia/Etc
Again you have lots of choices, from simply sharing the folders through to MythTV, Music Player Daemon, and so forth.

> 4. Remote Access - want to be able to access the server remotely.  Make changes, remote desktop, that sort of thing.
SSH, VNC etc are readily available.

> 5. FTP Server - I want the same idea like an FTP server, but not actually an FTP server.  WHS had basically has a web access page that would show the shares on the server that I allowed them to see based off a username given to them to login with.  So I want to have the same sort of thing, with a login page, and then access to certain files/folders based off permissions of that username.
Not sure about this since I've never looked at this aspect. However FTP server apps and their variations are aplenty

> 6. Download/Torrent - want to have a web accessible management for downloading torrents/monitor torrents downloading.  I'm guessing this would just be uTorrent with webui running.  Also want to have a download manager that will allow me to web access and be able to say add a link to a download and it will just download for me.  Basically like remote access to add/remove/manage torrents and downloads.
Or you could look at TorrentFlux.

> 7. Printer Server - I want to be able to have the server offer up the share to all the printers on the network and allow anyone to print to any printer w/o any complications of drivers etc.  Drop down and choose which printer.  There are currently only 2 - 1 Laser/1 Inkjet.Thanks!
CUPS can manage all this for you. Add printer, share it, setup Samba to allow printer access. Done

Here's a useful link: [ Useful Links on Servers, System Administration, and Security]("http://ubuntuforums.org/showthread.php?t=681267") which is one of the stickies in our own [Servers & Security forum]("http://ubuntuforums.org/forumdisplay.php?f=7").

:cool:

---

### Post by SMix on 2008-02-07
Awesome.  Thanks much for the ideas and the links.  I will definitely be sure to check into all this.  I actually have a spare system laying around that I ended up installing the server to already.  I must say WebMin really brings Ubuntu Server into the realm of ease as WHS.  It's not all graphical, but thats Ok since I'm the only one who needs to understand it.  I haven't quite figured out the remote access and all but I'm working on it.  

Another question that came up in reading all this, I mentioned Backups.  Is there anyway to do something like WHS does where they actually have a restore disk you can put into a PC that has completely crapped out and it will find the server, let you choose the backup, and then it will go to work? I find this useful as I will often 6 months or so re-install my primary computer so as to clean out loose ends completely, and get rid of any crap that builds up in my PC, and god forbid any virii etc.  WHS basically lets me setup my PC, install all my software, make my tweaks and customizations, create that backup, and now I basically have a clean install image to re-install my system to perfect everytime without the hassle of going through everything.  This may be getting off topic but does something like this exist for Linux? or possibly in the works?

---

