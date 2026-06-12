---
title: "Need help configuring httpd.conf"
date: 2007-07-16
forum: Server Platforms
---

### Post by capnbenzo on 2007-07-16
Hey There,

I setup Apache2 a little while ago to only accept connections from machines on my home network.  Now I want to open it up to requests from outside.  How can I change my httpd.conf file to reflect this?  Here's the file right now:

<Directory /var/www/htdocs>
     # Deny all accesses by default
     Order deny,allow
     # Allow access to local machine
     Allow from 127.0.0.1
     # Allow access to local network
     Allow from 192.168.1.
     # Allow access to a certain machine
     Allow from 192.168.3.6
     # Set the default policy to deny
     Deny from all
    </Directory>



Thanks in advance for help.  BTW- I'm a newb... go easy on me!

---

### Post by twistedtwig on 2007-07-16
I am not at home so cant double check the syntax (or if I am actually right) but I would say delete / comment out the allow XX.XX.XX.XX and have allow all instead.

I am sure someone more knowledgeable will correct me if I am wrong

---

### Post by capnbenzo on 2007-07-16
> **twistedtwig said:**
> I am not at home so cant double check the syntax (or if I am actually right) but I would say delete / comment out the allow XX.XX.XX.XX and have allow all instead.

I am sure someone more knowledgeable will correct me if I am wrong


I was wondering if I need to change the 'Order deny,allow' to 'Order allow, deny'.   Hmmmm...

---

### Post by Mr. C. on 2007-07-16
Order allow,deny
allow from all

MrC

---

### Post by capnbenzo on 2007-07-16
Thanks!

This worked!

---

