---
title: "Automatically starting a guest"
date: 2008-05-15
forum: Virtualisation
---

### Post by Peter09 on 2008-05-15
Hi,
I am having trouble automatically starting a VirtualBox guest at boot.

I have tried using rc.local --- VBoxHeadless --startvm <name>

but this does not work, I get a machine not found error.

I guess this is to do with the fact that no one is logged on and the paths are not there to get to the machine. I have tried putting a full pathname in but this is either incorrect or I am not doing it correctly.

Has anyone done this, what am I missing here?

PC

---

### Post by Peter09 on 2008-05-22
bump

---

### Post by pldaniels on 2008-08-03
Same problem here, trying to start up in Ubuntu 8.04 via /etc/rc.local (or similar) and it just keeps dying, best I can report is that it returns error code '5', though I've not yet found a reference to what that code means.

Paul.

[UPDATED - Here's a strace of the attempt, as you can see, it's trying to run as root (despite su'ing it as the user, obviously I need to make it drop to the user a different way) ]
stat64("/root", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64("/root/.VirtualBox", 0xbfcb5fc0) = -1 ENOENT (No such file or directory)
lstat64("/root", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat64("/root/.VirtualBox", 0xbfcb1f2c) = -1 ENOENT (No such file or directory)
lstat64("/root", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat64("/root", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat64("/root/.VirtualBox", 0xbfcb1f2c) = -1 ENOENT (No such file or directory)
mkdir("/root", 0777)                    = -1 EEXIST (File exists)
mkdir("/root/.VirtualBox", 0777)        = -1 EACCES (Permission denied)
exit_group(-2147467259)                 = ?
Process 5378 detached

---

### Post by pldaniels on 2008-08-03
Okay, here goes, this is what's now working for me in my rc.local file

(USER = the username that the vbox belongs to,  VBOXname is the machine you want to start)

> #/home/USER/bridge-up  (this is a small script I've got to bring the tun/br's up prior to starting my Vbox

/bin/su USER -c '/usr/bin/VBoxHeadless -s "VBOXname"' &


The crux here is using 'su' rather than 'sudo', as I just couldn't get sudo to work right in this instance.

---

