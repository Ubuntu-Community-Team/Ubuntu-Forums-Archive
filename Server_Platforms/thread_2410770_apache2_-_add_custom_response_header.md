---
title: "apache2 - add custom response header"
date: 2019-01-20
forum: Server Platforms
---

### Post by dam034 on 2019-01-20
Dear users,

I want to add a custom response header if the file requested has a particular extension.

I think the directives will be written in httpd.conf.

Example:
all files .txt will have encoding utf-8, so I want to instruct the client browser the encoding.

Is it possible? And how?

Thanks

---

### Post by SeijiSensei on 2019-01-21
In the definition for the virtual host use a Files directive with AddDefaultCharset

```

<VirtualHost *:80>
[stuff]

<Files "*.txt">
AddDefaultCharset utf-8
</Files>

[more stuff]
</VirtualHost>

```

[https://httpd.apache.org/docs/2.4/mod/core.html#files](https://httpd.apache.org/docs/2.4/mod/core.html#files)

[https://httpd.apache.org/docs/2.4/mod/core.html#adddefaultcharset](https://httpd.apache.org/docs/2.4/mod/core.html#adddefaultcharset)

You can force the entire server to use utf-8 by editing /etc/apache2/conf-available/charset.conf.

---

### Post by dam034 on 2019-01-23
I found in /etc/apache2/conf-available/charset.conf this line:
```
#AddDefaultCharset utf-8
```
I have just uncommented it and restarted apache2 service and now it works.

But now, if I want to add a particular http response header, like this:
```
X-Dachi: dam034
```

How can I do it?

Thanks

---

### Post by SeijiSensei on 2019-01-23
[http://httpd.apache.org/docs/current/mod/mod_headers.html](http://httpd.apache.org/docs/current/mod/mod_headers.html)

---

### Post by dam034 on 2019-01-24
And if I want to overwrite some apache default response headers?

Like Server response header?

Thanks

---

### Post by SeijiSensei on 2019-01-24
That's what documentation is for.  Apache's is pretty extensive.

---

