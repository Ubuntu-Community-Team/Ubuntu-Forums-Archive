---
title: "apt/dpkg status-old file error"
date: 2020-12-21
forum: Ubuntu/Debian BASED
---

### Post by bardiamgtgc on 2020-12-21
when i try to install a package or upgrade or even dpkg -i
i get the error E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. which isnt anything unusual it happens when i stop apt while installing something but after running that command i get dpkg: error: error creating new backup file '/var/lib/dpkg/status-old': Operation not permitted
i tried to make status-old with touch after running the command again it gets removed
i tried copying status to status-old it gets removed 
when i run apt update sometimes it runs without any issues and the status file is there other times i get 
E: flAbsPath on /var/lib/dpkg/status failed - realpath (2: No such file or directory)
E: Could not open file  - open (2: No such file or directory)
E: Problem opening
E: The package lists or status file could not be parsed or opened.
and status file file is called status-new so if i rename it to status apt update will work again
distro is kali but because its based on ubuntu i thought i will post it here
it was working like last night 
also just a quick info in /var/backups there is no dpkg backup nor there is a backup in /var/lib/dpkg

---

### Post by Bashing-om on 2020-12-21
bardiamgtgc; Hello -

Try:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt update
sudo apt upgrade

```

MergeLists are a working tool of apt, part of the way it keeps track of which packages are in which repositories. It's the gears of a text-based database that apt relies upon. When corrupted, they can be safely deleted. Apt will recreate them during the next apt update.

[INDENT]my bit to try and help
[/INDENT]

---

### Post by bardiamgtgc on 2020-12-21
hey thanks for your reply
i tried doing this didnt really seem to work same errors

---

### Post by ActionParsnip on 2020-12-21
What is the full output of
```

sudo apt-get update
sudo apt-get upgrade 

```

---

### Post by bardiamgtgc on 2020-12-21
if i dont rename status-new to status:

root@localhost:/var/lib/dpkg# sudo apt-get update;sudo apt-get update >> output
Hit:1 [http://mirror.fsmg.org.nz/kali](http://mirror.fsmg.org.nz/kali) kali-rolling InRelease
Reading package lists... Error!
E: flAbsPath on /var/lib/dpkg/status failed - realpath (2: No such file or directory)
E: Could not open file  - open (2: No such file or directory)
E: Problem opening
E: The package lists or status file could not be parsed or opened.
E: flAbsPath on /var/lib/dpkg/status failed - realpath (2: No such file or directory)
E: Could not open file  - open (2: No such file or directory)
E: Problem opening
E: The package lists or status file could not be parsed or opened.

if i rename status-new to status it will be this:

root@localhost:/var/lib/dpkg# apt update
Hit:1 [http://mirror.fsmg.org.nz/kali](http://mirror.fsmg.org.nz/kali) kali-rolling InRelease
Reading package lists... Done
Building dependency tree
Reading state information... Done
3 packages can be upgraded. Run 'apt list --upgradable' to see them.
root@localhost:/var/lib/dpkg# apt upgrade
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
root@localhost:/var/lib/dpkg# dpkg --configure -a
dpkg: error: error creating new backup file '/var/lib/dpkg/status-old': Operation not permitted

---

### Post by deadflowr on 2020-12-21
*Thread moved to **Ubuntu/Debian BASED***

---

