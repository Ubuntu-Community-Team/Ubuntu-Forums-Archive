---
title: "User Permissions"
date: 2009-10-25
forum: Security
---

### Post by faisal892 on 2009-10-25
Hi all,

When I try to open Synaptic i get this message

"Failed to run /usr/sbin/synaptic as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator"

Similarly Users and Groups is not opening, it says.

"The configuration could not be loaded

You are not allowed to access the system configuration"

Every thing was going on well till yesterday but today this problem occured.

Please help.

Faisal.

---

### Post by iMisspell on 2009-10-25
Dont think this will fix your problem, but might help trouble shoot.

Try this in a terminal window...
```
gksu /usr/sbin/synaptic
```
It shuold ask you for your root password, then load Synaptic.

_

---

### Post by cariboo on 2009-10-25
It sounds like you removed yourself from the admin group. IF that is what happen start in recovery mode and at the prompt type gpasswd -a <username> admin.

---

### Post by faisal892 on 2009-10-25
> **cariboo907 said:**
> It sounds like you removed yourself from the admin group. IF that is what happen start in recovery mode and at the prompt type gpasswd -a <username> admin.

This solved my problem. Thank you very much Sir.

Faisal.

---

### Post by cariboo on 2009-10-25
Your welcome

---

