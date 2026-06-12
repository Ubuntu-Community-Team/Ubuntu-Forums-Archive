---
title: "How does Ubuntu Server compare to Windows Home Server?"
date: 2009-10-09
forum: Server Platforms
---

### Post by dv-design on 2009-10-09
Hello all,

Im highly considering buying or building a Windows Home Server (WHS), and im curious how Ubuntu server compares to it.

Im mainly looking to accomplish 2 things, automatic backups of computers on my network (from which i can restore a given computer from), and sharing Media (Movies, Music, and Images).

Some of my concerns are ease of use and ability to deliver movie content (stream) at reasonable speeds.

Itd be nice to have remote access over the web, but not necessary.

How well does Ubuntu Server function in a home setting, is it as easy and functional as WHS seems to be?

---

### Post by undecim on 2009-10-09
I've never actually used WHS, but I can tell you that an Ubuntu server will suite your needs just fine. All you will need to do is install Samba (this option should be available on installation, or through aptitude)

---

### Post by Lars Noodén on 2009-10-09
> **dv-design said:**
> 
Itd be nice to have remote access over the web, but not necessary.

How well does Ubuntu Server function in a home setting, is it as easy and functional as WHS seems to be?

Ubuntu works very well.  WHS has a bad reputation for ease of use and function so I'd have to say that based on the reputation Ubuntu is easier.  Ubuntu has it beat hands done on function.  WHS just doesn't have the variety and choice of applications nor the ability to mix and match.  

Any non-Windows server is a la carte style, but when you're done it looks like a single unit.  

For sharing files, as @undecim  mentioned, you'll want Samba.  WebDAV+HTTPS is another option, and not mutually exclusive with Samba.  

For streaming, you'll probably want Icecast.

---

### Post by dv-design on 2009-10-09
Well i figured that sharing media would be the easier part, but how do i go about setting up automatic backups? How are the backups stored and how easy is it to use those backups to restore a machine?

Essentially what id like to do with my backups is have 2 images for each machine...

1 image being the original done after ive installed the OS and all software i want. This image would rarely or never change.

The second image would change at regular intervals everytime i backup.

Im not really concerned with being able to restore individual files from a backup.

It is important however that i be able to "set it and forget it"...in other words schedule the backups and not need to fuse with settings or manually do anything again unless some major issue arrises.

Also, how easy is it to remotely change settings/shares and such on ubuntu server. For instance the console for WHS can be accessed from any computer on the network, and from this programs can be added, the system monitored, and settings changed.

I personally dont enjoy terminal/command line type of stuff, so does ubuntu server have the ability to do the above through a GUI?

Thanks guys.

---

### Post by Lars Noodén on 2009-10-09
> **dv-design said:**
> 
I personally dont enjoy terminal/command line type of stuff, 


The normal way would be to use [FONT="Courier New"]dump[/FONT] + [FONT="Courier New"]restore[/FONT] or [FONT="Courier New"]rsync[/FONT] either locally or over ssh.  The shell should not be underrated.  It's the shortest path to set-and-forget.  As long as you think of it as "command line" it's going to be unattractive, no matter how easy or useful.  Very little about working in the shell is specific to Ubuntu.  Virtually all of it is exactly the same on other APT-based distros, nearly all of it is portable to other linuxes, and most of it is portable to other systems including OSX, Solaris and OpenSolaris, and  [Free|Net|Open]BSD.

(It's also a darn better for cut-n-paste into you own lab notes, shell scripts for automation, howto's, tutorials, or Ubuntu Forums) 

> **dv-design said:**
> 
so does ubuntu server have the ability to do the above through a GUI?


