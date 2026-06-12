---
title: "using hosts.deny"
date: 2012-04-29
forum: Security
---

### Post by shirkkan on 2012-04-29
I've read that hosts.deny file is used to avoid specific users/groups to access some services.

On the other hand, if I write "localhost" in the browser it shows the index page in /var/www, and I want to restrict this access, so I guess that if I put "all:all" in hosts.deny, that should deny the access to everybody, shouldn't it? But it doesn't work.

How can I use hosts.deny to deny access to /var/www?

thanks!

---

### Post by codemaniac on 2012-04-29
Cant you change the permissions to /var/www to restrict aceess .
```
sudo chmod -R 640 /var/www/
```
would bar the outside world to access your running webserver .

---

### Post by CharlesA on 2012-04-29
> **codemaniac said:**
> Cant you change the permissions to /var/www to restrict aceess .
```
sudo chmod -R 640 /var/www/
```
would bar the outside world to access your running webserver .
If you change the permissions, you would still be able to access the web server by going to [http://localhost](http://localhost) but www-data wouldn't have write access.

I thought the default permissions for /var/www/ was 775 with it being owned by root?

---

### Post by codemaniac on 2012-04-29
> **CharlesA said:**
> If you change the permissions, you would still be able to access the web server by going to [http://localhost](http://localhost) but www-data wouldn't have write access.

I thought the default permissions for /var/www/ was 775 with it being owned by root?

Changing the permissions to 640 causes the webserver throw up 403 forbidden messages .

> You don't have permission to access / on this server.

755 restores the access .

---

### Post by CharlesA on 2012-04-29
> **codemaniac said:**
> Changing the permissions to 640 causes the webserver throw up 403 forbidden messages .

Right cuz www-data would count as "other". That would still prevent you from browsing from another machine wouldn't it?

I guess I don't really understand what the OP is trying to accomplish.

---

### Post by unspawn on 2012-04-30
> **shirkkan said:**
> How can I use hosts.deny to deny access to /var/www?
Unless you find a way to compile your web server with *libwrap* support you don't. As long as "localhost" resolves to 127.0.0.1 and the client uses any proto:// URI other than file:// try setting an Order directive in a .htaccess file or your web servers configuration file instead:
```

<Directory /path/to/directory>
Order Allow,Deny
deny from 127.0.0.
allow from all
</Directory>

```

---

