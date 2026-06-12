---
title: "LibreOffice 4.1 Beta on Saucy Salamander a.k.a. 13.10..."
date: 2013-06-04
forum: Ubuntu Development Version
---

### Post by zika on 2013-06-04
Anybody tried it?

---

### Post by JMB74 on 2013-06-04
If you mean the debs to download frpm [http://www.libreoffice.org/download/pre-releases/](http://www.libreoffice.org/download/pre-releases/) then I had some broken symlinks and desktop integration, meaning that the programs would not launch via shortcut or command line. 

Fixable by making some manual fixs after a bit of investigation, but not ideal.

---

### Post by zika on 2013-06-04
Thank You for sharing Your experience...
I'm now on Version 4.0.2.2 (Build ID: 400m0(Build:2)). What would be main difference?
It did install side-by-side with existing install of LO?

---

### Post by jfernyhough on 2013-06-04
I'm going to wait for it to be packaged on the pre-release PPA. [https://launchpad.net/~libreoffice/+archive/libreoffice-prereleases](https://launchpad.net/~libreoffice/+archive/libreoffice-prereleases)

---

### Post by zika on 2013-06-04
> **jfernyhough said:**
> I'm going to wait for it to be packaged on the pre-release PPA. [https://launchpad.net/~libreoffice/+archive/libreoffice-prereleases](https://launchpad.net/~libreoffice/+archive/libreoffice-prereleases)
This version I've got is not from that PPA and is newer than versions there...
I think they came from Saucy main repo...
I planned to wait but that PPA does not even have Saucy branch yet...

---

### Post by jfernyhough on 2013-06-16
I've just installed 4.1 beta 2  from the pre-release PPA. I haven't tested it extensively but it loads. :D

---

### Post by zika on 2013-06-16
I was brave but, obviously, not smart enough ;)
```
The following NEW packages will be installed:  libboost-system1.53.0{a} liborcus-0.6-0{a} 
The following packages will be REMOVED:
  libhsqldb1.8.0-java{u} libreoffice-filter-mobiledev{u} 
  libreoffice-java-common{u} 
The following packages will be upgraded:
  fonts-opensymbol libreoffice libreoffice-base libreoffice-base-core 
  libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw 
  libreoffice-gnome libreoffice-gtk libreoffice-impress libreoffice-math 
  libreoffice-pdfimport libreoffice-style-human libreoffice-style-tango 
  libreoffice-writer python3-uno uno-libs3 ure 
The following partially installed packages will be configured:
  rhythmbox-plugin-zeitgeist 
19 packages upgraded, 2 newly installed, 3 to remove and 0 not upgraded.
Need to get 84.5 MB of archives. After unpacking 18.9 MB will be used.
Do you want to continue? [Y/n/?] 
Get: 1 http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu/ saucy/main libreoffice-base amd64 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4 [1,846 kB]
Get: 2 http://archive.ubuntu.com/ubuntu/ saucy/main libboost-system1.53.0 amd64 1.53.0-4ubuntu1 [10.7 kB]
Get: 3 http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu/ saucy/main libreoffice-calc amd64 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4 [5,822 kB]
Get: 4 http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu/ saucy/main libreoffice-impress amd64 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4 [818 kB]
Get: 5 http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu/ saucy/main libreoffice-draw amd64 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4 [2,628 kB]
Get: 6 http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu/ saucy/main libreoffice-gnome amd64 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4 [135 kB]
Get: 7 http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu/ saucy/main libreoffice-gtk amd64 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4 [257 kB]
Get: 8 http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu/ saucy/main libreoffice-writer amd64 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4 [8,992 kB]
Get: 9 http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu/ saucy/main libreoffice amd64 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4 [71.0 kB]
Get: 10 http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu/ saucy/main python3-uno amd64 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4 [164 kB]
Get: 11 http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu/ saucy/main libreoffice-style-human all 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4 [1,945 kB]
Get: 12 http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu/ saucy/main libreoffice-style-tango all 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4 [1,798 kB]
Get: 13 http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu/ saucy/main libreoffice-core amd64 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4 [28.5 MB]
Get: 14 http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu/ saucy/main libreoffice-common all 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4 [27.5 MB]
Get: 15 http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu/ saucy/main libreoffice-pdfimport amd64 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4 [265 kB]
Get: 16 http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu/ saucy/main libreoffice-math amd64 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4 [401 kB]
Get: 17 http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu/ saucy/main libreoffice-base-core amd64 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4 [764 kB]
Get: 18 http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu/ saucy/main ure amd64 4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4 [1,341 kB]
Get: 19 http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu/ saucy/main uno-libs3 amd64 4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4 [791 kB]
Get: 20 http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu/ saucy/main liborcus-0.6-0 amd64 0.5.1-2ubuntu1~ppa1 [259 kB]
Get: 21 http://ppa.launchpad.net/libreoffice/libreoffice-prereleases/ubuntu/ saucy/main fonts-opensymbol all 2:102.3+LibO4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4 [124 kB]
Fetched 84.5 MB in 56s (1,485 kB/s)                                             
(Reading database ... 351171 files and directories currently installed.)
Preparing to replace libreoffice-base 1:4.0.2-0ubuntu5 (using .../libreoffice-base_1%3a4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_amd64.deb) ...
Unpacking replacement libreoffice-base ...
Preparing to replace libreoffice-calc 1:4.0.2-0ubuntu5 (using .../libreoffice-calc_1%3a4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_amd64.deb) ...
Unpacking replacement libreoffice-calc ...
Preparing to replace libreoffice-impress 1:4.0.2-0ubuntu5 (using .../libreoffice-impress_1%3a4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_amd64.deb) ...
Unpacking replacement libreoffice-impress ...
Preparing to replace libreoffice-draw 1:4.0.2-0ubuntu5 (using .../libreoffice-draw_1%3a4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_amd64.deb) ...
Unpacking replacement libreoffice-draw ...
Preparing to replace libreoffice-gnome 1:4.0.2-0ubuntu5 (using .../libreoffice-gnome_1%3a4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_amd64.deb) ...
Unpacking replacement libreoffice-gnome ...
Preparing to replace libreoffice-gtk 1:4.0.2-0ubuntu5 (using .../libreoffice-gtk_1%3a4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_amd64.deb) ...
Unpacking replacement libreoffice-gtk ...
Preparing to replace libreoffice-writer 1:4.0.2-0ubuntu5 (using .../libreoffice-writer_1%3a4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_amd64.deb) ...
Unpacking replacement libreoffice-writer ...
Preparing to replace libreoffice 1:4.0.2-0ubuntu5 (using .../libreoffice_1%3a4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_amd64.deb) ...
Unpacking replacement libreoffice ...
Processing triggers for mime-support ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
(Reading database ... 351166 files and directories currently installed.)
Removing libreoffice-filter-mobiledev ...
(Reading database ... 351151 files and directories currently installed.)
Preparing to replace python3-uno 1:4.0.2-0ubuntu5 (using .../python3-uno_1%3a4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_amd64.deb) ...
Unpacking replacement python3-uno ...
Preparing to replace libreoffice-style-human 1:4.0.2-0ubuntu5 (using .../libreoffice-style-human_1%3a4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_all.deb) ...
Unpacking replacement libreoffice-style-human ...
Preparing to replace libreoffice-style-tango 1:4.0.2-0ubuntu5 (using .../libreoffice-style-tango_1%3a4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_all.deb) ...
Unpacking replacement libreoffice-style-tango ...
Preparing to replace libreoffice-core 1:4.0.2-0ubuntu5 (using .../libreoffice-core_1%3a4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_amd64.deb) ...
Unpacking replacement libreoffice-core ...
dpkg: error processing /var/cache/apt/archives/libreoffice-core_1%3a4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libreoffice/program/librptlo.so', which is also in package libreoffice-report-builder-bin 1:4.0.2-0ubuntu5
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
dpkg: considering deconfiguration of libreoffice-core, which would be broken by installation of libreoffice-common ...
dpkg: yes, will deconfigure libreoffice-core (broken by libreoffice-common)
Preparing to replace libreoffice-common 1:4.0.2-0ubuntu5 (using .../libreoffice-common_1%3a4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_all.deb) ...
De-configuring libreoffice-core ...
Unpacking replacement libreoffice-common ...
Preparing to replace libreoffice-pdfimport 1:4.0.2-0ubuntu5 (using .../libreoffice-pdfimport_1%3a4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_amd64.deb) ...
Unpacking replacement libreoffice-pdfimport ...
Preparing to replace libreoffice-math 1:4.0.2-0ubuntu5 (using .../libreoffice-math_1%3a4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_amd64.deb) ...
Unpacking replacement libreoffice-math ...
Preparing to replace libreoffice-base-core 1:4.0.2-0ubuntu5 (using .../libreoffice-base-core_1%3a4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_amd64.deb) ...
Unpacking replacement libreoffice-base-core ...
Preparing to replace ure 4.0.2-0ubuntu5 (using .../ure_4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_amd64.deb) ...
Unpacking replacement ure ...
Preparing to replace uno-libs3 4.0.2-0ubuntu5 (using .../uno-libs3_4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_amd64.deb) ...
Unpacking replacement uno-libs3 ...
Selecting previously unselected package libboost-system1.53.0.
Unpacking libboost-system1.53.0 (from .../libboost-system1.53.0_1.53.0-4ubuntu1_amd64.deb) ...
Selecting previously unselected package liborcus-0.6-0.
Unpacking liborcus-0.6-0 (from .../liborcus-0.6-0_0.5.1-2ubuntu1~ppa1_amd64.deb) ...
Preparing to replace fonts-opensymbol 2:102.2+LibO4.0.2-0ubuntu5 (using .../fonts-opensymbol_2%3a102.3+LibO4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_all.deb) ...
Unpacking replacement fonts-opensymbol ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gnome-icon-theme ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils ...
Processing triggers for mime-support ...
Processing triggers for shared-mime-info ...
Processing triggers for menu ...
Processing triggers for fontconfig ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-core_1%3a4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up libreoffice-style-human (1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4) ...
dpkg: dependency problems prevent configuration of python3-uno:
 python3-uno depends on libreoffice-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Version of libreoffice-core on system is 1:4.0.2-0ubuntu5.


dpkg: error processing python3-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-math:
 libreoffice-math depends on libreoffice-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Version of libreoffice-core on system is 1:4.0.2-0ubuntu5.


dpkg: error processing libreoffice-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-impress:
 libreoffice-impress depends on libreoffice-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Version of libreoffice-core on system is 1:4.0.2-0ubuntu5.


dpkg: error processing libreoffice-impress (--configure):
 dependency problems - leaving unconfigured
Setting up libreoffice-style-tango (1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4) ...
dpkg: dependency problems prevent configuration of libreoffice:
 libreoffice depends on libreoffice-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Version of libreoffice-core on system is 1:4.0.2-0ubuntu5.
 libreoffice depends on libreoffice-impress; however:
  Package libreoffice-impress is not configured yet.
 libreoffice depends on libreoffice-math; however:
  Package libreoffice-math is not configured yet.
 libreoffice depends on python3.3-uno | python3-uno (>= 4.0~) | python-uno; however:
  Package python3.3-uno is not installed.
  Package python3-uno is not configured yet.
  Package python-uno is not installed.


dpkg: error processing libreoffice (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-writer:
 libreoffice-writer depends on libreoffice-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Version of libreoffice-core on system is 1:4.0.2-0ubuntu5.


dpkg: error processing libreoffice-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-base-core:
 libreoffice-base-core depends on libreoffice-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Version of libreoffice-core on system is 1:4.0.2-0ubuntu5.


dpkg: error processing libreoffice-base-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on libreoffice-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Version of libreoffice-core on system is 1:4.0.2-0ubuntu5.


dpkg: error processing libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-base:
 libreoffice-base depends on libreoffice-base-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Package libreoffice-base-core is not configured yet.
 libreoffice-base depends on libreoffice-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Version of libreoffice-core on system is 1:4.0.2-0ubuntu5.


dpkg: error processing libreoffice-base (--configure):
 dependency problems - leaving unconfigured
Setting up uno-libs3 (4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4) ...
Setting up fonts-opensymbol (2:102.3+LibO4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4) ...
dpkg: dependency problems prevent configuration of libreoffice-gtk:
 libreoffice-gtk depends on libreoffice-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Version of libreoffice-core on system is 1:4.0.2-0ubuntu5.


dpkg: error processing libreoffice-gtk (--configure):
 dependency problems - leaving unconfigured
Setting up rhythmbox-plugin-zeitgeist (2.99.1+git20130606.051d8b96-0ubuntu1~13.10~ricotz0) ...
  File "/usr/lib/rhythmbox/plugins/rbzeitgeist/rbzeitgeist.py", line 40
    except RuntimeError, e:
                       ^
SyntaxError: invalid syntax


dpkg: error processing rhythmbox-plugin-zeitgeist (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libboost-system1.53.0 (1.53.0-4ubuntu1) ...
dpkg: dependency problems prevent configuration of libreoffice-draw:
 libreoffice-draw depends on libreoffice-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Version of libreoffice-core on system is 1:4.0.2-0ubuntu5.


dpkg: error processing libreoffice-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-calc:
 libreoffice-calc depends on libreoffice-base-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Package libreoffice-base-core is not configured yet.
 libreoffice-calc depends on libreoffice-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Version of libreoffice-core on system is 1:4.0.2-0ubuntu5.


dpkg: error processing libreoffice-calc (--configure):
 dependency problems - leaving unconfigured
Setting up ure (4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4) ...
Setting up libreoffice-common (1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4) ...
Setting up liborcus-0.6-0 (0.5.1-2ubuntu1~ppa1) ...
dpkg: dependency problems prevent configuration of libreoffice-core:
 libreoffice-common (1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4) breaks libreoffice-core (<< 1:4.1~) and is installed.
  Version of libreoffice-core to be configured is 1:4.0.2-0ubuntu5.
 ure (4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4) breaks libreoffice-core (<< 1:4.1.0~alpha) and is installed.
  Version of libreoffice-core to be configured is 1:4.0.2-0ubuntu5.


dpkg: error processing libreoffice-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-pdfimport:
 libreoffice-pdfimport depends on libreoffice-core; however:
  Package libreoffice-core is not configured yet.


dpkg: error processing libreoffice-pdfimport (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 python3-uno
 libreoffice-math
 libreoffice-impress
 libreoffice
 libreoffice-writer
 libreoffice-base-core
 libreoffice-gnome
 libreoffice-base
 libreoffice-gtk
 rhythmbox-plugin-zeitgeist
 libreoffice-draw
 libreoffice-calc
 libreoffice-core
 libreoffice-pdfimport
                                         
Current status: 13 broken [+13], 1 update [-18].
```
```
sudo aptitude dist-upgrade 
The following packages will be upgraded: 
  libreoffice-core 
The following partially installed packages will be configured:
  libreoffice libreoffice-base libreoffice-base-core libreoffice-calc 
  libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-impress 
  libreoffice-math libreoffice-pdfimport libreoffice-writer python3-uno 
  rhythmbox-plugin-zeitgeist 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/28.5 MB of archives. After unpacking 2,896 kB will be used.
Do you want to continue? [Y/n/?] 
(Reading database ... 351880 files and directories currently installed.)
Preparing to replace libreoffice-core 1:4.0.2-0ubuntu5 (using .../libreoffice-core_1%3a4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_amd64.deb) ...
Unpacking replacement libreoffice-core ...
dpkg: error processing /var/cache/apt/archives/libreoffice-core_1%3a4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libreoffice/program/librptlo.so', which is also in package libreoffice-report-builder-bin 1:4.0.2-0ubuntu5
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-core_1%3a4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of python3-uno:
 python3-uno depends on libreoffice-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Version of libreoffice-core on system is 1:4.0.2-0ubuntu5.


dpkg: error processing python3-uno (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-math:
 libreoffice-math depends on libreoffice-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Version of libreoffice-core on system is 1:4.0.2-0ubuntu5.


dpkg: error processing libreoffice-math (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-impress:
 libreoffice-impress depends on libreoffice-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Version of libreoffice-core on system is 1:4.0.2-0ubuntu5.


dpkg: error processing libreoffice-impress (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice:
 libreoffice depends on libreoffice-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Version of libreoffice-core on system is 1:4.0.2-0ubuntu5.
 libreoffice depends on libreoffice-impress; however:
  Package libreoffice-impress is not configured yet.
 libreoffice depends on libreoffice-math; however:
  Package libreoffice-math is not configured yet.
 libreoffice depends on python3.3-uno | python3-uno (>= 4.0~) | python-uno; however:
  Package python3.3-uno is not installed.
  Package python3-uno is not configured yet.
  Package python-uno is not installed.


dpkg: error processing libreoffice (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-writer:
 libreoffice-writer depends on libreoffice-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Version of libreoffice-core on system is 1:4.0.2-0ubuntu5.


dpkg: error processing libreoffice-writer (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-base-core:
 libreoffice-base-core depends on libreoffice-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Version of libreoffice-core on system is 1:4.0.2-0ubuntu5.


dpkg: error processing libreoffice-base-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-gnome:
 libreoffice-gnome depends on libreoffice-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Version of libreoffice-core on system is 1:4.0.2-0ubuntu5.


dpkg: error processing libreoffice-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-base:
 libreoffice-base depends on libreoffice-base-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Package libreoffice-base-core is not configured yet.
 libreoffice-base depends on libreoffice-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Version of libreoffice-core on system is 1:4.0.2-0ubuntu5.


dpkg: error processing libreoffice-base (--configure):
 dependency problems - leaving unconfigured
Setting up libreoffice-pdfimport (1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4) ...
dpkg: dependency problems prevent configuration of libreoffice-gtk:
 libreoffice-gtk depends on libreoffice-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Version of libreoffice-core on system is 1:4.0.2-0ubuntu5.


dpkg: error processing libreoffice-gtk (--configure):
 dependency problems - leaving unconfigured
Setting up rhythmbox-plugin-zeitgeist (2.99.1+git20130606.051d8b96-0ubuntu1~13.10~ricotz0) ...
  File "/usr/lib/rhythmbox/plugins/rbzeitgeist/rbzeitgeist.py", line 40
    except RuntimeError, e:
                       ^
SyntaxError: invalid syntax


dpkg: error processing rhythmbox-plugin-zeitgeist (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of libreoffice-draw:
 libreoffice-draw depends on libreoffice-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Version of libreoffice-core on system is 1:4.0.2-0ubuntu5.


dpkg: error processing libreoffice-draw (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libreoffice-calc:
 libreoffice-calc depends on libreoffice-base-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Package libreoffice-base-core is not configured yet.
 libreoffice-calc depends on libreoffice-core (= 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4); however:
  Version of libreoffice-core on system is 1:4.0.2-0ubuntu5.


dpkg: error processing libreoffice-calc (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python3-uno
 libreoffice-math
 libreoffice-impress
 libreoffice
 libreoffice-writer
 libreoffice-base-core
 libreoffice-gnome
 libreoffice-base
 libreoffice-gtk
 rhythmbox-plugin-zeitgeist
 libreoffice-draw
 libreoffice-calc
```

