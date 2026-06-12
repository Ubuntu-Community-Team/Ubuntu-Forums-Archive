---
title: "Can't write to VBox shared folder Win7 (host) Lubuntu 12.04 (guest)"
date: 2012-10-26
forum: Virtualisation
---

### Post by sysmatck on 2012-10-26
I'm posting here cause I have no idea how can I solve my problem...

I'm used to make VBox lubuntu (hosts) and WinXP (guests) and had no problem with it so far. Now trying on Win7 host is pissing me off! But I guess the problem is on some config. on linux, cause I guess it was working before, maybe an update (kernel?) might have messing things up!

Ok, let's go:

Host: Windows 7 Ultimate
Client: Ubuntu 12.04
VM software: VirtualBox
Guest additions: installed
Shared directory: C:\trocas
NTFS folder permissions: Everyone = full control

I'm mounting the shared folder through /etc/fstab like this:
```
trocas  /home/lnks/Downloads/   vboxsf  rw,auto,exec,uid=1000,gid=116   0       0
```
but also tried with gid=1000 and on /etc/rc.local with the command:
```
sudo mount -t vboxsf -o rw,exec,auto trocas /home/lnks/Downloads/
```

```
groups lnks
``` retrurns:
lnks : vboxsf adm lp dialout fax cdrom floppy tape sudo audio dip www-data video plugdev fuse lpadmin netdev lnks sambashare

The wierd thing is, I can't grant write permissions to the mounted folder with:
```
sudo chmod +w Downloads/
```
No error is returned, but permissions continue to be:
dr-xr-xr-x 1 lnks vboxsf 4096 Out 26 17:11 Downloads

All other /home/lnks/ folders have drwxr-xr-x permissions

Can't change owner with:
```
sudo chown root.root Downloads/
```
Only with the mounting commands...

Another thing, I can write with Super User:
```
sudo mkdir /home/lnks/Downloads/test
```
But
```
mkdir /home/lnks/Downloads/test2
```
returns: "permission denied"

Can list an read all files on ~/Downloads/ and cannot write!

---

### Post by sysmatck on 2013-01-05
Solved using "Auto-mount" option...

---

