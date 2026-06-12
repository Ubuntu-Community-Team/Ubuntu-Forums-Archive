---
title: "Simplify apache configuration"
date: 2008-03-07
forum: Server Platforms
---

### Post by jcpunk on 2008-03-07
With apache 2.2 there is a nifty setting for SSLEngine - optional.  Optional lets me in band (on port 80) do TLS.  This got me thinking.... I have one Vhost for my port 80 and one for port 443.  They serve the same content, except one is editable (443) and the other is not.  The app I am running (Drupal) lets me enforce this all on its own.  The app knows if I am encrypted or not, so I don't have to worry about that.

That being said, does anyone out there know how I can merge the two stanzas?  For port 443 the SSLEngine must be On and for port t80 it must be Optional at its most aggressive.

Essentially I have

```
NameVirtualHost *:80
<VirtualHost *:80>
ServerName mysite.com
DocumentRoot /my/webroot/with/stuff/and/junk/
SSLEngine Optional
...
</VirtualHost>
<VirtualHost *:443>
ServerName mysite.com
DocumentRoot /my/webroot/with/stuff/and/junk/
SSLEngine On
...
</VirtualHost>

```

Since SSLEngine is the only parm that needs to be different between the two, it seems keeping them separate is a bit silly.....  Any ideas on how to merge them?  Running Optional on port 443 generates a protocol error as you have to upgrade to TLS rather than get it handed to you automatically

---

