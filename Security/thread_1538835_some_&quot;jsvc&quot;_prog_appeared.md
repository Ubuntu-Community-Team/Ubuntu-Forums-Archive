---
title: "some &quot;jsvc&quot; prog appeared"
date: 2010-07-25
forum: Security
---

### Post by vaibhav292 on 2010-07-25
i ran netstat
**************o/p**************************
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      3167/cupsd      
tcp        0      0 117.99.6.100:53970      66.220.146.11:80        ESTABLISHED 4839/firefox    
tcp        0      0 117.99.6.100:57727      174.120.149.130:80      ESTABLISHED 4839/firefox    
tcp        0      0 117.99.6.100:56091      69.63.176.177:80        ESTABLISHED 4839/firefox    
tcp        0      0 117.99.6.100:45868      69.63.189.11:80         ESTABLISHED 4839/firefox    
tcp6       0      0 :::8080                 :::*                    LISTEN      20832/jsvc      
tcp6       0      0 ::1:631                 :::*                    LISTEN      3167/cupsd      
*********************************************
.
.
i recently installed tomcat, is it because of this??
.
.
**IS IT A SECURITY THREAT??**

---

### Post by cariboo on 2010-07-25
It may be an idea to check google first before asking about anything you don't know about. By googling jsvc I get [this ]("http://commons.apache.org/daemon/jsvc.html")result.

Much of security is knowing what your system is running, I would suggest you read a services documentation before installing it, so you are aware of what it does, and how it works. Blindly installing services without knowing what they do is just an invitation to get cracked.

---

