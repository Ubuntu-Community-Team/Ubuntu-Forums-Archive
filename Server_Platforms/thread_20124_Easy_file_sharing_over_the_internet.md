---
title: "Easy file sharing over the internet"
date: 2005-03-15
forum: Server Platforms
---

### Post by Berkut on 2005-03-15
Hi.
I'am searching for an easy way to share my files in Ubuntu to a friend on WinXP over the internet (and maybe the other way too). I tried it with Openssh, but that's a bit hard to configure for me (is there a gui for the server?). What would be the easiest way? I mean something like sharing a folder (like in nutilus for the local network).
Something like Spike would be cool ( [http://www.porchdogsoft.com/products/spike/](http://www.porchdogsoft.com/products/spike/) ) but its only for Win and Mac (and i don't have a credit card).

Thank you for any sugestions!

---

### Post by deuce868 on 2005-03-15
What I do is create a webdav directory with apache. Then there is a tool for windows called NetDrive from novell. It will map the webdav directory as a drive in windows like Z:\.

There are several good tutorials on setting up webdav just look around.

---

### Post by Berkut on 2005-03-15
That seems to be it! I'am reading the tutorials now.
Thanx Deuce.

---

### Post by JaF on 2005-05-19
You could always try [http://www.yousendit.com/](http://www.yousendit.com/) you can send files up to 1GB and its useful for one off transfers etc.

---

### Post by WimVriend on 2005-07-07
[QUOTE=Berkut]Hi.
I'am searching for an easy way to share my files in Ubuntu to a friend on WinXP over the internet (and maybe the other way too). I tried it with Openssh, but that's a bit hard to configure for me (is there a gui for the server?). What would be the easiest way? I mean something like sharing a folder (like in nutilus for the local network).
Something like Spike would be cool ( [http://www.porchdogsoft.com/products/spike/](http://www.porchdogsoft.com/products/spike/) ) but its only for Win and Mac (and i don't have a credit card).

Thank you for any sugestions![/QUOTE]

Hi,
Look at this one

[http://gnomefiles.org/app.php?soft_id=545](http://gnomefiles.org/app.php?soft_id=545)


I am very happy with it.
Wim

---

### Post by LordHunter317 on 2005-07-07
I recommend you don't use WebDAV, as it's a security issue on the Linux side.  You can't provide sufficent control of the permissions, currently.  Which is a crying shame.

Using SSH and SFTP is quite easy.  I don't know why you're looking for a configuration tool for the server, as there is nothing to configure.  It comes out of the box setup just fine.

---

### Post by deuce868 on 2005-07-07
How is it a security issue on the linux side? Most tutorials show you how to set it up using apache2 on https and tools like subversion use this setup all the time with no major security headaches I've seen. 

Can you point to something I've not heard about?

---

### Post by LordHunter317 on 2005-07-07
WebDAV runs as the Apache user.  This means all files are owned by the Apache user on the filesystem (not a good thing), making providing proper security rather difficult.

---

### Post by deuce868 on 2005-07-08
[QUOTE=LordHunter317]WebDAV runs as the Apache user.  This means all files are owned by the Apache user on the filesystem (not a good thing), making providing proper security rather difficult.[/QUOTE]

Well I guess we're just going to have to disagree here. What's the problem with the apache user owning the files? It happens all the time. Who else is going to own them? I'm sorry, but you just seem to be making baseless generalizations. Saying something is not a good thing just doesn't help anyone understand why at all.

---

### Post by LordHunter317 on 2005-07-08
[QUOTE=deuce868]Well I guess we're just going to have to disagree here. What's the problem with the apache user owning the files?[/quote]What if I have not one person accessing the files, but 3?  Now, I don't know who owns what files.  In a screw up, one of the users could access the others' files.

In the advent of an Apache daemon compromise, it means all that WebDAV data is vulnerable.  It's standard security practice to not have anything owned by the Apache user for that very reason: it prevents an attacker from messing with your data.

That also ignores the fact that unless you use different passwords for WebDAV access, you have to open up the permission on /etc/shadow, which is an incredibly bad idea.  Good way to get your entire box owned very quickly these days, via a rainbow-table attack on the stolen file.

This also ignores the fact that WebDAV/SSL is much harder to setup properly than SSH for SFTP, even ignoring these flaws in the implementation.

---

### Post by relix42 on 2005-07-08
Thank you for any sugestions![/QUOTE]
 Wouldn't it be easier to use FTP and the Windows "Network Place" capabities?  Or am I missing something?

---

### Post by Endolith on 2008-05-14
> **LordHunter317 said:**
> What if I have not one person accessing the files, but 3?  Now, I don't know who owns what files.  In a screw up, one of the users could access the others' files.

This also ignores the fact that WebDAV/SSL is much harder to setup properly than SSH for SFTP, even ignoring these flaws in the implementation.


But doesn't SSH/SFTP have the same flaws of allowing users to access each others' files?

---

