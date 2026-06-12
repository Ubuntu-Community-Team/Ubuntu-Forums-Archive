---
title: "Questions about LDAP"
date: 2008-07-08
forum: Server Platforms
---

### Post by johnnybeem on 2008-07-08
I have recently set up LDAP in my house to keep track of files/permissions/users on different computers. It works great, but I have a couple questions...

1) I have created a *local* user account "uadmin" that has super-user privileges. I intended to use this as a "backup" account. In case the internet ever went down (and couldn't access LDAP), I could use the uadmin account to at least get onto the computer. The thing is - when I don't have internet, it takes a *really* long time to log into the uadmin account. 10-20 minutes. I'm guessing there is a timeout configured somewhere that says "keep trying to connect to LDAP for this long". GNOME also gives me errors like "HAL daemon failed to initialize" when I log in. Any idea how to fix this??

2) I have NFS set up on the same computer as the LDAP server. Right now, I can mount NFS shares manually or put them in /etc/fstab, but I have heard there's a way for LDAP to automatically mount NFS directories to LDAP clients. Anybody have a pointer to a good tutorial for this?

Thanks a lot,
John

---

### Post by pdwerryhouse on 2008-07-08
1) Is your PAM configuration looking at ldap first, and then the local password second? That would cause a delay.

/etc/pam.d/common-auth might be the file to look at.

2) I think you might be thinking of autofs here; it doesn't have any relationship to ldap though.

Cheers,

Paul

---

### Post by johnnybeem on 2008-07-09
1) Not sure what these mean, used a tutorial to set this up...

/etc/pam.d/common-auth
```

auth       sufficient   pam_ldap.so
auth       required     pam_unix.so nullok_secure use_first_pass

```

/etc/nsswitch.conf
```

[...]
passwd:         files ldap
group:          files ldap
shadow:         files ldap
[...]

```

2) Oh yeah I think you're right. I must be thinking of autofs... Do you have a good link to a tutorial? I want to set something up on my server that tells all the clients "mount these directories on boot"

Thanks a lot!

---

### Post by johnnybeem on 2008-07-14
..bump..

Please help!! My big problem is question one... With LDAP set up, why does it take so long to log into a *local* user account (when there is no network connection)??

---

### Post by pdwerryhouse on 2008-07-17
Yeah, I think the problem is that your common-auth file is trying to authenticate with ldap first. Try the following in that file instead:

```
auth [success=1 default=ignore] pam_unix.so
auth required pam_ldap.so use_first_pass
auth required pam_permit.so

```

This will check the shadow file first, and then use ldap if that doesn't work.

---

### Post by furlabs on 2008-07-19
Alternatively you could edit your ldap.conf and change 
```

bind_policy hard

```
to
```

bind_policy soft

```
This will make the LDAP authentication fail quickly if it can't find a connection, instead of trying a million times.

---

