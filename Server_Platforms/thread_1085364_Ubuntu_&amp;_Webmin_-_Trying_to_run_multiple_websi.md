---
title: "Ubuntu &amp; Webmin - Trying to run multiple websites"
date: 2009-03-03
forum: Server Platforms
---

### Post by Presto-X on 2009-03-03
Hello everyone,

I have installed and updated Ubuntu server 8.10 then I installed Webmin 1.45 and updated it also.

I have setup my first domain lets call it "domain-a.com", and then I setup "domain-b.com" and restarted apache. but whenever I go to domain-b.com in the browser it loads domain-a.com, I setup custom folders for each.

I have setup the Address with both my public static ip and with the servers inturnal ip address. This is how I have the virtual servers setup:

Address: Any
Port: Any
Document Root: /home/myusername/www/domain-a
Server Name: domain-a.com

Address: Any
Port: Any
Document Root: /home/myusername/www/domain-b
Server Name: domain-b.com

What am I missing?

---

### Post by volkswagner on 2009-03-03
Make sure the site is in the enabled list.

```
ls -alt /etc/apache2/sites-enabled
```

Make sure the permissions are correct for your files in domain-b.  Group should be set to www-data or what ever you are using for apache.

Check the logs in  /var/log/apache2

```
cat /var/log/apache2/access.log
```

```
cat /var/log/apache2/error.log
```

---

### Post by ikonia on 2009-03-03
you do know that one of the reasons webmin is not available as a package in ubuntu is because it was dropped for security reasons and compatability issues with the way ubuntu sets out certainly application configuration files like apache.

---

### Post by bigbearomaha on 2009-03-03
Webmin is able to be run as securely a any admin app, Jamie Cameron does a tremendous amount of work to make it so.  Just because Ubuntu veers away from debian in packaging doesn't make the apps better or  worse, it only means that Ubuntu is inconsistent with debian

As has been said in other threads, most security is up to how the admin configures access and apps, keeps up with security updates etc...

Have you been to the Webmin doc site?  tey have very good documentation for setting up these very things.
[URL="http://doxfer.com/Webmin/Modules"]
http://doxfer.com/Webmin/Modules[/URL]

Have fun, learn lots

Big Bear

---

### Post by E_K on 2009-03-03
just follow this how to, nice and easy

[http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

---

