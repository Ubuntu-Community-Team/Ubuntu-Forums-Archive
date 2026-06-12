---
title: "Feisty repos"
date: 2007-04-10
forum: Repositories &amp; Backports
---

### Post by griz on 2007-04-10
Hi all,

Can anyone recommend a good repository list for Feisty.  I'm in Australia so, should I use Australian repos or not have any country specific codes in the list?

Thanks in advance

Griz.

---

### Post by Kateikyoushi on 2007-04-11
I would recommend to use the local repositories with enabled universe and multiverse I do not have other repos in my sources.list.

---

### Post by krazyd on 2007-04-11
My sources.list looks like this:```

deb http://ftp.iinet.net.au/pub/ubuntu/ feisty main restricted universe multiverse
deb-src http://ftp.iinet.net.au/pub/ubuntu/ feisty main restricted universe multiverse

deb http://ftp.iinet.net.au/pub/ubuntu/ feisty-updates main restricted universe multiverse
deb-src http://ftp.iinet.net.au/pub/ubuntu/ feisty-updates main restricted universe multiverse

deb http://ftp.iinet.net.au/pub/ubuntu/ feisty-security main restricted universe multiverse
deb-src http://ftp.iinet.net.au/pub/ubuntu/ feisty-security main restricted universe multiverse

deb http://ftp.iinet.net.au/pub/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://ftp.iinet.net.au/pub/ubuntu/ feisty-backports main restricted universe multiverse


```

---

### Post by mlind on 2007-04-11
> **griz said:**
> Hi all,

Can anyone recommend a good repository list for Feisty.  I'm in Australia so, should I use Australian repos or not have any country specific codes in the list?

Thanks in advance

Griz.

You can find nearest official Ubuntu mirror from
[https://wiki.ubuntu.com/Mirrors](https://wiki.ubuntu.com/Mirrors)

For one of the Australian mirrors on the list:
```

deb http://mirror.optus.net/ubuntu feisty main restricted universe multiverse
deb http://mirror.optus.net/ubuntu feisty-updates main restricted universe multiverse
deb http://mirror.optus.net/ubuntu feisty-security main restricted universe multiverse
#deb http://mirror.optus.net/ubuntu feisty-proposed main restricted universe multiverse

```

---

### Post by griz on 2007-04-12
Thanks people.  I've tried the iinet repos and they seem to work a lot better than the default ones.  

Griz

---

### Post by LookTJ on 2007-04-12
```

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ feisty free
deb http://medibuntu.sos-sts.com/repo/ feisty non-free
deb-src http://medibuntu.sos-sts.com/repo/ feisty free
deb-src http://medibuntu.sos-sts.com/repo/ feisty non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main

## Listen
#deb http://theli.free.fr/packages/ feisty listen

```

---

### Post by andrew.46 on 2007-04-26
Hi,

 Good to see a fellow Australian:

> **griz said:**
> Hi all, Can anyone recommend a good repository list for Feisty.  I'm in Australia so, should I use Australian repos or not have any country specific codes in the list?.

 I have found the Australian repos to actually be a lot slower than the US ones so I do not use the Australian ones at all. You might be interested to see the [Ubuntu Source List Generator]("http://www.ubuntu-nl.org/source-o-matic/"). It will generate a source.list of the most essential repos and leave you to add any extras. Just be sure that you are confident in manipulating this file before you start :) .

                   Andrew

---

