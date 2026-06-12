---
title: "Replace Windows AD Domain"
date: 2010-05-29
forum: Server Platforms
---

### Post by badger_fruit on 2010-05-29
Hello
At home I am using a Windows Server 2003 as Domain controller with  Active Directory. My "client" computers are all currently running  Windows XP.  They all require CONTROL-ALT-DELETE and the user to enter  their credentials before they will allow logon.

Shared files reside on various other Server 2003 machines and have  restrictions on so only specific users can access certain resources.

For example, I have the family finances and other important documents in  a share named 'Private-Files', only members of the 'PrivateFiles'  global group have access.  Likewise, I have my movies sorted into their  appropriate age categories - after all, I don't want my 5 year old son  accidentally watching Aliens!

So this all works but the copies of Windows XP and  Server 2003 are far from legitimate.  I want to go legal and the only  real way I can afford to do this is to switch over to Linux.

The problem is, although I can install the OSes, I have no idea where to  proceed from there - for example, how do I create a Domain? Where and how do I create domain users and groups? How do I set  permissions on shares for the domain users?

**Please, can someone point me to docs or help out here in the forum  (so others can see the results and problems run into for avoidance etc  in the future)?**

---

### Post by Lucky. on 2010-05-29
I believe that with NFS and Kerberos, you can set up an AD-like central authentication for linux clients & servers.  I'm really interested in learning / trying to do this myself, but I haven't had the time yet.

[Here's a link on the subject](https://help.ubuntu.com/community/NFSv4Howto), but it looks kinda hard to follow.  It covers both basic NFS and NFS + Kerberos (which is what I think you want).

Here's [another link too](https://help.ubuntu.com/community/SingleSignOn), but I'm not sure if this is the trick.  Sheesh, the whole process is daunting.  If I ever figure it out one of these decades, I'll be posting my own how-to.

---

### Post by HermanAB on 2010-05-30
Go to the Samba project web site and read the Official Howto.  It is all in there.  Other AD docs on the web typically have half the story and lots of wrong or misleading statements.

The other option is to quit the Windows addiction cold turkey and use Yellow Pages (Prehistoric), NIS (ancient), plain LDAP (old) or PAM MySQL (new).

---

### Post by Lucky. on 2010-05-30
If I understand correctly, I don't think he's asking about using AD with Samba.  I think he wants an open source alternative for the whole deal to use when he switches both clients and servers (as do I).

---

### Post by badger_fruit on 2010-05-30
> **Lucky. said:**
> If I understand correctly, I don't think he's asking about using AD with Samba.  I think he wants an open source alternative for the whole deal to use when he switches both clients and servers (as do I).

Correct, this is for a complete replacement as opposed to something to work with my existing setup.
A new domain will need to be created, new users, shares, permissions and so on but how to do this, well, that's beyond me (in Linux anyway!)

---

### Post by CharlesA on 2010-05-30
I think you can set something up like that in Samba 4 (using Samba as a DC), but that's still in alpha as far as I know.

---

### Post by SteveHillier on 2010-08-27
Hi guys,
I know this thread may be old but anyway....

I support a number of win 2003 server installations and am reasonable fluent in making them work.  I have installed one Win 2008 server and don't like it (it suffers from all the faults of Vista and few of its advantages)

So, I am in a similar market place.  I have looked at a couple of Linux systems.  ClearOS (Clearfoundation.com) and e-box.  I am prefering ClearOS (Centos/Redhat based).  It is easy to set up and easier to do the basic tasks that are required of a domain server.

If you have run a Windows domain server then you will kniow the sorts of things you have to do and then it is a case of finding it in the ClearOS web interface.

Hope this helps

---

### Post by headvampyre@hotmail.co.uk on 2010-08-29
If your looking for a replacement, try samba4 [http://wiki.samba.org/index.php/Samba4](http://wiki.samba.org/index.php/Samba4) its currently only in alpha stages, but it works flawlessly for me, and it supports 2000 style domains all the way to server 2008_R2 style domains, ive followed that uide and its perfect, and easy to follow.
Hope This Helps

---

