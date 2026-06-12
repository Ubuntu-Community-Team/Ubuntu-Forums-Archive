---
title: "Postfix prefixing  prefixing name"
date: 2012-07-03
forum: Server Platforms
---

### Post by Bob Fletcher on 2012-07-03
Sorry if this is so basic, I have just installed 12.04 server.

I have configured postfix to use mydomain.net given SMTP as mail.mydomain.net.

My server box is called the-dragon. The problem is postfix is sending mail out as [email]user@the-dragon.mydomain.net[/email] this is not in the /etc/postfix/main.cf file so I don't know where it is getting it from. I just want [email]user@mydomain.net[/email]

Can you help me

Robert...

---

### Post by kennethconn on 2012-07-03
[http://www.postfix.org/BASIC_CONFIGURATION_README.html#myorigin](http://www.postfix.org/BASIC_CONFIGURATION_README.html#myorigin)

---

### Post by Bob Fletcher on 2012-07-04
> **kennethconn said:**
> [http://www.postfix.org/BASIC_CONFIGURATION_README.html#myorigin](http://www.postfix.org/BASIC_CONFIGURATION_README.html#myorigin)

Thanks for the link and I have spent a long time going through it. Basically my /etc/postfix/main.cf seems correct except that in the link you gave me "myorigin = $myhostname" was using "myorigin = /etc/mailname" I tried changing that but made no difference.

It's getting very stressful for a newbie. Can someone give me a sample main.cf file that will work. I have my own domain and all I want to do is to send and receive mail on my own server through the Internet.

Alternatively is there a mail server that is easier to set up than postfix. At this stage I am not worries about TLS I just need it to work.

Robert...

---

### Post by kennethconn on 2012-07-04
If you are able to send and receive email from external to internal (and vice versa), which you seem to indicate that you are, then that really is the tough part done, so stick with it.
 
Post your main.cf file here and people should be able to spot any issues. What you want to do is common, so it should be something trivial if it's not working as expected (I have not looked at this in a while so I'm a bit rusty).

---

