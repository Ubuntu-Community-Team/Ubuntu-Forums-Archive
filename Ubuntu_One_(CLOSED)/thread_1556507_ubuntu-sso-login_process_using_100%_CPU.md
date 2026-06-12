---
title: "ubuntu-sso-login process using 100% CPU"
date: 2010-08-19
forum: Ubuntu One (CLOSED)
---

### Post by ratcheer on 2010-08-19
When I run Ubuntuone Preferences applet and connect to Ubuntuone, process ubuntu-sso-login starts using 100% of my CPU and continues to do so even if I log out and disconnect from Ubuntuone. The only way I can stop the high CPU utilization is to reboot or log off the desktop. Does this happen to others?

I opened bug 620584 on Launchpad.

Tim

---

### Post by ratcheer on 2010-08-19
I tested on Lucid and it did not constantly use 100% of the CPU. I went back to Maverick, tried it again, and it still does it in Maverick. So, it is apparently the Maverick Ubuntuone client that is the problem.

Tim

---

### Post by mc4man on 2010-08-19
This has been a known issue for a bit, bug report here
[https://bugs.launchpad.net/ubuntu-sso-client/+bug/617041](https://bugs.launchpad.net/ubuntu-sso-client/+bug/617041)

Supposedly the latest package fixes, I don't see any improvement here - cpu use still climbs to 100% on 1 cpu and will remain so till as you note.

Would be good if you could apply the update and test

---

### Post by ratcheer on 2010-08-20
> **mc4man said:**
> This has been a known issue for a bit, bug report here
[https://bugs.launchpad.net/ubuntu-sso-client/+bug/617041](https://bugs.launchpad.net/ubuntu-sso-client/+bug/617041)

Supposedly the latest package fixes, I don't see any improvement here - cpu use still climbs to 100% on 1 cpu and will remain so till as you note.

Would be good if you could apply the update and test

They have marked my bug as a duplicate of that bug. It is strange, when I searched for it on Launchpad, it found nothing. But when I created my bug report, it would show the existing bug when I searched for mine. Weird.

Anyway, there was an update of ubuntuone-client, yesterday. It did not fix the problem. There will be an update of ubuntu-sso-client, today. The delay of opening the web browser is an attempt at a workaround, but bug 617041 states that it is not really a fix:

```

ubuntu-sso-client (0.99.1-0ubuntu1) maverick; urgency=low

 * New upstream release:
   - Delayed opening the webkit browser to the latest possible. (LP: #617041)
   (nataliabidart)
   - Use a proper dictionary with different attributes for each key so old
   keys are not overwritten nor deleted. (LP: #617347) (alecu)

```

Tim

---

### Post by ratcheer on 2010-08-20
I have upgraded to the latest package ubuntu-sso-client. It did **not** fix the 100% CPU usage problem after opening the Ubuntuone Preferences applet.

Tim

---

### Post by yuretsz on 2010-11-07
Two bad, but this has not been fixed yet for Maverick.

---

