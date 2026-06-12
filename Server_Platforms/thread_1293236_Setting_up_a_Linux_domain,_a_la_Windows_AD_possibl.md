---
title: "Setting up a Linux domain, a la Windows AD: possible?"
date: 2009-10-16
forum: Server Platforms
---

### Post by djbon2112 on 2009-10-16
I know a fair bit about Windows Active Directory domains, and I love what you can do with them, things like roaming profiles and group policies. I was wondering if there's something like that I can set up for Ubuntu. I currently have a server running Debian, and 2 computers running Ubuntu 9.04, but I'm about to add a third and upgrade them all to 9.10. I'd like things like roaming profiles so I can log on to any of the computers with my account, plus group policies to do things like block sites and programs to certain users on certain computers. Partial integration with Windows (one computer runs Windows 7) would be amazing but I'm not going to hold my breath ;)

I've read about LDAP and how AD uses a (modified) version of it, and was looking at putting OpenLDAP on the server, but I've got no idea where to even begin setting this kind of thing up, if it's even possible!

Any advice would be appreciated :)

---

### Post by Vegan on 2009-10-16
SAMBA can help with a Windows client or 12. You can use it with a Windows Server or standalone as you want.

---

### Post by R.Bucky on 2009-10-16
Check out likewise-open. I used it at work to join Ubuntu 9.04 to the domain.

---

### Post by drumbug1 on 2009-10-17
You certainly can setup something similar to AD, but what you'll find is that there is no single way to do this.  I've been researching and testing the same idea on my test network.  I currently have a server running OpenLDAP for directory services (admin via phpLdapAdmin) and I recently started testing storing the profiles on a NFS share on the same server.  This gets you close to roaming profiles, but doesn't do any caching/copying - it just accesses it directly over the network.

I'd take a close look at the official 'server guide' documentation.  That should get you most of the way (these are the Jaunty guides):

[https://help.ubuntu.com/9.04/serverguide/C/network-authentication.html](https://help.ubuntu.com/9.04/serverguide/C/network-authentication.html)

[https://help.ubuntu.com/9.04/serverguide/C/network-file-system.html](https://help.ubuntu.com/9.04/serverguide/C/network-file-system.html)

As far as group policy goes:  I haven't gotten that far, but I think you'd be looking at more of a script-type setup.  One of the powerful things about linux (or UNIX) is that you can remotely login and change *any* config file on the system (unlike windows where most everything is stored in the registry).

---

### Post by djbon2112 on 2009-10-17
> **Vegan said:**
> SAMBA can help with a Windows client or 12. You can use it with a Windows Server or standalone as you want.

> **R.Bucky said:**
> Check out likewise-open. I used it at work to join Ubuntu 9.04 to the domain.

I'm trying to eliminate Windows as much as possible from my computers, so neither of these really matter... I want to set up a new domain, using a Linux server and only Linux clients.

> **drumbug1 said:**
> You certainly can setup something similar to AD, but what you'll find is that there is no single way to do this.  I've been researching and testing the same idea on my test network.  I currently have a server running OpenLDAP for directory services (admin via phpLdapAdmin) and I recently started testing storing the profiles on a NFS share on the same server.  This gets you close to roaming profiles, but doesn't do any caching/copying - it just accesses it directly over the network.

I'd take a close look at the official 'server guide' documentation.  That should get you most of the way (these are the Jaunty guides):

[https://help.ubuntu.com/9.04/serverguide/C/network-authentication.html](https://help.ubuntu.com/9.04/serverguide/C/network-authentication.html)

[https://help.ubuntu.com/9.04/serverguide/C/network-file-system.html](https://help.ubuntu.com/9.04/serverguide/C/network-file-system.html)

As far as group policy goes:  I haven't gotten that far, but I think you'd be looking at more of a script-type setup.  One of the powerful things about linux (or UNIX) is that you can remotely login and change *any* config file on the system (unlike windows where most everything is stored in the registry).

This sounds like exactly what I'm looking for. Group policy and true roaming profiles aren't really NEEDED, they were just something I wanted "just in case". Simply accessing files over the network should be fine for me, I don't plan on keeping much in the roaming directories anyways!

---

### Post by whoop on 2009-11-07
This is the most complete up-to-date tutorial on this topic (although written for ubuntu 7.10):
[http://www.rrcomputerconsulting.com/view.php?article_id=3](http://www.rrcomputerconsulting.com/view.php?article_id=3)

We need up-to-date complete documentation on this topic, please **vote**:
[http://brainstorm.ubuntu.com/idea/22151/](http://brainstorm.ubuntu.com/idea/22151/)

---

