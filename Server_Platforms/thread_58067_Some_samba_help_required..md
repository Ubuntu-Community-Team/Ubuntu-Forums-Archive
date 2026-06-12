---
title: "Some samba help required."
date: 2005-08-18
forum: Server Platforms
---

### Post by SlimDady on 2005-08-18
So I just switch from windows 2003 to ubuntu.
The main purpose of the server is as a file server for media, all the computers in the house, aswell as the xbox need to have access to the files.


What I have been able to do so far is edit the smb.conf file and have shares open to anyone as read only. Which is perfect for just sharing the media.

I now want to add shares that can only be accessed by certain users with write permission. Mainly this is for me when I want to delete files or copy files from another computer to the read only shares that I have already made. The idea is to set up a share that has write permissions for myself. And then in my windows machine map it as a drive.

Can anyone show me a sample smb.conf where I can look how to make these shares limmited to a certain user account.

---

### Post by nad on 2005-08-19
From: [http://us2.samba.org/samba/docs/man/Samba-Guide/simple.html#id2532128](http://us2.samba.org/samba/docs/man/Samba-Guide/simple.html#id2532128)

Chapter 1. No-Frills Samba Servers
Part I. Example Network Configurations

[files]
comment = Work area files
path = /data/%U
read only = No
[master]
comment = Master work area files
path = /data
valid users = alan
read only = No

You need to create a share of the parent directory that gives those users write permissions.

---

### Post by SlimDady on 2005-08-19
[QUOTE=nad]From: [http://us2.samba.org/samba/docs/man/Samba-Guide/simple.html#id2532128](http://us2.samba.org/samba/docs/man/Samba-Guide/simple.html#id2532128)

Chapter 1. No-Frills Samba Servers
Part I. Example Network Configurations

[files]
comment = Work area files
path = /data/%U
read only = No
[master]
comment = Master work area files
path = /data
valid users = alan
read only = No

You need to create a share of the parent directory that gives those users write permissions.[/QUOTE]


Thanks for the help.. I glanced through that guide.. but somehow missed this..

---

### Post by SlimDady on 2005-08-19
ok works like a charm.. thanks so much

---

### Post by SlimDady on 2005-08-19
I found another thing I have a question about.

So I have this share with write permissions now. I have maped it to a drive in windows on another computer.


When i try to delete files its acting weird. I can delete like 10 files at a time, if i try to delete say 50 nothing happens, windows shows it deleting but i never gets deleted

---

### Post by nad on 2005-08-20
I would suggest that you log into the server to perform maintenance of this magnitude.

---

### Post by Velox Letum on 2005-08-20
I haven't used Samba much in the past, but is there some sort of hard-limit flood prevention? It would certainly help stop anyone who got into your Samba share from doing too much damage.

---

### Post by LordHunter317 on 2005-08-21
Make sure you're hitting F5 in explorer, it doesn't update automatically in all cases, or are you saying the delete idalog never comes up at all?  If so, that's a misconfiguration or a bug... post your entire smb.conf.

---

