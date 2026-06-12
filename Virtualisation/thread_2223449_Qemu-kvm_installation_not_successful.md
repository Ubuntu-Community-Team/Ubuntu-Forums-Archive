---
title: "Qemu-kvm installation not successful"
date: 2014-05-11
forum: Virtualisation
---

### Post by ridah2 on 2014-05-11
Hi all,
i recently installed ubuntu 14 . Currently i am facing problem in installing qemu-kvm
```

:~$ sudo apt-get install qemu-kvm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 qemu-kvm : Depends: qemu-system-x86 (>= 1.7.0+dfsg-2~) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

and when i try to do this
```

~$ sudo apt-get install qemu-system-x86 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 qemu-system-x86 : Depends: libaio1 (>= 0.3.93) but it is not installable
                   Depends: libfdt1 but it is not installable
                   Depends: librados2 but it is not installable
                   Depends: librbd1 but it is not installable
                   Depends: libsdl1.2debian (>= 1.2.11) but it is not installable
                   Depends: libseccomp2 (>= 0.0.0~20120605) but it is not installable
                   Depends: libspice-server1 (>= 0.12.4) but it is not installable
                   Depends: libusbredirparser1 (>= 0.6) but it is not installable
                   Depends: libxen-4.4 (>= 4.4.0) but it is not installable
                   Depends: libxenstore3.0 (>= 4.1.0~rc6) but it is not installable
                   Depends: seabios (>= 1.7.2-2~) but it is not installable
                   Depends: ipxe-qemu but it is not installable
                   Recommends: qemu-utils but it is not going to be installed
                   Recommends: cpu-checker but it is not installable
E: Unable to correct problems, you have held broken packages.

```
I donot want to meet the dependencies manualy. kindly provide the solution. Also i followed this , but the problem is still there
[http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies](http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies)

Any help would be much appreciated.

---

### Post by sudodus on 2014-05-11
Welcome to the Ubuntu Forums :-)

It works for me in Lubuntu 13.10 64-bits to install and run KVM according to this link

[https://help.ubuntu.com/community/KVM/VirtManager](https://help.ubuntu.com/community/KVM/VirtManager)

I have not yet tried it in 14.04 LTS.

---

### Post by matt_symes on 2014-05-11
Hi

Can we take a look at your sources please.

Open a terminal and type

```
grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
```

Please post the output back here.

Kind regards

---

### Post by ridah2 on 2014-05-11
thankyou for your help. Here is the  output
```

