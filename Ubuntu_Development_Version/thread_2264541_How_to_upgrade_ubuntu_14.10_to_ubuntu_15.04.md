---
title: "How to upgrade ubuntu 14.10 to ubuntu 15.04?"
date: 2015-02-08
forum: Ubuntu Development Version
---

### Post by NunoLava1998 on 2015-02-08
Hello, i came back to ubuntu and upgraded to ubuntu 14.10 which taked hours. How i upgrade to ubuntu 15.04 now? Do i have to put that upgrading command in terminal (i think its do-release-upgrade), When i search, i only get results of problems about upgrading from 14.10 or 14.04 to 15.04, do i need to do "do-release-upgrade" command in terminal??

---

### Post by NunoLava1998 on 2015-02-08
Added the option to upgrade to development versions, but do-release-upgrade still says there are no ubuntu versions to download.

---

### Post by Frogs Hair on 2015-02-08
Moved to ***Ubuntu Development Version***

---

### Post by oldos2er on 2015-02-08
Try ```
sudo apt-get update

sudo apt-get dist-upgrade

do-release-upgrade -d
```

---

### Post by NunoLava1998 on 2015-02-08
> **oldos2er said:**
> Try ```
sudo apt-get update

sudo apt-get dist-upgrade

do-release-upgrade -d
```
Tried and its upgrading. Thanks!

EDIT: I rebooted and nothing happened... I still saw the 14.10 thing at the left bottom corner of the background... I just runned lm-sensors and it got updated.. fan2 is strangely the only fan that is working. The rest of the fans are at 0RPM.

---

### Post by zika on 2015-02-08
Did You enable a proper choice for distribution upgrade?

---

### Post by NunoLava1998 on 2015-02-08
> **zika said:**
> Did You enable a proper choice for distribution upgrade?
Where i can enable that?

---

### Post by grahammechanical on 2015-02-08
Run

```
lsb_release -a
```

it should say

> No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu Vivid Vervet (development branch)
Release:	15.04
Codename:	vivid


You may need to run again

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Regards.

---

### Post by NunoLava1998 on 2015-02-08
> **grahammechanical said:**
> Run

```
lsb_release -a
```

it should say



You may need to run again

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Regards.

The only thing that installed or updated something was the first command (sudo apt-get update).
And the lsb_release -a did not say things of vivid, it did say about utopic. Restarting now.
EDIT: im still in ubuntu 14.10, I guess, i think i need to download the iso of 15.04

---

### Post by zika on 2015-02-08
Show us contents of [SIZE=1][COLOR=#333333][FONT=UbuntuRegular][SIZE=2]/var/log/dist-upgrade/[/SIZE] [SIZE=2]&#8203;...[/SIZE][/FONT][/COLOR][/SIZE]

---

### Post by NunoLava1998 on 2015-02-08
Things marked with "dir" are folders/directories, dist-upgrade is a folder and i can only show the file/directory names.
20150208-1559 (dir)
apt.log
apt-clone_system_state.tar.gz
lspci.txt
main.log

Inside 20150208-1559 directory there is:
apt.log
apt-term.log
history.log
main.log
xorg_fixup.log

What is the file you need information?
I think the cause is that i saw some errors when upgrading from 14.04 to 14.10.

---

### Post by zika on 2015-02-08
> **NunoLava1998 said:**
> What is the file you need information?I do not need any... ;) Just trying to gain some insight so I might be able to see what went wrong, even though I gave my guess above...> **zika said:**
> Show us **contents** of [SIZE=1][COLOR=#333333][FONT=UbuntuRegular][SIZE=2]/var/log/dist-upgrade/[/SIZE] [SIZE=2]&#8203;...[/SIZE][/FONT][/COLOR][/SIZE]You pick those from (I'd say freshest but that might not be enough since it looks like dist-upgrade was performed twice) sub-folder that are pertinent to Your question...
This might help: [https://wiki.ubuntu.com/DebuggingUpdateManager](https://wiki.ubuntu.com/DebuggingUpdateManager)
Update&#8321;: You might want use a method that I've tried so many times and described in previous U+1 cycle(s) and also in this (as far as I do remeber) that is self-contained and _it worked for me_ on numerous occasiona. I do not promote it... I do call it &#8222;Debian way of upgrade&#8220;...

---

### Post by NunoLava1998 on 2015-02-08
Just installing 15.04 iso. firefox says 8 minutes left.

---

