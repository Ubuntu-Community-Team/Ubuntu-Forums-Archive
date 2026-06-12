---
title: "Adito and build of ubuntu packages"
date: 2008-10-09
forum: Server Platforms
---

### Post by jujitsu-nut on 2008-10-09
Hi.

I am looking to make a package for Ubuntu of Adito. Adito is a fork of the SSL Explorer application which used to be 'open' but is now closed and hence the fork to Adito. The good thing is Matt Mattson is actively working on this application so I'd like to contribute and/or work with someone to help him out with this...

This application requires java 1.5 for the JRE and ant. Ant is used to install and configure Adito while the java is indeed for Adito as it's a java based SSL VPN application. 

Is anyone interested in guiding me through this process or helping out to create a package?

Thanks in advance,

JJN.

---

### Post by sasepp on 2008-11-27
Hi,

I'm the project manager for Adito. I found your post accidentally when googling - that why I hadn't replied sooner :). Building DEB packages should be rather easy, but I might be wrong. I've heard that there are special Apache Ant tasks for building DEB and RPM packages.

Getting Adito to distro repositories is currently one of my highest priority goals. It would give Adito some needed visibility - and hopefully more technically savvy contributors. When the DEB packages are ready, we can create a apt repository to Adito's private virtual server. After that we can start working on getting the packages to mainstream repos (Debian and Ubuntu). 

Anyway, please join the Adito mailinglists (adito-dev and adito-user) or drop a message to Adito forums about your plans! We can continue this discussion there. Naturally I'll provide you with access to Adito wiki and SVN when you need them. I'm also glad to help you as much as I can.

-matt

---

### Post by jujitsu-nut on 2008-12-09
> **sasepp said:**
> Hi,

I'm the project manager for Adito. I found your post accidentally when googling - that why I hadn't replied sooner :). Building DEB packages should be rather easy, but I might be wrong. I've heard that there are special Apache Ant tasks for building DEB and RPM packages.

Getting Adito to distro repositories is currently one of my highest priority goals. It would give Adito some needed visibility - and hopefully more technically savvy contributors. When the DEB packages are ready, we can create a apt repository to Adito's private virtual server. After that we can start working on getting the packages to mainstream repos (Debian and Ubuntu). 

Anyway, please join the Adito mailinglists (adito-dev and adito-user) or drop a message to Adito forums about your plans! We can continue this discussion there. Naturally I'll provide you with access to Adito wiki and SVN when you need them. I'm also glad to help you as much as I can.

-matt

Matt it's me, shogun - I am still trying to find a way to build packages.

I'll keep working on it.

JJN

---

### Post by Mr Popper on 2009-01-05
Hey guys, 

Just to pipe in here I'm also working on it as of tonight. I've downloaded everything nessisary to my dev-buntu box\\:D/ and to my Windows box :rolleyes: going to try the clean install method to create an install shield build if possible as well. 

For the record I'm no expert, not a programer and have only just started wrapping my head around java, just an unemployed IT guy with time on my hands. But figured I'd give it a shot just the same.

By the way, thanks a million for Adito.  It may take time, and effort to get it polished, but it's still a diamond as far as I'm concerned.  

Let me know if there's anything else I can do to help.  I'll stop back if I make any progress in the next couple days.

---

### Post by sapg on 2011-02-08
Did anything ever happen with this?  I have a pretty cheap and hence small amount of memory VPS that I would like to install Adito on but I run out of memory half way through the install.  I'm thinking that having a .deb might make it easier to get running.

---