Bacula would be *one* of your options either for regular shell or via the GUI:
  [http://www.bacula.org/en/](http://www.bacula.org/en/)

There are others you can find using bacula as the starting point for your searches.  However, these are all require learning.

When you choose one and getting running, it would be good to know what you found and what are for you the pluses and minuses and the deciding factor for choosing it and for not choosing others.

---

### Post by dv-design on 2009-10-19
So for anyone wondering, i think ive gotten my answer. I found a guide with very good simple explanations and some screen shots.

Essentially, Ubuntu Server w/Samba File server selected during install + Webmin + mdadm = Ubuntu Home Server.

Webmin adds a web based administrative GUI that looks similar to NAS web based interfaces and mdadm allows you to setup software RAID. Of course Samba is used to network share with windows platforms.

While i have not tried it myself yet, my guess is this is very close to what you get from a WHS based box. Still im not clear on setting up backup schedules and such, but i have a feeling with my win7 ultimate computer it wouldnt be an issue, as that has built in scheduling and the ability to backup to network locations.

So if i had a old computer hanging around Ubuntu Server would be a no brainer, but i dont so i have to decide if $400 for a Acer H340 is better then a DIY Ubuntu Server for about $300-400. Ubuntu would have quicker/better hardware but the case would be larger, not hotswap, and id have to set it up myself.

---

### Post by CharlesA on 2009-10-19
I was in the same boat as you (sorta). I wanted to run a hardware RAID with automatic backups and whatnot. I checked out WHS first, mostly due to it being cheap compared to WS2003/2008, but in the end I picked Ubuntu, due to the way WHS managed the shares and such. 

If I had picked WHS, I would have had to manage everything from the home desktop via RDP, which was of course "unsupported." Not to mention that WHS was unable to create or read a GUID volume. (but it can do RAID-5)

So, Ubuntu server won out for me (and it was free!)

I've got my server set up using Webmin for management, VNC if I need to get to the gui, which really doesn't happen that often, unless I want to configure or check settings in webmin or my raid software without being on the local LAN.

I mostly use SSH to get a shell securely be it on my local network or from a remote location. (Tunnel VNC over SSH, so it's secure)

Not that it'll help you much, but I ended up building my server from scratch, cost me about $530 not including the stuff for the hardware RAID array.

EDIT: I did a lot of research when I was looking into getting my server setup. RAID isn't supported by WHS (officially), and it doesn't look like that Acer NAS has hardware raid support. It's a nice little box tho. :-) You could probably install Ubuntu on it like you are planning with out much difficulty. Just make sure to image the drive with WHS just to be safe.

---

### Post by dv-design on 2009-10-19
Hey CharlesA thanks for your input.

At this point im teetering between a Acer H340 WHS, a home built linux server, or a H340 with a pci-e sata/esata/ide card (using the ide with a cf card to install linux on).

For me hardware RAID isnt a huge concern, and while i know that you can set WHS to mirror files/folders of your chosing, i also understand its not the same as raid.

A linux based solution becomes more appealing the more i think about it, but then i consider the time, research, and possible frustration id face and think maybe a pre-built WHS will be less of a headache.

I consider myself computer savy, but im not a linux guru and while i understand half the acronyms you used the other half like RDP and SSH are chinese to me. Its terms like that that scare me away from a linux solution.

My biggest fear is having to handle anything from a terminal/command line...i didnt like it when dos was out, and i think id like it even less now.

---

### Post by CharlesA on 2009-10-19
Heh, I'm not a linux expert by any means, but I was able to get mine up and running by asking questions on this forum here. Overall, I think my main questions were um.. 
- SSH
- VNC over SSH
- RAID Driver (which I ended up fixing myself)
- Crontab
- Exim server

Other then that, Ubuntu pretty much installed well. There were just a few things I had issues with.

If you do decide to go with WHS, it is able to run RAID-5, but it's "not supported" officially, since you are supposed to do everything from the "console."

That's a huge difference from what I am used to with servers: remote desktop over to the server, do maintenance, etc.

It's basically a stripped down version of Windows Server 2003, so it should be an ok OS, just different. :)

---

### Post by windependence on 2009-10-19
> **dv-design said:**
> 
My biggest fear is having to handle anything from a terminal/command line...i didnt like it when dos was out, and i think id like it even less now.

Then you're probably better off with Windoze. If you want pointy clicky with linux, you certainly don't need the server product. It's really intended for production type servers. In fact, most of the folks who post here on the server forum could easily do their "home" servers with the desktop editiion with no problems at all. Ubuntu Server is optimized to be used with enterprise class hardware, and unfortunately, most folks here are running it on desktop hardware. It really wasn't designed for that.

You can take the desktop distro, install Bacula, and a few other GUI front ends, and you'll be just fine. If that doesn't sound like something you want to tackle, you'd be better off staying with Micro$oft.

-Tim

---

### Post by CharlesA on 2009-10-19
> **windependence said:**
>  In fact, most of the folks who post here on the server forum could easily do their "home" servers with the desktop editiion with no problems at all. Ubuntu Server is optimized to be used with enterprise class hardware, and unfortunately, most folks here are running it on desktop hardware. It really wasn't designed for that.

You can take the desktop distro, install Bacula, and a few other GUI front ends, and you'll be just fine. If that doesn't sound like something you want to tackle, you'd be better off staying with Micro$oft.

-Tim

That's probably true. You'd just need to install the services that you need to use on it and you'd be fine. :P

---

### Post by hessiess on 2009-10-20
> 
My biggest fear is having to handle anything from a terminal/command line...i didnt like it when dos was out, and i think id like it even less now.


Just try it, the command line is *so* much faster than any GUI and wastes a lot less screen space (which is a precious resource ;) ). The command line on Linux is better than the one on any windows/dos OS.

---

### Post by mutrax on 2009-10-20
I use/sold a lot of linux home servers

The hardware is a shuttle k45 barebone with 1 Gb ram and a low power intel cpu and 2 identical disks ( from 500Gb to 2Tb each).

I run hardy 8.04 on them. I set up software raid 1 (/ and swap part).
-ssh shell and webmin for administration
-samba for file sharing
-mediatomb/ampache for music streaming to pc/console
-imap mail server with postfix/dovecot to make mail accesible evrywhere
-with cronjobs I handle automatic backups & auto shutdown from 23:55 to 7:30 (powersave)
-I'm in the middle of trying to get funambol running for phone/calendar /mai syncing

There's a steep learning curve if you're only used to windows systems, but these systems out perform windows by price (licensing costs), flexibility (wat can't be achieved?) and stability (viruses? crashes?)

I access the severs features from the outside via my dd-wrt enabled router that runs dns and a vpn server.

If you want to know more I'd be glad to go more into specifics.
This servers uses at minimum 35 watt (according to shuttle). But a average server with 2x 1Tb and celeron processor uses 55 watts in my experience.

---

### Post by dv-design on 2009-10-20
I have been using Ubuntu Desktop on and off since about 8.04. I actually have 9.04 on my ps3. I guess my ignorance as to what the desktop version and server version where is obvious here. So its my understanding that little sets apart the 2 versions except maybe some enterprise type drivers and maybe some gui type things?

The terminal is just not my cup of tea...its like any other tool, its only useful if you know how to use it, and i dont mind digging around to do certain things, but i just dont have the patience to type everything out, hit enter and realize i mispelled a command or a parameter.

Im not saying i wont use terminal, just that id like to limit the need for it.

Mutrax it sounds interesting, any info you can provide would be great. I definatly want to learn more, and anything i can do to keep my money out of Microsoft's hands tickles me pink.

Just for my edification, ubuntu server has a GUI interface like kde or gnome right?

---

### Post by mutrax on 2009-10-20
> **dv-design said:**
> 

Just for my edification, ubuntu server has a GUI interface like kde or gnome right?

Welleuhm, no it doesn't, thats where webmin comes in.. Its a web based gui that handles most default server tasks. If you get in to media servers etc, they usually have their own web ui. 

On a second thought, you can simply install the gnome ui on the server package (it literally takes one command). I personally don't see the use for that since there's webmin.

FYI, diffrence between server and desktop edition, is that desktop has gnome for gui with DT apps preinstalled, and the server edition allows you to pre-install server packages at install...
The server package is good at what it's ment for, and doesn't load gui's or unneeded resources what are needed in a desktop environment.

I would really recommend have to have a look at the webmin demo at [http://www.webmin.com/demo.html](http://www.webmin.com/demo.html)

PS. I to believe that terminal usage is not intended for average pc use... but I had to change my mind for this if I really wanted to create a truly great server. This way you can do stuff (beyond the basics) that you can't do without throwing tons of money at a windows server.

---

### Post by mutrax on 2009-10-20
So if you are intrested, my Ideal setup to start off with is;
For the hardware a shuttle k45, costs around 100&#8364; , put in a light processor (celeron430 for the basics, e21XX if you're into virtualisation) 1 gig ram (or 2 for virt) 2 identical disks (2x WD green 1Tb) That will give you hardware just above 300&#8364; in total.

Install ubuntu with raid 1 as described here
[http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1](http://www.howtoforge.com/how-to-install-ubuntu8.04-with-software-raid1)
Pick apache/mysql/php 
Pick ssh server for remote terminal ( I know, but you never know...)
Pick dovecot/postfix if you want to have centralised mail server (this takes a time to set up for a beginner, search the tutorials!)
INSTALL webmin 
```
wget http://downloads.sourceforge.net/project/webadmin/webmin/1.490/webmin_1.490_all.deb?use_mirror=mesh
sudo dpkg -i webmin_1.490_all.deb
```
Surf to [https://servername:10000](https://servername:10000) , and you're in business!

Oh yeah.. most packages are in the repos (installable via software ui in webmin) or you can set them up as any other webbased application (DB creation in webmin, extraction in apache docroot, etc.. etc...)

---

### Post by dv-design on 2009-10-20
Thanks for the explinations.

Would apache/mysql/php be nessasary if i _dont_ intend on using that computer as a web server?

Also, from what everyone here and various other places have said, it sounds like i could use either the desktop or server versions to accomplish what i want.

Webmin i have heard of, i was planning on using that if i made a linux box.

So i think im starting to understand what i will need for my needs, if i lay it out maybe someone can tell me if im on track;

-Ubuntu server or desktop
-webmin for remote config
-mdadm for software raid if i chose to do this
-Samba for network shares
-SSH (still not sure what this means)


Id like to run PS3 media server and Tversity from this box to, i dont think those would be hard to setup...and its not a huge concern as id only use these for streaming to ps3.

Lastly, if i wanted to schedule backups from the server, im still not sure what id need to do this...i could take the easy way out and have win7 do it to the server...but id like to learn how to get the server to do it.

---

### Post by CharlesA on 2009-10-20
> **dv-design said:**
> Thanks for the explinations.

Would apache/mysql/php be nessasary if i _dont_ intend on using that computer as a web server?

You wouldn't need it, no.

> Also, from what everyone here and various other places have said, it sounds like i could use either the desktop or server versions to accomplish what i want.

I used the server version, but you can use the desktop version as well, since you can just use:
apt-get samba
apt-get ssh
apt-get mdadm (I think, not sure)

Or just add them thru webmin. :)


> So i think im starting to understand what i will need for my needs, if i lay it out maybe someone can tell me if im on track;

-Ubuntu server or desktop
-webmin for remote config
-mdadm for software raid if i chose to do this
-Samba for network shares
-SSH (still not sure what this means)

Webmin for admin
mdadm for RAID
Samba for network sharing with Windows
SSH would be used for securely connecting to your machine and getting a terminal. You can use VNC to get to a desktop if you need to. I do it that way.

> Id like to run PS3 media server and Tversity from this box to, i dont think those would be hard to setup...and its not a huge concern as id only use these for streaming to ps3.

I don't know how the PS3 or Tversity streams audio, but if it uses a share, it'll probably work fine.

> Lastly, if i wanted to schedule backups from the server, im still not sure what id need to do this...i could take the easy way out and have win7 do it to the server...but id like to learn how to get the server to do it.

I use rsync for the backup and crontab for the scheduling on my box.

---

### Post by mutrax on 2009-10-21
you DO need the A/M/P setup if you intend to use web interfaces for administration of some server applications. Its easier for a novice to have them set up at installation

mdadm gets installed and configured at setup if you follow the tutorial I linked to.

you need a upnp enabled server to stream to your ps3, like mediatomb.

---

### Post by dv-design on 2009-10-21
Thanks both of you.

I have installed Wubi on my win7 machine and alloted like 20gb to the install. It installed windows desktop and i installed samba and webmin (no need for mdadm at this point).

I havent gotten much further then that nor have i played around. I spent maybe 5 mins poking around in webmin and it seems like a pretty good gui to use, only problem is i dont understand much of it or how it works.

For instance i tried setting up /home/videos as a share, webmin saved the settings but when i went to the desktop and clicked properties for that folder it was not checked off as shared.

Granted i didnt take the time to figure it out, im gonna wait til i have the time to sit down and explore and tinker...o and read guides lol.

I can see theres goin to be a learning curve, and that some functions will not be as intuitive as a windows machine...but free makes up for that and as long as its not rocket science im willing to give it a try.

---

### Post by CharlesA on 2009-10-21
Using Samba works a little differently then windows, since the folder won't show up as "shared" anywhere on the OS except in Samba.

You can check from a windows machine by typing \\machinename

---

