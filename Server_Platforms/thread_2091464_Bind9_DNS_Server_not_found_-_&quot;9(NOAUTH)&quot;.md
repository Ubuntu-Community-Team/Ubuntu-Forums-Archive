---
title: "Bind9 DNS Server not found - &quot;9(NOAUTH)&quot;"
date: 2012-12-05
forum: Server Platforms
---

### Post by Toriku on 2012-12-05
Today I followed this tutorial: [TUTORIAL]("http://lani78.wordpress.com/2012/07/22/setting-up-a-dns-for-the-local-network-on-the-ubuntu-12-04-precise-pangolin-server/")
But I get an error message:

> 
user@localhost:~$ host -l office.lan
; Transfer failed.
Host office.lan.office.lan not found: 9(NOTAUTH)
; Transfer failed.


what could I have missed?

---

### Post by SeijiSensei on 2012-12-05
> Host office.lan.office.lan not found

A quick guess is that you are missing a trailing period in some host declaration.  Notice how it has appended the domain to the domain.  The trailing period is critical in zone files and easy to miss.

For instance,

```

@  IN SOA example.com ...

   IN NS example.com


```

will result in the nameserver appearing to be example.com.example.com because the entry in the NS declaration is missing a trailing period.

---

### Post by SeijiSensei on 2012-12-05
Double-post due to server reboot.

Please, please, let us delete posts.  I do not understand why this feature is disabled here.

---

