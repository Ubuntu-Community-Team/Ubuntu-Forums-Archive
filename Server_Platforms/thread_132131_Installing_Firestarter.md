---
title: "Installing Firestarter"
date: 2006-02-17
forum: Server Platforms
---

### Post by Emma S on 2006-02-17
I'm wondering if anyone can help me out,I'm trying to install firestarter:
```
Reading package lists... Done
Building dependency tree... Done
You might want to run \uffff\uffff\uffffapt-get -f install\uffff\uffff\uffff to correct these:
The following packages have unmet dependencies:
  python2.4-gd: Depends: libgd2-noxpm (>= 2.0.33) but it is not going to be installed or
                         libgd2-xpm (>= 2.0.33) but it is not going to be installed
E: Unmet dependencies. Try \uffff\uffff\uffffapt-get -f install\uffff\uffff\uffff with no packages (or specify a solution).

```
[http://img152.imageshack.us/img152/1053/fsterminal4jo.jpg](http://img152.imageshack.us/img152/1053/fsterminal4jo.jpg)
Screenshot of it showing the ufffs as a character.

I'm wondering what i'm supposed to do,judging from that,as I have no idea-thanks in advance!

---

### Post by byen on 2006-02-17
Oh simple. This is what you do:

sudo apt-get install firestarter
sudo apt-get -f install

The first one installs firestarter and the second command installs all the unmet dependencies. The second command can also be used when you have dependencies while installing other programs. Hope that helps. Goodluck and welcome to Ubuntu!

---

### Post by Emma S on 2006-02-18
[QUOTE=byen]Oh simple. This is what you do:

sudo apt-get install firestarter
sudo apt-get -f install

The first one installs firestarter and the second command installs all the unmet dependencies. The second command can also be used when you have dependencies while installing other programs. Hope that helps. Goodluck and welcome to Ubuntu![/QUOTE]
Hi Byen,thanks for the help and welcome! :mrgreen: 
I've been using Hoary for a while but haven't got a lot to show for it in terms of CLI knowledge.


```
 
emma@cpc2-stre2-6-1-cust201:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgd2-noxpm
Suggested packages:
  libgd-tools
The following NEW packages will be installed:
  libgd2-noxpm
0 upgraded, 1 newly installed, 0 to remove and 691 not upgraded.
Need to get 197kB of archives.
After unpacking 635kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com breezy/main libgd2-noxpm 2.0.33-1.1ubuntu1 [197k B]
Fetched 197kB in 1s (118kB/s)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_br eezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/non-f ree Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dist s_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_ dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/non-f ree Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecont rib_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or direc tory)

Preconfiguring packages ...
Selecting previously deselected package libgd2-noxpm.
(Reading database ... 57900 files and directories currently installed.)
Unpacking libgd2-noxpm (from .../libgd2-noxpm_2.0.33-1.1ubuntu1_amd64.deb) ...
Setting up libgd2-noxpm (2.0.33-1.1ubuntu1) ...
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_br eezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/non-f ree Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dist s_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_ dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/non-f ree Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecont rib_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or direc tory)
W: You may want to run apt-get update to correct these problems
emma@cpc2-stre2-6-1-cust201:~$ sudo apt-get update
Ign http://security.ubuntu.com breezy-security Release.gpg
Ign http://security.ubuntu.com breezy-security Release
Ign http://security.ubuntu.com breezy-security/main Packages
Ign http://security.ubuntu.com breezy-security/restricted Packages
Ign http://security.ubuntu.com breezy-security/main Sources
Ign http://security.ubuntu.com breezy-security/restricted Sources
Ign http://security.ubuntu.com breezy-security/universe Packages
Ign http://security.ubuntu.com breezy-security/universe Sources
Ign http://security.ubuntu.com breezy-security/multiverse Packages
Ign http://security.ubuntu.com breezy-security/multiverse Sources
Err http://security.ubuntu.com breezy-security/main Packages
  Bad header line [IP: ]
Err http://security.ubuntu.com breezy-security/restricted Packages
  Bad header line [IP: ]
Err http://security.ubuntu.com breezy-security/main Sources
  Bad header line [IP: ]
Err http://security.ubuntu.com breezy-security/restricted Sources
  0 * [IP:  ]
Get:1 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:2 http://security.ubuntu.com breezy-security/universe Packages [3787B]
Get:3 http://security.ubuntu.com breezy-security/universe Sources [12.2kB]
Get:4 http://security.ubuntu.com breezy-security/multiverse Packages [899B]
Get:5 http://security.ubuntu.com breezy-security/multiverse Sources [32.4kB]
Ign http://archive.ubuntu.com breezy-updates Release.gpg
Ign http://archive.ubuntu.com breezy Release
Ign http://antesis.freecontrib.org breezy Release.gpg
Ign http://antesis.freecontrib.org breezy Release.gpg
Get:6 http://archive.ubuntu.com breezy-updates Release [30.9kB]
Ign http://antesis.freecontrib.org breezy Release
Ign http://antesis.freecontrib.org breezy Release
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Ign http://antesis.freecontrib.org breezy/free Packages
Ign http://antesis.freecontrib.org breezy/non-free Packages
Ign http://antesis.freecontrib.org breezy/free Sources
Ign http://antesis.freecontrib.org breezy/non-free Sources
Ign http://antesis.freecontrib.org breezy/free Packages
Ign http://antesis.freecontrib.org breezy/non-free Packages
Ign http://antesis.freecontrib.org breezy/free Sources
Ign http://antesis.freecontrib.org breezy/non-free Sources
Err http://antesis.freecontrib.org breezy/free Packages
  404 Not Found
Err http://antesis.freecontrib.org breezy/non-free Packages
  404 Not Found
Hit http://antesis.freecontrib.org breezy/free Sources
Hit http://antesis.freecontrib.org breezy/non-free Sources
Err http://antesis.freecontrib.org breezy/free Packages
  404 Not Found
Err http://antesis.freecontrib.org breezy/non-free Packages
  404 Not Found
Hit http://antesis.freecontrib.org breezy/free Sources
Hit http://antesis.freecontrib.org breezy/non-free Sources
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/multiverse Sources
Get:7 http://archive.ubuntu.com breezy-updates/main Packages [31.3kB]
Get:8 http://archive.ubuntu.com breezy-updates/restricted Packages [14B]
Get:9 http://archive.ubuntu.com breezy-updates/main Sources [15.8kB]
Get:10 http://archive.ubuntu.com breezy-updates/restricted Sources [14B]
Fetched 127kB in 8s (14.3kB/s)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/bin ary-amd64/Packages.gz  Bad header line [IP:  ]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restrict ed/binary-amd64/Packages.gz  Bad header line [IP:  ]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/sou rce/Sources.gz  Bad header line [IP:  ]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restrict ed/source/Sources.gz  0 * [IP:  ]
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/f ree/binary-amd64/Packages.gz  404 Not Found
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/n on-free/binary-amd64/Packages.gz  404 Not Found
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/ breezy/free/binary-amd64/Packages.gz  404 Not Found
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/ breezy/non-free/binary-amd64/Packages.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used  instead.

```

I've noticed Breezy is in all the URLs yet I'm using Hoary,excluding the 404s-would this be the reason for the errors? how can I fix this?
Thanks again!

---

### Post by o_fortuna on 2006-02-18
[QUOTE=Emma S]Hi Byen,thanks for the help and welcome! :mrgreen: 
I've been using Hoary for a while but haven't got a lot to show for it in terms of CLI knowledge.


```
 
emma@cpc2-stre2-6-1-cust201:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libgd2-noxpm
Suggested packages:
  libgd-tools
The following NEW packages will be installed:
  libgd2-noxpm
0 upgraded, 1 newly installed, 0 to remove and 691 not upgraded.
Need to get 197kB of archives.
After unpacking 635kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.ubuntu.com breezy/main libgd2-noxpm 2.0.33-1.1ubuntu1 [197k B]
Fetched 197kB in 1s (118kB/s)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_br eezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/non-f ree Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dist s_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_ dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/non-f ree Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecont rib_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or direc tory)

Preconfiguring packages ...
Selecting previously deselected package libgd2-noxpm.
(Reading database ... 57900 files and directories currently installed.)
Unpacking libgd2-noxpm (from .../libgd2-noxpm_2.0.33-1.1ubuntu1_amd64.deb) ...
Setting up libgd2-noxpm (2.0.33-1.1ubuntu1) ...
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dists_br eezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/non-f ree Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_plf_dist s_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecontrib_ dists_breezy_free_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/non-f ree Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirrors_ubuntu_freecont rib_dists_breezy_non-free_binary-amd64_Packages) - stat (2 No such file or direc tory)
W: You may want to run apt-get update to correct these problems
emma@cpc2-stre2-6-1-cust201:~$ sudo apt-get update
Ign http://security.ubuntu.com breezy-security Release.gpg
Ign http://security.ubuntu.com breezy-security Release
Ign http://security.ubuntu.com breezy-security/main Packages
Ign http://security.ubuntu.com breezy-security/restricted Packages
Ign http://security.ubuntu.com breezy-security/main Sources
Ign http://security.ubuntu.com breezy-security/restricted Sources
Ign http://security.ubuntu.com breezy-security/universe Packages
Ign http://security.ubuntu.com breezy-security/universe Sources
Ign http://security.ubuntu.com breezy-security/multiverse Packages
Ign http://security.ubuntu.com breezy-security/multiverse Sources
Err http://security.ubuntu.com breezy-security/main Packages
  Bad header line [IP: ]
Err http://security.ubuntu.com breezy-security/restricted Packages
  Bad header line [IP: ]
Err http://security.ubuntu.com breezy-security/main Sources
  Bad header line [IP: ]
Err http://security.ubuntu.com breezy-security/restricted Sources
  0 * [IP:  ]
Get:1 http://archive.ubuntu.com breezy Release.gpg [189B]
Get:2 http://security.ubuntu.com breezy-security/universe Packages [3787B]
Get:3 http://security.ubuntu.com breezy-security/universe Sources [12.2kB]
Get:4 http://security.ubuntu.com breezy-security/multiverse Packages [899B]
Get:5 http://security.ubuntu.com breezy-security/multiverse Sources [32.4kB]
Ign http://archive.ubuntu.com breezy-updates Release.gpg
Ign http://archive.ubuntu.com breezy Release
Ign http://antesis.freecontrib.org breezy Release.gpg
Ign http://antesis.freecontrib.org breezy Release.gpg
Get:6 http://archive.ubuntu.com breezy-updates Release [30.9kB]
Ign http://antesis.freecontrib.org breezy Release
Ign http://antesis.freecontrib.org breezy Release
Hit http://archive.ubuntu.com breezy/main Packages
Hit http://archive.ubuntu.com breezy/restricted Packages
Ign http://antesis.freecontrib.org breezy/free Packages
Ign http://antesis.freecontrib.org breezy/non-free Packages
Ign http://antesis.freecontrib.org breezy/free Sources
Ign http://antesis.freecontrib.org breezy/non-free Sources
Ign http://antesis.freecontrib.org breezy/free Packages
Ign http://antesis.freecontrib.org breezy/non-free Packages
Ign http://antesis.freecontrib.org breezy/free Sources
Ign http://antesis.freecontrib.org breezy/non-free Sources
Err http://antesis.freecontrib.org breezy/free Packages
  404 Not Found
Err http://antesis.freecontrib.org breezy/non-free Packages
  404 Not Found
Hit http://antesis.freecontrib.org breezy/free Sources
Hit http://antesis.freecontrib.org breezy/non-free Sources
Err http://antesis.freecontrib.org breezy/free Packages
  404 Not Found
Err http://antesis.freecontrib.org breezy/non-free Packages
  404 Not Found
Hit http://antesis.freecontrib.org breezy/free Sources
Hit http://antesis.freecontrib.org breezy/non-free Sources
Hit http://archive.ubuntu.com breezy/main Sources
Hit http://archive.ubuntu.com breezy/restricted Sources
Hit http://archive.ubuntu.com breezy/universe Packages
Hit http://archive.ubuntu.com breezy/universe Sources
Hit http://archive.ubuntu.com breezy/multiverse Packages
Hit http://archive.ubuntu.com breezy/multiverse Sources
Get:7 http://archive.ubuntu.com breezy-updates/main Packages [31.3kB]
Get:8 http://archive.ubuntu.com breezy-updates/restricted Packages [14B]
Get:9 http://archive.ubuntu.com breezy-updates/main Sources [15.8kB]
Get:10 http://archive.ubuntu.com breezy-updates/restricted Sources [14B]
Fetched 127kB in 8s (14.3kB/s)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/bin ary-amd64/Packages.gz  Bad header line [IP:  ]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restrict ed/binary-amd64/Packages.gz  Bad header line [IP:  ]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/main/sou rce/Sources.gz  Bad header line [IP:  ]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/breezy-security/restrict ed/source/Sources.gz  0 * [IP:  ]
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/f ree/binary-amd64/Packages.gz  404 Not Found
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/n on-free/binary-amd64/Packages.gz  404 Not Found
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/ breezy/free/binary-amd64/Packages.gz  404 Not Found
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/ breezy/non-free/binary-amd64/Packages.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used  instead.

```

I've noticed Breezy is in all the URLs yet I'm using Hoary,excluding the 404s-would this be the reason for the errors? how can I fix this?
Thanks again![/QUOTE]
Type sudo gedit /etc/apt/sources.list and get rid of/change everything that has Breezy in it, so that you only have Hoary; It's a bad idea to mix up the distributions.

Hang on, if everything is breezy, why not
```
sudo apt-get install ubuntu-desktop
sudo apt-get dist-upgrade
```
So you'll have breezy (Warning - that's a big download)! Are you sure you don't already have it though? Try this in the terminal:
```
cat /etc/issue
```
That tells you what version you have.

Definitely change everything back to hoary if you don't want to upgrade. That probably causes quite a few dependency errors. After you've fixed the problems, sudo apt-get -f install should fix the problems.

---

