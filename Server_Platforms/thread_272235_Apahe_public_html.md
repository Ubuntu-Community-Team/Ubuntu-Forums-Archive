---
title: "Apahe public_html"
date: 2006-10-05
forum: Server Platforms
---

### Post by hfranco on 2006-10-05
I'm currently hosting two personal websites on my computer under apache2, website1.com and website2.com. I have a public_html for a user named bob. How do I set it up so that I don't have to see website1.com/~bob and website2.com/~bob. I just want to see bob's public_html on website1.com

Is there a way where I can specify what domain name I want to show public_html to?

-hfranco

---

### Post by peanut butter on 2006-10-06
you will have to make a vhost.
this can be done by inserting the following lines into your apache2.conf:

```
        <VirtualHost *>
                ServerName MYDOMAINHERE.TLD
                DocumentRoot /Path/to/public/html/
        </VirtualHost>

```

for each site.:)

edit: [http://httpd.apache.org/docs/2.0/vhosts/](http://httpd.apache.org/docs/2.0/vhosts/) has more info on this including more feastures.:)

---

