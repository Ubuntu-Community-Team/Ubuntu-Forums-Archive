---
title: "Synaptic: Temporary failure resolving 'http'"
date: 2005-07-28
forum: Repositories &amp; Backports
---

### Post by lespro on 2005-07-28
Hello everybody,

I'm using Ubuntu for a few days and I'm very glad of it but ... when I'm trying to use synaptic nothing goes properly ...

Indeeed, each time I get the same message :

**Could not download all repository indexes** 

```
 
The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

http://archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg: Temporary failure resolving 'http'
http://archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz: Temporary failure resolving 'http'
http://archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz: Temporary failure resolving 'http'
http://archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz: Temporary failure resolving 'http'

```

then

```

**The following problems were found on your system:**

W: Couldn't stat source package list http://archive.ubuntu.com hoary/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com hoary/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)

```


Precisions :

1) I can browse on the Internet via Firefox  whitout any problem ...
2) I browse on the Internet through a proxy but ...
    a) I entered the address of my proxy into the preferences of synaptic
    b) and I also tried to enter this address in /etc/apt/apt.conf.d/70debconf

Unfortunately all my efforts are useless ...

Anybody has any idea about what kind of matter it is and how to resolve it ???

Thank you very much for answering me if you kwow a detail that I don't !!!

---

### Post by Xian on 2005-07-28
You either have an improperly configured sources.list or that particular server is experiencing difficulties. Does your /etc/apt/sources.list look similar to the one in the [Starter Guide](http://ubuntuguide.org/#extrarepositories)? 

You can try mine if you are having further problems.

```
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

deb-src http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hoary-security main restricted universe
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted universe

deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
deb ftp://ftp2.caliu.info/backports/ hoary-extras main universe multiverse restricted
```

Then do a '$ sudo apt-get update' session in either a terminal,
or by reloading the sources in Synaptic.

---

### Post by dbw on 2006-12-17
I also receive this error:
```
Err http://us.archive.ubuntu.com dapper Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'

```

I believe that this is a problem with either gpg or wireless.

My sources.list is:
```
# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

## dapper-commercial by canonical
## currently has realplay (realplayer 10) and opera (opera 9)
deb http://archive.canonical.com/ubuntu dapper-commercial main

```

Any advice?

---

### Post by dbw on 2006-12-17
[Another forum is discussing these problems.]("http://ubuntuforums.org/showthread.php?p=1900192#post1900192")

---

