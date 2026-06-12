---
title: "Having issues on upgrading 18.04 to latest version"
date: 2021-06-24
forum: Server Platforms
---

### Post by kustomjs on 2021-06-24
Hello People
its been long time since I posted on here but I am having issues upgrading my server from 18.04 lts to latest one and when I do update I get this error:

```
tim@mail:~$ sudo apt-get update
Ign:1 http://old-releases.ubuntu.com/ubuntu bionic InRelease
Ign:2 http://old-releases.ubuntu.com/ubuntu bionic-updates InRelease
Ign:3 http://old-releases.ubuntu.com/ubuntu bionic-backports InRelease
Ign:4 http://old-releases.ubuntu.com/ubuntu bionic-security InRelease
Err:5 http://old-releases.ubuntu.com/ubuntu bionic Release
  404  Not Found [IP: 91.189.91.123 80]
Err:6 http://old-releases.ubuntu.com/ubuntu bionic-updates Release
  404  Not Found [IP: 91.189.91.123 80]
Err:7 http://old-releases.ubuntu.com/ubuntu bionic-backports Release
  404  Not Found [IP: 91.189.91.123 80]
Err:8 http://old-releases.ubuntu.com/ubuntu bionic-security Release
  404  Not Found [IP: 91.189.91.123 80]
Reading package lists... Done
E: The repository 'http://old-releases.ubuntu.com/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://old-releases.ubuntu.com/ubuntu bionic-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://old-releases.ubuntu.com/ubuntu bionic-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://old-releases.ubuntu.com/ubuntu bionic-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

then when I try to do do-release I get this
```
tim@mail:~$ sudo do-release-upgrade
Checking for a new Ubuntu release
Err Upgrade tool signature
  404  Not Found [IP: 91.189.88.152 80]
Err Upgrade tool
  404  Not Found [IP: 91.189.88.152 80]
Fetched 0 B in 0s (0 B/s)
WARNING:root:file 'focal.tar.gz.gpg' missing
Failed to fetch
Fetching the upgrade failed. There may be a network problem.

```

Any Ideas how to fix this?

---

### Post by deadflowr on 2021-06-24
18.04 is  still supported so the archive still exist where they are and have never been moved to the old-release archives.
revert your sources.

---

### Post by kustomjs on 2021-06-24
deadflowr
how do I revert the sources back?

---

### Post by deadflowr on 2021-06-24
You can either use a repo generator like this [https://repogen.simplylinux.ch/]("https://repogen.simplylinux.ch/")
And then replace the current sources.list file with the one you generated.

Or you can copy over a generic sources.list file that comes with the apt docs in the /usr/share/doc/apt/examples folder.
But this one would require re-adding any extras sources like those from the universe and multiverse repositories.
For that run
```
sudo cp /usr/share/doc/apt/examples/sources.list /etc/sources.list
sudo add-apt-repository universe multiverse
sudo apt update ####  NOTE: this command should actually run as part of the add-apt-repository command, so it might not be necessary
sudo apt full-upgrade
```

---

### Post by irv on 2021-06-24
Just for the heck of it, do a 
```
cat /etc/network/interfaces
```
and then copy and paste the output. It should look something like this if you have a static IP on your server.
>  # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

source /etc/network/interfaces.d/*

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto enp4s0
iface enp4s0 inet static
	address 192.168.1.105
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	gateway 192.168.1.1
        dns-nameserver 8.8.8.8 8.8.4.4
 I just wanted to check your dns-nameserver settings to make sure it is okay.

---

### Post by kustomjs on 2021-06-24
irv
that is outdated information its been replaced by netplan
```

