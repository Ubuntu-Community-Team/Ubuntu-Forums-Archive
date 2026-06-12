---
title: "vmware server on gutsy 64"
date: 2007-10-20
forum: Virtualisation
---

### Post by benner on 2007-10-20
i am downloading the new vmware server and i already have the patch ready but before i get started i want to make sure that i can do this on a 64 bit system.  i have read a lot of posts of people getting it running on gutsy but didn't see any that mentioned 64-bit.  thought i'd ask before i get started.

---

### Post by cenwesi on 2007-10-22
What most people don't mention is that you need to recompile the kernel. 
Issue this commands before you run the installer...

$ sudo aptitude install build-essential linux-headers-`uname -r` xinetd
$ sudo aptitude install libxtst6 libxt6 libxrender1

---

### Post by LukeCarrier on 2008-01-01
I've also heard about people installing a package called 'ia32-libs' and 'libc6-i386'.

To install this, you'd need to run: 
```
sudo aptitude install ia32-libs libc6-i386
```

Try [this page]("https://help.ubuntu.com/community/VMware/Server/AMD64") in the Ubuntu Wiki.

---

### Post by fjgaude on 2008-01-01
I didn't have any troubles with my 64-bit Ubuntu Gutsy. I downloaded the binary from vmware.com and simply followed instructions. No issues what so ever. Used my old license and that worked.

Good luck and Happy New Year!

---

### Post by dcstar on 2008-01-03
> **cenwesi said:**
> What most people don't mention is that you need to recompile the kernel. 
Issue this commands before you run the installer...

$ sudo aptitude install build-essential linux-headers-`uname -r` xinetd
$ sudo aptitude install libxtst6 libxt6 libxrender1

I just installed the package in the repositories and it works fine.

There is no need whatsoever to do any compilation to install (and run) vmware server on Gutsy-64.

---

### Post by aliencam on 2008-01-09
> **dcstar said:**
> I just installed the package in the repositories and it works fine.

There is no need whatsoever to do any compilation to install (and run) vmware server on Gutsy-64.

how do you install vmware server from the repositories??? I have all respositories enabled and there is no vmware server, and there is no vmware period for x64...

---

### Post by Erik-NA on 2008-01-09
In /etc/apt/sources.list the following lines exist in my gutsy 64 bit install

[PHP]## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
#deb http://archive.canonical.com/ubuntu gutsy partner
#deb-src http://archive.canonical.com/ubuntu gutsy partner
[/PHP]

Remove the remarks  and try

---

### Post by aliencam on 2008-01-09
those two were already uncommended... 

i was only looking in the add/remove programs application. not in synaptic. lol. I just found it in synaptic.  thanks.

---

