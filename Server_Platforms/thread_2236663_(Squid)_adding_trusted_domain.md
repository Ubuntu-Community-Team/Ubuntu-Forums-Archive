---
title: "(Squid) adding trusted domain"
date: 2014-07-28
forum: Server Platforms
---

### Post by John_Haswell on 2014-07-28
I am testing squid for my company which consists of 2 domains which are trusted with each other. I have setup a squid virtual appliance on domain A and now want to test if users from Domain B can use it. At the moment they are prompted for authentication but I would like to know if there is something I can add to the squid conf to accept Domain B in the same way? 


Thanks

---

### Post by SeijiSensei on 2014-07-28
Since Squid doesn't require authentication by default, I'm guessing you are requiring it for people in domain A?  Do you want to keep authentication for them, but not require it for domain B?  Usually you would just create an ACL for domain B and place an appropriate http_access declaration ahead of the one requiring authentication.  Something like:
```

acl domainb src 192.168.50.0/24
http_access allow domainb

```

---

### Post by John_Haswell on 2014-07-28
I would like to keep authentication for both so we can report on them but I would like it not to ask for username and password when opening the browser. Is this possible?

---

### Post by SeijiSensei on 2014-07-28
I don't think so.  How else would authentication take place?

At my client's site, we use IP addresses to identify users, but their users work at the same machines all the time.  If you have a lot of floating staff members, that won't help.

---

### Post by John_Haswell on 2014-07-28
Can it not authenticate with AD the same way as domain A due to it being a trusted domain?

---

### Post by SeijiSensei on 2014-07-28
Well, you didn't tell us that you were using Active Directory.  Can't you simply replicate what you have for domain A and use it for domain B?

Like most of us here, I have no experience with AD.

Remember, here in the *nix world, a "domain" refers to something like ubuntuforums.com.  "Domains" in the Windows sense are a different critter entirely.

---

### Post by elico on 2014-07-28
> **John_Haswell said:**
> Can it not authenticate with AD the same way as domain A due to it being a trusted domain?

It's a bit more complicated then that.
Squid by itself do not care about the domain you as a user belongs to.
Also it depends on what helpers you are using to authenticate the clients.
Since it a more in depth question then a basic squid setup I would recommend you to try and ask at squid-users mailing list which the authentication helper developer is present most of the time.

---

