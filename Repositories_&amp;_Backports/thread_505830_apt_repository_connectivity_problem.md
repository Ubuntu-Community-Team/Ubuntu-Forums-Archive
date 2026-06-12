---
title: "apt repository connectivity problem"
date: 2007-07-20
forum: Repositories &amp; Backports
---

### Post by asalford on 2007-07-20
Thanks to all in advance for reading this post.

I am having difficulty downloading from the repositories.  I am running breezy 5.10.  The following data are the error messages, my config, and what I have tried to resolve the issue.

sudo apt-get update
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
  404 Not Found [IP: 82.211.81.138 80]
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates Release.gpg
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy Release.gpg
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  404 Not Found [IP: 82.211.81.138 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources
  404 Not Found [IP: 91.189.89.8 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
  404 Not Found [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
  404 Not Found [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
  404 Not Found [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
  404 Not Found [IP: 82.211.81.138 80]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Sources
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
  404 Not Found [IP: 91.189.89.8 80]
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
  404 Not Found [IP: 91.189.89.8 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
  404 Not Found [IP: 82.211.81.138 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
  404 Not Found [IP: 82.211.81.138 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Sources
  404 Not Found [IP: 91.189.89.8 80]
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy Release
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Sources
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Sources
  404 Not Found [IP: 91.189.89.8 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Sources
  404 Not Found [IP: 91.189.89.8 80]
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/restricted Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/universe Sources
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/multiverse Sources
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Sources
  404 Not Found
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/restricted Sources
  404 Not Found
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/universe Sources
  404 Not Found
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy/multiverse Sources
  404 Not Found
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.138 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz)  404 Not Found [IP: 82.211.81.138 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz)  404 Not Found [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz)  404 Not Found [IP: 82.211.81.138 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/multiverse/source/Sources.gz)  404 Not Found [IP: 82.211.81.138 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/main/source/Sources.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/restricted/source/Sources.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/universe/source/Sources.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/breezy-backports/multiverse/source/Sources.gz)  404 Not Found [IP: 91.189.89.8 80]
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz)  404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz)  404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz](http://au.archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz)  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

sources list 

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) breezy-updates main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) breezy universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) breezy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse


Tried it with au. default, with us, and without anything.

looked around at some of the posts 

I verified dns resolution with ping
ping yahoo.com
PING yahoo.com (216.109.112.135) 56(84) bytes of data.
64 bytes from w2.rc.vip.dcn.yahoo.com (216.109.112.135): icmp_seq=1 ttl=48 time=29.7 ms
64 bytes from w2.rc.vip.dcn.yahoo.com (216.109.112.135): icmp_seq=2 ttl=49 time=30.0 ms
64 bytes from w2.rc.vip.dcn.yahoo.com (216.109.112.135): icmp_seq=3 ttl=48 time=34.2 ms

--- yahoo.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 29.740/31.340/34.222/2.046 ms

cat /etc/resolv.conf
nameserver 205.152.37.23
nameserver 205.152.132.23

I tried this:

cd /var/lib/apt/lists
sudo rm * -f
cd partial
sudo rm * -f
sudo apt-get update

I made sure I can resolve & reach the archive

ping us.archive.ubuntu.com
PING us.archive.ubuntu.com (91.189.89.6) 56(84) bytes of data.
64 bytes from forster.canonical.com (91.189.89.6): icmp_seq=1 ttl=43 time=104 ms64 bytes from forster.canonical.com (91.189.89.6): icmp_seq=2 ttl=43 time=103 ms64 bytes from forster.canonical.com (91.189.89.6): icmp_seq=3 ttl=43 time=105 ms
--- us.archive.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 103.695/104.502/105.196/0.617 ms


Any ideas where to look next or what the problem might be?

---

### Post by smartboyathome on 2007-07-20
I think the repos have been shut down, do to it not being supported anymore. Instead, substitute US with old-releases, or better yet, UPGRADE! If you cant run the livecd, just use the alternate CD. it is worth it, trust me. ;)

---

### Post by bapoumba on 2007-07-21
Hello :)

As smartboyathome said, the archives for breezy are not on the main servers any longer.
Have a look here:
[http://ubuntuforums.org/showpost.php?p=3026621&postcount=13]("http://ubuntuforums.org/showpost.php?p=3026621&postcount=13")
[http://old-releases.ubuntu.com/releases/]("http://old-releases.ubuntu.com/releases/")

So you can, if you prefer, change your sources.list and keep breezy, provided you are aware of the drawbacks mentioned by fujitsu.

---

### Post by asalford on 2007-07-21
Thanks for the posts.  I had feared this would be the answer.  I just hate to bother a working machine that is mission critical to my family.  

but to go forward, guess will need to do something.  Thanks for the help

---

### Post by bapoumba on 2007-07-22
@ asalford:
> **fujitsu said:**
> 
That said, if you *really* want to be using a completely unsupported and likely insecure release, you can replace archive.ubuntu.com with old-releases.ubuntu.com, which still hosts the (no longer updated) repositories for warty, hoary and breezy.
If you change your sources.list, you can still keep breezy. There wont be any security updates (and this has been the case since breezy became unsupported), but you can still install packages if you need so.

---

### Post by asalford on 2007-07-24
changed the breezy line to dapper and was able to get a successful upgrade.  Thanks to all for your help :)

---

