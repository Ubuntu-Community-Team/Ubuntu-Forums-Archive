---
title: "postfix hostname resolution error with DNS round-robin"
date: 2013-05-12
forum: Server Platforms
---

### Post by snathan99 on 2013-05-12
My postfix server is set to reject mail from invalid hostnames. Below is the full/relevant config:


```

    smtpd_recipient_restrictions =
    check_client_access hash:/etc/postfix/white_lists,
    reject_invalid_hostname,
    reject_non_fqdn_hostname,
    reject_non_fqdn_sender,
    reject_non_fqdn_recipient,
    reject_unknown_sender_domain,
    reject_unknown_recipient_domain,
    reject_unknown_client_hostname,
    reject_unverified_sender,
    permit_mynetworks,
    reject_unauth_destination,
    reject_rbl_client zen.spamhaus.org,
    reject_rbl_client cbl.abuseat.org,
    permit

```

Sure enough I get this:
```

May 1 19:44:13 postfix/smtpd[15588]: warning: hostname mail.example.org does not resolve to address nnn.nnn.nnn.75
May 1 19:44:13 postfix/smtpd[15588]: connect from unknown[nnn.nnn.nnn.75]
May 1 19:44:13 postfix/smtpd[15588]: NOQUEUE: reject: RCPT from unknown[nnn.nnn.nnn.75]: 550 5.7.1 Client host rejected: cannot find your hostname, [nnn.nnn.nnn.75]; from= proto=ESMTP helo=
May 1 19:44:13 postfix/smtpd[15588]: disconnect from unknown[nnn.nnn.nnn.75]

```

However the sending server mail.example.org has "DNS round-robin" setup with both nnn.nnn.nnn.75 & nnn.nnn.nnn.76.

ping from my server to mail.example.org returns nnn.nnn.nnn.76 or nnn.nnn.nnn.75 interchangeably, while NSLOOKUP of the mail.example.org returns both. So the above error shows up when the sending server IP address happens to be nnn.nnn.nnn.75 and ping returns nnn.nnn.nnn.76 (or vice-versa).  How do I setup postfix to not reject this other than whitelisting it?

---

### Post by SeijiSensei on 2013-05-13
> So the above error shows up when the sending server IP address happens to be nnn.nnn.nnn.75 and ping returns nnn.nnn.nnn.76 (or vice-versa).

I suspect the forward and reverse lookups for the IP address do not match.  What do you get if you run a reverse query with
```
host -t ptr xx.xx.xx.75
host -t ptr xx.xx.xx.76
```
Do they both point to mail.example.com?  If not, that is what Postfix is complaining about.

I do not enforce rules like this on my incoming servers because they generate too many false positives like the one you encountered.  There are just too many uninformed mail administrators out there who do not understand the need to have consistent forward and reverse DNS resolution.  I let SpamAssassin handle this problem after the message arrives.  Its stock ruleset adds "spamminess" points to messages whose sending IPs do not resolve to match the hostnames.

---

### Post by snathan99 on 2013-05-14
Both respond correctly (as did nslookup)

```

host -t ptr nnn.nnn.nnn.75
75.nnn.nnn.nnn.in-addr.arpa domain name pointer mail.example.org.

```

```

host -t ptr nnn.nnn.nnn.76
76.nnn.nnn.nnn.in-addr.arpa domain name pointer mail.example.org.

```

Also here is what nslookup has to say:

```

nslookup mail.example.org.

Non-authoritative answer:
Name:   mail.example.org
Address: NNN.NNN.NNN.76
Name:   mail.example.org
Address: NNN.NNN.NNN.75

```

However postfix does NOT track ALL ips that resolve for mail.example.org.  So it does a lookup for IP and just goes with the 1st one it gets.  But then rejects that it does not compare with the incoming connection IP!

I suppose this is an issue with postfix that may not have a resolution unless postfix is updated.  Anyone think otherwise?  I would rather be proven wrong and have an easier way to handle this.  I love the spam prevention that postfix does and removes 99% of spam with these checks.  So would hate to remove that and get a flood of spam.  I particularly don't like ANTI-SPAM filters - too heavy.  And again, then probably come with quirks of their own that I have to deal with :)

Thanks

---

