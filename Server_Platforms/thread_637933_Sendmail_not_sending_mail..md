---
title: "Sendmail not sending mail."
date: 2007-12-11
forum: Server Platforms
---

### Post by M374llic4 on 2007-12-11
I have tried near all configurations and such as I can think of but no luck after 2 days. I only need sendmail to send messages from websites through php. It does not need to receive any messages, as we have a separate mail server. 

Maybe I am missing something with the DNS server or something, but I keep getting  

Dec 11 14:43:03 itsweb1 sendmail[21651]: lBBJh3r6021651: from=its@itstechsupport.com, size=457, class=0, nrcpts=1, msgid=<1197402183.21649@itstechsupport.com>, relay=root@localhost
Dec 11 14:43:03 itsweb1 sendmail[21651]: lBBJh3r6021651: to=dantermani@yahoo.com, ctladdr=its@itstechsupport.com (1000/1000), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30457, relay=[127.0.0.1] [127.0.0.1], dsn=4.0.0, stat=Deferred: Connection refused by [127.0.0.1]


If anyone has some help, I would really appreciate it!

Thanks,
Dan

---

### Post by HermanAB on 2007-12-11
Hmm well, unless you are a masochist, it would be better to use Postfix.  It is less problematic than Sendmail.  With Sendmail, you are on your own. One look at the Sendmail configuration file is enough to make anyone of sound mind run away screaming...

BTW, it sounds like all you need is nullmailer: [http://untroubled.org/nullmailer/](http://untroubled.org/nullmailer/) which will take about 10 seconds to set up.

---

### Post by adamonduty on 2007-12-11
If you want to be awed by the power of SSH, you could always do this:

[http://www.debian-administration.org/articles/487](http://www.debian-administration.org/articles/487)

---

### Post by M374llic4 on 2007-12-12
I would prefer to use postfix as it is one of the installed and included programs that works with webmin and virtualmin.

 Only problem is, when I try to refresh webmin check, it says "No virtual domains file was found in your posfix configuration. Maybe no virtual domain map has been defined"

I go to create a new mapping, but am lost at that point.

It wants Description
Name
Map to. 
If i put anything in it says No map file defined.

---

### Post by HermanAB on 2007-12-12
Well, we have given you the two simplest solutions on the planet: Nullmailer and SSH port forwarding.

"You can lead a horse to the water, but you cannot prevent him from drowning himself while going after the carrot painted on the bottom of the trough..."
;)

H.

---

