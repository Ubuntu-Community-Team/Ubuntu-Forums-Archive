---
title: "[solved] unable to do-release-upgrade under virtual machine"
date: 2013-05-23
forum: Server Platforms
---

### Post by Nw01f on 2013-05-23
Hi,

When I try to run do-release-upgrade (from 12.10 to 13.04), the following message occurred.

$ sudo do-release-upgrade
[sudo] password for admin: 
Checking for a new Ubuntu release
Get:1 Upgrade tool signature [198 B]                                                      
Get:2 Upgrade tool [1,206 kB]                                                             
Fetched 1,206 kB in 0s (0 B/s)                                                            
authenticate 'raring.tar.gz' against 'raring.tar.gz.gpg' 
extracting 'raring.tar.gz'
Can not run the upgrade
The error message is 'No such file or directory'.

Someone said it is about the /tmp is not mount as exec but I have mounted it to be

$ mount
/dev/vda1 on / type ext4 (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
tmpfs on /tmp type tmpfs (rw)

$ uname -a
Linux ldap 3.5.0-30-generic #51-Ubuntu SMP Tue May 14 18:47:48 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

Anyone has an idea on this?

---

### Post by Nw01f on 2013-05-23
I think it is this bug?

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1176701](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1176701)

---

### Post by ibjsb4 on 2013-05-23
Have you tried a dist-upgrade first?  May clear it up.

```
sudo apt-get dist-upgrade
```

---

### Post by Nw01f on 2013-05-25
> **ibjsb4 said:**
> Have you tried a dist-upgrade first?  May clear it up.

```
sudo apt-get dist-upgrade
```

Yes, I have run it before do-release-upgrade but it doesn't help.

$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by ibjsb4 on 2013-05-25
One hit I got solved this problem by changing download servers.

/var/log/dist-upgrade/ any other clues there?

---

### Post by Nw01f on 2013-05-25
Thanks for your help, ibjsb4

I just resolved this problem.

I have to apt-get install python-apt

Strange that do-release-upgrade did not prompt for this in one VM but the other.

:popcorn:

---

### Post by ibjsb4 on 2013-05-25
Strange indeed

---

### Post by Vegan on 2013-05-25
I found it easier to make new virtual machines for each new release so that if something blows up, the old VM is still there

---

