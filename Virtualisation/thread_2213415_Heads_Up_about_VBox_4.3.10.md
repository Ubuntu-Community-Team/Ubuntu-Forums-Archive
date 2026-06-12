---
title: "Heads Up about VBox 4.3.10"
date: 2014-03-26
forum: Virtualisation
---

### Post by JKyleOKC on 2014-03-26
Just a word of warning for VBox users seeing an upgrade to 4.3.10 that just became available: Be sure that all of your VMs are in "powered down" state rather than "saved" before installing the upgrade. I forgot to do so, and when I went to restore one of the saved VMs, the restore process went crazy. It stopped at 0%, then after a fairly long wait re-started itself without stopping the first instance, went to 20%, and froze solid at that point. I had to use the REISUB magic keys to get out of the lockup, and then my eth0 interface disappeared.

Powering down again, completely, and letting the system rest for 10 minutes, brought eth0 back into action, and using the "discard" option on all the "saved" VMs made them usable again, but it was a **very** stressful hour there...

---

### Post by QIII on 2014-03-26
I guess I'm glad I shut them all down in preparation for installing 14.04 on my daily driver and installing VBox 4.3.10.

Sometimes a fella just gets lucky, I suppose.

---

### Post by JKyleOKC on 2014-03-26
> **QIII said:**
> I guess I'm glad I shut them all down in preparation for installing 14.04 on my daily driver and installing VBox 4.3.10.

Sometimes a fella just gets lucky, I suppose.Yep; I knew better, having experienced a similar problem when I moved from 3.x to 4.x, but just didn't think about it soon enough! This time was a lot more scary, though. Glad you lucked out!!!

---

### Post by JKyleOKC on 2014-03-26
**[SIZE=5]CAUTION!!![/SIZE]** I've just tried to restore a saved session, that was saved by 4.3.10 -- and it, too, has frozen at 0% just like the first ones did. Best **NOT** try to save and restore any sessions, if you use 4.3.10, until this gets cleared up!!!

EDIT -- There's a new package available on the Oracle forum that appears to fix the problem, at least it seems to have done so for me though I've not tested all possibilities here yet. Meanwhile be very careful; the new version does not seem to have gotten into the PPA yet...

[COLOR="#FF0000"]2nd EDIT[/COLOR] -- Be sure that the package you install bears the build number "**r93012**" rather than one beginning "r92" to make sure you have the fixed package. It's in the Oracle download site but does not seem to have made it into the PPA just yet. It **does** now work properly with saved VMs, which greatly simplifies my use of them.

---

