---
title: "Home Server OS"
date: 2007-07-17
forum: Server Platforms
---

### Post by netkid91 on 2007-07-17
Well, leave it to microsoft to come up with Windows Home Server, and it appears it has gone GM: [http://arstechnica.com/news.ars/post/20070716-windows-home-server-1-0-finished-code-goes-rtm.html](http://arstechnica.com/news.ars/post/20070716-windows-home-server-1-0-finished-code-goes-rtm.html)

Honestly, all of the functionality could easily be made in a linux box, pretty easily even.  In fact, I know what we need to do to get everything and more that WHS provides in a Linux box, but I don't know how to package/distribute it all.  So now I ask, is anyone willing to work with me on such a project?

---

### Post by johng4 on 2007-07-17
I've been working on several concepts.  The easiest way to do this would be to setup a home server with all the setup more or less preconfigured.  The just use remastersys (google it, its a Mint package, but works on all Ubuntu variants) to package it into a live CD.

Unfortunately for me, the development train has pushed me to start working on Tuneforge again, otherwise I'd help you out.  I'll be glad to consult and help where I can, feel free to e-mail me through the forums, or just send private messages.  I'm logged into the forums constantly.

---

### Post by netkid91 on 2007-07-17
Thankfully, I got most of the concept planned, but thanks for that link.  In fact, here's how a good majority of things are going to work.

Server Storage: This will be handled in the same manner as WHS, drives can be added to the storage pool without any effort sans a button click or two.  A new directory will be added to the file system tree to accomplish this, /storage.  This directory will then contain two more folders, mount and shared.  The mount folder, obviously, will be where the filesystems will be mounted, and storage will contain symlinks to the files spread across these drives.

Backup: Still deciding on what tool to use, but there are many incremental backup tools out for linux, but they all do the same task.  Most can be ported to run on windows clients as well.

So, how am I doing?

---

### Post by darkog on 2007-07-17
there are quite a few similar projects out there. 

[http://www.clarkconnect.com/](http://www.clarkconnect.com/)

and some others that i can't remeber off hand now.

---

### Post by netkid91 on 2007-07-17
The link you provided is a enterprise solution, we are talking home usage here.

---

### Post by johng4 on 2007-07-18
I would also suggest a careful planning on which packages to contain, and their default settings.

For example... metapackages with configuration files that are already setup for them, and ready to go.  

Working example...
Apache + Webmin + eGroupware + MySQL (which will also include Postfix and some other goodies).

Lets call it "homeserver-intranet.deb" for simplicity sake.

Most of those packages are already preconfigured, some symlink touch-ups and maybe even a script to make installation of the MySQL db painless would make the server ready to go in minutes.

Another example..
Apache + Squid + Dansguardian + SARG + DHCP + Shorewall (and a few others)

Lets call this one "homeserver-cachegateway.deb" with all the preconfiguration setup to instantly have the machine ready to serve as a router/gateway server.


All these things and more are what a home server needs.  Some people will want just a quick and painless Samba/NFS setup.  Others will want the gateway.  If nothing else, you don't need to create a whole distro, so much as preconfigured meta-packages with preconfigured conf files, and scripts to make the symlinks.

I'm still reading up on packaging at the moment, as this was my exact goal for several ubuntu related projects.

---

### Post by netkid91 on 2007-07-18
That's probably going to be how the system will be configured, but remember, the goal of this project is to make it so Joe Schmo can set it up without issue.  Installing a .deb would be good for those of us here on this forum, but for most users a install CD would be the best option.

---

### Post by darkog on 2007-07-18
> **netkid91 said:**
> The link you provided is a enterprise solution, we are talking home usage here.

nope. there is a a free community edition and then there is the paid/support edition. similar to other projects .

[http://www.clarkconnect.com/info/compare.php](http://www.clarkconnect.com/info/compare.php)

clark has been around for a while.

i am not trying to discourage you from your idea. i was just letting you know that there are other players in that linux segment. 

all the power to you if you can get one going -- i will be first to beta test it.

---

### Post by az on 2007-07-18
[https://wiki.ubuntu.com/UbuntuEasyBusinessServer](https://wiki.ubuntu.com/UbuntuEasyBusinessServer)

That's also knows as SOHObuntu and is a Google summer of code project.

---

### Post by astralsin on 2007-07-24
i've considered starting a project like this.  my plan was to base the operating system around a GUIless setup accessible by a web client.  the box would feature LAMP, Ruby, Python, etc. , and have a custom CMS acting as a portal for all the members of the server.  Basically acting as a home-based extranet, allowing the home server to be accessible remotely for messaging, chat, etc., with family members, frat/sorority members, and any other group that might find this application usable (lots of non-profit organizations would probably be of interest, or at least potential users).  Of course, alot of energy would have to be spent making it very easy to set up and use with most everything "just working".  

of course, a plugin interface should be included, with default plugins such as a forum, blogs, a calendar, chat, private messaging, streaming media, etc.  The interface should be customizable with themes or templates.  Email server capabilities should exist, even if its only web-based email (that might be cool if a nice client were written).  

Unfortunately, I don't have the time to venture on such a daunting task, I've got too many other projects as it is.

---

### Post by johng4 on 2007-07-25
My server project at home is exactly that.  Only I've recently started using Xen, which makes life much more simple.

Since my main cache server's south bridge died, I've been pulling my hair out looking for a replacement motherboard for a dual slot P3 w/133 SDRAM.  Its unbelievable how hard it is to find exactly that at a reasonable price ($300 or more for the ones that meet my specs, got the original for $20 2 years ago).  Anyway, with Xen I've turned my remaining PowerEdge server into 5 servers.

"Brielle" is my cache server, with Squid/Dansguardian/APT-Mirror/Rsync.  It handles all my web caching and content filtering, and is also my local repository mirror for ppc/x86 ubuntu.

"Ariel" is my groupware server.  It has my egroupware installation, which lets friends, family,  and customers connect to a single interface for Calendars, E-mail, Knowledge Base, Tasks, etc.  Easy to use, and manage.  Lots of great options and add-ons.

"Daniel" is my DNS and Rsync server.  It handles DNS locally, as well as performs network backups on my servers as well as my personal machines on the network.

"Linus" is my mail server.  It handles pop/smtp/imap mail and spamassasin.

All of these servers are hosted on "Mercedes" which in the end is my domain controller and master web server.  It serves as my Samba file server as well.

The point of this explaination is simple... if I'm configuring any one of these servers for a client, the single thing that would make my life 1000X simpler than putting in a CD and doing a quick install, is using a basic install disk and then installing a metapackage that grabs everything I need and has it preconfigured for a standard setup.

See where I'm going?  The metapackage concept makes it so that you're not working on a new server distro (of which there are already too many), but an easier way to impliment preset server types for every project out there.  This lets you just use the existing LAMP server, and within minutes have a specialized home server up and running.  It also lets someone who wants to take their workstation at home to install a deb from Synaptic to get a preconfigured server to suit their needs.  No extra CD downloads, no mess, no fuss.  

Thats as simple as it gets.

After I get all my new Xen servers setup, I'm going to start doing what I can to make the preconfigured packages off of the existing systems I have.  Now that I have the installations segregated from each other, its a hell of a lot easier to do now.

---

### Post by dorath on 2007-07-26
Howdy,

I think an "Ubuntu Server For the Home" is a spectacular idea!  After all, the server market is currently where linux shines the brightest, yes?

However, since it is for the home, and also presumably for more non-technical users, the principle of KISS should be observed.  After all, more advanced users could just configure the already existing Ubuntu Server to meet their needs.

What are the most basic things that people would want in a home server?  I would suggest the following:
-Central location for music & video
-Backup for /home/ and|or /My Documents/
-Dirt simple configuration
-Easily accessible from Windows | OsX
-Print server capability

Yes, there are many, *many* other things that people *might* want.  However, I say again that people looking for more advanced uses will be willing to use a more advanced product.  Joe Sixpack might want to back up his My Documents folder, but has very likely never considered any sort of email package, and probably never will.

---

### Post by netkid91 on 2007-07-26
Exactly what I've been thinking about.  I have nothing but time to devote to the project, but I'm horrible at actually writting code, packaging, et. al.  I'm more than capable of writing ruby/GTK+ and RoR frontends, but that's it.  I really need more people to help with this.

---

### Post by b20963a2 on 2007-07-26
[http://www.ubuntuhomeserver.org/](http://www.ubuntuhomeserver.org/)

Also it seems that Ebox will be included in the Gutsy repos: [http://www.ubuntu.com/testing/tribe3/](http://www.ubuntu.com/testing/tribe3/)

---

### Post by oly on 2008-02-25
also checkout [http://ubuntusm.org/](http://ubuntusm.org/), i am afraid the screenshots are broken at moment, but the development is quite active and can currently do a number of tasks, but you will need to check out from launchpad the debs that are around are very old now.

---

