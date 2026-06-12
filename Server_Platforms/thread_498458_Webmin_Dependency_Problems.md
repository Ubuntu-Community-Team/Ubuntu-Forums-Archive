---
title: "Webmin Dependency Problems"
date: 2007-07-11
forum: Server Platforms
---

### Post by djearwig on 2007-07-11
Hello,

I am trying to install Webmin to graphically manage my Feisty server; however, I am getting dependency errors when I try to install the package...

administrator@linux1:/etc/apt$ sudo apt-get install webmin
Reading package lists... Done
Building dependency tree
Reading state information... Done
webmin is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  webmin: Depends: libnet-ssleay-perl but it is not installable
          Depends: libio-pty-perl but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


I downloaded the two packages causing the issue, but now I don't know where to place them. :(
Or do I just need to install the latest version of perl?

Can someone please assist me?

Thank you.

---

### Post by tgm4883 on 2007-07-11
> **djearwig said:**
> Hello,

I am trying to install Webmin to graphically manage my Feisty server; however, I am getting dependency errors when I try to install the package...

administrator@linux1:/etc/apt$ sudo apt-get install webmin
Reading package lists... Done
Building dependency tree
Reading state information... Done
webmin is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  webmin: Depends: libnet-ssleay-perl but it is not installable
          Depends: libio-pty-perl but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


I downloaded the two packages causing the issue, but now I don't know where to place them. :(
Or do I just need to install the latest version of perl?

Can someone please assist me?

Thank you.

sudo apt-get install libnet-ssleay-perl libio-pty-perl

You may have to remove webmin first, i don't remember if I had to or not.

:EDIT:

If they still aren't found, could you post your sources.list

---

### Post by stalker145 on 2007-07-11
> **djearwig said:**
> Hello,

I am trying to install Webmin to graphically manage my Feisty server; however, I am getting dependency errors when I try to install the package...

administrator@linux1:/etc/apt$ sudo apt-get install webmin
Reading package lists... Done
Building dependency tree
Reading state information... Done
webmin is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  webmin: Depends: libnet-ssleay-perl but it is not installable
          Depends: libio-pty-perl but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


I downloaded the two packages causing the issue, but now I don't know where to place them. :(
Or do I just need to install the latest version of perl?

Can someone please assist me?

Thank you.


I would suggest that you head for the [WebMin web site]("http://www.webmin.com") and grab the .deb. It worked perfectly for me downloading all necessary dependencies.

---

### Post by djearwig on 2007-07-11
> **tgm4883 said:**
> sudo apt-get install libnet-ssleay-perl libio-pty-perl

You may have to remove webmin first, i don't remember if I had to or not.

:EDIT:

If they still aren't found, could you post your sources.list

I already tried that.  And I have all the universes/multiverses in my sources list:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted unive$
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted u$

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

