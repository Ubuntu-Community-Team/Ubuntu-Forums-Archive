---
title: "How to upgrade Ubuntu-16.04-beta2 to Ubuntu-16.04 LTS stable"
date: 2016-04-21
forum: Ubuntu Development Version
---

### Post by parker-hugh on 2016-04-21
Hi, I have been using Ubuntu-16.04-beta2 for a few weeks, and am very happy so far.  I would like to upgrade to Ubuntu-16.04 LTS stable when available.  

I checked here...  [http://www.ubuntu.com/download/desktop/upgrade](http://www.ubuntu.com/download/desktop/upgrade)

... and it suggests search for Update Manager, and select the tab called "Updates". Then set the "Notify me of a new Ubuntu version" dropdown menu to "For any new version".  (on my system it's set to 'for long term support versions').  Press Alt+F2 and type in "update-manager"  (without the quotes) into the command box.  The Update Manager should  open up and tell you that a new distribution is available. Click Upgrade and follow the on-screen instructions.

I only want the LTS version so is my system setup already to automatically get the LTS version when it is available, or do I need to do something different?

Thanks for any help, as I'm still learning linux.

---

### Post by dino99 on 2016-04-21
updating & upgrading is enough (as you already use that LongTermSupport) :P

sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by grahammechanical on 2016-04-21
Believe what you see on the login screen. If you want proof run

```
lsb_release -a
```

> graham@sdb7-Dev:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial


If it says "development branch" then you are not yet there.

Regards.

---

### Post by parker-hugh on 2016-04-21
> **dino99 said:**
> updating & upgrading is enough (as you already use that LongTermSupport) :P
sudo apt-get update
sudo apt-get dist-upgrade
Thanks for reply. I did what you suggested...

```
$ sudo apt update 
 
hugh@INSP-15-UBUNTU:~$ sudo apt dist-upgrade 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Calculating upgrade... Done 
The following packages were automatically installed and are no longer required: 
  linux-headers-4.4.0-17 linux-headers-4.4.0-17-generic linux-image-4.4.0-17-generic 
  linux-image-extra-4.4.0-17-generic linux-signed-image-4.4.0-17-generic 
Use 'sudo apt autoremove' to remove them. 
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade. 
hugh@INSP-15-UBUNTU:~$
``` 
So I ran the autoremove command for the suggested packages and it completed ok.
> **grahammechanical said:**
> Believe what you see on the login screen. If you want proof run
```
lsb_release -a
```
If it says "development branch" then you are not yet there.
Regards.
Thanks for that, I ran the command...
```
hugh@INSP-15-UBUNTU:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial
hugh@INSP-15-UBUNTU:~$ 
```
so all looks good. Thanks for your quick support. Much appreciated.

---

### Post by Bucky Ball on 2016-04-21
Those update commands will work with 16.04 LTS fine, but the newer commands are:

```
sudo apt update
sudo apt full-upgrade
```

After that:

```
sudo apt autoremove
```

:)

---

### Post by parker-hugh on 2016-04-21
Sorry, got one last quick question, does my sources list look ok?

```
hugh@INSP-15-UBUNTU:~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Beta amd64 (20160323)]/ xenial main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ xenial main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
# deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial universe
deb http://gb.archive.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner

deb http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse
hugh@INSP-15-UBUNTU:~$
```
That's one thing that I had problems with in previous installation.

Thanks

---

### Post by parker-hugh on 2016-04-21
> **Bucky Ball said:**
> Those update commands will work with 16.04 LTS fine, but the newer commands are:

```
sudo apt update
sudo apt full-upgrade
```

After that:

```
sudo apt autoremove
```

:)
Thanks for the feedback,  I'll keep a note of these commands for future reference.

---

### Post by Bucky Ball on 2016-04-21
Unless you've manually altered it or added repos, wouldn't worry about that.

Just run:

```
sudo apt update
sudo apt full-upgrade
```

... regularly and you will get to the final release ... when it's released. There's been a slight delay.

---

### Post by parker-hugh on 2016-04-21
> **Bucky Ball said:**
> Unless you've manually altered it or added repos, wouldn't worry about that.
I haven't added any repos so should be ok then.
> Just run:
```
sudo apt update
sudo apt full-upgrade
```
... regularly and you will get to the final release ... when it's released. There's been a slight delay.
I wondered why there wasn't anything to upgrade when I ran the dist-upgrade command.  I'll run it again later this evening.

---

### Post by howefield on 2016-04-21
> **parker-hugh said:**
> Sorry, got one last quick question, does my sources list look ok?

Compared your sources.list to mine which was fresh installed yesterday and they are absolutely identical with one exception - I have a space between # and the word deb on the first line, which won't affect anything. Your sources.list is fine.

```
hugh@wily-laptop:~$  diff Documents/list1.txt Documents/list2.txt 
1c1
< # deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Release amd64 (20160419)]/ xenial main restricted
---
> #deb cdrom:[Ubuntu 16.04 LTS _Xenial Xerus_ - Beta amd64 (20160323)]/ xenial main restricted
hugh@wily-laptop:~$
```

---

### Post by parker-hugh on 2016-04-21
> **howefield said:**
> Compared your sources.list to mine which was fresh installed yesterday and they are absolutely identical with one exception - I have a space between # and the word deb on the first line, which won't affect anything. Your sources.list is fine.
Thanks for doing that.  I should be all set now.

---

