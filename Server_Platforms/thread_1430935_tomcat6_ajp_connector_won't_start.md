---
title: "tomcat6 ajp connector won't start"
date: 2010-03-16
forum: Server Platforms
---

### Post by leptogenesis on 2010-03-16
I'm trying to do a standard mod_jk setup--get apache to forward requests to Tomcat.  I must admit that I'm not so familiar with the details of mod_jk, but I got this working before when I had used tomcat 6 directly from apache's website, but now that I've switched to the version in Ubuntu's repositories I can't get it working.  

The log for mod_jk says:

```
[Mon Mar 15 23:59:41 2010] [5575:3004840816] [error] ajp_send_request::jk_ajp_common.c (1359): (ajp13_worker) connecting to backend failed. Tomcat is probably not started or is listening on the wrong port (errno=111)
[Mon Mar 15 23:59:41 2010] [5575:3004840816] [error] ajp_send_request::jk_ajp_common.c (1359): (ajp13_worker) connecting to backend failed. Tomcat is probably not started or is listening on the wrong port (errno=111)
[Mon Mar 15 23:59:41 2010] [5575:3004840816] [error] ajp_service::jk_ajp_common.c (2212): (ajp13_worker) Connecting to tomcat failed. Tomcat is probably not started or is listening on the wrong port
```

and indeed, netstat confirms that there's nothing listening on port 8009.  However, I've made sure that the following line in my server.xml is uncommented:

```
    <!-- Define an AJP 1.3 Connector on port 8009 -->

    <Connector port="8009" protocol="AJP/1.3" redirectPort="8443" />


```

Any idea why the connector doesn't start listening when I start tomcat?

---

### Post by leptogenesis on 2010-03-16
Fixed it...I was editing /usr/share/tomcat6/skel/conf/server/xml, but the right one was /etc/tomcat/server.xml.

---

