---
title: "[apache] Virtual Directory generation problem"
date: 2008-07-28
forum: Server Platforms
---

### Post by Myth123 on 2008-07-28
hi ,
  I tried to configure a virtual directory for apache2
I follow following method

sudo gedit /etc/apache2/conf.d/alias

Alias /web /home/mithun/projects/

<Directory /home/mithun/projects/>
DirectoryIndex index.html
Options FollowSymLinks
AllowOverride None
order allow,deny
allow from all
</Directory>

sudo /etc/init.d/apache2 restart

Still its giving me 404 error !! :(

---

