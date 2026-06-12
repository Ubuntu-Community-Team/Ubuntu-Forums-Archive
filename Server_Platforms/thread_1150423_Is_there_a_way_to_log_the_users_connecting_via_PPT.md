---
title: "Is there a way to log the users connecting via PPTP"
date: 2009-05-06
forum: Server Platforms
---

### Post by CrashTest71 on 2009-05-06
Hi Folks,
    Is there a way to record in the logs which user account (from the chap-secrets file) has connected via a PPTP VPN?  Currently nothing appears in any of the logs except an IP address, and I'd like to keep track of who is has connected.

Thanks in advance.
 :)

---

### Post by CrashTest71 on 2009-05-06
Ok, I can answer my own question now....

If you have the option "logwtmp" specified in the /etc/pptpd.conf file then all connections and disconnections are logged in /var/log/wtmp.

You can use the "last" command to view connections and disconnections. 

"last |grep ppp" works well. :)

---

