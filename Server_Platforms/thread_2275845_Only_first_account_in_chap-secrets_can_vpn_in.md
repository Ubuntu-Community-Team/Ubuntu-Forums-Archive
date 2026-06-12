---
title: "Only first account in chap-secrets can vpn in?"
date: 2015-04-28
forum: Server Platforms
---

### Post by fizgig on 2015-04-28
I installed pptp as described here:  [https://help.ubuntu.com/community/PPTPServer](https://help.ubuntu.com/community/PPTPServer)

Works like a champ if I try to login with the credentials of the first account in chap-secrets.  If I do the second account, no dice.  It's pretty straightforward:

```
name1 * password1 *
name2 * password2 *
```

If I flip the order, then I can login with name2 and not name1.  I'm not talking simultaneous login by the way, just logging in with one account at a time.  Anyone know what's going on here?

---

