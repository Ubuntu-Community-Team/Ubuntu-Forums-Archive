---
title: "Installing latest vm tools problem"
date: 2022-09-15
forum: Server Platforms
---

### Post by dansss on 2022-09-15
Hi,

First of all I'm a linux noob and have been for the last 20 years or so of IT.

I need to update the vmware tools on one of our ubuntu servers (18.04.6)

I've done the following so try to get it updated but no luck

1. sudo apt list, then I found open-vm-tools/bionic-updates,bionic-security,now 2:11.0.5-4ubuntu0.18.04.2 amd64 [installed]
so I believe thats showing me the open-vm-tools is version 11.0.5, the latest version is 12.1.0, however I did find another verison which said the open-vm-tools latest is 11.3.5

2. sudo apt list update
all packages are up to date

3. sudo apt upgrade open-vm-tools
open-vm-tools is already the newest version (2:11.0.5-4ubuntu0.18.04.2).

this is where i'm getting stuck, as to why its saying im on the latest version, when I'm not.  Earlier I said my linux skills are poor, so do I need to point the update checker (is it called repo?) to somewhere different which has it, because when I do following 
sudo apt update
Hit:1 [http://ppa.launchpad.net/ondrej/php/ubuntu](http://ppa.launchpad.net/ondrej/php/ubuntu) bionic InRelease
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease [88.7 kB]
Hit:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic InRelease
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Get:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates InRelease [88.7 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [99.8 kB]
Get:7 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports InRelease [74.6 kB]
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe i386 Packages [1,035 kB]
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/universe amd64 Packages [1,228 kB]

i'm thinking maybe open-vm-tools isn't in those repos (if thats what they are)

Thanks

---

### Post by MAFoElffen on 2022-09-15
If you are refering to the VMware guest additions types of tools... I will explain later. STOP now.

VM Toolsets are matched and locked to the VMware Hypervisor version. If you install a different version to your guests, they will stop working with your hypervisor.

Just saying.

---

### Post by dansss on 2022-09-16
> **MAFoElffen said:**
> If you are refering to the VMware guest additions types of tools... I will explain later. STOP now.

VM Toolsets are matched and locked to the VMware Hypervisor version. If you install a different version to your guests, they will stop working with your hypervisor.

Just saying.

Hello, this is no logner true, since annoyingly vmware stopped using the vmware tools for linux, it's not open-vm-tools

---

### Post by MAFoElffen on 2022-09-17
I'm confused now. You started out saying that you had 'open-vm-tools' installed... And wanted to upgrade it to a newer version...

In your last post you say that it is not used anymore(???)

Could you please exlpain what you are trying to do and/or what is happening now?

---

### Post by dansss on 2022-09-20
Sorry I meant to say vmware tools stopped making their own vmware tools for linux, its now open-vm-tools.

i'm trying to get open-vm-tools updated to the latest which appears to be 12.10 but unsure how

---

### Post by LHammonds on 2022-09-20
> **dansss said:**
> Sorry I meant to say vmware tools stopped making their own vmware tools for linux, its now open-vm-tools.

i'm trying to get open-vm-tools updated to the latest which appears to be 12.10 but unsure how

You install open-vm-tools from the repository and it keeps itself updated when you use "apt update / apt upgrade" for the OS you are running but you are NOT going the see the bleeding edge version on LTS servers.  You are also not going to see the same version across different versions of operating systems.

Here is what I currently have installed on fully-patched VM servers on top of ESXi hosts: (all of which have always worked just fine)

Ubuntu Server 22.04.1 LTS
```
open-vm-tools/jammy-updates,jammy-security,now 2:11.3.5-1ubuntu4.1 amd64 [installed,automatic]
```

Ubuntu Server 20.04.5 LTS
```
open-vm-tools/focal-updates,focal-security,now 2:11.3.0-2ubuntu0~ubuntu20.04.3 amd64 [installed]
```

Ubuntu Server 18.04.6 LTS
```
open-vm-tools/bionic-updates,bionic-security,now 2:11.0.5-4ubuntu0.18.04.2 amd64 [installed]
```

LHammonds

---

