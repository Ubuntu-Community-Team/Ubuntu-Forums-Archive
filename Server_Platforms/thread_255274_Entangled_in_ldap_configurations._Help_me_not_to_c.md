---
title: "Entangled in ldap configurations. Help me not to cross that distro border again..."
date: 2006-09-11
forum: Server Platforms
---

### Post by Macchi on 2006-09-11
Hello,

I am having problems to get ldap authentication to work for a small network. This is a VERY important function for my small office/home office server. Obviously I am doing something wrong, but I have a feeling that there must be a golden path to get it to work within a few seconds. Preferably with high level administration of the directory.

Please, would you recommend proven open source ldap solutions for Dapper?
I am very thankfull för suggestions.


I am fully aware that there are several tutorials and recommendations on the net, some even customized for Dapper. But it is frustrating that despite following all details on fresh installs, I still dont get ldap authentication to work! As the title insinuates, I confess to have used SuSE on servers before but now decided to try to stay with Ubuntu!

---

### Post by fnjordy on 2006-09-12
If you don't mind a separate appliance you could check this out:

[http://developer.novell.com/wiki/index.php/miru_directory_server](http://developer.novell.com/wiki/index.php/miru_directory_server)

Otherwise your best bet is to use phpmyadmin + lighttpd/apache + openldap.

There's a howto on the Ubuntu wiki:

[https://help.ubuntu.com/community/LDAPClientAuthentication](https://help.ubuntu.com/community/LDAPClientAuthentication)

Neither path is really straightforward, but then the alternatives are Windows or contract someone to help you.  Ubuntu Dapper only got LDAP NSS support post release in the Universe repository.

---

### Post by Macchi on 2006-09-13
Thanks for the hints fnjordy!

I did not solve the problem yet but will engage in a new ldap experiment by the end of the week.

The link at Novell for the miru directory server is really very interesting! I have been looking for something similar, but would also like to add some functions to it. Thus instead of the well integrated BSD solution I would have to go for the Ubuntu alternative (at Novell!).

This is a classic dilemma between flexibility and tight integration of components. Higher flexibility requires increased effort/cost to configure and implies in an increased risk for lower reliability. There is always a visible or hidden trade-off.

---

