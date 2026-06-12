---
title: "Creating permission on file server..."
date: 2009-08-26
forum: Server Platforms
---

### Post by pkbest87 on 2009-08-26
Ok, so i created a file server with server 9.04. Installed ubuntu-desktop so id have a gui. I have in my /srv/samba/share directory , two folders. One is called public and the other is called private.

 I want to set it up so my mom, dad, and one employee can access the public (so not everyone can get in) and then only my mom and dad can get into the private. I have Employee as under the group Public and my parents under Private group. I just do not get how i should change the permissions on each directory folder.

Can someone help me out?

 Thanks,

Patrick

---

### Post by jocampo on 2009-08-26
> **pkbest87 said:**
> Ok, so i created a file server with server 9.04. Installed ubuntu-desktop so id have a gui. I have in my /srv/samba/share directory , two folders. One is called public and the other is called private.

 I want to set it up so my mom, dad, and one employee can access the public (so not everyone can get in) and then only my mom and dad can get into the private. I have Employee as under the group Public and my parents under Private group. I just do not get how i should change the permissions on each directory folder.

Can someone help me out?

 Thanks,

Patrick

Hi

In Linux, you can change permissions via "chmod" command. For a complete guide of what you can or can't do, type this on your console

```
man chmod
```

But in a short, if you want to grant read and write to a group you should do something like this

```
chmod g+rw MyFile
```

the "g" is for the group

To remove the permissions to the others, is something like this

```
chmod uo-rw MyFile
```

where "u" and "o" stands for user and others.

Now, that's a file system or Linux level. You must configure permissions at Samba Level as well. A simple Samba configuration for Home, could be

```

[home]
read only = no
browseable = no

```

Here, the user mapped to home can write there but can not browse outside of its own folder.

This Samba guide will explain that easily but more in depth: [http://samba.netfirms.com/index.htm]("http://samba.netfirms.com/index.htm")

---

### Post by pkbest87 on 2009-08-26
thanks...ill check out that link.. i think its probably something i need to set up in samba and not so much in the ubuntu permissions.

thanks for the speedy response!

---

### Post by pkbest87 on 2009-08-26
ok now im running into problems. i found where the problem lies tho. when i right click on the directory it has the right group...but instead of saying read and write it says ---. i want to change this but dont know how. i have the group set, but not the permissions OF that group? understand?  i have to restrict the private folder due to pay roll stuff so that is why i have to keep it secure. if i try and change it via GUI under properties it reverts my settings every time.

---

### Post by jocampo on 2009-08-26
> **pkbest87 said:**
> ok now im running into problems. i found where the problem lies tho. when i right click on the directory it has the right group...but instead of saying read and write it says ---. i want to change this but dont know how. i have the group set, but not the permissions OF that group? understand?  i have to restrict the private folder due to pay roll stuff so that is why i have to keep it secure. if i try and change it via GUI under properties it reverts my settings every time.

DO it via console ;-) ...

Let's say the folder is Payroll

```

chmod g+rw Payroll

```

then

```
ls -la
``` to check permissions, it should read rw now ... btw, I believe you should have X too in order to browse or open that folder

---

