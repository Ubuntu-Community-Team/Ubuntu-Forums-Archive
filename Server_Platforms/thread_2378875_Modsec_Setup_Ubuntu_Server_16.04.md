---
title: "Modsec Setup Ubuntu Server 16.04"
date: 2017-11-28
forum: Server Platforms
---

### Post by markshepparduk on 2017-11-28
Hi eveyone,
I followed this guide to install [https://2buntu.com/articles/1571/installing-lamp-modsecurity-modsecurity-crs-on-ubuntu-1604/](https://2buntu.com/articles/1571/installing-lamp-modsecurity-modsecurity-crs-on-ubuntu-1604/)
On installing Modsec and i had to make minior changes as some of the information was outdated.

Anyone now when i visit my site i automatically get block and get the following error in the log

ModSecurity: Access denied with code 500 (phase 1). Operator EQ matched 0 at TX. [file "/usr/share/modsecurity-crs/rules/REQUEST-901-INITIALIZATION.conf"] [line "61"] [id "901001"] [msg "ModSecurity Core Rule Set is deployed without configuration! Please copy the crs-setup.conf.example template to crs-setup.conf, and include the crs-setup.conf file in your webserver configuration before including the CRS rules. See the INSTALL file in the CRS directory for detailed instructions."] [severity "CRITICAL"] [hostname "192.168.1.251"] [uri "/"] [unique_id "Wh1pX38AAQEAACAFdxQAAAAA"]

This is on my home network hence the internal IP, i can't see what i have missed form that guide to fix this?

Thanks

Mark

---

