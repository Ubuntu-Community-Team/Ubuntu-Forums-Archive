---
title: "How 2 get error message for failed SMTP???"
date: 2006-05-31
forum: Server Platforms
---

### Post by henkdeswardt on 2006-05-31
Thank you for everybody that helped me so far.
MY SMTP sending via MX Lookups works very well.

I use the server ONLY for sending e-mail.
How do I get an error message back to an e-mail sender if the e-mail address is incorrect, fo instance.

My configuration:
Windows Server 2003 using Proxy+ for POP and SMTP: IP 192.168.0.150
Linux Server using Postfix for SMTP only: IP 192.168.0.223
ADSL router with static IP Address: (Internal) IP 192.168.0.222
Users: IP 192.168.0.50-149

The user send and received e-mail from the Windows Server.
The windows server relays outside e-mail via SMTP to the Linux server.
The Linux server sends via MX Lookups and SMTP all outgoing e-mail.


Thank you.

Henk de Swardt

---

### Post by garyng on 2006-05-31
set your windows machines relay host(smart host or smtp server depending on how it is called) to the linux box. If you have the right reply-to address setup, failed deliveries should be sent to the right mailbox by the linux SMTP server, even it is say on your ISP. Of course, if the path is broken and the linux box finds no way to do it otherwise, it will be on that linux box usually in the root's mail box.

---

