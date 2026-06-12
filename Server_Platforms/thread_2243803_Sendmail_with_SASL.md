---
title: "Sendmail with SASL"
date: 2014-09-11
forum: Server Platforms
---

### Post by Jikjik on 2014-09-11
Please excuse my post if it is in a wrong thread. I read a lot of posts here and beyond regarding sendmail + sasl (cyrus). I admit that I am new to both sendmail and ubuntu. 

Here is my situation:
I am able to send email from my ubuntu server to my gmail account using the default settings of sendmail. I can telnet to my mail server on port 25 and can see,

[B]250-AUTH LOGIN
250-STARTTLS[/B]


I want to change the AUTH type to PLAIN LOGIN. So I change my /etc/mail/sendmail.mc with:

```

TRUST_AUTH_MECH(`PLAIN LOGIN')dnl
define(`confAUTH_MECHANISMS', `PLAIN LOGIN')dnl

```

Then I run:

```

m4 sendmail.mc > sendmail.cf
sendmailconfig

```


But the changes I make on sendmail.mc doesn't reflect. I can only change the auth type if I make changes in /usr/lib/sasl2/Sendmail.conf with
```
mech_list: PLAIN LOGIN
```

Any idea how to incorporate the changes in sendmail.mc to my mail server?

---

### Post by slickymaster on 2014-09-11
*Moved to the ***Server Platforms*** sub-forum*

---

