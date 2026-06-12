---
title: "LVM or No on a headless KVM install"
date: 2019-11-01
forum: Server Platforms
---

### Post by Heeter on 2019-11-01
Hi all,

Having a couple of issues with a fresh new bare metal install of Ubuntu18.4.3 with only KVM and SSH installed. I installed using "Use Entire Disk with LVM" option.

My intention is to run 2 virtual servers, both 18.4.3 as well.

My first issue is that I see this when I first logon using SSH:

```

Welcome to Ubuntu 18.04.3 LTS (GNU/Linux 4.15.0-66-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

  System information as of Sat Nov  2 01:10:02 UTC 2019

  System load:     0.28              IP address for eno1:   192.168.1.11
  ***_Usage of /:      99.3% of 3.87GB _***  IP address for eno2:   192.168.1.12
  Memory usage:    0%                IP address for eno3:   192.168.1.13
  Swap usage:      0%                IP address for eno4:   192.168.1.14
  Processes:       305               IP address for virbr0: 192.168.122.1
  Users logged in: 0

  ***_=> / is using 99.3% of 3.87GB_***

 * Kata Containers are now fully integrated in Charmed Kubernetes 1.16!
   Yes, charms take the Krazy out of K8s Kata Kluster Konstruction.

     https://ubuntu.com/kubernetes/docs/release-notes

0 packages can be updated.
0 updates are security updates.

```

since this server has a total physical disk space of just under 2TB (6x600gigs in a RAID10 configuration), I am trying to figure out why the / folder is max'd out?

Second:
```


root@server:/home/vmserv# kvm-ok
INFO: /dev/kvm exists
KVM acceleration can be used

root@server:/home/vmserv# virt-install --name mail --ram=8000 --vcpus=4 --cpu host --hvm --disk path=/var/lib/libvirt/images/ubuntu-18.04.3-vm1,size=250 --cdrom /var/lib/libvirt/boot/ubuntu-18.04.3-live-server-amd64.iso --graphics vnc

Traceback (most recent call last):
  File "/usr/lib/python2.7/logging/__init__.py", line 892, in emit
    self.flush()
  File "/usr/lib/python2.7/logging/__init__.py", line 852, in flush
    self.stream.flush()
IOError: [Errno 28] No space left on device
Logged from file cli.py, line 265
Traceback (most recent call last):
  File "/usr/lib/python2.7/logging/__init__.py", line 892, in emit
    self.flush()
  File "/usr/lib/python2.7/logging/__init__.py", line 852, in flush
    self.stream.flush()
IOError: [Errno 28] No space left on device
Logged from file cli.py, line 279
Traceback (most recent call last):
  File "/usr/lib/python2.7/logging/__init__.py", line 892, in emit
    self.flush()
  File "/usr/lib/python2.7/logging/__init__.py", line 852, in flush
    self.stream.flush()
IOError: [Errno 28] No space left on device
Logged from file cli.py, line 282
Traceback (most recent call last):
  File "/usr/lib/python2.7/logging/__init__.py", line 892, in emit
    self.flush()
  File "/usr/lib/python2.7/logging/__init__.py", line 852, in flush
    self.stream.flush()
IOError: [Errno 28] No space left on device
Logged from file virt-install, line 358
Traceback (most recent call last):
  File "/usr/lib/python2.7/logging/__init__.py", line 892, in emit
    self.flush()
  File "/usr/lib/python2.7/logging/__init__.py", line 852, in flush
    self.stream.flush()
IOError: [Errno 28] No space left on device
Logged from file cli.py, line 317
Traceback (most recent call last):
  File "/usr/lib/python2.7/logging/__init__.py", line 892, in emit
    self.flush()
  File "/usr/lib/python2.7/logging/__init__.py", line 852, in flush
    self.stream.flush()
IOError: [Errno 28] No space left on device
Logged from file cli.py, line 318
ERROR    Host does not support virtualization type 'hvm' 
Traceback (most recent call last):
  File "/usr/lib/python2.7/logging/__init__.py", line 892, in emit
    self.flush()
  File "/usr/lib/python2.7/logging/__init__.py", line 852, in flush
    self.stream.flush()
IOError: [Errno 28] No space left on device
Logged from file cli.py, line 320


```

```

root@server:/home/vmserv# df
Filesystem                        1K-blocks    Used Available Use% Mounted on
udev                               49461204       0  49461204   0% /dev
tmpfs                               9898472    9588   9888884   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv   4062912 4046532         0 100% /
tmpfs                              49492360       0  49492360   0% /dev/shm
tmpfs                                  5120       0      5120   0% /run/lock
tmpfs                              49492360       0  49492360   0% /sys/fs/cgroup
/dev/loop0                            90624   90624         0 100% /snap/core/7270
/dev/loop1                            91264   91264         0 100% /snap/core/7917
/dev/sda2                            999320  146284    784224  16% /boot
tmpfs                               9898472       0   9898472   0% /run/user/1000

```

Don't understand why it is complaining that it doesn't have enough disk space. and that it doesn't support hvm acceleration.

Could it be because of the LVM install instead of just just using regular "Entire Disk" option during the base Ubuntu install?

Could someone propose a better partitioning option?

Regards

---

