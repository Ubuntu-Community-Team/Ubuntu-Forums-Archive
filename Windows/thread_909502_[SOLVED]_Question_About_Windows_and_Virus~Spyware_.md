---
title: "[SOLVED] Question About Windows and Virus~Spyware Scanning"
date: 2008-09-03
forum: Windows
---

### Post by Rytron on 2008-09-03
Hi,
Someone I know has viruses on their Windows Vista pc.
They have an administrator account under their own name. They also have a limited account.

My question is this: Could I have them set up another administrator account and then let me do full virus and spyware scans from that newly created account? Would scanning from this newly created account scan all other accounts on the machine also?

Please reply.

Thank you.

---

### Post by karellen on 2008-09-03
I don't think so. there can be only one administrator account, thought I know in Vista there is something called Super User mode or something like that that escalates the privileges of the administrator

---

### Post by Erdaron on 2008-09-04
Are you sure there can only be one admin account? On XP you could have multiple admins.

I don't think creating a new account would insulate you from the existing viruses. Anything you install using that account would be affected by the virus (if the virus is sophisticated enough to attack anti-virus software).

You could try using an online scanning service, such as the one from [Comodo]("http://www.comodo.com/products/free_products.html"). It might also be possible to load a Linux-based anti-virus software (ClamAV is one, I believe) onto a LiveCD, and use that to scan the system.

---

### Post by Betsybuntu on 2008-09-04
It's entirely possible to create a second administrator account in Vista.

---

### Post by Battie on 2008-09-05
> **karellen said:**
> I don't think so. there can be only one administrator account, thought I know in Vista there is something called Super User mode or something like that that escalates the privileges of the administrator

Clarification:

In XP, there is a default administrator account, but any number of additional accounts can be created.  They all behave the same way.

In Vista, there is also a built-in administrator account, but it is disabled by default. This account is not affected by UAC. A user running this account will always be in privileged mode, just like in XP.  This behavior can be changed in Group Policy.

Any number of additional administrators can be created. These administrators, however, are affected by UAC and always run as a standard user unless they consent to the UAC prompt.  This is also configurable in Group Policy.

A standard user account must use the credentials of an administrator account to accomplish the same task.

Does that help?

---

