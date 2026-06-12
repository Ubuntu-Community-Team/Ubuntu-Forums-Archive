---
title: "Samba user group"
date: 2010-04-27
forum: Server Platforms
---

### Post by Yann76 on 2010-04-27
I have a little problem:

I have a share folder on Ubuntu server:
- Dump

That folder is share with SAMBA and everyone can put files on it.

My problem is the following:
When someone create a folder, the folder permissions are automatically set with:
(let's take my username: Yann)
Owner: Yann
Group: Yann

Clearly that's wrong.. I want the Group to be auto set has "users" so everyone can access the folders on that share.

Anyone know how to change this ? chmod and chown is getting a bit boring ;)

Thanks :P

---

### Post by bab1 on 2010-04-27
> **Yann76 said:**
> I have a little problem:

I have a share folder on Ubuntu server:
- Dump

That folder is share with SAMBA and everyone can put files on it.

My problem is the following:
When someone create a folder, the folder permissions are automatically set with:
(let's take my username: Yann)
Owner: Yann
Group: Yann

Clearly that's wrong.. I want the Group to be auto set has "users" so everyone can access the folders on that share.

Anyone know how to change this ? chmod and chown is getting a bit boring ;)

Thanks :P

Use the "force group" parameter in the share.  I created a gorup called smbusers. I use this group in my public shares like this```
force group = smbusers
```

See the section called *force user *[**_here _**]("http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html")for details.

---

### Post by Yann76 on 2010-04-27
Thank you !!!! it Works !!!

---

