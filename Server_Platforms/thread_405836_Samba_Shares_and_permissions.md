---
title: "Samba Shares and permissions"
date: 2007-04-10
forum: Server Platforms
---

### Post by AnyOne on 2007-04-10
Dear members, today I'm currently changing my fileserver here in my work to an ubuntu server machine, although, my linux knowledge is not very extense, I'm having some problems regarding Samba permissions.

Here's the deal, the real problem is not the main share, let me try to explain, my problem is the sub directory of the shares, here's goes:


Share - everyone access
Share\Folder 1 - user 1 and 2 have access, all the others do not
Share\Folder 1\UserPersonal - only user 1 have access all the others do not
Share\Folder 2 . user 2 and 3 have access, all the others do not
Share\Folder 3 - everyone access

I've read samba documentation and i cant find nothing related to sub directory configuration, can some1 give me an hand on this?

---

### Post by Kaput1982 on 2007-04-10
It probably isn't a problem with Samba.  Have you checked your folder permissions?  You may have to use the [chmod]("http://en.wikipedia.org/wiki/Chmod") and the [chown]("http://en.wikipedia.org/wiki/Chown") command.  chmod will change the permissions on the folder and chown will change the owner.  If you don't know how to use them check their man pages or click the links.  If you have any questions let me know.

---

### Post by Tylo on 2007-04-10
I've been messing around with Samba lately myself. You may have to set up group accounts through Samba. I'll look into this later on tonight and get back to you.

---

### Post by Tylo on 2007-04-11
Hey. Something things have come up and I won't be able to look this up for a little while. I'll get back here when/if I find it.

---

