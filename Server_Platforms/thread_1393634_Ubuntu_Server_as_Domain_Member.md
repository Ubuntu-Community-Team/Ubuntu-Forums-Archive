---
title: "Ubuntu Server as Domain Member"
date: 2010-01-29
forum: Server Platforms
---

### Post by HugoSalvador on 2010-01-29
Friends,

I need make a file server and I chose Ubuntu Server. 

I will put this server in a LAN in my job where have PDC and BCD. I want that my file server works like a member of domain.

I will make a example: 

- workgroup: JOB
- my file server name: FILE
- my user: HUGO

The user HUGO logon in the JOB workgroup when torn on the local Windos XP. Now the user HUGO access the server FILE, this server recognize HUGO and know which directories HUGO can read or write.

How can I configure smb.conf in order to server FILE recognize the user HUGO?
How can I configure smb.conf to the server FILE know that the user HUGO can write or just read a specific directory?

---

### Post by pirateghost on 2010-01-29
i messed around with this for quite a while, and could never get it just the way i wanted.  i wound up setting up iscsi targets on my ubuntu server and presented them to my windows domain controller and just used the filesharing in windows server.

---

### Post by HugoSalvador on 2010-01-30
But I have other trouble, I am not the administrator of Windows Domain!

I guessed I could do the same thing that I do in any Windows PC in the domain: click right button on the folder that a want share, put in share settings the name user, valid it and set read/write... I knew that it will be not so easy in GNU/Linux server, but I thought that it would be possible.

Any one have other tip?

---

### Post by koenn on 2010-01-30
You're talking about PDC and BDC - so you have a Windows NT4 domain ? 
Samba can be a member server in such domain (and in Active Directory domains) - see the samba manuals or the ubuntu server manual.


> But I have other trouble, I am not the administrator of Windows Domain!

I guessed I could do the same thing that I do in any Windows PC in the domain: click right button on the folder that a want share, put in share settings the name user, valid it and set read/write... I knew that it will be not so easy in GNU/Linux server, but I thought that it would be possible.
Even in a Windows domain, you can't do that unless you're domain admin, or the domain admin has given you sufficient rights to do so. 

Also, if you're not a domain admin, you have no business adding member servers to the domain.

---

