---
title: "totally confused by SOURCES SETTING for APT :((((("
date: 2005-05-05
forum: Repositories &amp; Backports
---

### Post by piggyaugu on 2005-05-05
m really a newbie to the linux world and i chose ubuntu for my first taste. but m now totally confused by *sources.list* ](*,)  .

I have followed step by step the part for adding extra repositories in *Unofficial Ubuntu 5.04 Starter Guide*, but now m still not able to connect to the new sources. i think i have mistaken sth in the times i edited it. 

Could anybody give a right version of *sources.list* ? that'll be so kind. thx ;-)

---

### Post by bored2k on 2005-05-05
> ## UBUNTU MAIN
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## UBUNTU UNIVERSE
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

## UBUNTU SECURITY
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## UBUNTU MULTIVERSE
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## MARILLAT
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main


Since you a self proclaimed newbie, I suggest you type this on a terminal window:
```
wget http://download.ubuntuforums.org/ubuntusetup/ubuntusetup.sh && sudo sh ubuntusetup.sh
```

---

### Post by poofyhairguy on 2005-05-05
> **piggyaugu]m really a newbie to the linux world and i chose ubuntu for my first taste. but m now totally confused by *sources.list* ](*,)  .

I have followed step by step the part for adding extra repositories in *Unofficial Ubuntu 5.04 Starter Guide*, but now m still not able to connect to the new sources. i think i have mistaken sth in the times i edited it. 

Could anybody give a right version of *sources.list* ? that'll be so kind. thx  said:**
> 

Here is one that probably has everything you want. Be careful with it:

[QUOTE]## deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted  

Wrong forum bye the way.

---

### Post by poofyhairguy on 2005-05-05
[QUOTE=bored2k]## MARILLAT
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
#deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main[/QUOTE]

I personally don't advise people to use these lines. Can cause problems...

---

### Post by bored2k on 2005-05-05
[QUOTE=poofyhairguy]I personally don't advise people to use these lines. Can cause problems...[/QUOTE]
 I always block them, but since the person is following Chua Wen Kiat's guide, some stuff there are only available through Marillat.

---

### Post by piggyaugu on 2005-05-05
thx a lot to all :)  :) . i can get synaptic running now \\:D/ , although i cant connect to the last 3 FTPs. 

sorry for mistaking forum  :-#  can you tell me where is the section for the ubuntu newbies??

i've still a problem. i can refresh the list with synaptic and soft update manager, but i cant fetch anything through * apt-get * or even * wget *. i connect to the internet through a http proxy in school. is the proxy server making the problem in terminal mode?

---

### Post by bored2k on 2005-05-05
[QUOTE=piggyaugu]thx a lot to all :)  :) . i can get synaptic running now \\:D/ , although i cant connect to the last 3 FTPs. 

sorry for mistaking forum  :-#  can you tell me where is the section for the ubuntu newbies??

i've still a problem. i can refresh the list with synaptic and soft update manager, but i cant fetch anything through * apt-get * or even * wget *. i connect to the internet through a http proxy in school. is the proxy server making the problem in terminal mode?[/QUOTE]
 1. You CAN connect to the last three, they just give a GPG signature "error"
2. WGet has nothing to do with apt-get
3. Whats the apt-get error?

---

### Post by piggyaugu on 2005-05-05
[INDENT]augu@ubuntu:~$ sudo apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (216.165.129.138). - connect (113 No route to host)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Err [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release.gpg
  Could not connect to ftp.nerim.net:21 (62.4.17.14). - connect (113 No route to host) [IP: 62.4.17.14 21]
Err [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release.gpg
  Could not connect to ftp.nerim.net:21 (62.4.17.14). - connect (113 No route to host) [IP: 62.4.17.14 21]
Err [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release.gpg
  Cannot initiate the connection to ftp.nerim.net:21 (2001:7a8:1:5::14). - connect (101 Network is unreachable) [IP: 2001:7a8:1:5::14 21]
Ign [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg
  Could not connect to archive.ubuntu.com:80 (82.211.81.138). - connect (113 No route to host) [IP: 82.211.81.138 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.151). - connect (113 No route to host) [IP: 82.211.81.151 80]
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports Release.gpg
  Could not connect to backports.ubuntuforums.org:80 (66.246.118.209), connection timed out
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
11% [Connecting to us.archive.ubuntu.com (216.165.129.138)] [Connecting to secu[/INDENT] 

that's the result of "apt-get update", i dont quite understand. i do get the lists in synaptic.

---

### Post by bored2k on 2005-05-05
[QUOTE=piggyaugu][INDENT]augu@ubuntu:~$ sudo apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (216.165.129.138). - connect (113 No route to host)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Err [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release.gpg
  Could not connect to ftp.nerim.net:21 (62.4.17.14). - connect (113 No route to host) [IP: 62.4.17.14 21]
Err [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release.gpg
  Could not connect to ftp.nerim.net:21 (62.4.17.14). - connect (113 No route to host) [IP: 62.4.17.14 21]
Err [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release.gpg
  Cannot initiate the connection to ftp.nerim.net:21 (2001:7a8:1:5::14). - connect (101 Network is unreachable) [IP: 2001:7a8:1:5::14 21]
Ign [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg
  Could not connect to archive.ubuntu.com:80 (82.211.81.138). - connect (113 No route to host) [IP: 82.211.81.138 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.151). - connect (113 No route to host) [IP: 82.211.81.151 80]
Err [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) hoary-backports Release.gpg
  Could not connect to backports.ubuntuforums.org:80 (66.246.118.209), connection timed out
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
11% [Connecting to us.archive.ubuntu.com (216.165.129.138)] [Connecting to secu[/INDENT] 

that's the result of "apt-get update", i dont quite understand. i do get the lists in synaptic.[/QUOTE]
 Do this:
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --armor --export 1F41B907 | sudo apt-key add -
sudo apt-get update

---

### Post by henriquemaia on 2005-05-05
For a moment I thought that this was a guide on how to get your apt.sources list totally messed up!

Just kidding, lol.

---

### Post by bored2k on 2005-05-05
[QUOTE=henriquemaia]For a moment I thought that this was a guide on how to get your apt.sources list totally messed up!

Just kidding, lol.[/QUOTE]
 heh. All that [code] will surely scare newbies away ;)

---

### Post by piggyaugu on 2005-05-06
well, m still wondering the problem with the net connection of the term. 'cause i got these when  i tried to creat gpg key.

[I]augu@ubuntu:~$ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg: /home/augu/.gnupg: directory created
gpg: new configuration file `/home/augu/.gnupg/gpg.conf' created
gpg: WARNING: options in `/home/augu/.gnupg/gpg.conf' are not yet active during this run
gpg: keyring `/home/augu/.gnupg/secring.gpg' created
gpg: keyring `/home/augu/.gnupg/pubring.gpg' created
gpg: can't get key from keyserver: No route to host
gpg: Total number processed: 0[/I]

---

