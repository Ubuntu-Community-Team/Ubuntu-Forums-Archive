---
title: "Make Postfix Listen to Outside Connections"
date: 2005-01-11
forum: Server Platforms
---

### Post by Jæd on 2005-01-11
Hi,

How can I make postfix listen to connections to accpt mail? I've tried using "inet_interfaces = all" but to explicity listen for outside mail but if I try and telnet to port 25 my connection is refused.

(The box is behind a firewall but 25 is forwarded to the box... I managed to get this working on Redhat previously...)

---

### Post by wallijonn on 2005-01-11
what does /var/log/mail.err, mail.log, mail.warn, mail.info say?

---

### Post by Jæd on 2005-01-11
When I do:

telnet excession.org.uk 25

I get nothing, but the computer is available as I can ping it and log in ok. If I do "telnet 127.0.0.1 25" I can get a response from postfix. I'm not sure what to change to get it to respond to the outside world.

Oh, and after each config change I restarted postfix... Is there something else to do?

---

### Post by ra1 on 2005-01-11
By default postfix listens only on localhost. You should look at /etc/postfix/master.cf

---

### Post by wallijonn on 2005-01-11
you may also have to issue [COLOR=Red]postfix newaliases[/COLOR] . For some reason my Postfix didn't like IPv6.

---

### Post by Jæd on 2005-01-11
[QUOTE=ra1]By default postfix listens only on localhost. You should look at /etc/postfix/master.cf[/QUOTE]

Ok... From reading the comments I'm guessting that the line starting submission should be uncommented. (Smtpd  takes the output from this and queues it?)

After restarting postfix there is no change... What is a good resource for understanding this files contents? I didn't get as much time today to deal with this as I would have liked.  :cry:

---

### Post by ra1 on 2005-01-11
You need to change ```
127.0.0.1:smtp inet n -	 -	 -	 -	 smtpd
``` to ```
smtp inet n -	 -	 -	 -	 smtpd
``` this way postfix will listen on all interfaces. You should read [documentation]("http://www.postfix.org/documentation.html").

---

### Post by Jæd on 2005-01-12
Thanks! This did the trick!

---

### Post by ra1 on 2005-01-12
You're welcome.

---

