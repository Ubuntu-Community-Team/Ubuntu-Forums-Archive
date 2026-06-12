---
title: "Need some help with users and groups and samba."
date: 2008-09-08
forum: Server Platforms
---

### Post by grs on 2008-09-08
I'm trying to learn about users and groups in Ubuntu Server.
I've created a few users and groups, and was trying out permissions as in the Ubuntu Server guide. 

I ran the following while logged in as grs, after createing a user called test:-

```

sudo chmod 0750 /home/test

```

Now I can't access /home/test. How can I undo the permissions I changed, the guide only covers the very basics, as I've found out!!

Is there then a second list of users for samba or are the system users automatically added to samba?

---

### Post by grs on 2008-09-08
I've managed to work out the file chmod permissions.
With samba I have managed to add the folders I want to access from my Windows PC and I can see the in Windows Explorer but I can't see there contents yet.
I'm still having trouble with the samba users/groups. I can add a use but there is no smbpasswd files in /etc/samba

---

### Post by cdenley on 2008-09-08
> **grs said:**
> I've managed to work out the file chmod permissions.
I'm still having trouble with the samba users/groups. I can add a use but there is no smbpasswd files in /etc/samba

Samba doesn't use the smbpasswd files by default anymore. Instead, it uses tdbsam.
```

sudo pdbedit -L -v

```

---

### Post by grs on 2008-09-08
what does that code do for it?

---

### Post by cdenley on 2008-09-08
> **grs said:**
> what does that code do for it?

It lists all the settings for all your users. pdbedit can also be used to change those options.
```

man pdbedit

```
What exactly are you trying to accomplish?

---

### Post by grs on 2008-09-08
File sharing.

That command you gave me lists the users and their details how do incorporate that informatio into samba?

I don't think pdbedit was mentioned in the Server guide

---

### Post by cdenley on 2008-09-09
> **grs said:**
> File sharing.

That command you gave me lists the users and their details how do incorporate that informatio into samba?

I don't think pdbedit was mentioned in the Server guide

That information is in samba! If the guide you are referring to mentions /etc/samba/smbpasswd, then the guide is outdated. As I mentioned, samba uses tdbsam by default. Data is stored in binary database files in /var/lib/samba. You cannot edit these with a text editor, and must use the pdbedit and smbpasswd commands. If you want to use an outdated method for configuring your samba users, then change "passdb backend" to "smbpasswd" in smb.conf.

```

man pdbedit
man smbpasswd

```

---

### Post by grs on 2008-09-09
I'll work with the curent version, I didn't realise it had been updated.
I'll read up on it some more.
Thanks

---

### Post by grs on 2008-09-09
I'm still not really getting this. I've had a read through the manuals but I don't fully understand what I'm trying to achive.
When I type

```
sudo pdbedit -L -v
```

I can see the one user and details for that use, called grs. In Windows Explorer on my Pc I can see the Ubuntu Server listed under My Network places but I can't access it, says I don't have permissions(?) Is there something in smb.conf if I should be setting?

---

