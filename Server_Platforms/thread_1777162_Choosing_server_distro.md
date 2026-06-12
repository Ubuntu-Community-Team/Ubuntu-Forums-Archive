---
title: "Choosing server distro"
date: 2011-06-07
forum: Server Platforms
---

### Post by Dry Lips on 2011-06-07
So I'm about to host my own web-site, (Static Html + downloads) and I'll have to decide which server distro to go for. I'm concerned with security, but also ease of use and I wonder if you have any suggestions about which server distro to choose.
 

 I'm especially interested in learning the difference between 10.04 and 11.04? Is there any reason at all to go for the LTS edition? And what about other distributions, would I be better off by simply hardening my Ubuntu server than installing, say, OpenBSD?

---

### Post by Lars Noodén on 2011-06-07
[s]What do you plan on doing with the server?  That will help determine which distro is most suitable.[/s]

Edit: I missed the first sentence.

---

### Post by collisionystm on 2011-06-07
> **Dry Lips said:**
> So I'm about to host my own web-site, (Static Html + downloads) and I'll have to decide which server distro to go for. I'm concerned with security, but also ease of use and I wonder if you have any suggestions about which server distro to choose.
 

 I'm especially interested in learning the difference between 10.04 and 11.04? Is there any reason at all to go for the LTS edition? And what about other distributions, would I be better off by simply hardening my Ubuntu server than installing, say, OpenBSD?

Zentyal

[www.zentyal.com](www.zentyal.com)

---

### Post by ojdon on 2011-06-07
I hear CentOS is the Distro of choice when it comes to servers, especially since it's designed with servers in mind. :) Though if you only want a Ubuntu based version then go with the LTS one simply because there is less messing around instead of having to upgrade every 6 months.

---

### Post by Lars Noodén on 2011-06-07
Since you are self-hosting you can choose any distro and web server available.

I normally recommend Debian because of the long release cycles and good old APT.  However, Ubuntu LTS would do the same job.  

Which Apache will you run, or will it be nginx?  If you want the Apache 1.3.x series, then that's where OpenBSD leads because of the extra work including built-in chroot.  If you want the 2.x series, then they are more evenly paced.

---

### Post by Lars Noodén on 2011-06-07
Another item in favor of OpenBSD is the availability of PF.  In many ways it is easier to use than IP Tables.

---

