---
title: "Send mail unable to send mail."
date: 2008-07-25
forum: Server Platforms
---

### Post by Alpha01 on 2008-07-25
Hello everyone,


I currently have a Debian Etch server configured and running. I was able to send emails using the mail command. However as of today I'm not able to do so. I tried starting the /etc/init.d/sendmail script but I wasn't able to locate the service script or the config script either. 

I have checked the system to see if it has working email server and was able to connect with out any problems. (telnet 127.0.0.1 25)

Any suggestions why I'm still not able to send emails using the mail command?

Thanks!!

---

### Post by Uluen on 2008-07-25
Well, what does your logs say?

"Not able to do so" isn't very informative ;)
What happens when you try?

---

### Post by Alpha01 on 2008-07-28
> **Uluen said:**
> Well, what does your logs say?

"Not able to do so" isn't very informative ;)
What happens when you try?

Thats the problem my logs are empty. Though I'm not sure why the daemon script(/etc/init.d/sendmail) is not present in the system nor is the sendmail config file.


I appreciate your help.
Thanks!

---

