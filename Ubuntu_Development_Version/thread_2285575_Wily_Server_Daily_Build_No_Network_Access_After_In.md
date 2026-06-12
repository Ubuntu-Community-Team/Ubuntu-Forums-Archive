---
title: "Wily Server Daily Build No Network Access After Install"
date: 2015-07-07
forum: Ubuntu Development Version
---

### Post by genesoo77072 on 2015-07-07
My first post to this forum so excuse any omissions.

I use the following command to obtain the Daily Server build 
zsync [http://cdimage.ubuntu.com/ubuntu-server/daily/pending/wily-server-amd64.iso.zsync](http://cdimage.ubuntu.com/ubuntu-server/daily/pending/wily-server-amd64.iso.zsync) -o ...(target iso file)

In the past several days, I cannot do anything with this build and have determined that the problem is that after the installation completes and the system reboots, I have no network access.
I am performing this installation under VirtualBox and get consistent results on both Ubuntu(Desktop Server) and Windows 7(Laptop) hosts.

When I ping 8.8.8.8, I get the message Network is unreachable.

I went back and installed Ubuntu Server 15.04 and the ping command works.

---

### Post by Doug S on 2015-07-07
Hi, and welcome to Ubuntu forums.

I downloaded the 64 bit server daily ISO via the [testing tracker]("http://iso.qa.ubuntu.com/") page (which I can not seem to access at the moment). I installed it as a libvirt/qemu/kvm type virtual machine quest where Ubuntu server 14.04.2 LTS is the host. It seems to be working fine for network access. ISO details:```
-rw-rwxr--+ 1 libvirt-qemu kvm   654311424 Jul  7 07:13 wily-server-20150707-amd64.iso
```

Edit: My md5sum agrees with [here]("http://cdimage.ubuntu.com/ubuntu-server/daily/current/MD5SUMS") and [here]("http://cdimage.ubuntu.com/ubuntu-server/daily/pending/MD5SUMS") ```
doug@s15:~/iso$ [COLOR=#ff0000]md5sum wily-server-20150707-amd64.iso[/COLOR]
4902796b8018fe640f908175aaad9975  wily-server-20150707-amd64.iso
```

---

### Post by slickymaster on 2015-07-07
IS is upgrading the servers for some of the domains under *[.qa.ubuntu.com]("http://qa.ubuntu.com/"). The process should be quick, but some downtime may be experienced for these sites today.

---

### Post by genesoo77072 on 2015-07-09
> **Doug S said:**
> Hi, and welcome to Ubuntu forums.

I downloaded the 64 bit server daily ISO via the [testing tracker]("http://iso.qa.ubuntu.com/") page (which I can not seem to access at the moment). I installed it as a libvirt/qemu/kvm type virtual machine quest where Ubuntu server 14.04.2 LTS is the host. It seems to be working fine for network access. ISO details:```
-rw-rwxr--+ 1 libvirt-qemu kvm   654311424 Jul  7 07:13 wily-server-20150707-amd64.iso
```

Edit: My md5sum agrees with [here]("http://cdimage.ubuntu.com/ubuntu-server/daily/current/MD5SUMS") and [here]("http://cdimage.ubuntu.com/ubuntu-server/daily/pending/MD5SUMS") ```
doug@s15:~/iso$ [COLOR=#ff0000]md5sum wily-server-20150707-amd64.iso[/COLOR]
4902796b8018fe640f908175aaad9975  wily-server-20150707-amd64.iso
```

Specifically downloaded this 7/7 drop and also the 7/8 drop. Results were the same. In order to proceed further with this, I need to clear an HD and perform a Native install eliminating Virtual Box. It will take a day or two to complete this task.

---

### Post by genesoo77072 on 2015-07-11
I was able to do a Native install without virtualization and the current build from 7/10 does enable networking. What I conclude is that the current Wily Server Build does not recognize the Virtualbox NIC and the post install boot is left without networking. If I can supply any further details, please advise however. I run the currently available levels of Virtual Box on both Ubuntu and Windows.

---

### Post by genesoo77072 on 2015-07-16
Just downloaded the 7/15 drop and it looks like the networking problem has been addressed. Thanks to the team for addressing this issue.

---

