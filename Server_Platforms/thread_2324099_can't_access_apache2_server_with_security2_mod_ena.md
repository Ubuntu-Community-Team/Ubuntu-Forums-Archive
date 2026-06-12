---
title: "can't access apache2 server with security2 mod enabled"
date: 2016-05-10
forum: Server Platforms
---

### Post by ptn107 on 2016-05-10
I have apache2 2.4.18 installed on my server with libapache2-mod-security2 & modsecurity-crs installed and configured.  I can access apache locally on the server (127.0.0.1 [localhost]) with security2/modsecurity enabled but I can only access it from other machines on the local network when security2/modsecurity is disabled.  I've been up and down the configuration files apache2.conf, security2.conf, & modsecurity.conf and can't figure out where it is declared that other boxes can't get in.

---

### Post by ptn107 on 2016-05-10
/var/log/apache2/error.log seems to point to one of the modsecurity rules /usr/share/modsecurity-crs/base_rules/modsecurity_crs_21_protocol_anomalies.conf which says "Host header is an ip address".  So i can't access apache via ip address from the other machines? That's crap.  Looks like I'm telling modsecurity to ignore this conf.

Update: In lieu of deleting the block of code in /usr/share/modsecurity-crs/base_rules/modsecurity_crs_21_protocol_anomalies.conf that deals with blocking ip addresses in headers, I've begrudgingly manually added the ip and apache servername to each machines /etc/hosts file.

---

