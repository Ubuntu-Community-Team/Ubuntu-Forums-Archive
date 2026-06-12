---
title: "Prevent Email from leaving local Domain"
date: 2013-10-24
forum: Server Platforms
---

### Post by lingpanda on 2013-10-24
I'm using Squirrelmail + Dovecot + SMTP and would like to prevent users from sending email to outside domains(ie. yahoo, gmail etc). I want to lock it down so only inter-office email is allowed to and from. Can someone start me in the right direction? Thanks.

---

### Post by SeijiSensei on 2013-10-24
A simple hard-and-fast approach is to block outbound traffic on port 25, SMTP. On the mail server add this pair of rules:
```

/sbin/iptables -A OUTPUT -i lo -p tcp --dport 25 -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp --dport 25 -j REJECT

```
The first allows traffic over the "localhost" interface, which your setup would be using to communicate between Squirrelmail and the local mail transfer agent (Postfix, sendmail, exim).  Mail to any other server is blocked.

---

### Post by lingpanda on 2013-10-25
> **SeijiSensei said:**
> A simple hard-and-fast approach is to block outbound traffic on port 25, SMTP. On the mail server add this pair of rules:
```

/sbin/iptables -A OUTPUT -i lo -p tcp --dport 25 -j ACCEPT
/sbin/iptables -A OUTPUT -p tcp --dport 25 -j REJECT

```
The first allows traffic over the "localhost" interface, which your setup would be using to communicate between Squirrelmail and the local mail transfer agent (Postfix, sendmail, exim).  Mail to any other server is blocked.

I receive the following error.
```

 # iptables -A OUTPUT -i lo -p tcp --dport 25 -j ACCEPT
iptables v1.4.12: Can't use -i with OUTPUT
```

---

### Post by SeijiSensei on 2013-10-26
Sorry, I mostly use INPUT rules.  Replace "-i" with "-o" since the rule appllies to traffic leaving the interface.

---

### Post by lingpanda on 2013-11-01
> **SeijiSensei said:**
> Sorry, I mostly use INPUT rules.  Replace "-i" with "-o" since the rule appllies to traffic leaving the interface.

Thanks but for whatever reason mail was still leaving the domain. I did find a fix I believe. I edited my Postfix main.cf file 
```
[relayhost]("http://www.postfix.org/postconf.5.html#relayhost") = $[mydomain]("http://www.postfix.org/postconf.5.html#mydomain")
``` 

It variables are

/etc/postfix/[main.cf]("http://www.postfix.org/postconf.5.html"):
    [relayhost]("http://www.postfix.org/postconf.5.html#relayhost") =                   (default: direct delivery to Internet)
    [relayhost]("http://www.postfix.org/postconf.5.html#relayhost") = $[mydomain]("http://www.postfix.org/postconf.5.html#mydomain")         (deliver via local mailhub)
    [relayhost]("http://www.postfix.org/postconf.5.html#relayhost") = [mail.$[mydomain]("http://www.postfix.org/postconf.5.html#mydomain")]  (deliver via local mailhub)
    [relayhost]("http://www.postfix.org/postconf.5.html#relayhost") = [mail.isp.tld]    (deliver via provider mailhub)


This prevents my mail from leaving the domain. However my Mail Queue fills up if mail is undeliverable. No bounce message to the sender.

---

