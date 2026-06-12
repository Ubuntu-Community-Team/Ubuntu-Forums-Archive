---
title: "To check mail server for virus"
date: 2007-11-07
forum: Server Platforms
---

### Post by satimis on 2007-11-07
Hi folks,


Ubuntu 7.04 server amd64
Postfix 2.3.8


I'm following; 

Test ClamSMTP for incoming Mail from the Internet
[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

However the test on sending harmless test mails is not availble on;
[http://www.webmail.us/email-traffic](http://www.webmail.us/email-traffic)

Please advise are there similar sites, other than "http://www.gfi.com/emailsecuritytest/", can be hooked for such test.  TIA


B.R.
satimis

---

### Post by Wallace on 2007-11-07
Can you just download a copy of the EICAR Test File and then try emailing it to yourself?

[http://www.eicar.org/anti_virus_test_file.htm](http://www.eicar.org/anti_virus_test_file.htm)

---

### Post by satimis on 2007-11-07
> **Wallace said:**
> Can you just download a copy of the EICAR Test File and then try emailing it to yourself?

[http://www.eicar.org/anti_virus_test_file.htm](http://www.eicar.org/anti_virus_test_file.htm)
Hi Wallace,


I can download the file on a workstation and email it to the server via Internet.  Can it work?  I have only one broadband.  OR email it on Intranet via router?


satimis

---

### Post by Wallace on 2007-11-07
You'll need to email it through the email server you're trying to test. If I download the eicar.com file then email it to myself, my mail server (Postfix running with ClamAV) picks it up as a virus. The email didn't leave my network though.

```
A virus was found: Eicar-Test-Signature

Scanner detecting a virus: ClamAV-clamd
```

---

