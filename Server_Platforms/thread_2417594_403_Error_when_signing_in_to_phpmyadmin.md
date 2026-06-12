---
title: "403 Error when signing in to phpmyadmin"
date: 2019-04-24
forum: Server Platforms
---

### Post by robertcull1 on 2019-04-24
I am installing phpMyAdmin per the instructions  here:

[https://devanswers.co/installing-phpmyadmin-nginx-ubuntu-18-04/](https://devanswers.co/installing-phpmyadmin-nginx-ubuntu-18-04/)

I get to part "2. Create Symbolic Link".

$ sudo ln -s /usr/share/phpmyadmin /var/www/html/phpmyadmin

When I visit the website <my-ip address>/phpmyadmin I get:

**403 Forbidden**
nginx/1.14.0 (Ubuntu)

---

### Post by spjackson on 2019-04-25
Have you checked /var/log/nginx/error.log ?

Possible causes:
[LIST]
[*]File ownership/permission
[*]Folder/site permission in nginx config
[*]Following symlinks is disabled in nginx config (controlled by disable_symlinks in /etc/nginx/nginx.conf but I understand it's off by default)
[/LIST]

---

### Post by robertcull1 on 2019-04-25
bump

---

### Post by robertcull1 on 2019-04-25
When I paste in the contents of the file it says:

Forbidden: You don't have permission to access /newreply.php
on this server.
Apache/2.4.7 (Ubuntu) Server at ubuntuforums.org Port 443

---

### Post by robertcull1 on 2019-04-25
I have found out when I try to post "HTTP/<the letter one>.<the letter one> I get errors trying to post my error log. So I am posting my error.log like this:

2019/04/24 16:04:06 [emerg] 24932#24932: unexpected end of file, expecting "}" in /etc/nginx/sites-enabled/mytest1.com:92
2019/04/24 16:06:31 [emerg] 24939#24939: unexpected end of file, expecting "}" in /etc/nginx/sites-enabled/mytest2.com:92
2019/04/24 16:10:11 [notice] 25028#25028: signal process started
2019/04/24 17:03:36 [error] 25029#25029: *8 directory index of "/var/www/mytest1.com/public_html/phpmyadmin/" is forbidden, client: <my IP address>, server: mytest1.com, request: "GET /phpmyadmin/ HTTP/<the letter one>.<the letter one>", host: "<my IP address>"
2019/04/24 17:05:04 [error] 25029#25029: *9 directory index of "/var/www/mytest1.com/public_html/phpmyadmin/" is forbidden, client: 192.168.43.67, server: mytest1.com, request: "GET /phpmyadmin/ HTTP/<the letter one>.<the letter one>", host: "<my IP address>"
2019/04/24 17:14:59 [error] 25029#25029: *11 directory index of "/var/www/mytest1.com/public_html/phpmyadmin/" is forbidden, client: <my IP address>, server: mytest1.com, request: "GET /phpmyadmin/ HTTP/<the letter one>.<the letter one>", host: "<my IP address>"
2019/04/24 17:15:01 [error] 25029#25029: *11 directory index of "/var/www/mytest1.com/public_html/phpmyadmin/" is forbidden, client: <my IP address>, server: mytest1.com, request: "GET /phpmyadmin/ HTTP/<the letter one>.<the letter one>", host: "<my IP address>"
2019/04/24 17:35:55 [error] 25029#25029: *12 directory index of "/var/www/mytest1.com/public_html/phpmyadmin/" is forbidden, client: 192.168.43.67, server: mytest1.com, request: "GET /phpmyadmin/ HTTP/<the letter one>.<the letter one>", host: "<my IP address>"
2019/04/24 17:40:52 [error] 25029#25029: *13 directory index of "/var/www/mytest1.com/public_html/phpmyadmin/" is forbidden, client: <my IP address>, server: mytest1.com, request: "GET /phpmyadmin/ HTTP/<the letter one>.<the letter one>", host: "<my IP address>"
2019/04/24 17:40:53 [error] 25029#25029: *14 directory index of "/var/www/mytest1.com/public_html/phpmyadmin/" is forbidden, client: <my IP address>, server: mytest1.com, request: "GET /phpmyadmin/ HTTP/<the letter one>.<the letter one>", host: "<my IP address>"
2019/04/24 17:47:33 [error] 25029#25029: *15 directory index of "/var/www/mytest1.com/public_html/phpmyadmin/" is forbidden, client: <my IP address>, server: mytest1.com, request: "GET /phpmyadmin/ HTTP/<the letter one>.<the letter one>", host: "<my IP address>"
2019/04/24 17:58:35 [error] 25029#25029: *16 directory index of "/var/www/mytest1.com/public_html/phpmyadmin/" is forbidden, client: <my IP address>, server: mytest1.com, request: "GET /phpmyadmin/ HTTP/<the letter one>.<the letter one>", host: "<my IP address>"
2019/04/24 18:03:51 [error] 25029#25029: *18 directory index of "/var/www/mytest1.com/public_html/phpmyadmin/" is forbidden, client: <my IP address>, server: mytest1.com, request: "GET /phpmyadmin/ HTTP/<the letter one>.<the letter one>", host: "<my IP address>"
2019/04/24 18:18:50 [error] 25029#25029: *19 directory index of "/var/www/mytest1.com/public_html/phpmyadmin/" is forbidden, client: <my IP address>, server: mytest1.com, request: "GET /phpmyadmin/ HTTP/<the letter one>.<the letter one>", host: "<my IP address>"
2019/04/24 18:28:48 [error] 31505#31505: *1 directory index of "/var/www/mytest1.com/public_html/phpmyadmin/" is forbidden, client: <my IP address>, server: mytest1.com, request: "GET /phpmyadmin/ HTTP/<the letter one>.<the letter one>", host: "<my IP address>"
2019/04/24 18:28:56 [error] 31505#31505: *1 directory index of "/var/www/mytest1.com/public_html/phpmyadmin/" is forbidden, client: <my IP address>, server: mytest1.com, request: "GET /phpmyadmin/ HTTP/<the letter one>.<the letter one>", host: "<my IP address>"
2019/04/24 18:29:05 [error] 31505#31505: *1 directory index of "/var/www/mytest1.com/public_html/phpmyadmin/" is forbidden, client: <my IP address>, server: mytest1.com, request: "GET /phpmyadmin/ HTTP/<the letter one>.<the letter one>", host: "<my IP address>"
2019/04/24 18:31:55 [error] 31505#31505: *2 directory index of "/var/www/mytest1.com/public_html/phpmyadmin/" is forbidden, client: <my IP address>, server: mytest1.com, request: "GET /phpmyadmin/ HTTP/<the letter one>.<the letter one>", host: "<my IP address>"
2019/04/24 19:21:32 [error] 31505#31505: *4 directory index of "/var/www/mytest1.com/public_html/phpmyadmin/" is forbidden, client: <my IP address>, server: mytest1.com, request: "GET /phpmyadmin/ HTTP/<the letter one>.<the letter one>", host: "<my IP address>"
2019/04/24 19:21:33 [error] 31505#31505: *4 directory index of "/var/www/mytest1.com/public_html/phpmyadmin/" is forbidden, client: <my IP address>, server: mytest1.com, request: "GET /phpmyadmin/ HTTP/<the letter one>.<the letter one>", host: "<my IP address>"
2019/04/24 20:58:02 [error] 31505#31505: *5 directory index of "/var/www/mytest1.com/public_html/phpmyadmin/" is forbidden, client: 127.0.0.1, server: mytest1.com, request: "GET /phpmyadmin/ HTTP/<the letter one>.<the letter one>", host: "localhost"
2019/04/25 11:59:06 [error] 31505#31505: *7 directory index of "/var/www/mytest1.com/public_html/phpmyadmin/" is forbidden, client: <my IP address>, server: mytest1.com, request: "GET /phpmyadmin/ HTTP/<the letter one>.<the letter one>", host: "<my IP address>"
2019/04/25 12:07:22 [error] 31505#31505: *8 "/var/www/mytest1.com/public_html/phpmyadmin/index.html" is forbidden (13: Permission denied), client: <my IP address>, server: mytest1.com, request: "GET /phpmyadmin/ HTTP/<the letter one>.<the letter one>", host: "<my IP address>"

---

### Post by spjackson on 2019-04-25
> **robertcull1 said:**
> 
2019/04/24 17:03:36 [error] 25029#25029: *8 directory index of  "/var/www/mytest1.com/public_html/phpmyadmin/" is forbidden, client:  <my IP address>, server: mytest1.com, request: "GET /phpmyadmin/  HTTP/<the letter one>.<the letter one>", host: "<my IP  address>"

I think this is a side effect of the error below. The webserver does not have permission to see whether there's an index file.

> **robertcull1 said:**
> 
2019/04/25 12:07:22 [error] 31505#31505: *8 "/var/www/mytest1.com/public_html/phpmyadmin/index.html" is forbidden (13: Permission denied), client: <my IP address>, server: mytest1.com, request: "GET /phpmyadmin/ HTTP/<the letter one>.<the letter one>", host: "<my IP address>"
"(13: Permission denied)" means that the permissions on the filesystem prevent the webserver user (probably www-data) from reading the file. (Side issue: Why index.html not index.php?)

You can trace access to the file as follows:
```

sudo su -s /bin/bash www-data -c "ls -l /var/www/mytest1.com/public_html/phpmyadmin"

```
The error 13 above implies that you should get "Permission denied", so remove directories from the right until it works. That will show you where you need to change permissions.

---

### Post by robertcull1 on 2019-04-25
There is no "index.html" in that directory. There is an "index.php".

The command you suggested gave me this:

$ sudo su -s /bin/bash www-data -c "ls -l /var/www/mytest1.com/public_html/phpmyadmin" lrwxrwxrwx 1 robert robert 21 Apr 24 18:17 /var/www/mytest1.com/public_html/phpmyadmin -> /usr/share/phpmyadmin

Here are the permissions on /usr/share/phpmyadmin:
drwxr-xr-x   10 root root  4096 Apr 24 18:14 phpmyadmin

What do you mean remove directories from the right?

What command should I use to change the permissions and what directories do I need to change?

---

### Post by spjackson on 2019-04-30
> **robertcull1 said:**
> There is no "index.html" in that directory. There is an "index.php".

That is that I would expect but in your original post the error message says 
```

"/var/www/mytest1.com/public_html/phpmyadmin/index.html" is forbidden (13: Permission denied)

```

> 
The command you suggested gave me this:

$ sudo su -s /bin/bash www-data -c "ls -l /var/www/mytest1.com/public_html/phpmyadmin" lrwxrwxrwx 1 robert robert 21 Apr 24 18:17 /var/www/mytest1.com/public_html/phpmyadmin -> /usr/share/phpmyadmin

Here are the permissions on /usr/share/phpmyadmin:
drwxr-xr-x   10 root root  4096 Apr 24 18:14 phpmyadmin

That would seem to be ok then, provided that www-data is the right user (depends on your nginx config files) and assuming the files in /usr/share/phpmyadmin are readable.

> 
What do you mean remove directories from the right?

I meant trying it first with /var/www/mytest1.com/public_html/phpmyadmin then with /var/www/mytest1.com/public_html then with /var/www/mytest1.com then with /var/www then with /var. However, that is now irrelevant since the files appear reachable at the lowest level, so the problem can't be higher up.

> 
What command should I use to change the permissions
Possibly chmod a+rx for directories and chmod a+r for files unless the content needs more protection than that. For a more secure setup, you would typically have the whole web tree owned by 'www-data' (if that's the right user) not 'robert' and not readable by others. On the other hand /usr/share/phpmyadmin is normally root owned and readable by all.

> 
and what directories do I need to change?
We don't know. That's what we are trying to find out.

Most webservers that I maintain use Apache. I only have one that uses nginx. Sorry I can't really help further.

---

