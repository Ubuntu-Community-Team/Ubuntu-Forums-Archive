---
title: "Dualboot ubuntu server-windows 2003 server"
date: 2008-10-10
forum: Server Platforms
---

### Post by santille on 2008-10-10
Hi,

I installed Ubuntu Server with following partitions :

/dev/sda3 : 9.7 G
varrun :379 M
varlock : 379 M
udev : 379 M
devshm : 379 M
/dev/sda2 : 133 M
/dev/sda4 : 63 G

I would like now to install windows 2003 server in dualboot.
What's the procedure?
Actually if I boot on windows 2003 server, at the level of partitions, it gives me one unknown 39 G partition...???

Thanks,

seb

---

### Post by Titan8990 on 2008-10-10
Typically, it is poor practice (and often does not work) to install an OS on an extended partition. 

Why would you want to break your Linux server by putting such a crappy OS on it?

---

### Post by lykwydchykyn on 2008-10-10
Windows does not recognize Linux partitions.  Did you set up your machine using LVM?

You might find it easier to run 2k3 server in a VM.  But if not, the basic idea is:

 - You need to free up some space on your drive
 - Install Windows 2k3 server in the free space
 - Reinstall GRUB since Windows overwrites it

Not sure about the 39 GB partition thing.  What kind of drive are you installing on?

---

### Post by santille on 2008-10-10
IDE
What is the command to check that?

Thanks,

seb the newbie

---

### Post by lykwydchykyn on 2008-10-10
check what?

---

### Post by santille on 2008-10-10
In my situation I think it would be easier to format my HDD mounted with Ubuntu Server, install Windows 2003 and afterwards Ubuntu Server. The problem is : how to do that considering my windows bootable recognize only 39 G! How to cancel my LINUX partitions to recover my entire HDD capacity?

Thanks,

seb

---

### Post by lykwydchykyn on 2008-10-10
You can use something like Darik's boot and nuke to clean the drive.  Or just do this:

**[COLOR="Red"]WARNING: UBER-DESTRUCTIVE COMMAND AHEAD[/COLOR]**

```

sudo dd if=/dev/zero of=/dev/sda count=512

```

That'll zap your partition table and leave the drive empty.

---

### Post by santille on 2008-10-10
Your command gives me :
512+0 records in
512+0 records out
262144 bytes copied

What does it mean?

---

### Post by lykwydchykyn on 2008-10-10
It means your master boot record and partition table are no more, and your partitions are gone.  Boot to your win2k3 install cd now.

---

### Post by santille on 2008-10-10
Thanks,

All is OK!
Apparently my hdd had a 32Gb capacity...

I will put 22 Gb to my 2003 and leave 10 Gb for my Ubuntu Server. After 2003 installed could you advise me about the best way to install Ubuntu server? Virtual box, wubi, others?

Thanks,

seb

---

### Post by lykwydchykyn on 2008-10-10
The best way is to boot to the Ubuntu disc and install to the free space with a normal install, no wubi.  And if you want to go the VM route, I'd highly recommend installing Windows as a guest on Ubuntu, not the other way 'round.

---

