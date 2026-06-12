---
title: "Trouble getting FQDN on 10.04"
date: 2010-07-31
forum: Server Platforms
---

### Post by nlsmith on 2010-07-31
Hi,

I'm using Rackspace Cloud Servers. If I create a new server named "test.example.com" running Ubuntu 9.10, log in, and run hostname -f, it gives me:

```
test.example.com
```If I do the same thing running 10.04, I get:

```
hostname: Name or service not known
```Both server instances had the same /etc/hosts:

```
127.0.0.1     localhost localhost.localdomain
174.143.208.230     test.example.com
```And /etc/hostname:

```
test.example.com
```Any ideas why this is happening?

(I'm using Chef to provision systems, which uses ohai, which uses hostname -f to set the FQDN of a node.)

Thanks,

Nathan

---

### Post by redmk2 on 2010-08-01
> **nlsmith said:**
> ...
```
hostname: Name or service not known
```Both server instances had the same /etc/hosts:

```
127.0.0.1     localhost localhost.localdomain
174.143.208.230     test.example.com
```

And /etc/hostname:

```
test.example.com
```Any ideas why this is happening?
...

I believe the hostname in your example is wrong.  The name in /etc/hostname should be only the **hosts name** -- As: ```
test
```

The FQDN test.example.com uses the hostname -- as in hostname.domain.root

---

### Post by nlsmith on 2010-08-01
> **redmk2 said:**
> The name in /etc/hostname should be only the **hosts name** -- As: ```
test
```

You're correct about that. I guess this is more a bug on how Rackspace Cloud provisions 10.04 instances with the FQDN as the name than a problem with Ubuntu.

Interestingly, this configuration works fine before 10.04.

Thanks for the help.

Nathan

---

