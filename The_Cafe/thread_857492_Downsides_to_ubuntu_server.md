---
title: "Downsides to ubuntu server?"
date: 2008-07-12
forum: The Cafe
---

### Post by kevin11951 on 2008-07-12
are there any downsides to using ubuntu as a server?

ubuntu server edition vs...

gentoo
slackware
debian
suse
redhat
fedora
etc...

---

### Post by Dr Small on 2008-07-12
It boots too fast, it installs software too easily, and if you use ethernet, the connection is to fast! :)

---

### Post by ghindo on 2008-07-12
You don't have to compile software from source, which is a real bummer :(

---

### Post by stmiller on 2008-07-12
Ok these are my thoughts:

If you like and know Ubuntu, that is a good choice of course! It has very nice graphical interface controls for a server if you need a server with a desktop.

Redhat/CentOS 5.x has security updates until 2014, for instance, if that concerns your server needs. 5.x is based on Fedora 6. CentOS is the free version of Redhat and is 100% binary compatible.

Debian has an extremely long testing period (years!) before a release is marked stable. So Debian is extremely stable, though package versions are not bleeding edge.

Fedora is not a good choice for a server as the package versions and constant updates are very rapid. Also Fedora security updates are only good for a year or so. If you love Fedora, use CentOS for server.

Gentoo - excellent for a server, as long as you stay with their stable package versions and don't install anything bleeding edge which may cause problems.

Slackware is also great for a server, though does not have an extensive repo of software like Debian.

SLED is the enterprise version of Suse. Suse has made a Fedora/Redhat relationship. So the opensuse version does not have a long support cycle of updates.

---

### Post by phrostbyte on 2008-07-12
I like Ubuntu Server because easy to install and has all the same administration tools and packages as Ubuntu desktop. So you use apt-get and what not to add software, and all the config files are in the same place. It's amazingly easy to set up too, without some experience with Linux servers even, it's a still a fairly short learning curve to set up a web server if you are familiar with Ubuntu on the command line. At this point I can get Ubuntu servers up in running with complex configurations in under an hour.

---

### Post by kevin11951 on 2008-07-12
my favorite thing about it is that if you run:
```
sudo tasksel
```
it lets you pick the type of server, and extras (ie. ssh, lamp, mail, file, etc...)
thats the reason i use it... wondering if there was anything easier/better.

---

### Post by FuturePilot on 2008-07-12
> **stmiller said:**
> 

If you like and know Ubuntu, that is a good choice of course! It has very nice graphical interface controls for a server if you need a server with a desktop.


The server version has no desktop. Pure command line. :mrgreen:

---

### Post by kevin11951 on 2008-07-12
> **FuturePilot said:**
> The server version has no desktop. Pure command line. :mrgreen:

and this server will be headless (ssh only)

---

### Post by stmiller on 2008-07-12
> **kevin11951 said:**
> my favorite thing about it is that if you run:
```
sudo tasksel
```
it lets you pick the type of server, and extras (ie. ssh, lamp, mail, file, etc...)
thats the reason i use it... wondering if there was anything easier/better.

Debian has this too, though Debian does not have as many meta-options as Ubuntu I don't believe.

---

### Post by kevin11951 on 2008-07-12
> **stmiller said:**
> Debian has this too, though Debian does not have as many meta-options as Ubuntu I don't believe.

double negative lolz

you right though, i have debian in an VM, and its meta options are limited

---

### Post by steve8track on 2008-07-12
Ubuntu is easy to set up, and you can install the Desktop edition and add the server components (or vice-versa) so you can still graphically log in if you want to.

Slackware, DSL, and other light weight servers are good for low end systems, although if you system can handle it, I would go with Ubuntu.  I had a ubuntu server on a 400 MHz 384 MB of RAM machine, complete with PHP, mysql, and it worked fine I guess.  I even had the GUI working on it, but that slowed the computer down substantially, since Ubuntu Desktop is designed for a minimum of 800 MHz or better (and 128 MB of RAM).  If your server is better than 800 MHz (or even 400 server only), then I would go with Ubuntu, and if you find it's too slow, then try the lighter weight ones.  There is nothing to stop you from trying out several except for time and patience.

Also, with Suse, Gentoo and many other distributions, you may not be used to the differences in command line work, such as installing software with "yum" and "rpm" instead of "apt-get" or "aptitude".

Also, if you are doing this for fun to learn how to make websites, you may consider running it on your own computer with whatever OS you are running.  For example, on my old laptop, I installed Ubuntu and Apache2 restricting access to only localhost so I could develop on the go.  It worked great on a 1.3 GHz Celeron, and if you are worried about day to day resources, you could just turn it on as you need it.

Good luck and I hope this helps,

Steve

---

### Post by Dragonbite on 2008-07-14
> **kevin11951 said:**
> are there any downsides to using ubuntu as a server?

ubuntu server edition vs...

gentoo
slackware
debian
suse
redhat
fedora
etc...

I've been trying to get my home server running and have tried a few:

CentOS does a nice job of setting you up and giving some nice tools to help set up and customize things.

Ubuntu Server, being CLI, is trickier for me as a newbie to Networking/Server related stuff. If you don't know the command line, or don't know where to find the commands ([http://www.howtoforge.org](http://www.howtoforge.org) is helpful) then it's a steep learning curve. I'm tempted to do a stock Ubuntu install and then add the packages I want and remove whatever I can.

OpenSUSE has the advantage that YAST provides for  configurating, installing and updating and is fully available over SSH (just type yast or yast2 at the prompt).  My biggest problem with openSUSE is that it gives me the ability to configure a LOT of things that I haven't a clue [LIST=1]
[*]What to change
[*]What to change it to
[/LIST]and this has gotten me into more than once.  This is my current server OS but I am now at the point of trying to figure out Samba permissions.

But like I said, I am a newbie to the whole thing, primarily used Linux on the desktop.

---

### Post by BDNiner on 2008-07-14
If you don't mind learning another distro then you could use either one of them. i am also setting up a home server and have tried fedora, opensuse, ubuntu, and centos. i think i am going to settle on centos. ubuntu is great and i had no problems setting it up i just want to use this an a chance to learn something new. fedora was too unstable. updates would break a lot of things on my system and since i was going to use the things i learnt at work then this was not a good idea. opensuse is ok, i didn't give it a fair chance since i am not really a fan. but after the first installed i asked myself what i was doing and went ahead and installed centos.

So far i love centos. especially since it is 100% compatible with the RHES binaries. but i have been unable to find DVR software yet. i also want the server to also record surviellance footage, and the solutions i have found call for a debian based system. i guess i could complie the software from scratch but my knowledge is not quite there yet.

---

