---
title: "Trouble installing VirtualBox"
date: 2011-01-04
forum: Virtualisation
---

### Post by royale1223 on 2011-01-04
I'm trying to run XP on VB. I installed VB from synaptic but didn't show up in Applications > System Tools. I did some checking and found out that virtualbox-ose-qt is not installed. so I tried to install it with aptitude, and got the following error.
```
root@binoy-pc:~# apt-get install virtualbox-ose-qt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 virtualbox-ose-qt : Depends: libqt4-network (>= 4:4.5.3) but it is not going to be installed
                     Depends: libqt4-opengl (>= 4:4.5.3) but it is not going to be installed
E: Broken packages

```

Then I tried "apt-get install libqt4-network libqt4-opengl"
It returns:
```
root@binoy-pc:~# apt-get install libqt4-network libqt4-opengl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libqt4-network : Depends: libqt4-dbus (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
                  Depends: libqtcore4 (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
 libqt4-opengl : Depends: libqtcore4 (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
                 Depends: libqtgui4 (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is to be installed
E: Broken packages

```

Output of "dpkg -l |grep libqt"
```
root@binoy-pc:~# dpkg -l |grep libqt
ii  libqt3-mt                                 3:3.3.8-b-6ubuntu2                              Qt GUI Library (Threaded runtime version), Version 3
ii  libqt4-dbus                               4:4.7.0-0ubuntu4.2                              Qt 4 D-Bus module
ii  libqt4-xml                                4:4.7.0-0ubuntu4.2                              Qt 4 XML module
ii  libqtcore4                                4:4.7.0-0ubuntu4.2                              Qt 4 core module
ii  libqtgui4                                 4:4.7.0-0ubuntu4.2                              Qt 4 GUI module
```

Output of "dpkg -l |grep virtualbox"
```
root@binoy-pc:~# dpkg -l |grep virtualbox
ii  virtualbox-ose                            3.2.8-dfsg-2ubuntu1                             x86 virtualization solution - base binaries
ii  virtualbox-ose-dkms                       3.2.8-dfsg-2ubuntu1                             x86 virtualization solution - kernel module sources for dkms

```

My /etc/apt/sources.list file:
```
deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://in.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://in.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://in.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://in.archive.ubuntu.com/ubuntu/ maverick universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://in.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://in.archive.ubuntu.com/ubuntu/ maverick multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

#opensync
deb http://opensync.gforge.punktart.de/repo/opensync-0.21/ feisty main
deb-src http://opensync.gforge.punktart.de/repo/opensync-0.21/ feisty main

#vmware
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
```

[COLOR="Red"][SIZE="6"]Is there any way to resolve this? Please help me out.[/SIZE][/COLOR]

---

### Post by sdowney717 on 2011-01-05
dont use the one in the ubuntu repos. it wont have usb support or menu list.

Use vbox 4.0 with extension download.
[http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack)

---

### Post by royale1223 on 2011-01-06
> **sdowney717 said:**
> dont use the one in the ubuntu repos. it wont have usb support or menu list.

Use vbox 4.0 with extension download.
[http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack](http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack)

Solved it using aptitude. Thank you..


