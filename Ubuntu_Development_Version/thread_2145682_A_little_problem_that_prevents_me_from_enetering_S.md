---
title: "A little problem that prevents me from enetering Saucy train..."
date: 2013-05-16
forum: Ubuntu Development Version
---

### Post by zika on 2013-05-16
```
$ sudo aptitude upgrade
Resolving dependencies...                
The following NEW packages will be installed:
  libasound2-data{a} 
The following partially installed packages will be configured:
  libasound2 rhythmbox-plugin-zeitgeist 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/71.5 kB of archives. After unpacking 296 kB will be used.
Do you want to continue? [Y/n/?] 
(Reading database ... 276129 files and directories currently installed.)
Unpacking libasound2-data (from .../libasound2-data_1.0.27-4ubuntu1~raring1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libasound2-data_1.0.27-4ubuntu1~raring1_all.deb (--unpack):
 trying to overwrite '/usr/share/alsa/pcm/dmix.conf', which is also in package libasound2:amd64 1.0.27-4ubuntu1~raring1
Errors were encountered while processing:
 /var/cache/apt/archives/libasound2-data_1.0.27-4ubuntu1~raring1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: dependency problems prevent configuration of libasound2:amd64:
 libasound2:amd64 depends on libasound2-data (>= 1.0.27-4ubuntu1~raring1); however:
  Package libasound2-data is not installed.

dpkg: error processing libasound2:amd64 (--configure):
 dependency problems - leaving unconfigured
Setting up rhythmbox-plugin-zeitgeist (2.99.1+git20130515.86cbdc8c-0ubuntu1~13.04~ricotz0) ...
  File "/usr/lib/rhythmbox/plugins/rbzeitgeist/rbzeitgeist.py", line 40
    except RuntimeError, e:
                       ^
SyntaxError: invalid syntax

dpkg: error processing rhythmbox-plugin-zeitgeist (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 libasound2:amd64
 rhythmbox-plugin-zeitgeist
``````
$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.8.0-19 linux-headers-3.8.0-19-generic linux-image-3.8.0-19-generic linux-image-extra-3.8.0-19-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libasound2-data
The following NEW packages will be installed:
  libasound2-data
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/71.5 kB of archives.
After this operation, 296 kB of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 276129 files and directories currently installed.)
Unpacking libasound2-data (from .../libasound2-data_1.0.27-4ubuntu1~raring1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libasound2-data_1.0.27-4ubuntu1~raring1_all.deb (--unpack):
 trying to overwrite '/usr/share/alsa/pcm/dmix.conf', which is also in package libasound2:amd64 1.0.27-4ubuntu1~raring1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libasound2-data_1.0.27-4ubuntu1~raring1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```
libasound2 is from [https://launchpad.net/~ubuntu-audio-dev/+archive/alsa-testing](https://launchpad.net/~ubuntu-audio-dev/+archive/alsa-testing) ...
Any idea how to quickly fix this so I could join Testing...?
(Yes, I've tried downgrading, DL-ing .deb files and all the stuff that was in my sleave...)

Update&#8321;: Simple solutions are always the best... Solved.

---

### Post by Harry33 on 2013-05-16
> **zika said:**
> 
...
libasound2 is from [https://launchpad.net/~ubuntu-audio-dev/+archive/alsa-testing](https://launchpad.net/~ubuntu-audio-dev/+archive/alsa-testing) ...
Any idea how to quickly fix this so I could join Testing...?
(Yes, I've tried downgrading, DL-ing .deb files and all the stuff that was in my sleave...)

Update&#8321;: Simple solutions are always the best... Solved.


Why not use the saucy source for libasound2?
This one:
alsa-lib (1.0.25-4ubuntu4)
Here the package libasound2 is not divided into separate libasound2 and libasound2-data.
[https://launchpad.net/ubuntu/+source/alsa-lib/1.0.25-4ubuntu4](https://launchpad.net/ubuntu/+source/alsa-lib/1.0.25-4ubuntu4)

---

### Post by zika on 2013-05-16
> **Harry33 said:**
> Why not use the saucy source for libasound2?
This one:
alsa-lib (1.0.25-4ubuntu4)
Here the package libasound2 is not divided into separate libasound2 and libasound2-data.
[https://launchpad.net/ubuntu/+source/alsa-lib/1.0.25-4ubuntu4](https://launchpad.net/ubuntu/+source/alsa-lib/1.0.25-4ubuntu4)I had PPA for alsa-testing on so that is the way I've got into that problem (after a long trip) ...
I planned to upgrade to Saucy but that postponed it for half an hour until that nanobit of my lucidity kicked in and I've solved that lock...
I'm on Saucy now... ;)

Update&#8321;:Messed thing with Ricotz's PPAs and now I do not have Empathy (that I do not use), Rhythmbox and Totem and a bunch od stuff... I'll have to see what happened... I've turned 3 Ricotz's PPAs on and then wanted to ppa-purge them... In the process things got messy... ;)

This seems to be the list of packages I've messed up:

```
account-plugin-empathy empathy gstreamer1.0-plugins-bad gstreamer1.0-plugins-good libfarstream-0.2-2 libtelepathy-farstream3 mcp-account-manager-uoa nautilus-sendto-empathy rhythmbox rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune rhythmbox-plugin-zeitgeist rhythmbox-plugins rhythmbox-ubuntuone totem totem-mozilla totem-plugins gstreamer1.0-plugins-bad gstreamer1.0-plugins-good  gir1.2-gst-plugins-base-1.0 gir1.2-gstreamer-1.0 gstreamer1.0-alsa gstreamer1.0-libav gstreamer1.0-plugins-base gstreamer1.0-plugins-base-apps gstreamer1.0-plugins-ugly gstreamer1.0-pulseaudio gstreamer1.0-tools gstreamer1.0-x libgstreamer-plugins-bad1.0-0 libgstreamer-plugins-base1.0-0 libgstreamer-plugins-good1.0-0 libgstreamer1.0-0 rhythmbox-plugin-zeitgeist
```

Update&#8322;: Rhythmbox recovered...
It seems that Gstreamer files are OK...
Totem and Empathy on the to-do-list waiting... ;)

---

