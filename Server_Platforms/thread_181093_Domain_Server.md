---
title: "Domain Server?"
date: 2006-05-23
forum: Server Platforms
---

### Post by srg0425 on 2006-05-23
I a new to linux and I have been trying to set up a domian server but after trying several sets of instructions on how to do this i have had no luck.  

Maybe a domain server is not what I need.  I have 5 computers connected to my network, including the one that is running abuntu.  For the most part the users of these computers use the same computer.  However, there are time they switch computer and I want their documents to go with them.  RIght now I just use Windows fill sharing but their is a major draw back to this, if the computer they normall use is not on they can not access the files.  

I want to make it so that when anyone in my house goes to a computer they login and their files will show up a network drive on the computer they are on.  All the computers they would be using to access the file are running Windows XP and they have the latest patches and updates installed.  

What is the best way to do this?

Was a right in thinking it is a domain server and if so how do I set this up?  

Thanks in advance for your help

---

### Post by Iowan on 2006-05-23
A domain server may not be as important to you as file storage.  Aside from some NAS servers (FreeNAS and NASlite come to mind), a file server running Samba may be what you're looking for.

My bad... I read domain server and brain hears domain ***controller**.*

---

### Post by basketcase on 2006-05-24
In a Windows environment this is called roaming profiles...Not sure if it is offered in a Linux environment.  

Good luck!!

Here is a quick google

[http://www.linuxselfhelp.com/HOWTO/LDAP-HOWTO-6.html](http://www.linuxselfhelp.com/HOWTO/LDAP-HOWTO-6.html)
[http://www.redhat.com/archives/k12osn/2002-June/msg00509.html](http://www.redhat.com/archives/k12osn/2002-June/msg00509.html)

---

### Post by Glut on 2006-05-24
With a Windows domain you can either automount a roaming profile, or mount a shared drive on login. You can do the same on linux using NFS with automount, or pam with smbmount, I've heard that it's doable with fuse but I haven't looked into it. 
ALL of these options are too much for 5 users. You're best off having a smb share somewhere and mapping it, say as a shared drive on windows or a network share on ubuntu on each profile on each computer. it's 30 seconds per user per machine  == 5*5*.5 == 12.5 minutes, You could have done it in a coffee break.

The other options require a proper AD domain (in the case of windows) or much fiddling (in the case of linux)

---

### Post by Iowan on 2006-05-25
[QUOTE=srg0425] if the computer they normall use is not on they can not access the files. [/QUOTE]IF there is a machine that will be left on, it could be used to share files - either a Windows box with sharing enabled or a Linux box running Samba.

---

