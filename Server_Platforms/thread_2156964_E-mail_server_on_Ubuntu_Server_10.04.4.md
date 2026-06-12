---
title: "E-mail server on Ubuntu Server 10.04.4"
date: 2013-06-23
forum: Server Platforms
---

### Post by DevonD on 2013-06-23
Hello all. I am quite new to Ubuntu Server and e-mail servers. I am looking to set up a POP3 and SMTP server on my Ubuntu 10.04.4 32-Bit server. I have a domain registered, let's pretend it is testdomain.com, and I have an A record for testdomain.com set to my public IP address. I also have a MX record for testdomain.com set to testdomain.com, and I have port 25 and 110 open on my router. I want to have a few e-mail addresses, such as [EMAIL="bob@testdomain.com"]bob@testdomain.com[/EMAIL], [EMAIL="joe@testdomain.com"]joe@testdomain.com[/EMAIL], and [EMAIL="bill@testdomain.com"]bill@testdomain.com[/EMAIL]. I want to have an e-mail client, such as Thunderbird, on a remote computer receive and send e-mails using these addresses. I don't want to make home directories for each e-mail address, if this is possible. I tried to install Postfix and Dovecot, but the configuration seems complex. Could someone please give me step-by-step detailed instructions as to how to set up the e-mail server, e-mail addresses, and anything else which is required? Any help will be much appreciated.

---

### Post by CharlesA on 2013-06-23
Check this out:
[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

---

### Post by DevonD on 2013-06-30
Thank you very much CharlesA. That link was very helpful, and Postfix and Dovecot are now working.

---

