---
title: "Ensuring a given init script runs before another"
date: 2014-03-11
forum: Server Platforms
---

### Post by User4519 on 2014-03-11
Hi :)

I'd like to create an init script to use on Amazon EC2, where ephemeral storage devices are wiped between start/stop cycles. I want it to initialize the storage so that it is ready for my web stack, which means that I'd like for it to run after some certain other scripts ($local_fs, $named, mdadm, ...) but also ensure that it runs before my web stack members get started. The first part is easy (via Required-Start), but I'm not sure how to accomplish the second part. That is, without modifying the init scripts of, e.g. apache and mysql (which, if possible, I'd prefer not to).

Is this possible without modifying init scripts that "don't belong to me"? And if so, how?

Thanks a lot :)

Daniel

EDIT: It might be useful to know that this is on a 14.04 version of Ubuntu Server.

**SOLVED**: Once again, I've failed to just do a simple manpage lookup before Googling and traversing old Debian-related documents :) The answer is simple, Ubuntu supports **X-Start-Before** to do exactly what I need :) Sorry!

---

