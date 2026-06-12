---
title: "lost n00b making the switch"
date: 2005-07-04
forum: Server Platforms
---

### Post by ryanoliver on 2005-07-04
First off, I've had Ubuntu for about 2 weeks now, but haven't used it very much because I've been still attached to M$. So that brings my overall linux time to about... 2 weeks now. I like what I see, but it's definitely different than what I'm used to so I got a bunch of books to help a little.

Here's the story behind everything. I'm planning on attending school in the spring to become a programmer. So for now, I'm reading what I can and trying to learn C and then C++, and as many other languages as I can before I have to start classes (not that it's a bad thing at all). But I think everyone here already knows that I'll be creating a lot of code and programs and testing things out. Also the school I want  to attend is quite a ways away from here which is what brings up a few questions for me.

I've been reading about the various servers here on the forums and am interested in making one for myself. I have the extra parts lying around to do it too. But I want to know if I can have a server that I can store everything on and run things like phpbb and teamspeak on. Also what programs should I use to do this. I want to be able to ftp whatever I want to my server (code, pics, Linux ISOs, whatever), be able to host phpbb as well as my own websites since I've already learned XHTML, and possibly use Teamspeak to connect to my family back home too. If you haven't figured it out, I'm all about the free software which is why I'm getting away from M$. Also, I'm curious to try new things so I read about Ubuntu and took a big dive into it to learn, I think the best way to learn is try it myself. 

The server will mostly be for me, and give my family access via phpbb. I want to be able to ftp remotely and across my home network. There would be about a dozen people that would access my phpbb for a long while and I wouldn't make too many sites that would require much traffic either. But I want to comfortable with a server while there is lower traffic so I can upgrade the server when I need to.

To recap all of this: I'm new, yet eager to learn; don't know what programs to use; want a server that can do a lot while not slowing down my ftp at all; and don't even know if it all is possible. I've also downloaded Trustix linux designed for servers, but was curious how that would be and if Ubuntu would be a better choice.

---

### Post by christooss on 2005-07-04
This will not anwser you question but you will know what to instal

[http://ubuntuguide.org/#apachehttpserver](http://ubuntuguide.org/#apachehttpserver)

You have to install apache+mysql and php for forums and pages to work.

about ftp server go down the ubuntuguide. There is a section ftp server

For more questions return to this forum :)

---

### Post by christooss on 2005-07-04
Ofcourse when you install Ubuntu to your sistem don't go for a normal installation. At start choose server installation.

Than when you come to command propt login and than install everything you want includding apache etc...

---

### Post by ryanoliver on 2005-07-04
I've read quite a bit aobut things like samba and other programs, but because I'm so new to linux I don't know what they're used for. Do they really matter right now regarding to what I'm trying to do? Will Apache, mysql, and php give me everything that I need to do what I want then?

---

### Post by ryanoliver on 2005-07-04
I read how to create a streaming media server, ftp server, and an image gallery server form ubuntuguide.org. Do I have to use filezilla to ftp to an ubuntu server if I'm using a windows system? Now I'm curious if one server can do all of these things, or do I need to make seperate partitions for each? Could I make it that I have access to one partition of my own while everyone else has access to all of the other partitions? Each time I read something new I get more questions about things. I would rather ask to make sure before I destroy something. But I also want to find out what all I can do like other programmers. I shouldn't reinvent the wheel, but if I do I will have a better udnerstanding of what I can use it for.

---

### Post by christooss on 2005-07-04
[QUOTE=ryanoliver]I read how to create a streaming media server, ftp server, and an image gallery server form ubuntuguide.org. Do I have to use filezilla to ftp to an ubuntu server if I'm using a windows system? Now I'm curious if one server can do all of these things, or do I need to make seperate partitions for each? Could I make it that I have access to one partition of my own while everyone else has access to all of the other partitions? Each time I read something new I get more questions about things. I would rather ask to make sure before I destroy something. But I also want to find out what all I can do like other programmers. I shouldn't reinvent the wheel, but if I do I will have a better udnerstanding of what I can use it for.[/QUOTE]
 You can have all this installed on same sstem. but its good if you put every thing on differeent partitions. Why? If One thing goes bad all others still remains untuched.

You should lurn about partitioning bfor installing things.

about access use google:
chmod tutorial

and wait for someone else to anwser this thread.

---

