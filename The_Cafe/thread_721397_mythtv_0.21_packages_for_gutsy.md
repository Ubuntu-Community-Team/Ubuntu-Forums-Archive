---
title: "mythtv 0.21 packages for gutsy"
date: 2008-03-11
forum: The Cafe
---

### Post by mtron on 2008-03-11
[B]EDIT: Forget all this here and grab myth 0.21 from gusty-Backpots!
For a upgrade from this packages, just enable the gutsy-Backports repository and run the apt-get install commands as shown below[/B]

for those of you eager to try the new mythtv 0.21 release, and don't wanna wait until hardy gets declared stable:

i've backported the current hardy mythtv packages to gutsy (32 bit) with prevu. The packages are tested and work nice on my system.

Be aware that this is nothing for Newcomers ;) you should have experience with mythtv and apt-get if you wanna try this packages

download the archive [here]("http://rapidshare.com/files/99073054/mythtv-0.21-ubuntu_gutsy_packages.tar.gz.html") (~ 60 MB)
unpack it under your home, and note the full path to the extracted packages. You will need it later. in my case this is 
```
/home/mtron/myth/packages
```

now add the new package source to your /etc/apt/sources.list:
```
## myth 0.21 backports
deb file:/home/mtron/myth/packages ./
```

replacing* /home/mtron/myth/packages* with the path to the packages on your system.

reload the package information and install or upgrade the base mythtv system. In this case i will install a full master-backend & frontend on one system. If you need a different setup you should read the wiki pages about mythtv and the package descriptions.

make apt aware of the new package source
```
sudo apt-get update
```

myth base install with back & frontend
```
sudo apt-get install mythtv mythtv-common mythtv-database mythtv-doc mythtv-frontend mythtv-backend-master libmyth-dev libmyth-perl libmyth-python
```
 
common mythplugins
```
sudo apt-get install mytharchive mytharchive-data mythbrowser mythcontrols mythexport mythvideo mythgallery mythgame mythmovies mythmusic mythnews mythphone mythplugins mythstream mythtv-transcode-utils mythweather mythweb
```

additional themes for mythtv
```
sudo apt-get install mythtv-theme-blootube mythtv-theme-blootube-osd mythtv-theme-gray-osd mythtv-theme-isthmus mythtv-theme-iulius mythtv-theme-iulius-osd mythtv-theme-minimalist-wide mythtv-theme-mythcenter mythtv-theme-mythcenter-wide mythtv-theme-projectgrayhem mythtv-theme-projectgrayhem-osd mythtv-theme-retro mythtv-theme-retro-osd mythtv-theme-titivillus mythtv-theme-titivillus-osd
```

The packages are not signed, and apt will complain about that during install. Apart from that the  system is ready to use after an upgrade. if you have installed mythtv for the first time, run mythtv-setup first.

---

### Post by d_morgan on 2008-03-11
Hi mtron,  thanks for the post.  I've installed the mythbuntu alpha3 as my frontend on a seperate system and its complaining about a protocol mismatch with the backend which is a regular desktop/backend for me.  Now i'd like to install 0.21 on the backend so that it matches the 0.21 frontend..

The packages seem to be missing the libmyth-0.21-0 package.  I completely removed my myth packages on the backend  using the synaptic package manager gui before i tried your instructions.. and i use your exact instructions.  The output i get is:

```

dmorgan@office-desktop:~$ sudo apt-get install mythtv mythtv-common mythtv-database mythtv-doc mythtv-frontend mythtv-backend-master libmyth-dev libmyth-perl libmyth-python
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libmyth-dev: Depends: libmyth-0.21-0 (= 0.21.0-0ubuntu2~7.10prevu1) but it is not installable
  mythtv: Depends: mythtv-backend (= 0.21.0-0ubuntu2~7.10prevu1) but it is not going to be installed
  mythtv-backend-master: Depends: mythtv-backend (= 0.21.0-0ubuntu2~7.10prevu1) but it is not going to be installed
  mythtv-frontend: Depends: libmyth-0.21-0 (>= 0.21.0) but it is not installable
E: Broken packages

```

Do you have any suggestions?

---

### Post by mtron on 2008-03-12
the package libmyth-0.21-0_0.21.0-0ubuntu2~7.10prevu1_i386.deb is part of the download archive, but i forgot to list it in the Package file.

Thanks for the hint. just add 

