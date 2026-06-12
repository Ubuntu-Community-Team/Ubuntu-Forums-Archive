---
title: "working flashplugin for ringtail -solved"
date: 2013-04-11
forum: Ubuntu Development Version
---

### Post by pumo on 2013-04-11
where do I find working flashplugin for new 13.04?
I distupgraded today.

ii  flashplugin-installer                         11.2.202.280ubuntu0.12.10.1         amd64        Adobe Flash Player plugin installer

---

### Post by zika on 2013-04-11
> **pumo said:**
> where do I find working flashplugin for new 13.04?
I distupgraded today.

ii  flashplugin-installer                         11.2.202.280ubuntu0.12.10.1         amd64        Adobe Flash Player plugin installerWhat is the problem? You have right/last package installed... Did install finish OK?
Check if plugin is in the right place```
ls -alt /usr/lib/flashplugin-installer/libflashplayer.so
```
If it is try puting it also in a folder that many browers do check:
```
mkdir ~/.mozilla/plugins
cp /usr/lib/flashplugin-installer/libflashplayer.so ~/.mozilla/plugins/libflashplayer.so
```

---

### Post by pfeiffep on 2013-04-11
Thanks zika, I had similar 'warnings' about flashplugin-installer and just posted additional [details]("http://ubuntuforums.org/showthread.php?t=2134464")

What symptoms would be present if this is a failure?

Just loaded a youtube video and played it perfectly - chormium browser Version 25.0.1364.160 Ubuntu 13.04 (25.0.1364.160-0ubuntu3)

---

### Post by pumo on 2013-04-11
there is only
```

:~$ ls -alt /usr/lib/flashplugin-installer/
-rwxr-xr-x 1 root root 792 huhti  9 22:47 /usr/lib/flashplugin-installer/install_plugin

```

and when I try to run in it:
```

sudo ./install_plugin 
Installing from local file 
cp: cannot stat ‘’: No such file or directory

```

and when I try to install again (removing first ofcourse):
```

pumo@s:/usr/lib/flashplugin-installer$ sudo aptitude install flashplugin-installer
The following NEW packages will be installed:
  flashplugin-installer 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 6*970 B of archives. After unpacking 139 kB will be used.
Get: 1 http://fi.archive.ubuntu.com/ubuntu/ raring/multiverse flashplugin-installer amd64 11.2.202.280ubuntu0.12.10.1 [6*970 B]
Fetched 6*970 B in 0s (50,9 kB/s)                
sh: 0: getcwd() failed: No such file or directory
sh: 0: getcwd() failed: No such file or directory
sh: 0: getcwd() failed: No such file or directory
Preconfiguring packages ...
sh: 0: getcwd() failed: No such file or directory
Selecting previously unselected package flashplugin-installer.
(Reading database ... 217123 files and directories currently installed.)
Unpacking flashplugin-installer (from .../flashplugin-installer_11.2.202.280ubuntu0.12.10.1_amd64.deb) ...
Processing triggers for update-notifier-common ...
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.280.orig.tar.gz
Installing from local file /tmp/tmpLjkf5N.gz
Flash Plugin installed.
Setting up flashplugin-installer (11.2.202.280ubuntu0.12.10.1) ...
                                         
sh: 0: getcwd() failed: No such file or directory


```

---

### Post by zika on 2013-04-11
> **pumo said:**
> there is only
```

:~$ ls -alt /usr/lib/flashplugin-installer/
-rwxr-xr-x 1 root root 792 huhti  9 22:47 /usr/lib/flashplugin-installer/install_plugin

```

and when I try to run in it:
```

sudo ./install_plugin 
Installing from local file 
cp: cannot stat &#8216;&#8217;: No such file or directory

```Something went wrong with install of flashplugin-installer... You're not supposed to start any script, that shoud happen automagically... Try reinstalll. What was the reason behind using dist-upgrade?
Until You sort things with flashpkugin-installer You could just DL archive, (for 64_bit) : [http://get.adobe.com/flashplayer/completion/?installer=Flash_Player_11.2_for_other_Linux_(.tar.gz)_64-bit](http://get.adobe.com/flashplayer/completion/?installer=Flash_Player_11.2_for_other_Linux_(.tar.gz)_64-bit) (For other: [http://get.adobe.com/flashplayer/?no_redirect](http://get.adobe.com/flashplayer/?no_redirect)) and take libflashplayer.so from archive and put it in ~/.mozilla/plugins ... That should work. If it does not we could make some adjustments with update-alternatives...

---

### Post by pumo on 2013-04-11
updatet sametime :) look my previous reply.
solved, I did remove with synaptic and reinstall now it works.

---

