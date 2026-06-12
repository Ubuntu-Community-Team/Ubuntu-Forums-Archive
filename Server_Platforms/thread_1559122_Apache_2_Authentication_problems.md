---
title: "Apache 2 Authentication problems"
date: 2010-08-23
forum: Server Platforms
---

### Post by Admiral Yi on 2010-08-23
Hi,
I have set up an apache 2 server, but can't seem to get authentication to work properly. I have set up this in my apache2.conf:

```
<Directory /var/www>
AllowOverride AuthConfig
</Directory>

<Directory /var/www>
AuthType Basic
AuthName "Restricted Files"
AuthUserFile /usr/local/apache/passwd/passwords
Require bob
</Directory>
```

I have created the passwords file with htpasswd and defiantly have the right password for bob. However, when  I try to log in the box just comes up over and over again and never authenticates. What am I doing wrong? I'm a newbie, so please bear with me if I've missed something really stupid.

---

### Post by Ryan Dwyer on 2010-08-23
Apache might not have read access to the password file. Check Apache's error log (/var/log/apache2/error.log).

---

### Post by Admiral Yi on 2010-08-23
I changed the permissions on the file to 777, but it didn't help. I checked the logs, and these are the only two things that stand out

```
[Mon Aug 23 13:32:52 2010] [error] [client 192.168.0.2] access to / failed, reason: require directives present and no Authoritative handler.

```

and 

```
[Mon Aug 23 10:15:25 2010] [error] [client 192.168.0.2] File does not exist: /var/www/favicon.ico

```

---

### Post by cdenley on 2010-08-23
```

<Directory /var/www>
AllowOverride AuthConfig
</Directory>

<Directory /var/www>
AuthType Basic
AuthName "Restricted Files"
AuthUserFile /usr/local/apache/passwd/passwords
Require **[COLOR="Red"]user[/COLOR]** bob
</Directory>

```

---

### Post by Admiral Yi on 2010-08-23
That worked, thanks.

---

### Post by nikhidet on 2011-10-11
hey 
do u create htpasswd file? im trying to authenticate my apache server but till now i still didnt get it.....to make it worse i couldnt even create my htpasswd file huhu...it always give me this following mesej
-cannot create file /usr/local/apache2/passwd/passwords..any ideas?

---

