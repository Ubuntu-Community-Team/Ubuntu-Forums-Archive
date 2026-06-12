---
title: "null mailer keeps trying to send unknown mail."
date: 2009-08-21
forum: Security
---

### Post by JoBangles on 2009-08-21
Hi, I just discovered nullmailer is trying to send mail as root, repeatedly, as shown in following list from syslog. The mail is being blocked. Is it a virus? I have run the latest ClamAV and ckrootkit with all O.K.
syslog tail:

Aug 21 15:02:30 Hal nullmailer[2967]: Rescanning queue.
Aug 21 15:02:30 Hal nullmailer[2967]: Starting delivery: protocol: smtp host: mail.tpg.com.au file: 1249609179.8173
Aug 21 15:02:31 Hal nullmailer[14126]: smtp: Failed: 550 5.7.1 <root@Hal.Hal>... sender blocked
Aug 21 15:02:31 Hal nullmailer[2967]: Sending failed:  Permanent error in sending the message
Aug 21 15:02:31 Hal nullmailer[2967]: Starting delivery: protocol: smtp host: mail.tpg.com.au file: 1249809083.10658
Aug 21 15:02:33 Hal nullmailer[14128]: smtp: Failed: 550 5.7.1 <root@Hal.Hal>... sender blocked
Aug 21 15:02:33 Hal nullmailer[2967]: Sending failed:  Permanent error in sending the message
Aug 21 15:02:33 Hal nullmailer[2967]: Starting delivery: protocol: smtp host: mail.tpg.com.au file: 1249809124.11351
Aug 21 15:02:35 Hal nullmailer[14129]: smtp: Failed: 550 5.7.1 <root@Hal.Hal>... sender blocked
Aug 21 15:02:35 Hal nullmailer[2967]: Sending failed:  Permanent error in sending the message
Aug 21 15:02:35 Hal nullmailer[2967]: Starting delivery: protocol: smtp host: mail.tpg.com.au file: 1249895601.12516
Aug 21 15:02:37 Hal nullmailer[14130]: smtp: Failed: 550 5.7.1 <root@Hal.Hal>... sender blocked
Aug 21 15:02:37 Hal nullmailer[2967]: Sending failed:  Permanent error in sending the message
Aug 21 15:02:37 Hal nullmailer[2967]: Starting delivery: protocol: smtp host: mail.tpg.com.au file: 1249963860.7302
Aug 21 15:02:38 Hal nullmailer[14131]: smtp: Failed: 550 5.7.1 <root@Hal.Hal>... sender blocked
Aug 21 15:02:38 Hal nullmailer[2967]: Sending failed:  Permanent error in sending the message
Aug 21 15:02:38 Hal nullmailer[2967]: Starting delivery: protocol: smtp host: mail.tpg.com.au file: 1250057568.12306
Aug 21 15:02:40 Hal nullmailer[14132]: smtp: Failed: 550 5.7.1 <root@Hal.Hal>... sender blocked
Aug 21 15:02:40 Hal nullmailer[2967]: Sending failed:  Permanent error in sending the message
Aug 21 15:02:40 Hal nullmailer[2967]: Starting delivery: protocol: smtp host: mail.tpg.com.au file: 1250130303.8153
Aug 21 15:02:42 Hal nullmailer[14133]: smtp: Failed: 550 5.7.1 <root@Hal.Hal>... sender blocked
Aug 21 15:02:42 Hal nullmailer[2967]: Sending failed:  Permanent error in sending the message
Aug 21 15:02:42 Hal nullmailer[2967]: Starting delivery: protocol: smtp host: mail.tpg.com.au file: 1250317469.5246
Aug 21 15:02:44 Hal nullmailer[14134]: smtp: Failed: 550 5.7.1 <root@Hal.Hal>... sender blocked
Aug 21 15:02:44 Hal nullmailer[2967]: Sending failed:  Permanent error in sending the message
Aug 21 15:02:44 Hal nullmailer[2967]: Starting delivery: protocol: smtp host: mail.tpg.com.au file: 1250402009.5476
Aug 21 15:02:45 Hal nullmailer[14135]: smtp: Failed: 550 5.7.1 <root@Hal.Hal>... sender blocked
Aug 21 15:02:45 Hal nullmailer[2967]: Sending failed:  Permanent error in sending the message
Aug 21 15:02:45 Hal nullmailer[2967]: Starting delivery: protocol: smtp host: mail.tpg.com.au file: 1250402051.5986
Aug 21 15:02:47 Hal nullmailer[14136]: smtp: Failed: 550 5.7.1 <root@Hal.Hal>... sender blocked
Aug 21 15:02:47 Hal nullmailer[2967]: Sending failed:  Permanent error in sending the message
Aug 21 15:02:47 Hal nullmailer[2967]: Starting delivery: protocol: smtp host: mail.tpg.com.au file: 1250566931.5989
Aug 21 15:02:49 Hal nullmailer[14137]: smtp: Failed: 550 5.7.1 <root@Hal.Hal>... sender blocked
Aug 21 15:02:49 Hal nullmailer[2967]: Sending failed:  Permanent error in sending the message
Aug 21 15:02:49 Hal nullmailer[2967]: Starting delivery: protocol: smtp host: mail.tpg.com.au file: 1250567056.6522
Aug 21 15:02:51 Hal nullmailer[14138]: smtp: Failed: 550 5.7.1 <root@Hal.Hal>... sender blocked
Aug 21 15:02:51 Hal nullmailer[2967]: Sending failed:  Permanent error in sending the message
Aug 21 15:02:51 Hal nullmailer[2967]: Starting delivery: protocol: smtp host: mail.tpg.com.au file: 1250655264.5811
Aug 21 15:02:52 Hal nullmailer[14139]: smtp: Failed: 550 5.7.1 <root@Hal.Hal>... sender blocked
Aug 21 15:02:52 Hal nullmailer[2967]: Sending failed:  Permanent error in sending the message
Aug 21 15:02:52 Hal nullmailer[2967]: Starting delivery: protocol: smtp host: mail.tpg.com.au file: 1250733166.5602
Aug 21 15:02:54 Hal nullmailer[14140]: smtp: Failed: 550 5.7.1 <root@Hal.Hal>... sender blocked
Aug 21 15:02:54 Hal nullmailer[2967]: Sending failed:  Permanent error in sending the message
Aug 21 15:02:54 Hal nullmailer[2967]: Starting delivery: protocol: smtp host: mail.tpg.com.au file: 1250812406.5790
Aug 21 15:02:56 Hal nullmailer[14141]: smtp: Failed: 550 5.7.1 <root@Hal.Hal>... sender blocked
Aug 21 15:02:56 Hal nullmailer[2967]: Sending failed:  Permanent error in sending the message
Aug 21 15:02:56 Hal nullmailer[2967]: Delivery complete, 15 message(s) remain.

---

### Post by cariboo on 2009-08-21
Are you using a static ip address, or dynamic dns. If you are using dynamic dns, the server you are  trying to send email to is probably doing a reverse lookup and finding an unknown email server

If you are using dynamic dns, have a look at this [article]("http://mark.michaelis.net/Blog/UsingGoogleAsYourDomainsEmailServerWithNoMoreSendOnBehalfOf.aspx")

It explains what is happening, and how to repair the problem.

---

### Post by JoBangles on 2009-08-21
Thanks for your advice, I will now try to sort it out since it is only a configuration problem.

---

### Post by JoBangles on 2009-08-22
Hi cariboo907,
 I have a static IP address and the only solution I came up with was to uninstall null mailer, which fixed the problem. I do not know if this effects the functionality of Ubuntu. Thanks for your help.

---

