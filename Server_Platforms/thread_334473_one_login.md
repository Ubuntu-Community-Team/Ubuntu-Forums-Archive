---
title: "one login"
date: 2007-01-08
forum: Server Platforms
---

### Post by umattu on 2007-01-08
Hey all

I really try not starting threads without looking for the info myself but I have either overlooked something or have not looked hard enough. 

My question is this:

I am running edgy on my desktop and I also have dapper running my server. I am using SAMBA for file sharing on my little LAN I have going. What really bugs me is that when I start my desktop up I have to login to my machine and then to get to my directories on the server I am required to login again. 

Is there anyway I can create one login, so when I log into my desktop I am logging into the server as well. I would really like to map a drive on the server that is with my desktop as soon as I login.

Thanks in advance for any advice!!!


umattu

---

### Post by scrooge_74 on 2007-01-09
Instead of SAMBA which is for connecting to Windows machines you can NFS to other machines and export the directories so they are ready from the time you boot.

You can also use SSH which Gnome will let you use from the Places>Connect to servers and you can have a nice icon on your desktop.  But you have to install OpenSSH server on the machines

---

### Post by umattu on 2007-01-09
I will try that

There wouldnt be any issue running NFS and samba are there?

---

### Post by scrooge_74 on 2007-01-09
NFS is for linux systems and SAMBA is for Windows systems for sharing files they run independ one from the other also you  use CUPS in linux to print and SAMBA to share a printer with a windows PC

---

