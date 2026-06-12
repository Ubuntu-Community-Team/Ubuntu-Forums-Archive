---
title: "what would you do if you had a server?"
date: 2008-01-15
forum: The Cafe
---

### Post by creamcheeze77 on 2008-01-15
Right now, i have a macbook pro laptop and a desktop which dual-boots ubuntu and windows.  However, i have enough spare parts lying around to build another computer, using a 1U server chassis and a 3.2ghz processor.  I also have about 10 500gb hard drives i could stick in there.  However, i don't really know what i'd do with such a server (it can't support a graphics card so there aren't really any other uses for it).  I mainly use my computers for music and movies.  Anyone have any ideas about what i could set up here? What would you do?

---

### Post by Lostincyberspace on 2008-01-15
You could set up a file server. for high quality music and movies.

---

### Post by Omnios on 2008-01-15
I was playing around with my new lappy and found I can play music that is on my old Pc. This might also work with videos freeing up some room on your other systems.

 Also my old pc has a 
tv tooner card am trying to figure out how to play tv a server and watch it remotely on the lappy. 

 Thinking about looking into being able to have it so I can remote download files to the server and also having it so the server can burn DVD's while I serf with the lappy.


 Dam I wish I had a 500G hard drive or two right now the biggest is a 160g in my lappy lol.

---

### Post by Æniad on 2008-01-15
A file server is probably what I'd do with it. But if you're tech savvy enough you could create a message board.

If you go with the file server I'd invest in a satellite ISP for better dl speed.

---

### Post by dgray_from_dc on 2008-01-15
[SIZE="5"][COLOR="Red"]I think I just crapped my pants![/COLOR][/SIZE]

If I were you, I would build a server with a RAID 5 array to store **_[COLOR="Red"][SIZE="6"]EVERYTHING!!!![/SIZE][/COLOR]_**



That's just me.  I have a lot of music, music vidoes, AMVs (Anime Music Videos), Movies etc.  All of which is becoming irreplaceable and I'm paranoid about data loss.  I'm currently trying to build a machine with a 4x250G array.

---

### Post by Hightide on 2008-01-15
oh I am so envious. You are spoilt for choice. what about a Gaming server!!

:lolflag:

---

### Post by bufsabre666 on 2008-01-15
it maybe just me but i thing dgray seems a little excitable

.... 

just a theory

---

### Post by prizrak on 2008-01-15
you could use it as a file server/Media PC. I am assuming it has some sort of a video out capability so you should be able to connect it to a TV even if you need to use an adapter.

---

### Post by dgray_from_dc on 2008-01-15
Sorry......

---

### Post by Joeb454 on 2008-01-15
I'd probably set it up as a file/media server as well...possibly a web server, depends if you wanted to host a webpage.

You could EVEN........do both!!!

---

### Post by creamcheeze77 on 2008-01-15
i was thinking of setting it up to stream movies and music to both computers.  unfortunatly since its a server it has no sound card and only a 8mb graphics card, so i cant do it directly.  anyone know how i'd do this? especially since i have two different operating systems

---

### Post by Joeb454 on 2008-01-15
I was under the impression that if you had a decent network card you wouldn't need a graphics card to stream movies.

I have proof of this because I have an old 1ghz 256 RAM PC, with only a built in Gfx card, and a 100mbps NIC. And it was running Windows Server...I used that to stream Movies to my laptop & to an Xbox 360 at the same time.

---

### Post by Omnios on 2008-01-15
Hi my laptop has Vista on it right now as I am stiff researching Ubuntu for it but found I could see the music files on the xp server and just click and play them on the laptop. This worked for music but not sure if it has the bandwidth for DVD's etc. So the laptop was playing the file from the server or rather just accessing the file and playing it on the lappy. 

 .

---

### Post by beercz on 2008-01-15
Use the server to back up your other machines - that's what I do.

My backup runs every day \\:D/

---

### Post by Christmas on 2008-01-15
Something like a message board or a website with Linux content. I have one (in my sig) and like working on it.

---

