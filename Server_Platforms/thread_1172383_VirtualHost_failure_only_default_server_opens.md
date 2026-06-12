---
title: "VirtualHost failure only default server opens"
date: 2009-05-28
forum: Server Platforms
---

### Post by erikbrannlund on 2009-05-28
I have tried to set up 2 virtualhosts on my Ubuntu/apache2 installation. However I only see the default host. As I'm more of a windows guy I can't find whats wrong.
My default
```

<VirtualHost *:80>
    ServerAdmin erik@localhost
 
    DocumentRoot /var/www/
<Directory />
        Options FollowSymLinks
 
.
.
.
.
.

```My second host
```

<VirtualHost *:80>
    ServerAdmin erik@telia.com
 
    DocumentRoot /home/brollop/www/
 
.
.
.
.
.
.
.

```
 
Edit: Removed long listing not containing the error

---

### Post by Alekz_ on 2009-05-28
You cannot start apache with a non-privileged account.

Try `sudo`:

```
sudo /etc/init.d/apache2 restart
```

About your 'vhosts'.. Well, as far as I know, vhost won't work IF you don't have different "server names" for each virtual host...

i.e

```
<VirtualHost *:80>
    ServerAdmin erik@telia.com
    ServerName your_server.com
    ServerAlias www.your_server.com
    DocumentRoot /home/brollop/www/
    <Directory /var/www/>
        ...
    </Directory>
</VirtualHost>

<VirtualHost *:80>
    ServerAdmin erik@telia.com
    ServerName your_server2.com
    ServerAlias www.your_server2.com
    DocumentRoot /home/brollop/www2/
    <Directory /var/www2/>
        ...
    </Directory>
</VirtualHost>
```

[]'s

---

### Post by erikbrannlund on 2009-06-01
Thanks for the answer! Isn't it strange when looking at something you have written yourself that it so often is impossible to see the error.
 
/Erik

---

