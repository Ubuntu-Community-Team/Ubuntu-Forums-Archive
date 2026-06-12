---
title: "Virtualbox Really Slow!"
date: 2008-04-30
forum: Virtualisation
---

### Post by Kiri on 2008-04-30
I've been finding a gust XP in vbox running really really slow when I try to do anything remotely intensive, like even just installing a program.


I have dedicated 1200mb of RAM for it (out of my system total 2.5gb).
The actual windows XP OS doesnt seem to lag, it just seems to take ages to complete tasks, like copying files, installing etc.

CPU is only being used a few % too...

Anyone know what might be up?

---

### Post by ArtPulse on 2008-04-30
Moments that require hard disk operations (and installations do!), while sharing the same physical disk with your ubuntu, end up in a big peformance loss... It's recommended to have your host and guest OS in separate disks (if possible, course!).

Though... I have both in same, only 1.5 GB RAM, P4 3GHz and I can play SimCity 4 o.O better than with Cedega.

Define me "slow" and "ages" =P mouse freezes? does ubuntu freeze a bit too?
And what's ur CPU? =)
To install Dreamweaver, i.e, I had to wait for 10 minutes I think...

---

### Post by Kiri on 2008-05-01
Thanks for the reply ArtPulse.
Basic operations seem to be fine and very responsive. I didn't notice much of a performance decrease in Ubuntu, but the XP guest really crawls when installing, or running some apps. 
I wonder if it also could be something to do with me having my VDI on an NTFS volume?
Because I see that when I am doing disk intensive stuff (like installing programs) in the XP guest, that the NTFS-mount process is using a fair chunk of CPU in ubuntu. (maybe 40%)

At the moment I only have one HD, but I plan to pick an external USB drive soon, and will try a new XP guest with the VDI on that volume and see if it makes a difference..

---

### Post by Azzuron on 2008-08-14
I think the NTFS partition is exactly the issue. I think it has to do with how the Virtualbox VirtualDisk process writes to the file and it overloads the ntfs-3g driver. I am experiencing this issue this very moment actually. You should notice that the HDD light on your vm has a solid red dot. Writing appears to be much worse than reading. how to solve it? i suppose convert to ext3 or some other linux native Filesystem. 

 --Dave

---

### Post by tuncay on 2009-02-02
Azzuron.

i have the same problem... my virtualbox-> windows xp is really slow...

what about the NTFS format?! You say that the NTFS Partition slows down the virtualbox ?!

I actually only use the virtualbox to play poker but it is really slow...


what steps i should take to solve the problem?




so i would be very happy if anybody can help me...

thank you very much

---

### Post by dkev on 2009-02-02
I don't have this issue. Do you have a SATA HDD, and if so do you have it enabled on VB? Also make sure you have your AMD or Intel extensions enabled.
Don't know if it will help, but it can't hurt.

---

### Post by bkann on 2009-02-02
This may be a long shot, but if there is a network address that your virtual machine is having trouble accessing, that may slow it down quite a lot.

My virtual XP machine is on a Windows domain.  If it is not attached to the local network and file synchronization is enabled, even the most trivial tasks can take minutes.  When it's up and running on the network, I can't tell that it's a virtual environment at all.  It's a huge difference, and I see the same effect if I have drives mapped to inaccessible remote servers or even just links on the desktop to offline file locations.

A long shot, but maybe worth a look.  Would any of these conditions apply to your situation?

---

### Post by tuncay on 2009-02-03
soooo

now i know where the problem comes from...

if i start a pogramm which connects to the PostgreSQL Server ( the server is installed on ubuntu )

the guest (Windows XP running on virtualbox) is starting to lag...

thats the problem!

should i install the postgreSQL server on windows at the virtualbox ? Could this solve the problem?

:p

---

### Post by bkann on 2009-02-03
I do believe it would help a lot, tuncay, to run PG server on the XP host and then just have those Windows applications query the virtual localhost.  If I understand your situation correctly, an alternative may be to use your virtual network adapter in 'host interface' mode.  This may or may not cure your problem, depending on your specific setup, by removing NAT between Ubuntu and XP.

The problem I have found with the second method above is that when you don't have access to a network (eg., a home or work network), the host and VM can't see each other.  I have submitted a separate post about this, but it hasn't seen any replies yet ([http://ubuntuforums.org/showthread.php?t=1058416]("http://ubuntuforums.org/showthread.php?t=1058416")).  Regardless, it is really only a problem with a laptop that is going to move between multiple networks or none at all at times.

I'm not a VirtualBox guru by any means, but these are things I've encountered.  Your mileage may vary.

---

### Post by tuncay on 2009-02-03
what do you mean by " to run PG server on the XP host and then just have those Windows applications query the virtual localhost. "

and 

"to use your virtual network adapter in 'host interface' mode"

could you explain it in more details please... how to do it and so on..

many thanks !

---

### Post by xiaomao5 on 2011-05-22
> **Azzuron said:**
> I think the NTFS partition is exactly the issue. I think it has to do with how the Virtualbox VirtualDisk process writes to the file and it overloads the ntfs-3g driver. I am experiencing this issue this very moment actually. You should notice that the HDD light on your vm has a solid red dot. Writing appears to be much worse than reading. how to solve it? i suppose convert to ext3 or some other linux native Filesystem. 

 --Dave

Are you sure?? NTFS is in the virtual disk and uses windows driver for NTFS! Linux is not reading it...

---

### Post by MartyBuntu on 2011-05-22
Since Azzuron posted that nearly three years ago, I would say it's a safe bet you won't be getting an answer any time soon.

---

### Post by CharlesA on 2011-05-22
Good night sweet thread..

---

