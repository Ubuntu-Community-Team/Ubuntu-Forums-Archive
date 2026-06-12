---
title: "[XP] Desktop will not load"
date: 2008-11-09
forum: Windows
---

### Post by fiddler616 on 2008-11-09
Hello,
I recently reinstalled Windows XP, and it wanted to update to SP3. However, halfway through the upgrade process, it told me there wasn't enough disk space, and it was going to cancel.

So I loaded up gparted off a Live CD, gave a few GBs to the XP partition, and booted back into Windows....except it wouldn't boot all the way, instead hanging at the blue "welcome" screen. I've tried Safe Mode, Safe Mode with Command Prompt, Last-Known-Good, Debugging Mode--the works, and it always hangs there. After a bit of processor activity, it'll just start flicking the processor light about once a second.

Any ideas?

Thanks.

---

### Post by smoker on 2008-11-09
i think you may have damaged the file table and windows can't find the files it needs where it thinks they should be. try booting into the 'recovery console' from your install cd, and doing a 'chkdsk drive /p /r' without the quotes, and change drive for windows drive, ie, C: if so.

 there's more info here: [http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

---

### Post by fiddler616 on 2008-11-09
> **smoker said:**
> i think you may have damaged the file table and windows can't find the files it needs where it thinks they should be. try booting into the 'recovery console' from your install cd, and doing a 'chkdsk drive /p /r' without the quotes, and change drive for windows drive, ie, C: if so.

 there's more info here: [http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)
Þe problem is I don't have a Recovery Disk per se--when I reinstalled it was a bit hokey, I downloaded and burned [BartPE]("http://www.nu2.nu/pebuilder/") and used þat to launch winnt32.exe from my hard drive.

---

### Post by smoker on 2008-11-09
not sure if you can maybe access chkdsk off the bartpe, may be worth a try booting off it and trying it, if you can open windows explorer, or a cmd window give it a try,

best of luck

---

### Post by fiddler616 on 2008-11-09
> **smoker said:**
> 
best of luck
Thanks, I'm off to go give it a shot. (I'm just savoring my last few minutes of running off a hard drive :) )

---

### Post by fiddler616 on 2008-11-09
Two things:
a) I'm a bad person, and forgot to tell you that the first time I booted XP after not-updating and partitioning it ran CHKDSK (or something similar)
b) Command prompt from BartPE:
```

E:/>chkdsk E: /p /r
Invalid parameter - /p

```
:(

---

### Post by smoker on 2008-11-09
try the /f /r parameter, /p may only be valid in recovery console

---

### Post by fiddler616 on 2008-11-09
> **smoker said:**
> try the /f /r parameter, /p may only be valid in recovery console
Hrm...chkdsk ran great, didn't report any errors or bad sectors or anything....and it's the same problem.
Now that I've looked at it some more, it's not the "welcome" screen it hangs on, it's the very-similar-to-the-welcome-screen blue one with the Windows logo and the two horizontal lines, one ~an inch from the top and one ~an inch from the bottom and the cool gradient.
For all it's worth :)
Thanks for all your help so far, though!

---

