---
title: "or ubuntu file server."
date: 2011-03-29
forum: Server Platforms
---

### Post by ralph9994 on 2011-03-29
i've got a thing here.
i need to make an file server.
but I'm not gonna ask how because that's a piece of pie.
The thing is i need to make an ubuntu/xubuntu based file server.
For windows users.
But not just a regular file server. A File Server with accounts. That when you try to access the file server in explorer you need to provide a username and password.
And that you( as the administrator) manage the privileges for the server/folder/file. so with different permissions.
so a samba file server with accounts that is being used on windows machines.

hope you guys can help me out.

thanks

---

### Post by Thund3rstruck on 2011-03-29
> But not just a regular file server. A File Server with accounts. That when you try to access the file server in explorer you need to provide a username and password.
And that you( as the administrator) manage the privileges for the server/folder/file. so with different permissions.

I'm not sure what you mean by regular file server. All file servers require accounts, unless you explicitly configure it to allow guest users. 

I use FreeNAS for my file server. It's based on FreeBSD. If you need additional permissions beyond the traditional Unix Owner+Group+Users construct then you'll need to install the acl package and use the ```
getfacl
``` and ```
setfacl
``` utilities to configure extended permissions. You will also need to configure the volume to enable ACL permissions in /etc/fstab. Refer to the man pages for additional detail.

---

### Post by cariboo on 2011-03-29
You most certainly don't need Xubuntu either, the users aren't directly working on the server, and explorer doesn't care whether there's a gui or not.

---

### Post by hawk2010 on 2011-03-30
Why not simply use Samba.


> **ralph9994 said:**
> i've got a thing here.
i need to make an file server.
but I'm not gonna ask how because that's a piece of pie.
The thing is i need to make an ubuntu/xubuntu based file server.
For windows users.
But not just a regular file server. A File Server with accounts. That when you try to access the file server in explorer you need to provide a username and password.
And that you( as the administrator) manage the privileges for the server/folder/file. so with different permissions.
so a samba file server with accounts that is being used on windows machines.

hope you guys can help me out.

thanks

---

### Post by ralph9994 on 2011-03-30
Yea so Ive read this guide: [http://www.intac.net/build-your-own-server/](http://www.intac.net/build-your-own-server/)

Thats why i came up with xubuntu because the guide recommends it.

so yea if you say it always needs an  account to acces the file server. What is the best way to manage it??

like adding users with passwords. , groups setting permissions etc.

---

