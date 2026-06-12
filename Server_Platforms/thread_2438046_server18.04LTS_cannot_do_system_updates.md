---
title: "server18.04LTS cannot do system updates"
date: 2020-03-04
forum: Server Platforms
---

### Post by Heeter on 2020-03-04
Hi all,

Trying to do security updates to a Ubuntu18.04LTS server. Only servers running on this server is KVM & SSH

Keep getting these errors

```

root@serv:/home/adminpc# apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 linux-headers-generic : Depends: linux-headers-4.15.0-88-generic but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
root@serv:/home/adminpc# apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.15.0-70 linux-headers-4.15.0-70-generic linux-image-4.15.0-70-generic
  linux-modules-4.15.0-70-generic linux-modules-extra-4.15.0-70-generic
Use 'apt autoremove' to remove them.
The following additional packages will be installed:
  linux-headers-4.15.0-88-generic
The following NEW packages will be installed:
  linux-headers-4.15.0-88-generic
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
42 not fully installed or removed.
Need to get 0 B/1,127 kB of archives.
After this operation, 13.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
(Reading database ... 221243 files and directories currently installed.)
Preparing to unpack .../linux-headers-4.15.0-88-generic_4.15.0-88.88_amd64.deb ...
Unpacking linux-headers-4.15.0-88-generic (4.15.0-88.88) ...
dpkg: error processing archive /var/cache/apt/archives/linux-headers-4.15.0-88-generic_4.15.0-88.88_amd64.deb (--unpack):
 error creating directory './usr/src/linux-headers-4.15.0-88-generic/include/config/mfd/ti/am335x': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-4.15.0-88-generic_4.15.0-88.88_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@serv:/home/adminpc# 

```

I do have room on the disk:

```

root@serv:/home/adminpc# df -h
Filesystem                  Size  Used Avail Use% Mounted on
udev                         48G     0   48G   0% /dev
tmpfs                       9.5G  1.3M  9.5G   1% /run
/dev/mapper/LVG-root        2.0G  1.6G  288M  85% /
/dev/mapper/LVG-usr         3.0G  1.9G  963M  67% /usr
tmpfs                        48G     0   48G   0% /dev/shm
tmpfs                       5.0M     0  5.0M   0% /run/lock
tmpfs                        48G     0   48G   0% /sys/fs/cgroup
/dev/mapper/LVG-tmp         984M  2.8M  932M   1% /tmp
/dev/sda1                   1.9G  294M  1.5G  17% /boot
/dev/mapper/LVG-opt          51G   20G   29G  41% /opt
/dev/mapper/LVG-bak         2.9G  3.1M  2.8G   1% /bak
/dev/mapper/LVG-srv         989M  2.7M  939M   1% /srv
/dev/mapper/LVG-home        481M  2.3M  453M   1% /home
/dev/mapper/LVG-var         2.0G  1.2G  652M  66% /var
/dev/mapper/LVG-isostorage  4.9G  920M  3.7G  20% /var/isostorage
/dev/mapper/LVG-vmstorage   167G  150G  8.1G  95% /var/vmstorage
/dev/mapper/LVG-vmbackup    137G  112G   18G  87% /var/vmbackup
tmpfs                       9.5G     0  9.5G   0% /run/user/1000
root@serv:/home/adminpc# 

```

If anyone can assist me that would be greatly appreciated

Regards

---

### Post by guiverc on 2020-03-04
Check you have inodes free, ie. `df -hi`

If you've created loads of tiny little files, you may have used them up.. and new files cannot be created until some of those tiny files are removed.  ([http://manpages.ubuntu.com/manpages/bionic/man7/inode.7.html](http://manpages.ubuntu.com/manpages/bionic/man7/inode.7.html))

---

### Post by Heeter on 2020-03-04
Thank you for your quick response

Here is the result:
```

root@serv:/home/adminpc# df -hi
Filesystem                 Inodes IUsed IFree IUse% Mounted on
udev                          12M   563   12M    1% /dev
tmpfs                         12M   998   12M    1% /run
/dev/mapper/LVG-root         127K   36K   92K   29% /
/dev/mapper/LVG-usr          191K  186K  5.3K   98% /usr
tmpfs                         12M     1   12M    1% /dev/shm
tmpfs                         12M     4   12M    1% /run/lock
tmpfs                         12M    18   12M    1% /sys/fs/cgroup
/dev/mapper/LVG-tmp          254K    19  254K    1% /tmp
/dev/sda1                    120K   324  119K    1% /boot
/dev/mapper/LVG-opt           13M    13   13M    1% /opt
/dev/mapper/LVG-bak          762K    11  762K    1% /bak
/dev/mapper/LVG-srv          251K    11  251K    1% /srv
/dev/mapper/LVG-home         124K    25  124K    1% /home
/dev/mapper/LVG-var          127K  4.6K  123K    4% /var
/dev/mapper/LVG-isostorage   320K    12  320K    1% /var/isostorage
/dev/mapper/LVG-vmstorage     11M    12   11M    1% /var/vmstorage
/dev/mapper/LVG-vmbackup     8.8M    13  8.8M    1% /var/vmbackup
tmpfs                         12M    11   12M    1% /run/user/1000
root@serv:/home/adminpc# 

```

---

### Post by volkswagner on 2020-03-05
I think /usr is a bit undersized or you should try manually removing old kernels.
Operating at 85% capacity on root is a bit full as well. I believe anything
over 80% should be addressed.

I realized the package manager says
"After this operation, 13.1 MB of additional disk space will be used"
but I don't think that's accurate for what needs to be added to /usr
to fix kernels.

```
Filesystem                  Size  Used Avail Use% Mounted on
/dev/mapper/LVG-root        2.0G  1.6G  288M  85% /
/dev/mapper/LVG-usr         3.0G  1.9G  963M  67% /usr
```

As you can see from your last post, /usr is an issue.
```
root@serv:/home/adminpc# df -hi
Filesystem                 Inodes IUsed IFree IUse% Mounted on
/dev/mapper/LVG-usr          191K  186K  5.3K   98% /usr
```


[See how many unused kernels you can remove]("https://askubuntu.com/questions/668582/false-disk-full-error-apt-get-unable-to-install-or-remove").

```
dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+' | grep -Fv $(uname -r)
```

---

### Post by Heeter on 2020-03-08
Hey, volkswagner, thank you for pointing that out.

I couldn't do anything because the partition was full, so I increased the LVM-usr from 6gigs to 10gigs

Now the autoremove is working properly to remove the extra kernels

Thank you for that.

Regards

---

