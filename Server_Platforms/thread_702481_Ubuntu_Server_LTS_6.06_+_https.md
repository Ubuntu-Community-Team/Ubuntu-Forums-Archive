---
title: "Ubuntu Server LTS 6.06 + https"
date: 2008-02-20
forum: Server Platforms
---

### Post by chrislynch8 on 2008-02-20
HI,

So i have https setup for my install and I am able to access the web folder via https using a cert created via apache-ssl-certificate.... I want to also make it so it asks for a password when a certain folder is opened....

How is this possible?

Rgds
Chris

---

### Post by cdenley on 2008-02-20
First, make sure the AllowOverride line in your site configuration has AuthConfig, and not none.
```

AllowOverride AuthConfig

```

If you had to change this line, reload your configuration
```

sudo /etc/init.d/apache2 reload

```

Then, create your password file and user
```

sudo htpasswd -c /etc/apache2/auth chrislynch8

```

Then, create a file called .htaccess in the directory you want to protect, with this text
```

AuthName "My Secret Directory"
AuthType Basic
AuthUserFile auth
require valid-user

```

---

