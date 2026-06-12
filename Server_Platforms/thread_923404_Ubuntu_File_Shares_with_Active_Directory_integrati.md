---
title: "Ubuntu File Shares with Active Directory integration"
date: 2008-09-18
forum: Server Platforms
---

### Post by smirnoff76 on 2008-09-18
Hi all wonder if you can give me some help with the following issue i have. 

The network here is a full windows 2003 obviously running AD for user authentication. 
I have just setup ubuntu server with Gnome desktop which i am currently using for testing purposes. I now have the Ubuntu server authenticating against AD having followed the documentation on the help.ubuntu.com site using likewise. 

What I want to do with this server is set up file shares but be able to specify users / groups from the 2003 domain and then set up the appropriate permissions. 
I am able to set up a file share but am unable to specify the 2003 domain users / groups. 

Any help would be greatly appreciated as I am keen to start getting linux implemented within our network.

---

### Post by promodus on 2008-09-19
```
sudo apt-get install likewise-open-gui

sudo domainjoin-gui
```

---

### Post by jamesrfla on 2008-09-19
> **promodus said:**
> ```
sudo apt-get install likewise-open-gui

sudo domainjoin-gui
```

Can Ubuntu join a windows domain? Is likewise-open-gui only used for file sharing permissions?

---

### Post by vegas588 on 2008-09-20
Yes, Ubuntu or really any other UNIX/LINUX release, including MAC, can join a Windows Domain using likewise. I did it myself just recently and it works really well. 

There are two open versions, one for command line only and one with a gui or one you can pay for if you want more features. See [www.likewisesoftware.com](www.likewisesoftware.com)

You can install likewise-open on ubuntu server by following these simple instructions: [https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html](https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html)

good luck.

---

### Post by jamesrfla on 2008-09-20
> **vegas588 said:**
> Yes, Ubuntu or really any other UNIX/LINUX release, including MAC, can join a Windows Domain using likewise. I did it myself just recently and it works really well. 

There are two open versions, one for command line only and one with a gui or one you can pay for if you want more features. See [www.likewisesoftware.com](www.likewisesoftware.com)

You can install likewise-open on ubuntu server by following these simple instructions: [https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html](https://help.ubuntu.com/8.04/serverguide/C/likewise-open.html)

good luck.

That answered one of my questions. Dose Ubuntu have a like a windows domain? Like Ubuntu being the head domain controller? Or something like Linux Active Directory. Let me know if this sounds unclear.

---

### Post by likeWiseGuy on 2008-09-24
> **jamesrfla said:**
> That answered one of my questions. Dose Ubuntu have a like a windows domain? Like Ubuntu being the head domain controller? Or something like Linux Active Directory. Let me know if this sounds unclear.

I haven't tested this out but here's an article describing how to turn an Ubuntu 7.10 system into a Windows Server 2003-like domain controller: [http://www.linewbie.com/2008/01/configure-openldap-samba-domain-controller-on-ubuntu-710.html](http://www.linewbie.com/2008/01/configure-openldap-samba-domain-controller-on-ubuntu-710.html)

I can't attest to how this works but I figured I'd point you in that direction and see how well it suits your needs.

Thanks.

---

