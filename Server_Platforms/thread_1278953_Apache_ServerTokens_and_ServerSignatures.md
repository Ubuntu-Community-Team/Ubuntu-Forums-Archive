---
title: "Apache ServerTokens and ServerSignatures"
date: 2009-09-30
forum: Server Platforms
---

### Post by shoaibi on 2009-09-30
From apache2.conf:
```

# Clipped

ServerRoot "/etc/apache2"
ServerName "localhost"

ServerSignature Off
ServerTokens    Prod

# Clipped

```


Being printed on error pages:
```

Apache/2.2.11 (Ubuntu) DAV/2 SVN/1.5.4 mod_fastcgi/2.4.6 Phusion_Passenger/2.2.4 mod_ssl/2.2.11 OpenSSL/0.9.8g mod_chroot/0.5 mod_perl/2.0.4 Perl/v5.10.0 Server at redmine.blade.local Port 443

```

Its not working as it should. Why could be the reason?

[EDIT]:
Modified conf.d/security and commented the overridden settings there.

---

### Post by bluefrog on 2009-09-30
have you reloaded/restarted apache?

---

### Post by JeshurunDaniel on 2010-08-21
> **shoaibi said:**
> From apache2.conf:
```

# Clipped

ServerRoot "/etc/apache2"
ServerName "localhost"

ServerSignature Off
ServerTokens    Prod

# Clipped

```


Being printed on error pages:
```

Apache/2.2.11 (Ubuntu) DAV/2 SVN/1.5.4 mod_fastcgi/2.4.6 Phusion_Passenger/2.2.4 mod_ssl/2.2.11 OpenSSL/0.9.8g mod_chroot/0.5 mod_perl/2.0.4 Perl/v5.10.0 Server at redmine.blade.local Port 443

```

Its not working as it should. Why could be the reason?

[EDIT]:
Modified conf.d/security and commented the overridden settings there.

Thanks, that had me scratching my head for a while!

---

### Post by opensshd on 2012-09-01
I found my ServerToken in /etc/apache2/conf.d/security (ubuntu precise with apache port)

Changing/adding values to httpd.conf or apache.conf had no effect here.

Seems signatures are controlled by the ServerTokens directive since 2.0.2 or so as well.

Use nmap -A your.ip.address after reloading to ensure your edits are in fact giving you the desired effect.

:)

---

