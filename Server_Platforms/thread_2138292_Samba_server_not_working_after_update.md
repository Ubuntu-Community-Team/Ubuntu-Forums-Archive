---
title: "Samba server not working after update"
date: 2013-04-23
forum: Server Platforms
---

### Post by tsunamikitsune on 2013-04-23
I recently logged into my Ubuntu server machine and ran an "apt-get upgrade" command. I'm not sure what exactly it ended up breaking, but for some reason my Samba shares are now completely inaccessible from my Windows computers. When I try to check the status of the smbd service, it's always stopped, even if after attempting to start it:

```

$ sudo service smbd status
smbd stop/waiting
$ sudo service smbd start
smbd start/running, process 12503
$ sudo service smbd status
smbd stop/waiting

```

I'm not sure if this is relevant, but if I just type "smbd", I get the following:

```

$ smbd
smbd: relocation error: smbd: symbol krb5_locate_kdc, version krb5_3_MIT not defined in file libkrb5.so.3 with link time reference

```

Any suggestions? I don't know that it's specifically the fact that I updated something, but I didn't notice an issue with share access until after I finished messing around. I can't think of anything else I may have done, though. :/

---

### Post by cj13579 on 2013-04-24
Is your system fully up to date now? A quick google on your error brings up and old bug from 2 years ago but that shouldn't be an issue now I wouldn't think. It may also be useful to post your log from /var/log/samba (log.smbd)

---

