---
title: "Apache wildcard subdomain woes.."
date: 2012-08-22
forum: Server Platforms
---

### Post by linuxman94 on 2012-08-22
So I have an apache server set up with rewrite to force ssl connections and wildcard subdomains.  The issue I am having with the wildcard subdomains is that if you enter them without https:// in the browser, a www is added when it is redirected to ssl.  For example, if I enter

[http://test.example.com](http://test.example.com)

it redirects to

[https://www.test.example.com](https://www.test.example.com)

Which is not how I want it to work.

Here is my default and default-ssl server configs:

Default:

```
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        VirtualDocumentRoot /var/www/%0/

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
RewriteEngine On
RewriteCond %{HTTPS} off
RewriteCond %{HTTP_HOST} ^www\.(.*)$ [NC]
RewriteRule ^(.*)$ https://%1/$1 [R=302,L,QSA]
</VirtualHost>

```Default-ssl:
```

<VirtualHost *:443>
ServerAdmin webmaster@localhost
ServerName *.example.com (replaced for privacy)
SSLEngine On
SSLCertificateFile /etc/ssl/server.crt
SSLCertificateKeyFile /etc/ssl/server.key
SSLProtocol all
SSLCipherSuite HIGH:MEDIUM
VirtualDocumentRoot /var/www/%0/
</VirtualHost>

```

And Httpd.conf:
```
ServerName example.com
<Directory /var/www/sub.example.com>
        AuthType Basic
        AuthName "Authorized users only"
        AuthUserFile /etc/***/***.passwd
        <limit GET PUT POST>
        require valid-user
        </limit>
</Directory>

```
Any suggestions would be appreciated.  I have tried multiple rewrite rules in the ssl virtual host to remove the www but they have not been helpful.

---

### Post by SeijiSensei on 2012-08-23
I haven't used RewriteCond, but what is the purpose of 

```
RewriteCond %{HTTP_HOST} ^www\.(.*)$ [NC]
```

Might that be the source of the problem?

I usually just use a Redirect like this:
```

<VirtualHost *:80>
    ServerName test.example.com
    Redirect / https://test.example.com/
</VirtualHost>

```

---

### Post by linuxman94 on 2012-08-24
The rewritecond statement removes the www from the url before sending it to ssl.  I tried your suggestion but then it redirects all the subdomains to the main domain.

---

### Post by SeijiSensei on 2012-08-25
> **linuxman94 said:**
> The rewritecond statement removes the www from the url before sending it to ssl.  I tried your suggestion but then it redirects all the subdomains to the main domain.

You need to set up separate <VirtualHost> definitions for each subdomain to use my method.  It relies on matching the requested URL to ServerName as does all name-based virtual hosting in Apache.

---

