---
title: "OSSEC &quot;Common web attack&quot;"
date: 2012-08-26
forum: Security
---

### Post by Stonecold1995 on 2012-08-26
I'm using OSSEC with the web UI, and the logs keep getting the a message saying "Common web attack" with a level 6 severity.  However, the source is localhost.

```
**2012 Aug 26 19:14:27** Rule Id: [COLOR="Red"]31104[/COLOR] level: 6
**Location:** kubuntu->/var/log/apache2/access.log
**Src IP:** 127.0.0.1
**Common web attack.**
```
Why is OSSEC under the impression that my computer is attacking itself?  I looked at /var/log/apache2/access.log and it looks like [this]("http://www.pictureshack.us/images/64994_log1.png").  That makes sense because I have Apache set to disallow all incoming data except that from 127.0.0.1 (I'm not running a web site so the rest is disabled for security), but it doesn't explain why OSSEC believes this is an attack.  I know I don't have to worry about my computer getting attacked through Apache like this, so is there a way for me to make OSSEC ignore things like that?  I don't know how to set custom rules and the documentation is kind of confusing...

---

### Post by Stonecold1995 on 2012-09-01
bump

---

### Post by bodhi.zazen on 2012-09-02
It is almost certainly a false positive. You should file a bug with OSSEC.

---

