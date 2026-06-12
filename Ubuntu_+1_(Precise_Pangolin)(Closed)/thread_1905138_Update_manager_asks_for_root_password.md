---
title: "Update manager asks for root password"
date: 2012-01-06
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by eyelessfade on 2012-01-06
So I upgraded to 12.04 in an vm for test purposes. I found that the Update Manager now asks for the root password, and not for the sudo password. (Note that both has been set.) Is this a bug or the new trend?

---

### Post by ajgreeny on 2012-01-06
Having set a root password, even though this is not recommended by Ubuntu or this forum, surely the behaviour you see is to be expected.  If not, what is the point of ever having the root account enabled?

---

### Post by eyelessfade on 2012-01-06
> **ajgreeny said:**
> Having set a root password, even though this is not recommended by Ubuntu or this forum, surely the behaviour you see is to be expected.  If not, what is the point of ever having the root account enabled?

11.10 didn't ask for root pw.

As for the point. Root pw is for staff, and sudo for clients.
So if this behaviour is what we can expect we need to rethink our approach.

---

### Post by ajgreeny on 2012-01-06
OK, I see your point, but unfortunately I do not know of an answer.

---

### Post by mc4man on 2012-01-06
What's happening is reminiscent of when the change from admin to sudo first occurred in 12.04. (no longer an issue in policykit whether user(s) are in sudo or admin group

With your particular use case you could file a bug, here's the orig & ongoing report if add. issues arise

[https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/893842](https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/893842)

---

### Post by eyelessfade on 2012-01-06
Thanks. I'll see into that.

---

### Post by dino99 on 2012-01-06
maybe check your users & groups settings

---

### Post by jbicha on 2012-01-06
eyelessfade, are you running Unity or some other desktop?

---

### Post by eyelessfade on 2012-01-06
I'm just testing default setup for our users, so yes unity is the wm I'm using now.

---

### Post by eyelessfade on 2012-01-06
> **dino99 said:**
> maybe check your users & groups settings

indeed, it seems that I'm in no special groups anymore, I'll have to take a look at that on monday.

---

### Post by eyelessfade on 2012-01-06
The problem was indeed the lack of groups for the user.

---

