---
title: "Postfix email server for Nagios"
date: 2011-01-27
forum: Server Platforms
---

### Post by KLStringer on 2011-01-27
I have a Nagios server set up at work and need to configure postfix to log into a gmail account and send out SMS alerts from Nagios. I had Nagios sending out the alerts directly and the IP it was using got blacklisted so we stopped the SMS alerts until I had time to get it set up correctly.

I've found a couple tut's about sending or relaying Postfix mail through gmail but not sure if their a comprehensive how-to as I've never set up a mail server before. I've linked the two that I've found below but figured I'd also ask for help as I worked my way through them. Thanks in advance for any help with getting this setup its much appreciated.


[http://ubuntu-tutorials.com/2008/11/11/relaying-postfix-smtp-via-smtpgmailcom/](http://ubuntu-tutorials.com/2008/11/11/relaying-postfix-smtp-via-smtpgmailcom/)

[http://www.marksanborn.net/linux/send-mail-postfix-through-gmails-smtp-on-a-ubuntu-lts-server/](http://www.marksanborn.net/linux/send-mail-postfix-through-gmails-smtp-on-a-ubuntu-lts-server/)

---

### Post by KLStringer on 2011-01-27
Following the steps in the 2nd link when I get to step 2 and enter in the command 

```
openssl req -new -nodes -subj  '/CN=domain.com/O=Sanborn_Widgets/C=US/ST=New York/L=New  York/emailAddress=username@gmail.com' -keyout FOO-key.pem -out  FOO-req.pem -days 3650
```

I get an error message
```
 openssl:Error" '-new' is an invalid command.
```

not sure what to do from there

---

### Post by KLStringer on 2011-01-27
Found the problem I missed part of the command and fat fingered another.:P

---

