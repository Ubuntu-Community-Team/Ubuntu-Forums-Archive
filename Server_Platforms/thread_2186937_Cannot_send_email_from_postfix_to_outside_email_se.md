---
title: "Cannot send email from postfix to outside email servers."
date: 2013-11-10
forum: Server Platforms
---

### Post by russ2 on 2013-11-10
I have set up an email server and can send/receive email  localhost and I can receive mail from outside sources but I cannot send  emails to outside sources.  I get this error when I try to send to an  outside source such as live.com or gmail.com:


  Nov  8 22:15:13 server2 postfix/smtp[7598]: 699D480A64: to=,  relay=none, delay=122043, delays=122022/0.01/20/0, dsn=4.4.3,  status=deferred (Host or domain name not found. Name service error for  name=live.com type=MX: Host not found, try again)


  Any ideas where I could look to resolve this?

---

### Post by sanderj on 2013-11-10
What is your output of:

```
sander@flappie:~$ host -t mx live.com

live.com mail is handled by 5 mx2.hotmail.com.
live.com mail is handled by 5 mx3.hotmail.com.
live.com mail is handled by 5 mx4.hotmail.com.
live.com mail is handled by 5 mx1.hotmail.com.
sander@flappie:~$
```

---

### Post by russ2 on 2013-11-10
I typed in the command that you posted and this is what I got: "connection timed out; no servers could be reached".  I tried to use different ones also like yahoo and gmail

---

### Post by sanderj on 2013-11-10
So you have a DNS problem.

On what kind of network are you? At home, at work, behind a proxy, ... ?

What is the result of "host www.cisco.com" ?

---

### Post by russ2 on 2013-11-10
I am on a home network without a proxy.  I have the ability to set up dns entries and virtual servers into my router.  I have put smtp.myaddress.us into both tables.

Results:

[www.cisco.com](www.cisco.com) is an alias for [www.cisco.com.akadns.net](www.cisco.com.akadns.net).
[www.cisco.com.akadns.net](www.cisco.com.akadns.net) is an alias for wwwds.cisco.com.edgekey.net.
wwwds.cisco.com.edgekey.net is an alias for wwwds.cisco.com.edgekey.net.globalre dir.akadns.net.
wwwds.cisco.com.edgekey.net.globalredir.akadns.net is an alias for e144.dscb.aka maiedge.net.
e144.dscb.akamaiedge.net has address 23.202.48.170
;; connection timed out; no servers could be reached
;; connection timed out; no servers could be reached

---

### Post by sanderj on 2013-11-11
There is definitely something with your DNS name resolving. See below what the output should be.

What is your output of "host [www.cisco.com](www.cisco.com) 8.8.8.8"?



```
$ host [www.cisco.com](www.cisco.com)
[www.cisco.com](www.cisco.com) is an alias for [www.cisco.com.akadns.net](www.cisco.com.akadns.net).
[www.cisco.com.akadns.net](www.cisco.com.akadns.net) is an alias for wwwds.cisco.com.edgekey.net.
wwwds.cisco.com.edgekey.net is an alias for wwwds.cisco.com.edgekey.net.globalredir.akadns.net.
wwwds.cisco.com.edgekey.net.globalredir.akadns.net is an alias for e144.dscb.akamaiedge.net.
e144.dscb.akamaiedge.net has address 2.19.208.170
e144.dscb.akamaiedge.net has IPv6 address 2a02:26f0:60:484::90
e144.dscb.akamaiedge.net has IPv6 address 2a02:26f0:60:48b::90
```

---

### Post by russ2 on 2013-11-11
Well interesting problem that I have found.  The modem router that my isp gave me to use does not support IPv6 like in your example.  So they will be delivering a new modem/router this weekend so I will see what happens and get back with you as soon as I can run the test again.

---

### Post by houstonbofh on 2013-11-11
It may also be that you do not have a full or clean DNS feed to that router.  Grab a copy of namebench [http://code.google.com/p/namebench/](http://code.google.com/p/namebench/) and find a good DNS you can use, and have your mail server use that directly.

---

