---
title: "Setup 7.04 Server to replace Win2003 Server"
date: 2007-05-20
forum: Server Platforms
---

### Post by vbmds on 2007-05-20
We have decided to move from Microsoft operating systems to Linux - Ubuntu specifically.

I've spent the day trawling the documentation and forums for assistance in setting up our server using the Server version of Ubuntu, with little success - ending going around in circles.

To start, I've never setup a linux machine so I come at this as complete and utter novice. 

I am starting our move to linux with a rebuild of our server, to be followed by our PCs. And no, this is not a commerical situation but our home setup. We work in the IT industry so are not scared to use the appropriate hardware - our home server is really a server - Dell PowerEdge. We currently run Windows Server 2003 Standard with the following Roles active: DNS server, DCHP server, File server, Print server - so we want to end up with the linux server servering the same roles, plus any other(s) that a linux server can provide that might be useful for a home server.

What I have done thus far is to install Ubuntu Server 7.04 via the ISO I downloaded. Its installed without incident and I can login to the user I setup as part of the install. Now I'm stuck at the console...

I've located an article in atomic magazine, Issues 65 - 69, that goes over setting up a server with ubuntu but from the Desktop edition and I've found most of the console commands in the article don't work with the Server edition - well for me anyway. 

From the documentation I've looked at I've tried to install the gnome desktop, it went away and downloaded 420 odd meg but I can not workout how to start gnome - the console command from atomic doesn't work (sudo /etc/init.d/gdm start). I had hoped that if I had a GUI I might be able to muddle my way through getting the Roles setup more esily.

I have no problem with following documentation but thus far have not found any that I can actually follow. 

Thus I need help - pointing me to appropriate documentation would be fine, but any help will be greatly accepted.

---

### Post by foresth on 2007-05-20
Hi,

first of all, it is a serious security risk to run an X server (eg. with GNOME) on server. I am not familiar with Ubuntu Server edition but I'd be surprised if it were delivered with GNOME.

Although I use Ubuntu only on desktops, my server is running Debian, which is the very base of Ubuntu. The general methods of setting up DNS server, mail server etc. are very similar or even identical thus for such tutorials I'd recommend you [http://www.debian-administration.org/](http://www.debian-administration.org/) or [http://www.howtoforge.com/](http://www.howtoforge.com/) (HowtoForge has also a special Ubuntu section).

---

