---
title: "install a lamp server ontop of xubuntu"
date: 2006-12-03
forum: Server Platforms
---

### Post by Wofl on 2006-12-03
hello

i read a thread where it showed how to set up a lamp server. now i wanted to do just that. so i downloaded the server install cd and installed it. but i then had to give up on the part of getting my wireless going. so now i switched to using xubuntu under which i (finally after 5 reinstalls) got my wireless working. now i have heard of people having a server install working and then using some groovy commands get all the xubuntu stuff on top. now i wanted to know what i have to do to get all the server stuff on top off my xubuntu, and how to get it to set up a nice lamp server for me.

and then will the server run in the background while i can still use the pc for other stuff??? (like online radio and surfing)

sorry that its so long
and thanks for any answers

---

### Post by az on 2006-12-03
See here:

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

To install the LAMP stack on any ubuntu system, install the following packages:

apache2 php5-mysql libapache2-mod-php5 mysql-server


If this is not a production system (need it to run securely and reliably) it will work fine on a desktop machine.

---

### Post by Wofl on 2006-12-03
does this include the automatic configuration and all???

if read horror stories that it takes an professional hours to get all those set up manually from source, and that the lamp install takes care off all that

---

### Post by az on 2006-12-04
> **Wofl said:**
> does this include the automatic configuration and all???



The LAMP stack is what it is.  You will need to set a mysql root password and then install your web application.  But as for the LAMP infrastructure, it is good to go.

It takes less than four minutes.

---

### Post by Wofl on 2006-12-04
thanks
i got it all installed now

but when i start apatche, it tells me that it could not determine the "server's fully qualified domain name" and that it now is "using 127.0.1.1 for ServerName"

how can i set a server name?

---

### Post by technodigifreak on 2006-12-04
> **Wofl said:**
> thanks
i got it all installed now

but when i start apatche, it tells me that it could not determine the "server's fully qualified domain name" and that it now is "using 127.0.1.1 for ServerName"

how can i set a server name?

You'll need to do this under root permissions.  Assuming that ubuntu.domain.local is your FQDN.  Then edit your /etc/hosts file so that it has an entry like the following (of course replace the X's with your IP):

```

127.0.0.1            localhost
XXX.XXX.XXX.XXX      ubuntu.domain.local ubuntu

```

Save the file and then issue the following command.

```
echo ubuntu.domain.local > /etc/hostname
```

restart your networking that should put the changes into effect, if it doesn't then you need to reboot.

---

### Post by virilc on 2007-09-14
> **Wofl said:**
> thanks
i got it all installed now

but when i start apatche, it tells me that it could not determine the "server's fully qualified domain name" and that it now is "using 127.0.1.1 for ServerName"

how can i set a server name?

What I did was I just edited (as root or just sudo) /etc/apache2/apache2.conf and placed "ServerName myserver.namehere.com" anywhere in there and the message went away! (remove the double quotes)

---

