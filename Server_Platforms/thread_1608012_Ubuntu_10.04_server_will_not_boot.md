---
title: "Ubuntu 10.04 server will not boot"
date: 2010-10-28
forum: Server Platforms
---

### Post by collimic on 2010-10-28
Yesterday I did some upgrades from 8.10 to 10.04. 
The upgrades seam to have gone well but not the system will not boot. I have tried to boot from a live cd and it will boot all the files are still on the system. The log files have not been much help. 

I would like to post the log files but I do not have any way to get them to my windows computer to post. I did take a picture of the log files but they are kind of hard to read. 

Any help would be great.

[IMG]http://i8.photobucket.com/albums/a42/collimic/Cell%20Album/2010-10-28095043.jpg[/IMG]

[IMG]http://i8.photobucket.com/albums/a42/collimic/Cell%20Album/2010-10-28095020.jpg[/IMG]

---

### Post by Vegan on 2010-10-28
I suggest a backup of your files and a fresh install of 10.10 as its far too messy and time consuming to try to fix it.

---

### Post by CharlesA on 2010-10-28
When you say "does not boot" are you able to get into recovery mode?

---

### Post by dtfinch on 2010-10-28
Does the 's' key do anything? It can get stuck waiting if it can't mount one of the filesystems in /etc/fstab.

---

### Post by collimic on 2010-10-28
> **CharlesA said:**
> When you say "does not boot" are you able to get into recovery mode?

It will goto the recovery mode but when I try and boot normal it gets to where the log in prompt is and then reboots.

> Does the 's' key do anything? It can get stuck waiting if it can't mount one of the filesystems in /etc/fstab.
Not sure what you mean by the 's' key. what should it do?

---

### Post by dtfinch on 2010-10-28
The 's' key tells mountall to stop waiting for missing devices to appear. I get this sometimes if an md raid or lvm volume fails to activate.

---

### Post by CharlesA on 2010-10-28
It would skip a failed mount.

I've had it happen if I have an entry in fstab that the system cannot find - it'll just "sit there" without displaying an error. TTY 7 should have an error in that case tho.

---

### Post by the_original_billq on 2010-10-28
> **collimic said:**
> It will goto the recovery mode but when I try and boot normal it gets to where the log in prompt is and then reboots.

Can you boot into single user mode?  That may allow you to step through the init scripts normally run when you init to 2 and debug what's blowing up.

---

### Post by collimic on 2010-10-28
Ok well I gave up on it for now and I was able to get my golden-client to boot and restore me to a week ago. 

So My server is almost back up. 
I just need to find a way with 8.10 to get the network interfaces reordered. 
eth0 is now eth4
eth1 is now eth0
eth4 is now eth1

I need to find a way to get them back in the right order.
I did look for the file /etc/iftab but it is not there. but I am not sure it should be there on ubuntu 8.10

Thank you all for your help.

---

### Post by CharlesA on 2010-10-28
Hi there,

Check this out: [http://www.science.uva.nl/research/air/wiki/LogicalInterfaceNames](http://www.science.uva.nl/research/air/wiki/LogicalInterfaceNames)

I looked at the ***nameif*** command.

---

### Post by collimic on 2010-10-28
Ok I am all back up and running. :)
I hate the posts where they do not show how they fixed it so here is what I had to do.

To fix the booting issue I did not have to time to invest anymore as this was a production server. So I was lucky enough to have a golden client backup of it but it is over 2 weeks old so we are missing a lot of web site information and a lot of email. 

That will be my next project to find a good real-time backup configuration that I can understand and get setup.

To fix the network cards I did the following:
```
for dir in /sys/class/net/* ; do
    [ -e $dir/device ] && {
        basename $dir ; readlink -f $dir/device
    }
done
```
It gave me an out put of:
```
eth0
/sys/devices/pci0000:00/0000:00:09.0/0000:05:0c.0
eth1
/sys/devices/pci0000:00/0000:00:0a.0
eth2
/sys/devices/pci0000:00/0000:00:09.0/0000:05:08.0
```
I then did? 
```
cat > /etc/udev/rules.d/70-persistent-net.rules << EOF
ACTION=="add", SUBSYSTEM=="net", BUS=="pci", KERNELS=="0000:05:0c.0", NAME="eth0"
ACTION=="add", SUBSYSTEM=="net", BUS=="pci", KERNELS=="0000:00:0a.0", NAME="eth1"
ACTION=="add", SUBSYSTEM=="net", BUS=="pci", KERNELS=="0000:05:08.0", NAME="eth4"
EOF
```
Then I rebooted the computer.

Credit for this goes here:  [http://www.linuxfromscratch.org/blfs/view/development/chapter07/network.html]("http://www.linuxfromscratch.org/blfs/view/development/chapter07/network.html")

---

### Post by CharlesA on 2010-10-28
Interesting fix.

I use rsync for backing up my server. Works wonders for me. :)

---

### Post by collimic on 2010-10-28
> **CharlesA said:**
> I use rsync for backing up my server. Works wonders for me. :)
I would really like to find a tutorial for setting up rsync as a client server with the instruction on how to restore. If you know of one or would like to post how it is done I would like that much.

---

### Post by CharlesA on 2010-10-28
I use it to sync stuff from my server to external media nightly.

What sort of environment do you have? I've got a script on my Windows machines that runs nightly and backs up user documents to the server and then they server backs it up to external media.

---

