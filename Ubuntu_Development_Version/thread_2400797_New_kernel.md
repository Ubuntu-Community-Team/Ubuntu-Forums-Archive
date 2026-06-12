---
title: "New kernel"
date: 2018-09-10
forum: Ubuntu Development Version
---

### Post by P-I H on 2018-09-10
The latest upgrade included
```
p-i@pi-MS-7A34:~$ uname -r
4.18.0-7-generic
p-i@pi-MS-7A34:~$
``` 

with only two errors
```
-- Logs begin at Thu 2018-08-09 20:03:45 CEST, end at Mon 2018-09-10 15:35:34 CEST. --
sep 10 15:21:31 pi-MS-7A34 spice-vdagent[1751]: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
sep 10 15:21:53 pi-MS-7A34 spice-vdagent[2525]: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
~
~

```

---

### Post by corradoventu on 2018-09-11
on my Ubuntu Cosmic the last upgrade is
```
corrado@corrado-HP-p6-cc-0904:~$ date
mar 11 set 2018, 09.02.07, CEST
corrado@corrado-HP-p6-cc-0904:~$ uname -a
Linux corrado-HP-p6-cc-0904 4.17.0-9-generic #10-Ubuntu SMP Wed Aug 22 13:33:37 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
corrado@corrado-HP-p6-cc-0904:~$ 

```
and the log shows more errors:
```
08:44:30 spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
08:44:23 gnome-session-b: Unrecoverable failure in required component org.gnome.Shell.desktop
08:44:08 spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
08:43:38 kernel: uvcvideo: Failed to query (GET_INFO) UVC control 4 on unit 2: -32 (exp. 1).
```

---

### Post by P-I H on 2018-09-11
I'm using the Main server and this was the upgrade ```
Start-Date: 2018-09-10  15:20:13Commandline: aptdaemon role='role-commit-packages' sender=':1.444'
Install: linux-modules-4.18.0-7-generic:amd64 (4.18.0-7.8, automatic), linux-headers-4.18.0-7:amd64 (4.18.0-7.8, automatic), linux-image-4.18.0-7-generic:amd64 (4.18.0-7.8, automatic), linux-headers-4.18.0-7-generic:amd64 (4.18.0-7.8, automatic), linux-modules-extra-4.18.0-7-generic:amd64 (4.18.0-7.8, automatic)
Upgrade: linux-headers-generic:amd64 (4.17.0.9.12, 4.18.0.7.8), linux-image-generic:amd64 (4.17.0.9.12, 4.18.0.7.8), linux-signed-generic:amd64 (4.17.0.9.12, 4.18.0.7.8), linux-generic:amd64 (4.17.0.9.12, 4.18.0.7.8)
End-Date: 2018-09-10  15:20:49

```Before the upgrade I also had the error```
gnome-session-b: Unrecoverable failure in required component org.gnome.Shell.desktop

```

---

### Post by harry332 on 2018-09-11
There is a new kernel version on its way to the section proposed:

[https://launchpad.net/ubuntu/+source/linux/4.18.0-8.9](https://launchpad.net/ubuntu/+source/linux/4.18.0-8.9)

---

### Post by corradoventu on 2018-09-13
```
corrado@corrado-HP-p7-cc-0911:~$ inxi -SMx
System:    Host: corrado-HP-p7-cc-0911 Kernel: 4.19.0-041900rc3-generic x86_64 bits: 64 compiler: gcc 
           v: 8.2.0 Desktop: Gnome 3.30.0 Distro: Ubuntu 18.10 (Cosmic Cuttlefish) 
Machine:   Type: Laptop System: Hewlett-Packard product: HP 250 G3 Notebook PC 
           v: 0991100000000000000600087 serial: <root required> 
           Mobo: Hewlett-Packard model: 2211 v: 86.49 serial: <root required> UEFI: Insyde v: F.36 
           date: 12/18/2014 
corrado@corrado-HP-p7-cc-0911:~$ 

```
and new messages
```
17:46:20 sudo:  corrado : a password is required ; TTY=pts/0 ; PWD=/home/corrado ; USER=root ; COMMAND=/usr/sbin/hddtemp -nq -u C /dev/sda
17:15:39 spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
17:15:32 gnome-session-b: Unrecoverable failure in required component org.gnome.Shell.desktop
17:15:18 kernel: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
17:14:43 kernel: uvcvideo: Failed to query (GET_INFO) UVC control 4 on unit 2: -32 (exp. 1).
```

---

### Post by corradoventu on 2018-09-20
```
corrado@corrado-HP-p7-cc-0911:~$ inxi -SMx
System:
  Host: corrado-HP-p7-cc-0911 Kernel: 4.19.0-041900rc4-generic x86_64 
  bits: 64 compiler: gcc v: 8.2.0 Desktop: Gnome 3.30.0 
  Distro: Ubuntu 18.10 (Cosmic Cuttlefish) 
Machine:
  Type: Laptop System: Hewlett-Packard product: HP 250 G3 Notebook PC 
  v: 0991100000000000000600087 serial: <root required> 
  Mobo: Hewlett-Packard model: 2211 v: 86.49 serial: <root required> 
  UEFI: Insyde v: F.36 date: 12/18/2014 
corrado@corrado-HP-p7-cc-0911:~$ 

```

```
09:39:29 spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
09:39:23 gnome-session-b: Unrecoverable failure in required component org.gnome.Shell.desktop
09:30:27 spice-vdagent: Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0
09:30:00 kernel: uvcvideo: Failed to query (GET_INFO) UVC control 4 on unit 2: -32 (exp. 1).
```

---

