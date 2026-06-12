---
title: "Multiple samba shares with different permissions"
date: 2012-01-10
forum: Server Platforms
---

### Post by elo_b on 2012-01-10
Hi everyone,

I'm making a file server under ubuntu server LTS with two shared folders, say fileX and fileY. I created two samba users x (network share: /home/x/fileX, group x) and y (network share: /home/y/fileY, group y). 

I want to make it possible that when you log in as user x, you also have access to the shared folder y. In my case windows gives problems with different users on the same server. So its either access to fileX or fileY (with ubuntu I dont have that problem, you just give usernames and passwords and you can read the two files at the same time).

To accomplish that I used the "gpasswd -a x y" command and added user x to the group of user y.

When you do the "groups x" command you see that user x is also menber of the y group. I also adapted the permissions for /home/y to drwxrw----.

When I try to get access via the x user to fileY it always gives "access denied".

I wonder if this is the right approach of this problem

thanks

---

### Post by Morbius1 on 2012-01-10
> I also adapted the permissions for /home/y to drwxrw----
But /home/y isn't shared.

What are the ownership and permissions of /home/y/fileY ?

And can you show us that actual share definition for [fileY].

---

### Post by elo_b on 2012-01-10
In smb.conf I have:

[fileY]
writable=yes
path = /home/y/fileY

permissions for fileY: drwxrw----

---

### Post by Morbius1 on 2012-01-10
You did add the user to the samba database , right?
```
sudo smbpasswd -a x
```

---

### Post by kevinthecomputerguy on 2012-01-10
[http://woodel.com](http://woodel.com)

---

### Post by elo_b on 2012-01-11
Yes I did make samba users for x and y, the shared files are both accessable in windows, but when logged in as user x I dont have access to fileY, not in shell linux, and not in windows.

---

