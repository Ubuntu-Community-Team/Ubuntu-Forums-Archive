---
title: "Apache Redirect for connection coming via external IP"
date: 2010-05-14
forum: Server Platforms
---

### Post by chrislynch8 on 2010-05-14
HI,

On my Server I have an application running. I have the External IP address of the Server registered in DNS so users requiring access from outside the office can enter a full URL rather then an IP address.

How to I change my Apache config so that all traffic that comes into the server from the URL is put over https?

Rgds
Chris

---

### Post by cdenley on 2010-05-14
Add this to your default site configuration
```

RewriteEngine On
RewriteCond %{HTTPS} off
RewriteRule (.*) https://www.mydomain.com$1

```

then run
```

sudo a2enmod rewrite
sudo /etc/init.d/apache2 restart

```

---

### Post by chrislynch8 on 2010-05-17
Hi,

Thanks, but that seems to redirect all traffic over https, I only want traffic coming from mydomain.com to be put over https. Internal users still access the application using my internal ip address 192.168.1.250.

Rgds
Chris

---

### Post by cdenley on 2010-05-17
> **chrislynch8 said:**
> Hi,

Thanks, but that seems to redirect all traffic over https, I only want traffic coming from mydomain.com to be put over https. Internal users still access the application using my internal ip address 192.168.1.250.

Rgds
Chris

You mean if accessed by the hostname mydomain.com without SSL, redirect to [https://mydomain.com](https://mydomain.com), otherwise do nothing?
```

RewriteEngine On
RewriteCond %{HTTPS} off
RewriteCond %{HTTP_HOST} ^mydomain\.com$
RewriteRule (.*) https://mydomain.com$1

```

Or you can redirect everything that isn't from a specific network, for example, 192.168.0.xxx.
```

RewriteEngine On
RewriteCond %{HTTPS} off
RewriteCond %{REMOTE_ADDR} !^192\.168\.0\..*$
RewriteRule (.*) https://mydomain.com$1

```

[http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html](http://httpd.apache.org/docs/2.2/mod/mod_rewrite.html)

---

### Post by chrislynch8 on 2010-05-17
Thank You very much that is working a charm now.

---

### Post by chrislynch8 on 2010-05-26
Can I ask another question.

In apache if a user is connecting to an internal site/application etc using the IP address, can I have apache show a different URL in the users address bar?

Rgds
Chris

---

### Post by cdenley on 2010-05-26
> **chrislynch8 said:**
> Can I ask another question.

In apache if a user is connecting to an internal site/application etc using the IP address, can I have apache show a different URL in the users address bar?

Rgds
Chris

The URL displayed in the browser's address bar is always going to reflect the URL which was requested by the browser, unless there is a security vulnerability in the browser the visitor is using and you exploit it. You can either redirect them, or you can display a page which is nothing but a frame for another URL taking up the whole page.

---

