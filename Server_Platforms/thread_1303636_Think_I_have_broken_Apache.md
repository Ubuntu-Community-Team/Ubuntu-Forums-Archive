---
title: "Think I have broken Apache"
date: 2009-10-28
forum: Server Platforms
---

### Post by Twizzle on 2009-10-28
I have Ubuntu running on a small home server. On this I have Zarafa for my email etc and last nighht I tried to do two things. Upgrade to the latest version and add a new user.

I followed the upgrade guide [here]("http://www.zarafa.com/wiki/index.php/Upgrading_Zarafa") - and everything seemed to go ok. I restarted apache using ```
/etc/init.d apache2 reload
``` and tried to log into the webaccess page for Zarafa and could see that the upgrade seemed to have worked.

I then tried to add a new user to it by using 

```
sudo zarafa-admin -c name -p secret -e email@address -f "Full Name"

```

but got an error, so I then tried to create the user account on Ubuntu which seemed to work. I rebooted my server and... can't access the web side of things.

I can ssh into it. I can see the server as a shared drive. I can go to [https://192.168.1.101:10000/](https://192.168.1.101:10000/) for webmin which works, but anything where I try [http://192.168.1.101/anything](http://192.168.1.101/anything) else does not work.

Previously I could go to server/ , server/zm , server/muin.

It seems to me that something has happened to Apache but I don't know how to check. I have looked in the log files and there is nothing that jumps out at me.

---

### Post by koenn on 2009-10-28
run
```

/etc/init.d/apache2 stop
/etc/init.d/apache2 start

```
and post the error msgs you get

---

### Post by kevin11951 on 2009-10-28
also post the output of 
```
tail /var/log/apache2/error.log
```

---

