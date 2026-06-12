---
title: "File server part of a Domain"
date: 2010-02-14
forum: Server Platforms
---

### Post by Rokurosv on 2010-02-14
So I think I posted this in another section but since I'm planning to install Ubuntu Server I might post it here.

So What I'm trying to achieve is to create a File server where people can pass around documents and files, but since we're on a Windows environment at work I need integration with my Active Directory for access permissions. I've configured Samba for a LAN but I've never done it for a Domain. 

Now I've read several guides and most suggest using Samba + Kerberos + Winbind to join the domain. I've read the official Samba wiki and tried all the recommended configs [http://wiki.samba.org/index.php/Samba_%26_Active_Directory](http://wiki.samba.org/index.php/Samba_%26_Active_Directory)

Now what I've done is after I enter wbinfo -u or -g I can see all of my AD users and groups. But I can't seem to configure a share, I've tried to configure a test folder but everytime I try to access my linux box from a windows machine I get a "no process is on the other end of the pipe" error.

I was also reading something about likewise and how it can integrate Linux UIDs with Windows SIDs. Perhaps someone can point me to a good resource to match Samba + Likewise?

So has anyone configured a share like this successfully? Where I can have directories with Group permissions just like I would on a Windows Server? 

Thanks for your time

---

### Post by Satoru-san on 2010-02-14
Even better than that is a simple **ftp** server, ftp works on windows linux and mac, and if you do so decide, you can open it up to the world so people can upload and download from home.

---

### Post by koenn on 2010-02-14
try these:
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm)
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm)

---

### Post by Rokurosv on 2010-02-14
> **Satoru-san said:**
> Even better than that is a simple **ftp** server, ftp works on windows linux and mac, and if you do so decide, you can open it up to the world so people can upload and download from home.

Well that would be nice but I want something that integrates the way the users have been working with, just hiting a link and accessing the desired folder, it could work for us but I don't think it will work for the rest of the company

---

### Post by Rokurosv on 2010-02-14
> **koenn said:**
> try these:
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba2.htm)
[http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/samba4.htm)


Thanks man I'll look them up

---

