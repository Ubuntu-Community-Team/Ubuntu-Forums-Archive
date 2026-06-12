---
title: "Samba and Windows Sharing"
date: 2010-02-19
forum: Server Platforms
---

### Post by halit.yilmaz on 2010-02-19
Hi,

I've installed Ubuntu Server 7.10 Gutsy and Webmin 1.500 on it. The thing that I want to do is:

I want to share a folder an sub folders for windows users ( guest user)
I should modify those folders from my ubuntu desktop 9.10 karmic

they are all same folders. Is it possible? if yes how can i make it.

you can tell from webmin or samba configuration file.

Thank you

---

### Post by isecore on 2010-02-19
First off, why did you install such an old (outdated) version of Ubuntu Server? There's no security updates for it, and no support whatsoever. It passed it's end of life a long while back.

Secondly, setting up a samba share is fairly easy, but this depends on a few different things. I'm a bit fuzzy on what you're trying to accomplish, but sharing a folder using Webmin to setup Samba is a fairly straightforward business.

Help me out with some more details, that would help.

---

### Post by halit.yilmaz on 2010-02-19
i'm a newbie on linux. so ubuntu server 7.10 was the only server platform that i had. anyway. i have 9.10 karmic desktop now. 

when i type \\server\ADMIN$ on windows machine for windows server i can write and delete files on it. 

I have a shared folder on Documents folder. i want windows users to browse folder. but i want to add new file, delete or update existing files on server. 

do you know how i can make it. 

ubuntu 9.10 desktop is installed on my laptop and on the machine that i will use as server.

thanks

---

### Post by Morbius1 on 2010-02-19
> [COLOR=Blue]I have a shared folder on Documents folder[/COLOR]. i want windows users to browse folder. but i want to add new file, delete or update existing files on server.How did you share the Documents folder?

Please post the output of the following commands, It will tell us what method you're using to share and how you are sharing it:

Open **Terminal**
Type **net usershare info**
Type **testparm -s**

---

### Post by halit.yilmaz on 2010-02-19
right clicked on folder. i checked "share this folder" and "Guest Account" on share tab.

[dökümanlar]
path=/home/letoon/Belgeler/Dökümanlar
comment=
usershare_acl=Everyone:R,
guest_ok=y


Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
    server string = %h server (Samba, Ubuntu)
    map to guest = Bad User
    obey pam restrictions = Yes
    pam password change = Yes
    passwd program = /usr/bin/passwd %u
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    unix password sync = Yes
    syslog = 0
    log file = /var/log/samba/log.%m
    max log size = 1000
    dns proxy = No
    usershare allow guests = Yes
    panic action = /usr/share/samba/panic-action %d

[printers]
    comment = All Printers
    path = /var/spool/samba
    create mask = 0700
    printable = Yes
    browseable = No
    browsable = No

[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

---

### Post by Morbius1 on 2010-02-19
> i want windows users to browse folder. but i want to add new file, delete or update existing files on server. OK, it appears you're using Nautilus-share but your share is not configured properly:
> [dökümanlar]
path=/home/letoon/Belgeler/Dökümanlar
comment=
[COLOR=Blue]usershare_acl=Everyone:R[/COLOR],
guest_ok=yThis is set up to "Read Only"

Go back into nautilus, right click on /home/letoon/Belgeler/Dökümanlar, select "Sharing Options" and make sure all boxes are checked.

If you still cannot get access then it may not be a Samba issue it may be a linux permissions issue. If so please post the output of this command:

ls -al /home/letoon/Belgeler/Dökümanlar

---

### Post by halit.yilmaz on 2010-02-19
if i check all boxes on sharing options everbody can makes changes on files. i don't want it. 

windows users will be able to see and copy files on server.
i use ubuntu 9.10 on my laptop. i want to have root privileges on it and add documents, folders, files etc.

imagine this. 
there are one linux machine ( i use it to share files), one linux machine ( my laptop - ubuntu 9.10 installed on it) and 35 windows machines  on my lan.

nobody can use server machine, 
i should add folders and files on it from my laptop.
windows cliens should see the files only.

we will work on the same folder.

i can make it on windows machine like this \\server_name\c$  so i have administrator privileges on that machine. i want to do the same thing on ubuntu.

Thanks.

---

### Post by Morbius1 on 2010-02-19
First, my apologies. I completely misunderstood the nature of the problem.

Second, what you are trying to do is not possible using Nautilus-share ( right click on a folder and selecting "Sharing Options ). The Nautilus-share share definitions are limited to everyone can access or everyone needs to authenticate. What you are trying to do requires Classic Samba.

Third, I completely missed the forum that you're in - "Server Platforms" or else I wouldn't have responded. I'm strictly a home networking person.

I have used the " write list =" option in the share definition of classic samba before to allow only one user to write to an otherwise read only share but that share required authentication for all users. I don't think adding something like this in smb.conf will work by itself:

> [sharename]
comment = Any comment you like
path = /home/user/Documents
guest ok = yes
writeable= no
write list = johnWhere john is the only user that can write to the share.

---

### Post by halit.yilmaz on 2010-02-20
thank you very much. 

you've solved my problem. thanks a lot

:)

---

