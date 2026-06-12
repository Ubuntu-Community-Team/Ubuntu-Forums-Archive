---
title: "Issues installing VMware Server 2.0.2 on 10.10"
date: 2011-10-26
forum: Virtualisation
---

### Post by Onthax on 2011-10-26
Hi guys

I'm having some trouble installing vmware server on a fresh install of ubuntu and it isnt poping out a useful msg, any ideas?

i followed the instructions on [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

and the directory looks like this
```


onthax@daedalus:~/vmware$ ls -l
total 463364
-rwxrwxr-x 1 onthax onthax     22247 2011-10-26 17:01 vmware-server-2.0.2-203138-update.patch
-rwxrwxr-x 1 onthax onthax 474415801 2011-10-26 17:30 VMware-server-2.0.2-203138.x86_64.tar.gz
-rwxrwxr-x 1 onthax onthax     10775 2011-10-26 16:52 vmware-server-2.0.x-kernel-2.6.3x-install.sh

onthax@daedalus:~/vmware$ sudo ./vmware-server-2.0.x-kernel-2.6.3x-install.sh
./vmware-server-2.0.x-kernel-2.6.3x-install.sh: 2: Syntax error: ")" unexpected


```

---

### Post by HermanAB on 2011-10-27
Howdy,

VMware Server is not recommended - it is a total POS.

Rather use the free VMware Player or buy VMware Workstation.

Alternatively, download Virtualbox from the Oracle web site.

---

### Post by Onthax on 2011-10-27
> **HermanAB said:**
> Howdy,

VMware Server is not recommended - it is a total POS.

Rather use the free VMware Player or buy VMware Workstation.

Alternatively, download Virtualbox from the Oracle web site.

Alas i'm playing around, trying to get some experience with vmware for work. seems like a pain to run under linux tho.

---

### Post by varunendra on 2011-10-27
> **Onthax said:**
> 
```

onthax@daedalus:~/vmware$ [COLOR=Red]**sudo ./vmware-server-2.0.x-kernel-2.6.3x-install.sh**[/COLOR]
./vmware-server-2.0.x-kernel-2.6.3x-install.sh: 2: Syntax error: ")" unexpected

```
IIRC, the highlighted command should be:
```
sudo sh ./vmware-server-2.0.x-kernel-2.6.3x-install.sh
```(that is, you are missing the 'sh' in the beginning, after sudo.)

By the way, is there something particular that VMware server can do and player can not? I second HermanAB's opinion that 'player' is much better than 'server' version (although haven't installed or used it for a long time on Linux. I currently prefer Virtualbox on Linux installations).

---

### Post by dcstar on 2011-10-29
> **Onthax said:**
> Alas i'm playing around, trying to get some experience with vmware for work. seems like a pain to run under linux tho.

Commercial VMware installations are now ESXI, Server is redundant everywhere.

---

### Post by Onthax on 2011-10-30
> **dcstar said:**
> Commercial VMware installations are now ESXI, Server is redundant everywhere.

yeh i know, but i can migrate to that later, esxi requires scsi, sas or san, no sata support :^(

---

### Post by dcstar on 2011-10-31
> **Onthax said:**
> yeh i know, but i can migrate to that later, esxi requires scsi, sas or san, no sata support :^(

Bulldust. I have an EXSI 4.1 system running using 2 SATA drives.

---