### Post by TheFu on 2019-11-01
Looks like LVM isn't fully allocating storage, which is excellent!  You want this.

You are out of space. 
```
/dev/mapper/ubuntu--vg-ubuntu--lv   4062912 4046532         **0** 100% /
```
There isn't anywhere for a new VM to go based on the command used.
I would bet that /var/lib/libvirt/boot/ubuntu-18.04.3-live-server-amd64.iso isn't the complete ISO too, assuming you attempted to place it in that location.

If you will post the output from these commands:
```
lsblk
sudo pvs
sudo vgs
sudo lvs
```
then we will have a better idea for what is really happening.

I always use LVM on physical installations because it is crazy flexible, but it does require some understanding to take advantage of that flexibility.

Chances are, the first thing you'll want to do is to resize / to be 15-25G in size.
If you will be using libvirt and virt-manager to manage the VMs and the VM storage, then you can tell libvirt to create an LV for each VM. There are many reasons to do this - better performance, snapshots for backups, easier storage management, etc.  For example:
```
$ lsblk  -o name,size,type,fstype,mountpoint
NAME                                SIZE TYPE FSTYPE      MOUNTPOINT
sdb                                 477G disk             
&#9500;&#9472;sdb2                                1K part             
&#9500;&#9472;sdb5                            476.2G part LVM2_member 
&#9474; &#9500;&#9472;hadar--vg-swap_1                976M lvm  swap        [SWAP]
&#9474; &#9500;&#9472;hadar--vg-root                 22.3G lvm  ext4        /
&#9474; &#9500;&#9472;hadar--vg-libvirt--lv           200G lvm  ext4        /var/lib/libvirt
&#9474; &#9500;&#9472;hadar--vg-lv--zcs45--1604        25G lvm              
&#9474; &#9500;&#9472;hadar--vg-lv--lubuntu11--1604    31G lvm              
&#9474; &#9500;&#9472;hadar--vg-lv--xen41--1604      12.5G lvm              
&#9474; &#9500;&#9472;hadar--vg-lv--srv--1910          10G lvm              
&#9474; &#9500;&#9472;hadar--vg-test--1804             10G lvm              
&#9474; &#9500;&#9472;hadar--vg-lv--spam61--1604        7G lvm              
&#9474; &#9500;&#9472;hadar--vg-lv--blog44--1604     16.2G lvm              
&#9474; &#9492;&#9472;hadar--vg-lv--vpn09--1604       7.5G lvm              

```
All those 'lvm' allocations that don't have mount points, those are each virtual machines with the block device presented to the VM for management.  Most are servers which I know will never need all that much storage.

Increasing storage is really easy in LVM.

---

### Post by Heeter on 2019-11-01
Great, Thank you for your response, There is hope for me then!!!!

```

root@server:/home/vmserv# lsblk
NAME                      MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
loop0                       7:0    0 88.5M  1 loop /snap/core/7270
loop1                       7:1    0 89.1M  1 loop /snap/core/7917
sda                         8:0    0  1.7T  0 disk 
&#9500;&#9472;sda1                      8:1    0    1M  0 part 
&#9500;&#9472;sda2                      8:2    0    1G  0 part /boot
&#9492;&#9472;sda3                      8:3    0  1.7T  0 part 
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0    4G  0 lvm  /
sr0                        11:0    1 1024M  0 rom  

```

```

root@server:/home/vmserv# sudo pvs
  PV         VG        Fmt  Attr PSize PFree
  /dev/sda3  ubuntu-vg lvm2 a--  1.63t 1.63t

```

```

root@server:/home/vmserv# sudo vgs
  VG        #PV #LV #SN Attr   VSize VFree
  ubuntu-vg   1   1   0 wz--n- 1.63t 1.63t

```

```

root@server:/home/vmserv# sudo lvs
  LV             VG               Attr           LSize Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv   ubuntu-vg   -wi-ao---- 4.00g                                                    

```

First, how do I resize the / folder?

Thank you

---

### Post by TheFu on 2019-11-01
**lvresize**
You'll need to read the manpage for all the options.  If you don't use the  --resizefs option, then you'll need 2 commands - lvresize AND resize2fs.  Easier to let the --resizefs option to lvresize handle that part, IMHO.

Be certain you review the command outputs above and understand the relationship between the LVs, VGs, and PVs.  Before too long, it would be smart to make a VM with LVM inside it, then play around with adding, removing, migrating, mirroring, snapshots, backups, all using LVM.

If you are going to be running servers, best to get into manpages. Everything is documented there.
[https://www.howtoforge.com/linux_lvm](https://www.howtoforge.com/linux_lvm) wouldn't be a bad intro either.  LVM commands have been pretty stable for 15+ yrs. There aren't any GUI tools for this that can be trusted, so don't bother looking.

BTW, I wouldn't use virt-install unless you absolutely need to create 10+ VMs a month following specific settings.  Run **virt-manager** on your Linux desktop and connect to the KVM hypervisor using it (via libvirt) over ssh.  It makes all sorts of things really easy.

You can disable the Canonical advertising messages at login in the /etc/default/motd-news file.

---

### Post by Heeter on 2019-11-01
Ok I will go there and learn more about LVM

Thank you for your assistance so far

---

