---
title: "Failed to fetch"
date: 2012-02-01
forum: Ubuntuzilla
---

### Post by Dinsdale Piranha on 2012-02-01
I added the repository to Ubuntu Software Center:
```
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```Added the key:
```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
```Selected "Mozilla .debs packaged by Ubuntuzilla" in Software Center, then Install for SeaMonkey.  I get a dialog that reads:

> Failed to download package files

Check your Internet connection

Failed to fetch [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/pool/main/s/seamonkey-mozilla-build/seamonkey-mozilla-build_2.6.1-0ubuntu1_i386.deb](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/pool/main/s/seamonkey-mozilla-build/seamonkey-mozilla-build_2.6.1-0ubuntu1_i386.deb) Got a single header line over 360 charsI'm using Maverick, if it makes any difference.

---

### Post by dcolhoun on 2012-02-01
Hi

I am getting the same error

---

### Post by nanotube on 2012-02-02
Hi,
This is due to a problem on the sourceforge.net downloads servers, they actually do produce a header line > 360 chars long.
I have filed a bug with sourceforge:
[http://sourceforge.net/apps/trac/sourceforge/ticket/24072](http://sourceforge.net/apps/trac/sourceforge/ticket/24072)

In the meantime, as a workaround, instead of using downloads.sourceforge.net as the server for the repo, you could try using one of the mirrors directly. e.g., switch.dl.sourceforge.net. Your deb line in sources.list then would be this:
```
deb http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```

I'll post here with any updates!

---

### Post by dcolhoun on 2012-02-02
Thanks nanotube - it is working from the mirror

---

### Post by ub-pir on 2012-02-02
> **nanotube said:**
> Hi,
In the meantime, as a workaround, instead of using downloads.sourceforge.net as the server for the repo, you could try using one of the mirrors directly. e.g., switch.dl.sourceforge.net.

Yep, this worked for me. Thanks!

---

### Post by nanotube on 2012-02-02
Update: the ticket is actively being worked on by sf.net staff (see ongoing discussion on the allura ticket). Already there's some improvement - using downloads.sourceforge.net works about half the time :) (the set-cookie http header appears to vary in length depending on where the redirect gateway decides to send you...)

The workaround of using a mirror directly of course still works.

---

### Post by mikewhatever on 2012-02-02
Thanks for the update. I've downloaded the deb package with wget and installed with 'dpkg -i' to bypass the error. Wget did seem to mind, and all is well.

...somewhat unrelated, but I was wondering, what would happen to /usr/bin/firefox when Firefox 10 finally hits the repositories? After installing the package from Ubuntuzilla, the link points to /opt/firefox/firefox, so wouldn't it get overwritten?

---

### Post by nanotube on 2012-02-03
> **mikewhatever said:**
> Thanks for the update. I've downloaded the deb package with wget and installed with 'dpkg -i' to bypass the error. Wget did seem to mind, and all is well.

yes, that works too, but maybe a little easier would have been to change the deb line in sources.list to point to switch.dl.sourceforge.net :)

> 
...somewhat unrelated, but I was wondering, what would happen to /usr/bin/firefox when Firefox 10 finally hits the repositories? After installing the package from Ubuntuzilla, the link points to /opt/firefox/firefox, so wouldn't it get overwritten?

everything would work just fine - ubuntuzilla package places a redirect on the ubuntu package, so that its startup link goes into /usr/bin/firefox.ubuntu. so when new version comes out in the ubuntu repos, it knows not to overwrite /usr/bin/firefox, but instead writes its link in firefox.ubuntu. so you can install those updates without fear! :)

---

### Post by pneaveill on 2012-02-10
Been following this thing for a few days or so.  The updates are not working for me either directly or from repository or from installzilla straight from downloads.sf or 
deb [http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main


](*,)

edit: 

What is proper syntax for the wget/ dpkg -i?

wget [http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt) 

then what please

second edit:

Failed to fetch [http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release](http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release)  Unable to find expected entry  main/source/Sources in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by mikewhatever on 2012-02-12
Do you want Firefox or Thunderbird? 32 or 64bit?

The original problem seems to be fixed, so you should probably post the output of the following for review:
```
tail /etc/apt/sources.list
```

---

