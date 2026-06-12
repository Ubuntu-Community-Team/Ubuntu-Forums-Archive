---
title: "Ubuntu 18.04 server can not apt upgrade"
date: 2019-09-28
forum: Server Platforms
---

### Post by deepakdeshp on 2019-09-28
Hello,
I am running Ubuntu 18.04 server 64 bits. I cant upgrade it. Kindly advise.

```
  
sudo apt upgrade
W: Target CNF (stable/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:63E: Splitting of file /var/lib/apt/lists/ppa.launchpad.net_opencpn_opencpn_ubuntu_dists_bionic_InRelease failed as it doesn't contain all expected parts 0 1 0
E: The package lists or status file could not be parsed or opened.



```

---

### Post by Bashing-om on 2019-09-28
deepakdeshp; Hello -

The advisory clearly states to fix the /etc/apt/sources.list file.
Let's have a look at the subject sources,
post back:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

see here what it will take to make things right.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by deepakdeshp on 2019-09-29
```
cat -n /etc/apt/sources.list     1	# 
     2	
     3	# deb cdrom:[Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8)]/ xenial main restricted
     4	
     5	# deb cdrom:[Ubuntu-Server 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.8)]/ xenial main restricted
     6	
     7	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     8	# newer versions of the distribution.
     9	deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
    10	# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
    11	
    12	## Major bug fix updates produced after the final release of the
    13	## distribution.
    14	deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
    15	# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
    16	
    17	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    18	## team. Also, please note that software in universe WILL NOT receive any
    19	## review or updates from the Ubuntu security team.
    20	deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
    21	# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial universe
    22	deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
    23	# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
    24	
    25	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    26	## team, and may not be under a free licence. Please satisfy yourself as to 
    27	## your rights to use the software. Also, please note that software in 
    28	## multiverse WILL NOT receive any review or updates from the Ubuntu
    29	## security team.
    30	deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
    31	# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
    32	deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
    33	# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
    34	
    35	## N.B. software from this repository may not have been tested as
    36	## extensively as that contained in the main release, although it includes
    37	## newer versions of some applications which may provide useful features.
    38	## Also, please note that software in backports WILL NOT receive any review
    39	## or updates from the Ubuntu security team.
    40	deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
    41	# deb-src http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
    42	
    43	## Uncomment the following two lines to add software from Canonical's
    44	## 'partner' repository.
    45	## This software is not part of Ubuntu, but is offered by Canonical and the
    46	## respective vendors as a service to Ubuntu users.
    47	# deb http://archive.canonical.com/ubuntu xenial partner
    48	# deb-src http://archive.canonical.com/ubuntu xenial partner
    49	
    50	deb http://security.ubuntu.com/ubuntu bionic-security main restricted
    51	# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
    52	deb http://security.ubuntu.com/ubuntu bionic-security universe
    53	# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
    54	deb http://security.ubuntu.com/ubuntu bionic-security multiverse
    55	# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
    56	# deb http://nginx.org/packages/mainline/ubuntu bionic nginx # disabled on upgrade to bionic
    57	deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable
    58	# deb-src [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable
    59	deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable
    60	# deb-src [arch=amd64] https://download.docker.com/linux/ubuntubionic stable
    61	deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable
    62	# deb-src [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable
    63	deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable
    64	# deb-src [arch=amd64] https://download.docker.com/linux/ubuntubionic stable





```

