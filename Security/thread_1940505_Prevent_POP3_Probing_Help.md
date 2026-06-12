---
title: "Prevent POP3 Probing Help"
date: 2012-03-13
forum: Security
---

### Post by own3mall on 2012-03-13
Hi Everyone,

I noticed today that my server was being flooded via POP3 attempted logins from a Chinese IP address.  I have since blocked that IP Address in my iptables from even connecting to my machine.  However, is there a way to limit the number of attempted logins?

I found this while searching:

[http://serverfault.com/questions/247744/fail2ban-stop-pop3-login-attempts](http://serverfault.com/questions/247744/fail2ban-stop-pop3-login-attempts)

As taken from the link above, would this code fix my problem?

```

iptables -A INPUT -p tcp --dport 110 -m state --state NEW -m recent --name pop --rsource --update --seconds 60 --hitcount 5 -j DROP iptables -A INPUT -p tcp --dport 110 -m state --state NEW -m recent --name pop --rsource --set -j ACCEPT
```Is there a better way to limit login attempts for POP3 and other related services?

---

### Post by own3mall on 2012-03-14
Anyone know?

---

### Post by wacky_sung on 2012-03-15
Are you running a mail server?

---

### Post by own3mall on 2012-03-15
> **wacky_sung said:**
> Are you running a mail server?

Yes, I'm running a mail server.

---

### Post by HermanAB on 2012-03-18
Simple really.  Don't use POP3 or IMAP.  Rather use POP3S and IMAPS.

And add this to your firewall rules:
# General new connection rate limiting for DOS and Brute Force protection
iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

---

