---
title: "how to backup or clone my server?"
date: 2011-08-09
forum: Server Platforms
---

### Post by bone2006 on 2011-08-09
I have a file server running in an office that's mostly used for file sharing and a scanner saves pdf files to the server.

I'm running the latest LTS ubuntu server edition and I really only have ssh installed and samba.   

My question is that I've done so much to the server as far as premissions and configuration and I'd like to make a clone of this to another computer and not sure how I would do this?

I'm not sure if clonezilla or something like this can perform this task?  I basically just have a very old computer and now I have another very old computer that I want to make into a spare just incase something happens to the original.

Any recommedations on how I would accomplish this?

---

### Post by ajgreeny on 2011-08-09
I think you answered your own question with clonezilla as a live CD, assuming that you have a CD drive, of course, and somewhere to save the clone.

---

### Post by Hack.The.Pow. on 2011-08-09
If you want an **exact** copy of your installation you can use fsarchiver.  It just makes an image of your partition and then you can just install that image on another computer.

Just make sure the hard drive on your other computer is as big or bigger than this one.

[http://www.fsarchiver.org/QuickStart]("http://www.fsarchiver.org/QuickStart")

---

### Post by headvampyre@hotmail.co.uk on 2011-08-09
Or you could run:

tar cf / /Location/To/Store/Back/BackupName.tar

That just stores the entire FS in a tar archive :)

---

### Post by LtPitt on 2011-10-18
Excuse me for reviving an old topic but my problem is quite tough to me.

I have an old proxy server

uname -a

Linux proxy 2.6.18-6-686 SMP etc etc

I _think_ it's debian (I have apt-get).

I've read an interesting article to achieve the virtualization result:
[http://www.madgenius.com/blog/index.php?/archives/6-Migrating-Linux-physical-server-to-a-ESXi-VM-server.html](http://www.madgenius.com/blog/index.php?/archives/6-Migrating-Linux-physical-server-to-a-ESXi-VM-server.html)

But this server has differente disks:

df -h

Filesystem         Dimens. Usati Disp. Uso% Montato su
/dev/sda1              28G  4,6G   22G  18% /
tmpfs                1015M     0 1015M   0% /lib/init/rw
udev                   10M   96K   10M   1% /dev
tmpfs                1015M     0 1015M   0% /dev/shm
/dev/sda2              92M   12M   75M  14% /boot
/dev/sdb2              25G  5,9G   18G  26% /log
/dev/sdb1             9,2G   96M  8,7G   2% /squidcache

It acts mainly as proxy server but it has a LOT of iptables rules I've tried to save and import in a new server I've prepared getting only errors (iptables-save and then iptables-restore)

I would like to do a perfect cloning of it and, if possible, virtualize it in a vmware esxi server.

What path should I take?

---

### Post by youareno6 on 2011-10-18
For OpenSource there is a product called Mondo. It's cludgy, but supposed to work. We use a commercial product that called Storix. It works really well, but is not free.

---

### Post by collisionystm on 2011-10-18
> **LtPitt said:**
> Excuse me for reviving an old topic but my problem is quite tough to me.

I have an old proxy server

uname -a

Linux proxy 2.6.18-6-686 SMP etc etc

I _think_ it's debian (I have apt-get).

I've read an interesting article to achieve the virtualization result:
[http://www.madgenius.com/blog/index.php?/archives/6-Migrating-Linux-physical-server-to-a-ESXi-VM-server.html](http://www.madgenius.com/blog/index.php?/archives/6-Migrating-Linux-physical-server-to-a-ESXi-VM-server.html)

But this server has differente disks:

df -h

Filesystem         Dimens. Usati Disp. Uso% Montato su
/dev/sda1              28G  4,6G   22G  18% /
tmpfs                1015M     0 1015M   0% /lib/init/rw
udev                   10M   96K   10M   1% /dev
tmpfs                1015M     0 1015M   0% /dev/shm
/dev/sda2              92M   12M   75M  14% /boot
/dev/sdb2              25G  5,9G   18G  26% /log
/dev/sdb1             9,2G   96M  8,7G   2% /squidcache

It acts mainly as proxy server but it has a LOT of iptables rules I've tried to save and import in a new server I've prepared getting only errors (iptables-save and then iptables-restore)

I would like to do a perfect cloning of it and, if possible, virtualize it in a vmware esxi server.

What path should I take?

Just use the vmware converter to push it onto your esxi server.

---

### Post by LtPitt on 2011-10-19
:O

And nothing else?

No software has to be installed on the target machine? :O

---

### Post by collisionystm on 2011-10-19
> **LtPitt said:**
> :O

And nothing else?

No software has to be installed on the target machine? :O

It is handled automatically.

You need an ESXi server.

On a windows machine, install the vmware converter

Follow the instructions

on your linux box, you must enable the ROOT account for it to work though.

---

### Post by LtPitt on 2011-10-19
You are awesome.

I am gonna try this right away and keep you posted.

God bless you!

---

### Post by CharlesA on 2011-10-19
If the VMware converter doesn't work, you can always set up the drives on the VM and just clone the entire system with something like Clonezilla.

The VM conversion should work fine tho.

---

### Post by LtPitt on 2011-10-20
Thank you all guys!

Since I'm a bit scared of screwing and need to do this fast I'll try the acronis solution: it seems very easy.

I'll keep you posted :)

---

