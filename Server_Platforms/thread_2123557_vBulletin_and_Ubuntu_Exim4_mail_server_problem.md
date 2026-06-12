---
title: "vBulletin and Ubuntu Exim4 mail server problem"
date: 2013-03-08
forum: Server Platforms
---

### Post by ravenseal on 2013-03-08
I have a vBulletin Forum and would like to connect it to my Ubuntu 12.04 Exim4 mail server to use it in order to send emails to members, however, the server is continually refuting my domain's connection whenever I try to send a test message.

> **Warning**[COLOR=#001F30][FONT=verdana]: fsockopen() [[/FONT][/COLOR][function.fsockopen]("http://www.mordorhq.com/admincp/function.fsockopen")[COLOR=#001F30][FONT=verdana]]: unable to connect to tcp://xxx.xxx.xxx.xxx:25 (Connection refused) in [/FONT][/COLOR]**[path]/includes/class_mail.php**[COLOR=#001F30][FONT=verdana] on line [/FONT][/COLOR]**747**

Can anyone give me any ideas as how to how to configure the server properly to accept my domain name/host ip?

I can send out message to my Gmail account, but only through SSH.

Sorry if this a stupid question, but I'm still learning my way around server environments.

---

### Post by ravenseal on 2013-03-08
It says at least 90 people have seen this thread, can anyone at least drop a hint or two? :(

---

### Post by cariboo on 2013-03-09
vBulletin4 (the version we run here) has a builtin email server, wouldn't it be easier to use that instead of exim? BTW, you'll probably get more help on the [vBulletin Forum]("http://www.vbulletin.com/forum/"), than you will here, as it isn't free to use, you have to pay the licensing fee, before you get the source.

---

