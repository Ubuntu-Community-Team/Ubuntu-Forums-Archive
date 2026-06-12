---
title: "Apache and symbolic links"
date: 2011-07-17
forum: Server Platforms
---

### Post by TimeDistort12 on 2011-07-17
I am trying to make my Apache server show symbolic links in a directory listing, but have so far been unsuccessful.

In my latest attempt, I have placed the following code in .htaccess, in the directory with the symlinks that I want listing:

```
<Directory />
Options All
</Directory>
```

Im httpd-vhosts.conf, I have also placed the following code within the relative <VirtualHost></VirtualHost>:

```
Alias /music /home/n/Music
```

Any suggestions?

---

### Post by CharlesA on 2011-07-17
Check here: [http://www.maxi-pedia.com/FollowSymLinks](http://www.maxi-pedia.com/FollowSymLinks)

I've not used that option, so I don't know if it's supposed to accomplish what you want to do or not.

---

### Post by SeijiSensei on 2011-07-18
.htaccess files are disabled by default in Ubuntu.  In /etc/apache2/sites-enabled/000-default you'll see the "AllowOverride None" directive; that disables .htaccess.

You can either replace "None" with "All" there and restart, or you can add "Options FollowSymLinks" to the <Directory> stanza in your <VirtualHost> container.

Also, the <Directory> directive isn't used in .htaccess.  Everything in that file applies to the directory in which it's located, so there's no need for a <Directory> entry.

I've seen a lot of people having this problem with .htaccess.  I understand the logic of disabling it for security, but it sure wreaks havoc with people setting up Apache for the first time in Ubuntu.

---

### Post by CharlesA on 2011-07-18
> **SeijiSensei said:**
> .htaccess files are disabled by default in Ubuntu.

Does that apply to only newer versions of Ubuntu? I seem to recall using .htaccess to password protect a directory on Ubuntu 10.04 a while ago.

---

### Post by SeijiSensei on 2011-07-18
I think it was true then as well.  I recall installing 10.04LTS server in a virtual machine some months back, and the "AllowOverride None" directive was used there.

---

### Post by CharlesA on 2011-07-18
> **SeijiSensei said:**
> I think it was true then as well.  I recall installing 10.04LTS server in a virtual machine some months back, and the "AllowOverride None" directive was used there.

Thanks. :)

---