```
tail -v -n +1 /etc/apt/sources.list.d/*==> /etc/apt/sources.list.d/jookies_python-jasmin.list <==
# this file was generated by packagecloud.io for
# the repository at https://packagecloud.io/jookies/python-jasmin


# deb https://packagecloud.io/jookies/python-jasmin/ubuntu/ bionic main # disabled on upgrade to bionic
# deb-src https://packagecloud.io/jookies/python-jasmin/ubuntu/ bionic main # disabled on upgrade to bionic


==> /etc/apt/sources.list.d/jookies_python-jasmin.list.distUpgrade <==
# this file was generated by packagecloud.io for
# the repository at https://packagecloud.io/jookies/python-jasmin


deb https://packagecloud.io/jookies/python-jasmin/ubuntu/ xenial main
deb-src https://packagecloud.io/jookies/python-jasmin/ubuntu/ xenial main


==> /etc/apt/sources.list.d/jookies_python-jasmin.list.save <==
# this file was generated by packagecloud.io for
# the repository at https://packagecloud.io/jookies/python-jasmin


# deb https://packagecloud.io/jookies/python-jasmin/ubuntu/ bionic main # disabled on upgrade to bionic
# deb-src https://packagecloud.io/jookies/python-jasmin/ubuntu/ bionic main # disabled on upgrade to bionic


==> /etc/apt/sources.list.d/linuxuprising-ubuntu-java-bionic.list <==
deb http://ppa.launchpad.net/linuxuprising/java/ubuntu bionic main
# deb-src http://ppa.launchpad.net/linuxuprising/java/ubuntu bionic main
# deb-src http://ppa.launchpad.net/linuxuprising/java/ubuntu bionic main


==> /etc/apt/sources.list.d/linuxuprising-ubuntu-java-bionic.list.save <==
deb http://ppa.launchpad.net/linuxuprising/java/ubuntu bionic main
# deb-src http://ppa.launchpad.net/linuxuprising/java/ubuntu bionic main
# deb-src http://ppa.launchpad.net/linuxuprising/java/ubuntu bionic main


==> /etc/apt/sources.list.d/ondrej-ubuntu-php-bionic.list <==
deb http://ppa.launchpad.net/ondrej/php/ubuntu bionic main
# deb-src http://ppa.launchpad.net/ondrej/php/ubuntu bionic main


==> /etc/apt/sources.list.d/ondrej-ubuntu-php-bionic.list.save <==
deb http://ppa.launchpad.net/ondrej/php/ubuntu bionic main
# deb-src http://ppa.launchpad.net/ondrej/php/ubuntu bionic main


==> /etc/apt/sources.list.d/opencpn-ubuntu-opencpn-bionic.list <==
deb http://ppa.launchpad.net/opencpn/opencpn/ubuntu bionic main
# deb-src http://ppa.launchpad.net/opencpn/opencpn/ubuntu bionic main
# deb-src http://ppa.launchpad.net/opencpn/opencpn/ubuntu bionic main


==> /etc/apt/sources.list.d/opencpn-ubuntu-opencpn-bionic.list.save <==
deb http://ppa.launchpad.net/opencpn/opencpn/ubuntu bionic main
# deb-src http://ppa.launchpad.net/opencpn/opencpn/ubuntu bionic main
# deb-src http://ppa.launchpad.net/opencpn/opencpn/ubuntu bionic main


==> /etc/apt/sources.list.d/opmantek-xenial.list <==
deb http://deb.debian.org/debian xenial main contrib non-free


==> /etc/apt/sources.list.d/opmantek-xenial.list.save <==
deb http://deb.debian.org/debian xenial main contrib non-free



```

---

