---
title: "HU for those using padoka/mesa ppa &amp; oibaf/graphics-drivers"
date: 2018-02-21
forum: Ubuntu Development Version
---

### Post by zika on 2018-02-21
For a week now...
```
The following NEWpackages will be installed:
  libegl-mesa0{ab} libegl1{a} libglvnd0{a}
The followingpackages will be upgraded:
  gir1.2-mutter-1gnome-session gnome-session-bin gnome-session-commongnome-settings-daemon gnome-settings-daemon-schemas libmutter-1-0ubuntu-session unity-session
9 packages upgraded,3 newly installed, 0 to remove and 0 not upgraded.
Need to get 2866 kBof archives. After unpacking 6010 kB will be used.
The followingpackages have unmet dependencies: 
 libegl-mesa0 :Depends: libgbm1 (= 18.1~git1802210730.afa7b2~oibaf~b) but1:18.1~git180219165200.f78fe98~a~padoka0 is installed
:~$ apt policylibegl-mesa0
libegl-mesa0:
  Installed: (none)
  Candidate:18.1~git1802210730.afa7b2~oibaf~b
  Version table:
    18.1~git1802210730.afa7b2~oibaf~b 500
        500http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu devel/mainamd64 Packages
    18.0.0~rc4-1ubuntu1 500
        500http://archive.ubuntu.com/ubuntu devel-proposed/main amd64 Packages
:~$ apt policylibegl1
libegl1:
  Installed: (none)
  Candidate:1.0.0-2ubuntu1
  Version table:
     1.0.0-2ubuntu1500
        500http://archive.ubuntu.com/ubuntu devel-proposed/universe amd64Packages
    0.2.999+git20170802-2 500
        500http://archive.ubuntu.com/ubuntu devel/universe amd64 Packages
:~$ apt policylibglvnd0
libglvnd0:
  Installed:1.0.0-2ubuntu1
  Candidate:1.0.0-2ubuntu1
  Version table:
 *** 1.0.0-2ubuntu1500
        500http://archive.ubuntu.com/ubuntu devel-proposed/universe amd64Packages
        100/var/lib/dpkg/status
    0.2.999+git20170802-2 500
        500http://archive.ubuntu.com/ubuntu devel/universe amd64 Packages
```
libglvnd0 can be installed with some push... ;) Other two do not budge even with force... ;) PPA-purge gets chocked at a try to revert any of those two PPAs...
 I'll dive into changing apt base files once i get some spare time to remove this dependence restriction... Any other ideas/experiences?
I know that Oibaf and Paulo Dias would laugh at me so... I will not ask them... ;)

---

### Post by mc4man on 2018-02-21
They'd likely tell you you shouldn't be mixing theses ppa's particularly when one doesn't even support 18.04 yet.
If you didn't do that purposely, i.e upgraded from artful,   then the response would have  been to have used  ppa-purge before a release upgrade.

Probably easily fixed with dpkg.

---

### Post by zika on 2018-02-22
Not complaining, to the contrary, just giving HU for those who, like me, use devel branches of PPAs to test rollingness of Ubuntu... ;)
Not yet found easy and smooth way with dpkg to get out of this corner I've painted myself in but it is not a big deal and time (not the one that I have to spare, sigh) is on my side...

---

### Post by mc4man on 2018-02-22
> **zika said:**
> Not complaining, to the contrary, just giving HU for those who, like me, use devel branches of PPAs to test rollingness of Ubuntu... ;)
Not yet found easy and smooth way with dpkg to get out of this corner I've painted myself in but it is not a big deal and time (not the one that I have to spare, sigh) is on my side...
Doesn't oibaf have all the packages you'v installed from the 1:18.1~git180219165200.f78fe98~a~padoka0 source?

---

### Post by zika on 2018-02-23
Trouble is strict dependence of = in:```
libegl-mesa0 :Depends: libgbm1 (= 18.1~git1802230730.4562a7~oibaf~b) but1:18.1~git180219165200.f78fe98~a~padoka0 is installed
```
It's all only my fault, not for the first time, I just wanted to give HU to those who could make same mistake. Still kicking although... ;)

Update&#8321;: Arctic weather provided some spare time (seems that also some stuff got changed in dependencies in the meantime, I did not follow all the branches on that tree and I've attacked holdup from the Gnome3StagingPPA-side) so all is left just to curl waiting:```
:~$ apt list --upgradable -a
Listing... Done
curl/bionic-proposed 7.58.0-2ubuntu2 amd64 [upgradable from: 7.58.0-2ubuntu1]
curl/bionic,now 7.58.0-2ubuntu1 amd64 [installed,upgradable to: 7.58.0-2ubuntu2]
:~$ sudo apt install -s libcurl4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libboinc7 libboost-serialization1.65.1 yudit-common
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  curl
The following packages will be REMOVED:
  boinc boinc-client boinc-manager content-hub feh indicator-transfer-download-manager libcontent-hub0 libcurl3 libertine-tools libertine-xmir-tools libnet-cpp2 libubuntu-app-launch4 libubuntu-location-service3 libunity-scopes1.0 netsurf-gtk opera-developer qtdeclarative5-ubuntu-content1 spotify-client
  ubuntu-app-launch-tools ubuntu-application-api3-desktop uget whoopsie
The following NEW packages will be installed:
  libcurl4
The following packages will be upgraded:
  curl
```;)

---

