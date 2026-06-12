---
title: "Interpreting OSSEC warning"
date: 2010-03-05
forum: Security
---

### Post by pytheas22 on 2010-03-05
OSSEC gave me this warning (I've obfuscated the hostname and IP address):

```
Received From: (hostname) xxx.xxx.xx.xx->/var/log/apache2/access.log
Rule: 31106 fired (level 12) -> "A web attack returned code 200 (success)."
Portion of the log(s):

66.71.245.177 - - [05/Mar/2010:22:10:56 -0500] "GET /?C=../../../../../../../../../../../../../../../etc/passwd%00 HTTP/1.1" 200 738 "-" "-"
```

From what I can tell, this suggests that someone was able to wget the /etc/passwd file, but I'm not entirely sure if that's true or where to go from here.  If anyone could offer any tips on what this means or how to go about investigating this issue further, I'd be really grateful.

The machine in question runs Ubuntu 8.04.

---

### Post by bodhi.zazen on 2010-03-06
> **pytheas22 said:**
> OSSEC gave me this warning (I've obfuscated the hostname and IP address):

```
Received From: (hostname) xxx.xxx.xx.xx->/var/log/apache2/access.log
Rule: 31106 fired (level 12) -> "A web attack returned code 200 (success)."
Portion of the log(s):

66.71.245.177 - - [05/Mar/2010:22:10:56 -0500] "GET /?C=../../../../../../../../../../../../../../../etc/passwd%00 HTTP/1.1" 200 738 "-" "-"
```From what I can tell, this suggests that someone was able to wget the /etc/passwd file, but I'm not entirely sure if that's true or where to go from here.  If anyone could offer any tips on what this means or how to go about investigating this issue further, I'd be really grateful.

The machine in question runs Ubuntu 8.04.

I agree. You can test this yourself by putting that code in your browser.

I assume some part of your server is "misconfigured" to allow such a request. Are you running php ? You need to secure your code or use mod_security.

[http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/](http://blog.bodhizazen.net/linux/how-to-mod_security-ubuntu-904/)

At a minimum I would change passwords. Make sure you do not have ssh with password authentication !!!

---

### Post by The Cog on 2010-03-06
I just tried that URL on an apache here, and it returned success. But note that all the ../../ stuff is after "?C=", meaning that the path to etc/passwd is all just argument. On my apache, although the request is succesful, it just returns the root document, same as when I do "GET /". 

Try it for yourself of course, but it doesn't automatically mean they actually got your passwd file.

---

### Post by bodhi.zazen on 2010-03-06
> **The Cog said:**
> I just tried that URL on an apache here, and it returned success. But note that all the ../../ stuff is after "?C=", meaning that the path to etc/passwd is all just argument. On my apache, although the request is succesful, it just returns the root document, same as when I do "GET /". 

Try it for yourself of course, but it doesn't automatically mean they actually got your passwd file.


Good point, I did not interpret the Apache code correctly, and get the same response on a test server.

It does depend on how the server is configured, and the OP should certainly test.

---

### Post by pytheas22 on 2010-03-07
Thanks to both of you for your helpful responses.  It makes sense now that ?C=anything_you_want will return a success code, and that they didn't get the passwd file.  On the other hand, I'm still curious as to what exactly they were trying to do.

So it's good to know that they didn't get access to any sensitive information, but I will probably come up with a mod_rewrite rule to prevent this from happening again, just in case.

---

