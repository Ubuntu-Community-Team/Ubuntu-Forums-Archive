---
title: "Why make a server? And what to do with it?"
date: 2009-10-05
forum: Server Platforms
---

### Post by ready4thebreak on 2009-10-05
I honestly have no intentions other then curiosity and exploration. I'm currently studying to become an Electrical Engineer, but I think I'd rather work with a more hands-on experience like being an IT or something. 

I recently installed Ubuntu server on a desktop that my job was getting rid that has more than moderate specs, so I figured I would take a dive and learn how to setup a network and what to use it for. I have a few computers throughout my house connected to my network and a Lacie NAS Drive. 

I really don't know what to do with the server and I was fairly frozen when all I saw was a command line after my install. I looked at the Server Guide thread(and I also have the Official Ubuntu Guide that Canonical makes) and it really doesn't say much. I'm just trying to find any kind of info on any possible practical uses, possible projects or just things to learn about using a server.

Help of ANY kind would be most greatly appreciated.

---

### Post by HermanAB on 2009-10-05
Linux is Linux is Linux...  It really doesn't matter much whether you run the server version or the desktop version.  

In general, the server version is meant for use when a machine is sitting in a dank corner of a data centre and doesn't have a screen, keyboard or mouse connected to it, and your only access is via SSH from another machine.

If you do have a screen etc connected, then do yourself a favour and run the desktop version.

---

### Post by ready4thebreak on 2009-10-05
Well if I access it via SSH then what would I be accessing? That doesn't seem to make much sense. There must be something to do on the actual computer itself...

---

### Post by marshmallow1304 on 2009-10-05
You would use server edition for running services (e.g. mail server, web server, ssh server, etc.) on a machine where a GUI would be unnecessary or if you're wanting to learn command line.  If these apply, take a look at the [Ubuntu Server Guide]("https://help.ubuntu.com/9.04/serverguide/C/index.html") for setting up common services.

If neither of those applies, install a GUI by entering
```
sudo apt-get install ubuntu-desktop
```
then entering your password.


> Well if I access it via SSH then what would I be accessing?
You would be accessing the command line, just as you see it now.

---

### Post by lykwydchykyn on 2009-10-05
> **ready4thebreak said:**
> Well if I access it via SSH then what would I be accessing? That doesn't seem to make much sense. There must be something to do on the actual computer itself...

A "server" by definition is a machine running network services.  Typically you aren't interacting with the machine directly but rather accessing its services through your clients/workstation/desktop (whatever you want to call it).

As for what services you could run, take your pick.  I have one at home that does all the following:

 - web server (we have a wiki)
 - file server
 - print server
 - scan server (only works with Linux clients)
 - DNS (so I can access other computers on the network by name).
 - Web filter/proxy
 - remote access via ssh (so I can access things at home from work)
 - dictionary server

I think that's it.  There are all kinds of services you can run, but telling you which ones would be useful for you is a bit difficult; it's like asking what you should grow in your garden.

---

### Post by dragos2 on 2009-10-06
> **lykwydchykyn said:**
> A "server" by definition is a machine running network services.  Typically you aren't interacting with the machine directly but rather accessing its services through your clients/workstation/desktop (whatever you want to call it).

As for what services you could run, take your pick.  I have one at home that does all the following:

 - web server (we have a wiki)
 - file server
 - print server
 - scan server (only works with Linux clients)
 - DNS (so I can access other computers on the network by name).
 - Web filter/proxy
 - remote access via ssh (so I can access things at home from work)
 - dictionary server

I think that's it.  There are all kinds of services you can run, but telling you which ones would be useful for you is a bit difficult; it's like asking what you should grow in your garden.

maybe mail server is missing :)

The OP needs to read some books on Ubuntu or Linux in general.

---

### Post by Dzingis on 2009-10-06
Try Webmin or even eBox.

These two make administration much easier.

---

### Post by Lars Noodén on 2009-10-06
Computers are a tool to be **used in support of an activity**.  What do you actually want to do?  Then we can figure out how the server fits in.   

