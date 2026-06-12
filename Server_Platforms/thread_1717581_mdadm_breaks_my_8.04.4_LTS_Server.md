---
title: "mdadm breaks my 8.04.4 LTS Server"
date: 2011-03-30
forum: Server Platforms
---

### Post by mysticBoer on 2011-03-30
Hi all,

I've got a strange problem. I have the following system:

```

1 x Intel DQ45CB Motherboard
1 x Intel Q9400 Processor
4 x Kingston Value Ram 2Gb Sticks totalling 8Gb
2 x 500Gb Seagate hdd's

```

I install the system as follows with the following type of scenario
```

Partitions:
/dev/sda
---/dev/sda1 as '/' - 8GB
---FREE SPACE       - 492.1GB

/dev/sdb
---/dev/sdb1 as SWAP - 8GB
---FREE SPACE       - 492.1GB

Additional Packages:
LAMP
OpenSSH Server
Samba Server

```

After doing this install everything works fine as expected. I can reboot, shutdown and bootup as I much as I want to and the system will work. Now, I proceed to do the following (as root obviously - sudo bash)
```

apt-get update

apt-get upgrade #Upgrade system

apt-get install ntp ntop tcpdump build-essential graphviz vim tofrodos sysstat dhcping socat snmp snmpd mdadm ncurses-dev flex bison libpcap-dev libpng12-dev 

php5 php5-dev php5-gd php5-mysql php-pear apache2 libapache2-mod-php5 unzip zip tcptrace nmap sysklogd iperf reiserfsprogs lm-sensors postfix

```

When I try to restart the system now, I get to the grub boot loader and then it just breaks with the following message 
[[IMG]http://img683.imageshack.us/img683/7377/img0491ge.jpg[/IMG]](http://img683.imageshack.us/i/img0491ge.jpg/)

I've identified 'mdadm' as being the culprit here. Any idea why this would happen?

---

Just a subnote. The reason I'm installing mdadm is to create a soft-raid as follows with the remaining space on each drive:

```

mdadm --create --verbose /dev/md0 --level=0 --raid-devices=2 /dev/sda2 /dev/sdb2 #Create the stripe set

mkfs -t reiserfs /dev/md0 #Format the new stripe set

```

---

### Post by deconstrained on 2011-03-30
How do you figure mdadm is the cause of your troubles, since you installed dozens of other packages with it? Also, you don't even have any arrays set up yet, based on the information you've given.

I think dpkg messed up your initramfs. You installed mdadm, and since it's a utility that could potentially affect how the system boots, one of the hooks was rebuilding the Linux image -- a sort of post-installation knee-jerk reaction. Something went wrong in that part of the process, and now your initramfs isn't booting properly.

If I'm reading your post right, you've installed on plain old partitions (/dev/sd[a-z][1-9]) but want to migrate Ubuntu to a software RAID. You simply cannot transfer a system to software RAID in-place; the superblock of the involved partitions will be written with necessary metadata for assembling the array, which means that filesystems on there already may be affected.

What you should be doing instead is backing up your data, creating/assembling the RAID while booted to a livedisk, then transferring the data back over to the array (or reinstalling, onto the array) once you've set it up, then chrooting, updating /etc/fstab and /etc/mdadm/mdadm.conf, rebuilding the initramfs and running grub-install with the option flag "--modules=raid".

---

### Post by mysticBoer on 2011-03-30
> **deconstrained said:**
> How do you figure mdadm is the cause of your troubles, since you installed dozens of other packages with it? Also, you don't even have any arrays set up yet, based on the information you've given.

I think this was a hasty 'assumption' because it looks like the only thing here that has anything to do with partitions/disks/etc
 Wrong way, I agree. Assumption is the mother of all stuff-ups!

> **deconstrained said:**
> If I'm reading your post right, you've installed on plain old partitions (/dev/sd[a-z][1-9]) but want to migrate Ubuntu to a software RAID. You simply cannot transfer a system to software RAID in-place; the superblock of the involved partitions will be written with necessary metadata for assembling the array, which means that filesystems on there already may be affected.

I think I should give you more detail. The reason I build the system as I do (and I've done it like this for over 2 years) is because I create a folder '/data' afterwards to which I mount /dev/md0. This gives me a striped volume with a reasonable speed increase to put a MySQL database on as well as some tcpdumps - the machine in question is being built as a probe which captures network traffic. It's a little IO intensive, hence the setup. 

Redundancy isn't much of an issue.

I hope this answers your question.

I read in [URL="http://ubuntuforums.org/showthread.php?t=1469017"]this 
[/URL] post that it might be the GRUB which might be stuffed up. Will have a look at that now.

Thanks for the reply!

---

### Post by deconstrained on 2011-03-30
Okay, that greatly simplifies it. Your system can be left as-is, no need to reinstall grub or rebuild the Linux image, except to fix your current problem.

Nevertheless, properly configuring of mdadm.conf and fstab are necessary to have the array up and ready at boot time, even though the initramfs needs nothing extra, since the root FS isn't on an mdadm device. If it were, then the extra steps I mentioned would be necessary.

---

### Post by mysticBoer on 2011-03-31
> **mysticBoer said:**
> I think this was a hasty 'assumption' because it looks like the only thing here that has anything to do with partitions/disks/etc
 Wrong way, I agree. Assumption is the mother of all stuff-ups!


Ok, it might have been an assumption, but it seems I was correct anyway. I re-installed the machine. Did the following:

```

sudo bash

apt-get update

apt-get upgrade

```

At this stage I rebooted the machine and everything was still fine.

```

apt-get install mdadm

```

BOOM! Unable to restart successfully.

I then used the 'Rescue a broken system' feature on the install disk and executed a shell in '/dev/sda1'.

While in this shell I changed the fstab to load from /dev/sda1 instead of the UUID method. I also did the following for the mdadm, although no RAID's have been configured yet:

```

cp /etc/mdadm/mdadm.conf /etc/mdadm/mdadm.conf.ori

mdadm --detail --scan > /etc/mdadm/mdadm.conf

```


Any thoughts?

---

### Post by deconstrained on 2011-03-31
Worthy problem of filing a bug I think (especially since it's a server; support for 8.04 server continues until April 2013). Just adding a few executables to the system should not affect how it boots per se, so it has to be one of the post-installation actions that messed with your initramfs and/or kernel.

---

