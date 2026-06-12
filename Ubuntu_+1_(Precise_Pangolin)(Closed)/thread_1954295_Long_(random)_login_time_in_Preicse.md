---
title: "Long (random) login time in Preicse"
date: 2012-04-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mmasroorali on 2012-04-07
Did any of you notice this? 

After upgrading to 12.04, sometimes (at random) it takes too long to login. 

You put in your password and press enter. Sometimes, the login window disappears instanteneously, and after login processes begin. Sometimes, the login window remains there, mouse works, you can not type in the password box, and after about a minute or more the after login processes begin.

Any idea why is this happening? 

Hope this is corrected before the final release at the end of this month.

All the best.

---

### Post by cryptotheslow on 2012-04-08
Yes, I see the same here. Not just as you describe, but also random delays for the password entry box to accept input in the first place as well as delays after password entry.

I've done no investigation at all, but I vaguely suspect it is down to ureadahead reprofiling. I generally pull down updates once a day or so and more often than not the update process states something like "ureadahead will be reprofiled on next reboot". As I only reboot once every day or two, ureadahead is reprofiling on every boot thanks to the number of updates received on a beta.

Some info on ureadahead:
[http://ubuntuforums.org/showthread.php?t=1434502](http://ubuntuforums.org/showthread.php?t=1434502)

That's just my speculation and more than likely wrong. I'll try some reboots when I'm sure ureadahead isn't reprofiling and see if the behaviour changes as expected.

---

### Post by mmasroorali on 2012-04-08
> **cryptotheslow said:**
> Yes, I see the same here. Not just as you describe, but also random delays for the password entry box to accept input in the first place as well as delays after password entry.

I've done no investigation at all, but I vaguely suspect it is down to ureadahead reprofiling. I generally pull down updates once a day or so and more often than not the update process states something like "ureadahead will be reprofiled on next reboot". As I only reboot once every day or two, ureadahead is reprofiling on every boot thanks to the number of updates received on a beta.

Some info on ureadahead:
[http://ubuntuforums.org/showthread.php?t=1434502](http://ubuntuforums.org/showthread.php?t=1434502)

That's just my speculation and more than likely wrong. I'll try some reboots when I'm sure ureadahead isn't reprofiling and see if the behaviour changes as expected.

Thanks for responding. For me the first effect (the password entry box to accept input in the first place) never happened (I don't claim that it will not). But the effect I described started about a month when I went for beta version.

As I tell the Windows cult members in my office, life is pretty dull when you use linux, everything is so smooth. This is only twice in a year (beta version period) I get the taste of what you have believed to be the speciality (of Windows) of your operating system.

But again, these are not the same. 

Just shared some scattered feelings.

---

