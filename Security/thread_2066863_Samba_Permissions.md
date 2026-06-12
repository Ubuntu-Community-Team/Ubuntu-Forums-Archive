---
title: "Samba Permissions"
date: 2012-10-05
forum: Security
---

### Post by StrutServer on 2012-10-05
I go to Seaside High School and in my computer repair class we are trying set up a ubuntu server. It is accessible to everybody plugged into the network but we want to make it so that everybody has permissions, so one person can save something to the folder and nobody else could access that but the creator and the administrator.

---

### Post by cybercity@localhost on 2012-10-05
you have to make some changes in your smb.conf file. suppose if you want to create a share named "Home" with read write access to user account administrator and paul add this line under your share definition "Home"
```
write list = administrator, pual
```
for read only access add this line under the same share.
```
read list = john, jack
```

---

### Post by bab1 on 2012-10-05
> **cybercity@localhost said:**
> you have to make some changes in your smb.conf file. suppose if you want to create a share named "Home" with read write access to user account administrator and paul add this line under your share definition "Home"
```
write list = administrator, pual
```
for read only access add this line under the same share.
```
read list = john, jack
```

There already is a [homes] directory defined in the smb.conf file.  You just have to uncomment it.  It is only defined once.  All Samba users are provided there own home directory on the Samba host server.  The root user always has access via sudo in Ubuntu.

See [**_[COLOR="Blue"]Code Listing 1.4: Sharing multiple homes[/COLOR]_**]("http://www.gentoo.org/doc/en/articles/samba-p3.xml") in this documentation.

---

### Post by bab1 on 2012-10-05
> **StrutServer said:**
> I go to Seaside High School and in my computer repair class we are trying set up a ubuntu server. It is accessible to everybody plugged into the network but we want to make it so that everybody has permissions, so one person can save something to the folder and nobody else could access that but the creator and the administrator.

Use the [homes] share for this.  See the previous post.

---

