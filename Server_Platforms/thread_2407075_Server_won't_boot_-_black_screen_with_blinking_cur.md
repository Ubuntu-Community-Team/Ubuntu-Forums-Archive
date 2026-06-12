---
title: "Server won't boot - black screen with blinking cursor"
date: 2018-11-29
forum: Server Platforms
---

### Post by trv75 on 2018-11-29
Hello -

I trying to recover a server, that was brought to me and isn't booting.  I'm kind of stuck - not sure how to proceed, without destroying the data.

Server boots up, and instead of getting a grub menu or anyhting just has a black screen with a blinking cursor.

It's got 4 3 TB drives, in software raid.  

Ran the boot-repair iso, and was unable to apply any fixes, as the boot-repair app complained about "no network connection" when in fact there _is_ a network connection.  So, I saved the output to pastebin:

[https://paste.ubuntu.com/p/SwQw2zDNn2/](https://paste.ubuntu.com/p/SwQw2zDNn2/)

If I uncheck the "check for network connectivity" option in the boot-repair tool - it just complains about some missing grub2 package.

I haven't done much with software raid (mdadm), so I am unclear where the /boot partition lives?  Is it on the software raid?  Or does it need to be a separate partition? If so, why does it seem like it's viewable across all 4 drives?

Ideally, I'd like to save the data.  It's not my server, so I have to be careful.

Thanks.

---

### Post by QIII on 2018-11-29
Moved to Server Platforms.

---

