---
title: "How to set permissions for HDD access?"
date: 2012-01-13
forum: Server Platforms
---

### Post by Aaron053191 on 2012-01-13
Ok everyone, on to my next problem.

I am trying to copy files to the HDD that is in my server from a Windows 7 PC.

Here is what pops up on Windows

[IMG]http://i43.tinypic.com/67nxb5.jpg[/IMG]

Here is what is written in my Samba config file.

[SDB HARD Disk]
comment = public folder
path = media/sdb1
public = yes
writable = yes --- Just a hunch, shouldn't this line let me move files around?
create mask = 0777
directory mask = 0777
force user = SuperUser
force group = homeusers

All I tried to do was drag a photo from my desktop to the server to test if it would let me transfer files, and it would not.

Everything Linux is unknown to me right now. I have never had any association with it, but I thought it would be worth a shot to have some extra data storage and gain some experience. I appreciate all of the help that may be provided.

-Aaron

---

### Post by arrrghhh on 2012-01-13
> **Aaron053191 said:**
> Ok everyone, on to my next problem.

I am trying to copy files to the HDD that is in my server from a Windows 7 PC.

Here is what pops up on Windows

Here is what is written in my Samba config file.

[SDB HARD Disk]
comment = public folder
path = media/sdb1
public = yes
writable = yes --- Just a hunch, shouldn't this line let me move files around?
create mask = 0777
directory mask = 0777
force user = SuperUser
force group = homeusers

All I tried to do was drag a photo from my desktop to the server to test if it would let me transfer files, and it would not.

Everything Linux is unknown to me right now. I have never had any association with it, but I thought it would be worth a shot to have some extra data storage and gain some experience. I appreciate all of the help that may be provided.

-Aaron

Well, let's start with a simple setup.  You can "see" the share, so that's a good start.  Let's modify the share a bit:

```
[SDB HARD Disk]
comment = public folder
path = **/media/sdb1**
public = yes
writable = yes
guest account = nobody
guest ok = yes
create mask = 777
directory mask = 777
```

I added a few things, removed a few things... I think the most important piece is the path = however, I bolded it.  You should have a forward slash before media, /media/sdb1...

After making that change restart smb and try again:

```
sudo service smbd restart
```

---

### Post by Aaron053191 on 2012-01-13
I made those following changes, restarted SMB. Then I attempted to drag the file to the server once again. Yet, it is still telling me I do not have permissions to do so.

---

### Post by arrrghhh on 2012-01-13
> **Aaron053191 said:**
> I made those following changes, restarted SMB. Then I attempted to drag the file to the server once again. Yet, it is still telling me I do not have permissions to do so.

Hrm...

This is insecure, but if you trust everyone on your LAN, change ```
security = user
``` to ```
security = share
``` in smb.conf.

Also, perhaps you should try restarting nmbd...

```
sudo service nmbd restart
```

Of course if you made a change to smb.conf, you should restart smbd again as well.

If you'd like to read where I'm getting this from, here's the pages I'm using:

[https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/11.04/serverguide/C/samba-fileserver.html)

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)

Edit - as a troubleshooting step, paste the output (in [ code] braces) of your complete smb.conf, and the result of these commands:```
testparm
``````
smbtree
```

Hopefully some others will chime in, I'm far from an expert with samba... (you might want to put something about samba in the title, otherwise people won't know ;)) I typically just do the Webmin configuration and forget about it :(.

---

### Post by Morbius1 on 2012-01-13
It may not be permissions by Samba. It may be permissions by Linux.

What are the ownership and permissions of the target shared folder:
```
ls -dl /media/sdb1
```

---

### Post by Aaron053191 on 2012-01-13
> **Morbius1 said:**
> It may not be permissions by Samba. It may be permissions by Linux.

What are the ownership and permissions of the target shared folder:
```
ls -dl /media/sdb1
```

Thanks for the help, I re-installed Ubuntu and followed a tut on howtoforge.com

I used the ls -dl /media/store (changed due to tut)

and it looks it is owned my root if I am not mistaken.

It says exactly    drwxrwrwx 1 root root 4096 2012-1-13 7:01

I'm pretty sure I need to change the ownership or something?

I am sorry, I have found that I am following step by step tutorials and it is not teaching me exactly what I am looking at because I am acting as a programmed robot that is simply repeating a command.

---

### Post by Aaron053191 on 2012-01-13
Closed, not sure quite what I done, but I now have access to the folders and am transferring data right now. :D

---

