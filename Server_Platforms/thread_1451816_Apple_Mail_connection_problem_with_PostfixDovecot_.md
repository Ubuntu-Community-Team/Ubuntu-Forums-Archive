---
title: "Apple Mail connection problem with Postfix/Dovecot setup"
date: 2010-04-11
forum: Server Platforms
---

### Post by CCG121 on 2010-04-11
[FONT=monospace]I setup my mail system on a clean install of Postfix and Dovecot from
[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

on the: 
[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto#Testing%20Your%20Setup](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto#Testing%20Your%20Setup) part everything checks out yet when i input the details into Apple Mail it tells me That it Can't connect.

I can Connect via Squirrelmail and telnet but not through mail.
also my [/FONT]/var/log/mail.log s not recording anything and my mail.log.1 only goes up to april 6

---

### Post by Skidbladnir on 2010-04-11
This is stupid, but, have you set up port forwarding?  I know that TWC also refuses to let mail servers receive mail unless they have proper PTR records.

---

### Post by CCG121 on 2010-04-11
Yes ports 110,143, and 25 are all forwarded to the server.

---

