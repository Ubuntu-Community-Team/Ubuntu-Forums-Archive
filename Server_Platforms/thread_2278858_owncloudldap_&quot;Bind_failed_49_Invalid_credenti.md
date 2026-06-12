---
title: "owncloud/ldap &quot;Bind failed: 49: Invalid credentials&quot;"
date: 2015-05-19
forum: Server Platforms
---

### Post by oandarilho01 on 2015-05-19
Hi,

Firstly, I hope this is the right section to ask about owncloud problems.

I'm running owncloud 8.0.2 in an Ubuntu Server 14.04.1 LTS (php 5.5.9-1ubuntu4.9). My user database is on a Windows Server, and all went fine until a few days ago. The problem is that new users can't login on owncloud webclient (and I have a small AD base, round 150 users), although they can log in on the windows server via RDP. Owncloud issues this on the log:

> {"reqId":"e9ed188fe2ff012a928a004a45c54074","remoteAddr":"CLI_IP","app":"user_ldap","message":"Bind failed: 49: Invalid credentials","level":3,"time":"2015-05-19T15:15:42+00:00"}
{"reqId":"e9ed188fe2ff012a928a004a45c54074","remoteAddr":"CLI_IP","app":"core","message":"Login failed: 'alias155' (Remote IP: 'CLI_IP', X-Forwarded-For: '')","level":2,"time":"2015-05-19T15:15:42+00:00"}


I'm aware there's owncloud 8.0.3, but I have another server, which was running 7.0.4 and started to present the same behavior and the (gradual) upgrade to 8.0.2 didn't fixed the problem.

I don't believe firewall rules are causing this problem. However, I can't say if this has started after a windows update. 

Any clues?

Thanks in advance

---

