---
title: "Ubuntu 18.04 on Active Directory"
date: 2018-09-06
forum: Security
---

### Post by nbatescmf on 2018-09-06
I've been in Linux for something like 15 years, but I've never added a Linux Server to an Active Directory domain. I followed [this post]("https://help.ubuntu.com/lts/serverguide/sssd-ad.html.en") to add an experiment Ubuntu Server to my company domain, and when I got to this part:

```

[FONT=monospace]sudo net ads join -k
[/FONT]
```

This was the result

```
administrator@it-srv:~$ sudo net ads join -k
Host is not configured as a member server.
Invalid configuration.  Exiting....
Failed to join domain: This operation is only allowed for the PDC of the domain.

```

Any advice? I did use the domain administrator account to try to add.

---