### Post by deepakdeshp on 2019-09-29
```

sudo apt update
Get:1 https://download.docker.com/linux/ubuntu bionic InRelease [64.4 kB]      
Ign:2 https://download.docker.com/linux/ubuntu bionic/stable amd64 Packages    
Ign:3 https://download.docker.com/linux/ubuntu bionic/stable amd64 Contents (deb)
Ign:2 https://download.docker.com/linux/ubuntu bionic/stable amd64 Packages    
Get:3 https://download.docker.com/linux/ubuntu bionic/stable amd64 Contents (deb) [2,288 B]
Err:2 https://download.docker.com/linux/ubuntu bionic/stable amd64 Packages    
  Could not open file /var/lib/apt/lists/partial/download.docker.com_linux_ubuntu_dists_bionic_stable_binary-amd64_Packages.bz2 - open (13: Permission denied) [IP: 13.225.103.65 443]
Get:4 http://security.ubuntu.com/ubuntu bionic-security InRelease [250 B]      
Err:4 http://security.ubuntu.com/ubuntu bionic-security InRelease              
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Get:5 http://ppa.launchpad.net/linuxuprising/java/ubuntu bionic InRelease [250 B]
Err:5 http://ppa.launchpad.net/linuxuprising/java/ubuntu bionic InRelease      
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Get:6 http://ppa.launchpad.net/ondrej/php/ubuntu bionic InRelease [250 B]      
Err:6 http://ppa.launchpad.net/ondrej/php/ubuntu bionic InRelease              
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Get:7 http://ppa.launchpad.net/opencpn/opencpn/ubuntu bionic InRelease [250 B] 
Err:7 http://ppa.launchpad.net/opencpn/opencpn/ubuntu bionic InRelease         
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Err:8 http://us.archive.ubuntu.com/ubuntu bionic InRelease                     
  Could not connect to us.archive.ubuntu.com:80 (91.189.91.14), connection timed out
Err:9 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease             
  Unable to connect to us.archive.ubuntu.com:http:
Err:10 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease          
  Unable to connect to us.archive.ubuntu.com:http:
Err:11 http://deb.debian.org/debian xenial InRelease                           
  Could not connect to prod.debian.map.fastly.net:80 (151.101.196.204), connection timed out Could not connect to deb.debian.org:80 (128.31.0.62), connection timed out
Reading package lists... Error!                
W: Target CNF (stable/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:63
W: Target CNF (stable/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:63
W: Target Contents-deb (stable/Contents-all) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:63
W: Target Contents-deb (stable/Contents-amd64) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:63
W: Target Translations (stable/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:63
W: Target Translations (stable/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:63
W: Target Packages (stable/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:63
W: Target Packages (stable/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:63
W: Target CNF (stable/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:61
W: Target CNF (stable/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:61
W: Target Contents-deb (stable/Contents-all) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:61
W: Target Contents-deb (stable/Contents-amd64) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:61
W: Target Translations (stable/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:61
W: Target Translations (stable/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:61
W: Target Packages (stable/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:61
W: Target Packages (stable/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:61
W: Target CNF (stable/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:59
W: Target CNF (stable/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:59
W: Target Contents-deb (stable/Contents-all) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:59
W: Target Contents-deb (stable/Contents-amd64) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:59
W: Target Translations (stable/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:59
W: Target Translations (stable/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:59
W: Target Packages (stable/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:59
W: Target Packages (stable/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:59
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
E: The repository 'http://security.ubuntu.com/ubuntu bionic-security InRelease' is not signed.
E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
E: The repository 'http://ppa.launchpad.net/linuxuprising/java/ubuntu bionic InRelease' is no longer signed.
E: Failed to fetch http://ppa.launchpad.net/linuxuprising/java/ubuntu/dists/bionic/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: Failed to fetch http://ppa.launchpad.net/ondrej/php/ubuntu/dists/bionic/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: The repository 'http://ppa.launchpad.net/ondrej/php/ubuntu bionic InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/opencpn/opencpn/ubuntu/dists/bionic/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: The repository 'http://ppa.launchpad.net/opencpn/opencpn/ubuntu bionic InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (stable/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:59
W: Target Packages (stable/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:59
W: Target Translations (stable/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:59
W: Target Translations (stable/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:59
W: Target Contents-deb (stable/Contents-amd64) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:59
W: Target Contents-deb (stable/Contents-all) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:59
W: Target CNF (stable/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:59
W: Target CNF (stable/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:59
W: Target Packages (stable/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:61
W: Target Packages (stable/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:61
W: Target Translations (stable/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:61
W: Target Translations (stable/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:61
W: Target Contents-deb (stable/Contents-amd64) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:61
W: Target Contents-deb (stable/Contents-all) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:61
W: Target CNF (stable/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:61
W: Target CNF (stable/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:61
W: Target Packages (stable/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:63
W: Target Packages (stable/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:63
W: Target Translations (stable/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:63
W: Target Translations (stable/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:63
W: Target Contents-deb (stable/Contents-amd64) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:63
W: Target Contents-deb (stable/Contents-all) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:63
W: Target CNF (stable/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:63
W: Target CNF (stable/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:57 and /etc/apt/sources.list:63
E: Splitting of file /var/lib/apt/lists/ppa.launchpad.net_opencpn_opencpn_ubuntu_dists_bionic_InRelease failed as it doesn't contain all expected parts 0 1 0
E: The package lists or status file could not be parsed or opened.



```

---

### Post by Bashing-om on 2019-09-29
deepakdeshp; Welp:

The purpose of the /etc/apt/sources.list.d/ directory is to hold these 3rd party sources.

Now you have "download.docker.com" listed 3 times in the default ubuntu sources file - they do need to be removed and ONLY one instance moved to the 3rd party directory. (lines 57, 61, and 63 are duplicates)
In addition you have also in /etc/apt/sources.list.d/ several instances of the xenial repo --- NO NO ! Please remove them.

Once the sources files have been corrected what now results:
```

sudo apt update
sudo apt upgrade

```

see here if our work
[INDENT][INDENT]here is done 
[/INDENT][/INDENT]

---

### Post by deepakdeshp on 2019-10-04
Thank you , but No joy after clearing the 3 extra lines in /etc/apt/sources.list and after removing the xenial lines.

