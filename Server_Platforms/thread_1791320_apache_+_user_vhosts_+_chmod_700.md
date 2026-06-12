---
title: "apache + user vhosts + chmod 700"
date: 2011-06-26
forum: Server Platforms
---

### Post by jamesa00789 on 2011-06-26
My current set up is:

[LIST]
[*]User Virtual hosts in /home/*/public_html
[*]Suexec, so that apache runs CGI scripts as the owner of that script
[*]chmod 700 on /home/* so that other users cannot browse each others home directories
[/LIST]

* = username of user on server

But however I am getting error 403: You don't have permission to access /home/*/public_html on this server.

So basically I want a server where I can add users and allow them to run their own scripts, but have a complete lock down on where they can go, so they are unable to browse other user directories or execute CGI scripts under user "www-data" which can browse other directories.

Any help on this would be much appreciated.

---

### Post by jamesa00789 on 2011-08-17
Bump

---

### Post by jamesa00789 on 2011-08-17
Vhost config:

```
<VirtualHost *:80>
        SuexecUserGroup jamesa00789 jamesa00789
        ServerAdmin admin@*****
        ServerName www.****
        ServerAlias ***
        DocumentRoot /home/jamesa00789/public_html
</VirtualHost>
```

---

### Post by tswsl1989 on 2011-08-17
Try adding the following block:
```

<Directory /home/jamesa00789/public_html>
    Order Deny, Allow
    Allow from All
    AllowOverride None #Adjust this if you need to use .htaccess files
</Directory>

```

---

