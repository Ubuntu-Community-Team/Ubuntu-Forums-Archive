---
title: "removed myself from sudoers list"
date: 2011-12-15
forum: Security
---

### Post by d0.higgs on 2011-12-15
Hi,

This does not seem to be my day. For some reason (mostly experimenting) I used sudo visudo and removed my name (the whole line) from there. Now, of course, I cannot use sudo any more. I cannot even use "sudo su" to be root. The whole system is unaccessible to me now.

Any solution(s) to this issue?

---

### Post by d0.higgs on 2011-12-15
I followed this link:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)
but I could not use sudo visudo from the root command line. It said root is not in the sudoers file. This incident will be reported.

I don't get this, how can root be not in the sudoers list?

---

### Post by haqking on 2011-12-15
> **d0.higgs said:**
> I followed this link:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)
but I could not use sudo visudo from the root command line. It said root is not in the sudoers file. This incident will be reported.

I don't get this, how can root be not in the sudoers list?

you cant sudo su if you are not in the sudo group.

And root doesnt need to use sudo

see here to repair sudo

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by d0.higgs on 2011-12-15
It did not work. sudo visudo did not work :(

---

### Post by OpSecShellshock on 2011-12-15
If you're in a root shell you shouldn't need to use sudo because you're already root.

---

### Post by hawkmage on 2011-12-15
If you boot from CD into recovery mode and directly edit the sudoers file you should be able to fix the issue.  In recovery mode you are root and do not need to use sudo or su to edit the sudoers file.

---

### Post by d0.higgs on 2011-12-16
Solved.

I found an old live-CD (10.04) and out of nothing else to do to save my system, I used it (after all, it should give me some way to mount my system partition) following some windows I asked for a root command which I used to "vi" my file.

All seems fine now.

Thanks guys.

---

