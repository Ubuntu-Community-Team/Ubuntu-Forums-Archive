---
title: "Apache 2 screen notice"
date: 2009-01-05
forum: Server Platforms
---

### Post by happyhacker on 2009-01-05
During bootup I get the line:

"Apache(2) Could not reliably determine the server's fully qualified domain name using 192.168.0.2 for server name."

Is this something I should correct (and if so how)?

dhcp is from router and config. is "static" in interfaces file.

---

### Post by bluefrog on 2009-01-05
it is just telling you the /etc/hosts (or hostname, not sure...) do not contain a FQDN for your IP.

it doesn't matter and won't prevent apache from functioning.

---

### Post by happyhacker on 2009-01-05
I use my server on two networks 192.168.0.x and 192.168.1.x. Maybe if I put the fqdn in (I assume this is the servername) this would be better. Is this the case and how should I do it?

---

### Post by cdenley on 2009-01-05
> **cantthinkofanickname said:**
> I use my server on two networks 192.168.0.x and 192.168.1.x. Maybe if I put the fqdn in (I assume this is the servername) this would be better. Is this the case and how should I do it?

FQDN = fully qualified domain name
[http://en.wikipedia.org/wiki/FQDN](http://en.wikipedia.org/wiki/FQDN)
I don't think it would cause any problems, but you can add this line to /etc/hosts
```

192.168.0.2 www.myserver.com

```
then edit /etc/hostname
```

www.myserver.com

```
then run
```

sudo hostname www.myserver.com

```
Replace "www.myserver.com" with your correct FQDN, of course.

---

### Post by Iowan on 2009-01-05
[This]("https://help.ubuntu.com/community/ApacheMySQLPHP#Troubleshooting%20Apache") help page offers the following suggestion:> If you get this error:
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
then use a text editor such as "sudo nano" at the command line or "gksudo gedit" on the desktop to create a new file,
sudo nano /etc/apache2/conf.d/fqdn
or
gksu "gedit /etc/apache2/conf.d/fqdn"
then add
ServerName localhost
to the file and save. This can all be done in a single command with the following:
echo "ServerName localhost" | sudo tee /etc/apache2/conf.d/fqdn
Personally, I like the previous suggestions better.

---

### Post by happyhacker on 2009-01-06
Thanks I have done that. As my server is called "acdorserver1" should this be the name?

---

### Post by cdenley on 2009-01-06
> **cantthinkofanickname said:**
> Thanks I have done that. As my server is called "acdorserver1" should this be the name?

Well, that is not a FQDN. See my previous post.

---

### Post by happyhacker on 2009-01-06
Does that mean I can call my server [www.acdorserver1.com?](www.acdorserver1.com?) I thought that was to do with the internet. Is there something to read up in this context?

---

