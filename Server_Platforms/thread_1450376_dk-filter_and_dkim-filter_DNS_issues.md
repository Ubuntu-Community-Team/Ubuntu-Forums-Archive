---
title: "dk-filter and dkim-filter DNS issues"
date: 2010-04-09
forum: Server Platforms
---

### Post by ernieg92 on 2010-04-09
How can I tell if there is a DNS resolution problem with my server?  I'm using a basic Ubuntu Server 9.10 x64 installation with Postfix/Amavis/DKIM setup.  My outgoing mail is signed fine.  However, the incoming mail doesn't appear to be.  

99.9% of the mail comes in with this in the mail log:
```

dkim-filter[1626]: 07CF5134C5: no signature data
```

I did have one come in with this in the log:
```

dkim-filter[1626]: CD2CCD95 ADSP query: syntax error in policy data
dkim-filter[1626]: CD2CCD95: no signature data

```

and another one with this one (and this is the one that makes me wonder about DNS resolution):
```

dkim-filter[1626]: 7E6FDD95 ADSP query: timeout DNS query for `d49.org'
dkim-filter[1626]: 7E6FDD95: no signature data

```

This error comes from the header of an email from gmail user:
```

domainkeys=softfail (invalid, public key: DNS query timeout for gamma._domainkey.gmail.com)
```

Do most senders NOT use DK or DKIM signatures?  Do I have a problem with my DNS?  How can I troubleshoot/fix?  

Thanks for your help.

---

