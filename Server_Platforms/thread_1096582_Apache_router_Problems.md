---
title: "Apache router Problems"
date: 2009-03-15
forum: Server Platforms
---

### Post by antland01 on 2009-03-15
\\Hi,

When i try and Access my Apache server via my ip address it comes up with the routers configuration page but when i use the internal ip address (192.168.1.6) it comes up with my page i have port forwarded it to port 80 and it still does this i have even tryed to change my Apache port to 78 and portforwarded it on it i have my router hooked onto dyndns.org....what am i doing wrong ?:(

---

### Post by windependence on 2009-03-15
This is normal behavior. You will not be able to access your site from the external IP unless your router supports NAT reflection, and most home routers do not. 

If you want to use the DNS name from within your network, you will have to modify your hosts file to resolve the name to your internal IP. If you are accessing your site from a Windows client, the hosts file is located in Windows/system32/drivers/etc. In Linux or Unix boxes, it is usually in /etc/hosts. You should edit the file to look like this to make it work for you:

```
192.168.1.6      servername.mysite.com
```

Of course you need to replace servername and mysite with the proper names.

Restart the network before you try to access the site.

-Tim

---

### Post by Grey08 on 2009-03-15
try to access it outside your LAN, or you can ask your friend over the internet to access the page, it should work.

---

### Post by antland01 on 2009-03-15
> **windependence said:**
> This is normal behavior. You will not be able to access your site from the external IP unless your router supports NAT reflection, and most home routers do not. 


My router does support NAT i will try it tommorow from outside of my lan

---

### Post by windependence on 2009-03-15
> **antland01 said:**
> My router does support NAT i will try it tommorow from outside of my lan
Read carefully. I didn't say NAT, I said NAT [COLOR=Red]*reflection. *[COLOR=Black]This is where the outside IP address is essentially reflected back so that you can access your internal server as if you were outside the LAN. 

-Tim
[/COLOR][/COLOR]

---

### Post by antland01 on 2009-03-16
i have tryed it from and outside lan network and i can manage to access it thank you for or your help

---