deb [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge contrib

That's all my sources...

So, do you see something that I am missing?

---

### Post by djearwig on 2007-07-11
> **stalker145 said:**
> I would suggest that you head for the [WebMin web site]("http://www.webmin.com") and grab the .deb. It worked perfectly for me downloading all necessary dependencies.

That was the first thing I tried.  I dpkg the webmin install package and that was when I got flooded with dependency issues.  I managed to resolve all but these 2...

---

### Post by tgm4883 on 2007-07-11
You say you have downloaded the two files you need.  Are they in deb packages? If so you should just be able to 

```
sudo dpkg -i "package 1.deb" "package 2.deb"
```

:EDIT:

You did sudo apt-get update after adding the repos right?

---

### Post by djearwig on 2007-07-11
> **tgm4883 said:**
> You say you have downloaded the two files you need.  Are they in deb packages? If so you should just be able to 

```
sudo dpkg -i "package 1.deb" "package 2.deb"
```

:EDIT:

You did sudo apt-get update after adding the repos right?

Yes, they were deb packages that I unpacked.  Now I am wondering where I should move these files to...

---

### Post by tgm4883 on 2007-07-11
> **djearwig said:**
> Yes, they were deb packages that I unpacked.  Now I am wondering where I should move these files to...

Why did you unpack them?  dpkg -i should install them where they are supposed to go

---

### Post by djearwig on 2007-07-11
> **tgm4883 said:**
> Why did you unpack them?  dpkg -i should install them where they are supposed to go

Well then, that's maybe what I did wrong.
Let's go see...

---

### Post by Endwin on 2007-07-11
What I do to install webmin is install the downloaded package with 

```
dpkh -i webmin*
```

then once it fails I do 

```
aptitude -f install
```

Aptitude will then try and resolve the issue the first suggestion is usually to uninstall webmin. I select no for that then it advises installing all the dependencies. to which I click yes and then webmin works.

---

### Post by djearwig on 2007-07-11
> **djearwig said:**
> Well then, that's maybe what I did wrong.
Let's go see...

Nope:

administrator@linux1:/tmp$ sudo dpkg -i webmin_1.350_all.deb
Selecting previously deselected package webmin.
(Reading database ... 24061 files and directories currently installed.)
Unpacking webmin (from webmin_1.350_all.deb) ...
dpkg: dependency problems prevent configuration of webmin:
 webmin depends on libnet-ssleay-perl; however:
  Package libnet-ssleay-perl is not installed.
 webmin depends on libio-pty-perl; however:
  Package libio-pty-perl is not installed.
dpkg: error processing webmin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 webmin


Poopy!

---

### Post by tgm4883 on 2007-07-11
> **djearwig said:**
> I already tried that.  And I have all the universes/multiverses in my sources list:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted unive$
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted u$

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

deb [http://download.webmin.com/download/repository](http://download.webmin.com/download/repository) sarge contrib

That's all my sources...

So, do you see something that I am missing?

Here is mine 

```
## See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
## newer versions of the distribution.

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

## Uncomment deb-src if you wish to download the source packages

## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
#deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
#deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
#deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://launchpad.net/products/medibuntu/+bugs
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
#deb-src http://medibuntu.sos-sts.com/repo/ feisty free non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu feisty-commercial main

## enlightenment e17 beta, use at your own risk
## E17 is in Beta and may break or break your system
#deb http://edevelop.org/pkg-e/ubuntu feisty e17
#deb http://e17.dunnewind.net/ubuntu feisty e17
#deb-src http://edevelop.org/pkg-e/ubuntu feisty e17

## Virtualbox Repos
deb http://www.virtualbox.org/debian feisty non-free

## Treviño's Ubuntu feisty EyeCandy Repository (GPG key: 81836EBF - DD800CD9)
## Many eyecandy 3D apps like Beryl, Compiz, Fusion and kiba-dock snapshots
## built using latest available (working) sources from git/svn/cvs... 
deb http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy-amd64

## Screenlets
deb http://hendrik.kaju.pri.ee/ubuntu feisty screenlets

## Avant Window Navigator
#deb http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator
#deb-src http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator
```

apt-get installs it in mine.  I have a few more repos than you, but after checking libnet-ssleay-perl is located in main, so it should be working.  I only have 3 ideas.

1.  Your debian sarge repo is causing some sort of conflict.
2.  You didn't run "sudo apt-get update" then "sudo apt-get upgrade" then "sudo apt-get install libnet-ssleay-perl libio-pty-perl

So I would recommend that you do this.  Comment out the debian sarge repo, then do the following one at a time.  If you get any errors, stop and let us know.

```
sudo dpkg remove --purge webmin
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install libnet-ssleay-perl libio-pty-perl
```

---

### Post by djearwig on 2007-07-11
OK, but it's quittin' time for today.  I'll try first thing in the morning and let you know how it goes...

Thanks for the help!

---

### Post by djearwig on 2007-07-12
Alright, I removed webmin, then ran the 'sudo apt-get update' command; however, it threw A LOT of errors at me.  Stuff like :

[COLOR="Navy"]Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg
  Could not resolve 'us.archive.ubuntu.com'[/COLOR]

and

[COLOR="Navy"]Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'[/COLOR]

This leads me to believe that there may be something wrong with my internet connection?  I'm fairly certain I configured this correctly during set-up, but...  How do I check my settings?

Thanks again for helping this Windows user in a linux world...

---

### Post by djearwig on 2007-07-16
Any ideas from anybody?

---

### Post by tgm4883 on 2007-07-16
Have you tried ping to see if your internet connection is working?  

if it does not work, you could try
sudo ifconfig eth0 down
sudo ifconfig eth0 up

---

### Post by djearwig on 2007-07-18
Yes, my internet connection is working.  I can ping both inside and outside my network.
However. I can only ping IP addresses, not the actual domain name.  This leads me to believe something may be wrong with the DNS?  Is there a way I can check the settings?

Thank you in advance.  I really super-duper appreciate it...

---

### Post by djearwig on 2007-07-25
Anybody have a solution for me?

Why can I ping IPs, but not domains?

I cannot use my repositories because of this problem.

I'd really appreciate some help.

Thanks!!!

---

### Post by tgm4883 on 2007-07-25
ifconfig --help

You need to set it to a roper DNS server, whether it is a real DNS server or a router that forward.

---

