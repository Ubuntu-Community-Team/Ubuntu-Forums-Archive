---
title: "Add users form another Ubuntu box in to Server Groups"
date: 2010-11-30
forum: Server Platforms
---

### Post by lmicu on 2010-11-30
Here is my question:

I have a server 192.168.1.14 (I will call it 14) it runs Ubuntu server 10.04 and I have my Ubuntu Laptop 192.168.1.3 ( I will call it 3) that runs Ubuntu 10.10.

I need to find a way to add users from my Laptop (user X) or a Windows machine user (Y). 

What I am trying to accomplish is to have file permissions some for Y only and some for X only and some for a group that contains X and Y. 

Now I have a Dir, on the server 14, with the owner Z (server user) and I gave it permission 760. Now my user X, from Laptop 3, (they have the same name in real life) is not able to access those files on a NFS share.

I would like to have the 760 perm and be able to access those files without doing a 777. I am thinking to add all users (XYZ)to a group and give read permissions for the group. My dilemma comes when the users are on different machines.   

PS: I already created equal users on server with the same name but it does not do the trick. When connecting to server from 3 I can't access files that are owner by the group where user Z belongs (even if user X has the same name and password).

I am thinking there has to be a deeper way of identifying users.

---

### Post by capscrew on 2010-12-01
> **lmicu said:**
> Here is my question:

I have a server 192.168.1.14 (I will call it 14) it runs Ubuntu server 10.04 and I have my Ubuntu Laptop 192.168.1.3 ( I will call it 3) that runs Ubuntu 10.10.

I need to find a way to add users from my Laptop (user X) or a Windows machine user (Y). 

What I am trying to accomplish is to have file permissions some for Y only and some for X only and some for a group that contains X and Y. 

Now I have a Dir, on the server 14, with the owner Z (server user) and I gave it permission 760. Now my user X, from Laptop 3, (they have the same name in real life) is not able to access those files on a NFS share.

I would like to have the 760 perm and be able to access those files without doing a 777. I am thinking to add all users (XYZ)to a group and give read permissions for the group. My dilemma comes when the users are on different machines.   

PS: I already created equal users on server with the same name but it does not do the trick. When connecting to server from 3 I can't access files that are owner by the group where user Z belongs (even if user X has the same name and password).

I am thinking there has to be a deeper way of identifying users.

Each system uses UID/GUID for the users and groups.  The name is really an alias.  If you match the UID/GUID numbers it should work.  These are matched accounts NOT the same account even with the matched user ID numbers.  I have my system set up that way rather than a centralized user setup.

---

