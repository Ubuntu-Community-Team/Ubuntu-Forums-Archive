---
title: "Squid 3.5+ - How to Spoof SSL User Agent"
date: 2017-02-06
forum: Server Platforms
---

### Post by xdracco on 2017-02-06
Successfully able to spoof my user agent when the request is unencrypted over http. I've been trying, unsuccessfully, to spoof my user agent with encrypted requests over https.


For the record, my Squid installation is also intercepting and filtering all SSL traffic.


Any ideas on how to spoof user agents on encrypted traffic? Is it possible to modify user agent on encrypted traffic?


Thanks in advance

---

### Post by xdracco on 2017-02-09
the solution is,,,,,,,,,,,, >>

unless you have a CA issued from a root authority, use:

```
ssl_bump splice all
```

not 

```
ssl_bump bump all
```

From squid docs:

> ##
##    **splice**
##    Become a TCP tunnel without decrypting proxied traffic.
##    This is the default action.
##
##    **bump**
##    Establish a secure connection with the server and, using a
##    mimicked server certificate, with the client.
##

---

