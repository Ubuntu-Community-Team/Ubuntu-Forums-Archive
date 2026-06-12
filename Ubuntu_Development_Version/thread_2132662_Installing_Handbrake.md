---
title: "Installing Handbrake"
date: 2013-03-21
forum: Ubuntu Development Version
---

### Post by shantiq on 2013-03-21
i tried to use the usual PPA and take the software sources back to Quantal but not yet an option so using the debian packages a quick route for now if anyone needs this software

```

[noparse]wget http://ftp.dk.debian.org/getdeb/ubuntu/pool/apps/h/handbrake/handbrake-cli_0.9.8-1~getdeb1_amd64.deb && wget http://ftp.dk.debian.org/getdeb/ubuntu/pool/apps/h/handbrake/handbrake-gtk_0.9.8-1~getdeb1_amd64.deb[/noparse]
```

```
sudo dpkg -i handbrake-cli_0.9.8-1~getdeb1_amd64.deb

```

 ```
sudo dpkg -i handbrake-gtk_0.9.8-1~getdeb1_amd64.deb
```


Then find in Applications/Sound and Video

---

### Post by coldraven on 2013-03-21
Does handbrake still want to remove a heap of things using your method?
See my post here:
[http://ubuntuforums.org/showthread.php?t=2126187&p=12560051#post12560051](http://ubuntuforums.org/showthread.php?t=2126187&p=12560051#post12560051)

---

### Post by shantiq on 2013-03-21
Hi Raven

asked absolutely nothing be removed and very fast that route

under 2 minutes

> shan@shan:~$ wget [http://ftp.dk.debian.org/getdeb/ubuntu/pool/apps/h/handbrake/handbrake-cli_0.9.8-1~getdeb1_amd64.deb](http://ftp.dk.debian.org/getdeb/ubuntu/pool/apps/h/handbrake/handbrake-cli_0.9.8-1~getdeb1_amd64.deb) && wget [http://ftp.dk.debian.org/getdeb/ubuntu/pool/apps/h/handbrake/handbrake-gtk_0.9.8-1~getdeb1_amd64.deb](http://ftp.dk.debian.org/getdeb/ubuntu/pool/apps/h/handbrake/handbrake-gtk_0.9.8-1~getdeb1_amd64.deb)
--2013-03-21 10:18:46--  [http://ftp.dk.debian.org/getdeb/ubuntu/pool/apps/h/handbrake/handbrake-cli_0.9.8-1~getdeb1_amd64.deb](http://ftp.dk.debian.org/getdeb/ubuntu/pool/apps/h/handbrake/handbrake-cli_0.9.8-1~getdeb1_amd64.deb)
Resolving ftp.dk.debian.org (ftp.dk.debian.org)... 130.225.254.116, 2001:878:346::116
Connecting to ftp.dk.debian.org (ftp.dk.debian.org)|130.225.254.116|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7046796 (6.7M) [application/x-debian-package]
Saving to: &#8216;handbrake-cli_0.9.8-1~getdeb1_amd64.deb&#8217;

100%[======================================================================================================>] 7,046,796   1.09MB/s   in 6.4s   

2013-03-21 10:18:52 (1.06 MB/s) - &#8216;handbrake-cli_0.9.8-1~getdeb1_amd64.deb&#8217; saved [7046796/7046796]

--2013-03-21 10:18:52--  [http://ftp.dk.debian.org/getdeb/ubuntu/pool/apps/h/handbrake/handbrake-gtk_0.9.8-1~getdeb1_amd64.deb](http://ftp.dk.debian.org/getdeb/ubuntu/pool/apps/h/handbrake/handbrake-gtk_0.9.8-1~getdeb1_amd64.deb)
Resolving ftp.dk.debian.org (ftp.dk.debian.org)... 130.225.254.116, 2001:878:346::116
Connecting to ftp.dk.debian.org (ftp.dk.debian.org)|130.225.254.116|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7285952 (6.9M) [application/x-debian-package]
Saving to: &#8216;handbrake-gtk_0.9.8-1~getdeb1_amd64.deb&#8217;

100%[======================================================================================================>] 7,285,952   1.09MB/s   in 6.6s   

2013-03-21 10:18:59 (1.05 MB/s) - &#8216;handbrake-gtk_0.9.8-1~getdeb1_amd64.deb&#8217; saved [7285952/7285952]


shan@shan:~$ sudo dpkg -i handbrake-cli_0.9.8-1~getdeb1_amd64.deb
(Reading database ... 276884 files and directories currently installed.)
Preparing to replace handbrake-cli 0.9.8-1~getdeb1 (using handbrake-cli_0.9.8-1~getdeb1_amd64.deb) ...
Unpacking replacement handbrake-cli ...
Setting up handbrake-cli (0.9.8-1~getdeb1) ...

shan@shan:~$ sudo dpkg -i handbrake-gtk_0.9.8-1~getdeb1_amd64.deb
(Reading database ... 276884 files and directories currently installed.)
Preparing to replace handbrake-gtk 0.9.8-1~getdeb1 (using handbrake-gtk_0.9.8-1~getdeb1_amd64.deb) ...
Unpacking replacement handbrake-gtk ...
Setting up handbrake-gtk (0.9.8-1~getdeb1) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...

---

### Post by cariboo on 2013-03-21
I've been using the handbrake snapshot ppa to install it without any problems. One of my hard drives died last weekend, so I'm re-ripping all my dvds,and except for a crash ripping GI Joe, it has worked flawlessly.

---

### Post by shantiq on 2013-03-21
well i tried that twice and no go on my setup   "said it was referring to an obsolete package etc etc " only goes up to quantal in the PPA so far

glad to hear it worked for you; i had to use the debs and fine by me and dead quick too

---

### Post by coldraven on 2013-03-21
Shantiq
> only goes up to quantal in the PPA so far


The ppa for Quantal was what nearly ruined my system. (12.10)
I used your method and it is working fine, thanks.

---

### Post by mc4man on 2013-03-21
The only issue with either of the handbrake ppa's in 12.10 or 13.04 other than atm there are no raring builds exists solely in synaptic.
For whatever reason on an amd64 install synaptic will default to only showing the :i386 packages unless specifically searched in arch: amd64
From there they are properly installed, apt-get has no such problem & will install the amd64 package(s)

---

### Post by shantiq on 2013-03-22
thanx for the insight mc ::]]

---

### Post by WorLord on 2013-03-22
I've been using the 12.10 repo in 13.04... seems to work just fine.  Is there supposed to be any harm in this?

---

### Post by cariboo on 2013-03-22
> **WorLord said:**
> I've been using the 12.10 repo in 13.04... seems to work just fine.  Is there supposed to be any harm in this?

There shouldn't be any problems using the Quantal repositories in Raring, in most cases the owners of the ppas, don't update it, until a version is released.

---

### Post by FishboyFive on 2013-04-05
hello I really need Handbrake but can not find it i went to the website and it has a repo but it does not work or i can not get it to work can anyone help please

[https://launchpad.net/~stebbins/+archive/handbrake-releases](https://launchpad.net/~stebbins/+archive/handbrake-releases)

[http://handbrake.fr/downloads.php](http://handbrake.fr/downloads.php)

---

### Post by cariboo on 2013-04-05
You need to add the ppa to your software sources list. Open a terminal, and type the following command:

```
sudo apt-add-repository ppa:stebbins/handbrake-releases
```

you will have to open software sources, and change the version to quantal, then run an update and install tha package using your favourite method.

---

### Post by bird1500 on 2013-04-05
> sudo apt-add-repository ppa:stebbins/handbrake-releases
Then in "Software and Updates" change "raring" to "quantal" as shown on screenshot.

---

### Post by FishboyFive on 2013-04-05
thanks for the help but this is what i get 

W: Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/raring/main/binary-amd64/Packages](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/raring/main/binary-amd64/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by FishboyFive on 2013-04-05
i found install instructions that work for anyone that needs them , thanks for the help

[http://www.liberiangeek.net/2013/04/install-handbrake-0-9-8-in-ubuntu-13-04-raring-ringtail/](http://www.liberiangeek.net/2013/04/install-handbrake-0-9-8-in-ubuntu-13-04-raring-ringtail/)

---

### Post by cariboo on 2013-04-05
> **FishboyFive said:**
> thanks for the help but this is what i get 

W: Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/raring/main/binary-amd64/Packages](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/raring/main/binary-amd64/Packages)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/raring/main/binary-i386/Packages](http://ppa.launchpad.net/stebbins/handbrake-releases/ubuntu/dists/raring/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.

If you check the links you provided, you can see that you didn't change the version to quantal in System Settings->[s]Software Sources[/s] Software & Updates.

It's been a while since I checked it from system settings, as I use synaptic package manager, and access it from there.

---

### Post by shantiq on 2013-04-06
Hi Fishboy       for reasons unknown  [i had gone to software sources and picked quantal]   i too got messages which did not allow me take that route


but**[ this ]("http://ubuntuforums.org/showthread.php?t=2127803&p=12567215#post12567215")**worked for me   it will for you too probably and is very fast

---

### Post by cariboo on 2013-04-06
I use the handbrake snapshot ppa, set to quantal, and I usually get daily updates to handbrake using synaptic.

---

### Post by FishboyFive on 2013-04-10
> **shantiq said:**
> i tried to use the usual PPA and take the software sources back to Quantal but not yet an option so using the debian packages a quick route for now if anyone needs this software

```

[noparse]wget http://ftp.dk.debian.org/getdeb/ubuntu/pool/apps/h/handbrake/handbrake-cli_0.9.8-1~getdeb1_amd64.deb && wget http://ftp.dk.debian.org/getdeb/ubuntu/pool/apps/h/handbrake/handbrake-gtk_0.9.8-1~getdeb1_amd64.deb[/noparse]
```

```
sudo dpkg -i handbrake-cli_0.9.8-1~getdeb1_amd64.deb

```

 ```
sudo dpkg -i handbrake-gtk_0.9.8-1~getdeb1_amd64.deb
```


Then find in Applications/Sound and Video

dependency problems prevent configuration of handbrake-gtk:
 handbrake-gtk depends on libwebkitgtk-1.0-0 (>= 1.3.10); however:
  Package libwebkitgtk-1.0-0 is not installed.


dpkg: error processing handbrake-gtk (--install):
 dependency problems - leaving unconfigured

---

### Post by FishboyFive on 2013-04-10
this is what works for me in 13.04

64Bit

wget [https://launchpad.net/~stebbins/+archive/handbrake-releases/+files/handbrake-gtk_0.9.8%2Bppa1~quantal1_amd64.deb](https://launchpad.net/~stebbins/+archive/handbrake-releases/+files/handbrake-gtk_0.9.8%2Bppa1~quantal1_amd64.deb)

then

sudo dpkg -i handbrake*; sudo apt-get -f install

---

### Post by cariboo on 2013-04-10
Merged two similar threads

---

