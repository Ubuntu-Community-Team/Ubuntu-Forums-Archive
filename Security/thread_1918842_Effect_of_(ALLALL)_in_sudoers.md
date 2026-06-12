---
title: "Effect of (ALL:ALL) in sudoers?"
date: 2012-02-01
forum: Security
---

### Post by blak111 on 2012-02-01
Hello,

What is the purpose of the ALL:ALL in the sudoers file for the default %sudo group entry?

```

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

```

In other words, what's the difference between those two lines? I understand that the admin group can run any command from any machine as any user, so what extra or reduced functionality does the sudo group get?

Thanks

---

### Post by Dangertux on 2012-02-01
> **blak111 said:**
> Hello,

What is the purpose of the ALL:ALL in the sudoers file for the default %sudo group entry?

```

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

```In other words, what's the difference between those two lines? I understand that the admin group can run any command from any machine as any user, so what extra or reduced functionality does the sudo group get?

Thanks

Users in the admin group may become root. Users in the sudo group can only use the sudo command.

For instance, they could not sudo su

Hope this helps.

---

### Post by Dave_L on 2012-02-02
So ":ALL" denies permission to become another user?  I looked at the man page, but it wasn't clear to me.

---

### Post by Lars Noodén on 2012-02-02
(ALL:ALL) refers to (user:group) that [sudo](http://manpages.ubuntu.com/manpages/oneiric/en/man8/sudo.8.html) will use.  It can be specified with **-u** and **-g** when you run sudo.  If you don't specify anything it will run as root:root, which is the default.  That's how most end up using it anyway.

---

