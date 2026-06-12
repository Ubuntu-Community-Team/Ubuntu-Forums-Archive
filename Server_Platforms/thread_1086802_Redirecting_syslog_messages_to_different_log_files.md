---
title: "Redirecting syslog messages to different log files"
date: 2009-03-04
forum: Server Platforms
---

### Post by befrenchy on 2009-03-04
What I'd like to know is if there is any way to redirect syslog messages from specific devices to a specific log file as opposed to have everything go to /var/log/messages? If so, what would the syslog.conf file look like?

Thanks in advance for your response,
Eric

---

### Post by HermanAB on 2009-03-04
I guess you need to look at both of these:
/etc/syslog.conf and /etc/logrotate.conf

Then play with some redirection commands:
[http://www.mathinfo.u-picardie.fr/asch/f/MeCS/courseware/users/help/general/unix/redirection.html](http://www.mathinfo.u-picardie.fr/asch/f/MeCS/courseware/users/help/general/unix/redirection.html)

Cheers,

Herman

---

