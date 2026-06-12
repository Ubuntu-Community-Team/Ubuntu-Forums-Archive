---
title: "Cannot do apt update, error"
date: 2023-09-06
forum: Server Platforms
---

### Post by hamimi on 2023-09-06
I have installed Ubuntu 22.04-server
getting this when i try do apt update:
root@bwezdmzprxy01:~# apt update
Err:1 [http://dl.openfoam.org/ubuntu](http://dl.openfoam.org/ubuntu) jammy InRelease
  403  Forbidden [IP: 13.41.234.222 80]
Err:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy InRelease
  403  Forbidden [IP: 91.189.91.81 80]
Err:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease
  403  Forbidden [IP: 91.189.91.81 80]
Err:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-backports InRelease
  403  Forbidden [IP: 91.189.91.81 80]
Err:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-security InRelease
  403  Forbidden [IP: 91.189.91.81 80]

---

### Post by hamimi on 2023-09-06
here is my sources.list


root@bwezdmzprxy01:/etc/apt# more sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-backports main restricted universe mu
ltiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-backports main restricted unive
rse multiverse


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-security main restricted
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-security universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-security multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-security multiverse




PRETTY_NAME="Ubuntu 22.04.3 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.3 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy

---

### Post by coffeecat on 2023-09-06
Support, not chat.

*Thread moved to **Server Platforms**.*

---

### Post by grahammechanical on 2023-09-07
To update/upgrade Ubuntu Server or Ubuntu Desktop (using the terminal) we enter two comands. This is the command that you entered:

> root@bwezdmzprxy01:~# apt update

This is the command that you should use:

```
sudo apt update
```

The prefix sudo will cause the OS to demand a password before it will process the update command. The same condition applies to the second command

```
sudo apt upgrade
```

Did you install Ubuntu Server? Then, the installed required you to register a password. That same password will allow you to login to Ubuntu but as a standard user. When we need become the administrator (as when needing to update/upgrade) we prefix the command with sudo and then enter our password. We become the administrator with elevated privileges temporarily.

You were trying to do as a standard user what only an administrator is allowed to do. You were forbidden to do that.

Regards

---

### Post by Rubi1200 on 2023-09-07
The errors might have been only temporary, I could access the links.

But, what I do know is that you should NOT be running a server as root. This is a serious security flaw that could break the system or allow malicious actors access.

Please login as a standard user and only use elevated privileges as/when you need to.

The difference:

Standard user: ```
~$ sudo apt update
```

Root user: ```
~[COLOR=#ff0000]#[/COLOR] apt update
```

---

