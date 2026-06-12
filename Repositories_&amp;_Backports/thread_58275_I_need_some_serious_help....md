---
title: "I need some serious help..."
date: 2005-08-19
forum: Repositories &amp; Backports
---

### Post by Muhammad on 2005-08-19
I got this when I accessed Synaptic...

```
W: Couldn't stat source package list http://au.archive.ubuntu.com hoary/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://au.archive.ubuntu.com hoary/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://au.archive.ubuntu.com hoary/universe Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://au.archive.ubuntu.com hoary-updates/main Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://au.archive.ubuntu.com hoary-updates/restricted Packages (/var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)

```

I need help... If this problem is unsolveable, then I may aswell say farewell to ubuntu and go back to that Shitty Windows XP  :mad:

---

### Post by giopas on 2005-08-19
I think you have just to try to reconfigure "sources.list", copying and pasting the source.list from the ubuntu guide.

If nothing change, try putting the Hoary CD in your desktop cd player, and running "apt-cdrom".

enjoy, ;)
giopas

---

### Post by Muhammad on 2005-08-19
I edited the sources.list according to the ubuntuguide.org just like you said, and when I inserted the command

```
apt-cdrom
```

I recieved this 

```
root@ubuntu:~ # apt-cdrom
apt 0.6.35ubuntu2 for linux i386 compiled on Apr  6 2005 20:37:35
Usage: apt-cdrom [options] command

apt-cdrom is a tool to add CDROM's to APT's source list. The
CDROM mount point and device information is taken from apt.conf
and /etc/fstab.

Commands:
   add - Add a CDROM
   ident - Report the identity of a CDROM

Options:
  -h   This help text
  -d   CD-ROM mount point
  -r   Rename a recognized CD-ROM
  -m   No mounting
  -f   Fast mode, don't check package files
  -a   Thorough scan mode
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp

```

Now when I launched Synaptic again, I got this error messege:

```
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)

```

and when I issued this command:

```
sudo apt-get update

```

I recieved this:

```
Err http://ubuntu-backports.mirrormax.net hoary-backports Release.gpg
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Err http://archive.ubuntu.com hoary Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Err http://ubuntu-backports.mirrormax.net hoary-extras Release.gpg
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Err http://us.archive.ubuntu.com hoary Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Ign http://archive.ubuntu.com hoary Release
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release
Err http://us.archive.ubuntu.com hoary-updates Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Ign http://archive.ubuntu.com hoary/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release
Ign http://us.archive.ubuntu.com hoary Release
Ign http://archive.ubuntu.com hoary/multiverse Sources
Ign http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Ign http://us.archive.ubuntu.com hoary-updates Release
Err http://archive.ubuntu.com hoary/multiverse Packages
  Temporary failure resolving 'archive.ubuntu.com'
Ign http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Ign http://us.archive.ubuntu.com hoary/main Packages
Err http://archive.ubuntu.com hoary/multiverse Sources
  Temporary failure resolving 'archive.ubuntu.com'
Ign http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Ign http://us.archive.ubuntu.com hoary/restricted Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Ign http://us.archive.ubuntu.com hoary/main Sources
Ign http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Ign http://us.archive.ubuntu.com hoary/restricted Sources
Ign http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Ign http://us.archive.ubuntu.com hoary/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Ign http://us.archive.ubuntu.com hoary/universe Sources
Ign http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Ign http://us.archive.ubuntu.com hoary-updates/main Packages
Err http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Ign http://us.archive.ubuntu.com hoary-updates/restricted Packages
Err http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Ign http://us.archive.ubuntu.com hoary-updates/main Sources
Err http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Ign http://us.archive.ubuntu.com hoary-updates/restricted Sources
Err http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Err http://us.archive.ubuntu.com hoary/main Packages
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Err http://us.archive.ubuntu.com hoary/restricted Packages
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Err http://us.archive.ubuntu.com hoary/main Sources
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Err http://us.archive.ubuntu.com hoary/restricted Sources
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Err http://us.archive.ubuntu.com hoary/universe Packages
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com hoary/universe Sources
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com hoary-updates/main Packages
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com hoary-updates/restricted Packages
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com hoary-updates/main Sources
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://us.archive.ubuntu.com hoary-updates/restricted Sources
  Temporary failure resolving 'us.archive.ubuntu.com'
Err http://security.ubuntu.com hoary-security Release.gpg
  Temporary failure resolving 'security.ubuntu.com'
Ign http://security.ubuntu.com hoary-security Release
Ign http://security.ubuntu.com hoary-security/main Packages
Ign http://security.ubuntu.com hoary-security/restricted Packages
Ign http://security.ubuntu.com hoary-security/main Sources
Ign http://security.ubuntu.com hoary-security/restricted Sources
Ign http://security.ubuntu.com hoary-security/universe Packages
Ign http://security.ubuntu.com hoary-security/universe Sources
Err http://security.ubuntu.com hoary-security/main Packages
  Temporary failure resolving 'security.ubuntu.com'
Err http://security.ubuntu.com hoary-security/restricted Packages
  Temporary failure resolving 'security.ubuntu.com'
Err http://security.ubuntu.com hoary-security/main Sources
  Temporary failure resolving 'security.ubuntu.com'
Err http://security.ubuntu.com hoary-security/restricted Sources
  Temporary failure resolving 'security.ubuntu.com'
Err http://security.ubuntu.com hoary-security/universe Packages
  Temporary failure resolving 'security.ubuntu.com'
Err http://security.ubuntu.com hoary-security/universe Sources
  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/Release.gpg  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/Release.gpg  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/Release.gpg  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/Release.gpg  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hoary/multiverse/binary-i386/Packages.gz  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hoary/multiverse/source/Sources.gz  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/main/binary-i386/Packages.gz  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/universe/binary-i386/Packages.gz  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/multiverse/binary-i386/Packages.gz  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/source/Sources.gz  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://ubuntu-backports.mirrormax.net/dists/hoary-extras/restricted/binary-i386/Packages.gz  Temporary failure resolving 'ubuntu-backports.mirrormax.net'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz  Temporary failure resolving 'us.archive.ubuntu.com'Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/source/Sources.gz  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/source/Sources.gz  Temporary failure resolving 'security.ubuntu.com'
Reading package lists... Done
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://security.ubuntu.com hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary/multiversePackages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or d irectory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such fileor directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such fileor directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

...

---

### Post by giopas on 2005-08-19
try typing "apt-cdrom add", with your hoary cdrom insered: this has fixed my problem (that was almost the same as yours), I hope that will fix yours too... 

enjoy, ;)
giopas

---

### Post by Muhammad on 2005-08-19
I dunno how the hell did I fix this problem, but it's gone now, weird eh?

Thanks for the advice anyway giopas :)

---

