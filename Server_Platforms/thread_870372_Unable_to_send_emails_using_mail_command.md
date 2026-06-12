---
title: "Unable to send emails using mail command"
date: 2008-07-25
forum: Server Platforms
---

### Post by Alpha01 on 2008-07-25
Hello everyone,


I currently have a Debian Etch server configured and running. I was able to send emails using the mail command before. However as of today I'm not able to do so. I tried starting the /etc/init.d/sendmail script but I wasn't able to locate the service script or the config script either. 

I have checked the system to see if it has working email server and was able to connect with out any problems. (telnet 127.0.0.1 25)

Any suggestions why I'm still not able to send emails using the mail command?

Thanks!!

---

### Post by RealPSL on 2008-07-27
See if you can trace the source of the problem with 

```
sendmail -v user@example.com
```

Enter your test message and on a newline submit a "." and you will see the process it takes to send the message. Hopefully it will provide some insight into why your mail is no longer working.

---

