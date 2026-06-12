---
title: "Ubuntu 10.04 File server and Authentication"
date: 2010-05-20
forum: Server Platforms
---

### Post by X1R1 on 2010-05-20
Hi guys, a little help here, this is driving me crazy.

I just installed Ubuntu server on an Hp Proliant Server, I will use this server to provide File Services within a Domain using Samba.

The thing is we have a Windows 2008 server running an active directory. What I want to do is give all the AD users access to the file server, and automount the network volume when the user logs in ( I guess that part should be done in th AD server, right)?

I used likewise open to join the Server to the domain, got a big SUCCESS message and then rebooted, now the ubuntu server appears on the domain (If I go to a windows machine on the network, the to network places, entire network, mydomain, I can see the server there, but cant connect (asks for username and password).

I have searched for a while now and cant find anything specific to my problem. I know kerberos has something to do with this and that I should install it, but the package name should have changed or something cause I tried to do what the Ubuntu server guide tells me and apt complains that it cant find the package.

Another weird thing is that while im joined to the domain, (a tip to verify this would be nice) if I type:

```
wbinfo -u
```

to see all the users in the AD, it gives me:

> Error looking up domain users

So in short:

-How do I validate users in the AD to use the Ubuntu File Server?

Any info you need just ask.

thanks a lot

---