Now, after rescuing efforts I get:
```
:~$ libreoffice 
/usr/lib/libreoffice/program/../ure-link/bin/javaldx: error while loading shared libraries: libxmlreader.so: cannot open shared object file: No such file or directory
Warning: failed to read path from javaldx
/usr/lib/libreoffice/program/soffice.bin: error while loading shared libraries: libxmlreader.so: cannot open shared object file: No such file or directory
```

Any ideas how to rectify that... ;)

Update&#8321;: Fixed it after some radical cuts... It works... ;)

---

### Post by levomac on 2013-06-18
@zika

I installed the 4.1 beta2 libre office via the launchpad prerelease ppa on saucy and have got the folloeing dependency issue
```

The following extra packages will be installed:
  libreoffice-report-builder-bin
The following NEW packages will be installed:
  libreoffice-report-builder-bin
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
23 not fully installed or removed.
Need to get 0 B/820 kB of archives.
After this operation, 3,475 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 284369 files and directories currently installed.)
Unpacking libreoffice-report-builder-bin (from .../libreoffice-report-builder-bin_1%3a4.0.2-0ubuntu5_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-report-builder-bin_1%3a4.0.2-0ubuntu5_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libreoffice/program/librptxmllo.so', which is also in package libreoffice-core 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
_ /var/cache/apt/archives/libreoffice-report-builder-bin_1%3a4.0.2-0ubuntu5_amd64.deb_
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
 
It pesists even after trying sudo apt-get install -f ,and so cant update/install anything now.

Could you please help me to fix this

Thanks

---

### Post by zika on 2013-06-18
> **levomac said:**
> @zika

I installed the 4.1 beta2 libre office via the launchpad prerelease ppa on saucy and have got the folloeing dependency issue
```