tim@mail:~$ cat /etc/netplan/*.yaml
# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    version: 2
    renderer: networkd
    ethernets:
        enp2s0:
            dhcp4: true 
```


deadflowr 
I tried that rep generator still getting error message after doing apt-update:```
 

tim@mail:~$ sudo apt-get update
Ign:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease
Ign:2 http://us.archive.ubuntu.com/ubuntu bionic-security InRelease
Ign:3 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease
Ign:4 http://us.archive.ubuntu.com/ubuntu bionic-proposed InRelease
Ign:5 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease
Err:6 http://us.archive.ubuntu.com/ubuntu bionic Release
  404  Not Found [IP: 91.189.91.38 80]
Err:7 http://us.archive.ubuntu.com/ubuntu bionic-security Release
  404  Not Found [IP: 91.189.91.38 80]
Err:8 http://us.archive.ubuntu.com/ubuntu bionic-updates Release
  404  Not Found [IP: 91.189.91.38 80]
Err:9 http://us.archive.ubuntu.com/ubuntu bionic-proposed Release
  404  Not Found [IP: 91.189.91.39 80]
Err:10 http://us.archive.ubuntu.com/ubuntu bionic-backports Release
  404  Not Found [IP: 91.189.91.38 80]
Reading package lists... Done
E: The repository 'http://us.archive.ubuntu.com/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu bionic-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu bionic-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu bionic-proposed Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu bionic-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

I can ping to 1.1.1.1 and to  91.189.91.39

---

### Post by irv on 2021-06-24
I am using 18.04 but I just upgraded from 16.04.
Can you ping the domain name, try
```
ping www.google.com
```

---

### Post by MAFoElffen on 2021-06-24
This is where I posted the default sources.list's for 16.04 and 18.04: [https://ubuntuforums.org/showthread.php?t=2463934&p=14044977#post14044977](https://ubuntuforums.org/showthread.php?t=2463934&p=14044977#post14044977)
The second is for 18.04. All you would have to do is to copy and paste it into a text document and save as a file called sources.list... then copy (using sudo) over the existing /etc/apt/sources.list...

Or use this to change your exisiting incorrect sources list:
```

# Make a copy of the original
sudo cp /etc/apt/sources.list ~/sources.list.old_backup

# Change all instances of "old-releases" into "us.archive" in the sources list file 
sudo sed -i 's/old\-releases/us\.archive/g' /etc/apt/sources.list

# Check your work and see if it is pointing to the correct repo..
sudo apt-get update

```

**EDIT:** A sources.list doesn't get to the "old-releases" repo's by accidient. I suspect you used something someone (maybe me) wrote for a specific user, that had a specific problem, with what they had going on, and needed something outside the box, to get back on track to what is recommened. That recent recommendation by me, was for someone that had something specific going on, that was not in the main repo's by about 4-1/2 years past. But my instructions to "that specific user" included instructions on how to get back to the main repo's. Please ensure you undederstand that something applies to you, your system, and your circumstances, before trying things. Just a disclaimer... LOL

...Or referring to my signature line in another forum: [SIZE=3]*"Don't worry! I saw this work in a cartoon once..."*[/SIZE]

---

### Post by kustomjs on 2021-06-24
I can ping to google

---

### Post by MAFoElffen on 2021-06-24
So please post your /etc/apt/sources.list within code tags...

---

### Post by kustomjs on 2021-06-25
Here is the source code I have under sources.list

```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner


deb http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
```

thats what I am using

when you do sudo apt-get update I get this:

```

tim@mail:~$ sudo apt-get update
Ign:1 http://security.ubuntu.com/ubuntu bionic-security InRelease
Ign:2 http://us.archive.ubuntu.com/ubuntu bionic InRelease
Err:3 http://security.ubuntu.com/ubuntu bionic-security Release
  404  Not Found [IP: 91.189.91.38 80]
Ign:4 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease
Ign:5 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease
Err:6 http://us.archive.ubuntu.com/ubuntu bionic Release
  404  Not Found [IP: 91.189.91.39 80]
Err:7 http://us.archive.ubuntu.com/ubuntu bionic-updates Release
  404  Not Found [IP: 91.189.91.38 80]
Err:8 http://us.archive.ubuntu.com/ubuntu bionic-backports Release
  404  Not Found [IP: 91.189.91.38 80]
Reading package lists... Done
E: The repository 'http://security.ubuntu.com/ubuntu bionic-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu bionic-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu bionic-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details. 
```

when trying do the update release
```

tim@mail:~$ sudo do-release-upgrade
Checking for a new Ubuntu release
Err Upgrade tool signature
  404  Not Found [IP: 91.189.88.142 80]
Err Upgrade tool
  404  Not Found [IP: 91.189.88.142 80]
Fetched 0 B in 0s (0 B/s)
WARNING:root:file 'focal.tar.gz.gpg' missing
Failed to fetch
Fetching the upgrade failed. There may be a network problem.
```

---

### Post by LHammonds on 2021-06-25
I never do in-place upgrades so the one 18.04 server I have is how it was installed.  You seem to have something else going on besides just messing up your sources.list

Here is my sources.list:

```

#

# deb cdrom:[Ubuntu-Server 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic main restricted

# deb cdrom:[Ubuntu-Server 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner

deb http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse

```

Here is the result of an apt update:

```

Get:1 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]
Hit:2 http://us.archive.ubuntu.com/ubuntu bionic InRelease
Get:3 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [2,127 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [1,309 kB]
Hit:7 http://ppa.launchpad.net/ondrej/php/ubuntu bionic InRelease
Get:8 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [1,738 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [1,568 kB]
Fetched 6,994 kB in 3s (2,255 kB/s)
Reading package lists... Done
Building dependency tree
Reading state information... Done
All packages are up to date.

```

Here are some DNS resolving tests:
```

ping -c 1 us.archive.ubuntu.com
PING us.archive.ubuntu.com (91.189.91.39) 56(84) bytes of data.
64 bytes from kazooie.canonical.com (91.189.91.39): icmp_seq=1 ttl=48 time=47.4 ms

--- us.archive.ubuntu.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 47.426/47.426/47.426/0.000 ms

```

```

ping -c 1 security.ubuntu.com
PING security.ubuntu.com (91.189.91.38) 56(84) bytes of data.
64 bytes from banjo.canonical.com (91.189.91.38): icmp_seq=1 ttl=48 time=47.2 ms

--- security.ubuntu.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 47.279/47.279/47.279/0.000 ms

```

```
lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.5 LTS
Release:        18.04
Codename:       bionic
```

```

uname -a
Linux ubuntu18 4.15.0-147-generic #151-Ubuntu SMP Fri Jun 18 19:21:19 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux

```

LHammonds

---

### Post by MAFoElffen on 2021-06-25
Those ARE specifically different errors than your previous posts..  

Now can you post the results of 
```
dig +noall +answer us.archive.ubuntu.com
dig +trace us.archive.ubuntu.com
```
That is to where your machine says it's trying to get to now...

---

### Post by kustomjs on 2021-06-25
```

tim@mail:~$ dig +noall +answer us.archive.ubuntu.com
us.archive.ubuntu.com.  47      IN      A       91.189.91.38
us.archive.ubuntu.com.  47      IN      A       91.189.91.39
tim@mail:~$ dig +trace us.archive.ubuntu.com

; <<>> DiG 9.11.3-1ubuntu1.14-Ubuntu <<>> +trace us.archive.ubuntu.com
;; global options: +cmd
;; Received 51 bytes from 127.0.0.53#53(127.0.0.53) in 0 ms


```

```

tim@mail:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.5 LTS
Release:        18.04
Codename:       bionic
tim@mail:~$ ping -c 1 is.archive.ubuntu.com
PING mirrors.opensource.is (176.57.227.242) 56(84) bytes of data.
64 bytes from mirrors.opensource.is (176.57.227.242): icmp_seq=1 ttl=49 time=116 ms

--- mirrors.opensource.is ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 116.670/116.670/116.670/0.000 ms
tim@mail:~$ ping -c 1 security.ubuntu.com
PING security.ubuntu.com (91.189.91.39) 56(84) bytes of data.
64 bytes from kazooie.canonical.com (91.189.91.39): icmp_seq=1 ttl=53 time=18.5 ms

--- security.ubuntu.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 18.515/18.515/18.515/0.000 ms
tim@mail:~$

```

it seems like the code for source is broke and not working correctly and it doesnt matter how many times I reboot the machine it still does that error update issue

---

### Post by deadflowr on 2021-06-25
Are you or have you ever setup a proxy or have configured some other networking setup that has since changed?

---

### Post by MAFoElffen on 2021-06-26
I agree with deadflower...

Look at your DNS trace... It was 3 lines total. Even if you were next door to the repo, you should have more lines. I do not even see the first DNS server.

For example look at my output for the same:
```
mafoelffen@Ubuntu-20041-G2:~$ dig +trace us.archive.ubuntu.com

; <<>> DiG 9.16.1-Ubuntu <<>> +trace us.archive.ubuntu.com
;; global options: +cmd
.            461550    IN    NS    e.root-servers.net.
.            461550    IN    NS    f.root-servers.net.
.            461550    IN    NS    g.root-servers.net.
.            461550    IN    NS    h.root-servers.net.
.            461550    IN    NS    i.root-servers.net.
.            461550    IN    NS    a.root-servers.net.
.            461550    IN    NS    j.root-servers.net.
.            461550    IN    NS    k.root-servers.net.
.            461550    IN    NS    l.root-servers.net.
.            461550    IN    NS    m.root-servers.net.
.            461550    IN    NS    b.root-servers.net.
.            461550    IN    NS    c.root-servers.net.
.            461550    IN    NS    d.root-servers.net.
;; Received 262 bytes from 127.0.0.53#53(127.0.0.53) in 855 ms


com.            172800    IN    NS    g.gtld-servers.net.
com.            172800    IN    NS    d.gtld-servers.net.
com.            172800    IN    NS    a.gtld-servers.net.
com.            172800    IN    NS    j.gtld-servers.net.
com.            172800    IN    NS    c.gtld-servers.net.
com.            172800    IN    NS    l.gtld-servers.net.
com.            172800    IN    NS    e.gtld-servers.net.
com.            172800    IN    NS    b.gtld-servers.net.
com.            172800    IN    NS    h.gtld-servers.net.
com.            172800    IN    NS    f.gtld-servers.net.
com.            172800    IN    NS    m.gtld-servers.net.
com.            172800    IN    NS    i.gtld-servers.net.
com.            172800    IN    NS    k.gtld-servers.net.
com.            86400    IN    DS    30909 8 2 E2D3C916F6DEEAC73294E8268FB5885044A833FC5459588F4A9184CF C41A5766
com.            86400    IN    RRSIG    DS 8 1 86400 20210709050000 20210626040000 14631 . qvm2JTG2IOHHvPHU/3ihftilxK6l/w0DJUO+2RW2AYpuhJEm+goUz6v/ Cv4+hMn0qJhZoPg3HCiGlxvtMSEpc3dSf2GRV1T1WKs80U+IE/ylTiNw RtJ6e8k7D3m8njP0q5ZnfyEyyUM3zgFaH/ZhkKWsjcpUKCiG396lIfGO 6LEMrtDq+Jo3WWCdDlbnapsDd2IEmKsuQKzd0VzDA5q7HxqiIsGKxE/m cNIFrUsR89oxBbU5DinWXwEo3/5xvGS7JX9lDQYt4Lv/oo5SYa7uJlNQ C8AlXlTBUZcKxRQx4aoKyDtNyyUahbqkzG2x6qjLobgKRBkj/cllawon u/fqCQ==
;; Received 1212 bytes from 192.36.148.17#53(i.root-servers.net) in 35 ms


ubuntu.com.        172800    IN    NS    ns1.canonical.com.
ubuntu.com.        172800    IN    NS    ns2.canonical.com.
ubuntu.com.        172800    IN    NS    ns3.canonical.com.
CK0POJMG874LJREF7EFN8430QVIT8BSM.com. 86400 IN NSEC3 1 1 0 - CK0Q1GIN43N1ARRC9OSM6QPQR81H5M9A NS SOA RRSIG DNSKEY NSEC3PARAM
CK0POJMG874LJREF7EFN8430QVIT8BSM.com. 86400 IN RRSIG NSEC3 8 2 86400 20210703042346 20210626031346 54714 com. fpRZKBFjStpVmT0pXcXOuti8qzhE0DfHJhriwBJn6Uj/rYfpI788/Jj6 K55Qs394YruLilWiMbHWRu7ubsSTwgqBD76CVuyqsq/jVUZePqBeU/5r nN68gFAjpfBZnG5UkxH9CzTHmercrzWD4rAp+5ZcpxkjjcT6x1VxbnYO brhgCDWKEipgGtByalV7NfRjyTuJrsrO8j1loeBOJOXnSQ==
894IO8AM9NDQ8VM84GPASGU0QDHFLFS1.com. 86400 IN NSEC3 1 1 0 - 894J5FN26LROBLRR48NQHCUNICNAGJQ6 NS DS RRSIG
894IO8AM9NDQ8VM84GPASGU0QDHFLFS1.com. 86400 IN RRSIG NSEC3 8 2 86400 20210703052427 20210626041427 54714 com. EGyusmxTdGs1P/nJyoRQHze8SnJPDbBYEGu6ZdProYBp/vzCNs0/Upek +XhGndx1tcEVLdMyGEqJ1PEJD7P2KW/nSbta8Knmu+Vlged6niJ3d9KX rv6MzCaH9+Mqtsz5JnlINT+Kr/N40CcMwwafWUVgWCmvx8/STK90dfAT x8HkvVTcB3hhHHpoMJwtnrldn99O0bnteqvKNeTjXBWYYQ==
;; Received 711 bytes from 192.42.93.30#53(g.gtld-servers.net) in 31 ms


us.archive.ubuntu.com.    60    IN    A    91.189.91.39
us.archive.ubuntu.com.    60    IN    A    91.189.91.38
ubuntu.com.        600    IN    NS    ns1.canonical.com.
ubuntu.com.        600    IN    NS    ns3.canonical.com.
ubuntu.com.        600    IN    NS    ns2.canonical.com.
;; Received 194 bytes from 91.189.95.3#53(ns2.canonical.com) in 155 ms

```
I see yourtrace just dropping off dead [COLOR=#000000][FONT=&amp]with no nameserver records.[/FONT][/COLOR]

---

### Post by kustomjs on 2021-06-26
There was never no proxy&#8217;s or any else network change since this was installed at all. So it&#8217;s a dns issue? If it&#8217;s dns issue then how I go about fixing it since it&#8217;s under netplan network configuration

---

### Post by MAFoElffen on 2021-06-26
Please post /etc/netplan/01-*.yaml and /etc/network/interfaces...

Then post the reslults of
```
ifconfig -a
netplan try
networkctl list
networkctl status
# If the following command's output is longer than 1 page, there will be a white bar at the bottom, saying Lines (x-xx)
# If so, press the spacebar until it gets to the end, then press "q" to quit.
resolvectl status
```
In your my last post, I said that 127.0.0.53 is where you were dropping off your DNS (consistency)... There is something (new) that makes that specific IP Address unique and special. Just like 127.0.0.1 is your internal home / link local address, in systemd.resolved, 127.0.0.53 is the local address where the systemd-resolved process listens for DNS queries, which it then forwards on. (Which yours is not doing that consistently!)

It does the DNS process dynamically, so could be that there is a file (or symlink) that got whacked, misconfigured, or... If you are getting your network settings via DCHP, then there might be a problem in the DHCP server in how it is handing out it's leases.

---

### Post by kustomjs on 2021-06-27
```

enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 70.33.168.xxx  netmask 255.255.255.240  broadcast 70.33.xxx.xxx
        inet6 fe80::d63d:7eff:fee2:7c65  prefixlen 64  scopeid 0x20<link>
        ether d4:3d:7e:e2:7c:xx  txqueuelen 1000  (Ethernet)
        RX packets 38840380  bytes 2420519911 (2.4 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1013865  bytes 187634619 (187.6 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 3417140  bytes 2228544225 (2.2 GB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 3417140  bytes 2228544225 (2.2 GB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


ERROR: cannot create file run/systemd/network/10-netplan-enp2s0: Failed to create file “/run/systemd/network/10-netplan-enp2s0.network.FRVF50”: Permission denied

An error occurred: the configuration could not be generated

Reverting.
Something really bad happened while reverting config: [Errno 13] Permission denied: '10-netplan-enp2s0.network'
You should verify the netplan YAML in /etc/netplan and probably run 'netplan apply' again.
tim@mail:~$ sudo netplan try
Warning: Stopping systemd-networkd.service, but it can still be activated by:
  systemd-networkd.socket
Do you want to keep these settings?


Press ENTER before the timeout to accept the new configuration


Changes will revert in 114 seconds

tim@mail:~$ networkctl list
IDX LINK             TYPE               OPERATIONAL SETUP
  1 lo               loopback           carrier     unmanaged
  2 enp2s0           ether              routable    configured


&#9679;        State: routable
       Address: 70.33.xxx.xxx on enp2s0
                fe80::d63d:7eff:fxx2:7cxx on enp2s0
       Gateway: 70.33.xxx.xxx on enp2s0
           DNS: 70.33.168.193
                1.1.1.1
           NTP: 129.6.15.28

tim@mail:~$ resolvectl status
resolvectl: command not found
tim@mail:~$

```

---

### Post by MAFoElffen on 2021-06-27
Can you go back your post #19 and add comments behind an "#" character to add the specific command proceding each output (please) that will help greatly on identifying and getting through that... Because I really want to see what caused this error:
```
[COLOR=#ff0000]ERROR: cannot create file run/systemd/network/10-netplan-enp2s0: Failed to create file &#8220;/run/systemd/network/10-netplan-enp2s0.network.FRVF50&#8221;: Permission denied 
An error occurred: the configuration could not be generated[/COLOR]
```

*** Did you inherit this machine from someone else? Was it always running there or was it running somewhere else? Meaning... Is the Network 70.33.168.xxx/7 yours? ...and is 70.33.168.193 your local network's DNS, where you have control or your ISP's? *** If you are worried about who see's those answers, you can PM on those.
```
im@mail:~$ networkctl list
IDX LINK             TYPE               OPERATIONAL SETUP
  1 lo               loopback           carrier     unmanaged
  [COLOR=#ff0000]2 enp2s0           ether              routable    configured[/COLOR]

```
Is this on you network and 
```
&#9679;        State: routable
       Address: 70.33.xxx.xxx on enp2s0
                fe80::d63d:7eff:fxx2:7cxx on enp2s0
       Gateway: 70.33.xxx.xxx on enp2s0
           DNS:[COLOR=#ff0000] 70.33.168.193[/COLOR]
                1.1.1.1
           NTP: 129.6.15.28

```
On the command not found... on resolvectl, please do 
```
journalctl -u systemd-resolve -f
systemd-resolve status
```
My bad on that, I forgot that 18.04 was still in transition with systemd. "systemd-resolve" was renamed to "resolvectl" in "systemd" version 239, but Bionic was still "systemd" version 237.

It looks like some things were manually configured, which may not exist and/or be the same in the current environment(?) Is this true?

Because I see a managed device for Ethernet and a managed router table, which I haven't seen the config files for either yet... If you are worried about "the world" seeing it, then just PM me.
and to dump the info for the router table:
```

route -n
ip route

```

---

### Post by kustomjs on 2021-06-27
```
tim@mail:~$ -bash: syntax error near unexpected token `newline'
> tim@mail:~$         ether d4:3d:7e:e2:7c:xx  txqueuelen 1000  (Ethernet)
> -bash: syntax error near unexpected token `('
-bash: syntax error near unexpected token `('
tim@mail:~$ tim@mail:~$         RX packets 38840380  bytes 2420519911 (2.4 GB)
-bash: syntax error near unexpected token `('
tim@mail:~$ -bash: syntax error near unexpected token `('
> tim@mail:~$         RX errors 0  dropped 0  overruns 0  frame 0
> RX: command not found
> tim@mail:~$         TX packets 1013865  bytes 187634619 (187.6 MB)
> -bash: syntax error near unexpected token `('
-bash: syntax error near unexpected token `('
tim@mail:~$ tim@mail:~$         TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
TX: command not found
tim@mail:~$
tim@mail:~$
tim@mail:~$ ERROR: cannot create file run/systemd/network/10-netplan-enp2s0: Failed to create file &#8220;/run/systemd/network/10-netplan-enp2s0.network.FRVF50&#8221;: Permission denied
ERROR:: command not found
tim@mail:~$
tim@mail:~$ An error occurred: the configuration could not be generated
An: command not found
tim@mail:~$
tim@mail:~$ Reverting.
Reverting.: command not found
tim@mail:~$ Something really bad happened while reverting config: [Errno 13] Permission denied: '10-netplan-enp2s0.network'
Something: command not found
tim@mail:~$ You should verify the netplan YAML in /etc/netplan and probably run 'netplan apply' again.
You: command not found
tim@mail:~$ tim@mail:~$ sudo netplan try
tim@mail:~$: command not found
tim@mail:~$ Warning: Stopping systemd-networkd.service, but it can still be activated by:
Warning:: command not found
tim@mail:~$   systemd-networkd.socket
systemd-networkd.socket: command not found
tim@mail:~$ Do you want to keep these settings?
Do: command not found
tim@mail:~$
tim@mail:~$
tim@mail:~$ Press ENTER before the timeout to accept the new configuration
Press: command not found
tim@mail:~$
tim@mail:~$
tim@mail:~$ Changes will revert in 114 seconds
Changes: command not found
tim@mail:~$
tim@mail:~$ tim@mail:~$ networkctl list
tim@mail:~$: command not found
tim@mail:~$ IDX LINK             TYPE               OPERATIONAL SETUP
IDX: command not found
tim@mail:~$   1 lo               loopback           carrier     unmanaged
1: command not found
tim@mail:~$   2 enp2s0           ether              routable    configured
2: command not found
tim@mail:~$
tim@mail:~$
tim@mail:~$ &#9679;        State: routable
&#9679;: command not found
tim@mail:~$        Address: 70.33.xxx.xxx on enp2s0
Address:: command not found
tim@mail:~$                 fe80::d63d:7eff:fxx2:7cxx on enp2s0
fe80::d63d:7eff:fxx2:7cxx: command not found
tim@mail:~$        Gateway: 70.33.xxx.xxx on enp2s0
Gateway:: command not found
tim@mail:~$            DNS: 70.33.168.193
DNS:: command not found
tim@mail:~$                 1.1.1.1
1.1.1.1: command not found
tim@mail:~$            NTP: 129.6.15.28
NTP:: command not found
tim@mail:~$
tim@mail:~$ tim@mail:~$ resolvectl status
tim@mail:~$: command not found
tim@mail:~$ resolvectl: command not found
resolvectl:: command not found
tim@mail:~$ tim@mail:~$
tim@mail:~$: command not found
tim@mail:~$ 
```
```
: No such file or directory
tim@mail:~$: command not found
tim@mail:~$ TX: command not found
TX:: command not found
tim@mail:~$ tim@mail:~$
tim@mail:~$: command not found
tim@mail:~$ tim@mail:~$ lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
-bash: UP,LOOPBACK,RUNNING: No such file or directory
tim@mail:~$ -bash: UP,LOOPBACK,RUNNING: No such file or directory
-bash:: command not found
tim@mail:~$ tim@mail:~$         inet 127.0.0.1  netmask 255.0.0.0
tim@mail:~$: command not found
tim@mail:~$
tim@mail:~$ Command 'inet' not found, did you mean:
Command: command not found
tim@mail:~$
tim@mail:~$   command 'inetd' from deb openbsd-inetd

Command 'inetd' not found, but can be installed with:

sudo apt install openbsd-inetd

tim@mail:~$   command 'dnet' from deb golang-libnetwork

Command 'dnet' not found, but can be installed with:

sudo apt install golang-libnetwork

tim@mail:~$   command 'net' from deb samba-common-bin

Command 'net' not found, but can be installed with:

sudo apt install samba-common-bin

tim@mail:~$   command 'init' from deb systemd-sysv
Too many arguments.
tim@mail:~$
tim@mail:~$ Try: sudo apt install <deb name>
-bash: syntax error near unexpected token `newline'
tim@mail:~$
tim@mail:~$ tim@mail:~$         inet6 ::1  prefixlen 128  scopeid 0x10<host>
-bash: syntax error near unexpected token `newline'
tim@mail:~$ -bash: syntax error near unexpected token `newline'
> tim@mail:~$         loop  txqueuelen 1000  (Local Loopback)
> -bash: syntax error near unexpected token `('
-bash: syntax error near unexpected token `('
tim@mail:~$ tim@mail:~$         RX packets 3417140  bytes 2228544225 (2.2 GB)
-bash: syntax error near unexpected token `('
tim@mail:~$ -bash: syntax error near unexpected token `('
> tim@mail:~$         RX errors 0  dropped 0  overruns 0  frame 0
> RX: command not found
> tim@mail:~$         TX packets 3417140  bytes 2228544225 (2.2 GB)
> -bash: syntax error near unexpected token `('
-bash: syntax error near unexpected token `('
tim@mail:~$ tim@mail:~$         TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
tim@mail:~$: command not found
tim@mail:~$ TX: command not found
TX:: command not found
tim@mail:~$ tim@mail:~$
tim@mail:~$: command not found
tim@mail:~$ tim@mail:~$
tim@mail:~$: command not found
tim@mail:~$ tim@mail:~$ ERROR: cannot create file run/systemd/network/10-netplan-enp2s0: Failed to create file &#8220;/run/systemd/network/10-netplan-enp2s0.network.FRVF50&#8221;: Permission denied
tim@mail:~$: command not found
tim@mail:~$ ERROR:: command not found
ERROR::: command not found
tim@mail:~$ tim@mail:~$
tim@mail:~$: command not found
tim@mail:~$ tim@mail:~$ An error occurred: the configuration could not be generated
tim@mail:~$: command not found
tim@mail:~$ An: command not found
An:: command not found
tim@mail:~$ tim@mail:~$
tim@mail:~$: command not found
tim@mail:~$ tim@mail:~$ Reverting.
tim@mail:~$: command not found
tim@mail:~$ Reverting.: command not found
Reverting.:: command not found
tim@mail:~$ tim@mail:~$ Something really bad happened while reverting config: [Errno 13] Permission denied: '10-netplan-enp2s0.network'
tim@mail:~$: command not found
tim@mail:~$ Something: command not found
Something:: command not found
tim@mail:~$ tim@mail:~$ You should verify the netplan YAML in /etc/netplan and probably run 'netplan apply' again.
tim@mail:~$: command not found
tim@mail:~$ You: command not found
You:: command not found
tim@mail:~$ tim@mail:~$ tim@mail:~$ sudo netplan try
tim@mail:~$: command not found
tim@mail:~$ tim@mail:~$: command not found
tim@mail:~$:: command not found
tim@mail:~$ tim@mail:~$ Warning: Stopping systemd-networkd.service, but it can still be activated by:
tim@mail:~$: command not found
tim@mail:~$ Warning:: command not found
Warning::: command not found
tim@mail:~$ tim@mail:~$   systemd-networkd.socket
tim@mail:~$: command not found
tim@mail:~$ systemd-networkd.socket: command not found
systemd-networkd.socket:: command not found
tim@mail:~$ tim@mail:~$ Do you want to keep these settings?
tim@mail:~$: command not found
tim@mail:~$ Do: command not found
Do:: command not found
tim@mail:~$ tim@mail:~$
tim@mail:~$: command not found
tim@mail:~$ tim@mail:~$
tim@mail:~$: command not found
tim@mail:~$ tim@mail:~$ Press ENTER before the timeout to accept the new configuration
tim@mail:~$: command not found
tim@mail:~$ Press: command not found
Press:: command not found
tim@mail:~$ tim@mail:~$
tim@mail:~$: command not found
tim@mail:~$ tim@mail:~$
tim@mail:~$: command not found
tim@mail:~$ tim@mail:~$ Changes will revert in 114 seconds
tim@mail:~$: command not found
tim@mail:~$ Changes: command not found
Changes:: command not found
tim@mail:~$ tim@mail:~$
tim@mail:~$: command not found
tim@mail:~$ tim@mail:~$ tim@mail:~$ networkctl list
tim@mail:~$: command not found
tim@mail:~$ tim@mail:~$: command not found
tim@mail:~$:: command not found
tim@mail:~$ tim@mail:~$ IDX LINK             TYPE               OPERATIONAL SETUP
tim@mail:~$: command not found
tim@mail:~$ IDX: command not found
IDX:: command not found
tim@mail:~$ tim@mail:~$   1 lo               loopback           carrier     unmanaged
tim@mail:~$: command not found
tim@mail:~$ 1: command not found
1:: command not found
tim@mail:~$ tim@mail:~$   2 enp2s0           ether              routable    configured
tim@mail:~$: command not found
tim@mail:~$ 2: command not found
2:: command not found
tim@mail:~$ tim@mail:~$
tim@mail:~$: command not found
tim@mail:~$ tim@mail:~$
tim@mail:~$: command not found
tim@mail:~$ tim@mail:~$ &#9679;        State: routable
tim@mail:~$: command not found
tim@mail:~$ &#9679;: command not found
&#9679;:: command not found
tim@mail:~$ tim@mail:~$        Address: 70.33.xxx.xxx on enp2s0
tim@mail:~$: command not found
tim@mail:~$ Address:: command not found
Address::: command not found
tim@mail:~$ tim@mail:~$                 fe80::d63d:7eff:fxx2:7cxx on enp2s0
tim@mail:~$: command not found
tim@mail:~$ fe80::d63d:7eff:fxx2:7cxx: command not found
fe80::d63d:7eff:fxx2:7cxx:: command not found
tim@mail:~$ tim@mail:~$        Gateway: 70.33.xxx.xxx on enp2s0
tim@mail:~$: command not found
tim@mail:~$ Gateway:: command not found
Gateway::: command not found
tim@mail:~$ tim@mail:~$            DNS: 70.33.168.193
tim@mail:~$: command not found
tim@mail:~$ DNS:: command not found
DNS::: command not found
tim@mail:~$ tim@mail:~$                 1.1.1.1
tim@mail:~$: command not found
tim@mail:~$ 1.1.1.1: command not found
1.1.1.1:: command not found
tim@mail:~$ tim@mail:~$            NTP: 129.6.15.28
tim@mail:~$: command not found
tim@mail:~$ NTP:: command not found
NTP::: command not found
tim@mail:~$ tim@mail:~$
tim@mail:~$: command not found
tim@mail:~$ tim@mail:~$ tim@mail:~$ resolvectl status
tim@mail:~$: command not found
tim@mail:~$ tim@mail:~$: command not found
tim@mail:~$:: command not found
tim@mail:~$ tim@mail:~$ resolvectl: command not found
tim@mail:~$: command not found
tim@mail:~$ resolvectl:: command not found
resolvectl::: command not found
tim@mail:~$ tim@mail:~$ tim@mail:~$
tim@mail:~$: command not found
tim@mail:~$ tim@mail:~$: command not found
tim@mail:~$:: command not found
tim@mail:~$ tim@mail:~$ 
```


```

tim@mail:~$ systemd-resolve status
status: resolve call failed: No appropriate name servers or networks for name found
tim@mail:~$

```

```

tim@mail:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         70.33.168.xxx   0.0.0.0         UG    100    0        0 enp2s0
70.33.168.xxx   0.0.0.0         255.255.255.240 U     0      0        0 enp2s0
70.33.168.xxx   0.0.0.0         255.255.255.255 UH    100    0        0 enp2s0

```

```
tim@mail:~$ ip route
default via 70.33.168.xxx dev enp2s0 proto dhcp src 70.33.168.xxx metric 100
70.33.168.xxx/28 dev enp2s0 proto kernel scope link src 70.33.168.xxx
70.33.168.xxx dev enp2s0 proto dhcp scope link src 70.33.168.xxx metric 100

```

For Security reasons I have edited the Public IP address

---

### Post by MAFoElffen on 2021-06-29
Tim:   It's a lot simpler than you think... I just spent 2 hours trace through every onne of you posts. Through all the errors and parsing through them...

My apologies on asking you for your .yaml file again... I found it in post#4
> **kustomjs said:**
> 
```

tim@mail:~$ cat /etc/netplan/*.yaml
# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    version: 2
    renderer: [COLOR=#ff0000]networkd[/COLOR]
    ethernets:
        enp2s0:
            dhcp4: true 
```

Along the way I asked you to do this:
> **MAFoElffen said:**
> Then post the reslults of
```
netplan try

```

Later you posted output, but didn't post the associated commands that went with that out... I asked you to go back and edit that... no matters. 

This is is important and is reoccurring throughout you errors...Here was your results of "netplan try":
QUOTE=kustomjs;14045922]

```

ERROR: cannot create file run/systemd/network/10-netplan-enp2s0: Failed to create file &#8220;/run/systemd/network/10-netplan-enp2s0.network.FRVF50&#8221;: Permission denied

An error occurred: the configuration could not be generated

Reverting.
Something really bad happened while reverting config: [Errno 13] Permission denied: '10-netplan-enp2s0.network'
You should verify the netplan YAML in /etc/netplan and probably run 'netplan apply' again.
tim@mail:~$ sudo netplan try
Warning: Stopping systemd-networkd.service, but it can still be activated by:
  systemd-networkd.socket
Do you want to keep these settings?

Press ENTER before the timeout to accept the new configuration

Changes will revert in 114 seconds

```[/quote]
Which say's your NetPlan network configuration is not working...

I parsed through those errors... Look what I find besides the above error:
```
mafoelffen@Opti-Ubuntu-Main:~$ sudo find ~/Test/ -type f -name "*.log" -print0 | xargs -I {} -0 grep -i ": command not found" "{}"
[COLOR=#b22222]> RX: [/COLOR]command not found
[COLOR=#b22222]TX:[/COLOR] command not found
[COLOR=#b22222]ERROR::[/COLOR] command not found
[COLOR=#b22222]An: [/COLOR]command not found
[COLOR=#b22222]Reverting.:[/COLOR] command not found
[COLOR=#b22222]Something: [/COLOR]command not found
[COLOR=#b22222]You[/COLOR]: command not found
[COLOR=#b22222]tim@mail:~$:[/COLOR] command not found
[COLOR=#b22222]Warning::[/COLOR] command not found
[COLOR=#b22222]systemd-networkd.socket: [/COLOR]command not found
[COLOR=#b22222]Do:[/COLOR] command not found
[COLOR=#b22222]Press: [/COLOR]command not found
[COLOR=#b22222]Changes:[/COLOR] command not found
[COLOR=#b22222]tim@mail:~$:[/COLOR] command not found
[COLOR=#b22222]IDX: [/COLOR]command not found
[COLOR=#b22222]1: [/COLOR]command not found
[COLOR=#b22222]2:[/COLOR] command not found
[COLOR=#b22222]&#9679;: [/COLOR]command not found
[COLOR=#b22222]Address::[/COLOR] command not found
[COLOR=#b22222]fe80::d63d:7eff:fxx2:7cxx: [/COLOR]command not found
[COLOR=#b22222]Gateway::[/COLOR] command not found
[COLOR=#b22222]DNS::[/COLOR] command not found
[COLOR=#b22222]1.1.1.1: [/COLOR]command not found
[COLOR=#b22222]NTP::[/COLOR] command not found
t[COLOR=#b22222]im@mail:~$: [/COLOR]command not found
[COLOR=#b22222]tim@mail:~$ resolvectl:[/COLOR] command not found
[COLOR=#b22222]resolvectl:: [/COLOR]command not found
[COLOR=#b22222]tim@mail:~$:[/COLOR] command not found
[COLOR=#b22222]tim@mail:~$:[/COLOR] command not found
[COLOR=#b22222]tim@mail:~$ TX:[/COLOR] command not found
[COLOR=#b22222]TX:: [/COLOR]command not found
[COLOR=#b22222]tim@mail:~$:[/COLOR] command not found
[COLOR=#b22222]-bash:: [/COLOR]command not found
[COLOR=#b22222]tim@mail:~$:[/COLOR] command not found
[COLOR=#b22222]Command:[/COLOR] command not found
[COLOR=#b22222]> RX: [/COLOR]command not found
[COLOR=#b22222]tim@mail:~$: [/COLOR]command not found
[COLOR=#b22222]tim@mail:~$ TX: [/COLOR]command not found
[COLOR=#b22222]TX::[/COLOR] command not found
[COLOR=#b22222]tim@mail:~$:[/COLOR] command not found
[COLOR=#b22222]tim@mail:~$:[/COLOR] command not found
[COLOR=#b22222]tim@mail:~$: [/COLOR]command not found
[COLOR=#b22222]tim@mail:~$ ERROR::[/COLOR] command not found
[COLOR=#b22222]ERROR::: [/COLOR]command not found
[COLOR=#ff0000]tim@mail:~$: [/COLOR]command not found
[COLOR=#ff0000]tim@mail:~$: [/COLOR]command not found
[COLOR=#ff0000]tim@mail:~$ [/COLOR]An: command not found
[COLOR=#ff0000]An:: [/COLOR]command not found
[COLOR=#ff0000]## I stopped highlighting here... I think you get the idea. ##[/COLOR]
tim@mail:~$: command not found
tim@mail:~$: command not found
tim@mail:~$ Reverting.: command not found
Reverting.:: command not found
tim@mail:~$: command not found
tim@mail:~$ Something: command not found
Something:: command not found
tim@mail:~$: command not found
tim@mail:~$ You: command not found
You:: command not found
tim@mail:~$: command not found
tim@mail:~$ tim@mail:~$: command not found
tim@mail:~$:: command not found
tim@mail:~$: command not found
tim@mail:~$ Warning:: command not found
Warning::: command not found
tim@mail:~$: command not found
tim@mail:~$ systemd-networkd.socket: command not found
systemd-networkd.socket:: command not found
tim@mail:~$: command not found
tim@mail:~$ Do: command not found
Do:: command not found
tim@mail:~$: command not found
tim@mail:~$: command not found
tim@mail:~$: command not found
tim@mail:~$ Press: command not found
Press:: command not found
tim@mail:~$: command not found
tim@mail:~$: command not found
tim@mail:~$: command not found
tim@mail:~$ Changes: command not found
Changes:: command not found
tim@mail:~$: command not found
tim@mail:~$: command not found
tim@mail:~$ tim@mail:~$: command not found
tim@mail:~$:: command not found
tim@mail:~$: command not found
tim@mail:~$ IDX: command not found
IDX:: command not found
tim@mail:~$: command not found
tim@mail:~$ 1: command not found
1:: command not found
tim@mail:~$: command not found
tim@mail:~$ 2: command not found
2:: command not found
tim@mail:~$: command not found
tim@mail:~$: command not found
tim@mail:~$: command not found
tim@mail:~$ &#9679;: command not found
&#9679;:: command not found
tim@mail:~$: command not found
tim@mail:~$ Address:: command not found
Address::: command not found
tim@mail:~$: command not found
tim@mail:~$ fe80::d63d:7eff:fxx2:7cxx: command not found
fe80::d63d:7eff:fxx2:7cxx:: command not found
tim@mail:~$: command not found
tim@mail:~$ Gateway:: command not found
Gateway::: command not found
tim@mail:~$: command not found
tim@mail:~$ DNS:: command not found
DNS::: command not found
tim@mail:~$: command not found
tim@mail:~$ 1.1.1.1: command not found
1.1.1.1:: command not found
tim@mail:~$: command not found
tim@mail:~$ NTP:: command not found
NTP::: command not found
tim@mail:~$: command not found
tim@mail:~$: command not found
tim@mail:~$ tim@mail:~$: command not found
tim@mail:~$:: command not found
tim@mail:~$ tim@mail:~$ resolvectl: command not found
tim@mail:~$: command not found
tim@mail:~$ resolvectl:: command not found
resolvectl::: command not found
tim@mail:~$: command not found
tim@mail:~$ tim@mail:~$: command not found
tim@mail:~$:: command not found
mafoelffen@Opti-Ubuntu-Main:~$ 
```
Which strangely looks like some misdirect of stdout as stdin... Either a piping, direction of output, or ??? But that has nothing to do with your networking. That's just another problem.

I see nothing wrong what your routing table. It goes to your local DNS, which goes to the OpenDNS at CloudFlare.


###   ###   ###   ###   ###   ###   ###
Some things about your NetPlan file:
RE: [Canonical NetPlan Reference]("https://netplan.io/reference/") 
Change your's  to this:
```
# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    version: 2
    [COLOR=#000000]renderer: networkd[/COLOR] 
    ethernets:
        enp2s0:
            dhcp4: true

```

---

### Post by kustomjs on 2021-06-29
I sent you a other PM

---

### Post by LHammonds on 2021-06-29
networkd "is" my renderer in all of my 20.04 config files.

```

# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  ethernets:
    ens160:
      dhcp4: false
      dhcp6: false
      addresses: [192.168.1.42/24]
      gateway4: 192.168.1.1
      nameservers:
        addresses: [192.168.1.1,192.168.1.2,1.1.1.1,8.8.8.8]

```

I suspect the bungled code in post #21 was just the OP copying the output, then accidentally pasting it in PuTTY to get all those "command not found" messages and then for some reason, copied that and pasted it into the thread here.

LHammonds

---

### Post by MAFoElffen on 2021-06-29
@LHammands

Yes. You are right. The problem is somewhere in NetPlan and systemd.networkd on that system. It could be as simple as an extraneous character in a file or an old/extra file in the build path.  I think the smart way to go about it is to run a trace in the "netplan generate" and "netplan try" processes to narrow done where the problem lies. That is not something you would post the results of in a public forum, for a public facing host.

The problem with NetPlan, yaml, and the .yaml file, is that the .yaml config file is very picky about formatting, idents, and whitespace!!! An extra space or a tab in it and it will cause the generate to "fail." And just using a --debug switch with the netplan utility won't display those errors. It reminds me of Python language conventions.


EDIT: @LHammonds... Thank you for triggering my memory on that! His fix could be as easy as recreating his .yaml file and trying it. (just in case there is an extraneous character or formatting error in that file...)

---

### Post by kevdog on 2021-06-30
@MAFoElffen 

Slightly off topic -- I never understood why Ubuntu has netplan in the first place when it relies on systemd-networkd?? On Arch for example I just configure systemd-networkd directly without any netplan intermediate.  The syntax is a little different, but it's no more or less difficult.  I'm a big fan of yaml config files (like used in docker compose), however I've setup vim to provide for the correct spacing since I'm aware one extra space can screw things up.  With systemd-networkd, the config files don't depend on yaml syntax and seem less prone to errors.  I guess some things I just don't understand.

---

