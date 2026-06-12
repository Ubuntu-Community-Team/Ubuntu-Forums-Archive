---
title: "User mounting USB, but is not in plugdev"
date: 2023-09-04
forum: Security
---

### Post by dotdotdot3 on 2023-09-04
Hello,

I have a domain user that is able to mount USB drives, despite not being part of plugdev. the user is an unprivileged user.
I am using 22.04, and tested on Ubuntu, xubuntu, and kubuntu, all with the same issue.

The user is only part of 2 groups:[INDENT]domain [email]users@mydomain.com[/email]
[email]no_usb@mydomain.com[/email][/INDENT]

(I use the [email]no_usb@mydomain.com[/email] to block access to USB on Windows workstations)

Should domain users that have no plugdev be able to mount USB storage devices?

---

### Post by Morbius1 on 2023-09-05
plugdev isn't a thing any longer as it's function has been replaced by udisks2.

For a more authoritative description please see: [group plugdev is deprecated]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=897916")

---

### Post by dotdotdot3 on 2023-09-05
Thanks Morbius1, i did not know about that.

For future reference I ended up going with a polkit solution, as it allowed me to be very granular with very little overhead.


> **Morbius1 said:**
> plugdev isn't a thing any longer as it's function has been replaced by udisks2.

For a more authoritative description please see: [group plugdev is deprecated]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=897916")

---

