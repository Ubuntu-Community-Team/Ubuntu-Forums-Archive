---
title: "Public folder (out the domain) with Samba +LDAP"
date: 2013-06-18
forum: Security
---

### Post by MikiBroki on 2013-06-18
Hi all,


I'm newbie with this but I have installed them on Ubuntu. I created some groups and users with LAM and I can join from the domain from Windows XP and Windows 7.


But I spent 2 days trying to share a public folder with Windows computers NOT JOINED to the domain... is that's possible ?


**/etc/samba/smb.conf**:


```

[global]
    workgroup = CURSO
    netbios name = SERVIDOR
    
    security = user
    ....
[shared]
    path = /home/javier/compartir
    read only = no
    public = yes	 			
    guest ok = yes



```


Then...


```

    $ sudo adduser userx
    $ sudo smbpasswd -a userx
    $ sudo service smbd restart

```


Under My Network on Windows I can't see the shared folder, only the domain, and if I click on it I'm prompted for user credentials: I can't login with 'userx', only domain users are valid.


Some help, please ?

---

