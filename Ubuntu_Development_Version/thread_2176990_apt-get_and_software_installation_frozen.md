---
title: "apt-get and software installation frozen"
date: 2013-09-26
forum: Ubuntu Development Version
---

### Post by Ramesh_Jude_Fernando on 2013-09-26
Hi I am trying to run the Ubuntu software installer and it continues to give error.

```
ramesh@ramesh-Aspire-V3-771:~$ apt-get upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
ramesh@ramesh-Aspire-V3-771:~$ sudo apt-get upgrad
E: Invalid operation upgrad
ramesh@ramesh-Aspire-V3-771:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 plasma-active : Depends: ksplash-theme-active but it is not installed
                 Recommends: plasma-widgets-active (= 1:0.5-0ubuntu1) but it is not installed
E: Unmet dependencies. Try using -f.
ramesh@ramesh-Aspire-V3-771:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  gir1.2-gst-plugins-base-0.10 gir1.2-gstreamer-0.10 libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev startactive-ksplash-theme
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ksplash-theme-active
The following NEW packages will be installed:
  ksplash-theme-active
0 upgraded, 1 newly installed, 0 to remove and 38 not upgraded.
1 not fully installed or removed.
Need to get 0 B/55.0 kB of archives.
After this operation, 113 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 570252 files and directories currently installed.)
Unpacking ksplash-theme-active (from .../ksplash-theme-active_1%3a0.4-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/ksplash-theme-active_1%3a0.4-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/share/kde4/apps/ksplash/Themes/qmldefault/images/kdeletter.png', which is also in package startactive-ksplash-theme 3.0-0ubuntu1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/ksplash-theme-active_1%3a0.4-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

How do I get the ksplash*.* to be removed permanently so apt-get and software installer will work.

Thanks
Ramesh

---

### Post by ibjsb4 on 2013-09-26
Try:

```
sudo apt-get clean && sudo apt-get update && sudo apt-get upgrade
```

---

### Post by grahammechanical on 2013-09-27
One package is not installing. Does this prevent you from installing and removing packages? When you run apt-get update does it update the sources list? When you run apt-get upgrade does it upgrade the packages that need updating or does the whole operation fail?

During the development cycle when I get situations like this I wait. I update/upgrade every day and sometimes things get fixed. I have just noticed that we now have the beta version of Ubuntu available for download. I will use it to re-install a broken saucy salamander that I have. It is an installation that I gave up wasting my time on a few weeks ago. There must also be beta 2 versions of the flavours available. Sometimes the simplest way of fixing things is to re-install.

By the way did you do this

> [COLOR=#000000]The following packages were automatically installed and are no longer required:[/COLOR]
[COLOR=#000000]gir1.2-gst-plugins-base-0.10 gir1.2-gstreamer-0.10 libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev startactive-ksplash-theme[/COLOR]
[COLOR=#000000]_Use 'apt-get autoremove' to remove them_.[/COLOR]

Did you notice that startactive-ksplash-theme is part of the problem?

> [COLOR=#000000]which is also in package startactive-ksplash-theme 3.0-0ubuntu1[/COLOR]

Could be the answer

Regards.

---

### Post by zika on 2013-09-27
```
sudo apt-get update
sudo apt-get autoremove
sudo apt-get upgrade
sudo apt-get dist-upgrade (be carefull before You answer &#8222;Y&#8220;... Do not do that unless You're completely sure...)

```
Current example:```
:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libunity-core-6.0-7
The following NEW packages will be installed:
  libunity-core-6.0-8
The following packages will be upgraded:
  unity unity-services
2 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 2,214 kB of archives.
After this operation, 8,192 B disk space will be freed.
Do you want to continue [Y/n]?Y
```
Out with old and in with new... ;)
Also, learn to read logs for packages to see what is new, what is old and what stuff is safe to remove...

---

### Post by Ramesh_Jude_Fernando on 2013-09-27
Thanks for your help, this is the output I received
```
ramesh@ramesh-Aspire-V3-771:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 plasma-active : Depends: ksplash-theme-active but it is not installed
                 Recommends: plasma-widgets-active (= 1:0.5-0ubuntu1) but it is not installed
E: Unmet dependencies. Try using -f.
ramesh@ramesh-Aspire-V3-771:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 plasma-active : Depends: ksplash-theme-active but it is not installed
                 Recommends: plasma-widgets-active (= 1:0.5-0ubuntu1) but it is not installed
E: Unmet dependencies. Try using -f.
ramesh@ramesh-Aspire-V3-771:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 plasma-active : Depends: ksplash-theme-active but it is not installed
                 Recommends: plasma-widgets-active (= 1:0.5-0ubuntu1) but it is not installed
E: Unmet dependencies. Try using -f.
ramesh@ramesh-Aspire-V3-771:~$
```

---

### Post by Ramesh_Jude_Fernando on 2013-09-27
I am thinking of backing up to Ubuntu One and then reinstalling a fresh one??

---

### Post by Bashing-om on 2013-09-27
Ramesh_Jude_Fernando; Hi !
Do not be too hasty in (re-)installing ,, this is but a dependency issue .. 
Try giving the package manager what it is missing;
Terminal codes:
```

sudo apt-get install ksplash-theme-active
sudo apt-get install  plasma-widgets-active
sudo apt-get update
sudo apt-get upgrade

```

See if all is happy now .

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by Ramesh_Jude_Fernando on 2013-09-28
Tried both result :-(
```

ramesh@ramesh-Aspire-V3-771:~$ sudo apt-get install ksplash-theme-active
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-gst-plugins-base-0.10 gir1.2-gstreamer-0.10
  libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev
  startactive-ksplash-theme
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  ksplash-theme-active
0 upgraded, 1 newly installed, 0 to remove and 364 not upgraded.
1 not fully installed or removed.
Need to get 0 B/55.0 kB of archives.
After this operation, 113 kB of additional disk space will be used.
(Reading database ... 570252 files and directories currently installed.)
Unpacking ksplash-theme-active (from .../ksplash-theme-active_1%3a0.4-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/ksplash-theme-active_1%3a0.4-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/share/kde4/apps/ksplash/Themes/qmldefault/images/kdeletter.png', which is also in package startactive-ksplash-theme 3.0-0ubuntu1
Errors were encountered while processing:
 /var/cache/apt/archives/ksplash-theme-active_1%3a0.4-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ramesh@ramesh-Aspire-V3-771:~$ sudo apt-get install  plasma-widgets-active
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 plasma-active : Depends: ksplash-theme-active but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

 Thanks for the link. Would you believe I actually installed Slackware Linux dual boot  with  Windows 95 off a CD-ROM on the second PC I ever bought,  when I went back into university on a IBM PC-clone system  with Pentium and 32 megs of RAM, all the way back in 1996. I recall it was an ASUS motherboard.

---

### Post by Ramesh_Jude_Fernando on 2013-09-28
Python 2.7 or at least IDLE and tkinter menus opening old Python 2.7 files I was using  for a Computational Investing were not being read. What is weird is Stani's editor worked fine loading the files, just  Python 2.7 for  Linux IDLE  (installed from Ubuntu Unity software installer) didn't work I will clean and reinstall. And keep away from Saucy 13.10 until it officially comes out.

---

### Post by sandyd on 2013-09-28
> **Ramesh_Jude_Fernando said:**
> Tried both result :-(
```

ramesh@ramesh-Aspire-V3-771:~$ sudo apt-get install ksplash-theme-active
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gir1.2-gst-plugins-base-0.10 gir1.2-gstreamer-0.10
  libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev
  startactive-ksplash-theme
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  ksplash-theme-active
0 upgraded, 1 newly installed, 0 to remove and 364 not upgraded.
1 not fully installed or removed.
Need to get 0 B/55.0 kB of archives.
After this operation, 113 kB of additional disk space will be used.
(Reading database ... 570252 files and directories currently installed.)
Unpacking ksplash-theme-active (from .../ksplash-theme-active_1%3a0.4-0ubuntu1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/ksplash-theme-active_1%3a0.4-0ubuntu1_all.deb (--unpack):
 trying to overwrite '/usr/share/kde4/apps/ksplash/Themes/qmldefault/images/kdeletter.png', which is also in package startactive-ksplash-theme 3.0-0ubuntu1
Errors were encountered while processing:
 /var/cache/apt/archives/ksplash-theme-active_1%3a0.4-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
ramesh@ramesh-Aspire-V3-771:~$ sudo apt-get install  plasma-widgets-active
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 plasma-active : Depends: ksplash-theme-active but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

 Thanks for the link. Would you believe I actually installed Slackware Linux dual boot  with  Windows 95 off a CD-ROM on the second PC I ever bought,  when I went back into university on a IBM PC-clone system  with Pentium and 32 megs of RAM, all the way back in 1996. I recall it was an ASUS motherboard.

```

**The following packages were automatically installed and are no longer required:**
gir1.2-gst-plugins-base-0.10 gir1.2-gstreamer-0.10
libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev
**startactive-ksplash-theme**
```
Try using dpkg to force remove startactive-ksplash-theme while ignoring deps, and installing ksplash-theme-active via apt - apt doesnt handle dependency hell too well - might break things though

---

### Post by Ramesh_Jude_Fernando on 2013-09-28
Thanks. I just reinstalled. For some reason it wouldn't let me install 13.04 Roaring.  The installer on USB stick didn't install 13.04, so I had to install 13.10 Saucy. Oh well. Hopefully it will be fine when it comes out.

If I didn't personally reply to the other suggestions please note I didn't ignore them. I appreciate everyone's help.

Thank you all.
Ramesh

---

