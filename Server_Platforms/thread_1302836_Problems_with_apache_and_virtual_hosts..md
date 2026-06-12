---
title: "Problems with apache and virtual hosts."
date: 2009-10-27
forum: Server Platforms
---

### Post by rnodal on 2009-10-27
Hello all,

I removed the default site that ships with ubuntu and put all my
virtual hosts under one file.
I have a default virtual host, vhost1 and vhost2. I can access all of
them but when I
try to access vhost2 via some of its aliases(the first alias works,
the rest don't) then all the requests go to the default one.
I have setup DNS. I'm having a hard time seeing why is does not work.
Do I have to setup up a virtual host per domain? I thought I could use
ServerAlias to point multiple domains to the same virtual host.
Any input would be appreciated. Thank you!

-r

Here is the content of the file:
```

## Defaults.
ServerName              "servername.domain.com:80"
NameVirtualHost *:80

# Default.
<VirtualHost *:80>
       Servername              "servername.domain.com"
       DocumentRoot            "/path/default"
       ServerSignature         "Off"
</VirtualHost>

# vhost1
<VirtualHost *:80>
       ServerName              "domain001.com"
       VirtualDocumentRoot     "/path/vhost1/%-2.0.%-1.0"
       ServerAlias             "www.domain001.com"
       ServerSignature         "Off"
</VirtualHost>

# vhost2
<VirtualHost *:80>
       ServerName              "www.domain002.com"
       VirtualDocumentRoot     "/path/vhost2/%-2.0.%-1.0"
       ServerAlias             "domain002.com"
       ServerAlias             "www.domain003.com domain003.com"
       ServerAlias             "www.domain004.com domain004.com"
       ServerAlias             "www.domain005.com domain005.com"
       ServerAlias             "www.domain006.com domain006.com"
       ServerSignature         "Off"
</VirtualHost>

```

---

### Post by rnodal on 2009-10-27
Fixed.

Instead of:
```

...
ServerAlias             "www.domain003.com domain003.com"
...

```

It should be:
```

...
ServerAlias             "www.domain003.com" "domain003.com"
...

```

Or simply without any quotes at all. wow!!

-r

---