> Package: libmyth-0.21-0
Source: mythtv
Version: 0.21.0-0ubuntu2~7.10prevu1
Architecture: i386
Bugs: mailto:ubuntu-mythtv@lists.ubuntu.com
Maintainer: MythTV Ubuntu Maintainers <ubuntu-mythtv@lists.ubuntu.com>
Installed-Size: 20788
Depends: fftw3, liba52-0.7.4, libartsc0 (>= 1.5.0-1), libasound2 (>> 1.0.14), libavc1394-0 (>= 0.5.3), libc6 (>= 2.6-1), libfaac0 (>= 1.24clean), libfaad2-0 (>= 2.0.0+cvs20040908+mp4v2+bmp), libfreetype6 (>= 2.3.5), libgcc1 (>= 1:4.2.1), libgl1-mesa-glx | libgl1, libglib2.0-0 (>= 2.14.0), libglu1-mesa | libglu1, libiec61883-0 (>= 1.1.0), libjack0 (>= 0.103.0), liblame0 (>= 3.97), liblircclient0, libqt3-mt (>= 3:3.3.8really3.3.7), libraw1394-8, libstdc++6 (>= 4.2.1), libx11-6, libx264-54, libxext6, libxinerama1, libxmu6, libxrandr2 (>= 2:1.2.0), libxv1, libxvidcore4 (>= 1:1.0.0-0.0), libxvmc1, libxxf86vm1, zlib1g (>= 1:1.2.3.3.dfsg-1), libqt3-mt-mysql | libqt3c102-mt-mysql
Conflicts: mythtv (<< 0.7-5)
Replaces: mythtv (<< 0.7-5)
Filename: ./libmyth-0.21-0_0.21.0-0ubuntu2~7.10prevu1_i386.deb
Size: 7953376
MD5sum: c98746f6177ed5d139cdd29a99b39b96
Section: multiverse/libs
Priority: optional
Description: Common library code for MythTV and add-on modules (runtime)
 MythTV provides a unified graphical interface for recording and viewing
 television programs. Refer to the mythtv package for more information.
 .
 This package contains a shared library, libmyth, which is used by various
 components in the system.


to the "Packages" file in the same folder as  the debs and reload the package information
> sudo apt-get update
sudo apt-get install libmyth-0.21-0

i'have uploaded a fixed download archive. Sorry for the mistake!

---

### Post by d_morgan on 2008-03-12
that did it.  thanks.

---

### Post by svtcontour on 2008-03-13
> **d_morgan said:**
> Hi mtron,  thanks for the post.  I've installed the mythbuntu alpha3 as my frontend on a seperate system and its complaining about a protocol mismatch with the backend which is a regular desktop/backend for me.  Now i'd like to install 0.21 on the backend so that it matches the 0.21 frontend..

The packages seem to be missing the libmyth-0.21-0 package.  I completely removed my myth packages on the backend  using the synaptic package manager gui before i tried your instructions.. and i use your exact instructions.  The output i get is:

```

dmorgan@office-desktop:~$ sudo apt-get install mythtv mythtv-common mythtv-database mythtv-doc mythtv-frontend mythtv-backend-master libmyth-dev libmyth-perl libmyth-python
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libmyth-dev: Depends: libmyth-0.21-0 (= 0.21.0-0ubuntu2~7.10prevu1) but it is not installable
  mythtv: Depends: mythtv-backend (= 0.21.0-0ubuntu2~7.10prevu1) but it is not going to be installed
  mythtv-backend-master: Depends: mythtv-backend (= 0.21.0-0ubuntu2~7.10prevu1) but it is not going to be installed
  mythtv-frontend: Depends: libmyth-0.21-0 (>= 0.21.0) but it is not installable
E: Broken packages

```

Do you have any suggestions?


I basically get the same thing, but this is from a fresh install

> 
sudo apt-get install mythtv mythtv-common mythtv-database mythtv-doc mythtv-frontend mythtv-backend-master libmyth-dev libmyth-perl libmyth-python
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
  mythtv: Depends: mythtv-backend (= 0.21.0-0ubuntu2~7.10prevu1) but it is not going to be installed
  mythtv-backend-master: Depends: mythtv-backend (= 0.21.0-0ubuntu2~7.10prevu1) but it is not going to be installed
E: Broken packages
root@htpc:/home/htpc/Desktop/myth/packages#


---

