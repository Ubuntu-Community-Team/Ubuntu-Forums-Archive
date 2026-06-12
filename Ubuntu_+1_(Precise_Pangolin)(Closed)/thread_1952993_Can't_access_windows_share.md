---
title: "Can't access windows share"
date: 2012-04-05
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by hfw on 2012-04-05
After upgrading to 12.04 I can no longer access the windows shares at work.  The shortcuts are still listed in nautilus, but when I try to access them it just keeps asking me to input my password again.  It also does not work if I try to get to them through 'Browse Network'

Any help would be appreciated.

Thanks,
Hal

---

### Post by cariboo on 2012-04-05
This has already been discussed, try the solution [here]("http://ubuntuforums.org/showpost.php?p=11685772&postcount=5").

---

### Post by hfw on 2012-04-05
Thanks.

my search skills on the forum are obviously lacking.  That worked liked magic.

-hal

---

### Post by cariboo on 2012-04-05
> **hfw said:**
> Thanks.

my search skills on the forum are obviously lacking.  That worked liked magic.

-hal

I actually got the fix from a bug report on Launchpad. I'm glad you got the problem resolved.

---

### Post by sgage on 2012-04-06
> **hfw said:**
> Thanks.

my search skills on the forum are obviously lacking.  That worked liked magic.

-hal

Didn't work for me. I have been successfully browsing Windows shares on my network with nautilus for a long time, and it simply stopped working with 12.04. I've searched around and tried all the fixes I've found, but no joy. Does anyone have a simple working smb.conf they might share?

Browsing with Nautilus finds "Windows Network", but double-clicking that gets me the ol' "unable to mount location, failed to retrieve share list from server" error.

Also, the Windows machines can see my Ubuntu box, but can't access it.

This really shouldn't be so hard to do.

---

### Post by miguelpires on 2012-04-06
> **sgage said:**
> Didn't work for me. I have been successfully browsing Windows shares on my network with nautilus for a long time, and it simply stopped working with 12.04. I've searched around and tried all the fixes I've found, but no joy. Does anyone have a simple working smb.conf they might share?

Browsing with Nautilus finds "Windows Network", but double-clicking that gets me the ol' "unable to mount location, failed to retrieve share list from server" error.

Also, the Windows machines can see my Ubuntu box, but can't access it.

This really shouldn't be so hard to do.

Same problem with my all my machines, 5 Ubuntu's... Some update from this week that cause the problem, in 12.04 and in 11.10!!!

---

