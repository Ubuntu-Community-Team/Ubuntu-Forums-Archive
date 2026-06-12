---
title: "Enabling NX Features on the Starling"
date: 2010-05-14
forum: System76 Support
---

### Post by Carl Hamlin on 2010-05-14
Heya, everyone.

Since installing 10.04, I've been getting the following message when I log in:

```

Your CPU appears to be lacking expected security protections.
Please check your BIOS settings, or for more information, run:
/usr/bin/check-bios-nx --verbose

```

OK, fair enough. When I run check-bios-nx, I get the following message:

```

This CPU is family 6, model 28, and has NX capabilities but is unable to
use these protective features because the BIOS is configured to disable
the capability. Please enable this in your BIOS. For more details, see:
https://wiki.ubuntu.com/Security/CPUFeatures

```

I went out to the wiki, and got the information I needed concerning NX features. Doesn't look like a real issue for a netbook, but out of curiosity, I tried to enable the features in the BIOS. As it turned out, the process for enabling these features is either absent, or so non-intuitive that I wasn't able to piece it together.

Anybody know how to do it with the Starling?

---

### Post by macabrem on 2010-05-15
Your question might be answered here:

[http://ubuntuforums.org/showthread.php?t=1481459](http://ubuntuforums.org/showthread.php?t=1481459)

Hope that helps.

---

### Post by Carl Hamlin on 2010-05-15
> **macabrem said:**
> Your question might be answered here:

[http://ubuntuforums.org/showthread.php?t=1481459](http://ubuntuforums.org/showthread.php?t=1481459)

Hope that helps.

Thanks, macabrem. That's pretty much what I was afraid of.

When I get a little time I'll bang out a workaround just to see what happens.

---

### Post by narcisgarcia on 2010-12-26
I see the "check-bios-nx" message in a lot of computers, and because of lacking BIOS option to enable NX feature, now I remove the warning message:

```
sudo rm /etc/update-motd.d/20-cpu-checker
```

---

