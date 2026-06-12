---
title: "auth_mysql and apache2"
date: 2007-02-27
forum: Server Platforms
---

### Post by Honig on 2007-02-27
I am running a 6.06 LTS server for a wireless gateway (chillispot, freeradius, & mysql). I have built some simple pages to add/delete users, change passwords, and view usage. I have attempted to use auth_mysql (libapache2-mod-auth-mysql) to authenticate admin users who need these tools, but since I am posting here I guess you can figure out it is not working. :) 

**My install steps:**
1. apt-get install libapache2-mod-auth-mysql
2. a2enmod auth_mysql
3. created & populated database
4. edited .htaccess and apache2.conf

I have two valid accounts on the server in the correct table but when I enter in the Username and Password it just loops like I am not authorized at all. I have verified that I can logon to the mysql server with the account/password that is specified in the apache2.conf and I have run a simple select query against the table where my users are stores; this works fine.

I cannot figure out for the life of me what the problem is. It is hard to diagnose from the lack of hard error messages unless I break it completely causeing the server to go HTTP 500 Error on me.

I would appreciate any help that any one could give me.

Below are my .htaccess, apache2.conf, and access.log files:
**.htaccess**
```
AuthName "MySQL Testing"
AuthType Basic
<Limit GET POST>
Auth_MySQL_Password_Table clients
Auth_MySQL_Username_Field username
Auth_MySQL_Password_Field passwd
AuthMySQL_Empty_Passwords off
Auth_MySQL On
require valid-user
</Limit>

```

**apache2.conf**
```

Auth_MySQL_Info localhost auth_user XXXXXXXXXXX
Auth_MySQL_General_DB auth

```

**Entry in /var/log/apache2/access.log for one of the attempts**
```

xxx.xxx.xxx.xxx - test [27/Feb/2007:15:27:48 -0600] "GET /radcreate/main.html HTTP/1.1" 401 521 "-" "Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1) Gecko/20060601 Firefox/2.0 (Ubuntu-edgy)"

```

---

### Post by Honig on 2007-02-27
NEVERMIND! :D 
I found the problem. Seems that the howto I was reading was not very comprensive about the 
AuthMYSQL_Encryption_Types setting. I set that to match my password field in the database and it worked like a charm.

**.htaccess**
```
AuthName "MySQL Testing"
AuthType Basic
<Limit GET POST>
Auth_MySQL_Password_Table clients
Auth_MySQL_Username_Field username
Auth_MySQL_Password_Field passwd
AuthMySQL_Empty_Passwords off
AuthMySQL_Encryption_Types Plaintext
Auth_MySQL On
require valid-user
</Limit>

```

Thanks again for reading this. 
Have a great day!

---

### Post by lonetree on 2007-04-30
Hi Honig,

looks like you have successfully configured your wifi hotspot, I have been trying to figure out these few days on configuring one for my company, and I couldn't get one decent tutorial that teach step by step. Do you have any reference that you can direct me to or could you share your experience? Maybe you could write a comprehensive HowTo that benefits the whole community.

Thanks, awaiting your reply.

Regards,

---

### Post by Honig on 2007-05-01
> **lonetree said:**
> Hi Honig,

looks like you have successfully configured your wifi hotspot, I have been trying to figure out these few days on configuring one for my company, and I couldn't get one decent tutorial that teach step by step. Do you have any reference that you can direct me to or could you share your experience? Maybe you could write a comprehensive HowTo that benefits the whole community.

Thanks, awaiting your reply.

Regards,

The one that helped me the most is: [https://help.ubuntu.com/community/WifiDocs/ChillispotHotspot](https://help.ubuntu.com/community/WifiDocs/ChillispotHotspot)

I have thought about documenting what I did to get mine working. I am going to redo this when I get a new server in the next few days and will try to do a better job documenting it. But that one above is the one that helped me figure out what is going on between freeRADIUS, Chillispot, and my laptop.

---

