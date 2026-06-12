---
title: "System Problem Detected Error"
date: 2013-05-15
forum: Ubuntu Development Version
---

### Post by roly33 on 2013-05-15
I've started getting a System Problem Detected Error today, so I did a full re-Install of 12.10 then upgraded to 13.04 and finally to 13.10 and I still keep getting the error, I even got it on the fresh install of 12.10 and then the upgraded 13.04.  When I click on cancel everything works fine.

I'm at a loss as to what is causing this error message, but according to the Disks App my HDD has got 1 bad sector so wondered if that could be causing the problem?

Roland

---

### Post by grahammechanical on 2013-05-15
You will get those in Saucy because Apport is enabled by default in the development branch. You should have been given a Details button that would have showed you what exactly had crashed. It should also have given you an opportunity to report the crash on Launchpad (Lauchpad account needed). If the bug has already been reported you may be directed to the existing bug report so that you can confirm that it effects you also. Or the bug may be so well known on Launchpad that you confirmation is not necessary.

But as you have no information as to what is crashing there is nothing that anyone here can advise you on.

Regards.

---

### Post by ibjsb4 on 2013-05-15
Sounds like your now on 13.04.

If everything is working then you can just disable apport.

[https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F](https://wiki.ubuntu.com/Apport#Why_is_it_disabled.3F)

[http://ubuntuforums.org/showthread.php?t=2053494&p=12219467&viewfull=1#post12219467](http://ubuntuforums.org/showthread.php?t=2053494&p=12219467&viewfull=1#post12219467)

---

### Post by cariboo on 2013-05-15
> **roly33 said:**
> I've started getting a System Problem Detected Error today, so I did a full re-Install of 12.10 then upgraded to 13.04 and finally to 13.10 and I still keep getting the error, I even got it on the fresh install of 12.10 and then the upgraded 13.04.  When I click on cancel everything works fine.

I'm at a loss as to what is causing this error message, but according to the Disks App my HDD has got 1 bad sector so wondered if that could be causing the problem?

Roland

Usually it's better to see what is causing the error message, by clicking the details button, then checking here, or in General Help for released versions to see if there is a solution to the problem, instead of doing multiple installations. During the development cycle apport and whoopsie are enabled, and will throw up error message, for almost any error.

---

