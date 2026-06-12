---
title: "Help diagnosing postfix hack"
date: 2014-03-19
forum: Security
---

### Post by kuba-g on 2014-03-19
Hi,

I think that my postfix installation has been hacked. My df -h shows that rootfs is used in 100%:
```

rootfs                 9,2G  8,7G   39M 100% /

```

and I am constantly receiving emails like this:
Email title: Postfix SMTP server: errors from 118-168-105-197.dynamic.hinet.net[118.168.105.197]
```

Out: 220 mydomain.example.pl ESMTP Postfix (Debian/GNU)
 In:  HELO 41.22.209.91
 Out: 250 mydomain.example.pl
 In:  MAIL FROM: <tbdzcpiqpktsze@yahoo.com>
 Out: 250 2.1.0 Ok
 In:  RCPT TO: <larry55662000@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <kang168168@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <juice2267@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <owenfrp@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <malinyi@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <jijd@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <k0918933@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <hurenling@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <kenchloe@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <joanna2890@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <mage0329@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <lee480506@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <ready0114@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <jmmr@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <orrira@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <mau_maukuo@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <onlykinki0410@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <k8a0r1r5y@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <k123363@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <ken112717@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <lingpiecesjj@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <lcabc1@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <lechiche@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <nslx@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  RCPT TO: <no92@yahoo.com.tw>
 Out: 250 2.1.5 Ok
 In:  DATA
 Out: 354 End data with <CR><LF>.<CR><LF>
 Out: 250 2.0.0 Ok: queued as 7897350311
 In:  RSET
 Out: 250 2.0.0 Ok
 In:  MAIL FROM: <zcwctmwuey@yahoo.com>
 Out: 452 4.3.1 Insufficient system storage
 Out: 421 4.7.0 mydomain.example.pl Error: too many errors

Session aborted, reason: too many errors

For other details, see the local mail logfile

```
(domain name and IP are fake in above example, except title).

Could someone help me in diagnosing this problem?

Thanks in advance!

---

### Post by lisati on 2014-03-19
It almost looks like someone is trying to use your server as a relay.

The IP address 118.168.105.197 appears to be listed in a handful of DNSBLs, including Spamhaus's "PBL" list. 

If you haven't already done so, one solution might be to include something like this in Postfix's main.cf file:
```
smtpd_recipient_restrictions =
    reject_invalid_hostname, 
    reject_non_fqdn_sender, 
    reject_non_fqdn_recipient, 
    reject_unknown_sender_domain, 
    reject_unknown_recipient_domain, 
    reject_unauth_pipelining, 
    permit_mynetworks, 
    reject_unauth_destination, 
    reject_rbl_client bl.spamcop.net,
    reject_rbl_client zen.spamhaus.org,
    permit

```

---

### Post by SeijiSensei on 2014-03-19
Take the server offline and read this: [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html).

You're being exploited as an "open relay." Visit [this page](http://mxtoolbox.com/blacklists.aspx) and enter your server's public IP address to see if you have yet been blacklisted.

---

### Post by lisati on 2014-03-19
> **SeijiSensei said:**
> Take the server offline and read this: [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html).

You're being exploited as an "open relay" and have apparently already been listed on at least one blacklist.

^^^This.

---

