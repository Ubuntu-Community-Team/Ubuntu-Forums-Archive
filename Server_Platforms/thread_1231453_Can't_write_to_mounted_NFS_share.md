---
title: "Can't write to mounted NFS share"
date: 2009-08-04
forum: Server Platforms
---

### Post by maandverband on 2009-08-04
Hello.

Last year I installed Ubuntu Server with NFS on a PC. There were three hard drives in this PC (sda for the operating system, sdb for my own files (mounted at /backup/myname) and sdc for my parents files (mounted at /backup/myfathersname)). My parents PC had access only to /backup/myfathersname (read and write) and my own PCs had access to both shares (read and write). This PC was running Ubuntu Server 8.04 32-bit and everything worked without any problems.

Now I wanted to upgrade, so I took a newer PC and installed Ubuntu Server 9.04 32-bit. I also placed a 1TB hard disk (mounted at /backup) and copied all my data from the old hard drive to a directory /backup/myname and all of my parents data to a directory /backup/myfathersname. I set up the same permissions (read and write for all of my PCs to both shares and read and write access for my parents PC on /backup/myfathersname).

I used the same command as before to mount the NFS share on my laptop (it was still in the list of used commands, so I just pressed the up arrow a few times in a terminal window). The command completes without any errors and I can see all of my files, but I can't find out how to write. On my old server installation I never had this problem, but now it won't give me any write access.

Somebody has an idea how to fix this?

---

### Post by cdunbar on 2009-08-04
Hello,

It sounds like the NFS share is shared out as read only. Can you go into more detail on how you configured the share?

Thanks,
Chris

---

### Post by maandverband on 2009-08-04
I was thinking the samen, but I checked /etc/exports at least three times, but there's nothing shared as read only. Everything is shared as read and write. The only difference between the old installation and the old installation is I also made a /backup/temp this time (read and write access for everyone on the network). The file /etc/exports looks like this:

/backup/myname 192.168.0.3(rw) 192.168.0.4(rw) 192.168.0.5(rw) 192.168.0.6(rw)
/backup/myfathersname 192.168.0.3(rw) 192.168.0.4(rw) 192.168.0.5(rw) 192.168.0.6(rw) 192.168.0.7(rw)
/backup/temp 192.168.0.0/24(rw)

---

### Post by cdunbar on 2009-08-04
What about the underlying permissions on the directories themselves?

---

### Post by maandverband on 2009-08-04
I even tried a chmod -R 777 on /backup, to give access to everyone in all directories and subdirectories, but that didn't give me any rights to write in the directorie when mounted from my laptop.

---

### Post by koenn on 2009-08-04
are you accessing them as root ?

---

### Post by maandverband on 2009-08-04
I use the command "sudo mount 192.168.0.3:/backup/myname Servermount" to mount with root privileges.

---

### Post by koenn on 2009-08-04
> **maandverband said:**
> I use the command "sudo mount 192.168.0.3:/backup/myname Servermount" to mount with root privileges.
no, on the clients, where they are mounted. Do you access these directories/mount points as root ?  NFS 'squashes' root because it's a potential security hole to allow root access.

---

### Post by maandverband on 2009-08-04
The command of my previous post is the command I use to mount a NFS share on a client (as described [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo#Mounts")). In my home directory on my clients I made a directory with the name Servermount to mount the NFS share. Then I use the command "sudo mount 192.168.0.3:/backup/myname Servermount", just like it says in the SettingUpNFSHowTo.

---

### Post by maandverband on 2009-08-05
Problem resolved. I had to change ownership of /backup to my own account. Now everything works as it did before.

---

