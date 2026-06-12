---
title: "Samba write permissions"
date: 2009-04-21
forum: Server Platforms
---

### Post by swraman on 2009-04-21
Hi,
Ive gone through countless forums about this to no avail.

I setup a samba server on my Ubuntu box so that I can read and write files on it from my Windows laptop.

The problem is that I can not write to the shared folder from Windows (I get a "ACCESS DENIED" in Windows).

I am trying to enable read and write access to anyone on my network, with no passwords.

My samba conf file for the share directory looks like:

```

[Apache]
comment = Apache2 Server config and htdocs
path = /usr/local/apache2/
writable = yes
read only = no
guest ok = yes

```

Thanks

---

### Post by dmizer on 2009-04-21
Can you please post your entire smb.conf file?

---

### Post by awe on 2009-04-21
Hello, sorry if what I write is obvious and you've done it already, but sometimes the easy things are ignore until someone tells us about them and we realised that we forgot somthing tiny.

What write permissions do you have on the shared folder and on the files that is contains? I do not mean the permissions on the smb config, you've already posted those, but rather I mean the permissions on the server box itself. You may need to phisically go to the computer that serves the shared folder and CHMOD and/or CHOWN the folder and its contents with the right permissions.

Regards

---

### Post by dmizer on 2009-04-21
> **awe said:**
> Hello, sorry if what I write is obvious and you've done it already, but sometimes the easy things are ignore until someone tells us about them and we realised that we forgot somthing tiny.

What write permissions do you have on the shared folder and on the files that is contains? I do not mean the permissions on the smb config, you've already posted those, but rather I mean the permissions on the server box itself. You may need to phisically go to the computer that serves the shared folder and CHMOD and/or CHOWN the folder and its contents with the right permissions.

Regards
That's a REALLY good point.

According to your post:
> **swraman said:**
> ```

[Apache]
comment = Apache2 Server config and htdocs
path = /usr/local/apache2/
writable = yes
read only = no
guest ok = yes

```

Thanks

You're trying to share /usr/local/apache2. That folder is owned by root, and should NEVER EVER EVER be shared ... ever. And whatever you do, don't chown or chmod them, because apache wouldn't be able to use them anymore.

If you want to configure your apache files remotely, use ssh.

---

