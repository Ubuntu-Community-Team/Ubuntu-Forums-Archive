---
title: "Server Setup"
date: 2009-05-20
forum: Server Platforms
---

### Post by peekaboo on 2009-05-20
I'd like to use an old Pentium 2 (500 MHz), 512 MB of ram, computer as a home server and I need some hand holding.

I have one old 120 Gb IDE hard drive and another 250 Gb 4 year old IDE hard drive that I'd like to use in it.

1. Do I need to have both hard drives installed when I install the server OS?

2. Do I need (should I) to use LVM?

3. Should I partition the hard drives? What is a suggested structure?

I'd like to be able to do the following:

A. Create several directories (movies, pictures, software, documents, backups...)

B. Have some directories accessible to everyone and some accessible to me only

C. Have the server automatically backup directories on the network (once a week copy any new files I've added to my pictures directory on my main computer, once a month/week backup documents from my wife's computer...)

D. Be able to save files downloaded with my main computer directly to the server and/or have my torrent client run on the server so I can leave the server running and sharing torrents while my main computer is turned off.

Can someone guide me on how to set up my system?

Thanks

---

### Post by fatbotgw on 2009-05-20
You don't say which version you're using so I'm assuming 9.04...

Have you tried the Server Guide yet?

[9.04 Server Guide]("https://help.ubuntu.com/9.04/serverguide/C/index.html")

---

### Post by peekaboo on 2009-05-21
> **fatbotgw said:**
> You don't say which version you're using so I'm assuming 9.04...

Have you tried the Server Guide yet?

[9.04 Server Guide]("https://help.ubuntu.com/9.04/serverguide/C/index.html")

I'm using 9.04.
I did have a look at the server guide.
It does not mention whether LVM is for noobs like myself or if it will offer my proposed setup any advantages/disadvantages.

I was hoping for a response along the lines of:

1. no need to have both drives installed. you can add another hard drive later

2. LVM will offer no advantage to your setup and only complicate things. don't use it.

3. just do a guided install of the entire drive.

A. type XXXXX to create a directory in location XXXXX. type XXXXX to share it over the network.

B. type...


etc.

---

### Post by fatbotgw on 2009-05-21
> **peekaboo said:**
> I'd like to use an old Pentium 2 (500 MHz), 512 MB of ram, computer as a home server and I need some hand holding.

I have one old 120 Gb IDE hard drive and another 250 Gb 4 year old IDE hard drive that I'd like to use in it.

1. Do I need to have both hard drives installed when I install the server OS?

2. Do I need (should I) to use LVM?

3. Should I partition the hard drives? What is a suggested structure?

I'd like to be able to do the following:

A. Create several directories (movies, pictures, software, documents, backups...)

B. Have some directories accessible to everyone and some accessible to me only

C. Have the server automatically backup directories on the network (once a week copy any new files I've added to my pictures directory on my main computer, once a month/week backup documents from my wife's computer...)

D. Be able to save files downloaded with my main computer directly to the server and/or have my torrent client run on the server so I can leave the server running and sharing torrents while my main computer is turned off.

Can someone guide me on how to set up my system?

Thanks


I'll see what I can answer...

1)  No, all you need is the drive the OS will be installed on.  You can add as many drives as you want later.

2)  If you're going to use a RAID setup then I would use LVM with the RAID.  It will make things easier if you upgrade the size of you RAID drives.  If you're not going to use RAID then I wouldn't bother.  Other people might have different opinions though...

3)  When I built my server, I used an entire 80GB drive as my / drive and let the installer "auto-partition" it.  That was because I was installing a 2TB RAID array later for storage.  For ease of install, let the installer partition as it sees fit on the 120 and then use the 250 as a separate "storage only" drive.  Again, other's opinions will vary...

A/B)  Take a look at these for setting up a "private/public" LAN share through Samba:  [Part 1]("http://www.linuxjournal.com/article/10224"); [Part 2]("http://www.linuxjournal.com/article/10256"); [Part 3]("http://www.linuxjournal.com/article/10292"); [Part 4]("http://www.linuxjournal.com/article/10336")

C)  This one I don't know about...sorry.

D)  I use rtorrent and love it.  I used these to help me:  [howto-use-rtorrent-like-a-pro]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/")  &  [Rtorrent]("http://wiki.archlinux.org/index.php/Rtorrent")

I hope this helps you out...

---

### Post by ugm6hr on 2009-05-21
Not directly related, but I thought I'd offer some thoughts...

If you are still experimenting, consider FreeNAS as an easier alternative for your file server.  

Benefits:
1. Can install to a 256MB USB flash drive (as long as your computer will boot from USB), leaving the full HD capacity for storage.  You can just add HDs as you like later.  Partitioning: not an issue (none required).
2. Easy to install, and preconfigured for network storage.
3. Has Transmission BitTorrent preconfigured.
4. Samba shares can be configured to allow access by specific IP addresses.  Or you could use SSH for your personal (password protected secure) shares and NFS or Samba for all others.
5. It has Unison and Rsync; just set up a scheduled backup from each client computer (and ensure server is on when the event occurs).

