---
title: "Postgrey?"
date: 2005-07-26
forum: Server Platforms
---

### Post by Nequeo on 2005-07-26
Just wondering - has anyone used Postgrey under Ubuntu?

I installed it through Synaptic. I can see it running with 'ps -e'

```

5070 ?        00:00:00 postgrey

```

I can see it listening with 'netstat -a | grep 60000'

```
 
tcp        0      0 mail.tebbuts.com.:60000 *:*                     LISTEN

```

I've added it into main.cf like so:
```

smtp_recipient_restrictions =
        reject_unauth_pipelining,
        reject_non_fqdn_recipient,
        reject_unknown_recipient_domain,
        permit_mynetworks,
        reject_unauth_destination,
        check_policy_service inet:127.0.0.1:60000,

```

...and yet, when I telnet into my mail server remotely, I get the following.

```

220 mail.tebbutts.com.au ESMTP Postfix (Ubuntu)
HELO mail.blaironia.com
250 mail.tebbutts.com.au
MAIL FROM:<####@####.com>
250 Ok
RCPT TO:<####@tebbutts.com.au>
250 Ok

```

No greylisting to be seen! Any ideas what I'm doing wrong? I'm a little worried about that listening at mail.tebbuts.com.au thing. The MX records haven't been reassigned yet, so it's not actually mail.tebbutts.com.au. In fact, that address currently points to an off-site mail server run by a different company. However, I have set that as the FQDN of the machine in /etc/hosts. 

Any ideas?

---

### Post by Nequeo on 2005-07-27
Never mind. It was a typo.

smtp*d*_recipient_restrictions

---

### Post by deuce868 on 2005-07-27
You'll love postgrey. It's cut down my spam levels a TON and in 3 months I've yet to have a reported problem from any users.

---

