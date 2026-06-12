---
title: "Apache permissions"
date: 2008-09-02
forum: Server Platforms
---

### Post by rick71 on 2008-09-02
Can someone tell me how to configure Apache so I can write write files to /var/www/ ?

I am using 8.04. There is a www-data group, my user is a member of www-data group, and /var/www is owned by www-data, and is supposedly writable by members of the www-data group. However, I cannot write to /var/www.

Any help appreciated.

---

### Post by cdenley on 2008-09-02
I thought /var/www was owned by root by default. Are you using ubuntu?

You don't mention whether the group owner is www-data or the user owner.
```

sudo ls -ld /var/www

```
I would suggest doing this (if you need write access without sudo)
```

sudo chgrp -R www-data /var/www
sudo chmod -R 750 /var/www
sudo chown -R 1000 /var/www

```
Of course making yourself the owner does compromise a layer of security. It would be best to let root own it, then use sudo when you need to access it.

---

### Post by rick71 on 2008-09-02
Thanks.

I am indeed using Ubuntu. I change the directory group ownership to www-data, made a www-data group and added myself to it. I was hoping to be able to put other users (students) in the group so they write files to the server.

---

### Post by windependence on 2008-09-02
> **cdenley said:**
> I thought /var/www was owned by root by default. Are you using ubuntu?

You don't mention whether the group owner is www-data or the user owner.
```

sudo ls -ld /var/www

```
I would suggest doing this (if you need write access without sudo)
```

sudo chgrp -R www-data /var/www
sudo chmod -R 750 /var/www
sudo chown -R 1000 /var/www

```
Of course making yourself the owner does compromise a layer of security. It would be best to let root own it, then use sudo when you need to access it.

I'm not so sure this is the best approach.

According to Apache, you want to leave the doc root owned by root and then just grant read and execute access to others.

For write access, I think I would use a group other than www-data since that is the apache group. You could even set up a special group (or groups) with different access.

-Tim

---

### Post by caco on 2008-09-03
Check this [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP).
It should point you in the right direction...

---

### Post by cdenley on 2008-09-03
> **windependence said:**
> I'm not so sure this is the best approach.

According to Apache, you want to leave the doc root owned by root and then just grant read and execute access to others.

For write access, I think I would use a group other than www-data since that is the apache group. You could even set up a special group (or groups) with different access.

-Tim

Agreed.
> 
Of course making yourself the owner does compromise a layer of security. It would be best to let root own it, then use sudo when you need to access it.

I don't think it is best to grant read access to EVERYONE, though. If a remote user gains filesystem access through another service, they may be able to read your php script source code! I say don't grant any more access than absolutely necessary.

---

