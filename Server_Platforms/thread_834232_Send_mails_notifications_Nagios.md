---
title: "Send mails notifications Nagios"
date: 2008-06-19
forum: Server Platforms
---

### Post by klcom on 2008-06-19
Hi, i configured a Nagios system but i want send mails with a other server who have configurated postfix, how i can send this notifications with a external mail server, i can configure smtp in nagios? 

I read a lot of sides, that work with a local mail server and mailx. 

Thanks.

---

### Post by bruski on 2008-06-19
Hi Klcom,

Mate, I think you should be looking at sending the notifications from the server running Nagios and with the new version of Nagios this is quite a bit easier than it used to be.

I have also seen a lot of people use Postfix but I have personally used Sendmail and it is working very well in the end either will do.

There is a lot of research and figuring things out needed to get this working but it is well worth it.

BTW, I dont think you will be able to send mail from another server than that that is running Nagios.

Bruski.

---

### Post by cviniciusm on 2008-06-21
Hello,

Just install Postfix (as local server) on the server that has Nagios, then use the postfix's option "relayhost" to send the e-mail to whatever e-mail server you want. The destination e-mail server must the enable to receive the e-mail relayed.


Regards,
cviniciusm.

---

