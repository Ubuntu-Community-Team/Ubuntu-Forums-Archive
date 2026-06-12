---
title: "Geary won't update"
date: 2019-04-05
forum: Ubuntu/Debian BASED
---

### Post by ray42 on 2019-04-05
Using Pop os 18.04LTS:

Geary shows in notification area, and software as a new update. When it try it fails. I suspect it is already installed, see image link.

Current version is 0.13.3

[https://www.dropbox.com/s/bi9c6hyv8b86mj5/Screenshot%20from%202019-04-05%2017-38-21.png?dl=0](https://www.dropbox.com/s/bi9c6hyv8b86mj5/Screenshot%20from%202019-04-05%2017-38-21.png?dl=0)

[IMG]https://www.dropbox.com/s/bi9c6hyv8b86mj5/Screenshot%20from%202019-04-05%2017-38-21.png?dl=0[/IMG][IMG]https://www.dropbox.com/s/bi9c6hyv8b86mj5/Screenshot%20from%202019-04-05%2017-38-21.png?dl=0[/IMG]

---

### Post by Rubi1200 on 2019-04-06
What happens if you run ```
sudo apt-get update
```?

Post any errors here please.

Thanks.

---

### Post by ray42 on 2019-04-06
No errors

---

### Post by Rubi1200 on 2019-04-07
Do you use the software?

---

### Post by ray42 on 2019-04-07
> **Rubi1200 said:**
> Do you use the software?

I have done before, and wish to again.

---

### Post by Rubi1200 on 2019-04-07
Would try this:

```
sudo apt-get update && apt-get upgrade geary
```

---

### Post by ray42 on 2019-04-07
The first part worked but the second failed i had to use:

```
sudo apt-get upgrade geary
```

The output was then:

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be DOWNGRADED:
  geary
0 to upgrade, 0 to newly install, 1 to downgrade, 0 to remove and 0 not to upgrade.
Need to get 0 B/1,743 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 281260 files and directories currently installed.)
Preparing to unpack .../geary_0.13.3-1~bionic1_amd64.deb ...
Unpacking geary (0.13.3-1~bionic1) over (0.13.3-1~bionic1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Processing triggers for libglib2.0-0:amd64 (2.56.3-0ubuntu0.18.04.1) ...
Setting up geary (0.13.3-1~bionic1) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
libdvd-pkg: Downloading orig source...
I: libdvdcss_1.4.2
/usr/bin/wget --tries=3 --timeout=40 --read-timeout=40 --continue -O libdvdcss_1.4.2.orig.tar.bz2 \
          http://download.videolan.org/pub/libdvdcss/1.4.2/libdvdcss-1.4.2.tar.bz2 \
        || /usr/bin/uscan --noconf --verbose --rename --destdir=/usr/src/libdvd-pkg --check-dirname-level=0 --force-download --download-current-version /usr/share/libdvd-pkg/debian
--2019-04-07 15:18:27--  http://download.videolan.org/pub/libdvdcss/1.4.2/libdvdcss-1.4.2.tar.bz2
Resolving download.videolan.org (download.videolan.org)... 2a01:e0d:1:3:58bf:fa02:c0de:5, 88.191.250.2
Connecting to download.videolan.org (download.videolan.org)|2a01:e0d:1:3:58bf:fa02:c0de:5|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 366824 (358K) [application/octet-stream]
Saving to: &#8216;libdvdcss_1.4.2.orig.tar.bz2&#8217;


libdvdcss_1.4.2.orig.tar 100%[===============================>] 358.23K   347KB/s    in 1.0s    


2019-04-07 15:18:28 (347 KB/s) - &#8216;libdvdcss_1.4.2.orig.tar.bz2&#8217; saved [366824/366824]


libdvd-pkg: Checking orig.tar integrity...
/usr/src/libdvd-pkg/libdvdcss_1.4.2.orig.tar.bz2: OK
libdvd-pkg: `apt-get check` failed, you may have broken packages. Aborting...



```

...and Geary still showing an update despite being at latest version.

---

### Post by Rubi1200 on 2019-04-07
It's odd because it says it is downgrading the package.

Perhaps remove and reinstall?

---

### Post by Frogs Hair on 2019-04-07
I see you are using Pop OS . Does it use Ubuntu repository its own repository ? The output of the following will tell you.

```
sudo apt update
```

---

### Post by ray42 on 2019-04-08
> **Rubi1200 said:**
> It's odd because it says it is downgrading the package.

Perhaps remove and reinstall?

How do I remove completely, database etc.?

Because as soon as I reinstall my old account are still present.

---

### Post by ray42 on 2019-04-08
> **Frogs Hair said:**
> I see you are using Pop OS . Does it use Ubuntu repository its own repository ? The output of the following will tell you.

```
Hit:1 http://archive.ubuntu.com/ubuntu bionic InReleaseIgn:2 http://dl.google.com/linux/chrome/deb stable InRelease                   
Hit:3 http://linux.teamviewer.com/deb stable InRelease                         
Hit:4 http://archive.ubuntu.com/ubuntu bionic-updates InRelease                
Hit:5 http://dl.google.com/linux/chrome/deb stable Release                     
Hit:6 http://ppa.launchpad.net/danielrichter2007/grub-customizer/ubuntu bionic InRelease
Hit:7 http://archive.ubuntu.com/ubuntu bionic-security InRelease               
Hit:8 http://archive.ubuntu.com/ubuntu bionic-backports InRelease              
Hit:9 http://ppa.launchpad.net/geary-team/releases/ubuntu bionic InRelease     
Hit:10 https://repo.skype.com/deb stable InRelease                             
Hit:11 http://ppa.launchpad.net/linrunner/tlp/ubuntu bionic InRelease          
Hit:12 https://deb.opera.com/opera-stable stable InRelease                     
Hit:13 http://ppa.launchpad.net/system76/pop/ubuntu bionic InRelease           
Hit:14 http://apt.pop-os.org/proprietary bionic InRelease                
Hit:15 http://ppa.launchpad.net/umang/indicator-stickynotes/ubuntu bionic InRelease
Reading package lists... Done                      
Building dependency tree       
Reading state information... Done
All packages are up-to-date.

```

I use the software centre which has a download for Geary, so I assume it is Pop OS.

---

### Post by Frogs Hair on 2019-04-08
> **ray42 said:**
> How do I remove completely, database etc.?

Because as soon as I reinstall my old account are still present.

You can remove the configuration files from home/hidden folders look in .config. Try ctrl + H to show hidden folders. A new folder will be created upon re-installation.

---

### Post by ray42 on 2019-04-08
Hmm, done this and email accounts are still found without set-up on re-installation. So does it appear that no data has been removed?

Also the terminal shows:

```

sudo apt-get upgrade



Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be DOWNGRADED:
  geary
0 to upgrade, 0 to newly install, 1 to downgrade, 0 to remove and 0 not to upgrade.
Need to get 0 B/1,743 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n]   

```

---

### Post by Frogs Hair on 2019-04-08
> Hmm, done this and email accounts are still found without set-up on  re-installation. So does it appear that no data has been removed?

Also the terminal shows: The info could be in the root file system for security reasons then. Geary is default on Ubuntu Budgie but I don't use it. My current version is 0.12.4-4 on 19.04. It may just be the repository is behind.

---

### Post by ray42 on 2019-06-28
I think I have fixed this with:

```

sudo apt update && sudo apt upgrade -y

```

Geary now at 0.13.3

I HAVE NO IDEA WHY THIS WORKED

Update:
No it didn't, error is back!

---

