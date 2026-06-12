---
title: "Problem setting up domein"
date: 2011-02-16
forum: Server Platforms
---

### Post by Mkaveli on 2011-02-16
Hello i am new to Ubuntu server and so far i am loving it. But i have registered two domain names that i want to use to connect to my ubuntu server. I was wondering how to do this i was looking at bind9 but that didn't work that great. The server is behind a router with firewall i can connect to it using the external IP address but i like to use the two domain names if that is possible.

Thanks, Mkaveli

---

### Post by volkswagner on 2011-02-16
Do you have a static ip address from your isp?  If you do, the simple way is to use the DNS server from your registrar.  Point your A record, CNAME and MX record (if using email server) to your ip address in your registrars control panel.

---

### Post by Neo@Matrix on 2011-02-16
> **Mkaveli said:**
>  The server is behind a router with firewall i can connect to it using the external IP address but i like to use the two domain names if that is possible.

Most of the routers can expose 1 (one!) local machine to internet. 
Look for something like "DMZ" or Virtual server in Your router settings.
With that , UR server should be available on internet by Your domain- more or less depending on other settings in Your server config file.

---

### Post by Neo@Matrix on 2011-02-17
Bump...

---

