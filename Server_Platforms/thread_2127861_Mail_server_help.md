---
title: "Mail server help"
date: 2013-03-21
forum: Server Platforms
---

### Post by joker535 on 2013-03-21
Disregard. I decided to scrap the ubuntu mail server idea. It was too much of a pain in the ass.

---

### Post by SeijiSensei on 2013-03-21
Are you sure your ISP allows outbound traffic to port 25?  Many block this to thwart spambots running on their customers' malware-infected computers.

If you run "telnet aspmx.l.google.com 25" can you connect?

---

### Post by joker535 on 2013-03-21
The server is co-located and no ports are blocked by the ISP. it is running on the same connection (different IP in the same range) as the windows mail server which works fine. Telnet to google works fine.

user1@mail:/var/log$ telnet aspmx.l.google.com 25
Trying 173.194.73.26...
Connected to aspmx.l.google.com.
Escape character is '^]'.
220 mx.google.com ESMTP b1si25913661vdk.5 - gsmtp

There are no errors in any of the logs that I can find in /var/logs. I can generate mail from the command line, evolution client, or via webmail and the messages just sit in the queue. The resolv file is identical to the system one and all mail related services are running and restart with no errors.

---

### Post by joker535 on 2013-03-21
**I noticed something in the log after sending a test message using my evolution client (see the bold item)**

Mar 21 11:25:01 mail pop3d: Connection, ip=[::1]
Mar 21 11:25:01 mail pop3d: Disconnected, ip=[::1]
Mar 21 11:25:01 mail imapd: Connection, ip=[::1]
Mar 21 11:25:01 mail imapd: Disconnected, ip=[::1], time=0
Mar 21 11:25:01 mail postfix/smtpd[4942]: connect from localhost[127.0.0.1]
Mar 21 11:25:01 mail postfix/smtpd[4942]: lost connection after CONNECT from localhost[127.0.0.1]
Mar 21 11:25:01 mail postfix/smtpd[4942]: disconnect from localhost[127.0.0.1]
Mar 21 11:25:33 mail pop3d: Connection, ip=[::ffff:xxx.xxx.xxx.xxx]
Mar 21 11:25:34 mail pop3d: LOGIN, user=user1@mydomainname.com, ip=[::ffff:xxx.xxx.xxx.xxx], port=[3200]
Mar 21 11:25:34 mail pop3d: LOGOUT, user=user1@mydomainname.com, ip=[::ffff:xxx.xxx.xxx.xxx], port=[3200], top=0, retr=0, rcvd=24, sent=96, time=0, stls=1
Mar 21 11:25:53 mail postfix/smtpd[4942]: warning: xxx.xxx.xxx.xxx: hostname xxx-xxx-xxx-xxx-my isp verification failed: Name or service not known
Mar 21 11:25:53 mail postfix/smtpd[4942]: connect from unknown[xxx.xxx.xxx.xxx]
Mar 21 11:25:54 mail postfix/smtpd[4942]: 0D1303611AA: client=unknown[xxx.xxx.xxx.xxx], sasl_method=LOGIN, sasl_username=user1@mydomainname.com
Mar 21 11:25:54 mail postfix/cleanup[4964]: 0D1303611AA: **hold:** header Received: from [192.168.0.225] (unknown [xxx.xxx.xxx.xxx])??(Authenticated sender: [email]user1@mydomainname.com[/email])??by mail.mydomainname.com (Postfix) with ESMTPA id 0D1303611AA??for <user2@myisp.net>; T from unknown[xxx.xxx.xxx.xxx]; from=<user1@mydomainname.com> to=<user2@myisp.net> proto=ESMTP helo=<[192.168.0.225]>
Mar 21 11:25:54 mail postfix/cleanup[4964]: 0D1303611AA: message-id=<1363879552.4037.0.camel@sysadmin.local>
Mar 21 11:25:54 mail postfix/smtpd[4942]: disconnect from unknown[xxx.xxx.xxx.xxx]

**I see the word hold right before header received. Is that responsible for all of my messages sitting in the queue? If so what would cause that?**

---

### Post by joker535 on 2013-03-21
I set up a second domain on the server and added a test address. I made sure all the DNS records were set up and tested it with mxtoolbox.com with all positive results. I went and sent an inbound message to the test address in the new domain from my gmail account. The message was accepted by the server and is now sitting in the queue with all of my outbound test messages. Apparently the queue is accepting inbound messages from external sources and outbound messages from webmail and clients but the queue just never processes. 

Any ideas?

---

