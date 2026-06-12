---
title: "e-Sword Font Problem"
date: 2007-04-15
forum: Ubuntu Christian Edition
---

### Post by tak1150 on 2007-04-15
A few days ago I all of a sudden lost all the fonts for e-Sword. And the screenshot of it is attached below. Then I tried some of the protocols on this forum for installing e-Sword with wine after I removed e-Sword. I got very desperate and I even backed up /home and re-installed Ubuntu CE 2.2 and installed e-Sword with e-Sword Installer that comes with it. And it still has the same symptom. When you go to "options" "Bible fonts", there are no fonts in the pull-down menu. Somebody help!

Blessings,
Tak

[ATTACH]29801[/ATTACH]

---

### Post by david_kt on 2007-04-15
I have wrote below how to:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

and mine is still working fine up to know, without any problem. I have upgraded wine from 0.9.32 to 0.9.35 without any problem.

Please let me know if you still have problems.

DK

---

### Post by tak1150 on 2007-04-15
Thanks for your reply. I did a clean install of Ubuntu CE 2.2 and e-Sword from the e-Sword installer and it works (ie BEFORE I do any of the updates w/ update-manager). I'm a bit nervous to try and update things; especially wine. But we will see...

---

### Post by mhancoc7 on 2007-04-16
> **tak1150 said:**
> A few days ago I all of a sudden lost all the fonts for e-Sword. And the screenshot of it is attached below. Then I tried some of the protocols on this forum for installing e-Sword with wine after I removed e-Sword. I got very desperate and I even backed up /home and re-installed Ubuntu CE 2.2 and installed e-Sword with e-Sword Installer that comes with it. And it still has the same symptom. When you go to "options" "Bible fonts", there are no fonts in the pull-down menu. Somebody help!

Blessings,
Tak

[ATTACH]29801[/ATTACH]

This must be an issue with the latest updates to wine. I just noticed it in my IEs4Linux. I just checked my e-Sword and same thing. I will try to get this fixed asap. 

Thanks, Jereme

---

### Post by david_kt on 2007-04-16
> **tak1150 said:**
> Thanks for your reply. I did a clean install of Ubuntu CE 2.2 and e-Sword from the e-Sword installer and it works (ie BEFORE I do any of the updates w/ update-manager). I'm a bit nervous to try and update things; especially wine. But we will see...

I did manual installation as until now I am still using original ubuntu. There is no problem with wine 0.9.35. But, if you are using a lot of programs (or even just one program) in wine but you are not sure how to troubleshoot wine, just do this:

1. Open synaptic package manager
2. click wine
3. on synaptic menu, click package, and lock version.

In this case, your wine will not be automatically updated (unless you upgrade from terminal). The automatic upgrade would skip wine as it is locked.

Regards,
DK

---

### Post by mhancoc7 on 2007-04-16
Ok, after upgrading to 0.9.35 the problem seems to be fixed.

Jereme

---

### Post by tak1150 on 2007-04-17
> Ok, after upgrading to 0.9.35 the problem seems to be fixed.

I'll second that. Thanks guys for looking into this.

---

