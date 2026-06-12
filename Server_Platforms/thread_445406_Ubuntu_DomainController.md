---
title: "Ubuntu DomainController"
date: 2007-05-15
forum: Server Platforms
---

### Post by davemk on 2007-05-15
I recently made the decision to bring my home network from Windows 2000 to Ubuntu 7.04. When I had  2000 server version I had a windows domain controller to manage all the accounts my family had. Now I am looking to do the same thing with Ubuntu. I've read up on Samba but it appears it is ment to allow Linux to act like a Windows domain controller.

Does Ubuntu Server have avaliable a software package which allows for a similar functionality with network users and logins?? All I keep finding is samba this and samba that...and maybe that is the right path but it doesn't seem like it to me.

Thanks a bunch!
Dave

---

### Post by benzies on 2007-05-16
Try Searching in your synaptics for

Bind or Gbind  [http://freshmeat.net/projects/gbindadmin/](http://freshmeat.net/projects/gbindadmin/)

and

Gsambad  [http://freshmeat.net/projects/gsambad/](http://freshmeat.net/projects/gsambad/)

and 

Sadms [http://freshmeat.net/projects/sadms/?branch_id=61366&release_id=210955](http://freshmeat.net/projects/sadms/?branch_id=61366&release_id=210955)

Hope it helps 

>:3 RAWR

---

### Post by SepheeBear on 2007-05-18
> **davemk said:**
> I had a windows domain controller to manage all the accounts my family had. Now I am looking to do the same thing with Ubuntu. I've read up on Samba but it appears it is ment to allow Linux to act like a Windows domain controller.

Does Ubuntu Server have avaliable a software package which allows for a similar functionality with network users and logins?? All I keep finding is samba this and samba that...and maybe that is the right path but it doesn't seem like it to me.

It seems you are not exactly looking to go the samba route, but still want a net login server. Take a look at running openLDAP for user authentication and NFS to get something like roaming profiles in linux. Take a look at:
[LDAP-Samba PDC (for Linux and Windows)]("https://help.ubuntu.com/community/LDAP-Samba_PDC_%28for_Linux_and_Windows%29?highlight=%28pdc%29%7C%28samba%29")

---

### Post by tinny on 2008-07-21
Have a read of this...

[https://help.ubuntu.com/8.04/serverguide/C/windows-networking.html]("https://help.ubuntu.com/8.04/serverguide/C/windows-networking.html")

[https://help.ubuntu.com/8.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/8.04/serverguide/C/openldap-server.html)

---

