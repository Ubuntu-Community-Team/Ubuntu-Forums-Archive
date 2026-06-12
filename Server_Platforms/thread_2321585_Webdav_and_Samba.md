---
title: "Webdav and Samba"
date: 2016-04-23
forum: Server Platforms
---

### Post by kambiz2 on 2016-04-23
Hi everybody,
The configuration of my server is: Ubuntu 14.04.02 lts, apache 2.4.7 and php  5.5.9

I've configured a shared folder (/srv/samba/docs) with Windows, via Samba

And now I want to use webdav to edit documents from this folder. I've been reading about it and I've done the follow:

I've added these modules:
- sudo e2enmod dav
- sudo a2enmod dav_fs
- sudo a2enmod dav_lock

I've created a webdav user with his password:
- sudo htpasswd -c /etc/apache2/users.password user

I've modified /etc/apache2/sites-available/000-default.conf:
- added this at the first line DavLockDB /srv/samba/docs
- added a virtualhost
<VirtualHost *.80>
    Alias /webdav /srv/samba/docs
    <Directory /srv/samba/docs>
       DAV On
       AuthType Basic
       AuthName "user"
       AuthUserFile /etc/apache2/users.password
       Require valid-user
   </Directory>
</VirtualHost>

In this file I've got another virtualhost, for samba configured, in the same port.

After this, I restart apache and it's suposed it should go, but no.

I map a network drive:
Z:
\\ip\webdav
User: user
password: xxx

And it asks again

Can anybody help me? What I'm doing wrong?

Thanks very much

---

### Post by TheFu on 2016-04-23
Ooops. My mistake.  Misread the column headings.

Cannot help with the root issue, just know that webdav has a history of many security issues.

---

### Post by kambiz2 on 2016-04-23
??

---

### Post by SeijiSensei on 2016-04-23
> AuthUserFile /etc/apache2/users.password
Did you add users to this file with the htpasswd program?

The files /var/log/apache2/access.log and /var/log/apache2/error.log are your friends.  What errors do they report when you try to connect with webdav?

I doubt webdav on a local office network is any less secure than Samba.

---

### Post by kambiz2 on 2016-04-24
Ok, the log files, in this case, are not my friends. There is nothing interesting :(
Ok, I use samba because I've implemented OwnCloud in my server, and it's perfect to share files between us (Windows users) and our costumers (Owncloud users).
But very often, we go to visit our costumers, and we need to edit files (word and excel) and save.  Of course, using Owncloud we can download, edit and finally upload. But our workers wants to edit directly, without downloading.
Is there a better way than Webdav?

Thanks very much

---

### Post by volkswagner on 2016-04-24
I see you used:

```
sudo htpasswd -c /etc/apache2/users.password user
```

To create the user.

What are the permissions of the file /etc/apache2/users.password?

It should be readable by apache user www-data.

---

### Post by TheFu on 2016-04-24
> **kambiz2 said:**
>  
Is there a better way than Webdav?
 

Better? Don't know if it is better, but I'd use openvpn. You need/want it for any road warrior anyway so they don't keep any sensitive data on their local machines and to protect email access to just authenticated users.

Is that better for your needs? I cannot say.

We use remote desktops for everything here. People are free to use whatever OS they want and remote back to the office using x2go. This way data never leaves our systems and if a laptop is stolen or broken, they only need to load 1 program on the replacement to be 100% back and productive again - x2go-client.   But this method does require internet connectivity, which isn't always available. That is the downside for our method. Management decided the inconvenience was worth it to keep the sensitive data secured.

---

