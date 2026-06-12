---
title: "make it so webpage unavailable by IP?"
date: 2013-02-14
forum: Server Platforms
---

### Post by SlugSlug on 2013-02-14
I am trying to setup virtual hosts.

I only want my website available via its [www.domain.com](www.domain.com)  address not my IP

this is a snip of site available

```
<VirtualHost *:80>
        ServerAdmin webmaster@example.com
ServerName example.com
    DocumentRoot /var/www/example.com/
    <Directory />
        Options FollowSymLinks
        AllowOverride All
    </Directory>
```

Thats locked out other domains pointing at my IP but when I simply type IP in address bar I am sent to /var/www/example.com

---

### Post by Cheesemill on 2013-02-14
When you are using virtual hosts if a page is requested by IP address instead of a URL it automatically matches the first enabled site, if you do an 'ls -l' of /etc/apache2/sites-enabled you'll find that your example.com file is top of the list.

You can solve your issue by creating and enabling a new virtual host and naming it 000-whatever so that it is always first in the listing of available sites. Just create an error page or a redirect on this vhost to do whatever you want.

---

### Post by SlugSlug on 2013-02-14
Thanks cheesemill,

Thats working now but it's now blocked the non www. address

[www.example.com]("http://www.example.com") works but not example.com

Do I need two sites enabled or is there a better way?

---

### Post by matt_symes on 2013-02-14
Hi
 
I'm sure there's a mod-security rule that can do this.
 
Install mod security and the mod security core rule set.
 
I'm open to correction if i am wrong though.
 
Kind regards

---

### Post by SlugSlug on 2013-02-14
just needed

```
ServerName example.com
ServerAlias *.example.com
```



Thanks all

---

### Post by spynappels on 2013-02-14
> **SlugSlug said:**
> just needed

```
ServerName example.com
ServerAlias *.example.com
```



Thanks all

That works for now, but what if you want to add a virtualhost of a subdomain like mail.example.com (e.g. for webmail) or members.example.com (e.g. for a members only sub-site)?

Maybe safer replacing the * with www to leave subdomains with different sites possible?

---

### Post by SlugSlug on 2013-02-14
ok thanks changed

---

