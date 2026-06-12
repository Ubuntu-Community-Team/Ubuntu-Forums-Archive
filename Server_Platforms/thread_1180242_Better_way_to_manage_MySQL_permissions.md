---
title: "Better way to manage MySQL permissions?"
date: 2009-06-06
forum: Server Platforms
---

### Post by Vunutus on 2009-06-06
I'm attempting to configure a MySQL server for use in a small office. Each employee will have a MySQL user account. As it stands right now, whenever I add a new user I have to set up permissions and manually specify what machine they are connecting from.

For example, to grant permissions to a user I have to do something like this:

```

GRANT ALL ON *.* TO 'user'@'sample-workstation' IDENTIFIED BY 'password';

```

Now this works fine, as long as the user is connecting from sample-workstation. If they go to another computer, it denies them permission. Is it possible, or even advisable, to use wildcards in the host name section? Like, could I grant permissions to user@192.168.1.* to allow a user to connect from any machine on the local network? Does this cause any security vulnerabilities (and speaking of which I know granting to *.* is a security hole but that's just an example)?

---

### Post by koenn on 2009-06-06
> You can specify wildcards in the host name. For example, [email]user_name@'%.example.com[/email]'  applies to user_name for any host in the example.com domain, and user_name@'192.168.1.%'  applies to user_name for any host in the 192.168.1 class C subnet.  -- [http://dev.mysql.com/doc/refman/5.1/en/grant.html](http://dev.mysql.com/doc/refman/5.1/en/grant.html)

It's a reasonable thing to do if your users have free seating. In that case, your security will have to deal with "who has access to workstations in this subnet ?"

---

### Post by pogztimz on 2009-06-06
> **Vunutus said:**
> I'm attempting to configure a MySQL server for use in a small office. Each employee will have a MySQL user account. As it stands right now, whenever I add a new user I have to set up permissions and manually specify what machine they are connecting from.

For example, to grant permissions to a user I have to do something like this:

```

GRANT ALL ON *.* TO 'user'@'sample-workstation' IDENTIFIED BY 'password';

```

Now this works fine, as long as the user is connecting from sample-workstation. If they go to another computer, it denies them permission. Is it possible, or even advisable, to use wildcards in the host name section? Like, could I grant permissions to user@192.168.1.* to allow a user to connect from any machine on the local network? Does this cause any security vulnerabilities (and speaking of which I know granting to *.* is a security hole but that's just an example)?

u should grant permissions for remote users like this.
 
```
GRANT ALL ON sampleDB.* TO 'user'@'%' IDENTIFIED BY 'passwd';
```

---

