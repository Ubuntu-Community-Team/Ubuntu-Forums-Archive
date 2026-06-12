---
title: "Postfix mail server."
date: 2010-05-06
forum: Server Platforms
---

### Post by hockey97 on 2010-05-06
Hi, I am trying to run my own mail server. I have followed a online guide to doing this but so far the mail server dosen't work and the logs dosen't help much. It just shows some root area has permission issues.


This is the guide I followed.
[http://flurdy.com/docs/postfix/#config-simple-imap](http://flurdy.com/docs/postfix/#config-simple-imap)

I skipped the first requirement which was to install a firewall.

I just installed postfix and Courier IMAP. That's the only ones I followed in the guide.

Was how to install postfix and config it and same with Courier and also mysql.

after those I tested using telnet to see if my mail server is good.

So far I connected to localhost 25  but when I do the helo I get not response.

is there anything I am missing?

I have followed the guide exactly. The same names etc.

would like to know why when I typed helo or ehlo with the mail server name that I get no response. 

Is there a command that I can find out the mail server name?

---

### Post by Black_Prince on 2010-05-06
Mail server name is actualy name of server you are connected to (In your case **localhost**)

Did you tried doing

```
ehlo localhost
```after connecting to your mail server?

---

### Post by hockey97 on 2010-05-18
yes, I have tried it and I get no response.


I looked at my local library online catolog and they have a book called UBUNTU LINUX BIBLE   which shows how to setup your mail server.

Do you think I should read it? It was published in 2007. I am thinking they don't cover using mysql with postfix.

---

### Post by noway2 on 2010-05-18
Try using netcat and see if anything is even listening on port 25, which would be your SMTP server.  If it is listening, you should be able to connect via localhost regardless of any sort of firewall.

It sounds like Postfix may not actually be running.  You should try to restart it (code: sudo /etc/init.d/postfix restart) and watch for any error messages.  Then look in your syslog, mail logs, and daemon log for any associated error messages.

---

### Post by mbehamin on 2010-05-19
Hi
try [http://blog.mehdibehamin.com/?p=80](http://blog.mehdibehamin.com/?p=80) 
regards

---

