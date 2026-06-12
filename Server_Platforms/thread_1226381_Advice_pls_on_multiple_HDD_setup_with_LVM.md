---
title: "Advice pls on multiple HDD setup with LVM"
date: 2009-07-29
forum: Server Platforms
---

### Post by omichaels on 2009-07-29
I am building my first Linux server using Ubuntu 8.04 and would appreciate advice on best options for LVM config of the 3 IDE drives available for deployment (1 x 40GB, 2 x 125GB: sda, sdb, sdc respectively).

This box will serve all webapps in our small office network (<50 users), running VMware Server 2 host with Ubuntu 9.04 and Win2k3 guest OSs.

This implementation is using old retired equipment. This is being used to demonstrate proof of concept before purchasing new tin. 

This will be our first Linux implementation, and hence there is some trepidation due to the lack of experience in this environment.

This migration will also bring into existence a range of new apps for business use, so it is difficult to know what our data needs will potentially be. This is another reason why LVM seems the right approach.

Following is what I have mapped out for the HDD config:

Device and partitions
sda1 primary 150MB ext3 /boot
sda# logical 39GB lvm 
sdb1 primary 125GB lvm
sdc1 primary 125GB lvm

Logical volume groups and devices 
1. system-sda
    Logical volumes
    i   swap (3GB)
    ii  root (10GB)
    iii tmp (10GB)
    iv usr (15G)

2. data-sdb-sdc
    Logical volumes
    i   srv (50GB)
    ii  opt (5GB)
    iii var (50GB)
    iv home (10GB)

The rationale for the above is to separate system and static data from volatile/dynamic.

I would value some feedback and suggestions.

---

### Post by nutznboltz on 2009-07-29
*sda1 primary 150MB ext3 /boot*

A journal on /boot only serves to waste space.

It would be safer to have 200MB of space on /boot as well.

[FONT="Courier New"]sda1 primary 200MB ext2 /boot[/FONT]

---

### Post by omichaels on 2009-07-29
Thanks nutznboltz for the feedback. 

Good suggestion for /boot that I had not thought about. 

Does the allocation of the logical vols to vol groups seem appropriate to you? I have been wondering whether to:
1. move usr from sys-sda to data-sdb-sdc
2. create another swap on data-sdb-sdc

Opinions?

---

