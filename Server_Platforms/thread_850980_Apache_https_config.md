---
title: "Apache https config"
date: 2008-07-06
forum: Server Platforms
---

### Post by johnelle on 2008-07-06
I am trying to switch from Fedora to Ubuntu and I am struggling with a piece of Ubuntu's Apache setup.  I want to be able to browse the default doc root with with either http:// or https:// because of a Verizon block on port 80 inbound.  

This works by default in the Fedora config but when I add the secure setup lines to the Ubuntu config (from the official directions):
```

SSLEngine on

SSLOptions +StrictRequire

SSLCertificateFile /etc/ssl/certs/server.crt
SSLCertificateKeyFile /etc/ssl/private/server.key

```

It forces you to use https:// by putting up a "bad request" error for http:// access.  Of course turning ssl off allows normal access to work but https:// gets an error.

Do I need a 2nd virtual host overlapping the default?  The Fedora config has no virtual host...can I just get rid of it in the Ubuntu config?

John

---

### Post by Dr Small on 2008-07-06
Here is a sample HTTPS virtual host that I have. You may gleen something out of it:
```
<VirtualHost *:443>
        ServerAdmin email@domain.tld
        SSLEngine On
        SSLCertificateFile /etc/ssl/certs/mail.pem
        DocumentRoot /opt/lampp/htdocs/
        ServerName example.com
        ServerAlias www.example.com
        CustomLog logs/https_log combined
</VirtualHost>
```

---

### Post by johnelle on 2008-07-06
Thanks that--it inspired me to try two virtual hosts with the same doc root, one for 80 and one for 443.  That seems to be working.  Had to get rid of the NameVirtualHost * directive in the first line and turn the 2nd line into a *:80 and then I have the 2nd virtual host that looks a lot like your code at the end of the file.  It shares the same doc root but doesn't have all the directory settings.

---

