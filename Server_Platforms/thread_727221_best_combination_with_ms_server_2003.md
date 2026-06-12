---
title: "best combination with ms server 2003 ?"
date: 2008-03-17
forum: Server Platforms
---

### Post by imax36581 on 2008-03-17
hi my friends
i have some questions.
now im a ubuntu user and i using it in my home but what about enterprise network?
now im learning ms server 2003 and wants to be work with linux distro with ms server.
1.can we use ubuntu for **enterprise level** with ms server 2003?
2.whats the maximum of trust between each other?for example AD with LDAP?or can we create this trust for some replications and ....
3.Is ubuntu is the best solution or distro for combination with ms server 2003 or we can use other distro?
4. thanks in advance ;)

---

### Post by HermanAB on 2008-03-17
Linux is Linux is Linux...  deep down they are all equally good or bad.  

However, some distributions have better wizards than others.  The Ubuntu wizards are not bad - the problem is that there isn't one for what you want to do.  You would therefore be better served with Mandriva, since it does have a wizard that can configure Samba for authentication against Active Directory.

See this for all the gory details:
[http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us3.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

See this for some more specific help with what you want to do:
[http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)
(This was written before the Mandriva authentication wizard was created).

Cheers,

Herman

---

