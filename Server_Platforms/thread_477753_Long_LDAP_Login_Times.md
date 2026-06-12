---
title: "Long LDAP Login Times"
date: 2007-06-18
forum: Server Platforms
---

### Post by Greslore on 2007-06-18
Greetings all,

I have a weird issue I was hoping someone could give me some insight to.  With Ubuntu 7.04.  I am using LDAP authentication and LDAP users can log in fine.  

However, if for example, the machine reboots and a user types in their LDAP username, the machine will pause for about 97 seconds until the password box becomes available.  This also happens when I use a local account, log out, then type in an LDAP username - pause for 97 seconds.

I checked the /etc/libnss-ldap.conf file and changed the following:

# Search timelimit
# timelimit 30 < DEFAULT
timelimit 10

#Bind/connect timelimit
#bind_timelimit 30 < DEFAULT
timelimit 10

bind_policy soft

But still that long pause.  I am also indeed using nscd.  Anyone have any ideas?

---

### Post by AlexThomson_NZ on 2007-06-18
Just a thought- but is it trying to use ipv6 before timing out and falling back to ipv4?  Also, how long is the ping?

Actually, I have seen something similar before too, caused by connecting a very new openssl version to a box with a very old openssl version.  Don't know how applicable this would be with LDAP tho...

---

### Post by Thearnold on 2007-06-26
Are you sure nscd daemon is running?  I have a similiar problem except nscd will run for 5 minutes or less than core dumps if you use nscd -d to start it to see what is happening.  If I start with startup script nscd stops without and log entries.


The Arnold

---

### Post by Greslore on 2007-07-04
Followup:

I figured out the problem.  I needed to install the portmap package.  As soon as I did "sudo apt-get install portmap" no more long login times.  Wahooo!  :D

---