### Post by nanotube on 2012-02-12
The 360-chars problem is still not completely fixed - occurs intermittently depending on which mirror you get sent to. but switch.dl should be working fine at least. so as mike said, please post your sources.list.

---

### Post by nanotube on 2012-02-16
Update:
Sourceforge has fixed the long-header problem, and the repository now works without issues using the downloads.sourceforge.net server.

---

### Post by hewittkennedy on 2013-01-05
I followed the 4 term line steps for automating Firefox updates at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/), but it's not working.  

My sources.list file is (so you'll see I've already added mirror per nanotube): 
[INDENT]deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-updates main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-security main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-netbook-base main universe multiverse restricted

deb [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted
deb-src [http://dell-mini.archive.canonical.com/ubuntu/](http://dell-mini.archive.canonical.com/ubuntu/) hardy-dell-mini main universe multiverse restricted

deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main
deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main

deb [http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main
[/INDENT]The sudo apt-key step shows:
[INDENT]susan@susan:~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com C1289A29
gpg: requesting key C1289A29 from hkp server keyserver.ubuntu.com
gpg: key C1289A29: "Daniel Folkinshteyn (Ubuntuzilla signing key) <nanotube@users.sourceforge.net>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
[/INDENT]The sudo apt-get shows (see blue text in middle):
[INDENT]susan@susan:~$ sudo apt-get update
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release.gpg
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Translation-en_US
Hit [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all Release.gpg
Ign [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all/main Translation-en_US      
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Translation-en_US      
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release.gpg
Hit [http://switch.dl.sourceforge.net](http://switch.dl.sourceforge.net) all Release
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all Release                   
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release.gpg
Ign [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release.gpg
[COLOR=RoyalBlue]Err [http://downloads.sourceforge.net](http://downloads.sourceforge.net) all/main Packages
  404 Not Found[/COLOR]
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Translation-en_US
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release.gpg
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/public Translation-en_US
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini Release
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-updates/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-security/restricted Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources
Ign [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/public Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/public Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-netbook-base/restricted Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Packages
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/main Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/universe Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/multiverse Sources
Hit [http://dell-mini.archive.canonical.com](http://dell-mini.archive.canonical.com) hardy-dell-mini/restricted Sources
W: Failed to fetch [http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release](http://switch.dl.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/Release)  Unable to find expected entry  main/binary-lpia/Packages in Meta-index file (malformed Release file?)

W: Failed to fetch [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/main/binary-lpia/Packages.gz](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/main/binary-lpia/Packages.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
[/INDENT]Perhaps it shouldn't be surprising that the sudo apt-get install didn't work:
[INDENT]susan@susan:~$ sudo apt-get install firefox-mozilla-build
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package firefox-mozilla-build
[/INDENT]I thought I'd try the instructions at:  [http://www.psychocats.net/ubuntu/ubuntuzilla](http://www.psychocats.net/ubuntu/ubuntuzilla) and everything went fine till I asked the Software Sources to reload, at which point I get same error message as in sudo apt-get update step.  The Synaptic Package Manager also can't find the mozilla-build.

Any idea why this isn't working for me?  I currently have Firefox for Ubuntu 3.6.17.  I think I have Hardy Heron 8.04 for Linux, but don't remember how to figure that out.
Thanks!

---

### Post by nanotube on 2013-01-05
hi hewittkennedy,

yes you do appear to have an old ubuntu release, hardy 8.04, and further which is the dell flavor of the lpia architecture.

There are a number of problems here:
1. lpia is a separate architecture build, and the packages of ubuntuzilla (or really almost anything else out there) don't support it.
2. hardy is old, and the apt-get system doesn't support http redirects, which the main downloads.sourceforge.net gateway uses, so you'd have to specific mirror (switch.dl.sourceforge.net is one such mirror - you'll see in your output that that one worked fine - but complained about missing lpia packages)

my suggestion to you is to do the following:
1. back up your personal files from this computer
2. make a fresh install of the latest ubuntu 32bit (or xubuntu - these days i'm a xubuntu fan :) )
3. if you wish, follow the steps again to add the ubuntuzilla repository and install the latest mozilla builds, though the latest ubuntu would also come with recent mozilla software.

all the best!

---

