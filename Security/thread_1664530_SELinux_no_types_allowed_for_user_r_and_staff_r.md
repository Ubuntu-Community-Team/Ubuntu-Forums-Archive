---
title: "SELinux: no types allowed for user_r and staff_r?"
date: 2011-01-11
forum: Security
---

### Post by freemant on 2011-01-11
Hi,

I am trying to understand how SELinux works on Ubuntu Lucid. I found that there are no types (domains) allowed for the user_r and staff_r roles, as shown by the seinfo command:
```

seinfo -ruser_r -x
seinfo -rstaff_r -x

```

Is this intended? In fact, I found no types like user_t nor staff_t but there is indeed sysadm_r and sysadm_t. What's the reasoning behind?

Thanks!

---

### Post by bodhi.zazen on 2011-01-11
> **freemant said:**
> Hi,

I am trying to understand how SELinux works on Ubuntu Lucid. I found that there are no types (domains) allowed for the user_r and staff_r roles, as shown by the seinfo command:
```

seinfo -ruser_r -x
seinfo -rstaff_r -x

```

Is this intended? In fact, I found no types like user_t nor staff_t but there is indeed sysadm_r and sysadm_t. What's the reasoning behind?

Thanks!

In my experience , selinux is poorly supported in Ubuntu.

If you want to run selinux I highly advise you run RHEL, Centos, or Fedora.

The tools to manage selinux and selinux alerts / denials alone in Fedora 14 are worth the switch.

---

### Post by freemant on 2011-01-11
Thanks for the pointers!

---

### Post by bodhi.zazen on 2011-01-12
You are most welcome. 

You might also be interested in xguest

Basically it is a kiosk but locked down by selinux.

Very very handy for friends and family ;)

---