```
root@binoy-pc:~# aptitude install virtualbox-ose-qt 
The following NEW packages will be installed:
  libqt4-network{ab} libqt4-opengl{ab} virtualbox-ose-qt 
0 packages upgraded, 3 newly installed, 0 to remove and 64 not upgraded.
Need to get 5,700kB of archives. After unpacking 18.8MB will be used.
The following packages have unmet dependencies:
  libqt4-opengl: Depends: libqtcore4 (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is installed.
                 Depends: libqtgui4 (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is installed.
  libqt4-network: Depends: libqt4-dbus (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is installed.
                  Depends: libqtcore4 (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     libqt4-network [Not Installed]                     
2)     libqt4-opengl [Not Installed]                      
3)     virtualbox-ose-qt [Not Installed]                  



Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

     Downgrade the following packages:                                      
1)     libqt4-dbus [4:4.7.0-0ubuntu4.2 (now) -> 4:4.7.0-0ubuntu4 (maverick)]
2)     libqt4-xml [4:4.7.0-0ubuntu4.2 (now) -> 4:4.7.0-0ubuntu4 (maverick)] 
3)     libqtcore4 [4:4.7.0-0ubuntu4.2 (now) -> 4:4.7.0-0ubuntu4 (maverick)] 
4)     libqtgui4 [4:4.7.0-0ubuntu4.2 (now) -> 4:4.7.0-0ubuntu4 (maverick)]  



Accept this solution? [Y/n/q/?] y
The following packages will be DOWNGRADED:
  libqt4-dbus libqt4-xml libqtcore4 libqtgui4 
The following NEW packages will be installed:
  libqt4-network{a} libqt4-opengl{a} virtualbox-ose-qt 
0 packages upgraded, 3 newly installed, 4 downgraded, 0 to remove and 64 not upgraded.
Need to get 12.0MB of archives. After unpacking 18.8MB will be used.
Do you want to continue? [Y/n/?] y
Err http://in.archive.ubuntu.com/ubuntu/ maverick/main libqtgui4 i386 4:4.7.0-0ubuntu4
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Err http://in.archive.ubuntu.com/ubuntu/ maverick/main libqt4-dbus i386 4:4.7.0-0ubuntu4
  Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
Get:1 http://in.archive.ubuntu.com/ubuntu/ maverick/main libqt4-xml i386 4:4.7.0-0ubuntu4 [134kB]
Get:2 http://in.archive.ubuntu.com/ubuntu/ maverick/main libqtcore4 i386 4:4.7.0-0ubuntu4 [1,848kB]
Get:3 http://in.archive.ubuntu.com/ubuntu/ maverick/main libqt4-network i386 4:4.7.0-0ubuntu4 [492kB]
Get:4 http://in.archive.ubuntu.com/ubuntu/ maverick/main libqt4-opengl i386 4:4.7.0-0ubuntu4 [314kB]
Get:5 http://in.archive.ubuntu.com/ubuntu/ maverick/universe virtualbox-ose-qt i386 3.2.8-dfsg-2ubuntu1 [4,894kB]
Err http://in.archive.ubuntu.com/ubuntu/ maverick/universe virtualbox-ose-qt i386 3.2.8-dfsg-2ubuntu1
  Cannot initiate the connection to in.archive.ubuntu.com:80 (111.91.91.37). - connect (101: Network is unreachable)
Fetched 2,788kB in 27min 53s (1,666B/s)      
E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.7.0-0ubuntu4_i386.deb: Something wicked happened resolving 'in.archive.ubuntu.com:http' (-5 - No address associated with hostname)
                                         
root@binoy-pc:~# aptitude install virtualbox-ose-qt 
The following NEW packages will be installed:
  libqt4-network{ab} libqt4-opengl{ab} virtualbox-ose-qt 
0 packages upgraded, 3 newly installed, 0 to remove and 64 not upgraded.
Need to get 4,894kB/5,700kB of archives. After unpacking 18.8MB will be used.
The following packages have unmet dependencies:
  libqt4-opengl: Depends: libqtcore4 (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is installed.
                 Depends: libqtgui4 (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is installed.
  libqt4-network: Depends: libqt4-dbus (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is installed.
                  Depends: libqtcore4 (= 4:4.7.0-0ubuntu4) but 4:4.7.0-0ubuntu4.2 is installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     libqt4-network [Not Installed]                     
2)     libqt4-opengl [Not Installed]                      
3)     virtualbox-ose-qt [Not Installed]                  



Accept this solution? [Y/n/q/?] n
The following actions will resolve these dependencies:

     Downgrade the following packages:                                      
1)     libqt4-dbus [4:4.7.0-0ubuntu4.2 (now) -> 4:4.7.0-0ubuntu4 (maverick)]
2)     libqt4-xml [4:4.7.0-0ubuntu4.2 (now) -> 4:4.7.0-0ubuntu4 (maverick)] 
3)     libqtcore4 [4:4.7.0-0ubuntu4.2 (now) -> 4:4.7.0-0ubuntu4 (maverick)] 
4)     libqtgui4 [4:4.7.0-0ubuntu4.2 (now) -> 4:4.7.0-0ubuntu4 (maverick)]  



Accept this solution? [Y/n/q/?] y
The following packages will be DOWNGRADED:
  libqt4-dbus libqt4-xml libqtcore4 libqtgui4 
The following NEW packages will be installed:
  libqt4-network{a} libqt4-opengl{a} virtualbox-ose-qt 
0 packages upgraded, 3 newly installed, 4 downgraded, 0 to remove and 64 not upgraded.
Need to get 9,240kB/12.0MB of archives. After unpacking 18.8MB will be used.
Do you want to continue? [Y/n/?] y
Get:1 http://in.archive.ubuntu.com/ubuntu/ maverick/main libqtgui4 i386 4:4.7.0-0ubuntu4 [4,108kB]
Get:2 http://in.archive.ubuntu.com/ubuntu/ maverick/main libqt4-dbus i386 4:4.7.0-0ubuntu4 [238kB]
Get:3 http://in.archive.ubuntu.com/ubuntu/ maverick/universe virtualbox-ose-qt i386 3.2.8-dfsg-2ubuntu1 [4,894kB]
Fetched 6,534kB in 14min 33s (7,481B/s)                                         
dpkg: warning: downgrading libqtgui4 from 4:4.7.0-0ubuntu4.2 to 4:4.7.0-0ubuntu4.
(Reading database ... 138947 files and directories currently installed.)
Preparing to replace libqtgui4 4:4.7.0-0ubuntu4.2 (using .../libqtgui4_4%3a4.7.0-0ubuntu4_i386.deb) ...
Unpacking replacement libqtgui4 ...
dpkg: warning: downgrading libqt4-dbus from 4:4.7.0-0ubuntu4.2 to 4:4.7.0-0ubuntu4.
Preparing to replace libqt4-dbus 4:4.7.0-0ubuntu4.2 (using .../libqt4-dbus_4%3a4.7.0-0ubuntu4_i386.deb) ...
Unpacking replacement libqt4-dbus ...
dpkg: warning: downgrading libqt4-xml from 4:4.7.0-0ubuntu4.2 to 4:4.7.0-0ubuntu4.
Preparing to replace libqt4-xml 4:4.7.0-0ubuntu4.2 (using .../libqt4-xml_4%3a4.7.0-0ubuntu4_i386.deb) ...
Unpacking replacement libqt4-xml ...
dpkg: warning: downgrading libqtcore4 from 4:4.7.0-0ubuntu4.2 to 4:4.7.0-0ubuntu4.
Preparing to replace libqtcore4 4:4.7.0-0ubuntu4.2 (using .../libqtcore4_4%3a4.7.0-0ubuntu4_i386.deb) ...
Unpacking replacement libqtcore4 ...
Selecting previously deselected package libqt4-network.
Unpacking libqt4-network (from .../libqt4-network_4%3a4.7.0-0ubuntu4_i386.deb) ...
Selecting previously deselected package libqt4-opengl.
Unpacking libqt4-opengl (from .../libqt4-opengl_4%3a4.7.0-0ubuntu4_i386.deb) ...
Selecting previously deselected package virtualbox-ose-qt.
Unpacking virtualbox-ose-qt (from .../virtualbox-ose-qt_3.2.8-dfsg-2ubuntu1_i386.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_IN.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up libqtcore4 (4:4.7.0-0ubuntu4) ...
Setting up libqt4-xml (4:4.7.0-0ubuntu4) ...
Setting up libqt4-dbus (4:4.7.0-0ubuntu4) ...
Setting up libqtgui4 (4:4.7.0-0ubuntu4) ...
Setting up libqt4-network (4:4.7.0-0ubuntu4) ...
Setting up libqt4-opengl (4:4.7.0-0ubuntu4) ...
Setting up virtualbox-ose-qt (3.2.8-dfsg-2ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

### Post by rainyu_2002 on 2011-03-04
I have same problem on dependencies. But I found problem happened on "Update Manager" settings. I unchecked "Important security updates(maverick-security)" and the following 3 options. 

Fix it
---------------
I checked the 3 options, click "close". wait form some minutes. Then I can install libqt4-opengl with command "apt-get install libqt4-opengl". Install virtualbox with command "dpkg -i virtualbox-4.0_4.0.4-70112~Ubuntu~maverick_i386.deb"

Great.:o

---

### Post by jslowery on 2012-07-27
Thanks for your solution. It worked perfectly!

---

### Post by wildmanne39 on 2012-07-29
Old thread closed.

---

