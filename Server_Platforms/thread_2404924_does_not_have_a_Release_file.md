---
title: "does not have a Release file"
date: 2018-10-30
forum: Server Platforms
---

### Post by bn8595 on 2018-10-30
My problem is when I try to update to newer os I get an error saying "does not have a Release file". It happens for all the os versions.
I am pretty new to linux, dont know much.
we have separate repo server. and I get below error when I say apt-get update
Reading package lists... Done
E: The repository 'http://xxx(fqdn)/custom bionic/ Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

On any server my sources.list file looks like below 
# cat /etc/apt/sources.list
deb [arch=amd64] [http://fqdn/ubuntu](http://fqdn/ubuntu) bionic universe main restricted # disabled on upgrade to bionic
deb [arch=amd64] [http://fqdnl/ubuntu](http://fqdnl/ubuntu) bionic-updates universe main restricted # disabled on upgrade to bionic
deb [arch=amd64] [http://fqdnl/ubuntu](http://fqdnl/ubuntu) bionic-security universe main restricted # disabled on upgrade to bionic
deb [http://fqdn/custom/](http://fqdn/custom/) bionic/ # disabled on upgrade to bionic

and below is the mirror.list file on repo server


############# config ##################
#
# set base_path    /var/spool/apt-mirror
#
# set mirror_path  $base_path/mirror
# set skel_path    $base_path/skel
# set var_path     $base_path/var
# set cleanscript $var_path/clean.sh
# set defaultarch  <running host architecture>
# set postmirror_script $var_path/postmirror.sh
# set run_postmirror 0
set nthreads     20
set _tilde 0
#
############# end config ##############


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main restricted universe multiverse
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-proposed main restricted universe multiverse
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports main restricted universe multiverse


deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-proposed main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports main restricted universe multiverse




deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates main restricted universe multiverse
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed main restricted universe multiverse
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports main restricted universe multiverse


deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-security main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-proposed main restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports main restricted universe multiverse
clean [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)

When I say apt-mirror on repo server I get below o/p
# /usr/bin/apt-mirror
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = "en_US:en",
    LC_ALL = (unset),
    LC_CTYPE = "UTF-8",
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
Downloading 324 index files using 20 threads...
Begin time: Tue Oct 30 14:06:23 2018
[20]... [19]... [18]... [17]... [16]... [15]... [14]... [13]... [12]... [11]... [10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]...
End time: Tue Oct 30 14:06:30 2018


Processing tranlation indexes: [TTTTTT]


Downloading 1122 translation files using 20 threads...
Begin time: Tue Oct 30 14:06:30 2018
[20]... [19]... [18]... [17]... [16]... [15]... [14]... [13]... [12]... [11]... [10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]...
End time: Tue Oct 30 14:06:36 2018


Processing DEP-11 indexes: [DDDDDD]


Downloading 106 dep11 files using 20 threads...
Begin time: Tue Oct 30 14:06:36 2018
[20]... [19]... [18]... [17]... [16]... [15]... [14]... [13]... [12]... [11]... [10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]...
End time: Tue Oct 30 14:06:36 2018


Processing indexes: [SSSSSSPPPPPP]


0 bytes will be downloaded into archive.
Downloading 0 archive files using 0 threads...
Begin time: Tue Oct 30 14:07:42 2018
[0]...
End time: Tue Oct 30 14:07:42 2018


mkdir /var/spool/apt-mirror/mirror/archive.ubuntu.com/ubuntu/dists/bionic/main/binary-amd64: File exists at /usr/bin/apt-mirror line 887.

Please Help me solve this.

---

### Post by dino99 on 2018-10-30
fqdn is misconfigured at first glance.

---

### Post by Frogs Hair on 2018-10-30
Moved to *Server Platforms. *

---

### Post by bn8595 on 2018-10-30
fqdn is i replace my host name with fqdn. It  is like 
deb [arch=amd64] [http://test.example.nl/ubuntu](http://test.example.nl/ubuntu) bionic universe main restricted # disabled on upgrade to bionic
deb [arch=amd64] [http://test.example.nl/ubuntu](http://test.example.nl/ubuntu) bionic-updates universe main restricted # disabled on upgrade to bionic
deb [arch=amd64] [http://test.example.nl/ubuntu](http://test.example.nl/ubuntu) bionic-security universe main restricted # disabled on upgrade to bionic
deb [http://test.example.nl/custom/](http://test.example.nl/custom/) bionic/ # disabled on upgrade to bionic

---

### Post by TheFu on 2018-10-30
Looks to me like the repo isn't setup correctly based on the error.
```
E: The repository 'http://xxx(fqdn)/custom bionic/ Release' does not have a Release file.
```
I don't know anything about running a repo, so cannot help. Sorry.  The problem isn't on the client-side.

---

