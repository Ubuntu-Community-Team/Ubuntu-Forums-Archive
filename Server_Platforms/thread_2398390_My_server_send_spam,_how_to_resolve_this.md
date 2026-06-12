---
title: "My server send spam, how to resolve this ?"
date: 2018-08-11
forum: Server Platforms
---

### Post by gorgo126 on 2018-08-11
Hello,

I'm a beginner with Linux/ Ubuntu and I have a little problem.

I have a VPS at OVH with Ubuntu 16.04 and the last Plesk install on it.

Sinds the beginning my server seem to be blacklisted, apparently he send soms spam mail...

When I check CBL Lookup, here wath is say :
```
----------------------------------------------------- 
RESULTS OF LOOKUP 
139.99.198.6 is listed
This IP address was detected and listed 17 times in the past 28 days, and 0 times in the past 24 hours. The most recent detection was at Fri Aug 10 04:05:00 2018 UTC +/- 5 minutes
This IP address was self-removed 1 times in the past week.
New: many of these listings are caused by a MikroTik Router compromise. If you have a Microtik router, please consult this entry on the MikroTik Support Forum
If this IP address is NOT a shared hosting IP address, this IP address is infected with/emitting spamware/spamtrojan traffic and needs to be fixed. Find and remove the virus/spamware problem then use the CBL delisting link below. 
-----------------------------------------------------
```
Can you help me or tell me how can I resolve this problem ?
Thanks a lot,
Olivier.

---

### Post by HermanAB on 2018-08-11
Well, first you have to check whether the problem is real.

Use 'top' to see what is running.  Use 'ntop' and 'tcpdump' to see what is going over the network.

If the machine really has a mail server and is really sending junk - then simply 'kill -9 PID' the process that is doing it, then find the user account that is controlling it and 'userdel' it.  After that, the fight starts.

---

### Post by wildmanne39 on 2018-08-11
Hello and welcome to the forum gorgo126.

*Thread moved to **Server Platforms for a more appropriate fit**.* 

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