The following extra packages will be installed:
  libreoffice-report-builder-bin
The following NEW packages will be installed:
  libreoffice-report-builder-bin
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
23 not fully installed or removed.
Need to get 0 B/820 kB of archives.
After this operation, 3,475 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 284369 files and directories currently installed.)
Unpacking libreoffice-report-builder-bin (from .../libreoffice-report-builder-bin_1%3a4.0.2-0ubuntu5_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-report-builder-bin_1%3a4.0.2-0ubuntu5_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libreoffice/program/librptxmllo.so', which is also in package libreoffice-core 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
_ /var/cache/apt/archives/libreoffice-report-builder-bin_1%3a4.0.2-0ubuntu5_amd64.deb_
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
 
It pesists even after trying sudo apt-get install -f ,and so cant update/install anything now.

Could you please help me to fix this

ThanksNot with information given...
Did You follow instructions given on ppa man page?
What did You do to get here...?
As I wrote i pushed myself up to the wall and then had to make radical moves to get out of there.
I did and LO is working these days at my machine nice and fast...

---

### Post by levomac on 2013-06-18
I purged the default libre office with

sudo apt-get remove --purge libreoffice*

then installed the pre release ppa as follows

sudo add-apt-repository ppa:libreoffice/libreoffice-prereleases
sudo apt-get update
sudo apt-get install libreoffice

Libre office works fine ,install is also ok but no new updates and ppas install due the dependency issiues

trying 
sudo apt-get update and sudo apt-get dist-upgrade causes

```
 sudo apt-get update && sudo apt-get dist-upgrade
Hit http://archive.canonical.com saucy Release.gpg
Hit http://extras.ubuntu.com saucy Release.gpg                                 
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Get:1 http://ftp.halifax.rwth-aachen.de saucy Release.gpg [933 B]              
Hit http://archive.canonical.com saucy Release                                 
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Hit http://ftp.halifax.rwth-aachen.de saucy-updates Release.gpg                
Hit http://extras.ubuntu.com saucy Release                                     
Hit http://archive.canonical.com saucy/partner Sources                         
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Ign http://packages.medibuntu.org free Release.gpg                             
Hit http://ftp.halifax.rwth-aachen.de saucy-backports Release.gpg              
Hit http://archive.canonical.com saucy/partner amd64 Packages                  
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Hit http://extras.ubuntu.com saucy/main Sources                                
Hit http://ftp.halifax.rwth-aachen.de saucy-security Release.gpg               
Hit http://archive.canonical.com saucy/partner i386 Packages                   
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Hit http://extras.ubuntu.com saucy/main amd64 Packages                         
Ign http://packages.medibuntu.org free Release                                 
Get:2 http://ftp.halifax.rwth-aachen.de saucy-proposed Release.gpg [933 B]     
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Hit http://extras.ubuntu.com saucy/main i386 Packages                          
Get:3 http://ftp.halifax.rwth-aachen.de saucy Release [40.8 kB]                
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://ftp.halifax.rwth-aachen.de saucy-updates Release                    
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://ppa.launchpad.net saucy Release                                     
Ign http://archive.canonical.com saucy/partner Translation-en_IN               
Ign http://archive.canonical.com saucy/partner Translation-en                  
Ign http://extras.ubuntu.com saucy/main Translation-en_IN                      
Hit http://ppa.launchpad.net saucy Release                                     
Ign http://extras.ubuntu.com saucy/main Translation-en                         
Hit http://ftp.halifax.rwth-aachen.de saucy-backports Release                  
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Hit http://ppa.launchpad.net saucy/main i386 Packages                 
Hit http://ppa.launchpad.net saucy/main amd64 Packages                
Hit http://ppa.launchpad.net saucy/main i386 Packages                 
Hit http://ftp.halifax.rwth-aachen.de saucy-security Release                   
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Err http://packages.medibuntu.org free/non-free amd64 Packages                 
  404  Not Found
Get:4 http://ftp.halifax.rwth-aachen.de saucy-proposed Release [40.8 kB]       
Hit http://ppa.launchpad.net saucy/main i386 Packages                          
Err http://packages.medibuntu.org free/non-free i386 Packages                  
  404  Not Found
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Ign http://packages.medibuntu.org free/non-free Translation-en_IN              
Hit http://ppa.launchpad.net saucy/main i386 Packages                          
Get:5 http://ftp.halifax.rwth-aachen.de saucy/main Sources [983 kB]            
Ign http://packages.medibuntu.org free/non-free Translation-en                 
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Hit http://ppa.launchpad.net saucy/main i386 Packages                          
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Hit http://ppa.launchpad.net saucy/main i386 Packages                          
Ign http://ppa.launchpad.net saucy/main Translation-en_IN                      
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Ign http://ppa.launchpad.net saucy/main Translation-en_IN                      
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Ign http://ppa.launchpad.net saucy/main Translation-en_IN                      
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Ign http://ppa.launchpad.net saucy/main Translation-en_IN                      
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Ign http://ppa.launchpad.net saucy/main Translation-en_IN                      
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Ign http://ppa.launchpad.net saucy/main Translation-en_IN                      
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Get:6 http://ftp.halifax.rwth-aachen.de saucy/restricted Sources [6,236 B]     
Get:7 http://ftp.halifax.rwth-aachen.de saucy/universe Sources [6,037 kB]      
Get:8 http://ftp.halifax.rwth-aachen.de saucy/multiverse Sources [175 kB]      
Get:9 http://ftp.halifax.rwth-aachen.de saucy/main amd64 Packages [1,206 kB]   
Get:10 http://ftp.halifax.rwth-aachen.de saucy/restricted amd64 Packages [9,936 B]
Get:11 http://ftp.halifax.rwth-aachen.de saucy/universe amd64 Packages [5,566 kB]
Get:12 http://ftp.halifax.rwth-aachen.de saucy/multiverse amd64 Packages [132 kB]                                                                                                         
Get:13 http://ftp.halifax.rwth-aachen.de saucy/main i386 Packages [1,204 kB]                                                                                                              
Get:14 http://ftp.halifax.rwth-aachen.de saucy/restricted i386 Packages [9,948 B]                                                                                                         
Get:15 http://ftp.halifax.rwth-aachen.de saucy/universe i386 Packages [5,571 kB]                                                                                                          
Get:16 http://ftp.halifax.rwth-aachen.de saucy/multiverse i386 Packages [134 kB]                                                                                                          
Get:17 http://ftp.halifax.rwth-aachen.de saucy/main Translation-en [694 kB]                                                                                                               
Hit http://ftp.halifax.rwth-aachen.de saucy/multiverse Translation-en                                                                                                                     
Hit http://ftp.halifax.rwth-aachen.de saucy/restricted Translation-en                                                                                                                     
Get:18 http://ftp.halifax.rwth-aachen.de saucy/universe Translation-en [3,840 kB]                                                                                                         
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/main Sources                                                              
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/restricted Sources                                                        
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/universe Sources                                                          
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/multiverse Sources                                                        
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/main amd64 Packages                                                       
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/restricted amd64 Packages                                                 
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/universe amd64 Packages                                                   
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/multiverse amd64 Packages                                                 
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/main i386 Packages                                                        
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/restricted i386 Packages                                                  
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/universe i386 Packages                                                    
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/multiverse i386 Packages                                                  
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/main Translation-en                                                       
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/multiverse Translation-en                                                 
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/restricted Translation-en                                                 
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/universe Translation-en                                                   
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/main Sources                                                            
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/restricted Sources                                                      
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/universe Sources                                                        
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/multiverse Sources                                                      
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/main amd64 Packages                                                     
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/restricted amd64 Packages                                               
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/universe amd64 Packages                                                 
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/multiverse amd64 Packages                                               
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/main i386 Packages                                                      
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/restricted i386 Packages                                                
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/universe i386 Packages                                                  
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/multiverse i386 Packages                                                
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/main Translation-en                                                     
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/multiverse Translation-en                                               
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/restricted Translation-en                                               
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/universe Translation-en                                                 
Hit http://ftp.halifax.rwth-aachen.de saucy-security/main Sources                                                             
Hit http://ftp.halifax.rwth-aachen.de saucy-security/restricted Sources                                                       
Hit http://ftp.halifax.rwth-aachen.de saucy-security/universe Sources                                                         
Hit http://ftp.halifax.rwth-aachen.de saucy-security/multiverse Sources
Hit http://ftp.halifax.rwth-aachen.de saucy-security/main amd64 Packages
Hit http://ftp.halifax.rwth-aachen.de saucy-security/restricted amd64 Packages
Hit http://ftp.halifax.rwth-aachen.de saucy-security/universe amd64 Packages
Hit http://ftp.halifax.rwth-aachen.de saucy-security/multiverse amd64 Packages
Hit http://ftp.halifax.rwth-aachen.de saucy-security/main i386 Packages
Hit http://ftp.halifax.rwth-aachen.de saucy-security/restricted i386 Packages
Hit http://ftp.halifax.rwth-aachen.de saucy-security/universe i386 Packages
Hit http://ftp.halifax.rwth-aachen.de saucy-security/multiverse i386 Packages
Hit http://ftp.halifax.rwth-aachen.de saucy-security/main Translation-en
Hit http://ftp.halifax.rwth-aachen.de saucy-security/multiverse Translation-en
Hit http://ftp.halifax.rwth-aachen.de saucy-security/restricted Translation-en
Hit http://ftp.halifax.rwth-aachen.de saucy-security/universe Translation-en
Get:19 http://ftp.halifax.rwth-aachen.de saucy-proposed/restricted amd64 Packages [14 B]
Get:20 http://ftp.halifax.rwth-aachen.de saucy-proposed/main amd64 Packages [12.7 kB]
Get:21 http://ftp.halifax.rwth-aachen.de saucy-proposed/universe amd64 Packages [166 kB]
Get:22 http://ftp.halifax.rwth-aachen.de saucy-proposed/multiverse amd64 Packages [1,445 B]                                   
Get:23 http://ftp.halifax.rwth-aachen.de saucy-proposed/restricted i386 Packages [14 B]                                       
Get:24 http://ftp.halifax.rwth-aachen.de saucy-proposed/main i386 Packages [12.7 kB]                                          
Get:25 http://ftp.halifax.rwth-aachen.de saucy-proposed/universe i386 Packages [158 kB]                                       
Get:26 http://ftp.halifax.rwth-aachen.de saucy-proposed/multiverse i386 Packages [1,447 B]                                    
Get:27 http://ftp.halifax.rwth-aachen.de saucy-proposed/main Translation-en [6,869 B]                                         
Hit http://ftp.halifax.rwth-aachen.de saucy-proposed/multiverse Translation-en                                                
Hit http://ftp.halifax.rwth-aachen.de saucy-proposed/restricted Translation-en                                                
Get:28 http://ftp.halifax.rwth-aachen.de saucy-proposed/universe Translation-en [90.6 kB]                                     
Ign http://ftp.halifax.rwth-aachen.de saucy/main Translation-en_IN                                                            
Ign http://ftp.halifax.rwth-aachen.de saucy/multiverse Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy/restricted Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy/universe Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-updates/main Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-updates/multiverse Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-updates/restricted Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-updates/universe Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-backports/main Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-backports/multiverse Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-backports/restricted Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-backports/universe Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-security/main Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-security/multiverse Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-security/restricted Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-security/universe Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-proposed/main Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-proposed/multiverse Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-proposed/restricted Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-proposed/universe Translation-en_IN
Fetched 26.1 MB in 7min 27s (58.3 kB/s)
W: Failed to fetch http://packages.medibuntu.org/saucy/dists/free/non-free/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://packages.medibuntu.org/saucy/dists/free/non-free/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
a@A:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice : Depends: libreoffice-report-builder-bin but it is not installed
E: Unmet dependencies. Try using -f.

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libnetpbm10 linux-headers-3.9.0-5 linux-headers-3.9.0-5-generic linux-image-3.9.0-5-generic
  linux-image-extra-3.9.0-5-generic netpbm
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libreoffice-report-builder-bin
The following NEW packages will be installed:
  libreoffice-report-builder-bin
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
23 not fully installed or removed.
Need to get 0 B/820 kB of archives.
After this operation, 3,475 kB of additional disk space will be used.
Do you want to continue [Y/n]? 

(Reading database ... 284369 files and directories currently installed.)
Unpacking libreoffice-report-builder-bin (from .../libreoffice-report-builder-bin_1%3a4.0.2-0ubuntu5_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-report-builder-bin_1%3a4.0.2-0ubuntu5_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libreoffice/program/librptxmllo.so', which is also in package libreoffice-core 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-report-builder-bin_1%3a4.0.2-0ubuntu5_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by zika on 2013-06-18
> **levomac said:**
> I purged the default libre office with

sudo apt-get remove --purge libreoffice*

then installed the pre release ppa as follows

sudo add-apt-repository ppa:libreoffice/libreoffice-prereleases
sudo apt-get update
sudo apt-get install libreoffice

Libre office works fine ,install is also ok but no new updates and ppas install due the dependency issiues

trying 
sudo apt-get update and sudo apt-get dist-upgrade causes

```
 sudo apt-get update && sudo apt-get dist-upgrade
Hit http://archive.canonical.com saucy Release.gpg
Hit http://extras.ubuntu.com saucy Release.gpg                                 
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Get:1 http://ftp.halifax.rwth-aachen.de saucy Release.gpg [933 B]              
Hit http://archive.canonical.com saucy Release                                 
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Hit http://ftp.halifax.rwth-aachen.de saucy-updates Release.gpg                
Hit http://extras.ubuntu.com saucy Release                                     
Hit http://archive.canonical.com saucy/partner Sources                         
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Ign http://packages.medibuntu.org free Release.gpg                             
Hit http://ftp.halifax.rwth-aachen.de saucy-backports Release.gpg              
Hit http://archive.canonical.com saucy/partner amd64 Packages                  
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Hit http://extras.ubuntu.com saucy/main Sources                                
Hit http://ftp.halifax.rwth-aachen.de saucy-security Release.gpg               
Hit http://archive.canonical.com saucy/partner i386 Packages                   
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Hit http://extras.ubuntu.com saucy/main amd64 Packages                         
Ign http://packages.medibuntu.org free Release                                 
Get:2 http://ftp.halifax.rwth-aachen.de saucy-proposed Release.gpg [933 B]     
Hit http://ppa.launchpad.net saucy Release.gpg                                 
Hit http://extras.ubuntu.com saucy/main i386 Packages                          
Get:3 http://ftp.halifax.rwth-aachen.de saucy Release [40.8 kB]                
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://ftp.halifax.rwth-aachen.de saucy-updates Release                    
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://ppa.launchpad.net saucy Release                                     
Hit http://ppa.launchpad.net saucy Release                                     
Ign http://archive.canonical.com saucy/partner Translation-en_IN               
Ign http://archive.canonical.com saucy/partner Translation-en                  
Ign http://extras.ubuntu.com saucy/main Translation-en_IN                      
Hit http://ppa.launchpad.net saucy Release                                     
Ign http://extras.ubuntu.com saucy/main Translation-en                         
Hit http://ftp.halifax.rwth-aachen.de saucy-backports Release                  
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Hit http://ppa.launchpad.net saucy/main i386 Packages                 
Hit http://ppa.launchpad.net saucy/main amd64 Packages                
Hit http://ppa.launchpad.net saucy/main i386 Packages                 
Hit http://ftp.halifax.rwth-aachen.de saucy-security Release                   
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Err http://packages.medibuntu.org free/non-free amd64 Packages                 
  404  Not Found
Get:4 http://ftp.halifax.rwth-aachen.de saucy-proposed Release [40.8 kB]       
Hit http://ppa.launchpad.net saucy/main i386 Packages                          
Err http://packages.medibuntu.org free/non-free i386 Packages                  
  404  Not Found
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Ign http://packages.medibuntu.org free/non-free Translation-en_IN              
Hit http://ppa.launchpad.net saucy/main i386 Packages                          
Get:5 http://ftp.halifax.rwth-aachen.de saucy/main Sources [983 kB]            
Ign http://packages.medibuntu.org free/non-free Translation-en                 
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Hit http://ppa.launchpad.net saucy/main i386 Packages                          
Hit http://ppa.launchpad.net saucy/main amd64 Packages                         
Hit http://ppa.launchpad.net saucy/main i386 Packages                          
Ign http://ppa.launchpad.net saucy/main Translation-en_IN                      
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Ign http://ppa.launchpad.net saucy/main Translation-en_IN                      
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Ign http://ppa.launchpad.net saucy/main Translation-en_IN                      
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Ign http://ppa.launchpad.net saucy/main Translation-en_IN                      
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Ign http://ppa.launchpad.net saucy/main Translation-en_IN                      
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Ign http://ppa.launchpad.net saucy/main Translation-en_IN                      
Ign http://ppa.launchpad.net saucy/main Translation-en                         
Get:6 http://ftp.halifax.rwth-aachen.de saucy/restricted Sources [6,236 B]     
Get:7 http://ftp.halifax.rwth-aachen.de saucy/universe Sources [6,037 kB]      
Get:8 http://ftp.halifax.rwth-aachen.de saucy/multiverse Sources [175 kB]      
Get:9 http://ftp.halifax.rwth-aachen.de saucy/main amd64 Packages [1,206 kB]   
Get:10 http://ftp.halifax.rwth-aachen.de saucy/restricted amd64 Packages [9,936 B]
Get:11 http://ftp.halifax.rwth-aachen.de saucy/universe amd64 Packages [5,566 kB]
Get:12 http://ftp.halifax.rwth-aachen.de saucy/multiverse amd64 Packages [132 kB]                                                                                                         
Get:13 http://ftp.halifax.rwth-aachen.de saucy/main i386 Packages [1,204 kB]                                                                                                              
Get:14 http://ftp.halifax.rwth-aachen.de saucy/restricted i386 Packages [9,948 B]                                                                                                         
Get:15 http://ftp.halifax.rwth-aachen.de saucy/universe i386 Packages [5,571 kB]                                                                                                          
Get:16 http://ftp.halifax.rwth-aachen.de saucy/multiverse i386 Packages [134 kB]                                                                                                          
Get:17 http://ftp.halifax.rwth-aachen.de saucy/main Translation-en [694 kB]                                                                                                               
Hit http://ftp.halifax.rwth-aachen.de saucy/multiverse Translation-en                                                                                                                     
Hit http://ftp.halifax.rwth-aachen.de saucy/restricted Translation-en                                                                                                                     
Get:18 http://ftp.halifax.rwth-aachen.de saucy/universe Translation-en [3,840 kB]                                                                                                         
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/main Sources                                                              
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/restricted Sources                                                        
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/universe Sources                                                          
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/multiverse Sources                                                        
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/main amd64 Packages                                                       
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/restricted amd64 Packages                                                 
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/universe amd64 Packages                                                   
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/multiverse amd64 Packages                                                 
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/main i386 Packages                                                        
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/restricted i386 Packages                                                  
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/universe i386 Packages                                                    
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/multiverse i386 Packages                                                  
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/main Translation-en                                                       
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/multiverse Translation-en                                                 
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/restricted Translation-en                                                 
Hit http://ftp.halifax.rwth-aachen.de saucy-updates/universe Translation-en                                                   
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/main Sources                                                            
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/restricted Sources                                                      
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/universe Sources                                                        
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/multiverse Sources                                                      
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/main amd64 Packages                                                     
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/restricted amd64 Packages                                               
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/universe amd64 Packages                                                 
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/multiverse amd64 Packages                                               
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/main i386 Packages                                                      
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/restricted i386 Packages                                                
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/universe i386 Packages                                                  
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/multiverse i386 Packages                                                
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/main Translation-en                                                     
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/multiverse Translation-en                                               
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/restricted Translation-en                                               
Hit http://ftp.halifax.rwth-aachen.de saucy-backports/universe Translation-en                                                 
Hit http://ftp.halifax.rwth-aachen.de saucy-security/main Sources                                                             
Hit http://ftp.halifax.rwth-aachen.de saucy-security/restricted Sources                                                       
Hit http://ftp.halifax.rwth-aachen.de saucy-security/universe Sources                                                         
Hit http://ftp.halifax.rwth-aachen.de saucy-security/multiverse Sources
Hit http://ftp.halifax.rwth-aachen.de saucy-security/main amd64 Packages
Hit http://ftp.halifax.rwth-aachen.de saucy-security/restricted amd64 Packages
Hit http://ftp.halifax.rwth-aachen.de saucy-security/universe amd64 Packages
Hit http://ftp.halifax.rwth-aachen.de saucy-security/multiverse amd64 Packages
Hit http://ftp.halifax.rwth-aachen.de saucy-security/main i386 Packages
Hit http://ftp.halifax.rwth-aachen.de saucy-security/restricted i386 Packages
Hit http://ftp.halifax.rwth-aachen.de saucy-security/universe i386 Packages
Hit http://ftp.halifax.rwth-aachen.de saucy-security/multiverse i386 Packages
Hit http://ftp.halifax.rwth-aachen.de saucy-security/main Translation-en
Hit http://ftp.halifax.rwth-aachen.de saucy-security/multiverse Translation-en
Hit http://ftp.halifax.rwth-aachen.de saucy-security/restricted Translation-en
Hit http://ftp.halifax.rwth-aachen.de saucy-security/universe Translation-en
Get:19 http://ftp.halifax.rwth-aachen.de saucy-proposed/restricted amd64 Packages [14 B]
Get:20 http://ftp.halifax.rwth-aachen.de saucy-proposed/main amd64 Packages [12.7 kB]
Get:21 http://ftp.halifax.rwth-aachen.de saucy-proposed/universe amd64 Packages [166 kB]
Get:22 http://ftp.halifax.rwth-aachen.de saucy-proposed/multiverse amd64 Packages [1,445 B]                                   
Get:23 http://ftp.halifax.rwth-aachen.de saucy-proposed/restricted i386 Packages [14 B]                                       
Get:24 http://ftp.halifax.rwth-aachen.de saucy-proposed/main i386 Packages [12.7 kB]                                          
Get:25 http://ftp.halifax.rwth-aachen.de saucy-proposed/universe i386 Packages [158 kB]                                       
Get:26 http://ftp.halifax.rwth-aachen.de saucy-proposed/multiverse i386 Packages [1,447 B]                                    
Get:27 http://ftp.halifax.rwth-aachen.de saucy-proposed/main Translation-en [6,869 B]                                         
Hit http://ftp.halifax.rwth-aachen.de saucy-proposed/multiverse Translation-en                                                
Hit http://ftp.halifax.rwth-aachen.de saucy-proposed/restricted Translation-en                                                
Get:28 http://ftp.halifax.rwth-aachen.de saucy-proposed/universe Translation-en [90.6 kB]                                     
Ign http://ftp.halifax.rwth-aachen.de saucy/main Translation-en_IN                                                            
Ign http://ftp.halifax.rwth-aachen.de saucy/multiverse Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy/restricted Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy/universe Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-updates/main Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-updates/multiverse Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-updates/restricted Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-updates/universe Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-backports/main Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-backports/multiverse Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-backports/restricted Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-backports/universe Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-security/main Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-security/multiverse Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-security/restricted Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-security/universe Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-proposed/main Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-proposed/multiverse Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-proposed/restricted Translation-en_IN
Ign http://ftp.halifax.rwth-aachen.de saucy-proposed/universe Translation-en_IN
Fetched 26.1 MB in 7min 27s (58.3 kB/s)
W: Failed to fetch http://packages.medibuntu.org/saucy/dists/free/non-free/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://packages.medibuntu.org/saucy/dists/free/non-free/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
a@A:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice : Depends: libreoffice-report-builder-bin but it is not installed
E: Unmet dependencies. Try using -f.

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libnetpbm10 linux-headers-3.9.0-5 linux-headers-3.9.0-5-generic linux-image-3.9.0-5-generic
  linux-image-extra-3.9.0-5-generic netpbm
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libreoffice-report-builder-bin
The following NEW packages will be installed:
  libreoffice-report-builder-bin
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
23 not fully installed or removed.
Need to get 0 B/820 kB of archives.
After this operation, 3,475 kB of additional disk space will be used.
Do you want to continue [Y/n]? 

(Reading database ... 284369 files and directories currently installed.)
Unpacking libreoffice-report-builder-bin (from .../libreoffice-report-builder-bin_1%3a4.0.2-0ubuntu5_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-report-builder-bin_1%3a4.0.2-0ubuntu5_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libreoffice/program/librptxmllo.so', which is also in package libreoffice-core 1:4.1.0~beta2~incompleteinternals1-0ubuntu1~ppa4
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-report-builder-bin_1%3a4.0.2-0ubuntu5_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```I do not have libreoffice-report-builder-bin installed...
As I can see You did not follow instructions:> sudo apt-get install libreoffice # for versions up to 4.0
sudo apt-get install libreoffice-writer libreoffice-calc libreoffice-impress # for 4.1
I did after a good cleanup... I think I made this or similar mistake in my first attempt documented above...
Look into problem with medibuntu, while You're into this...

---

### Post by levomac on 2013-06-18
ok messed up completely trying to purge stuff.
Doing a fresh install ,soooo frustrating.

---

### Post by zika on 2013-06-18
> **levomac said:**
> ok messed up completely trying to purge stuff.
Doing a fresh install ,soooo frustrating.No need for reinstall...

---

### Post by zika on 2013-06-22
```
Setting up python3-uno (1:4.1.0~rc1-buildfix1-0ubuntu1~ppa1) ...  File "/usr/lib/python3/dist-packages/uno.py", line 3
    echo os.putenv('URE_BOOTSTRAP', 'vnd.sun.star.pathname:usr/lib/libreoffice/program/fundamentalrc')
          ^
SyntaxError: invalid syntax
```

Update&#8321;: Remove &#8222;echo&#8220; at the very beginning of the line 3 in /usr/lib/python3/dist-packages/uno.py and all is good...
Update&#8322;: I found that [they]("https://launchpad.net/~libreoffice/+archive/libreoffice-prereleases")'ve already found that bug... :P
Update&#8323;: Fixed in today's upgrade(s)...

---

