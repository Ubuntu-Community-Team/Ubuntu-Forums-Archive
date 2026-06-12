---
title: "Migrating LVM-based KVM - issue with sudo"
date: 2017-01-04
forum: Virtualisation
---

### Post by Darren_Landrum on 2017-01-04
Hello!

I have two kvm hypervisor servers. One is an older machine, the other is a newer, much faster and bigger machine. I spent some time creating two servers on the older machine, and now I want to migrate them to the new one.

I have a third test VM which I tried to migrate first. I created the logical volume for it, and moved it with the migrate tool in Virtual Machine Manager (which is running on an Ubuntu desktop machine at my desk). So far, so good. I was able to SSH into the VM on the new host. Again, so far, so good.

Then I ran into the weirdest problem ever.

```
user@mytestvm91:/$ sudo apt update
-bash: /usr/bin/sudo: cannot execute binary file: Exec format error

```

This worked just fine on the old host. I have no idea where to begin, or if I'm going to have this issue with all of my virtual servers. Googling the problem says that it's an architectural mismatch, for example, trying to run an ARM executable on an Intel. Both of my physical servers are Intel, but different generations.

Commands like ls and cd still work fine. I just can't do anything as root. Does this have to do with the different underlying servers? I kinda thought the big benefit of KVM was to be able to go between different servers like this.

Thank you all for the help!

PS: file seems to have the same issue:

```
user@mytestvm91:/$ file sudo
-bash: /usr/bin/file: cannot execute binary file: Exec format error

```

More info: I decided to try a hard reboot from the hypervisor. Now it will not boot at all. It says the hard disk is not a bootable device. If this is because of the difference in arch between the old host server and the new, I'm in for a very rough ride.

---

### Post by KillerKelvUK on 2017-01-04
Anything different with the qemu binaries used between hosts to run the guests?

---

### Post by Darren_Landrum on 2017-01-04
```
user@oldvmhost:~$ dpkg -s qemu-kvm | grep Version
Version: 1:2.5+dfsg-5ubuntu10.6
```

The version on the new host is exactly the same. Both hosts are running Ubuntu Server 16.04 64-bit and both are up to date as of about two weeks ago.

---

### Post by Darren_Landrum on 2017-01-05
Okay, one night's sleep, a new day, and I decided to try the offline approach of:

1) Shut off VM
2) Save image to backup server (using dd)
3) Export definition (virsh xmldump)
4) Create new volume on new server and restore backup (again using dd)
5) Import VM definition using virsh define
6) Profit!

Lo and behold, this appears to have worked. I started the VM on the new server, and it booted with no errors and I was able to log in and run sudo, apt, and a few other things. These virtual servers do not require five nines of uptime, so this method will be fine. It also has the advantage that the VM still exists on the old server if anything goes wrong.

I'll mark this thread as solved.

---

