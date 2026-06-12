---
title: "Server Becoming Unresponsive"
date: 2014-06-04
forum: Server Platforms
---

### Post by Graysonh on 2014-06-04
This problem is a little difficult to explain - so bear with me.

The issue seems to arise when remote interfacing with the server (SSH, Transmission Web/Remote GUI). Say I add a torrent and begin to download, anywhere from 2 minutes to 2 hours later I will get a "Connection Failed" error that can be fixed by hitting any key on the keyboard of the server to wake the screen. I've found that monitoring from the Web GUI causes this to occur more quickly, and that quickly viewing the page for 5 seconds or so will NOT cause this to happen.

I've done some searches, but none of the solutions I've found are relevant to my situation. Any insights?

---

### Post by papibe on 2014-06-04
Hi Graysonh.

My first reaction is that it could be some sort of power-saving/sleep feature.

I'd start checking the BIOS to see if there any power saving settings that is causing the problem. 

Just a thought.
Regards.

---

### Post by Graysonh on 2014-06-04
Thank you for the suggestion.

I looked through the BIOS and wasn't able to find anything. I'm still new to this - what logs should I be looking at?

---

### Post by tgalati4 on 2014-06-05
Check all logs in /var/log and especially any powersaving such as pm-powersave.log or pm-suspend.log--that would be a clue.

Open an ssh terminal on another machine, install *htop* and watch *htop* during your transmission session. See if you notice any strange behavior.

There are ssh timeout features based on non-activity to improve security, so perhaps ssh is simply reaching the timeout and logging off your ssh process.

---

