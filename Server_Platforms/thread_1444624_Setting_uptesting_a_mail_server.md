---
title: "Setting up/testing a mail server"
date: 2010-04-01
forum: Server Platforms
---

### Post by hockey97 on 2010-04-01
Hi, I just tested my mail server for security. I got only this warning saying: Reverse DNS does not match SMTP Banner. 

what does this mean? I have my own server and notice my host name I use my domain name but at the end before the .com  I see my ISP'S name.

For example instead of having a hostname like domain.com.

I have something like this: domain.ISP.com 

How do I change this? I manually deleted the .ISP part but still my ISP name automatically gets attached.

Also is there any good tutorial on teaching how to setup postfix with mysql?

---

### Post by cdenley on 2010-04-01
You can view your SMTP banner with this command:
```

echo QUIT|nc 127.0.0.1 25

```

To change the hostname for postix:
```

sudo postconf -e myhostname=mydomain.com
sudo /etc/init.d/postfix restart

```

---

### Post by KB1JWQ on 2010-04-01
You also want to make sure that your rDNS matches your A records.  If you lack forward confirming reverse DNS, you're likely to get spam-binned most places.

---

