---
title: "Now just got going"
date: 2008-11-25
forum: Server Platforms
---

### Post by happyhacker on 2008-11-25
I have Ubuntu server installed and during the install I just selected ssh to install. I have downloaded webmin and have managed to access it from a laptop using 192.168.0.2 (which I've set as a fixed IP address for the server in our router.). I typed https://<myservername>:10000/ as instructed by webmin installer on the server command line screen but that did not work. If I use the IP address above that works. So I assume I do not have name resolution installed.

1. How do I install name resolution (do I need it)?
2. What is the next step I need to take to get file sharing working in webmin?

---

### Post by ibutho on 2008-11-25
You could edit the hosts file (/etc/hosts on Linux) of your laptop and add something like
```
192.168.0.2	hostname.localdomain hostname
```
Replace hostname and localdomain with the hostname and domain name of the server.

---

### Post by happyhacker on 2008-11-25
That would be OK if I use that laptop every time but I want to get at the server from any of the windows PCs on our office network. I'm assuming I will want name resolution going for when I setup file sharing on the server so common files can be accessed from here over the network.

What is the name of the packages I need to do name resolution and file sharing?

---

### Post by cdenley on 2008-11-25
> **cantthinkofanickname said:**
> That would be OK if I use that laptop every time but I want to get at the server from any of the windows PCs on our office network. I'm assuming I will want name resolution going for when I setup file sharing on the server so common files can be accessed from here over the network.

What is the name of the packages I need to do name resolution and file sharing?

Samba should allow windows computers to resolve your netbios name, which I believe defaults to your computer name (/etc/hostname). It is also  what you need to share files with windows computers.
```

sudo apt-get install samba

```
For just name resolution, I've seen bonjour recommended.

---

