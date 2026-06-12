---
title: "ssmtp issue"
date: 2007-08-24
forum: Server Platforms
---

### Post by md5hash on 2007-08-24
why ssmpt is sending emails twice?

heres my current config:

```
#
# Config file for sSMTP sendmail
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
#root=postmaster

# The place where the mail goes. The actual machine name is required no 
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=***.**.**.*

# Where will the mail seem to come from?
rewriteDomain=iportal

# The full hostname
#hostname=iportal

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
FromLineOverride=YES
```

---

### Post by NewbieNik on 2007-08-24
Because it loves you? only joking, badly!

Is there a possibility that you receive mail for more than one domain eg example.com and example.co.uk?

---

