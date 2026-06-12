---
title: "[Apache2] Bandwidth limitation on SSL Virtualhost"
date: 2021-11-23
forum: Server Platforms
---

### Post by Gkar on 2021-11-23
Hi everybody, 

  I would like to know if someone had already experienced a limitation on bandwidth with apache2 on SSL Virtualhost on ubuntu server

  I use ubuntu 21.04 server with Apache2 2.4.46 and all the package is up to date

  On hardware side i used core i9 11900T with 32 GB of Ram. 
 
  last month my ADSL cable was replaced by Fiber Optics with nearly 1 Gbps (930 Mbps) same on up and down (i used speedtest to verify it).

  When i tried to share files , the limit of my banwidth was 110 Mbps on my website with HTTPS, 930 Mbps with HTTP.

  Then i tried to install NGINX and create a small site with HTTPS and then my banwidth increase to nearly max speed.

  Is there any ideas of what i have to try to increase bandwidth with mod_ssl of Apache2.

Best regards.
G'kar

---

### Post by MAFoElffen on 2021-11-23
Sort of...

HTTPS does take a bit longer, because after an SSL certificate is  installed, HTTPS requires several more handshakes than HTTP during  website access. ... Therefore, the **access** speed of HTTPS is going to be slower than that of HTTP after SSL certificates are used. But there are other factors that affect it also... https requests are set at the same priorities as http requests... But need RequestWorkers to process those handshakes.... There is a way to tune that... To change the MaxRequestWorkers and a few other settings to tune that. It depends on when you search your /var/log/apache2/error.log and find this message:
```

egrep 'reached MaxRequestWorkers setting, consider raising the MaxRequestWorkers setting' /var/logapache2/error.log

```
I know that this is an old answer to this, but I think they explain it well...
[https://serverfault.com/questions/413743/https-is-over-50-times-slower-then-http](https://serverfault.com/questions/413743/https-is-over-50-times-slower-then-http)

 MPM settings affects this, and MaxRequestWorkers are calculated by: ServerLimit x ThreadsPerChild = MaxRequestWorkers

---

