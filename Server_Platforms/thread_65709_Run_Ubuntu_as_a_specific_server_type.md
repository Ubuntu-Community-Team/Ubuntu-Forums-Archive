---
title: "Run Ubuntu as a specific server type"
date: 2005-09-14
forum: Server Platforms
---

### Post by slooksterpsv on 2005-09-14
Is there any way to run Ubuntu as a server where users login (I want to use LDAP for this) they authenticate with the server I want to set up? I would also like File Services to be availalbe. Also, I would be able to store Home Directories on the server (like how you do with Mac OS X Server), but that comes with File Services, or should at least.

Server; Use for files, home directories, user authentication via LDAP
What machine I'll use: My AMD Duron would be the PC I'd use.
What I need though: On the server I would still need Gnome and KDE to administer the server.

---

### Post by LordHunter317 on 2005-09-14
Installing libpam-ldap would get you 90% of the way to doing LDAP authentication.  

You didn't say what protocol needs to be used for serving home directorys.  For Windows or Linux, use Samba.  For other UNIX, probably use NFS.  For OS X, I'm not sure what's best.

And I don't see why you'd need a GUI on the server itself.

---

### Post by Glut on 2005-09-14
We're running pam-ldap for account control quite well, although we use kerberos for authentication itself. We have all our home directories on various servers using a combination of samba and nfs. 
Automount mounts the home directory and I believe that the automount man page has an excellent example of doing just this. We had some issues with mounting the directories as windows profile directories, so it now just gets mounted as a network drive.
From memory our OSX users use NFS.

So it's all possible, and done in practice on a large scale. I'd also question your need for a gui on the server, but simply installing the default ubuntu install would work for that case.

---

### Post by slooksterpsv on 2005-09-14
[QUOTE=Glut]We're running pam-ldap for account control quite well, although we use kerberos for authentication itself. We have all our home directories on various servers using a combination of samba and nfs. 
Automount mounts the home directory and I believe that the automount man page has an excellent example of doing just this. We had some issues with mounting the directories as windows profile directories, so it now just gets mounted as a network drive.
From memory our OSX users use NFS.

So it's all possible, and done in practice on a large scale. I'd also question your need for a gui on the server, but simply installing the default ubuntu install would work for that case.[/QUOTE]
 The main reason for that is because I will be using that server, even though its acting as an LDAP server. My sister uses my iBook so when she's on that, I'll be using the server to run my apps and that, like talking to people on gaim and that.

---

