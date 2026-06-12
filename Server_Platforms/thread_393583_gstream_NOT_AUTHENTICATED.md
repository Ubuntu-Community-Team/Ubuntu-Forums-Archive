---
title: "gstream NOT AUTHENTICATED"
date: 2007-03-25
forum: Server Platforms
---

### Post by castudil on 2007-03-25
hello!

my synaptic has detected new packages updates for gstreamer,
when I want to install appears the following message

NOT AUTHENTICATED

should I trust them anyway?

thanks


## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multive
rse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe mul
tiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe
 multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe m
ultiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted univer
se multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own
 risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe m
ultiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.)
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main
deb [http://debian.websterwood.com/](http://debian.websterwood.com/) dapper main
deb-src [http://debian.websterwood.com/](http://debian.websterwood.com/) dapper main

---

### Post by stalefries on 2007-03-26
The problem is that you've added repositories that are not authenticated with a GPG key. Most likely the problem repo is either the PLF one, or the ones from websterwood.com.

I suggest you close synaptic, put a "#" before each of the above-mentioned repositories, and then re-start synpatic and see what it says.

---

### Post by castudil on 2007-03-26
thank you very much for the information. I will remove the unregistered locations from my repositories.

unfortunately I already took the risk and installed the packages :( . I hope all works fine.

thanks,

---

