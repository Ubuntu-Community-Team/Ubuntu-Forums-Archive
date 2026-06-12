---
title: "Postfix Blacklist/Whitelist"
date: 2016-02-25
forum: Server Platforms
---

### Post by theonlytalkinggoat on 2016-02-25
Can someone please tell me if I'm doing this right or if they see a problem? I have a server that blocks email from entire networks, from foreign countries. Since I really don't get mail from anyone else, outside of my country, there isn't really a reason to accept it and the reduction of spam far outweighs the risk of something getting blocked. However, sometimes an email will get blocked, because the account of the individual is hosted on a server within the blocked range. If I wanted to unblock a domain, say, hotmail.com, in the REJECT range of 5.0.0.0/8, should I use the following configuration:

main.cf
```
smtpd_recipient_restrictions = ... 
   check_sender_access hash:/etc/postfix/sender_access,
   check_client_access cidr:/etc/postfix/client_checks,
...
```

sender_access
```
...
hotmail.com    OK
...
```

client_access
```
...
5.0.0.0/8     REJECT    No foreign IP addresses.
...
```

For me, this configuration works and it is my understanding that, because sender_access comes before client access, anything in sender_access is whitelisted and shielded from any of the following rules or checks (rbls, blacklists, greylists). Is that correct?

---