### Post by mtron on 2008-03-13
so you mixed a svn install with those packages? that won't work, either SVN or the Packages in the archive, not mixing both!

---

### Post by svtcontour on 2008-03-13
Ok,

I think I got it to work with Mythbuntu, do these messages look ok?


When I run "sudo apt-get install mythtv mythtv-common mythtv-database mythtv-doc mythtv-frontend mythtv-backend-master libmyth-dev libmyth-perl libmyth-python"
> 
12 upgraded, 62 newly installed, 2 to remove and 107 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

When I run "sudo apt-get install mytharchive mytharchive-data mythbrowser mythcontrols mythexport mythvideo mythgallery mythgame mythmovies mythmusic mythnews mythphone mythplugins mythstream mythtv-transcode-utils mythweather mythweb"
> Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package mythexport


When I run "sudo apt-get install mythtv-theme-blootube mythtv-theme-blootube-osd mythtv-theme-gray-osd mythtv-theme-isthmus mythtv-theme-iulius mythtv-theme-iulius-osd mythtv-theme-minimalist-wide mythtv-theme-mythcenter mythtv-theme-mythcenter-wide mythtv-theme-projectgrayhem mythtv-theme-projectgrayhem-osd mythtv-theme-retro mythtv-theme-retro-osd mythtv-theme-titivillus mythtv-theme-titivillus-osd"
> 0 upgraded, 15 newly installed, 0 to remove and 121 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

---

### Post by pops66 on 2008-03-13
You know, I hate to ruin everyone's fun, but Myth 0.21 is available in the standard gutsy backports as of yesterday.  If you're having trouble, you might try those.

---

### Post by mcsmith on 2008-03-13
First, I apologize for the length of this post.

I'm stuck in the process of updating MythTV from 0.20 to 0.21 on Gutsy.  The database upgrade that's caused me problems, however I seem to have gotten past them, although I'd appreciate feedback on my workaround.

I was originally at verion 1160 of the schema (and have the backup of the database at this revision).  When I run mythbackend to update the database, the first problem encountered is when upgrading to schema version 1171.  I get the following:

2008-03-13 10:58:07.347 Upgrading to schema version 1171
2008-03-13 10:58:07.349 DB Error (Performing database upgrade): 
Query was: INSERT storagegroup (groupname, hostname, dirname)     SELECT 'Default', hostname, data     FROM settings     WHERE value = 'RecordFilePrefix'; 
Error was: Driver error was [2/1062]:
QMYSQL3: Unable to execute query
Database error was:
Duplicate entry 'Default-xw6000-/var/video' for key 2
 
new version: 1171
2008-03-13 10:58:07.349 Database Schema upgrade FAILED, unlocking.
2008-03-13 10:58:07.350 Couldn't upgrade database to new schema

I solved this by doing the following:

mysql> truncate storagegroup;

Upon restarting mythbackend, the absence of storagegroup rows seems to be recovered.  The next problem is when upgradint to schema version 1181.  I get the following:

2008-03-13 11:03:18.813 Upgrading to schema version 1181
2008-03-13 11:03:18.862 DB Error (Performing database upgrade): 
Query was: ALTER TABLE recordedmarkup MODIFY mark MEDIUMINT UNSIGNED NOT NULL DEFAULT 0, MODIFY type TINYINT NOT NULL DEFAULT 0; 
Error was: Driver error was [2/1062]:
QMYSQL3: Unable to execute query
Database error was:
Duplicate entry '1005-2008-02-21 21:00:00-5-0' for key 1
 
new version: 1181
2008-03-13 11:03:18.863 Database Schema upgrade FAILED, unlocking.
2008-03-13 11:03:18.863 Couldn't upgrade database to new schema

I looked at the contents of the recordedmarkup table and find the following rows for the specified starttime:

