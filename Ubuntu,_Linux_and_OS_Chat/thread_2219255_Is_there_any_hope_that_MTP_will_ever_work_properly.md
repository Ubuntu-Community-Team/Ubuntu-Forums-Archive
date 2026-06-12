---
title: "Is there any hope that MTP will ever work properly?"
date: 2014-04-23
forum: Ubuntu, Linux and OS Chat
---

### Post by halfbeing on 2014-04-23
Is there any hope that MTP will ever work properly? Someone told me that there were big improvements in MTP operability in Trusty, but I have just installed Trusty and am finding its MTP connectivity as hopeless as ever. I have just spent an hour trying and failing to copy three small files from my phone to disk and have so far failed. I have, in the process, had to reboot my phone half a dozen times, kill Thunar countless times, and I have been on a wild goose chase looking for alternative software to do the job, but all to no avail. If you can't connect to an android phone with Ubuntu then it cannot qualify as a mainstream desktop operating system. Why has this problem been allowed to fester for so long? Will it ever get better?

---

### Post by 3rdalbum on 2014-04-24
Why do you think this problem affects everybody? I haven't had any problems.

Your USB ports, or USB cable, are probably buggered. Also, don't put more than two devices into an unpowered hub.

---

### Post by halfbeing on 2014-04-24
Thanks for the suggestions.

I was feeling very frustrated about a lot of things yesterday and I let it spill onto the forum. I apologise to anyone I may have offended or upset.

Your suggestions were worth making because I had forgotten that my USB hub used to play up when I tried to run my webcam through it. However it turns out that the main problem in this case is very specifically to do with transferring photos that have been previously uploaded from the phone to Twitter. libmtp chokes on these for some reason. I have submitted a [bug report]("https://bugs.launchpad.net/ubuntu/+source/libmtp/+bug/1312377").

---

