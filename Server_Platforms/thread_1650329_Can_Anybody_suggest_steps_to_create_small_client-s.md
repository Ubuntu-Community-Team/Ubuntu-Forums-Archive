---
title: "Can Anybody suggest steps to create small client-server network environment?"
date: 2010-12-21
forum: Server Platforms
---

### Post by crazymoonboy on 2010-12-21
Hi,

I have experience in Linux as developer and not as an administrator. I downloaded and installed Ubuntu 10.10 (64 Bit) Server edition and installed. All of my systems are in Local Area Network (LAN). Now, I want to do the below things:

**Work Environment:** 

Server System: Ubuntu 10.10 (64 Bit) Server Edition
Client Systems: Windows XP

1) Setup DNS Server
2) Setup directory like Active Directory (Like Windows 2003 Server)
3) File and Folder sharing to the client systems users from the server
4) Every client user should come into the one domain
5) We create user names (login name) and passwords in the Ubuntu server
6) If I want to login to my PC, I should enter the user name and password and select the domain name also.

After reading some stuff, I understand a bit that we can implement all of the above using Samba, Bind etc... (Not sure)

**My Problem:**

What First? What Second? Can anybody suggest me step by step services that I need to setup?

Thanks in advance.

Regards,
Chandra.

---

### Post by TSJason on 2010-12-21
I would suggest to first setup DNS (Bind) and OpenLDAP. You will integrate services with LDAP as you install them so you'll want that ready and functional. All user accounts will be created (or imported if you already made the mistake of creating them as unix accounts)into your LDAP database. 

Once those are working properly, you'll move on to the samba setup. You'll want to use the Primary Domain Controller (PDC) method for samba with LDAP database back-end for your Windows workstation domain integration (roaming profiles, login scripts, etc.). Samba will also be used as your file sharing service.

---

### Post by drdos2006 on 2010-12-21
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by crazymoonboy on 2010-12-22
Hi Jason and Kevin,

Thank you for your reply. I will follow your guidelines and try to implement.

Regards,
Chandra

---

### Post by HugoSerrano on 2010-12-22
You can also use something like [http://www.zentyal.org/](http://www.zentyal.org/)
But you will not acquire the same level of knowledge then doing it like TSJason suggested.

---

### Post by gordintoronto on 2010-12-22
> **drdos2006 said:**
> Here is a HOWTO which I found comprehensive and invaluable.

regards

However, that how-to does not create a domain controller.

---

### Post by crazymoonboy on 2010-12-23
Hi,

I installed base system of Ubuntu server edition 10.10 (64 bit) and not getting GUI. What I have to do? I installed XServer. But, not getting GUI. 

Thanks in advance.

Regards,
Chandra

---

### Post by HugoSerrano on 2010-12-23
well... you going against the essence of the thing, but you can install it doing this:
$apt-get install gnome-desktop-environment

I think you can choose it too in one menu in the install process.

---

### Post by crazymoonboy on 2010-12-23
Hi,

As you said, I installed "gnome-desktop-environment" and getting GUI now. Thank you.

Regards,
Chandra

---

