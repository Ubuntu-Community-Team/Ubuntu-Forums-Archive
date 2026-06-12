---
title: "Mod_security configuration"
date: 2013-11-09
forum: Server Platforms
---

### Post by termvrl on 2013-11-09
**Mod_security configuration**
[INDENT]                     Hi, 
This is repost. i have post it before. but no response. 
Thanks

Dear All,
i'm new to web server security. i have a few question on modsecurity and web server.
first, let me brief what i try to do. I have apache server running a DVWA web application on ubuntu 12.04 64bit.
I installed modsecurity on that server to detect and generated alert on  attacks. Alert that generated from modsecurity than pass to a remote  syslog server using rsyslog.
And i also want to monitor the web server nic and cpu usage, so that i  can create a benchmark before and after implement modsecurity to web  server.

My questions:
1) i want to monitor the nic and cpu usage for a period of time. Appreciate if you suggest scripts/tools for that. 
2) i noticed that logging for modsecurity quiet challenging. Anyone can  share with me how to send modsecurity log/alert to remote server. What i  have doned, using local rsyslog in web server, i take the  modsecurlty_audit.log as input for rsyslog, and then send it to remote  syslog server. My problem is, the log send line by line. 
                                                         
```

192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: --e7b0fc0d-F--
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: HTTP/1.1 304 Not Modified
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: Last-Modified: Tue, 30 Apr 2013 22:46:46 GMT
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: ETag: "1a06ac-2e4-4db9bc6a5a180"
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: Accept-Ranges: bytes
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: Content-Length: 0
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: Vary: Accept-Encoding
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: Keep-Alive: timeout=5, max=100
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: Connection: Keep-Alive
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: Content-Type: application/javascript
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: --e7b0fc0d-E--
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: --e7b0fc0d-H--
11/7/2013 10:54:28 PM     UDP Traffic Received from 192.168.0.13: 
192.168.0.13|<187>Nov  7 06:54:26 ubuntu tag1: Message: Rule  7fb26ee5aa30 [id "950901"][file  "/etc/modsecurity/activated_rules/modsecurity_crs_41_sql_injection_attacks.conf"][line  "77"] - Execution error - PCRE limits exceeded (-8): (null).         

```             
     
Appreciate your helps.
Thanks                 
[/INDENT]

---