:~$ sudo grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
[sudo] password for ridah: 
/etc/apt/sources.list:5:deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty main restricted
/etc/apt/sources.list:6:deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty main restricted
/etc/apt/sources.list:10:deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
/etc/apt/sources.list:11:deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-updates main restricted
/etc/apt/sources.list:16:deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty universe
/etc/apt/sources.list:17:deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty universe
/etc/apt/sources.list:18:deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-updates universe
/etc/apt/sources.list:19:deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-updates universe
/etc/apt/sources.list:26:deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty multiverse
/etc/apt/sources.list:27:deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty multiverse
/etc/apt/sources.list:28:deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
/etc/apt/sources.list:29:deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-updates multiverse
/etc/apt/sources.list:36:deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
/etc/apt/sources.list:37:deb-src [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
/etc/apt/sources.list:39:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
/etc/apt/sources.list:40:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
/etc/apt/sources.list:41:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
/etc/apt/sources.list:42:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
/etc/apt/sources.list:43:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
/etc/apt/sources.list:44:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
/etc/apt/sources.list:50:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
/etc/apt/sources.list:51:deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
/etc/apt/sources.list:55:deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
/etc/apt/sources.list:56:deb [http://pk.archive.ubuntu.com/ubuntu/](http://pk.archive.ubuntu.com/ubuntu/) trusty-proposed universe multiverse restricted main
/etc/apt/sources.list:57:deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
grep: /etc/apt/sources.list.d/*: No such file or directory
```

---

### Post by matt_symes on 2014-05-11
Hi

> grep: /etc/apt/sources.list.d/*: No such file or directory
Do you really not have this directory ?

Can you post the output from these commands as well please.

```
cat /etc/lsb-release
```

```
ls -l /etc/apt/sources.list.d/
```

```
cat /etc/apt/sources.list.d/*
```

I'm looking to see if you have a missed place source file. I'll have a look at the ones you posted in a moment.

Have you installed anything in an unusual way ? Say from a deb file ?

Kind regards

---

### Post by TheFu on 2014-05-12
Perhaps this is a dumb question, but is the system 100% patched and current?
[B]sudo aptitude update
sudo aptitude upgrade[/B]
was run recently?

I have installed KVM on 14.04 recently. It worked here. Gave a presentation on it at the local LUGs too.
```
sudo aptitude install openssh-server virt-manager    kvm qemu-system    bridge-utils fail2ban

``` was it.

Aptitude tends to be a little smarter about resolving dependencies. If a raw .deb package was installed, it can be interfering with repository dependencies.

---

### Post by ridah2 on 2014-05-12
Thankyou for replying. I installed ubuntu 12 but had same dependencies issues. I thought it could be a version problem but the problem is persistent. I guess ia m doing smething wrong.

Here are the outputs

:~$ sudo cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04 LTS"


:~$ sudo ls -l /etc/apt/sources.list.d/
total 0

~$ sudo cat /etc/apt/sources.list.d/*
cat: /etc/apt/sources.list.d/*: No such file or directory

---

### Post by ridah2 on 2014-05-12
Also i havent installed anything unusually... not from a deb file

---

### Post by sandyd on 2014-05-12
Try running
```

sudo sed -i s/pk.archive.ubuntu.com/archive.ubuntu.com/ /etc/apt/sources.list
sudo apt-get update
```
Ive noticed that some country mirrors are out of date, and will produce odd errors such as this one.

---

### Post by ridah2 on 2014-05-12
Sandyd,

It worked like a charm!!!   God bless you. :)

However if you could guide me on this matter, it would a great help.
$ sudo grep -n "^[^#]" /etc/apt/sources.list{,.d/*}
[sudo] password for ridah: 
/etc/apt/sources.list:5:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty main restricted
/etc/apt/sources.list:6:deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty main restricted
/etc/apt/sources.list:10:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates main restricted
/etc/apt/sources.list:11:deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates main restricted
/etc/apt/sources.list:16:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty universe
/etc/apt/sources.list:17:deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty universe
/etc/apt/sources.list:18:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates universe
/etc/apt/sources.list:19:deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates universe
/etc/apt/sources.list:26:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty multiverse
/etc/apt/sources.list:27:deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty multiverse
/etc/apt/sources.list:28:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates multiverse
/etc/apt/sources.list:29:deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates multiverse
/etc/apt/sources.list:36:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
/etc/apt/sources.list:37:deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-backports main restricted universe multiverse
/etc/apt/sources.list:39:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
/etc/apt/sources.list:40:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security main restricted
/etc/apt/sources.list:41:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
/etc/apt/sources.list:42:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security universe
/etc/apt/sources.list:43:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
/etc/apt/sources.list:44:deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) trusty-security multiverse
/etc/apt/sources.list:50:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
/etc/apt/sources.list:51:deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) trusty partner
/etc/apt/sources.list:55:deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
/etc/apt/sources.list:56:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-proposed universe multiverse restricted main
/etc/apt/sources.list:57:deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
grep: /etc/apt/sources.list.d/*: No such file or directory

---

### Post by sandyd on 2014-05-13
The above looks fine - can you install qemu-kvm/virt-manager now?

---

### Post by matt_symes on 2014-05-13
Hi

Good call sandyd.

Stale repos. Must remember to consider and check for that in the future.
> 
However if you could guide me on this matter, it would a great help.
$ sudo grep -n "^[^#]" /etc/apt/sources.list{,.d/*}

That looks fine. 

You do have the directory /etc/apt/sources.list.d/ you just have nothing in it. I misinterpreted the error message.

Kind regards

---

