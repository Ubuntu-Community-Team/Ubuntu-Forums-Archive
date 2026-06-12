---
title: "set up ubuntu server on windows client/server network as server?"
date: 2008-11-11
forum: Server Platforms
---

### Post by kefurd06 on 2008-11-11
i've got a small college project to do, and i was hoping i could do it with ubuntu! the situation is that a client wants to upgrade their p2p network to client/server, and i'm given a 2 year old PC to make the server for the client/server network. can it be done? suggestions? 

i've gotten as far as installing ubuntu server on VMWare with the option for samba (not sure if i need it or not).

thanks for any advice. KE

---

### Post by Coreigh on 2008-11-11
Is this to be a login server or just a file server? Is it a Windows network with a Windows Domain Controller or just a mixed network with Windows and Linux (and Mac) computers?

To do straight up file sharing is easy, you have Samba. There are several tutorials available for creating a login server and for creating a Windows Domain member server. 

Google is your friend look for Ubuntu Join Domain and/or Ubuntu login server LDAP.

---

### Post by kefurd06 on 2008-11-11
> **Coreigh said:**
> Is this to be a login server or just a file server? Is it a Windows network with a Windows Domain Controller or just a mixed network with Windows and Linux (and Mac) computers?

To do straight up file sharing is easy, you have Samba. There are several tutorials available for creating a login server and for creating a Windows Domain member server. 

Google is your friend look for Ubuntu Join Domain and/or Ubuntu login server LDAP.

honestly my biggest problem was knowing the right words to google. my understanding of the network is that it's p2p, and i'm going to assume all of the computers on the network run windows xp. i'll do some googling. thanks coreigh!

---

### Post by Iowan on 2008-11-11
Because it's homework, I'll let you do the forum search.  Hint: use the Advanced Search, keyword peer, username Stormbringer.  It's starting to get a bit dated, but still a good starting place.

---

### Post by kefurd06 on 2008-11-12
> **Iowan said:**
> Because it's homework, I'll let you do the forum search.  Hint: use the Advanced Search, keyword peer, username Stormbringer.  It's starting to get a bit dated, but still a good starting place.

i appreciate the help. i don't know if the post i found that you hinted at ([http://ubuntuforums.org/showthread.php?t=202605&highlight=peer]("http://ubuntuforums.org/showthread.php?t=202605&highlight=peer")) applies to a client/server network where the clients are windows boxes and the login server is a linux box. did i misread the post, or am i misunderstanding some concepts?

---

### Post by Iowan on 2008-11-13
That's the one - it's a basic Samba-sharing setup.  I didn't notice the requirement for a login server. That complicates things a bit - I presume you'll want information on [LDAP Client Authentication]("https://help.ubuntu.com/community/LDAPClientAuthentication") or [Open LDAP Server]("https://help.ubuntu.com/community/OpenLDAPServer").

---

