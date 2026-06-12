---
title: "Importing *.debs into apt-proxy from ServerA to ServerB"
date: 2005-12-11
forum: Server Platforms
---

### Post by GregKroeker on 2005-12-11
I have an Ubuntu Breezy server running 'apt-proxy' on NetworkA, it works great. I set up a new Ubuntu server (for another customer) at my home office and decided I wanted to save time and bandwidth, so on ServerA, I burned the /var/cache/apt-proxy directory and contents the sources.list file and apt-proxy-v2.conf to CD. Then popped the CD into ServerB on NetworkB. Ran 'apt-proxy update' from Ubuntu on my notebook to initialize the cache, so far, so good. When I ran 'apt-proxy-import -i /home/username/debs (directory where I'd copy all the debs from the CD burned on server A), a lot were successfully imported. However, lots fail to import, I get the "no suitable backend found" message, and I am stumped.

I've been reading as much as time allows on this forum and w/ Google's help on importing *.debs, the layout of the 'sources.list' and the 'apt-proxy-v2.conf' file, etc. It's got to have something to do w/ the proxy.conf file, but I have to say that I am either quite dense (very possible), or I just have not found a decent doc on what is really happening in my apt-proxy-v2.conf' in terms of backends. If you have any insight you can give me, even pointing me to another thread I may have overlooked or a doc that explains how backends work and what to do to get this working on ServerB, I'd really appreciate that.

Here are the (IMO) relevant parts of the config files:

****apt-proxy-v2.conf:**** (default config options omitted)
;; Backend servers
;;
;; Place each server in its own [section]

[ubuntu]
;; Ubuntu archive
backends =
[http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/)

[ubuntu-security]
;; Ubuntu security updates
backends =
[http://security.ubuntu.com/ubuntu/pool](http://security.ubuntu.com/ubuntu/pool)


****sources.list****
# deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ breezy main restricted

#deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted
#deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy main restricted
deb [http://127.0.0.1:9999/ubuntu](http://127.0.0.1:9999/ubuntu) breezy main restricted
deb-src [http://127.0.0.1:9999/ubuntu](http://127.0.0.1:9999/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
#deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted
#deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb [http://127.0.0.1:9999/ubuntu](http://127.0.0.1:9999/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://127.0.0.1:9999/ubuntu](http://127.0.0.1:9999/ubuntu) breezy-updates main restricted universe multiverse


## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
#deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb [http://127.0.0.1:9999/ubuntu](http://127.0.0.1:9999/ubuntu) breezy universe universe multiverse
deb-src [http://127.0.0.1:9999/ubuntu](http://127.0.0.1:9999/ubuntu) breezy universe universe multiverse

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://127.0.0.1:9999/ubuntu-security](http://127.0.0.1:9999/ubuntu-security) breezy-security main restricted universe
deb-src [http://127.0.0.1:9999/ubuntu-security](http://127.0.0.1:9999/ubuntu-security) breezy-security main restricted universe

#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb [http://127.0.0.1:9999/ubuntu-security](http://127.0.0.1:9999/ubuntu-security) breezy-security universe multiverse
deb-src [http://127.0.0.1:9999/ubuntu-security](http://127.0.0.1:9999/ubuntu-security) breezy-security universe multiverse

---

### Post by kdw on 2005-12-12
[INDENT]I think this is a bug in the breezy version of apt-proxy, it's in the Debian BTS:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=319005]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=319005")
That thread prompted me to try out apt-cacher.  It also has import tools - tried the apt-proxy-to-apt-cacher script and it imported ~600 packages successfully.  No harm in running both if you have enough space, to see which suits your needs.[/INDENT]

---

### Post by GregKroeker on 2005-12-14
Thanks kdw for that link/explanation. It's a little odd that lots of the debs were successfully imported, others were not. Nonetheless, will take a look at apt-cacher too. Tx again.

---

