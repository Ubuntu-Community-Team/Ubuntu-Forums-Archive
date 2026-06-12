---
title: "ssh keys no longer accepted after something got upgraded by ubuntu"
date: 2012-03-11
forum: Security
---

### Post by Bashar &quot; on 2012-03-11
For some reason I no longer can ssh into any of tens of servers I manage running OpenSSH_5.8p1

I even copied back my older .ssh folder from a backup i had, still can't login

I'm suspecting openssh got upgraded or some other library got upgraded and this problem started?

another laptop with older version of openssh_5.3p1 with the same same ssh keys works fine but this laptop doesn't

the ssh -v shows these error messages multiple times with other lines in between too
debug2: we did not send a packet, disable method
Agent admitted failure to sign using the key.

anythign recently happened to openssh or shall i downgrade?

thanks

---

### Post by matt_symes on 2012-03-11
Hi

Post back the entire output from

```
ssh -vvv user@box
```

That will give more complete information.

Kind regards

---

### Post by Bashar &quot; on 2012-03-11
> **matt_symes said:**
> Hi

Post back the entire output from

```
ssh -vvv user@box
```

That will give more complete information.

Kind regards

i got some updates on ubuntu, so i've ran them including a kernel update which was tehre and now i can re-ssh again.

its really weird, openssh still the same

not sure what really happened


thanks anyway

---

