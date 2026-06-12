---
title: "Host data from two different locations on Apache?"
date: 2012-11-12
forum: Server Platforms
---

### Post by Roasted on 2012-11-12
I'm running a 12.04 box with Apache running. I have a few directories shared out, but they're all within the same DocumentRoot, which is /media/NAS/apache. Problem is, I have a directory on /media/NAS/motion that I want shared out. Sure, I could just re-route the "motion" dir to be a sub-dir under /media/NAS/apache, but it would create a bit of a headache for some other things. As a result, I'm questioning if I can just host a 2nd location with Apache somehow. Some reading suggests I may need a VirtualHost, or an Alias, but I'm not entirely certain. 

For right now I just created a symlink, which seems to work fine... but I'm not entirely sure how "proper" this is. In fact, I'm not even sure if I'm entirely sure if what I'm doing is entirely correct. I'm simply editing the /etc/apache2/sites-available/default config for what uses I need. Is that what I should be doing? Can anybody help me iron out exactly what I need to do? Thanks!

---

### Post by marks_linux on 2012-11-12
Alias would work well.

---

### Post by pkadeel on 2012-11-12
> **Roasted said:**
> I'm running a 12.04 box with Apache running. I have a few directories shared out, but they're all within the same DocumentRoot, which is /media/NAS/apache. Problem is, I have a directory on /media/NAS/motion that I want shared out. Sure, I could just re-route the "motion" dir to be a sub-dir under /media/NAS/apache, but it would create a bit of a headache for some other things. As a result, I'm questioning if I can just host a 2nd location with Apache somehow. Some reading suggests I may need a VirtualHost, or an Alias, but I'm not entirely certain. 

For right now I just created a symlink, which seems to work fine... but I'm not entirely sure how "proper" this is. In fact, I'm not even sure if I'm entirely sure if what I'm doing is entirely correct. I'm simply editing the /etc/apache2/sites-available/default config for what uses I need. Is that what I should be doing? Can anybody help me iron out exactly what I need to do? Thanks!
Setting up virtual host is quite easy if you want to do that. Create a file named "motion" and put the following text in it. Replace * with any specific IP address you want to use or else leave it as is. Replace "motionsitefullyqulifiedname" with the actual site address to be used.
```

<VirtualHost *:80>
    ServerName motionsitefullyqulifiedname
    ServerAdmin admin@motionsitefullyqulifiedname
    DocumentRoot /media/NAS/motion
    <Directory  /media/NAS/motion/>
        Options Indexes FollowSymLinks
        AllowOverride All
        Order Deny,Allow
        Allow from all
    </Directory>
    DirectoryIndex index.html
    ErrorLog ${APACHE_LOG_DIR}/motion-error.log
    CustomLog ${APACHE_LOG_DIR}/motion-access.log" combined
</VirtualHost>

```
Put this file in /etc/apache2/site-available folder then execute following commands
```

sudo a2ensite motion
sudo service apache2 restart

```
edit /etc/hosts file and add the following replacing the IP_address with the IP address you are using or 127.0.0.1 for localhost. replace motionsitefullyqulifiedname with the site domain name you are using for that site
```
IP_address                      motionsitefullyqulifiedname
```

---

### Post by sandyd on 2012-11-12
something like
```

Alias /motion /media/NAS/motion

```

The motion folder will then be accessable as if it were in /media/NAS/apache

---

### Post by Roasted on 2012-11-12
> **sandyd said:**
> something like
```

Alias /motion /media/NAS/motion

```

The motion folder will then be accessable as if it were in /media/NAS/apache

How is this different from a symlink?

---

### Post by sandyd on 2012-11-13
> **Roasted said:**
> How is this different from a symlink?

The link is not at filesystem level - i.e. if you try to visit /media/NAS/apache/motion through the terminal, it will not exist.

Its generally used when you don't want to use the FollowSymLinks option, but they are just two ways of doing the same thing.

---

