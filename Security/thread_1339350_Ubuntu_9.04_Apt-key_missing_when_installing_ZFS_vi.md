---
title: "Ubuntu 9.04: Apt-key missing when installing ZFS via zfs-fuse"
date: 2009-11-27
forum: Security
---

### Post by mikropolip on 2009-11-27
Hi! 
I want to install ZFS via zfs-fuse package in , so I follow the instructions from [COLOR="DarkRed"][Ubuntu Wiki]("https://wiki.ubuntu.com/ZFS/")[/COLOR].

I add repositories at [http://ppa.launchpad.net/brcha/](http://ppa.launchpad.net/brcha/) but while apt-getting I get warning that the package cannot be authenticated. 

Since there is no information about needed apt-key in the Ubuntu ZFS wiki (And it is a mistake) and since I'm pretty paranoid, I try key of package maintainer, Filip Brcic.

```
pub   1024D/162CE87F 2007-06-15
uid                  Filip Brcic <brcha@gna.org>
uid                  Filip Brcic <fbrcic@gmail.com>
uid                  Filip Brcic <brcha@laposte.net>
uid                  Filip Brcic <brcha@galeb.etf.bg.ac.yu>
uid                  Filip Brcic <brcha@users.sourceforge.net>
uid                  [jpeg image of size 4315]
sub   1024g/AC1A891A 2007-06-15
```

But still get the same warning that the package can't be authenticated.

So, there is my question: how can I retrieve package gpg-key without actually installing it?

---

### Post by sisco311 on 2009-11-27
[https://launchpad.net/~brcha/+archive/ppa]("https://launchpad.net/~brcha/+archive/ppa") -> Technical details about this PPA -> Signing key:

To download and add the key, just run:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 48A22A95
```

---

### Post by mikropolip on 2009-11-27
Thank you! But somehow I still get the same error. Here is my apt-key list:
```
~$ sudo apt-key list
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   1024R/365C5CA1 2009-01-22
uid                  Launchpad PPA for transmissionbt

pub   1024R/43CBFCC0 2009-01-20
uid                  Launchpad PPA for Exaile Developers

pub   1024D/162CE87F 2007-06-15
uid                  Filip Brcic <brcha@gna.org>
uid                  Filip Brcic <fbrcic@gmail.com>
uid                  Filip Brcic <brcha@laposte.net>
uid                  Filip Brcic <brcha@galeb.etf.bg.ac.yu>
uid                  Filip Brcic <brcha@users.sourceforge.net>
uid                  [jpeg image of size 4315]
sub   1024g/AC1A891A 2007-06-15

pub   1024R/48A22A95 2009-01-21
uid                  Launchpad PPA for Filip Brcic
```

I've tried apt-get update, but when I run apt-get install zfs-fuse I still have ```
WARNING: The following packages cannot be authenticated!
  zfs-fuse

```

---

### Post by sisco311 on 2009-11-27
Did you run:
```
sudo apt-get update
```?

---

### Post by mikropolip on 2009-11-27
> **sisco311 said:**
> Did you run:
```
sudo apt-get update
```?
Precisely yes.

```

xxx@xxx:~$ sudo apt-get update
Hit http://archive.ubuntu.com jaunty Release.gpg
Ign http://archive.ubuntu.com jaunty/main Translation-en_US         
Hit http://archive.canonical.com jaunty Release.gpg                 
Ign http://archive.canonical.com jaunty/partner Translation-en_US   
Hit http://ppa.launchpad.net jaunty Release.gpg                     
Ign http://ppa.launchpad.net jaunty/main Translation-en_US           
Hit http://ppa.launchpad.net jaunty Release.gpg                      
Ign http://archive.ubuntu.com jaunty/restricted Translation-en_US    
Ign http://archive.ubuntu.com jaunty/universe Translation-en_US      
Ign http://archive.ubuntu.com jaunty/multiverse Translation-en_US    
Hit http://archive.ubuntu.com jaunty-updates Release.gpg             
Ign http://archive.ubuntu.com jaunty-updates/main Translation-en_US  
Ign http://archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Hit http://archive.canonical.com jaunty Release                      
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Ign http://ppa.launchpad.net jaunty Release.gpg
Ign http://ppa.launchpad.net jaunty/main Translation-en_US
Hit http://ppa.launchpad.net jaunty Release
Ign http://archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://archive.ubuntu.com jaunty-security Release.gpg
Ign http://archive.ubuntu.com jaunty-security/main Translation-en_US
Hit http://archive.canonical.com jaunty/partner Packages             
Hit http://ppa.launchpad.net jaunty Release                          
Get:1 http://ppa.launchpad.net jaunty Release [31.1kB]               
Ign http://archive.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://archive.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://archive.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://archive.ubuntu.com jaunty-backports Release.gpg
Ign http://archive.ubuntu.com jaunty-backports/restricted Translation-en_US
Ign http://archive.ubuntu.com jaunty-backports/main Translation-en_US
Ign http://archive.ubuntu.com jaunty-backports/multiverse Translation-en_US
Hit http://ppa.launchpad.net jaunty/main Packages
Ign http://archive.ubuntu.com jaunty-backports/universe Translation-en_US
Hit http://archive.ubuntu.com jaunty Release
Hit http://archive.ubuntu.com jaunty-updates Release
Hit http://archive.ubuntu.com jaunty-security Release
Ign http://ppa.launchpad.net jaunty/main Packages                   
Ign http://ppa.launchpad.net jaunty/main Sources                    
Hit http://ppa.launchpad.net jaunty/main Packages                   
Hit http://ppa.launchpad.net jaunty/main Sources                    
Hit http://archive.ubuntu.com jaunty-backports Release              
Hit http://ppa.launchpad.net jaunty/main Packages                   
Hit http://ppa.launchpad.net jaunty/main Sources
Hit http://archive.ubuntu.com jaunty/main Packages
Hit http://archive.ubuntu.com jaunty/restricted Packages
Hit http://archive.ubuntu.com jaunty/main Sources
Hit http://archive.ubuntu.com jaunty/restricted Sources
Hit http://archive.ubuntu.com jaunty/universe Packages
Hit http://archive.ubuntu.com jaunty/universe Sources
Hit http://archive.ubuntu.com jaunty/multiverse Packages
Hit http://archive.ubuntu.com jaunty/multiverse Sources
Hit http://archive.ubuntu.com jaunty-updates/main Packages
Hit http://archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://archive.ubuntu.com jaunty-updates/main Sources
Hit http://archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://archive.ubuntu.com jaunty-updates/universe Packages
Hit http://archive.ubuntu.com jaunty-updates/universe Sources
Hit http://archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://archive.ubuntu.com jaunty-security/main Packages
Hit http://archive.ubuntu.com jaunty-security/restricted Packages
Hit http://archive.ubuntu.com jaunty-security/main Sources
Hit http://archive.ubuntu.com jaunty-security/restricted Sources
Hit http://archive.ubuntu.com jaunty-security/universe Packages
Hit http://archive.ubuntu.com jaunty-security/universe Sources
Hit http://archive.ubuntu.com jaunty-security/multiverse Packages
Hit http://archive.ubuntu.com jaunty-security/multiverse Sources
Hit http://archive.ubuntu.com jaunty-backports/restricted Packages
Hit http://archive.ubuntu.com jaunty-backports/main Packages
Hit http://archive.ubuntu.com jaunty-backports/multiverse Packages
Hit http://archive.ubuntu.com jaunty-backports/universe Packages
Fetched 1B in 1s (1B/s)  
Reading package lists... Done
xxx@xxx:~$ sudo apt-get install zfs-fuse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libaio1
The following NEW packages will be installed:
  libaio1 zfs-fuse
0 upgraded, 2 newly installed, 0 to remove and 1 not upgraded.
Need to get 1518kB of archives.
After this operation, 4338kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  zfs-fuse
Install these packages without verification [y/N]? n
E: Some packages could not be authenticated


```

---

