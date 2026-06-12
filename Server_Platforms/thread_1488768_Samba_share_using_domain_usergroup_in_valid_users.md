---
title: "Samba share using domain user/group in valid users"
date: 2010-05-20
forum: Server Platforms
---

### Post by NorthernSoul on 2010-05-20
I have Ubuntu server 10.04 joined to a domain using Likewise Open. I can login using my domain credentials and have added my domain account to the sudoers file. Now that I've got it joined to the domain I want to add some samba shares and have domain members use their accounts to access them. However, no matter what combination of my domain name and the domain user or group I use in the valid users field it won't let me in. What's the proper way of inputting a domain user or group in the valid user field? Thanks.

This is the entry I'm using for the share:
```
[testshare]
   path = /srv/testshare
   valid users = @"*Domain Name*+*Domain Group*" (Have tried many things here)
   public = no
   writable = yes
   printable = no
   create mask = 0765
```

---

### Post by NorthernSoul on 2010-05-25
Does anyone have any idea how this can be done?

---

### Post by capscrew on 2010-05-25
> **NorthernSoul said:**
> I have Ubuntu server 10.04 joined to a domain using Likewise Open. I can login using my domain credentials and have added my domain account to the sudoers file. Now that I've got it joined to the domain I want to add some samba shares and have domain members use their accounts to access them. However, no matter what combination of my domain name and the domain user or group I use in the valid users field it won't let me in. What's the proper way of inputting a domain user or group in the valid user field? Thanks.

This is the entry I'm using for the share:
```
[testshare]
   path = /srv/testshare
   valid users = @"*Domain Name*+*Domain Group*" (Have tried many things here)
   public = no
   writable = yes
   printable = no
   create mask = 0765
```

I don't believe the parameter *valid users *is what is used to authenticate a user to the share.  Valid users is a logical extension for the parameter *invalid users*.  This can used to limit a users ability to access a share.  But only if the user is already in the appropriate UNIX or NIS database (passwd, groups, etc.).

I take this to mean that with *valid users*, the user logically must have have a valid local account (passwd, groups) to be in the invalid or valid range.  When you map this to a domain you still have to get Samba to see the account, be it local or domain wide.

You can check to see who (if any) domain users are retrieved by using the [SIZE="2"][FONT="Courier New"]**getent**[/FONT][/SIZE]. 

For users you would use```
getent passwd
```  For groups you would use ```
getent groups
```

Speaking in a Windows way: You need to make sure your domain users and groups are treated as local users and groups.  Samba checks each call for service this way.

---

