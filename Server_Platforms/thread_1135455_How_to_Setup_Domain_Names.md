---
title: "How to Setup Domain Names"
date: 2009-04-24
forum: Server Platforms
---

### Post by LALING on 2009-04-24
I'm using CentOS as guest on VirtualBox, and I'd like to know how to setup or point my domain name to it so I can run my websites. I have more than one site/domain that I will be hosting, so how do I go about on setting this up?

I know this is not a CentOS community forum, but it is the most active forum for Linux OS's.

---

### Post by kvizz on 2009-04-24
if your virtualbox installation has its own ip then point all your domains' a-records to this ip and to google for "apache virtual domains"

---

### Post by Wiebelhaus on 2009-04-24
You should be running the appropriate Ubuntu version for your task , but what kvizz said is good advice.

---

### Post by LALING on 2009-04-24
> **kvizz said:**
> if your virtualbox installation has its own ip then point all your domains' a-records to this ip and to google for "apache virtual domains"

My Windows XP OS and VirtualBox Linux OS shares the same IP address. Is there a way I can get another IP for my VirtualBox?

---

### Post by kvizz on 2009-04-27
if your ip address is assigned to you by your provider then take a look at [http://mydebian.blogdns.org/?p=111](http://mydebian.blogdns.org/?p=111) etc

---

