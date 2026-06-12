---
title: "vmware-server broken manual installation blocks  synaptic package manager"
date: 2008-10-24
forum: Virtualisation
---

### Post by Gergely on 2008-10-24
hey, 
do you know how to delete broken manual installations in lenny/sid Ubuntu? i am getting pissed cause i cant find anyone around who would know, we tried command line apt-get stuff and aptitude but nothing seems to work.
The basic problem is that as I try to open the synaptic package manager it comes back with 

"An Error Occured,
E: the package vmware-server needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
"

so now I cannot install anything from the repositories...

thx

---

### Post by crom.osec on 2008-10-24
If apt crashed you can use the command:
 dpkg --configure -a
to restore it (from sudo)

I don't know if vmware-server is on default update list. When I want an upgrade on vmware-server I remove old vmware, download latest version from vmware site and I install it.

---

### Post by MaxIBoy on 2008-10-24
Try 
```
dpkg -l | grep -i vmware
```

Paste the results of that command into a post.

---

### Post by bodhi.zazen on 2008-10-24
> **Gergely said:**
> hey, 
do you know how to delete broken manual installations in lenny/sid Ubuntu? i am getting pissed cause i cant find anyone around who would know, we tried command line apt-get stuff and aptitude but nothing seems to work.
The basic problem is that as I try to open the synaptic package manager it comes back with 

"An Error Occured,
E: the package vmware-server needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
"

so now I cannot install anything from the repositories...

thx

Can you tell us what you did to install it ? Were you following a how to ?

Also you mention "lenny/sid Ubuntu" what are you running exactly ? Is this a so called "mixed system" with multople repos in your sources list ?

With that said, try :

```
sudo dpkg --remove --force-remove-reinstreq vmware-server
```

---

### Post by Bernman93 on 2009-08-02
> **bodhi.zazen said:**
> Can you tell us what you did to install it ? Were you following a how to ?

Also you mention "lenny/sid Ubuntu" what are you running exactly ? Is this a so called "mixed system" with multople repos in your sources list ?

With that said, try :

```
sudo dpkg --remove --force-remove-reinstreq vmware-server
```


But first, you have to remove all the archives (scripts) whose name began with "vmware" in the directory /var/lib/dpkg/info/ or the dpkg will fail with errors.  As soon as I removed those files, the package uninstalled.

---

### Post by cerebrum_cipher on 2009-10-26
Thanx a lot, I finally removed the broken vmware server !!!  THanx a million times.

---

