---
title: "What will be the easy way to re-direct websites visits?"
date: 2018-12-07
forum: The Cafe
---

### Post by satimis on 2018-12-07
Hi all,

What will be the easy way to re-direct websites visits?

I'm hosting my websites on Godaddy.  I'm prepared moving all my subdomain websites on domain-A to domain-B with the same names.  What will be the easy way to direct all visits to subdomain websites on domain-A to subdomain websites on domain-B i.e when visitors click subdomain websites on domain-A they will be automatically re-directed to subdomain websites on domain-B?

Thanks

Regards
satimis

---

### Post by TheFu on 2018-12-07
301 permanently moved
[https://css-tricks.com/snippets/htaccess/301-redirects/](https://css-tricks.com/snippets/htaccess/301-redirects/)
Apache settings can do it too, but I don't know if you have access to those at godaddy.

---

### Post by SeijiSensei on 2018-12-07
You could also specify domainB as a ServerAlias in Apache.

```

<VirtualHost *:80>
ServerName     www.domainA.com
ServerAlias    www.domainB.com

[stuff]
</VirtualHost>

```

---

