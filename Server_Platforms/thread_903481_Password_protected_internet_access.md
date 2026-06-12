---
title: "Password protected internet access??"
date: 2008-08-28
forum: Server Platforms
---

### Post by gm04030276 on 2008-08-28
Hey all,
Recently I have set up a squid proxy server in work with squidGuard...now mister MD wants to know if we can actually password protect the internet...does anyone know if this is possible with squid or something similar?

---

### Post by cdenley on 2008-08-28
I think what you want is a captive portal. I'm not sure if squid can do it.

---

### Post by forger on 2008-08-28
maybe pessulus (lockdown editor) could help:
> Description: lockdown editor for GNOME
 pessulus enables the system administrator to set mandatory settings in
 GConf, which apply to all users, restricting what they can do, which may
 be of particular usefulness for kiosks (internet cafes, for example).
 .
 Examples of what can be locked down are the panels (no changes in the panel
 configuration are allowed, locking their position and their contents), some
 of their functions individually (disabling screen locking and log out), the
 web browser (disabling specific protocols, arbitrary URLs, forcing the user
 to be in fullscreen mode), among many others.

```
sudo apt-get install pessulus
```

System > Administration > Lockdown editor

---

### Post by forger on 2008-08-28
Another suggestion is to use ubuntu firewall (ufw --help) to block port 80 until someone executes a command and types in a password:
```
zenity --entry --text "May I take your order?"
man ufw

```

---

### Post by HermanAB on 2008-08-28
Yes, Squid can do password controlled access.  You can create rules to control access any way you want, including user name, user groups, time of day, and URL based ACLs.

Cheers,

H.

---

### Post by moonpup on 2008-08-28
As long as the users are configured to go through the proxy, here's how to setup password authentication with squid. This is based on Redhat defaults but should be similar for Ubuntu.

 Password Authentication Using NCSA

You can configure Squid to prompt users for a username and password. Squid comes with a program called ncsa_auth that reads any NCSA-compliant encrypted password file. You can use the htpasswd program that comes installed with Apache to create your passwords. Here is how it's done:

1) Create the password file. The name of the password file should be /etc/squid/squid_passwd, and you need to make sure that it's universally readable.

```
[root@bigboy tmp]# touch /etc/squid/squid_passwd
[root@bigboy tmp]# chmod o+r /etc/squid/squid_passwd
```

2) Use the htpasswd program to add users to the password file. You can add users at anytime without having to restart Squid. In this case, you add a username called www:

```
[root@bigboy tmp]# htpasswd /etc/squid/squid_passwd www
New password:
Re-type new password:
Adding password for user www
[root@bigboy tmp]#
```

3) Find your ncsa_auth file using the locate command.

```
[root@bigboy tmp]# locate ncsa_auth
/usr/lib/squid/ncsa_auth
[root@bigboy tmp]#
```

4) Edit squid.conf; specifically, you need to define the authentication program in squid.conf, which is in this case ncsa_auth. Next, create an ACL named ncsa_users with the REQUIRED keyword that forces Squid to use the NCSA auth_param method you defined previously. Finally, create an http_access entry that allows traffic that matches the ncsa_users ACL entry. Here's a simple user authentication example; the order of the statements is important:

```

# Add this to the auth_param section of squid.conf
#
auth_param basic program /usr/lib/squid/ncsa_auth /etc/squid/squid_passwd
 
#
# Add this to the bottom of the ACL section of squid.conf
#
acl ncsa_users proxy_auth REQUIRED
 
#
# Add this at the top of the http_access section of squid.conf
#
http_access allow ncsa_users

```

Finally, save changes to the file and restart squid :)

---

### Post by cdenley on 2008-08-28
> **HermanAB said:**
> Yes, Squid can do password controlled access.  You can create rules to control access any way you want, including user name, user groups, time of day, and URL based ACLs.

Cheers,

H.

I believe this will only password-protect websites accessed through the proxy. They will still be able to access the internet (SSH,FTP,IM).

---

### Post by moonpup on 2008-08-28
You are correct :) The rest is left for the admin to control through the use of border routers and firewalls.

I believe at this point from the OP, they are looking to control web browsing... but I could be wrong.

---

