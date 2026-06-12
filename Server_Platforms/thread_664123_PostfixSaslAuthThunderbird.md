---
title: "Postfix/Sasl/Auth/Thunderbird"
date: 2008-01-10
forum: Server Platforms
---

### Post by jlbprof on 2008-01-10
I am trying to do something simple and have been unable to do it.

I want to have postfix with TLS, SMTP_AUTH using PAM and the Thunderbird email client.   This should be a cake walk, but I cannot get it to work.

I followed this article: 

[https://help.ubuntu.com/community/Postfix]("https://help.ubuntu.com/community/Postfix")

When I do a telnet 25 this is what I get:

```

root@website6:/var/log# telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 smtp.jlbprof.com ESMTP SMTP SERVER
ehlo localhost
250-smtp.jlbprof.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

```

As you can see I have AUTH listed, but notice that neither CRAM nor DIGEST nor NTLM are in there or any of the advanced AUTHing are there.

I think that is what is causing my problems.  If I set Thunderbird up to use a name and password it will not connect.  If I tell it to not use a name and password it works fine.

Looking at the syslog indicates to me Thunderbird never asks to login it just disconnects.

Here is a section of the postfix log.

```

Jan 10 20:06:33 website6 postfix/smtpd[12002]: < localhost[127.0.0.1]: EHLO [127.0.0.1]
Jan 10 20:06:33 website6 postfix/smtpd[12002]: > localhost[127.0.0.1]: 250-smtp.jlbprof.com
Jan 10 20:06:33 website6 postfix/smtpd[12002]: > localhost[127.0.0.1]: 250-PIPELINING
Jan 10 20:06:33 website6 postfix/smtpd[12002]: > localhost[127.0.0.1]: 250-SIZE 10240000
Jan 10 20:06:33 website6 postfix/smtpd[12002]: > localhost[127.0.0.1]: 250-VRFY
Jan 10 20:06:33 website6 postfix/smtpd[12002]: > localhost[127.0.0.1]: 250-ETRN
Jan 10 20:06:33 website6 postfix/smtpd[12002]: > localhost[127.0.0.1]: 250-AUTH LOGIN PLAIN
Jan 10 20:06:33 website6 postfix/smtpd[12002]: match_list_match: localhost: no match
Jan 10 20:06:33 website6 postfix/smtpd[12002]: match_list_match: 127.0.0.1: no match
Jan 10 20:06:33 website6 postfix/smtpd[12002]: > localhost[127.0.0.1]: 250-AUTH=LOGIN PLAIN
Jan 10 20:06:33 website6 postfix/smtpd[12002]: > localhost[127.0.0.1]: 250-ENHANCEDSTATUSCODES
Jan 10 20:06:33 website6 postfix/smtpd[12002]: > localhost[127.0.0.1]: 250-8BITMIME
Jan 10 20:06:33 website6 postfix/smtpd[12002]: > localhost[127.0.0.1]: 250 DSN
Jan 10 20:06:33 website6 postfix/smtpd[12002]: watchdog_pat: 0x808e280
Jan 10 20:06:33 website6 postfix/smtpd[12002]: vstream_fflush_some: fd 15 flush 169
Jan 10 20:06:33 website6 postfix/smtpd[12002]: vstream_buf_get_ready: fd 15 got 6
Jan 10 20:06:33 website6 postfix/smtpd[12002]: < localhost[127.0.0.1]: QUIT
Jan 10 20:06:33 website6 postfix/smtpd[12002]: > localhost[127.0.0.1]: 221 2.0.0 Bye
Jan 10 20:06:33 website6 postfix/smtpd[12002]: vstream_fflush_some: fd 15 flush 15
Jan 10 20:06:34 website6 postfix/smtpd[12002]: match_hostname: localhost ~? 127.0.0.0/8
Jan 10 20:06:34 website6 postfix/smtpd[12002]: match_hostaddr: 127.0.0.1 ~? 127.0.0.0/8
Jan 10 20:06:34 website6 postfix/smtpd[12002]: vstream_fflush_some: fd 15 flush 0
Jan 10 20:06:34 website6 postfix/smtpd[12002]: disconnect from localhost[127.0.0.1]                                                                                 

```

I have been trying to get this to work for 2 weeks now, and this is the 2nd Linux I have installed to try and get this to work.

Can anyone help me?

Thanx

Julian

---

