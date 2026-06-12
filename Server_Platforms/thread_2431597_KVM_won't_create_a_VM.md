---
title: "KVM won't create a VM"
date: 2019-11-19
forum: Server Platforms
---

### Post by Heeter on 2019-11-19
Hi all,

I am trying to create a VM for a nextcloud install. using Ubuntu18. This is on a fresh Ubuntu18 host install with LVM.

It just stays stuck at this:
```

root@serv:/etc/netplan# virt-install --name nextcloud --ram=10240 --vcpus=4 --cpu host --hvm --disk path=/var/vmstorage/nextcloud,size=99 --cdrom /var/isostorage/ubuntu-18.04.3-server-amd64.iso --graphics vnc
WARNING  Graphics requested but DISPLAY is not set. Not running virt-viewer.
WARNING  No console to launch for the guest, defaulting to --wait -1

Starting install...
Allocating 'nextcloud'                                                                                                                 |  99 GB  00:00:00     
Domain installation still in progress. Waiting for installation to complete.

```

I created an LVM partition for the vm's to be operating out of.
```

root@serv:/home/admin# lsblk
NAME               MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda                  8:0    0  1.7T  0 disk 
&#9500;&#9472;sda1               8:1    0  1.9G  0 part /boot
&#9500;&#9472;sda2               8:2    0    1K  0 part 
&#9492;&#9472;sda5               8:5    0  1.6T  0 part 
  &#9500;&#9472;LVG-root       253:0    0    4G  0 lvm  /
  &#9500;&#9472;LVG-usr        253:1    0    6G  0 lvm  /usr
  &#9500;&#9472;LVG-var        253:2    0    4G  0 lvm  /var
  &#9500;&#9472;LVG-tmp        253:3    0  3.5G  0 lvm  /tmp
  &#9500;&#9472;LVG-bak        253:4    0  7.5G  0 lvm  /bak
  &#9500;&#9472;LVG-srv        253:5    0  3.8G  0 lvm  /srv
  &#9500;&#9472;LVG-opt        253:6    0   32G  0 lvm  /opt
  &#9500;&#9472;LVG-home       253:7    0  1.8G  0 lvm  /home
  &#9500;&#9472;LVG-isostorage 253:8    0    5G  0 lvm  /var/isostorage
  &#9492;&#9472;LVG-vmstorage  253:9    0  150G  0 lvm  /var/vmstorage
sr0                 11:0    1 1024M  0 rom  
sr1                 11:1    1 1024M  0 rom  
root@serv:/home/admin# 

```

The virsh list is this:
```

root@serv:/home/admin# virsh list --all
 Id    Name                           State
----------------------------------------------------
 5     nextcloud                      running

root@serv:/home/admin#

```

I also try to create it in the virt-manager on my laptop, but it stays stuck the same way.

Can't figure out what I am missing.

---

### Post by Skaperen on 2019-11-19
are you doing this in a text-mode console?

---

### Post by Doug S on 2019-11-19
Did you attempt to connect to it via vnc as it expects? You should be able to continue from there.

Myself, and it has been awhile since I ever changed anything, I would have done this:

```

virt-install --name nextcloud --ram=10240 --vcpus=4 --cpu host --hvm --disk path=/var/vmstorage/nextcloud,size=99 --cdrom /var/isostorage/ubuntu-18.04.3-server-amd64.iso --video=vmvga --graphics vnc,listen=0.0.0.0 --noautoconsole

```

---

### Post by TheFu on 2019-11-19
virsh uses libvirtd.
virt-manager uses libvirtd.
I've never used virt-install, it also uses libvirtd.  
The userid using virsh or virt-manager needs to be in the libvirtd group and that group needs to be active. Either newgrp or logout+login are necessary to get the group active.

Use **virsh dumpxml {vm-name}** to see the settings .... or use virt-manager from a GUI-workstation.  You can manually define the VM settings using **virsh define {vm-name}.xml ** if you want to manually edit XML.  I just use virt-manager from a workstation over an ssh+qemu connection defined to the VM host from my workstation.

