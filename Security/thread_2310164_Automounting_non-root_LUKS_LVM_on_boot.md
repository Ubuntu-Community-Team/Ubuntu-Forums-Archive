---
title: "Automounting non-root LUKS LVM on boot?"
date: 2016-01-16
forum: Security
---

### Post by Dáire Fagan on 2016-01-16
So using the following I made it so Ubuntu would not boot, although I was able to remedy this by booting into Ubutnu recovery, dropping to a root shell, and putting fstab back as it was: [HOWTO: Automatically unlock LUKS encrypted drives with a keyfile]("http://ubuntuforums.org/showthread.php?t=837416")

When I started I had just set up LUKS with LVM. I was able to mount the main volume hdd1 by clicking on it from the launcher in Ubuntu and entering my password, but I need to set it up to mount on boot.

Even after the change I made in fstab - undoing what the guide recommended - now when I boot a volume is mounted of 973GB although I cannot write to it. Apart from that I am not sure if it is otherwise working as it should, or if say for instance it is left decrypted all of the time.

 Can you please look through the commands from my bash history and tell me anything I need to undo, the correct commands to do this, and any extra commands I need to enter to achieve what I am after, physical volume sda1 decrypted on boot, and the logical volumes swap and hdd1 automatically mounted, one password input on boot preferred, so I do not have to enter one to login and another to decrypt. This is all on a completely separate drive to my / and /home partitions.

If relevant one of the commands used during LUKS and LVM setup was:

```
pvcreate /dev/mapper enc-pv
```

The logical volumes:

```
dusf@roadrunner:~$ sudo lvdisplay
  --- Logical volume ---
  LV Path                /dev/vg/swap
  LV Name                swap
  VG Name                vg
  LV UUID                HBEt92-E8MQ-aCAu-DBDz-7VeJ-KLom-JeJ9k8
  LV Write Access        read/write
  LV Creation host, time roadrunner, 2016-01-16 20:36:42 +0000
  LV Status              available
  # open                 0
  LV Size                10.00 GiB
  Current LE             2560
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
  --- Logical volume ---
  LV Path                /dev/vg/kali
  LV Name                kali
  VG Name                vg
  LV UUID                BeWqMO-DQAf-zcAp-RJAf-vmaY-OZbt-GLQIWx
  LV Write Access        read/write
  LV Creation host, time roadrunner, 2016-01-16 20:40:39 +0000
  LV Status              available
  # open                 0
  LV Size                15.00 GiB
  Current LE             3840
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2
   
  --- Logical volume ---
  LV Path                /dev/vg/HDD1
  LV Name                HDD1
  VG Name                vg
  LV UUID                xFw2Yu-li8I-Ooav-Yjk2-P38q-CZeG-dmdhSl
  LV Write Access        read/write
  LV Creation host, time roadrunner, 2016-01-16 20:51:00 +0000
  LV Status              available
  # open                 1
  LV Size                906.51 GiB
  Current LE             232066
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:3


```

```
156  sudo dd if=/dev/urandom of=/root/keyfile bs=1024 count=4
  157  sudo chmod 0400 /root/keyfile
  160  sudo cryptsetup luksAddKey /dev/sda1 /root/keyfile
  161  sudo vi /etc/crypttab

I added the line: enc-pv      /dev/sda1  /root/keyfile  luks

  162  sudo vi /etc/fstab
I added the line: /dev/mapper/enc-pv  /media/sda1     ext4    defaults        0       2

 163  sudo mount -a
  164  mkdir /media/sda1
  165  sudo mkdir /media/sda1
  166  sudo mount -a


```

---

### Post by Dáire Fagan on 2016-01-17
Commands from terminal history that were used to configure LVM and LUKS before I did anything from my OP below. I was entering commands for work in different terminals windows at the time which account for missing entries :

 ```
100  sudo cryptsetup -v --cipher aes-xts-plain64 --key-size 512 --hash sha512 --use-urandom --verify-passphrase luksFormat /dev/sda1
131  systemctl start lvm2-lvmetad.service
  132  systemctl start lvm2-lvmetad.socket
  133  sudo pvcreate /dev/mapper/enc-pv
  134  sudo vgcreate vg /dev/mapper/enc-pv
  135  sudo lvcreate -L 10G -n swap vg
  136  sudo lvcreate -L 15G -n kali vg
  137  sudo vgdisplay | grep -i free
  138  man lvcreate
  140  sudo lvcreate -l +100%FREE -n HDD1 vg
  141  lvdisplay
  142  sudo mkfs.ext4 /dev/vg/HDD1
  143  cat /etc/lvm/lvm.conf
  144  vi /etc/lvm/lvm.conf
  145  systemctl enable lvm2-lvmetad.service
  146  systemctl enable lvm2-lvmetad.socket
  147  sudo -s
  148  sudo cryptsetup luksOpen /dev/sda1 enc-pv
  149  sudo pvcreate /dev/mapper/enc-pv
  150  sudo apt-get install lvm2
  151  sudo pvcreate /dev/mapper/enc-pv
```

---

### Post by Dáire Fagan on 2016-01-18
Can anyone assist me with this? There is no data on the drives, so I am happy to start over of someone can help me.

---

