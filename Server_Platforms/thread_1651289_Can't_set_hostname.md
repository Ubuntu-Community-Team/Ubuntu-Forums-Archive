---
title: "Can't set hostname"
date: 2010-12-22
forum: Server Platforms
---

### Post by clay7 on 2010-12-22
Hello,

I've looked at several tutorials and since i'm a newb I can't figure them out. I'm trying to set my hostname on my LAMP 10.04. What files do I need to configure? (all IP's below are fake)

Here are the first lines from /etc/apache2/sites-available/default

```
<VirtualHost 111.111.111.111:80>
	ServerAdmin webmaster@localhost
```

/etc/apache2/ports.conf  has these lines after the comments

```
NameVirtualHost 111.111.111.111:80
Listen 80
```

/etc/hosts

```
127.0.0.1 localhost
111.111.111.111 mysite.com
```

/etc/hostname
```
mysite
```

Thank you,

---

### Post by koenn on 2010-12-23
/etc/hostname + reboot.
having it in /etc/hosts is a good idea.

unless, of course, by "set my hostname" you do not really mean "set the hostname" but something completely different such as  "set up apache with virtual hosts" or "create a DNS record that resolves my hostname to the correct IP address" or "I'm going to throw a party but I want someone else to be the host".

---

### Post by clay7 on 2010-12-23
Thank you, koenn. I've put the hostname "mysite.com" (not really mysite.com) in each of those locations. No errors were reported on reboot. I've tested the Linode by typing the IP in my browser and I can see the default page. 

Am I now clear to order a SSL certificate for the domain? SSL is enabled and has been tested.

---

### Post by koenn on 2010-12-23
what you've done so far, afaik, is give the system a name. That's all.


It would help that you explain a bit about what you're doing. Setting up a website / webserver I suppose ?  
iirc, SSL certs are FQDN-specific, so you need DNS before you even think about getting a certificate. 

Unless you give some context, you risk getting correct answers to wrong questions. 


---------------------
besides that, I'm not really in to web servers and SSL, so if anyone else wants to have a go at this ....

---

### Post by clay7 on 2010-12-23
Yes, I'm setting up a LAMP web server. It's a VPS from Linode. I will have only one domain on the server. Thanks for your help!

---

