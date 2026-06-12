---
title: "Installing An Ubuntu Hardy 8.04 LTS DNS Server With BIND"
date: 2010-06-13
forum: Server Platforms
---

### Post by th0r_ on 2010-06-13
I have been using the below mentioned guide to set up one:
[http://www.howtoforge.com/installing-an-ubuntu8.04-dns-server-with-bind](http://www.howtoforge.com/installing-an-ubuntu8.04-dns-server-with-bind)

I have been able to setup up everything correctly but get stuck at Step 10 -- 
Start up BIND, and check /var/log/syslog  for errors:
 /etc/init.d/bind9 start


Please refer the screenshot:
[http://imgur.com/4eypV.jpg](http://imgur.com/4eypV.jpg)


I checked /var/log/syslog for errors:
[http://imgur.com/2XBhB.jpg](http://imgur.com/2XBhB.jpg)


PS: I am a total noob at this.


Any assistance would be greatly appreciated as I am just helping a pal of mine with his school project.

---

### Post by Ryan Dwyer on 2010-06-13
Looks like your permissions on /etc/bind/named.conf are wrong. What do you get when you run ls -l /etc/bind/named.conf?

---

### Post by th0r_ on 2010-06-13
> **Ryan Dwyer said:**
> Looks like your permissions on /etc/bind/named.conf are wrong. What do you get when you run ls -l /etc/bind/named.conf?

[http://imgur.com/ywyz3.jpg](http://imgur.com/ywyz3.jpg)

Thanks!

---

### Post by Ryan Dwyer on 2010-06-13
I just installed bind9. Everything in /etc/bind/ is rw-r--r-- (yours is correct).

bind.keys, zones.rfc1918 and all the db.* files are owned by root:root.
rndc.key is owned by bind:bind.
All the named.conf files are owned by root:bind.

You should make sure all your files are the same. chown username:groupname filename to change each file. Then restart bind9.

---

### Post by th0r_ on 2010-06-13
> **Ryan Dwyer said:**
> I just installed bind9. Everything in /etc/bind/ is rw-r--r-- (yours is correct).

bind.keys, zones.rfc1918 and all the db.* files are owned by root:root.
rndc.key is owned by bind:bind.
All the named.conf files are owned by root:bind.

You should make sure all your files are the same. chown username:groupname filename to change each file. Then restart bind9.

Looks like the same to me:
[http://imgur.com/UHZex.jpg](http://imgur.com/UHZex.jpg)

I restarted bind again and experienced this:
[http://imgur.com/Wz4qP.jpg](http://imgur.com/Wz4qP.jpg)

Any more suggestions?

Thanks.

---

### Post by Ryan Dwyer on 2010-06-13
Your files are not the same as mine. All your files have the bind user and bind group applied to them. Make them the same as what I said in my previous post.

---