mysql> select * from recordedmarkup where starttime = "2008-02-21 21:00:00" order by mark;
+--------+---------------------+----------------------+--------+------+
| chanid | starttime           | mark                 | offset | type |
+--------+---------------------+----------------------+--------+------+
|   1005 | 2008-02-21 21:00:00 | -5345200269870549280 | NULL   |    4 | 
|   1005 | 2008-02-21 21:00:00 | -4623262621601872528 | NULL   |    4 | 
|   1005 | 2008-02-21 21:00:00 | -4623258584332567608 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 | -4623256935065125944 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                    0 | NULL   |   -3 | 
|   1005 | 2008-02-21 21:00:00 |                    0 | NULL   |    4 | 
|   1005 | 2008-02-21 21:00:00 |                    5 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                10888 | NULL   |    4 | 
|   1005 | 2008-02-21 21:00:00 |                11327 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                11395 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                12745 | NULL   |    4 | 
|   1005 | 2008-02-21 21:00:00 |                13644 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                14029 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                14695 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                14723 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                24992 | NULL   |    4 | 
|   1005 | 2008-02-21 21:00:00 |                25902 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                26352 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                28152 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                29796 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                30407 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                31308 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                31311 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                44201 | NULL   |    4 | 
|   1005 | 2008-02-21 21:00:00 |                44203 | NULL   |    4 | 
|   1005 | 2008-02-21 21:00:00 |                45113 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                46013 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                47362 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                49162 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                49613 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                50513 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                51863 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                52313 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                52335 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                62483 | NULL   |    4 | 
|   1005 | 2008-02-21 21:00:00 |                64295 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                64938 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                65195 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                65645 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                66095 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                67000 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                67905 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                68355 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                68376 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                70194 | NULL   |    4 | 
|   1005 | 2008-02-21 21:00:00 |                71093 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                71118 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                85542 | NULL   |    4 | 
|   1005 | 2008-02-21 21:00:00 |                86440 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                87343 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                89460 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                89593 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                90043 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                90967 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |                92919 | NULL   |    5 | 
|   1005 | 2008-02-21 21:00:00 |   580676541877321730 | NULL   |    4 | 
+--------+---------------------+----------------------+--------+------+
56 rows in set (0.00 sec)

I don't see any duplicate keys, but the large positive and negative values may be what's causing the problem, considering that the datatype of mark is being changed to unsigned mediumint.  I deleted the rows for this timestamp (is this table used to mark where commercials are in the recording??) to see if that would get around the problem.

mysql> delete from recordedmarkup where starttime = "2008-02-21 21:00:00";
Query OK, 56 rows affected (0.00 sec)

I then restart mythbackend, which seems to complete:

root@xw6000:~# /usr/bin/mythbackend
2008-03-13 11:12:26.690 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-13 11:12:26.691 Empty LocalHostName.
2008-03-13 11:12:26.691 Using localhost value of xw6000
2008-03-13 11:12:26.707 New DB connection, total: 1
2008-03-13 11:12:26.712 Connected to database 'mythconverg' at host: localhost
2008-03-13 11:12:26.713 Closing DB connection named 'DBManager0'
2008-03-13 11:12:26.714 Connected to database 'mythconverg' at host: localhost
2008-03-13 11:12:26.715 New DB connection, total: 2
2008-03-13 11:12:26.716 Connected to database 'mythconverg' at host: localhost
2008-03-13 11:12:26.723 Current Schema Version: 1180
2008-03-13 11:12:26.732 New DB connection, total: 3
2008-03-13 11:12:26.740 Connected to database 'mythconverg' at host: localhost
2008-03-13 11:12:26.743 Backing up database to file: /var/video/mythconverg-1180-20080313111226.sql
2008-03-13 11:12:28.941 Compressing database backup file.
2008-03-13 11:12:31.185 Database Backup filename: /var/video/mythconverg-1180-20080313111226.sql.gz
2008-03-13 11:12:31.185 Database Backup complete.

Warning: MythTV wants to upgrade your database schema, from 1180 to 1214.

If your system becomes unstable, a database backup is located in /var/video/mythconverg-1180-20080313111226.sql.gz