XML files are stored in /etc/libvirt/....
By default, file-based VMs are stored in /var/libvirt/qemu/images/ or you can use an LVM for each VM which is setup in the host.  virt-manager understand using an LV for each VM.  For example, from a VM host:```

&#9500;&#9472;sdb5                            476.2G part LVM2_member 
&#9474; &#9500;&#9472;hadar--vg-libvirt--lv           200G lvm  ext4        /var/lib/libvirt
&#9474; &#9500;&#9472;hadar--vg-root                 22.3G lvm  ext4        /
&#9474; &#9500;&#9472;hadar--vg-swap_1                2.3G lvm  swap        [SWAP]
&#9474; &#9500;&#9472;hadar--vg-lv--srv--1910          10G lvm              
&#9474; &#9500;&#9472;hadar--vg-lv--zcs45--1604        25G lvm              
&#9474; &#9500;&#9472;hadar--vg-lv--lubuntu11--1604    31G lvm              
&#9474; &#9500;&#9472;hadar--vg-lv--spam3              10G lvm              
&#9474; &#9500;&#9472;hadar--vg-test--1804             10G lvm              
&#9474; &#9500;&#9472;hadar--vg-lv--spam61--1604        7G lvm              
&#9474; &#9500;&#9472;hadar--vg-lv--blog44--1604     16.2G lvm              
&#9474; &#9492;&#9472;hadar--vg-lv--vpn09--1604       7.5G lvm
&#9492;&#9472;sdb1                              731M part ext2        /boot
```
Basically, my KVM setup provides block storage to each VM.  Notice how the LVM setup for the host is minimal, not all that complex?  Why add complexity if it isn't needed?  I did setup 200G for file-based VMs, but using LVM is so easy that I don't expect to ever use that.

Have complexity only where it is actually necessary.  KISS whenever possible.

As for how to setup servers, I don't do step-by-step, but I do *big picture* stuff.  
[https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server](https://blog.jdpfu.com/2014/02/28/1st-five-minutes-on-a-server)  Be consistent. Have a process that can be followed.  Think about security.

There are lots and lots of different methods for doing all these things.  Over time, you'll come to your own "best practices."

I've been running a nextcloud setup for the house for a few years.  It runs in a VM on a different system than above.
```
$ virsh dominfo nextcloud
Id:             1
Name:           nextcloud
UUID:           280b0e5b-9f2e-4968-8eb0-cdb35bfd6761
OS Type:        hvm
State:          running
**CPU(s):         1**
CPU time:       17437.8s
**Max memory:     1048576 KiB**
Used memory:    1048576 KiB
Persistent:     yes
Autostart:      enable
Managed save:   no
Security model: apparmor
Security DOI:   0
Security label: libvirt-280b0e5b-9f2e-4968-8eb0-cdb35bfd6761 (enforcing)

``` That same VM runs Wallabag and ZNC servers too.  1 vCPU and 1GB RAM allocated. Performance is quite acceptable on a $50 CPU for that system that also runs a number of other VMs and is the main NFS server here.  Perhaps your nextcloud deployment is bigger? 10GB of RAM seems huge to me, same for 4 vCPUs.

The virt-install manpage:
```
       --memory OPTIONS
           Memory to allocate for the guest, in MiB. Sub options are
           available, like 'maxmemory' and 'hugepages'. This deprecates the
           -r/--ram option.

           Use --memory=? to see a list of all available sub options. Complete
           details at
           <http://libvirt.org/formatdomain.html#elementsMemoryAllocation>

```

---

### Post by Doug S on 2019-11-19
> **TheFu said:**
> You can manually define the VM settings using **virsh define {vm-name}.xml ** if you want to manually edit XML.I use virsh edit to make changes to the .xml file afterwards. It will use the editor as defined by the $EDITOR environment variable, or VI if it does not exist. add export EDITOR="/bin/nano" to your ~/.bashrc file to set, for example, nano as your default editor. It can be done from any directory, example:
```
virsh edit serv64_dev
```

---

### Post by TheFu on 2019-11-19
I'd forgotten about the *edit* option. Generally the main times I use virsh is to dumpxml so a VM can be relocated to a different physical server.  Every once in a while, virsh edit would be handy for some advanced libvirt needs that virt-manager doesn't support yet, but that happens less and less with each new release.  

virt-manager gives VM managing from anywhere the GUI like virtualbox or VMware Workstation, but with the advanced controls over storage.  

Network setup is weak, but I do that all externally, manually. That became habit because in the late 2000s, doing it any other way made for terrible network performance. I've just never changed to even try to use the libvirtd NAT or bridge networking.  If it ain't broke, don't fix it. ;)

---

### Post by Heeter on 2019-11-19
Thank you all for your help,

> **Doug S said:**
> Did you attempt to connect to it via vnc as it expects? You should be able to continue from there.

Myself, and it has been awhile since I ever changed anything, I would have done this:

```

virt-install --name nextcloud --ram=10240 --vcpus=4 --cpu host --hvm --disk path=/var/vmstorage/nextcloud,size=99 --cdrom /var/isostorage/ubuntu-18.04.3-server-amd64.iso --video=vmvga --graphics vnc,listen=0.0.0.0 --noautoconsole

```

Thank you, that is exactly what I needed. The moment I dropped this command in, The install proceeded properly.

Regards

---