See the link below for how I set it up.

---

### Post by Alekz_ on 2009-05-21
> **fatbotgw said:**
> I'll see what I can answer...

1)  No, all you need is the drive the OS will be installed on.  You can add as many drives as you want later.

2)  If you're going to use a RAID setup then I would use LVM with the RAID.  It will make things easier if you upgrade the size of you RAID drives.  If you're not going to use RAID then I wouldn't bother.  Other people might have different opinions though...

3)  When I built my server, I used an entire 80GB drive as my / drive and let the installer "auto-partition" it.  That was because I was installing a 2TB RAID array later for storage.  For ease of install, let the installer partition as it sees fit on the 120 and then use the 250 as a separate "storage only" drive.  Again, other's opinions will vary...

A/B)  Take a look at these for setting up a "private/public" LAN share through Samba:  [Part 1]("http://www.linuxjournal.com/article/10224"); [Part 2]("http://www.linuxjournal.com/article/10256"); [Part 3]("http://www.linuxjournal.com/article/10292"); [Part 4]("http://www.linuxjournal.com/article/10336")

C)  This one I don't know about...sorry.

D)  I use rtorrent and love it.  I used these to help me:  [howto-use-rtorrent-like-a-pro]("http://kmandla.wordpress.com/2007/05/02/howto-use-rtorrent-like-a-pro/")  &  [Rtorrent]("http://wiki.archlinux.org/index.php/Rtorrent")

I hope this helps you out...

Hi all! :)

Well.. Just some points...

...

3) I don't like to use a entire disk just for OS IF you'll use just one HD for OS and data! If so, I suggest to let about 25Gb for OS and you can use the free space for your /home or "/data"... But, as our friend said, there are lots of different opinions!

...

C) Use the `rsync` command (man rsync). It'll do exactly what you want!

One more point.. I don't think you'll need LVM! It's just unnecessary for a home server that probably won't have an 'array' set up.. Too much work for almost none benefits! :)

[]'s

---

### Post by hellarough on 2009-05-21
[Ubunut home server]("http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html")
[$80 Server in 45mins]("http://jonpeck.blogspot.com/2006/11/how-to-configure-80-fileserver-in-45.html")

Both of these tutorials are what I used to get my server up so I imagine they would suit your needs. The samba file shares are awesome because you can set users and access privileges for different 'shares' (directories); also, if you have a compatible printer then you can share that too. Torrentflux can manage all of your torrents so your personal machine isn't tied up with torrents and you can admin from your favorite browser. As for the backups I think you should look into rsync. Dont bother with LVM and as Alekz_ suggested I think you should restrict your install to a partition of about 25gb and use the rest of your space for your storage. 

I hope you have fun! (I havent been able to leave my server alone cause I am constantly looking for bits of functionality that I can add to it)

---

### Post by peekaboo on 2009-05-22
Thanks for the replies.
What do you guys think about [http://www.webmin.com/]("http://www.webmin.com/")?

---

### Post by lykwydchykyn on 2009-05-22
> **peekaboo said:**
> Thanks for the replies.
What do you guys think about [http://www.webmin.com/]("http://www.webmin.com/")?

Webmin is great; I use it all the time on all kinds of server applications.  I would still recommend being familiar with the config files (in many situations I've encountered, working with the config files is actually LESS confusing than working with webmin), but for quick point-and-click administration it's nice.

As for the drive setup, I would not mess with LVM personally, but I don't have a lot of experience with it.  I'm leery of software solutions to bind drives together into single volumes, I know in many cases if you lose one drive you end up losing the whole volume (so effectively both drives).  Don't know if that's the case with LVM so don't take my word as gospel.

How to partition kind of depends on the amount and distribution of your data.  You say you want some areas available to everyone, and some only to you.  I would recommend setting up the "homes" share in SAMBA then, and having one of your drives mounted to /home.  Then create a share for everyone to use and mount the other drive to that folder.

---

### Post by colau on 2009-05-22
> **fatbotgw said:**
> You don't say which version you're using so I'm assuming 9.04...

Have you tried the Server Guide yet?

[9.04 Server Guide]("https://help.ubuntu.com/9.04/serverguide/C/index.html")
Thanks for your link.

---

### Post by peekaboo on 2009-05-22
I tried FreeNas and it's pretty sweet but I thought I'd give Ubuntu another go.
I reinstalled the server (9.04) and installed Webmin so now I'm managing Samba from the web browser on my main (Windows 7 X64) computer.

When I installed Ubuntu, I did a guided install so there are no separate partitions for my data. I just created a folder (named "data") and created more folders within that folder.
I'm pretty sure I'll mess something up sooner or later so I'd like to keep the data separate and be able to reinstall the OS.

How do I now create a partition on my hard drive that I can move my data folder to?

Will I be able to see the partition automatically or do I have to create a folder on the system partition and somehow mount the data partition into that folder?

Thanks.

---

