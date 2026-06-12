---
title: "Getting LDAP + PHP &amp; GD  to work with 6.10 Server"
date: 2006-11-28
forum: Server Platforms
---

### Post by scrupul0us on 2006-11-28
I just did a fresh install of 6.10 server and im having some issues with PHP

First off im trying to get LDAP incorporated into PHP... so far ive done this:

sudo apt-get install slapd
sudo apt-get install openldap

and those were successful

a quick view of phpinfo() shows that util_ldap is loaded, but there is NO section for LDAP...

and a quick test of:

[php]
$ds=ldap_connect("localhost");
[/php]

tells me that ldap_connet is an undefined function... meaning LDAP isnt running

how do i get LDAP working with PHP?

by the same token iv'e noticed that GD isnt enabled/installed by default, how do i get GD working with PHP?

thanks for the help in advance!

---

### Post by scrupul0us on 2006-11-28
oh i got it... i edited:

```
/etc/php5/apache2/php.ini
```

and added:

```
extension=mod_ldap.so
```

then:

```
sudo /etc/init.d/apache2 restart
```

now i just need to figure out GD

---

### Post by scrupul0us on 2006-11-28
to get GD working:

```

sudo apt-get install php5-gd
sudo /etc/init.d/apache2 restart

```

hopefully this thread helps people!

---