Shall I upgrade this database? [yes]  
2008-03-13 11:12:37.170 Newest Schema Version : 1214
2008-03-13 11:12:37.172 Upgrading to schema version 1181
2008-03-13 11:12:39.426 Upgrading to schema version 1182
2008-03-13 11:12:39.428 Upgrading to schema version 1183
2008-03-13 11:12:39.771 Upgrading to schema version 1184
2008-03-13 11:12:39.790 Upgrading to schema version 1185
2008-03-13 11:12:39.793 Upgrading to schema version 1186
2008-03-13 11:12:39.796 Upgrading to schema version 1187
2008-03-13 11:12:39.851 Upgrading to schema version 1188
2008-03-13 11:12:39.859 Upgrading to schema version 1189
2008-03-13 11:12:39.885 Upgrading to schema version 1190
2008-03-13 11:12:39.891 Upgrading to schema version 1191
2008-03-13 11:12:39.918 Upgrading to schema version 1192
2008-03-13 11:12:39.945 Upgrading to schema version 1193
2008-03-13 11:12:39.971 Upgrading to schema version 1194
2008-03-13 11:12:40.002 Upgrading to schema version 1195
2008-03-13 11:12:40.038 Upgrading to schema version 1196
2008-03-13 11:12:40.040 Upgrading to schema version 1197
2008-03-13 11:12:40.042 Upgrading to schema version 1198
2008-03-13 11:12:40.043 New DB connection, total: 4
2008-03-13 11:12:40.044 Connected to database 'mythconverg' at host: localhost
2008-03-13 11:12:40.045 Upgrading to schema version 1199
2008-03-13 11:12:40.046 Upgrading to schema version 1200
2008-03-13 11:12:40.050 Upgrading to schema version 1201
2008-03-13 11:12:40.052 Upgrading to schema version 1202
2008-03-13 11:12:40.143 Upgrading to schema version 1203
2008-03-13 11:12:40.184 Upgrading to schema version 1204
2008-03-13 11:12:40.194 Upgrading to schema version 1205
2008-03-13 11:12:40.200 Upgrading to schema version 1206
2008-03-13 11:12:40.205 Upgrading to schema version 1207
2008-03-13 11:12:40.269 Upgrading to schema version 1208
2008-03-13 11:12:40.300 Upgrading to schema version 1209
2008-03-13 11:12:40.332 Upgrading to schema version 1210
2008-03-13 11:12:48.581 Upgrading to schema version 1211
2008-03-13 11:12:56.215 Upgrading to schema version 1212
2008-03-13 11:12:56.219 Upgrading to schema version 1213
2008-03-13 11:12:56.223 In 1213 upg
2008-03-13 11:12:56.224 Upgrading to schema version 1214
2008-03-13 11:12:56.227 Database Schema upgrade complete, unlocking.
Starting up as the master server.
2008-03-13 11:12:56.438 New DB scheduler connection
2008-03-13 11:12:56.438 Connected to database 'mythconverg' at host: localhost
2008-03-13 11:12:57.697 Main::Registering HttpStatus Extension
2008-03-13 11:12:57.697 mythbackend version: 0.21.20080304-1 [www.mythtv.org](www.mythtv.org)
2008-03-13 11:12:57.697 Enabled verbose msgs:  important general
2008-03-13 11:12:57.701 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-03-13 11:12:59.461 Reschedule requested for id -1.
2008-03-13 11:13:01.085 Scheduled 212 items in 1.6 = 0.91 match + 0.70 place
2008-03-13 11:13:01.090 Seem to be woken up by USER
2008-03-13 11:13:06.496 UPnpMedia: BuildMediaMap - no VideoStartupDir set,  skipping scan.
2008-03-13 11:13:53.907 MainServer::HandleVersion - Client speaks protocol version 31 but we speak 40!

root@xw6000:~# /etc/init.d/mythtv-backend start
 * Removing stale PID file /var/run/mythtv/mythbackend
 * Starting MythTV server: mythbackend                                                                                                                                                      [ OK ] 
root@xw6000:~# 

Unfortunately, now the mythweb client doesn't want to speak to the backend due to the protocol mismatch.

Any thoughts?

Regards,

Mike

---

### Post by svtcontour on 2008-03-13
Well,

I did a reboot, apt-get update, apt-get upgrade, and it looks like it went.  

I am at work so I will have to check for sure when I get home.

---

### Post by pops66 on 2008-03-15
The protocol mismatch presumably means that you need to upgrade mythweb to the new version.

---

### Post by mcsmith on 2008-03-15
I agree.  I checked the verison numbers of the various myth* packages and found that an older libmyth-0.20 was still installed, so I removed it, and then re-installed mythweb.  It looks like mythweb reinstalled libmyth-0.20.  Here's the list of packages I have installed:

> ```

root@xw6000:/var/www/mythweb/includes# dpkg --list | grep "myth"
rc  libmyth-0.20                               0.20.2-0ubuntu10.1                   Common library code for MythTV and add-on mo
ii  libmyth-0.21-0                             0.21.0-0ubuntu2~gutsy1               Common library code for MythTV and add-on mo
ii  libmyth-perl                               0.21.0-0ubuntu2~gutsy1               A PERL library to access some MythTV feature
ii  mythtv                                     0.21.0-0ubuntu2~gutsy1               A personal video recorder application (clien
ii  mythtv-backend                             0.21.0-0ubuntu2~gutsy1               A personal video recorder application (serve
ii  mythtv-common                              0.21.0-0ubuntu2~gutsy1               A personal video recorder application (commo
ii  mythtv-database                            0.21.0-0ubuntu2~gutsy1               A personal video recorder application (datab
ii  mythtv-doc                                 0.21.0-0ubuntu2~gutsy1               A personal video recorder application (docum
ii  mythtv-frontend                            0.21.0-0ubuntu2~gutsy1               A personal video recorder application (clien
ii  mythtv-theme-mythcenter-wide               0.21.0-0ubuntu1~gutsy1               The MythCenter Wide MythTV Theme
ii  mythtv-themes                              0.21.0-0ubuntu1~gutsy1               Additional themes metapackage for MythTV
ii  mythtv-transcode-utils                     0.21.0-0ubuntu2~gutsy1               Utilities used for transcoding MythTV tasks
ii  mythweb                                    0.21.0-0ubuntu2~gutsy1               Web interface add-on module for MythTV

```

Which package (if any of these) controls the protocol that mythweb is using to talk to the backend?

Thanks,

Mike

---

### Post by pops66 on 2008-03-17
You've got me now.  I have all the same packages installed as you do.  It does seem that mythweb needs the older version of libmyth.  Maybe start over and reinstall everything from the backports?  The other thought is perhaps deleting and rebuilding your database.  They could be trying to use different schema versions on the database and somehow that is causing the protocol mismatch.

---

### Post by MrHyde on 2008-03-21
I am still thinking about whether to upgrade from 0.20 to 0.21 or not.  I cannot afford to have the system down for long periods of time as the Myth box is our central point and the family will become very annoyed if it is not functioning.

I enabled the backport repository and ran apt-get upgrade.  The output was 

[PHP]The following packages have been kept back:
  mplayer mythbrowser mythmusic mythtv-backend mythtv-backend-master
  mythtv-common mythtv-database mythtv-frontend mythtv-transcode-utils
  mythvideo mythweather ntfs-3g
The following packages will be upgraded:
  libpq5 libtheora0 mytharchive mytharchive-data mythcontrols mythflix
  mythgallery mythgame mythnews mythphone mythstream mythtv-themes mythweb
  ubuntu-mythtv-frontend
14 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
[/PHP]

After that, I declined to proceed with the upgrade.  The 12 modules that will not be upgraded concern me.  Shouldn't they also be upgraded to 0.21.  Do I need to re-install everything from scratch?  What happens to my current myth database.. channels, schedules, etc, etc?

I just need a bit more information and confidence before I attempt the upgrade.

Thanks

---

### Post by Gadgetman on 2008-03-22
Use the following to perform the upgrade (and all should be well):-
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

After this I still had one remaining issue where mythvideo "was held back"!

However the following finally solved the issue:-
apt-get --reinstall install mythvideo

---

### Post by MrHyde on 2008-03-22
Thank you.  I have done the steps and everything has been upgraded and all my settings look to be still there.

However, I've noticed that all playback is now extremely blocky... almost unwatchable.  All the menu items during playback has a white tinge to all the writing, suggesting that it is rendering in the wrong size.  Also, I've noticed that when I first choose a channel, it takes up the entire screen and looks normal, then within 1 second, the screen gets compressed to a letterbox size and is blocky.  

The HD channels don't work at all.  The picture is stuck on the first frame and the audio sounds like it is going through a speech synthesizer... sounds all broken and computery.

Any ideas what is going on.

---

### Post by mcsmith on 2008-03-25
I went as far as uninstalling the entire myth* set of packages from my system, and then reinstalling.  The problem persisted.  I then uninstalled mythweb and found that the /var/www/mythweb directory was still there.  I manually deleted it, and then re-installed mythweb.  This time, rather than installing the mythweb stuff directly in /var/www, it created a symbolic link to the "real" location.  So, the previous stuff in /var/www/mythweb was the old 0.31 protocol, while the new stuff was residing in /usr/share/mythtv/mythweb.  It was just being ignored.

Hope this explanation helps someone else downstream.

Thanks to all who offered suggestions earlier.

Regards,

Mike

---

