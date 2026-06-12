---
title: "IP Aliasing, Virtual Host and SSL issues"
date: 2009-06-27
forum: Server Platforms
---

### Post by thepreacher on 2009-06-27
Naration:

I have 5 static IP addresses, one network card and need to host 10 domains 3 of which need to have SSL. I have assigned 1 of the static IPs to the server and have setup ip aliasing for the rest of the IPs. Is it posible to combine IP and Namebased virtual hosting on Apache? whereby 3 of the IPs will be assigned to specific domains and 1 IP will be assinged to all the other 7 domains that do not require SSL support.

I'll appreciate the correct steps to Create IP aliasing on Ubuntu and how to use the IP aliasing the the purpose outlined above. 

Commands and codes will be most helpful eg what files need to be modifieded etc. Thanks.

---

### Post by jhannah on 2009-06-30
Indeed it is, both the VirtualHost and NameVirtualHost directives will take a particular IP address instead of using a wildcard. Every site will technically be setup in a VirtualHost container and the configuration should look something like this:

```

NameVirtualHost *:80

<VirtualHost 1.1.1.1:80>
  ServerName domain1.com
  # Other directives
</VirtualHost>

<VirtualHost 1.1.1.1:443>
  ServerName domain1.com
  # Other directives
</VirtualHost>

<VirtualHost *:80>
  ServerName domain2.com
  # Other directives
</VirtualHost>

```

In this case, any HTTP traffic to 1.1.1.1 will always hit the first VirtualHost container, no matter the hostname. However, all other HTTP traffic to the machine will end up hitting the last container. Is that what you are looking to setup?

---

### Post by Wim Sturkenboom on 2009-07-01
And for the https part:
```


<VirtualHost 172.18.32.235:443>
DocumentRoot "/home/wim/tacroom/www/scheduler/web"
ServerName tac.btd-techweb02:443
... other stuff here
</VirtualHost>
<VirtualHost 172.18.32.236:443>
DocumentRoot "/home/wim/btd_general/www/asset_register/web"
ServerName asset_register.btd-techweb02:443
... other stuff here
</VirtualHost>

```

---

### Post by thepreacher on 2009-07-01
Thanks jhannah and Wim Sturkenboom for your help. I've got it working now with the IP aliasing and everything. I have put all the Virtual Host configurations in one file. To be honest i cannot figure out exactly what i was doing differently except I put each domains configuration into a seperate file.

If I were to go that route as seems to be the norm in ubuntu, how should I  break the virtual host configurations up?

thanks again

---

