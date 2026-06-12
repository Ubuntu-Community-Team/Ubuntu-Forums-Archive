---
title: "Samba serving a Windows Share"
date: 2013-05-25
forum: Server Platforms
---

### Post by larrinh on 2013-05-25
OK Here it is. I have a Windows machine which hosts an Ubuntu Server virtual Client. I can mount a folder in /etc/fstab and can browse and edit the files in Linux. I NEED to share this mounted folder via Samba so other Windows machines can access and modify the files. When I add the folder as a Samba share I can only see the top directory level and I cannot access any of the files or directories. Can this even be done? One restriction is that the files MUST stay hosted on the Windows machine and not be physically moved to the Ubuntu Server so that changes to the files are immediately available on the windows host machine. Have been messing with this for two weeks and have gotten nowhere.

---

### Post by koenn on 2013-05-26
just checking so we get this straight :

you have a Windows server that presents a directory to a Linux server where you run Samba to present  (Windows type) shares to Windows clients on your network.

Why do you need that samba server then - why not let the windows machine do the sharing ?



re. your question : first thing to check is if all user accounts and permissions propagate correctly through your contraption. You're dealing with Windows accounts, probably NTFS ACL,  possibly linux accounts and access modes, and samba permissions. It's easy to get this wrong. Hence the question : why such a complicated setup ?

---

### Post by larrinh on 2013-05-30
> **koenn said:**
> just checking so we get this straight :

you have a Windows server that presents a directory to a Linux server where you run Samba to present  (Windows type) shares to Windows clients on your network.

Why do you need that samba server then - why not let the windows machine do the sharing ?



re. your question : first thing to check is if all user accounts and permissions propagate correctly through your contraption. You're dealing with Windows accounts, probably NTFS ACL,  possibly linux accounts and access modes, and samba permissions. It's easy to get this wrong. Hence the question : why such a complicated setup ?

The Windows 7 machine is not a server OS. Therefore is it only allows a maximum of 20 connections after which I must reboot it. The goal is to have this machine as a central storage location for all of the plants PLC and HMI code without the intervention of corporate IT. The network is strictly for industrial controls purposes, is physically isolated from the corporate network and we want to keep it that way. As a result we can't drop the data on a corporate network server. We need to setup our own. I have a high end enterprise class PC sitting at my desk that I am currently using for this. Now I just need to fix the reboot after 20 connections issue. Oh, not to forget, that since the other engineers are "afraid" of Linux and virtual machines we need to keep the data on the windows host machine's drive. Now I hope that covers everything.

With all of that said, I found a solution. I am using VirtualBox as my VM manager. I installed the Guest Additions onto the Ubuntu 13.10 Server and setup an auto mount, permanent, "shared" folder in VirtualBox which points to the data in question. This shared folder, as it turns out, is automatically mounted in the Linux client at 
      /media/sf_ShareName
I then configured Samba to share this directory. I hope this may help anyone else who has run into this problem.

---

### Post by volkswagner on 2013-05-30
Please post your smb.conf.

Also have you setup linux users and samba users?  What are the permissions of /media/sf_ShareName?  
Also please post your entry in /etc/fstab related to the above mentioned folder.

---