> **ready4thebreak said:**
> Well if I access it via SSH then what would I be accessing? That doesn't seem to make much sense. There must be something to do on the actual computer itself...

You would be accessing the user interface known as the shell.  Don't let people fool you into calling it the 'command line' or you will never master it.  It is scripting and only a little different from other types of programming.  

Herman AB had a good point.  To paraphrase, the linux systems are all the same except for the packages that have been added, removed or re-configured.

Linux is modular, like Lego blocks, and so some of the pieces below include other pieces that can be added, removed, or replaced.  

**Some choices for server activities**:

[LIST]
[*] Stream Audio or Video / make a juke box: [Icecast]("http://Icecast.org")
[*] File Sharing aka NAS: [Samba]("http://us2.samba.org/samba/") or [OpenAFS]("http://openafs.org/")
[*] VoIP gateway and/or PBX: [Asterisk]("http://www.asterisk.or/")
[*] Web Server (SSL, SSI, CSS): Apache2, Lighttp, [nginx]("http://nginx.net/")
[*] Terminal Server: LTSP, K12LTSP, Skolelinux
[*] CRM: Lenya and others
[*] Groupware: [LIST]
[*] [Kolab](http://www.kolab.org/)
[*] [Citadel](http://www.citadel.org/)
[*] [OpenGroupware](http://www.opengroupware.org/)
[/LIST]
[*] Calendar only:[LIST]
[*] [Bedework](http://www.bedework.org/)
[*] [Darwin CalendarServer](http://trac.calendarserver.org/)
[/LIST]
[*] Mailing lists with archives: Mailman
[*] Document management:[LIST]
[*] [O3Spaces](http://o3spaces.org/)
[*] [Lenya](http://lenya.apache.org/)
[*] [SugardCRM](http://www.sugarforge.org/content/open-source/)
[*] [Alfresco](http://www.alfresco.com/products/)
[*] [Main pyrus](http://www.mainpyrus.org/)
[*] [Nuxeo](http://www.nuxeo.com/en/)
[/LIST]   
[*] Bug tracking / ticketing system [LIST]
[*] [RT](http://www.bestpractical.com/rt/)
[*] [Trac](http://trac.edgewall.org/)
[*] [Roundup](http://roundup.sourceforge.net/)
[*] [OTRS](http://otrs.org/)
[*] [Bugzilla](http://www.bugzilla.org/)
[/LIST]
[*] Software development / version control:[LIST]
[*] [GIT](http://git-scm.com/)
[*] [Subversion (svn)](http://subversion.tigris.org/)
[*] [Bazaar (bzr)](http://bazaar-vcs.org/en/)
[*] [Mercurial(Hg)](http://mercurial.selenic.com/wiki/)
[/LIST]
[*] Integrated Library System:[LIST]
[*] [Koha](http://www.koha.org/)
[*] [Evergreen](http://www.open-ils.org/)
[*] [Greenstone](http://www.greenstone.org/cgi-bin/library)
[/LIST]
[*] Electronic Health Records:[LIST]
[*] [WorldVistA Astronaut Auto-Installer](http://sourceforge.net/projects/worldvistaautoi/)
[*] [Open EMR](http://www.oemr.org/)
[*] [WorldVistA](http://worldvista.org/)
[/LIST]
[*] Web-mail: [RoundCube](http://roundcube.net/)
[*] Enterprise Resource Planning: [LIST]
[*] [OpenERP](http://www.openerp.com/)
[*] [Pupesoft](http://www.devlab.fi/pupesoft)
[/LIST]
[*] Various webshop and E-business tools
[/LIST]

Obviously, there's much, much more.  Say your interests and there's probably a way to get the computer to be an advantage.  

If you're looking for disadvantages, say your grades are too high, then install a MOO and share it with your classmates around the world...

---

### Post by NJC on 2009-10-06
I installed Ubuntu Server on a headless Dell in the crawlspace. Mostly because it was interesting, but also to have file redundancy and protection from theft. 

Ubuntu server was a breeze to setup. And do use a static IP on the server to avoid SSH login problems. Using "adduser" was also easy to setup, although setting file permissions might be trickier depending on your needs.

---

### Post by darksideforge on 2009-10-06
> **Lars Noodén said:**
> Computers are a tool to be **used in support of an activity**.  What do you actually want to do?  Then we can figure out how the server fits in.   

Obviously, there's much, much more.  Say your interests and there's probably a way to get the computer to be an advantage.  

If you're looking for disadvantages, say your grades are too high, then install a MOO and share it with your classmates around the world...

How do I give beans for such an AWESOME post?!?! This is probably the best description I've ever seen. Seriously. Kudos, Lars!

---

### Post by fela on 2009-10-06
> **HermanAB said:**
> Linux is Linux is Linux...  It really doesn't matter much whether you run the server version or the desktop version.

+1, and I love how Linux is like that. Why should I have to get a different version if I want multi user support? (talking about windows desktop vs. server editions)  

> In general, the server version is meant for use when a machine is sitting in a dank corner of a data centre and doesn't have a screen, keyboard or mouse connected to it, and your only access is via SSH from another machine.

Like mine :) If you call my dark room a data centre anyway :)

> If you do have a screen etc connected, then do yourself a favour and run the desktop version.

Unless you have my lovely graphics card with its delicious 1280x1024 framebuffer that is :)

Serious reply: yes, you should have a GUI if you have a screen. That's the way it is, IMO. My server runs headless, keyboardless, mouse? Since when did anyone connect a mouse to a server :)

---

### Post by Lucky. on 2009-10-06
Lars hit it right on the head, but some newbies to servers don't even know what they want to do.  They just want to explore and see their options.

Here's my best story about servers, if you care to read a novel.

In my early days of computing, servers seemed so awesome.  There was this magical thing about them.  Movies and idiotic IT managers I consorted with made them out to be super powerhouses with tons of memory, hard drive space, and processing power.  If only I could get my hands on a server, all of my video games would load ultra fast!

The first time I saw a server, I was disappointed.  It was some old piece of junk computer sitting dusty in the corner of a room.  There were no crazy flashing lights.  It didn't play Global Thermonuclear War.  It wasn't building the next Pixar CGI movie.  What did it do?  It just sat there and let people save files on its network drive.

Later I got my hands on Windows Server 2000.  Woohoo!  Perhaps if I ran this on my home computer, I'd get good at server stuff!  Yay!

I installed it on my desktop computer.  It ran slow, and the security settings made it nearly impossible to do anything on the Internet out of the box. Most of my games and software didn't work on the OS period.

Wow.

Later I scoped out some servers at work, and noticed they were all outdated.  I would never dream of using them for anything decent as a desktop computer, but they worked great to share files with everyone on a shared network drive.  I was beginning to clue in that super duper power servers are few and far between.  People simply don't need them.  Furthermore, servers are all about stability, so they can't be super duper.  You plug a server in, set it up, and leave it on 24/7 for 5 years or more!  You don't mess around upgrading nonstop making it faster and faster.  You get a nice fast one, and let it age into "slowness" for the next few years before it's nearly only its last legs.  Then you replace it.

What was the point of servers though? I could use Windows 98 or XP to share my files over a network.  Why buy Windows Server to share files if Windows XP could do it?  What was the point?

I got married, and my wife and I wanted to share some files on our home network (finances, photo albums, music).  At first I used Windows XP to share my files and printer from my desktop computer.  It was quick and easy.  The problem was that now I had to leave my computer on 24/7 for her to get her files.  That's more annoying than you think.  Playing some game that crashed my machine?  Wife would complain that her MP3s stopped playing.  Want to upgrade that video card?  Wife would complain that she needed to print something.  Want to take my computer to a friend's house to LAN?  Wife wanted to do some photo editing that night.  Want to format my computer?  Wife needed to reconnect to the new network share and printer.  Frustrating.

I was a Computer Science student...so I was reformatting every semester after installing dozens of crap software for classes.  This annoyed the heck of out my wife who kept losing her access to the files and the printer.  I didn't want to put the files on her computer because she just wasn't that computer savvy.  I wanted to protect them, and be able to back them up easily.

How could I make sure the files and printer were available to both my wife and I all the time, without the hassle of re-sharing stuff every time I reformatted?

A server.  That's how.

Even though Windows XP seemed like it would do a fine job of sharing files and a printer, I grabbed one of my old computers, and put Windows Server 2003 on it.  I shared the files and the printer through the server.  It worked fine, but sheesh, it was dreadfully slow on my old machine!  Hence I tried out a Linux server, which ran considerably faster.

After working with the server for a good amount of time, I decided I wanted to try my hand at web development.  I paid for web hosting, but I got sick of uploading and downloading files nonstop over the net.  It would be faster if I just had my own private web server to develop and test stuff on...then later upload the finished product to the real web server online.  I learned how to add web server software (Apache) to my existing home server sitting in my house.

Later I decided "Hmm, I have a lot of important information on this server.  I should research some form of decent backup."  Now I'm looking into encryption and rsync to back my data up with.

After you've had a taste of what a server can do, things keep coming to mind.  As someone else mentioned earlier, at some point I wanted to be able to access the stuff on my home server from work, or other people's houses.  I researched SSH for remote access.  This prompted me to study security.  The next thing you know, I was looking around at my IT department at work thinking "Gee I could probably replace some of these servers and machines with Linux...it would save us a ton of money."

...and now Linux servers are exciting to me.  I keep thinking of things to add, work on, and improve.  My home server does much more than I originally intended it to do.

The eye opener of all of this was the fact that (again like somebody said), Linux is Linux.  Microsoft makes a myriad of different operating systems for servers and desktops.  Multiple flavors of XP, Vista, and Windows 7.  They have a standard server edition, an enterprise server edition, a web server edition, etc.  What's the difference between all of these?  A few configuration settings, and a bunch of restrictions on what you can install and do.  Windows XP works great for sharing files at home...but I think only 5 people can connect at the same time.  Why 5?  No reason other than making money.  Trust me, if my Pentium III server at work with 1 GB can handle 50 people connecting to it, my quad core with 4GB at home can handle more than 5 people.  Yet Windows restricts you unless you pay money for literally a couple of bits being flipped.

Back in the day it made sense that certain software didn't run on certain versions of Windows (since they were designed differently).  Now they're almost all designed the same, but you end up paying out the wazoo again for the right version which allows some software to be installed and doesn't allow other stuff.  Try running SQL Server Standard on Windows XP.  It should work just fine, but Microsoft gives you an error message that says "Nope, you can't install it on here."  Just like the 5 max connections thing.  You're paying money for somebody to change a couple of settings to allow this or that.

In comparison?  Linux is Linux.  You can download a desktop version of Linux and make it into a server by simply installing server software on it...no extra money or licensing.  Likewise, you can download the server version of Linux and install all of the desktop stuff you like.  The server edition is simply stripped down with no desktop junk in order to save memory and processor cycles.  In fact if the command line scares you at first, go ahead and run Ubuntu Desktop on your server instead...then just add the extra server stuff you want.  A lot more people are doing this nowadays (I've found a lot more graphical tutorials lately).  You probably don't even have to install anything extra on Ubuntu Desktop to simply share files or a printer.  But if you do, it's free.

There is a bad part to all of this.  IT TAKES TIME.  Everything is different than Windows, and a lot of things are broken or incompatible with your hardware in Linux.  It takes tweak upon tweak upon obscure tweak to get things running.  There's always a few people that it works perfectly for, and I'm happy for them.  Then there's always the expert group that can get anything working.  Good for them.  Chances are though, you'll stumble on tough times getting things working the exact way you wanted them.  In Windows?  Share some files and walk away.  In Linux?  Ooh...yeah, your Windows machines might not see the server in Network Neighborhood without extra work.  Or maybe the security isn't set right...you can only read, but not write files, etc.  And in order to change those settings, you'd better learn how to get root access (the "sudo" command or enable a root account).  Also you need to find that config file to edit, which is big, arcane, and stuck in a strange file hierarchy you're not familiar with yet.  Asking for help gets you a dozen people telling or arguing to you how to do it differently (which is good for freedom and choice, but bad for efficiency).  The explanations from the community probably expect that you understand some basics...which you don't.  A simple question about editing a file ends up with people telling you to use commands like "chmod" and "chgrp", with guys arguing about "emacs", "nano", and "vim".  It is frustrating, and I've given up many a time.

But if you keep coming back or persevere, you end up with a whole lot of knowledge and a wonderful inexpensive home network (which home networks are becoming more commonplace nowadays).

As for what I consider the trap....I warn people against getting too wrapped up in the OS.  Some people get really good at Linux, and just love spending their entire weekends tweaking the kernel to get some extra performance out of their machine.  Well, good for them.  Time is money though, and you might be amazed at how much time Linux wastes.  Rather than tweaking a kernel, you could probably work minimum wage for a weekend or two and buy a faster processor.  Rather than goof around with network sharing, you could probably work minimum wage for a couple of weekends and buy Windows Standard Edition.  I joke that Linux is the broken project car of the computer world.  It's fun to buy new parts and rebuild the engine, but at some point you're just wasting time...go buy a new car.  And if it's too much of a waste of time to get the server working, go buy a Windows Server.

However once you get hooked in the server world, you'll start wanting to do more things...which cost more money with Microsoft.  Meanwhile the Linux side keeps improving and getting easier to use...always waiting for you to come back.

---

### Post by fela on 2009-10-06
> **Dzingis said:**
> Try Webmin or even eBox.

These two make administration much easier.

What could be easier and more enjoyable than editing text files with vim?

---

### Post by fela on 2009-10-06
@Lucky.

Good, well thought out post but just wanted to question you one one point: you said it took an entire weekend tweaking Linux to get it to the way you want? Or something like that anyway.

Let me tell you this: I setup my Linux server from scratch including installing Debian from the internet over a slow connection, in one evening (which happened to be a Saturday that I wasn't busy in).

Also I wouldn't dream of putting Windows on a server...period. Maybe I am just one of those geek types who love to be able to control their computers.

---

### Post by ready4thebreak on 2009-10-09
Man! Where do I start... I truly cannot thank you guys enough for all of your input(which is why I always use Ubuntu Forums for everything)! I guess I left out a point. I AM UBUNTU literate. I've been using Ubuntu for over two years now and I love every experience I have with it.

But back to the main topic. This helps me out a lot and in a way, I've realized that my Lacie home server is pretty much already serving most of the purposes mentioned. But's it's great to see that I was way overthinking how servers work(like Lucky. shared with us). I'm using my Lacie drive to backup all of my personal recorded music, music collection, videos, programs, Android ROMs, and everything I may need again. But I've been considering opening a new "Backup Server" project to my little computer maintenance shop(well more just a word of mouth-based, virus protection/repair outsourcing I do). I was considering allow people an allotted amount of disk space and they can backup all their important files and such on there. I think it would be nice to use Ubuntu server for this instead of my Lacie drive, which may not be as reliable as a dedicated computer and that way cannot have any access to my personal stuff.

Thank you guys so much! If there's any other info or possible directions you guys could throw my way(like I saw mentions of Webmin and eBox), I'd greatly appreciate it.

And what about virtualized workstations? We have these little Neoware computers around my office building that are pretty much images of XP that can't save anything to the machine, only to our Network Drives. Is there a network version of VirtualBox or something? I'd be interested in sheerly being able to setup and maintain one(I'm trying to become an IT). 

And FINALLY, I will shut up and stop asking so many questions! I truly cannot think of how much time and confusion you guys have saved me! Personal lifesavers!

---

### Post by Lars Noodén on 2009-10-09
> **ready4thebreak said:**
>  We have these little Neoware computers around my office building ... that can't save anything to the machine, only to our Network Drives. 

1) You could install a bare-bones system (in install, find the option for CLI) and then add the few pieces needed.  You'd need a GUI with a small foot-print, so FVWM-crystal is going to be one of the smallest, yet nice looking ones.  Fluxbox is good, too, but if you are going to 'sell' the idea to management, you'll need to customize it so it looks fancier.

2) From the HP website those look like thin clients.  You could look at LTSP or a variant.  Adjust to need.
[list]
[*] [LTSP](http://www.ltsp.org/)
[*] [K12LTSP](http://k12ltsp.org/mediawiki/index.php/Main_Page)
[*] [Skolelinux](http://www.skolelinux.org/en/)
[*] [Edubuntu](http://edubuntu.org/)
[/list]

A thin client is an illusion.  A linux system is made up of layers, and the terminal server puts some of these layers on another computer or loads them from another computer.

---

### Post by Lars Noodén on 2009-10-09
> **ready4thebreak said:**
> ...I've been considering opening a new "Backup Server" project to my little computer maintenance shop(well more just a word of mouth-based, virus protection/repair outsourcing I do). I was considering allow people an allotted amount of disk space and they can backup all their important files and such on there. I think it would be nice to use Ubuntu server for this instead of my Lacie drive, which may not be as reliable as a dedicated computer and that way cannot have any access to my personal stuff.

Consider at least two hard drives, for at least RAID 1, that protects from failure of a single hd.  And because RAID is not a substitute for backup, you'll want two removable storage units so that one is in the off-site, magnetic-media approved fire safe while the other is in transit.  If you have to choose, the back up is more important than RAID.  The file systems, or at least the home directories, should be encrypted, including on the removable media.  


As to how to do the file sharing, 

1) You can use disk quotas in a regular EXT filesystem and manage files via SFTP (not *FTPS*, that's very different).  SFTP is built into openssh-server.  Use the ChrootDirectory keyword in the sshd configuration to help lock down the directories.  To help directories private, set umask to 0077.  

Disk quotas can be managed with the tools quota and quotatool.

Filezilla is a good GUI-based tool to transfer files via SFTP. 

That is the option that best subscribes to the K.I.S.S. principle.  

2)  Samba is also a good choice there, on the low-end. Again make sure that umask is set so that files are not readable by other  groups or users.

---

### Post by Lars Noodén on 2009-10-09
> **ready4thebreak said:**
> ...my little computer maintenance shop(well more just a word of mouth-based, virus protection/repair outsourcing I do)....

A bit off topic but if you have some extra graphics cards, screens, RAM, keyboards and mice, you can try setting up some multi-seat stations to demo.  

Most, not all, but most, home users do nothing to burden the system resources.  They surf, they chat, they write e-mail, they edit and sort digital photos, they listen to music, and maybe do a little spreadsheet or wordprocessing action.  The idle resources on the probably overpowered box they already have could be used concurrently by a second user: spouse, sibling, etc. 

With a lot of people getting canned so that their former bosses can pay for new MS products, there will be much smaller holiday budgets and new computers may be out.  You know the prices better than I do, but here are some made-up numbers in the ballpark: $20 for more RAM, $25 for extra keyboard and mouse and $125 for a second screen, and (sometimes) $40 for a new graphics card and you functionally get a second computer.  

The money saved can be just that, money saved, or it can be a nicer holiday meal, or previously unaffordable screen or speakers.  

There is time for you to test it this month and, if it works, come up with some marketing buzz during November up to the big shopping weekend.  

[http://www.x.org/wiki/Development/Documentation/Multiseat](http://www.x.org/wiki/Development/Documentation/Multiseat)
[http://www2.userful.com/](http://www2.userful.com/)

---

### Post by lykwydchykyn on 2009-10-09
> **Lars Noodén said:**
> 
2) From the HP website those look like thin clients.  You could look at LTSP or a variant.  Adjust to need.
[list]
[*] [LTSP](http://www.ltsp.org/)
[*] [K12LTSP](http://k12ltsp.org/mediawiki/index.php/Main_Page)
[*] [Skolelinux](http://www.skolelinux.org/en/)
[*] [Edubuntu](http://edubuntu.org/)
[/list]

A thin client is an illusion.  A linux system is made up of layers, and the terminal server puts some of these layers on another computer or loads them from another computer.

+1 to this.  LTSP is pretty fun to tinker around with if you have some thin clients laying around.  Or create a PXE boot server and install some kind of Linux distro on a thin client for kicks.

---

