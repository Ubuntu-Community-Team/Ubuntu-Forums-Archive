---
title: "Configuring sshd"
date: 2009-03-26
forum: Security
---

### Post by a7ndrew on 2009-03-26
Is there a way to configure sshd so that user 1 (who is a sudoer) can only access from the local net (ie 192.168.X.X) or via port 22, while user (or usergroup) 2 (who is not a sudoer) can access ssh from anywhere, possibly using a different port?

Basically the idea is to permit remote access but limit it to user level accounts only, whilst allowing me to use ssh to access the machine here on the local network.

---

### Post by Bachstelze on 2009-03-26
Add something like this to [font="monospace"]/etc/ssh/sshd_config[/font]:

```
#user1 can connect only from a machine whose IP matches
AllowUsers user1@192.168.*.*

#user2 can connect from anywhere
AllowUsers user2

#likewise for all members of group1
AllowGroups group1
```

All users that are not [font="monospace"]user1[/font], [font="monospace"]user2[/font] or a member of [font="monospace"]group1[/font] can't connect at all. Also, unfortunately, [font="monospace"]AllowGroups[/font] does not accept a hostname restriction.

---

### Post by a7ndrew on 2009-03-26
Thanks so much!

---

