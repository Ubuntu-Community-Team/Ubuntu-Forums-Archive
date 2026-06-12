---
title: "how do i make linux server run similar like windows network"
date: 2011-11-03
forum: Server Platforms
---

### Post by jewfromdahood on 2011-11-03
ok in a general domain for windows. you have the users on the servers and clients can login to them from the desktop.
How do I do this same functionality on Ubuntu? As we are going to cloud computing software that is all web based and we in the IT department have been tinkering with new ideas to save money seeing as it is web based. I said lets ditch windows where we can and go with Linux, all we needed was Java, flash, and firefox or chrome. And Linux has that. I use linux personally. As well as mac. We are testing Ubuntu, Xbuntu, and Linux Mint for desktop platforms, in both 32 bit and 64 bit varieties. So far liking Xubuntu on the desktop. 
The server has Ubuntu. I was looking at maybe LDAP or something like that, just looking at different ways I can do things.

---

### Post by arrrghhh on 2011-11-03
If you need user authentication, I think samba is your only option.

I personally prefer NFS, but I'm not sure how that would integrate with LDAP auth.

If you just need simple file sharing and all clients are Linux-based, NFS can't be beat.

---

### Post by jaal on 2011-11-20
you can look this page

[http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html](http://tuxnetworks.blogspot.com/2010/07/howto-samba-ldap-on-1004-lucid-short.html)

install ubuntu server 10.04 LTS and the desktop you can install what you find nice...

---

### Post by newbie-user on 2011-11-20
Are you looking for something along the lines of an active directory setup or a terminal server?  What exactly do you mean by "clients can login to them from the desktop"?

If you're just asking about directory services, the OpenLDAP is what you want to look into.  If you're asking about terminal server, then LTSP will do that.  OpenLDAP + Samba if you want to use Windows clients.

---

