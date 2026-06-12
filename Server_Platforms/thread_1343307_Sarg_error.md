---
title: "Sarg error"
date: 2009-12-01
forum: Server Platforms
---

### Post by munchi3s on 2009-12-01
I am using squid3 to proxy a local network. I have sarg setup to publish the access log on a intranet server for the LAN to view. I have my main server set up with a mounted ftp drive that is the webserver for our network. I have sarg (with webmin) setup to record its reports to /mnt/squid-reports which is the webserver but for some reason every time I try to get a report I get an error message as below:

**Now generating Sarg report from Squid log file /var/log/squid3/access.log and all rotated versions ..**

sarg -l /var/log/squid3/access.log.1 
SARG: (report) Cannot open file: /var/www/squid-reports/2009Nov17-2009Dec01/sarg-general
**.. Sarg failed! See the output above for details.**

No matter where I tell sarg to put the files it always gives me the same error. Does anyone know what is going on?

---

### Post by Ilalmi on 2009-12-02
I assume you already checked the usual suspects (file owner and permissions, disk space). 
Have you tried sarg -x to get some additional information?

---

### Post by munchi3s on 2009-12-02
Yeah, Permissions are not an issue and neither is disk space. I will try sarg -x

---

### Post by munchi3s on 2009-12-02
Well I got SARG to write agian but it still won't write to the mounted directory. So instead of having the mounted directory of the apache server for hosting I will have the apache server connect to the main server for its information. I still havn't fixed the problem. If anyone knows why SARG had this error please tell me. 

Thanks

---

