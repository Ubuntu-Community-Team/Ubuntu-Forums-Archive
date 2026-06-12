---
title: "Ubuntu Server 16 latest has SNMP issues ?"
date: 2016-10-25
forum: Server Platforms
---

### Post by soamz on 2016-10-25
I was using Ubuntu 14.04 server LTS for last 1 year without any issues. Last friday, I did apt-upgrade and then the server broke, no idea, why. It was very irritating. 

So, I ended up installing 16.x latest from Ubuntu website and tried to install SNMP, but it doesnt work. 

I follow this tutorial, 
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-an-snmp-daemon-and-client-on-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-an-snmp-daemon-and-client-on-ubuntu-14-04)



Why the service start command are no more working on 16.x latest ?

Whats wrong or what am I missing ?

---

### Post by cariboo on 2016-10-25
16.04 uses systemd. Have you tried the following command:

```
sudo systemctl restart snmp.service
```

---

