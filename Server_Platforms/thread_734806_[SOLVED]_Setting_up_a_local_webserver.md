---
title: "[SOLVED] Setting up a local webserver"
date: 2008-03-25
forum: Server Platforms
---

### Post by larsdk on 2008-03-25
Hi there,

I would like to set up Apache , PHP and mySQL on my laptop in order to develop sites. However, I don't want these pages to be accessible to anyone else but me, since it's just for developing sites, not for actual hosting. My question is if it is possible to install the above mentioned web development applications without having to open up any ports (which I guess is what it takes to have it running only locally?)?

Thanks in advance
Lars

---

### Post by jonabyte on 2008-03-25
You would need to open ports on your router/firewall and forward them to your server in order for the outside world to get access to them.

As long as you do not do this, it will remain for your eyes only.

I am assuming that you have a router in place??

---

### Post by Boyohazard on 2008-03-25
Setting it all up is quite easy try this tutorial:
[http://howtoforge.com/ubuntu_lamp_for_newbies](http://howtoforge.com/ubuntu_lamp_for_newbies)

---

### Post by larsdk on 2008-03-25
@Boyohazard

thanks for the link - it seems to be very easy indeed. 

@jonabyte

i don't have a router, but I do have a static IP-adress and what I want is basically to get the LAMP setup, but I don't want either apache, mysql or php to be able to communicate with anything else than [http://localhost](http://localhost) 

I just thought that the LAMP setup opened up some ports?

---

### Post by erginemr on 2008-03-25
You can install firestarter (GUI frontend to IPTables, the default firewall in Ubuntu) with:
```
sudo aptitude install firestarter
```
to check whether there are ports open and to manipulate them.

---

### Post by Boyohazard on 2008-03-25
> **larsdk said:**
> 

I just thought that the LAMP setup opened up some ports?

I don't think it will open any ports just default to use ports that tend to be open e.g Apache will listen on port 80 I believe (I can't recall what port MySQL defaults to)

---

### Post by keithweddell on 2008-03-25
Look in the [Apache Documentation]("http://httpd.apache.org/docs/2.0/") for information on the Order, Allow and Deny directives,.  These allow you to choose who can access your server.  You can, if you wish, set your server up so that only localhost can access it.

Keith

---

### Post by larsdk on 2008-03-25
> **erginemr said:**
> You can install firestarter (GUI frontend to IPTables, the default firewall in Ubuntu) with:
```
sudo aptitude install firestarter
```
to check whether there are ports open and to manipulate them.

and firestarter would look like your screenshot if all ports are closed?

---

### Post by larsdk on 2008-03-25
I just stumbled on this

[https://help.ubuntu.com/community/ApacheMySQLPHP#head-967a645a6dc898f3e00c3dc7063c6949a4957d52]("https://help.ubuntu.com/community/ApacheMySQLPHP#head-967a645a6dc898f3e00c3dc7063c6949a4957d52")

in which it says that

[INDENT]Securing Apache

If you just want to run your Apache install as a development server and want to prevent it from listening for incoming connection attempts, this is easy to do.

$ gksudo "gedit /etc/apache2/ports.conf"
$ password:

Change ports.conf so that it contains:

Listen 127.0.0.1:80

Save this file, and restart Apache (see above). Now Apache will serve only to your home domain, [http://127.0.0.1](http://127.0.0.1) or [http://localhost](http://localhost)

[/INDENT]

that should pretty much do the trick should it not?

---

### Post by Boyohazard on 2008-03-25
That's the one :)

---

### Post by larsdk on 2008-03-25
It seems to be working now :). Anything else I should be aware of, securitywise?

Oh, and does anybody know how to start and shutdown mySQL and Apache. I would like to make some launchers for that.

---

### Post by leohart on 2008-03-26
I normally use 

/etc/init.d/apache2 start to start Apache
/etc/init.d/apache2 stop to stop Apache

similarly for mysqld.

I have not seen any integrated solution that allows for easy start/stop of Apache/MySQL yet. However, I don't think typing the above lines are that bad.

---

### Post by nbitting on 2008-03-26
This was an excellent thread!  Thanks for all the info!

---

