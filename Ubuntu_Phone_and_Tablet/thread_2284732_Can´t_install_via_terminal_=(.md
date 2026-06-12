---
title: "Can´t install via terminal =("
date: 2015-07-01
forum: Ubuntu Phone and Tablet
---

### Post by Robert_Langner on 2015-07-01
I wan´t to install some stuff via the terminal with my Aquaris e5 ubuntu edition.

W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
E: The package lists or status file could not be parsed or opened

What´s the problem? =(

Please help me=(

---

### Post by Bashing-om on 2015-07-01
Robert_Langner; Hello;

In the case of a dpkg lock:
```

sudo lsof /var/lib/dpkg/lock

```
Should tell you whats locking dpkg.

And in the case of  "file could not be parsed or opened" Indicates corruption at some level/point in apt's control files.
We can remove them and rebuild these controls files:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```

Reboot the system, and try and install a package from the software repository. What now results ?

[INDENT][INDENT][INDENT]all in the process
[/INDENT][/INDENT][/INDENT]

---

### Post by Robert_Langner on 2015-07-01
sudo lsof /var/lib/dpkg/lock tells me nothing. just a new ~$ line =(
and [COLOR=#000000][FONT=Ubuntu Mono]/var/lib/apt/lists cannot removed : Read-only file system =(
what is this "Read-only system"? and how can i change it?[/FONT][/COLOR]

---

### Post by Robert_Langner on 2015-07-01
$ mount /dev/loop0 / -o remount,rw. Thak´s for the help. This worked for me =)

---

### Post by Bashing-om on 2015-07-01
Robert_Langner; Well ..

in the case of the 'lsof' return to prompt:
Means there is no longer a lock on apt.

A "read only file system" :
The system has detected a problem and is protecting it's self from further damage.

Let's take a less intrusive method and see what results to 'fix' the file system.
In terminal execute :
```

sudo touch /forcefsck
sudo shutdown -r now

```
to set the flag to check the file system at next boot;
and 'shutdown' to reboot the system and do the file system check.

maybe will fix the issue.

[INDENT][INDENT]else we do else
[/INDENT][/INDENT]

---

### Post by coffeecat on 2015-07-02
*Thread moved to **Ubuntu Phone and Tablet**.*

---