### Post by az on 2007-05-20
> **vbmds said:**
> We currently run Windows Server 2003 Standard with the following Roles active: DNS server, DCHP server, File server, Print server - so we want to end up with the linux server servering the same roles, plus any other(s) that a linux server can provide that might be useful for a home server.

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)
[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)
[https://help.ubuntu.com/community/Servers#head-80dd5f86d31988e45e15caedce1d515e991a0f34](https://help.ubuntu.com/community/Servers#head-80dd5f86d31988e45e15caedce1d515e991a0f34)
[http://doc.ubuntu.com/ubuntu/serverguide/C/index.html](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html)
[http://doc.ubuntu.com/ubuntu/serverguide/C/cups.html](http://doc.ubuntu.com/ubuntu/serverguide/C/cups.html)

---

### Post by shamankick on 2007-05-20
i agree with "foresth"

Ubuntu server is atractive because you can get the very last version of software
(apache 2.2 mysql 5.08 php 5 etc etc)
but Debian still the best one for production. (as webserver in exemple)

- if you are newbie (like me) you can find a lot of documentation for Debian
- in fact you don't care about very last version of software, what you need it's only security
and stability. By installing Etch you have an up to date system.

i use this two OS (debian and feisty) on 2 differents servers and i prefer Debian for
the main one

it's just my "newbie " opinion

---

### Post by craigp84 on 2007-05-20
> first of all, it is a serious security risk to run an X server (eg. with GNOME) on server. 

P1sh, absolute p1sh. When will this community stop spreading FUD about itself. An xserver by itself is not a security risk. Go give yourself a good hard talking to forseth.

Vbmds, it depends how you want to play it. If you;re keen to learn linux and are willing to persevere, then keep going the way you're going. You'll learn loads, you'll also learn a lot about how windoze works under the covers so it'll make you a more capable windoze admin too.

If you just need a quick fix, away from virii and licencing costs, look to a more specialised linux distro like [http://www.smeserver.org/](http://www.smeserver.org/) - it's all point and click, and dead easy to setup. It just gets the job done very quickly. And of course it's linux underneath, so if it doesn't fit your needs exactly, it's easily tweakable.

There's a middle ground between the two, it's called SuSE Linux Enterprise server. It's a free download, and comes with a most excellent configuration system called YaST. In my experience windows administrators take to YaST very quickly.

HTH,

-c

---

### Post by eric_stewart on 2007-05-20
> **foresth said:**
> Hi,

first of all, it is a serious security risk to run an X server (eg. with GNOME) on server. I am not familiar with Ubuntu Server edition but I'd be surprised if it were delivered with GNOME.

Although I use Ubuntu only on desktops, my server is running Debian, which is the very base of Ubuntu. The general methods of setting up DNS server, mail server etc. are very similar or even identical thus for such tutorials I'd recommend you [http://www.debian-administration.org/](http://www.debian-administration.org/) or [http://www.howtoforge.com/](http://www.howtoforge.com/) (HowtoForge has also a special Ubuntu section).



Good advice.  Those sites are great places to start, but I will disagree with one thing.  I don't think it's a security issue to run X on a server any more than running terminal server on a Windows box constitutes a vulnerability.  X runs like any other server-side service....it must be locked down appropriately from attack by both insiders and outsiders and that starts with a solid authentication/authorization/accounting (AAA) policy as well as selective control at the perimeter by a firewall.  An X Server can be accessed using either the client's native SSL encryption or through a VPN if desired.

I run an X server on my Ubuntu server and I like the GUI for installation and configuration of my various packages.  I am compelled to use the command line from time to time, for example when I compile an application from source, do a 1st time install (again in some cases) and edit various configuration files.

I'm not a noob...either for Linux or network security.  I just think the vulnerabilities of X are overstated.

/Eric

---

### Post by foresth on 2007-05-20
> **craigp84 said:**
> P1sh, absolute p1sh. When will this community stop spreading FUD about itself. An xserver by itself is not a security risk. Go give yourself a good hard talking to forseth.


It is a security risk for anybody who doesn't know what he does.

Thanks.

---

### Post by craigp84 on 2007-05-20
> It is a security risk for anybody who doesn't know what he does.

Clearly. Doesn't that go for all software? Wake up.

Your original posting is a classic example of spreading FUD (Fear, Uncertainty and Doubt). Please refrain in future.

-c

---

### Post by foresth on 2007-05-20
> **craigp84 said:**
> Clearly. Doesn't that go for all software? Wake up.

Your original posting is a classic example of spreading FUD (Fear, Uncertainty and Doubt). Please refrain in future.

-c

Ok, I'll try to be more precise next time.

Vbmds, sorry for off-topic ;).

---

### Post by vbmds on 2007-05-20
Thank you all for your responses.

I think I need to clarify one point I mentioned in my originial post - I'm a novice: I don't even know how to open a file to edit it from the console. I'm working on increasing my knowledge of console commands but my thought is if I wait until I know all there is to know I'll never get started with the jump to linux.

Also, to clarify the server purpose a bit, this server sits next to my PC and stores all our movies, music, documents etc. It has our printers attached and our scanner also. Thats it...access to our stuff from anyway in the house. The server has no function or need to do anything related to the internet. We only ran DNS/DCHP roles because it was easier to setup in Win2K3 than with our modem, and a domain was more stable/reliable than a workgroup for the LAN.

Thanks for all the links, although I've already been through those given by az and still ended up here. I'll work my way through the other links - I like the idea of point n click with smeserver. 

If anyone has a suggested 'absolute beginner' link for helping a new comer with getting into Linux, please do post it. I'm off to also find a beginners book ;)

---

### Post by vbmds on 2007-05-20
Oh, just one addition based on point made in an article over at howtoforge - I'm using the 64bit server package.

---

### Post by iggyboy on 2007-05-21
I'm a linux (1 year of *buntu) user considered between a newbies to an average user when comes to practical, although my MS Windows (more then 15 years) knowledge are to an professional level.

Well, to the subject... I am using a low end system (1GHz sempron socket 745 with 512MB RAM and build-in vidoe) to serve 20 Lan PCs for the purpose of File Sharing, MP3 Streaming, Web-Hosting (Joomla CMS) and some other basic stuffs for desktop applications, like web surfing, openoffice, watch movies etc.

Originally I started with Ubuntu Server Edition (dapper drake 6.06LTS) but due to my laziness, however I ended up with normal Gnome Dapper edition with LAMP installation on  top of it. From my Experience I can say that it's alot easier (for newbies) to Install normal Desktop Edition and from there start package by package installation for Server requirement. And the best thing about this setup is I can use the system for both light desktop application use and as server at the same time. I know, this may not be an ideal to mix both, but for my requirement it's not a problem, since my server is not for a life mission or business task.

What actually I'm trying to share is, may be you can give a try by installing Desktop Editions Ubuntu and from there you can start to install other required packages for server application. Believe me if you are a Windows User then you might feel this is more to your previous OS experiance.

best regards :)

---

### Post by gingernuke on 2007-05-21
I too am learning ubuntu, I have found that this guide 

[http://www.howtoforge.com/perfect_setup_ubuntu_6.10](http://www.howtoforge.com/perfect_setup_ubuntu_6.10) 

works for setting up some basic server roles.  Personally I have a server which I use as a mucking about box and I have been trying to set it up with the roles you mentioned just so I can hold up my end of a conversation with my mate who develops for Ubuntu :)

The guide doesn't cover DHCP & DNS but a quick search revealed this post which links to some more setup guides.

[http://ubuntuforums.org/showthread.php?t=448156&highlight=dhcp+server](http://ubuntuforums.org/showthread.php?t=448156&highlight=dhcp+server)

Currently I am trying to get Samba up and running but I am not applying myself much as Halo 3 multiplayer beta has eaten up 99% of my free time.  But whilst searching for links you could use I came across this and might give it a whirl.

If your server isn't mission critical why not persevere with installing Ubuntu server and configuring from the command line.  Then you can answer questions from the next person determined to wrap their head around configuring a working server.  BTW search for webmin, its absolutely mint for remote admin once you have the base system installed.

---

### Post by vbmds on 2007-05-21
Thanks for the replies. 

I've decided to presist with the Server edition, and have followed an article I found on howtoforge - [http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10]("http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10") which was set at the right level for me to actually be able to follow. :D

gingernuke, have a look at the link above for samba setup. Webmin you say, great was exactly what I wondered how it would be done - thanks.

My next task is to install the storage hdds (1TB) which contain all our data, so installing a NTFS compatiblity package.

---

### Post by gingernuke on 2007-05-22
I think you can conquer NTFS by following this...

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

Right - back to Halo 3 :)

---

### Post by Chayak on 2007-05-22
> **vbmds said:**
> Thanks for the replies. 

I've decided to presist with the Server edition, and have followed an article I found on howtoforge - [http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10]("http://www.howtoforge.com/samba_domaincontroller_setup_ubuntu_6.10") which was set at the right level for me to actually be able to follow. :D

gingernuke, have a look at the link above for samba setup. Webmin you say, great was exactly what I wondered how it would be done - thanks.

My next task is to install the storage hdds (1TB) which contain all our data, so installing a NTFS compatiblity package.

I would advise against keeping your data on NTFS if it's in a linux system. I know the drivers for it are getting better but if you're serious about using linux I would transition your data over to a linux native file system for integrity's sake.

---

### Post by mariomiy on 2007-05-29
I am experimenting with Ubuntu Server 7.04 under vmware-server, installed under Ubuntu 7.04. I just brought it to a X environment by means of "sudo apt-get install xubuntu-desktop", which is now working fine. There is no need to go for the Suse Enterprise Server.

I installed this server by specifying LAMP server to be included. It appears that *apache2* is not configured for LAMP, because there are no *AddType* entries for .php in /etc/X11/apache2.conf, unless they are implicit or elsewhere. 
[p]Has anybody been successful in using LAMP under Ubuntu Server. If so, give me a hint. I am considering to go back to Fedora Core, which is more understandable in this respect.

---

### Post by oly on 2007-05-30
I would also recommend sme-server you install it, it will ask a few questions afterwards reboot and your away, also has a web interface for configuring the server and users that can use it.

---

### Post by Sapphiron on 2007-05-30
I prefer Clarkconnect to SME server, it's far more active.  the only limitation on the free version is you can only create 10 user mailboxes, if you don't use it as a mail server, it's for unlimited use.

it makes a pretty decent firewall too.
[www.clarkconnect.com](www.clarkconnect.com)

---

### Post by oly on 2007-05-30
dont know much about clarkconnect, but i know sme-server is used by some buisnesses in the uk and even in a school, because you can add on all sorts like content filtering set it to be a vmware server web server e-mail server and much more.

ubuntu needs a nice web style interface to setup and manage a server, because modifying config files is beyond most people, most windows admins dont have the knowledge to set up dns and samba type services because these things are hidden from them and dumbed down in windows.

---

### Post by craigp84 on 2007-05-30
> ubuntu needs a nice web style interface to setup and manage a server

No this would be a bad move. Currently it's aimed at a different market than SME server. Diversity is key. Use the right tool for the job.

---

### Post by oly on 2007-05-30
care to elaborate, i do not see why it would be a bad move, because it would be optional like everything else just install it if you need it, else do it the other way.

all the tools are there in the repositories they are just a pain for the average person to figure out, took me about a year to figure out howto setup a pdc drop in replacement for a windows server using ubuntu.

---

### Post by craigp84 on 2007-05-30
> all the tools are there in the repositories they are just a pain for the average person to figure out

Your argument hinges on this being a bad situation. It's not.

Proper systems administration requires a certain skill set which is learned over time. A GUI cannot replace that knowledge and competence. With current technology that is simply not possible.

There are other tools targeted at that job, such as smeserver or SuSE Linux enterprise server. This is the way of linux and open source in general. Individual tools for each job rather than one big all encompassing bloated mess.

Choose the appropriate tool for the job. Ubuntu is not, and more importantly, should not, be the correct hammer to use for every nail.

-c

---

### Post by vbmds on 2007-06-10
Well I've spent a week or two running SME and found it to be excellent in all things but 1...it has no NTFS support - which thus makes it useless to me. I've also looked at ClarkConnect and liked the look of that even more than SME, but alas it also does not have NTFS support.

So I'm back to ubuntu server and desktop. 

I've tried to install the desktop and then add server functions, but it takes so long to start the install from the LiveCD desktop - more than 20 minutes for the 1st window to come up and have the command buttons! and this is on a DELL PowerEdge server box :( - that I've given up on that idea and have now reinstalled ubuntu server and will install gnome or KDE, not sure which yet, and take it from there.

Although I've not made any progress with getting my NTFS drives made available to the LAN again, its been an interesting introduction to linux, which I have to say I've quite enjoyed :o

---

### Post by cprofitt on 2007-06-11
> **foresth said:**
> It is a security risk for anybody who doesn't know what he does.

Thanks.

Umm...

Running a server console based or not would be a security risk for anybody who doesn't know what he does.

running a GUI doesn't open up any security holes that are not already present unless you think it will result in buffer overflows or some such.

---

### Post by cprofitt on 2007-06-11
> **Chayak said:**
> I would advise against keeping your data on NTFS if it's in a linux system. I know the drivers for it are getting better but if you're serious about using linux I would transition your data over to a linux native file system for integrity's sake.

I am curious what Linux native file systems offer ACLs equivalent to NTFS or NFS.

---

### Post by craigp84 on 2007-06-11
Linux ACLs are horrendously terrible to look after compared to the windoze implementation.

That being said, normal unix style permissions have served well, normally (though certainly not always) it's possible to concoct a cunning access scheme using just plain old users, groups and unix permissions.

In a past job we ran into the 16 group limit (google it) on some older unix boxes. We stepped round that using common user accounts (which have their passwords locked) and allowing users to "sudo su - <user>" to that account. Somewhat like assuming a role in Solaris. This still provided the necessary audit trail thanks to sudo.

If you're really wanting the pain, tears, blood and lost sleep that linux ACLs deliver, check out the trustees project which makes it somewhat more bearable.

Hope this helps,

-c

---

### Post by netlogic on 2007-06-11
> **foresth said:**
> Hi,

first of all, it is a serious security risk to run an X server (eg. with GNOME) on server. I am not familiar with Ubuntu Server edition but I'd be surprised if it were delivered with GNOME.



No, it isn't if you tunnel your session with ssh and block unnecessary ports from the server's firewall.

---

### Post by Brazen on 2007-06-11
If you can do without a GUI, don't install one.  This argument has been done to death.  Install it if you must, but you will be better off without it (for reasons that could go on and on) and you should work towards transitioning away from it.  There is good reason why the server edition of Ubuntu does not install an x server.

Use Ubuntu Dapper instead of 7.04.  Use Dapper until the next LTS release.  The LTS releases are more thoroughly tested and a better choice for a stability and reliability - primary concerns for a server.

The best documentation I have seen for what the OP is wanting to do is the official Ubuntu documentation:  [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/index.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/index.html)  Don't settle for the imitation stuff, get the real thing ;)

And, as for Ubuntu needing a powerful web-based management interface, well... that's what Webmin is for!

---

### Post by netlogic on 2007-06-11
Installing GUI or not isn't a security risk long as you are using ssh to authenticate and tunnel. Just like Vnc isn't a security risk long as you are tunneling with ssh. If he isn't running a firewall on his server, he should yank out the GUI that turns on other services. Another thing is GUI will install more applications that an admin has to patch as the time goes. NO GUI will increase stability. GUI isn't a security risk with a firewall.

---

### Post by Chayak on 2007-06-13
For those asking for a web interface for management just install webmin

---