### Post by Dry Lips on 2011-06-07
**ojdon:**
> I hear CentOS is the Distro of choice when it comes to servers, especially since it's designed with servers in mind. :smile:  Though if you only want a Ubuntu based version then go with the LTS one  simply because there is less messing around instead of having to  upgrade every 6 months.     I heard that the CentOS project was in trouble:
 [http://ubuntuforums.org/showthread.php?t=1759817](http://ubuntuforums.org/showthread.php?t=1759817)

**collisionystm:**
> Zentyal

[www.zentyal.com]("http://www.zentyal.com/")
 Never heard about Zentyal before... Ubuntu based, yeah? What's the difference between Ubuntu and Zentyal then?

** Lars:**
> Since you are self-hosting you can choose any distro and web server available.

I normally recommend Debian because of the long release cycles and good old APT.  However, Ubuntu LTS would do the same job.  

Which Apache will you run, or will it be nginx?  If you want the Apache  1.3.x series, then that's where OpenBSD leads because of the extra work  including built-in chroot.  If you want the 2.x series, then they are  more evenly paced.     This'll be my first “real” server besides one old computer that I run 8.04 on, so this will be my first serious project... In other words, I've still got a lot to learn.

 To be honest I haven't given the differences between the Apaches much thought yet.
  I'm not completely sure what you mean... Setting up Apache in OpenBSD requires more configuration than the never versions?  

Regarding PF vs IP Tables: would OpenBSD generally be easier to set up than
Ubuntu, or is PF the exception?

---

### Post by Lars Noodén on 2011-06-07
> **Dry Lips said:**
> 
** Lars:**
This'll be my first “real” server besides one old computer that I run 8.04 on, so this will be my first serious project... In other words, I've still got a lot to learn.

 To be honest I haven't given the differences between the Apaches much thought yet.
  I'm not completely sure what you mean... Setting up Apache in OpenBSD requires more configuration than the never versions?  

Regarding PF vs IP Tables: would OpenBSD generally be easier to set up than
Ubuntu, or is PF the exception?

Apache 1.3.x on OpenBSD with PF is, for me, the far easiest to set up and maintain. (The system installation is a little harder but still doable with little experience.)  However, if you are coming from an Ubuntu experience, then there will be less new to learn for Debian.  In fact nearly 100% of what you know for Ubuntu will be valid for Debian.

---

### Post by collisionystm on 2011-06-07
Zentyal is Ubuntu. But BETTER. Try it out in a virtual machine. I use it as a file server, PDC, emaiil...etc. for 100 users. works great.

---

### Post by Dry Lips on 2011-06-07
> **Lars Noodén said:**
> Apache 1.3.x on OpenBSD with PF is, for me, the far easiest to set up and maintain. (The system installation is a little harder but still doable with little experience.)  However, if you are coming from an Ubuntu experience, then there will be less new to learn for Debian.  In fact nearly 100% of what you know for Ubuntu will be valid for Debian.

That's interesting! I've always thought that OpenBSD was a very secure,
but difficult distro. I guess the installation is Arch-style, but yeah, 
I'm definitively considering OpenBSD. 

On the other hand, what I like about Ubuntu is that the community is really 
great. My experience is that if I'm stuck, I get help here most the time.
I think that the OpenBSD guys don't even have their own forum, 
so migration to a completely unfamiliar distro seems a bit intimidating.

---

### Post by Dry Lips on 2011-06-07
> **collisionystm said:**
> Zentyal is Ubuntu. But BETTER. Try it out in a virtual machine. I use it as a file server, PDC, emaiil...etc. for 100 users. works great.

How about using it as a web server then? But I'll give it (and OpenBSD) a go in VirtualBox! ;)

---

### Post by collisionystm on 2011-06-07
> **Dry Lips said:**
> How about using it as a web server then? But I'll give it (and OpenBSD) a go in VirtualBox! ;)

[http://doc.zentyal.org/en/web.html](http://doc.zentyal.org/en/web.html)

---

### Post by irv on 2011-06-07
There is a very long thread out here: [Show us your server.]("http://ubuntuforums.org/showthread.php?t=334293&highlight=show+server") 
I believe it is worth looking at.
Years ago I setup a Web/Download file server and use it for testing web pages and transferring files. I setup a Ubuntu server, and I even forgot what version back then, but today It is still running and with 10.04 LTD. It was easy to setup and it just runs flawlessly. Very secure and low maintenance. One nice thing is you have a lot of distros to choose from. I believe I made the right choice for myself.

Edit: One thing I did was installed the Gnome 2.32 destop and I VNC into it to do updates.

---

### Post by Lars Noodén on 2011-06-07
> **Dry Lips said:**
> That's interesting! I've always thought that OpenBSD was a very secure,
but difficult distro. I guess the installation is Arch-style, but yeah, 
I'm definitively considering OpenBSD. 
On the other hand, what I like about Ubuntu is that the community is really 
great. My experience is that if I'm stuck, I get help here most the time.
I think that the OpenBSD guys don't even have their own forum, 
so migration to a completely unfamiliar distro seems a bit intimidating.
They have the mailing lists, [email]misc@openbsd.org[/email] plus other lists.  For example, there is a list for PF.  OpenBSD is easy in that it is very clean, orderly and exceptionally well documented.  Nearly everything can be figured out by following the documentation. That takes a little getting used to, in some cases it takes a lot of getting used to. ;)  

If you like the Ubuntu forum and community, then that would tip my recommendation of Debian back over to Ubuntu Server LTS.  There are not that many technical differences, but you'll have the forum here if you stick with Ubuntu.

---

### Post by Dry Lips on 2011-06-07
**Irv:**
> There is a very long thread out here: [Show us your server.]("http://ubuntuforums.org/showthread.php?t=334293&highlight=show+server") 
I've seen that thread; lost of nice pics!
 
 **collisionystm:**
Is the interface of  Zentyal completely web-based?

**Irv & Lars:**
So I guess you guys are unanimous that LTS is the preferred choice over never versions?

---

### Post by Lars Noodén on 2011-06-07
> **Dry Lips said:**
> **Irv & Lars:**
So I guess you guys are unanimous that LTS is the preferred choice over never versions?

Yes.  Surprises and change are undesirable on a server.

---

### Post by Lars Noodén on 2011-06-07
Sometimes newer versions of applications are available as [backports](https://help.ubuntu.com/community/UbuntuBackports).  But on a server, one usually picks a version and stays with that for the life of the server, if at all possible.

---

### Post by irv on 2011-06-07
Yes I agree that the LTD versions are the way to go for servers. I can't remember the date, but a little over a year ago my server has some hardware issues so I did a hardware upgrade, (motherboard, hard drive, memory, processor, etc). In other words I just built a new one using only a few old parts. I had my system backed up and within a few hours I was up and running again. And I went right back to 10.04 LTD.
By the way I had an old video on how I VNC into my server from my laptop using a local ip address on my home network.
[http://wabasha-server.net/Downloads/MyLaptop.ogv]("http://wabasha-server.net/Downloads/MyLaptop.ogv")

---

### Post by collisionystm on 2011-06-07
> **Dry Lips said:**
> **Irv:**
 
I've seen that thread; lost of nice pics!
 
 **collisionystm:**
Is the interface of  Zentyal completely web-based?

**Irv & Lars:**
So I guess you guys are unanimous that LTS is the preferred choice over never versions?


Mostly, but there is a desktop GUI and the terminal.

---

### Post by efpc2003 on 2011-06-07
CentOS is a distro dedicated server!

---

### Post by Dry Lips on 2011-06-07
OK everyone, thanks so much for the input so far. I appreciate it!

---

### Post by brettg on 2011-06-08
I have to admin FreeBSD at work. I hate it, hates it I does.

As for CentOS, I have to admin that too. I don't hate it to the same degree as FreeBSD but I still don't like the yum/rpm package management system they use. A world of hurt is potentially just around every corner it seems.

That leaves Ubuntu or Debian, unless you want to go truly old school with Slackware which I have no experience with. I believe there is a lot of compiling to be done with Slack, but I could be wrong. 

Debian is a good choice but their roadmap is not very predictable. Which version should I use, stable, unstable, testing? 

Unstable doesn't sound too good, nor does testing, so maybe I should choose "stable". OK then, but when will "stable" be supported until? Also, which one is stable today? Is that Lenny? Or Squeeze? The Debian folks deserve a lot of thanks for all their work but someone needs to take over their marketing ASAP because I've tried to figure out their road map and as far as I can tell there is none.  

Then we get to Ubuntu. Ubuntu definitely has some annoying bugs, such as the latest motd.tail fiasco. 

However most of them are not show stoppers, just annoying. The good thing is you know that 10.04 LTS will be supported for 5 years (server), which is April 2015. It's easy to know where you stand.

My advice is to try everything out and go with what you are comfortable with configuring/administering. Recently I've been experimenting with Debian but I've once again decided to stick with Ubuntu for now.

However, if you do choose Ubuntu for a production server, you should definitely choose the LTS edition because the last thing you want to be doing is dist-upgrades every six months. (Canonical does not recommend skipping versions when doing dist upgrades) 

Having a stable server is the most important thing unless you don't rely on it much and can live with any down time.

If that is not the case then stick with LTS releases.

---