### Post by LordHunter317 on 2005-07-04
[QUOTE=ryanoliver. Do I have to use filezilla to ftp to an ubuntu server if I'm using a windows system?[/quote]You can use any FTP server you want.

>  Now I'm curious if one server can do all of these things, or do I need to make seperate partitions for each?One installation can run multiple server daemons (services in the Windows world).  You don't need multiple partitions and shouldn't create them unless you know exactly what you're doing.  And for a home server, the value is somewhat debatable. 

> I would rather ask to make sure before I destroy something.This is good.  Part of your problem is I don't think you 100% know what you want your computer to be able to do.  The only clear things I saw were a phpbb forum and teamspeak, and the ability to access your files.  

For phpbb, you'll need to install Apache 2,  MySQL 4.1 or PostgreSQL 8.0, and PHP4 (including libapache2-mod-php4).

For teamspeak, I don't know.

For acccessing your files, I strongly recommend you don't use FTP.  It's a crap protocol that's largely fallen into disuse.  Install SSH and use SFTP (which has the advantage of being encrypted), or use Samba and windows file sharing.

---

### Post by ryanoliver on 2005-07-04
I've been exposed to partitions for several years now. Various RAID configurations is a little new to me, but RAID if I remember correctly originated in servers and was released to the rest of the general public. You are right though, I'm not 100% sure what I want my server to do. But I -do- know that I don't have many things to save on the server except some -very- small snippets of code and some different distro ISOs I got using bittorrent. So I would rather learn all I can about it and experiment with it now while I won't lose too much information (not that I wouldn't try puting in RAID or at lest use an external HDD to back it all up) so when I want to implement a more serious server I will be experienced with it and have a better idea of what I truly need. 

I have five hard drives, a mobo, a decent agp card, and a network card just liying around the area here that I would rather see put to use than just waste space. Also the information wouldn't be of any sensative matter but I would like to experiment on security for future use and if I lose any of it, I have it backed up already. I first learned about building computers because one of mine got hit by lightning and was fried. My family laughed at me (i was about 8 at the time) when I started to take it apart because it didn't work anymore. Now they all call me and ask me to fix their computers when they break because I wasn't afraid to dive in with a little guidence.

---

### Post by Belarios on 2005-07-04
Getting all that stuff up and working will take some tinkering, but won't be all that tough.  What takes real finesse is making it as secure and safe as possibe.  That takes alot of work.

Good partitioning falls into that second category.  You could put the whole thing on one partition on one drive and it will work just fine.  Your one or two concurrent users won't know the difference.  But if you separate it all out the way it's designed to be, it will be less prone to attack, easier to restore if some part gets messed up, and will provide better performance when you move to a large number of users.

Read up on the Filesystem Hierarchy Standard for Unix style operating systems. [http://www.pathname.com/fhs](http://www.pathname.com/fhs)

Basically a. you separate out things that change often from things that don't; b. separate things that general users have access to from things that they don't; c. sometimes you'll separate out the lowest level things that you need to get your system running from all the complicated higher level things that can get mucked up; d. organize things in accordance with your backup and disaster recovery strategy; e. balance the amount of wasted space and extra hardware used with the amount of security that a particular setup provides.

It sounds like you're gonna have fun with it.  Jump in and start learning.  Don't expect this first setup to be the one you want in a month.  Once you get everything installed and figure out how it all works, you'll make a real plan, backup all your data, and install it all from scratch.  As long as it's just a testbed and not mission critical there's nothing to be worried about.  Enjoy.

---

### Post by Belarios on 2005-07-04
Regarding FTP and Samba...

This comes down to what network protocols you want to use to manipulate files across the network.

Samba is an open-source implementation of Microsoft's SMB network file system.  If you're mostly serving Windows machines, it may be the way to go because Windows loves it, and Microsoft provides much less integration and support for anything that isn't THEIR way.  Since Samba is a reverse engineered version of Microsoft super secret SMB code, it's not as fast as true SMB Windows to Windows communication, but it's pretty darn close.  I believe the default Ubuntu install has a Samba client built in to let you access Windows machines from Ubuntu, but if you want Ubuntu to act as a server to other machines you have to install the Samba server.

FTP is an old system for serving files, and has some security problems, but it's effective and fast.  You run an FTP server on your Ubuntu machine like proFTP for example, and then you run an FTP client on your other machines.  I use Filezilla as my FTP client, but it's a personal choice.  If you closed off FTP to the internet and just used it on your local network, it'd be relatively safe, but still adds some risk to your system.

NFS is the Unix-style network file system, and since the new Mac is Unix based, you could use it between Linux and Mac machines but since Windows doesn't do NFS, almost no one uses it.

For my simple home network I use WebDav.  It's an emerging standard that uses a web server (like apache) to do the work instead of running its own server software.  It has some rough edges, and the Windows support isn't nearly as transparent as Samba, but it's getting better.  It's open source, it's built from the ground up to be used over the internet rather than local networks, and it's slowly gaining acceptance.

Do what I did and go ahead and install Samba server, install an FTP server, install WebDav into your Apache server.  Figure out how to configure all three.  Access all three from your windows machine.  See for yourself the limitations and annoyances of each.  Then choose for yourself.  Then become an expert in hardening the security of the ones you chose to use.  Come on...I promise...it'll be fun!

---

### Post by LordHunter317 on 2005-07-04
[QUOTE=ryanoliver]I've been exposed to partitions for several years now. Various RAID configurations is a little new to me, but RAID if I remember correctly originated in servers and was released to the rest of the general public.[/quote]It's been available in high-end workstations forever.  I don't see it's relevance here though.

>  You are right though, I'm not 100% sure what I want my server to do.You need to figure this out first.

> (not that I wouldn't try puting in RAID or at lest use an external HDD to back it all up)RAID is not a backup solution.

[quote=Belarios]But if you separate it all out the way it's designed to be, it will be less prone to attack,[/quote]No.

>  easier to restore if some part gets messed up,Situationally dependent.

>  and will provide better performance when you move to a large number of users.Situationally dependent.  It could eaisly provide less performance.

> Since Samba is a reverse engineered version of Microsoft super secret SMB code, it's not as fast as true SMB Windows to Windows communication, but it's pretty darn closeIt's umm, just as fast, generally.  The different on most hardware is negligible.

> NFS is the Unix-style network file system, and since the new Mac is Unix based, you could use it between Linux and Mac machines but since Windows doesn't do NFS, almost no one uses it.NFS is crap and the Linux NFS implmentation is unreliable at best, dangerous at worse.

> It's an emerging standard that uses a web server (like apache) to do the work instead of running its own server software. WebDAV is nice, but has major security issues on Linux, at least if you serve via apache.  Being stuck with everything owned by the Apache user isn't a good thing.

---

### Post by Belarios on 2005-07-04
Unsubstantiated attacks.  Ho-hum.  Welcome to the internet.

Now why don't you post some useful information and constructive advice for this fellow instead of wasting our bandwidth?

---

