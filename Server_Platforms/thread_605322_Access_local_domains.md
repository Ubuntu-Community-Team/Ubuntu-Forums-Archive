---
title: "Access local domains"
date: 2007-11-06
forum: Server Platforms
---

### Post by godsfshrmn on 2007-11-06
I am using webmin and ISPConfig to host a domain on a local machine. What config options do I need to do in order for me to access the domain locally? I can access it via my cell phone's internet, but not locally.

---

### Post by bmathis on 2007-11-07
you need to add it your dns or you can add it manually to your hosts file

> sudo nano /etc/hosts

follow the scheme and add the internal ip address and the domain name.

---

### Post by godsfshrmn on 2007-11-08
I have the domain.com working right now, but how about [www.domain.com?](www.domain.com?) I added another entry in the hosts file for that and it didnt appear to do anything. I need that to access some config areas.

---

### Post by bmathis on 2007-11-12
> **godsfshrmn said:**
> I have the domain.com working right now, but how about [www.domain.com?](www.domain.com?) I added another entry in the hosts file for that and it didnt appear to do anything. I need that to access some config areas.

That ones kinda easy as well, but you'll need to edit your vitualhost for your website to make it work.

```
<VirtualHost *:80>
        ServerAdmin admin@example.com
        **ServerName www.example.com**
        DocumentRoot /var/www/website
</VirtualHost>

<VirtualHost *:80>
        ServerAdmin admin@example.com
        **ServerName example.com**
        DocumentRoot /var/www/website
        **Redirect / http://www.example.com/**

       The rest of your virtualhost crap goes here!

</VirtualHost>
```

I made the first virtualhost tag show [www.example.com](www.example.com) domain and the second tag has the redirect with an absolute URL path.

NOTE: This is all in the same file.

Hope this helps

---

