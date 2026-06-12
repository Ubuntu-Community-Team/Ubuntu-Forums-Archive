---
title: "ubuntu 9.10 can't install"
date: 2009-09-05
forum: Virtualisation
---

### Post by linuxwl on 2009-09-05
I want install karmic-desktop-amd64 in vmware 6.5. 
After I chose Install ubuntu, then get a error:
PANIC:early exception 0e rip 10:ffffffff8185a794 error 0 cr2 fffffffef44003d.

---

### Post by dk06 on 2009-09-05
> **linuxwl said:**
> I want install karmic-desktop-amd64 in vmware 6.5. 
After I chose Install ubuntu, then get a error:
PANIC:early exception 0e rip 10:ffffffff8185a794 error 0 cr2 fffffffef44003d.


Try a Generic Linux 2.6 kernel as your OS type (when you create the Virtual Disk) & maybe check the integrity of the ISO...sometimes VMware freaks out when you boot a new system if the settings aren't correct and I'm not sure how different 9.10 is from the rest but maybe best to use a generic kernel and give it some more RAM...like more than 512

---

### Post by linuxwl on 2009-09-05
> **dk06 said:**
> Try a Generic Linux 2.6 kernel as your OS type (when you create the Virtual Disk) & maybe check the integrity of the ISO...sometimes VMware freaks out when you boot a new system if the settings aren't correct and I'm not sure how different 9.10 is from the rest but maybe best to use a generic kernel and give it some more RAM...like more than 512
**I **have tried to use linux 2.6xkeinel /ubuntu 64 bit/linux 64bit & 980M RAM,using Physical Disk(I want to install it as a independent OS,that is I can boot it from disk,I always install OS like that & never Failure )&#12290;
Starting vmare,booting from cd ,then chose language, All options will get the same  error except “Boot from first hard disk"

This error looks like a error about CPU,my cpu is amd5000+.

---

### Post by dk06 on 2009-09-08
> **linuxwl said:**
> 
I want install karmic-desktop-amd64 in vmware 6.5. 
After I chose Install ubuntu, then get a error:
PANIC:early exception 0e rip 10:ffffffff8185a794 error 0 cr2 fffffffef44003d.

**I **have tried to use linux 2.6xkeinel /ubuntu 64 bit/linux 64bit & 980M RAM,using Physical Disk(I want to install it as a independent OS,that is I can boot it from disk,I always install OS like that & never Failure )&#12290;
Starting vmare,booting from cd ,then chose language, All options will get the same  error except &#8220;Boot from first hard disk"

This error looks like a error about CPU,my cpu is amd5000+.

What is your host OS (the one with vmware installed on it) and is your host 32bit or 64 bit?

If your host OS is a 32bit, You may have better luck with the 32bit ubuntu karmic

Does the Live CD work on your PC without going through VMware....looks like you have a 64bit cpu so if it doesn't boot the Live CD it might be a problem with the integrity of the download/ISO. If so, maybe download a fresh one and check the MD5 (checksum)

Does VMware run other OSes? You can test the program with DSL (Damn Small Linux- 50mb download) [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)
If it runs DSL but not Ubuntu,  it could be many other things...do you have a log file for your vm guest?

---

### Post by Bucky Ball on 2009-09-08
Karmic is testing. Try 9.04 or better still 8.04 LTS. 9.10 hasn't even been released yet and I would give it six months after that. As a new user, 9.10 is the WRONG place to start.

---

### Post by linuxwl on 2009-09-10
Tkanks,I have upgrade from Ubuntu 9.04 Successful.

---

### Post by Bucky Ball on 2009-09-10
Like when a plan comes together. Enjoy. :)

---

