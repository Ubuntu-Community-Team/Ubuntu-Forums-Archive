---
title: "ubuntu server LTS 16.04 couldn't mount Raid6 created on ubuntu server 14.04"
date: 2016-05-06
forum: Server Platforms
---

### Post by yinj21 on 2016-05-06
Hello everyone,

I have a problem when I upgraded my server to LTS 16.04.

Previously, I installed ubuntu server 14.04 into a separated 500 GB HD, and created mdadm Raid6 with another 3TbX4 HDs:

 ```
# mdadm --create /dev/md0 --chunk=128 --level=0--raid-devices=4 /dev/sdb /dev/sdc dev/sdd /dev/sde
```

then mount it: 
```
# sudomkdir /mnt/rdisk
```
```
# sudo mount /dev/md0 /mnt/rdisk
```

find md0 UUID by:
```
#sudo blkid
```
then add it by:
```
#sudo vi /etc/fstab
```

Everthing was good and the server worked great, but when I upgraded to LTS 16.04, it was stuck on boot, and came up a message: "welcome to emergency......type control+S to continue...", I can't remember exactly what it said. 

So, I tried fresh installation into another drive and mount my Raid drive using same way. When I typed #sudo blkid, I couldn't find UUID of md0, only listed UUIDs of sda,sdb,sdc,sdd,sde. I added the same UUID used in 14.04, when I rebooted, same message came up. It couldn't recognize Raid drive. Is there anything I was wrong? 

I appreciate for any suggestion.







[/CODE]

---

### Post by neu5eeCh on 2016-05-06
Take a look at this bug and see if it's at all helpful:

[https://bugzilla.redhat.com/show_bug.cgi?id=1225184](https://bugzilla.redhat.com/show_bug.cgi?id=1225184)

You might test with a different distro (KDE) or Kernel (in 16.04). I've just dealt with a heap of problems solved by reverting to an earlier kernel.

---

### Post by ubu_dynamite on 2016-05-06
Not really following what you al did but at least the first command you gave shows you creating a 4 disk raid0/stripe not raid6.
```
# mdadm --create /dev/md0 --chunk=128 --level=0--raid-devices=4 /dev/sdb /dev/sdc dev/sdd /dev/sde
```

What do the following commands output for you.
```
cat /proc/mdstat
sudo mdadm -vv --detail --scan
sudo mdadm -vv --examine --scan

```

---

### Post by yinj21 on 2016-05-07
> **VTPoet said:**
> Take a look at this bug and see if it's at all helpful:

[https://bugzilla.redhat.com/show_bug.cgi?id=1225184](https://bugzilla.redhat.com/show_bug.cgi?id=1225184)

You might test with a different distro (KDE) or Kernel (in 16.04). I've just dealt with a heap of problems solved by reverting to an earlier kernel.

Good to know there is bug for it. I may wait for someone fix this issue. thanks.

---

### Post by yinj21 on 2016-05-07
> **ubu_dynamite said:**
> Not really following what you al did but at least the first command you gave shows you creating a 4 disk raid0/stripe not raid6.
```
# mdadm --create /dev/md0 --chunk=128 --level=0--raid-devices=4 /dev/sdb /dev/sdc dev/sdd /dev/sde
```

What do the following commands output for you.
```
cat /proc/mdstat
sudo mdadm -vv --detail --scan
sudo mdadm -vv --examine --scan

```

I will give it try and paste it when switch it to 16.04. Thanks.

---

### Post by ubu_dynamite on 2016-05-07
> **yinj21 said:**
> Good to know there is bug for it. I may wait for someone fix this issue. thanks.

Not really seeing the relevance of that fedora bug for your problem the bug does not even seem to be available in the fedora server version.

---

### Post by nerdtron on 2016-05-08
Thread moved to **Server Platforms**.

---

### Post by yinj21 on 2016-07-07
I can get UUID of md0 easily, BUT 16.04 won't give me UUID for it, it just give me UUIDs from each drives. Any suggestion? 

$ lsblk -o name,uuid
NAME   UUID
sda
&#9500;&#9472;sda1 cd227c41-45e3-4672-81ca-aee80b7b4a61
&#9500;&#9472;sda2 a6af4c20-b4c7-4f29-a516-ab1008c064e7
&#9500;&#9472;sda3 1dc94d55-710b-461e-9c89-36bba1725d9c
&#9492;&#9472;sda4 835fa7a4-46ef-4bab-81da-7b440c9512c0
sdb    9429ad4f-2c70-e3a8-daff-8fe2f989dece
&#9492;&#9472;md0
sdc    9429ad4f-2c70-e3a8-daff-8fe2f989dece
&#9492;&#9472;md0
sdd    9429ad4f-2c70-e3a8-daff-8fe2f989dece
&#9492;&#9472;md0
sde    9429ad4f-2c70-e3a8-daff-8fe2f989dece
&#9492;&#9472;md0

---

### Post by ubu_dynamite on 2016-07-08
Not sure i get your question you say you can get UUID of md0 easily and your output shows the UUIDs so whats the problem?

All drives show same UUID because they are in the same raid.
[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)

---

### Post by darkod on 2016-07-08
I also don't understand many things...

1. How and why did you upgrade 14.04 to 16.04 when a LTS release does not prompt you for the do-release-upgrade to the next LTS until the first .1 has been released. In other words, 14.04.x will not prompt you to upgrade to 16.04 until 16.04.1 is released which should be sometimes in August. Did you force it to upgrade? In such case are you sure you upgraded to 16.04 and not to some developer release?

2. You never replied in what Ubu commented above, that the command you posted shows creating raid0 array, not raid6. Did you mistype the command now, or you made an error creating the array and you only think you have raid6 when in fact you have raid0? It doesn't matter much, the array should assemble and work anyway, but it does make a big difference for you because raid0 has no redundancy and is no raid at all.

3. According to the command to create the array, you used the whole disks as devices (sdb, sdc, sdd and sde). That can work, but it is much better to use partitions. Make one big partition on the whole disk (or more partitions if you want more arrays) and use them when creating the array, not the whole disks. But that is just advice for the future, right now do not repartition your disks if you have important data on them because you will lose it.

4. Is the OS on sda, outside the array? In such case the server should boot even if the array is not recognized. Have you tried powering down the machine, disconnecting ALL data disks (not just one or two, all four), and see if it will boot with only the OS disk?

If you don't have it already, get the iso image of ubuntu desktop and make a live cd or live usb with it. That can help you booting the machine in live mode and working from there to try and fix your server.

---

