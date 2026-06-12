---
title: "problems with virtualbox"
date: 2019-03-15
forum: Virtualisation
---

### Post by nataniel12 on 2019-03-15
i am new to Ubuntu, i am using Ubuntu 18.04 lts.

the problem i am having goes like this:

i install virtualbox, in my 128gb SD and i have a 1tb hard drive, i want to use my HDD to install all the virtual machines but vitualbox keep giving me this message : 
"   Cannot create the machine folder windows in the parent folder /media/user/B66C09026C08BF5D/virtual machine.

 Please check that the parent really exists and that you have permissions to create the machine folder.

"
i started looking online for a solution but i cant find the way to give virtualbox the permission to create the virtual machine in that HDD.
can anyone help me solve this problem?

---

### Post by QIII on 2019-03-15
Moved to **Virtualisation** for a better fit.

---

### Post by SeijiSensei on 2019-03-16
First possibility is that the HDD is formatted with NTFS which does not support all the Linux primitives.  If you're using this drive for the first time, reformat the partition you're using to ext4.  Suppose you're using /dev/sdb1 from the HDD. 
```

sudo umount -f /dev/sdb1
sudo mkfs -t ext4 /dev/sdb1

```

Second possibility is that you don't have full permissions to the filesystem. After formatting, run the command

```

sudo mount /dev/sdb1
cd /media/user/
chown -R user:user B66C09026C08BF5D
chmod -R 0755 B66C09026C08BF5D

```

Some months back I bought myself a 512G SSD. Loading a Windows virtual machine from the SSD is much more responsive than from the HDD. (Don't ask about loading VMs over the network!) I only have the one VM so I put it on the SSD.

---

### Post by nataniel12 on 2019-03-17
thx i finally made it work, had to convert format , update virtual box and then run virtualbox as root to get it to work

---

### Post by edstevens on 2019-03-25
> **nataniel12 said:**
> thx i finally made it work, had to convert format , update virtual box and then run virtualbox as root to get it to work

You should not have to run VBox as root.  In fact, any time you find that you have to run an app as root, you need to step back and reconsider your 'fix'.  And don't forget that as far as the OS (any OS) is concerned, vbox is just another application.

Your problem appears to have more to do with the proper installation of the application, so you might find better help at virtualbox.org.

---