```
uma@localhost:/etc/apt/sources.list.d$ lsca-certificates.conf.dpkg-old
jookies_python-jasmin.list
jookies_python-jasmin.list.distUpgrade
jookies_python-jasmin.list.save
linuxuprising-ubuntu-java-bionic.list
linuxuprising-ubuntu-java-bionic.list.save
ondrej-ubuntu-php-bionic.list
ondrej-ubuntu-php-bionic.list.save
opencpn-ubuntu-opencpn-bionic.list
opencpn-ubuntu-opencpn-bionic.list.save
uma@localhost:/etc/apt/sources.list.d$ cat ../sources.list|grep -v ^#






deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted


deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted


deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe


deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse


deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse




deb http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable
uma@localhost:/etc/apt/sources.list.d$ sudo apt update
Get:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease [250 B]             
Err:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease                     
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Get:2 https://download.docker.com/linux/ubuntu bionic InRelease [64.4 kB]      
Get:3 http://security.ubuntu.com/ubuntu bionic-security InRelease [250 B]      
Err:3 http://security.ubuntu.com/ubuntu bionic-security InRelease              
  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
Ign:4 https://download.docker.com/linux/ubuntu bionic/stable amd64 Packages    
Ign:5 https://download.docker.com/linux/ubuntu bionic/stable amd64 Contents (deb)
Ign:4 https://download.docker.com/linux/ubuntu bionic/stable amd64 Packages    
Get:5 https://download.docker.com/linux/ubuntu bionic/stable amd64 Contents (deb) [2,288 B]
Err:4 https://download.docker.com/linux/ubuntu bionic/stable amd64 Packages    
  Could not open file /var/lib/apt/lists/partial/download.docker.com_linux_ubuntu_dists_bionic_stable_binary-amd64_Packages.bz2 - open (13: Permission denied) [IP: 13.224.161.117 443]
Err:6 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease             
  Could not connect to us.archive.ubuntu.com:80 (91.189.91.24), connection timed out [IP: 91.189.91.24 80]
Err:7 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease           
  Unable to connect to us.archive.ubuntu.com:http: [IP: 91.189.91.24 80]
Err:8 http://ppa.launchpad.net/linuxuprising/java/ubuntu bionic InRelease      
  Could not connect to ppa.launchpad.net:80 (91.189.95.83), connection timed out
Err:9 http://ppa.launchpad.net/ondrej/php/ubuntu bionic InRelease
  Unable to connect to ppa.launchpad.net:http:
Err:10 http://ppa.launchpad.net/opencpn/opencpn/ubuntu bionic InRelease
  Unable to connect to ppa.launchpad.net:http:
Reading package lists... Error!
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/bionic/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: The repository 'http://us.archive.ubuntu.com/ubuntu bionic InRelease' is no longer signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://security.ubuntu.com/ubuntu/dists/bionic-security/InRelease  Clearsigned file isn't valid, got 'NOSPLIT' (does the network require authentication?)
E: The repository 'http://security.ubuntu.com/ubuntu bionic-security InRelease' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Splitting of file /var/lib/apt/lists/ppa.launchpad.net_opencpn_opencpn_ubuntu_dists_bionic_InRelease failed as it doesn't contain all expected parts 0 1 0
E: The package lists or status file could not be parsed or opened.



```

---

### Post by Bashing-om on 2019-10-04
deepakdeshp; Hey !

Now is there a networking issue ?

what results:
```

ping -c3 ubuntu.com
ping -c3 91.189.91.24

```
One step at a time

[INDENT]can we talk to the server
[/INDENT]

---

### Post by deepakdeshp on 2019-10-07
> **Bashing-om said:**
> deepakdeshp; Hey !

Now is there a networking issue ?

what results:
```

ping -c3 ubuntu.com
ping -c3 91.189.91.24

```
One step at a time
[INDENT]can we talk to the server
[/INDENT]

The server is virtual machine and it is on the network.
```
 ping -c3 ubuntu.comPING ubuntu.com (91.189.90.58) 56(84) bytes of data.
64 bytes from www-ubuntu-com.avocado.canonical.com (91.189.90.58): icmp_seq=1 ttl=128 time=224 ms
64 bytes from www-ubuntu-com.avocado.canonical.com (91.189.90.58): icmp_seq=2 ttl=128 time=207 ms
64 bytes from www-ubuntu-com.avocado.canonical.com (91.189.90.58): icmp_seq=3 ttl=128 time=164 ms


--- ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 164.037/198.448/224.016/25.272 ms



```

---

### Post by deepakdeshp on 2019-10-08
Thank you Bashing-OM
The problem is solved. I was trying to install Koha, the open source library tool. In the process I was prompted to run ```
sudo apt --fix-missing
```. Running this command solved the problem.:D Now I can update and upgrade too.

---

### Post by Bashing-om on 2019-10-08
deepakdeshp; Great !

Pleased you got to the bottom of things :P

[INDENT]keep on keep'n on
[/INDENT]

---

