---
title: "Drobo Like Functionality"
date: 2008-10-30
forum: Server Platforms
---

### Post by Infinitas on 2008-10-30
I am interested in getting a file server set up that has the same functionality as the Drobo. See [http://www.drobo.com](http://www.drobo.com) for more details.

I would like to build a full tower machine that has plenty of room for expansion. That way the only reason to remove a drive from the machine is when it fails. Whenever I need more storage I could simply buy a drive that currently has a good price/byte ratio and plug it in.

Does any such system already exist? I am hoping for something as easy as the Drobo, but would be satisfied by any method that achieves the goal of distributing parity across multiply drives of differing sizes.

-Infinitas

---

### Post by cariboo on 2008-10-31
Basically just install the server, when you get to server types select Samba, NFS and openssh-server.

That way you can serve files to any type of computer and do all the administration via ssh.

Jim

---

### Post by Infinitas on 2008-10-31
I already have a file server that is using Samba, NFS and SSH. I am currently using software RAID through mdadm. However, when the drives that I am using fill up, the only option I have is to scrap the existing drives for bigger drives. What I would like to do is just be able to plug in a new drive of any size and have it mesh in with the existing drives.

-Infinitas

---

### Post by fjgaude on 2008-10-31
What is wrong with having backups of all data? I have three, one online, another near-line, and finally, one off-line. Data is so important it is necessary to have triple backups.

---

### Post by bab1 on 2008-10-31
Check out [[COLOR="DarkGreen"]**Nexenta**[/COLOR]]("http://www.nexenta.com/corp/index.php?option=com_content&task=blogsection&id=4&Itemid=67").  This uses Debian with an OpenSolaris kernel.  The file system is ZFS.  

Nexenta Stor is able to expand pools of hard drives.  There is a free version that has a limitation of 1TB.  I believe you can install the Nexenta OS yourself and configure the ZFS (zpools) on your own.  

Of course OpenSolaris will do this also, but with Solaris style unix structure

---

### Post by Infinitas on 2008-10-31
It appears that [LVM]("http://tldp.org/HOWTO/LVM-HOWTO") provides exactly the functionality I am looking for. Of course, it isn't as "set it and forget it" as the Drobo is, but I feel there is great potential here. Aparently it can be used in combination with software raid through mdadm. The combination of the two should be exactly as I desire.

I will post back with some links when I learn more... unless some knowledgeable reader beats me to it :)

-Infinitas

---

### Post by Infinitas on 2008-11-19
It looks like I finally got LVM to do exactly what I was looking for. The solution isn't as easy or as cheap as the drobo, but it is more flexible and has higher performance. Check out this [how-to]("http://infinitas.homelinux.com/useful/linux/lvm/") I wrote to get the same setup as me :D

[http://infinitas.homelinux.com/useful/linux/lvm/]("http://infinitas.homelinux.com/useful/linux/lvm/")

-Infinitas

---

