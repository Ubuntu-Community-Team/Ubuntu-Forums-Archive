---
title: "stand alone mysql for cloud use"
date: 2016-08-05
forum: Server Platforms
---

### Post by Vegan on 2016-08-05
Recently I upped a Ubuntu 16.04 virtual machine, I get 768MB of RAM and 20GB of storage, my old IBM PC300GL has 768MB of memory but the disk was limited to 128GB (Azure is not so tight with storage and the CPU is way faster than the old Pentium III-733)


sudu apt-get update
sudo apt-get upgrade
sudo apt-get install mysql-server

so my database is setup with a password, so I wanted to conjure some shell scripts so I can more easily make new database when I want to install a new web site etc

database and the vm are secured with good passwords

database is to be a pure cloud appliance

maybe i can mechanize the service more?

I am manually operating the VM with Putty now


I have a URL so I want to be able to add a site database so that CMS line WordPress or other package can then be given a database URL, user name and password for use, crude web form will do etc

---

### Post by Vegan on 2016-08-05
lets see where am i, added some storage so now the fun, trying to mount the disk

thoughts, was suspecting /dev/sdb etc

any way to scan disks?

sudo lshw -class disk

found it as dev/sdc

so now its partitioned a GPT

sudo mkfs -t ext4 /dev/sdc

I want to make MySQL use that disk for the databases there is 50GB of space allocated

so mount it as /data or maybe sneak it under the default mysql folder?

I have made /sql for the mount, so I need this to survive reboot

so what does Unbuntu need for this?

sudo ls /dev/disk/by-uuid/

where is the fstab located?

---

