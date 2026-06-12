---
title: "rsyslog courier debug logging ... how?"
date: 2011-02-21
forum: Server Platforms
---

### Post by tonyofthewoods on 2011-02-21
I am configuring a mail server on lenny (Elastic Host's ready made image). I am working through the fairly well known doc at [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) by Ivar Abrahamsen.

I'm getting authentication issues with courier/authmysql. Ivar suggests turning on debug logging for courier and then adjusting syslog configuration to make sure that the debug logging appears.

Here, however, we have rsyslog - the configuration syntax for which is a little bit mysterious to my untutored eye.

How can I configure rsyslog to output debug logging from courier and where should it appear?

Huge thanks, T.

---

### Post by tonyofthewoods on 2011-02-22
I seem to have got over that stumbling block - needed to restart courier services for log config changes to take effect - as far as I can see.

---