### Post by Dragonbite on 2008-01-16
Give it to me :mrgreen:
I'm in the process of setting up my home system and I am looking to set up a server for :
[LIST]
[*]Web server (with Mono so as to develop ASP.NET, which I use at work, and/or install Drupal and use Blogging technology for personal journals, image gallery for pics managemen, etc.)
[*]File server (to back up and store my files including multimedia and system's partition images). Having a central location which is accessible via Windows and Linux makes things MUCH easier.
[*]Email server (if/when I get broadband)
[*]Print server
[*]Gaming server (though I'm not a big game player, doesn't mean I can't play some)
[*]Virtual Machine server (one host OS and then all functions listed above in seperate images?)
[/LIST]

If you're brave you can also try an LTSP server (via Edubuntu is the easiest) and have the comuter(s) in the house boot over the network into it.  It's quite a learning experience (has been for me)

---

### Post by Johnsie on 2008-01-16
Oh... I'd make it either a world wide web server or a local intranet web server.


> sudo tasksel install lamp-server


That command will install the Apache web server with PHP and Mysql

Then you might also want to:
> sudo apt-get install phpmyadmin

> sudo apt-get install gproftpd

To install phpmyadmin (a cool browser based too for administering you servers mysql databases) and Gproftpd so you can upload files to your server using Protftpd.


Samba is also a good thing to install on there because it'll allow you to share files over your network. It's the file sharing what windows uses to it works cross platform. If you're using Samba make sure that you set the firewall settings properly so that people cannot access shared folders from outside your network.

If you're smart then you can hook the whole thing up to a domain name like [www.yourname.com](www.yourname.com). I do this in my house. I bought my domain off [http://nameroute.com](http://nameroute.com) and then used the free service at [http://zoneedit.com](http://zoneedit.com) to direct requests to my webservers ip.


**Things you might want to learn about or research:**
-Apache2 Web server
-Proftp
-PHP and Mysql
-Webserver security
-Samba
-IP Forwarding
-DNS

---

### Post by creamcheeze77 on 2008-01-16
thanks for all the responses guys.  i found that the chassis i have (it's a scrap one) is actually for a 1U server, and therefore has no room for hard drives, which makes things a little difficult.  i think i may try to build my own chassis, since having a central place to store everything seems like a really good idea, especially with three operating systems (linux, windows, and my mac).  i might also just run some sort of file-sharing server from my PC, since it's got room for 6 hard drives.  i'll let you guys know what i end up with, thanks again for the responses.

---

### Post by AndyCooll on 2008-01-16
> **creamcheeze77 said:**
> i was thinking of setting it up to stream movies and music to both computers.  unfortunatly since its a server it has no sound card and only a 8mb graphics card, so i cant do it directly.  anyone know how i'd do this? especially since i have two different operating systems

It doesn't need these to act as a media server, the computers on which you want to view the movies or play the music on are the ones that require the graphics and sound card.

At its most basic you can merely share the relevent folders on the server (using nfs or samba) and then mount that shared folder on your clients. In effect this is acting as a file server.

Alternatively you could set up a proper music server (e.g.MPD), but again its merely the clients that need the hardware.

Another purpose for a server is for downloading torrents, e.g using rTorrent or TorrentFlux.

:cool:

---

### Post by Kingsley on 2008-01-16
I would set up an FTP server to connect to from college whenever I feel like grabbing movies.

---

### Post by billgoldberg on 2008-01-16
10 500gb harddrives!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

You can store have the internet on there :p

A fileserver man, store all your files on there (music, video, backups). Start ripping those dvd's and share them in your network with the other pc's.

If you put in a cheap video card you could use it as media center.

Thinking about it, i have a spare partion and a computer that's on 24/7. I'll make a home network myself.

---

### Post by Omnios on 2008-01-16
Hi also found out if you can get a cheap TV tuner card you can set up Myth Tv and stream it to a client "laptop"

 
I am going to try setting this up after I finish researching installing K/Ubuntu for my laptop. "160G space issues"

 Crazy thing Vista is already at over 30G and theres not much installed

---

### Post by creamcheeze77 on 2008-01-16
yeah i tried vista for awhile and made like a 100gb partition, it was half full before i even installed anything
remotely downloading stuff from college is an absolutely fantastic idea
i took a look at my chassis and i think i can fit like 3 hard drives in there if i kinda cram them, with some liberal use of duct tape

---

### Post by arsenic23 on 2008-01-16
I can't beleive no one has mentioned [Torrentflux]("http://www.torrentflux.com/").

My server is mostly used for ftp and the above.

---

### Post by inversekinetix on 2008-01-17
i would put half my rom collection on it.

---

### Post by FuturePilot on 2008-01-17
Well, I would put my blog on it for one thing. Maybe setup my own email account as well. Maybe use it for ftp too.

---

### Post by SZF2001 on 2008-01-17
Wow, you just have ten five hundred gig drives lying around? I wanna be you.

Anyway, I'd make a simple picture that takes around 500 gigs on an upload. Just a simple website with the 500 gig picture and text saying "HEY DIS IS MY AWESOME PICTURE KEEP WAITING TO SEE HOW AWESOME IT IS".

---

### Post by allforcarrie on 2008-01-17
start a WOW server.

---

### Post by Visti on 2008-01-17
Media server and then slap LinuxMCE on top and you could connect thin clients to your televisions for media center goodness.

I'd probably make me a MUD server.. Or a regular file server.


Uh, and you could also do Network installs of distros with a neat fileserver.

---

### Post by mr.propre on 2008-01-17
First of. For home use I would not make a server of an old computer. Takes to much power, I would pick a pico-atx kind of server.

And the use:
Backup
Sharing
Lamp testing server
Maybe a few game severs.

---

### Post by PetePete on 2008-01-17
> **Omnios said:**
> 
 Also my old pc has a 
tv tooner card am trying to figure out how to play tv a server and watch it remotely on the lappy. 
.

sounds like an awsome idea, is this even possible?

---

### Post by Dragonbite on 2008-01-17
Virtual machine so you can go through trying Linux distros as often as you change your underwear! eww.... ! Maybe a little more often :lolflag:

---

### Post by afderrick on 2008-01-17
Okay, so my big suggestion has already been given of making it a file server.  This is actually what I want to do now, but unfortunately I don't have the $250 to put together a mini PC to store files.  You could also use it as an internet radio station, that hasn't been mentioned.  Connect to it from work and you can listen to all your music.

---

### Post by Dr Small on 2008-01-17
I have a server, so I'll tell you what I use it for :)

I have SSH setup on it, to remotely control every aspect of the system, via a terminal, with ProFTPd for transfering files to the server (over network) and using it as a fileserver (backup system) for important or big files, along with XAMPP as a webserver so all the FTP files can be viewed / downloaded via HTTP.

It works very well for my needs, and I am happy with it :)

Dr Small

---

### Post by PetePete on 2008-01-17
> **Dr Small said:**
> I have a server, so I'll tell you what I use it for :)

I have SSH setup on it, to remotely control every aspect of the system, via a terminal, with ProFTPd for transfering files to the server (over network) and using it as a fileserver (backup system) for important or big files, along with XAMPP as a webserver so all the FTP files can be viewed / downloaded via HTTP.

It works very well for my needs, and I am happy with it :)

Dr Small

just out of interest, why dont you use the sftp functionality of ssh to transfer files ?

---

### Post by Joeb454 on 2008-01-17
This is a good point actually.

Though I'm guessing the answer will be some bizarre function that ProFTPd provides that DrSmall uses :)

---

### Post by rustybronco on 2008-01-17
I have four, 2 proliant 1600's, 1 dl380, and as soon as I can pick it up a proliant 6000 with 4 xeon processors.
I use the dl380 as a file/media server, the others keep the floor from moving to much.

---

### Post by Omnios on 2008-01-17
> **PetePete said:**
> sounds like an awsome idea, is this even possible?

 Apparently there is a Myth tv backend server and also a Myth front end. From what I was told on another post you can stream from a lin box to another lin box but only stream PVR DVD's to win

---

### Post by PetePete on 2008-01-17
that'd be great, you could have TV anywhere in your house, all the portability of a laptop but without the hassle of setting up the arial and stuff.

---

### Post by getaboat on 2008-01-17
Mine's a crappy old computer with 2X80gb drives. 1 to be soon replaced by 500gb. + a USB external 500 Gb drive for back ups.  It's currently:

- A file server for sharing data around the house network.
- Print server (to be redone now I think I understand a bit more about CUPS)
- jinzora for shared music - pretty cool though the quality (MP3) isn't great.
- starting to organise the house photo collection to the server.
- WebCalendar host - that has ground to a halt because I can't get emails to work and the interface is a bit naff.

What I really want to do with it is be able to stream the recorded stuff off our Sky+ box so it can be watched from any PC on the house network - but a bit more research required.

What has become apparent though is that you don't get the benefit from a server in a multi user household unless it is on all the time.

---

### Post by Omnios on 2008-01-17
> **PetePete said:**
> sounds like an awsome idea, is this even possible?

> **getaboat said:**
> Mine's a crappy old computer with 2X80gb drives. 1 to be soon replaced by 500gb. + a USB external 500 Gb drive for back ups.  It's currently:

- A file server for sharing data around the house network.
- Print server (to be redone now I think I understand a bit more about CUPS)
- jinzora for shared music - pretty cool though the quality (MP3) isn't great.
- starting to organise the house photo collection to the server.
- WebCalendar host - that has ground to a halt because I can't get emails to work and the interface is a bit naff.

What I really want to do with it is be able to stream the recorded stuff off our Sky+ box so it can be watched from any PC on the house network - but a bit more research required.

What has become apparent though is that you don't get the benefit from a server in a multi user household unless it is on all the time.

 > a USB external 500 Gb drive for back ups.  It's currently:

 He he you might have just solved a partition problem. Can I through a 40G HD in a usb external case and use it for windows and linux backups? Idea is to use it for the backups as apposed to having it on a DEll ?:backup partition. Now If I can swap the dell restore to it I can free up 10G's.

---

### Post by Dr Small on 2008-01-17
> **Joeb454 said:**
> This is a good point actually.

Though I'm guessing the answer will be some bizarre function that ProFTPd provides that DrSmall uses :)
Well, I have never expirimented with sftp, but that is a good idea and concept.
I only used ProFTPd because I knew how to use it, and other Windows clients could transfer with via FireFTP and different clients.

Can you do this with sftp?

---

