---
title: "POSTFIX: Message body with &lt;CRLF&gt;.&lt;CRLF&gt; truncates mail"
date: 2010-12-30
forum: Server Platforms
---

### Post by erkant on 2010-12-30
Platform = **Ubuntu 10.04.1 LTS x64**
Postfix Version = **2.7.0**

Recently, I have replaced my old FreeBSD/Postfix machine with a new Ubuntu/Postfix installation with the same config file to take over the relay function to our Exchange Server. Everything was working very well so far except for one thing.

If a sender sends an email which has **<CRLF>.<CRLF>** in the message body (DATA) then Ubuntu thinks it's the end of message (truncates email) and stops communication with Exchange and starts relaying to upstream SMTP server (truncated message).

If I send the very same message through old FreeBSD/Postfix installation, message is sent fully with no truncating...

Do you know any relevant information or a workaround regarding this issue?

Thanks for your helps in advance...
CET

---

