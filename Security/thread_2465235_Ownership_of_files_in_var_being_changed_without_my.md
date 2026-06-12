---
title: "Ownership of files in var being changed without my knowledge."
date: 2021-07-26
forum: Security
---

### Post by EngineerStrange on 2021-07-26
I am having a problem which is being shown in the figure (using ubuntu 20.04.2) . Unfortunately the ownership is taken away from root sometimes and then problem occurs (owner becomes nobody). I set root as owner using sudo command but the problem again occurs in another file in the same directory after a few hours?
Am I affected by virus or what's happening? What should I do now?
[https://ubuntuforums.org/attachment.php?attachmentid=288875&stc=1](https://ubuntuforums.org/attachment.php?attachmentid=288875&stc=1)

---

### Post by ajgreeny on 2021-07-26
Please run terminal command ```
sudo apt-get update
``` and copy all of the output from that command back here. This will show much more detail about the problem which appears to be related to a launchpad.net_git-core repository.

---

### Post by deadflowr on 2021-07-26
You've already posted about the apt/package manager issue here:
[https://ubuntuforums.org/showthread.php?t=2465040]("https://ubuntuforums.org/showthread.php?t=2465040")


As far as file ownership changes go, we need more information to understand what is happening.
What files are changing?

---

### Post by EngineerStrange on 2021-07-27
If I use update command from terminal or synaptic or software-updater then I ownership automatically changes without doing anything and also error notification disappears.

---

### Post by EngineerStrange on 2021-07-27
Yeah I have already posted but that time I wasn't aware of the problems origin or what actually was going.

Regarding ownership change:
Files in directory /var/lib/apt/lists are being changed. The problem keeps occurring in new files as I fix one. Text files related to repositories are usually changed e.g. archive.canonical.com_ubuntu_dists_focal_InRelease, archive.ubuntu.com_ubuntu_dists_focal-backports_InRelease are two of the files where problem occured.
Is this because of virus? I have installed two gnome-shell-extensions and also virtual box and signed two kernel modules for virtual box one month ago. After that problem is arising and i don't which is the reason as I did all within 24 hours.

---

### Post by deadflowr on 2021-07-27
> Files in directory /var/lib/apt/lists are being changed. 
Those can change upon every time an apt update is run.
ajgreeny asked in this thread to post the results of the sudo apt update.
Do so.

---

### Post by EngineerStrange on 2021-07-27
```
Hit:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://ppa.launchpad.net/git-core/ppa/ubuntu](http://ppa.launchpad.net/git-core/ppa/ubuntu) focal InRelease             
Hit:3 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) stable InRelease          
Hit:4 [http://packages.microsoft.com/repos/edge](http://packages.microsoft.com/repos/edge) stable InRelease                
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal InRelease                         
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [114 kB]      
Hit:7 [https://packages.microsoft.com/repos/code](https://packages.microsoft.com/repos/code) stable InRelease               
Get:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB]        
Hit:9 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease                      
Get:10 [https://esm.ubuntu.com/infra/ubuntu](https://esm.ubuntu.com/infra/ubuntu) focal-infra-security InRelease [7,426 B]
Get:11 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security InRelease [114 kB]      
Get:12 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/multiverse amd64 Packages [22.3 kB]
Get:13 [https://esm.ubuntu.com/infra/ubuntu](https://esm.ubuntu.com/infra/ubuntu) focal-infra-updates InRelease [7,425 B]
Get:14 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-backports InRelease [101 kB]     
Get:15 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/multiverse i386 Packages [7,224 B]
Get:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages [1,127 kB]
Get:17 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/multiverse Translation-en [5,072 B]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:19 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 Packages [634 kB]
Get:20 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe i386 Packages [505 kB]
Get:21 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata [283 kB]
Get:22 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe Translation-en [97.8 kB]
Get:23 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 DEP-11 Metadata [60.7 kB]
Get:24 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 c-n-f Metadata [11.9 kB]
Get:25 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 DEP-11 Metadata [27.6 kB]
Get:26 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 c-n-f Metadata [8,364 B]
Get:27 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/restricted amd64 Packages [330 kB]
Get:28 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 c-n-f Metadata [13.8 kB]
Get:29 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/universe i386 Packages [626 kB]
Get:30 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/universe amd64 Packages [843 kB]
Get:31 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/universe amd64 DEP-11 Metadata [339 kB]
Get:32 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/universe DEP-11 48x48 Icons [210 kB]
Get:33 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/universe amd64 c-n-f Metadata [18.4 kB]
Get:34 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:35 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security/restricted amd64 Packages [330 kB]
Get:36 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security/main amd64 DEP-11 Metadata [27.6 kB]
Get:37 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security/main amd64 c-n-f Metadata [8,364 B]
Get:38 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security/universe amd64 Packages [634 kB]
Get:39 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security/universe i386 Packages [505 kB]
Get:40 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security/universe Translation-en [97.8 kB]
Get:41 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security/universe amd64 DEP-11 Metadata [60.7 kB]
Get:42 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security/universe amd64 c-n-f Metadata [11.9 kB]
Get:43 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security/multiverse amd64 Packages [22.3 kB]
Get:44 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security/multiverse i386 Packages [7,224 B]
Get:45 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security/multiverse Translation-en [5,072 B]
Get:46 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:47 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-backports/universe amd64 DEP-11 Metadata [10.3 kB]
Fetched 7,356 kB in 9s (812 kB/s)                                              
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
```

---

### Post by EngineerStrange on 2021-07-27
I have posted the output of sudo apt update. Btw I think you understood that files in directory /var/lib/apt/lists are being changed. Sorry I missed the ownership actually files idk if those changes or not ownership of one of existing files change which causes the problem.

---

### Post by EngineerStrange on 2021-07-27
I am worried because of these things [https://www.bleepingcomputer.com/news/security/new-linux-kernel-bug-lets-you-get-root-on-most-modern-distros/](https://www.bleepingcomputer.com/news/security/new-linux-kernel-bug-lets-you-get-root-on-most-modern-distros/)
[https://therecord.media/new-sequoia-bug-gives-you-root-access-on-most-linux-systems/](https://therecord.media/new-sequoia-bug-gives-you-root-access-on-most-linux-systems/)

---

### Post by The Cog on 2021-07-27
This command will list all the files and folders not owned by root in that folder:
```
sudo find /var/lib/apt -ls | head | awk '$5!="root"'
```
All I get is two folders owned by _apt:
```
~$ sudo find /var/lib/apt -ls | awk '$5!="root"'
   790433      4 drwxr-xr-x   2 _apt     root         4096 Jul 31  2020 /var/lib/apt/lists/auxfiles
   790434     24 drwx------   2 _apt     root        20480 Jul 26 16:26 /var/lib/apt/lists/partial

```
The user account **nobody** is sometimes used by processes that voluntarily drop their user priviledges so they can't do damage even if they get compromised - it is possible that your downloaded process is doing that while fetching new files. **nobody** is a valid user account on all systems, but you cannot log in as nobody, and it has very few access rights. I don't think there is anything amiss here. Even so, seek other opinions as well, to be sure.

---

### Post by EngineerStrange on 2021-07-27
But what is happening with me is unusual and as you said "The user account **nobody** is sometimes used by processes that  voluntarily drop their user priviledges so they can't do damage even if  they get compromised"- is this because something wrong has entered in my system or what?

---

### Post by scorp123 on 2021-07-27
> **EngineerStrange said:**
> But what is happening with me is unusual and as you said "The user account **nobody** is sometimes used by processes that  voluntarily drop their user priviledges so they can't do damage even if  they get compromised"- is this because something wrong has entered in my system or what?

No. It's standard procedure. A safety measure out of the box. Many processes, services and programs will drop all priviledges when they don't need them and then make use of "nobody".

There used to be a time (1980's) when everything on Unix (the spiritual ancestor of Linux) was running as "root" and every service that was available on the system was turned on by default. Many of those network services have completely fallen out of use exactly because they turned out to be such security nightmares and had more holes than a Swiss cheese, e.g. telnet, rsh, rlogin, rcp, finger, ftp, many others.

Back then Unix viruses such as the legendary "Morris Worm" were a thing.

Developers soon realised that running programs and services with way too many priviledges was a bad thing and most of the time is totally not necessary. Turning every available service on a system on per default was seen as a horribly bad idea too. So this all changed.

The solution was the invention of the "nobody" account and implementing processes and services in such a way that they would drop their rights to "root" and become "nobody" whenever they can. And all these unsafe services were either abolished completely or replaced with massively safer and encrypted alternatives such as SSH (which replaces rsh, rlogin, rcp, ftp and telnet ...).

When Linux was created in the early 1990's it adopted those changes too and that's where we are at today.

---

