---
title: "samba server without unix users"
date: 2008-06-11
forum: Server Platforms
---

### Post by emretemp on 2008-06-11
Hi, 

i want to ask smt about SAMBA. installed a standalone samba server yesterday. I m working on it now. 

Do I HAVE TO create a valid UNIX User just to share smb over windows network machines? I want to create a smb user only via smbpasswd command. How can i skip creating a unix user part? is there a way todo so ?

I dont want to crate a unix account first, then sync it with samba account. creating only a samba account must be enough to make my window client connect on my linux samba shared directories.

---

### Post by cdenley on 2008-06-11
The reason you need a unix account is so samba can restrict access to files according to permissions set on the filesystem. If the unix user doesn't have local permission to read a file, the samba user with the same name won't be able to read it either, regardless of the share's settings. I think you can disable the unix account, as long as the samba user is listed in /etc/passwd with a UID.
```

sudo passwd -l smbuser

```

---

### Post by mbeach on 2008-06-11
will you be having multiple users all with unique permissions on particular shares, or are you only trying to not have to create your windows usernames on your linux box?

the smbusers file can map multiple names to one account if that helps at all.  Some examples:
[http://htyp.org/smbusers](http://htyp.org/smbusers)

make sure 
username map = /etc/samba/smbusers
exists in your smb.conf file though (not sure if Samba creates it for you)

---

### Post by hyper_ch on 2008-06-11
or you could create unix users with restricted access so they cannot login by shell or somehow.

---

