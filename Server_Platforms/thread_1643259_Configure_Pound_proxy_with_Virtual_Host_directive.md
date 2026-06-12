---
title: "Configure Pound proxy with Virtual Host directive"
date: 2010-12-11
forum: Server Platforms
---

### Post by R.Bucky on 2010-12-11
I have 1 static ip address and multiple servers and domains. Most of my HTTP requests come in to a primary box. However, I have a domain that I want the primary box to forward to another server, also port 80. Using [the documentation for Pound]("http://www.apsis.ch/pound/"), I found the Virtual Host directive for the pound.cfg. However, outside requests are not forwarded to the correct box. Below is the primary area of concern within my pound.cfg.

```
 ListenHTTP
            Address 10.1.10.25
            Port    80

            Service
                HeadRequire "Host: .*www.olyubuntu.nwlinux.com.*"

                BackEnd
                    Address 10.1.10.26
                    Port    80
                End
            End
End
```

Internal requests for this domain are directed properly, as I have Bind pointed to that box. Anyone have ideas as to why the above configuration is not functioning appropriately for outside requests?

System: Ubuntu Server v10.04, dhcp3. bind9, etc...

---

