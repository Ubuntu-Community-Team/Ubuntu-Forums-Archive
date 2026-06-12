---
title: "No virtual cdrom"
date: 2012-02-28
forum: Virtualisation
---

### Post by dam00000007 on 2012-02-28
Hello

I have a Alienware M11X running under Windows 7which doesn't have any physical cd/dvd drive.
I have installed a Wmware version of Ubuntu in the Wmware player.
Now I have to install Wmware Tools, which has been downloaded by Wmware player automatically.
When I press install, Wmware ask for a virtual drive, which apparently I don't have.

I found the procedure on Wmware website
```

mkdir /mnt/cdrom; mount /dev/cdrom  /mnt/cdrom
cp /mnt/cdrom/VMwareTools-<version>.tar.gz /tmp/
cd /tmp/
tar zxpf VMwareTools-<version>.tar.gz 
cd vmware-tools-distrib/
./vmware-install.pl

```

But after the first command I have:
```
mount: special device /dev/cdrom does not exist
```

I tried to do:
```
mkdir /dev/cdrom
mount /dev/cdrom /mnt/cdrom
mount: /dev/cdrom/ is not a block device
```

My question is, how to create a virtual drive under ubuntu or how to make /dev/cdroma block device in order to complete the installation of Vmware tools?

Regards

Dam

---

### Post by nothingspecial on 2012-03-01
*Thread moved to **Virtualization**.*

---

### Post by pcpbslack on 2012-05-17
I don't know if you solved this, but I found myself in the same situation in many occasions. 

Normally, you should check in the /var/log/syslog which device block has been assigned to the CDROM and then type in the console:
sudo /dev/sr0 /media/cdrom

/dev/sr0 was the assigned device block to the CDROM

---

