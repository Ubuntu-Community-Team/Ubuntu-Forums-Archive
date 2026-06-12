---
title: "Mail Server Question"
date: 2009-10-01
forum: Server Platforms
---

### Post by bgandy on 2009-10-01
I have recently installed Ubuntu Server 9.04.  I am know needing to install the mail server.  I did not do it during the initial install.  If I start the install now, it gets to the "select install type" screen, but then it freezes.
 
Any ideas?

---

### Post by cdenley on 2009-10-01
> **bgandy said:**
> I have recently installed Ubuntu Server 9.04.  I am know needing to install the mail server.  I did not do it during the initial install.  If I start the install now, it gets to the "select install type" screen, but then it freezes.
 
Any ideas?

You don't need to reinstall ubuntu to get the mail server configuration.
```

sudo tasksel install mail-server

```

However, if you want an easy-to-manage full-feature mail server, I would recommend ubuntu 8.04 with zimbra.
[http://www.zimbra.com/community/downloads.html](http://www.zimbra.com/community/downloads.html)

---

### Post by bgandy on 2009-10-01
I did:
 
sudo tasksel
 
Then I selected install email server
 
That is when it hangs up.
 
I will try it the direct way and see how it works.
 
Thanks

---

### Post by cdenley on 2009-10-01
It will probably take a few minutes. It isn't very good at reporting progress. I think it is meant to be run at install when all the packages are on the disc, so when it "hangs" it is actually retrieving the needed packages.

---

### Post by bgandy on 2009-10-01
I let the installer run for nearly 3 hours with no results.  It hangs at the same screen when it asks you to select the install type.
 
Does anyone know of a good alternate mail server for ubuntu server 9.04, or a solution for my problem.

---

### Post by cdenley on 2009-10-02
> **bgandy said:**
> I let the installer run for nearly 3 hours with no results.  It hangs at the same screen when it asks you to select the install type.
 
Does anyone know of a good alternate mail server for ubuntu server 9.04, or a solution for my problem.

If you run the command I provided, it shouldn't prompt you for anything.
```

sudo tasksel install mail-server

```

Also, I already suggested an alternative.

---

