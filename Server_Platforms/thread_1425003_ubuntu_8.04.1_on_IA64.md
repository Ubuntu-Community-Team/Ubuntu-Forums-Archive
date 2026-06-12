---
title: "ubuntu 8.04.1 on IA64"
date: 2010-03-08
forum: Server Platforms
---

### Post by FidalgoMike on 2010-03-08
Greetings,

I have v 8.04.1 with the Gnome desktop installed on an HP IA64 server. Some of the System/Administration menu tools won't open in the GUI: namely Network and Users and Groups. If anyone has any suggestions, they would be most appreciated.

Thanx,
Mike

---

### Post by cdenley on 2010-03-08
How do they fail? Is there an error message?
```

network-admin
users-admin
id

```

---

### Post by FidalgoMike on 2010-03-08
> **cdenley said:**
> How do they fail? Is there an error message?
```

network-admin
users-admin
id

```

Didn't think to try launching from the command line. In both cases, the tools displayed briefly, then closed with the error Segmentaion fault.

---

### Post by cdenley on 2010-03-08
You are doing this from the local console, correct?
```

id
dpkg -l|grep policykit
hostname
cat /etc/hosts

```

---

### Post by FidalgoMike on 2010-03-10
Yes, I'm at a local console thru a 4 port KVM. Haven't set up remote access stuff yet. The IA64 box gets an IP and network info from a DHCP server on my network.

Output from suggested commands:
miker@ubuntu-vm-host:~$ id
uid=1000(miker) gid=1000(miker) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),113(lpadmin),114(admin),1000(miker)
miker@ubuntu-vm-host:~$ dpgg -l | grep policykit
bash: dpgg: command not found
miker@ubuntu-vm-host:~$ clear
miker@ubuntu-vm-host:~$ id
uid=1000(miker) gid=1000(miker) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),113(lpadmin),114(admin),1000(miker)
miker@ubuntu-vm-host:~$ dpkg- l | grep policykit
bash: dpkg-: command not found
miker@ubuntu-vm-host:~$ sudo su
[sudo] password for miker: 
root@ubuntu-vm-host:/home/miker# dpkg -l | grep policykit
ii  policykit                                   0.7-2ubuntu7                              framework for managing administrative polici
ii  policykit-gnome                             0.7-2ubuntu1.1                            GNOME dialogs for PolicyKit
root@ubuntu-vm-host:/home/miker# hostname
ubuntu-vm-host
root@ubuntu-vm-host:/home/miker# cat /etc/hosts
127.0.0.1       localhost
127.0.1.1       ubuntu-vm-host.dyndns.org       ubuntu-vm-host

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by FidalgoMike on 2010-03-19
Hi there, can anybody help me with this issue?

Thanks

---

### Post by FidalgoMike on 2010-03-29
I've found the same segmentation fault error in the following gnome admin programs: network-admin, users-admin, time-admin, and services-admin. The machine is an HP rx2600 server, 10 GB Ram, IA 64 CPU. Ubuntu Server IA64 8.04.1 with Gnome desktop installed. Anyone have any ideas?

---

### Post by cdenley on 2010-03-29
> **FidalgoMike said:**
> I've found the same segmentation fault error in the following gnome admin programs: network-admin, users-admin, time-admin, and services-admin. The machine is an HP rx2600 server, 10 GB Ram, IA 64 CPU. Ubuntu Server IA64 8.04.1 with Gnome desktop installed. Anyone have any ideas?

You can try reinstalling anything related to policykit. Sounds like something is corrupted. You may want to check your memory and hard drive.

---

### Post by FidalgoMike on 2010-03-29
> **cdenley said:**
> You can try reinstalling anything related to policykit. Sounds like something is corrupted. You may want to check your memory and hard drive.
Re-installed all policykit items indicated in synaptic. . . no change. Am looking into seeing if I can run memtest86 on the IA64 platform.

---

