---
title: "What's your favorite server distro &amp; why?"
date: 2008-01-21
forum: The Cafe
---

### Post by Sporkman on 2008-01-21
When the discussion turns to what people run on their servers, it seems like more people are running Debian Stable, CentOS, or distros other than Ubuntu Server...

What's YOUR favorite server distro, & if it's not Ubuntu, why did you choose it over Ubuntu?

---

### Post by Lostincyberspace on 2008-01-21
I like CentOs because

Stable 
Has all the server programs startable through ```
service ... start
```
I started with it.
and some other things to minor to mention

---

### Post by a9bejo on 2008-01-22
I'm not an administrator, but if I need a server I install Debian.  At my current workplace and also at the place I was working before that, we use(d) Debian.   I also share a private server with 3 Friends, which is running Gentoo.  But it was not my idea to use Gentoo, and I don't have to maintain the server myself anyway.

The reason I would use Debian and not something else is simply because I know and trust Debian as a server operating system.  I don't know of any reason why I should use a different Distro on the server, even if it is another Debian based OS like Ubuntu.  There are no downsides to Debian and I don't know any useful features that other distros have to offer in comparison.  

Well, I guess if you are administrator at a large company and you need commercial support, it makes sense to consider all the other distros as well.

But again, I'm not a professional admin.  Am I missing something?

---

### Post by DigitalDuality on 2008-01-22
CentOS, Debian, Gentoo (usage flags can come in handy), Solaris, FreeBSD, or OpenBSD.

---

### Post by Sporkman on 2008-01-22
> **DigitalDuality said:**
> CentOS, Debian, Gentoo (usage flags can come in handy), Solaris, FreeBSD, or OpenBSD.

Why not Ubuntu?

---

### Post by notwen on 2008-01-22
Debian Etch.  Simply put, stability. =]  I only use my server for NFS/FTP/webhosting.

---

### Post by Sporkman on 2008-01-22
Has anybody run into stability problems with Ubuntu server?

---

### Post by Lostincyberspace on 2008-01-22
you can ubuntu isn't really well set up for servers.

---

### Post by a9bejo on 2008-01-22
> **Lostincyberspace said:**
> you can ubuntu isn't really well set up for servers.

Huh? What is not well set up in [Ubuntu Server Edition](http://www.ubuntu.com/products/whatisubuntu/serveredition)?

---

### Post by igknighted on 2008-01-22
I've found CentOS/RHEL to be the top server distro's for me, although I do want to give SLED a shot at some point.  Ubuntu seems to be optimized for desktop use, and many server tasks are simply a much bigger PITA than on CentOS.  I would like to take a stab at running Open/Free BSD or Solaris on a server, but I don't have a test box to try it on at the moment.

---

### Post by Lostincyberspace on 2008-01-22
> **a9bejo said:**
> Huh? What is not well set up in [Ubuntu Server Edition](http://www.ubuntu.com/products/whatisubuntu/serveredition)?
The best server distros are set up so that it is easy to manage a server from the command line Ubuntu is set up to run as a GUI all around even the server edition. But you can set it up to work well for servers it just takes more work to get it set up.

---

### Post by a9bejo on 2008-01-22
> **Lostincyberspace said:**
> Ubuntu is set up to run as a GUI all around even the server edition.

That's interesting. I didn't know that. And I think it is a very strange decision to ship a server edition with a DE (I assume it is a full Gnome Desktop , correct?).  I expected it to be pretty much the same as Debian, but with support from canonical. 

> **Lostincyberspace said:**
> 
But you can set it up to work well for servers it just takes more work to get it set up.

Well, I can do this with the Ubuntu desktop edition too ;) . I thought the point of the server edition was to have a release that is already set up as a server ;).

---

### Post by igknighted on 2008-01-22
What!?! Ubuntu server edition has no GUI, unless this is a change with 7.10.  I have used 6.06 and 7.04 server editions and there is no GUI included at all, unless you choose to apt-get it manually after install.  There are no GUI server tools included with Ubuntu either, again unless you scour the repos, where there are a few made by the community.

In contrast, the CentOS installer gives you a choice of exactly what servers to install, and whether you want a GUI and GUI tools installed.  I find the GUI tools quite useful and tend to install them in a very basic Xfce environment, but they are by no means needed.  The CLI tools on CentOS are much better (my opinion... ymmv) than you find in Ubuntu as well.

> **a9bejo said:**
> Well, I can do this with the Ubuntu desktop edition too ;) . I thought the point of the server edition was to have a release that is already set up as a server ;).

They have a LAMP server pre-set-up, but its only a basic LAMP stack.  If you want email or file servers, those you need to do yourself.  And even the basic LAMP will probably take some customization before it is exactly what you want/need.

---

### Post by Xbehave on 2008-01-23
isnt centOS a "pirated" version of RedHat ?
i know GNU guarantees freedom but i think hurting the big companies like novel and RedHat that put alot into upstream development, is ultimately hurting even the community based distros like debian!

if you want a free (as in price) distro why not use one of the many available!

---

### Post by beercz on 2008-01-23
I use debian for my servers- have done for about 6 years, since Potato (v2.2), now running Etch (v4).  I have had no  issues.  Solid and reliable.  No real incentive to change to Ubuntu server or any other distro.  I have not had the need to.

---

### Post by hyper_ch on 2008-01-23
Been running debian servers sind Sarge and never had an issue (well, only in the beginning when I didn't know what I was doing)... but then they run just rock-solid.

---

### Post by gnomeuser on 2008-01-23
My server runs Fedora. It's a personal server so I don't mind the annual upgrade cycle (if I did, CentOS would probably be next on the list of choices). I use Fedora mainly because it's what I know and I trust the developers to provide a secure and stable platform that is well understood and tested. Fedora comes with all the tools I need (and then some), good tools and there is a very supportive community around it's development.

Generally I would recommend that people go with what they already know, if you are good with Ubuntu, then take a look at the Ubuntu Server, read up on how to secure it and have it provide those services you need. Then once comfortable with a setup, look to see if other platforms provide this to you easier or better. Most skills can be transferred over without having to relearn, but it still helps that you learn within the same community you learned the desktop.. same people to turn to for advice, same basic system to master, same commands to use for interacting with the package manager and so on. 

If I had to set up a corporate server I would no doubt go with Red Hat Enterprise Linux, they have by far the best security track record and their support is unparallelled. The distro has wide testing, a 7 year support cycle and new releases roughly every 2 years.. in short it's very well suited for such a deployment.

---

