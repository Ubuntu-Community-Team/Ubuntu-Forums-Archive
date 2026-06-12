---
title: "bug reporting - ubuntu-bug?"
date: 2012-05-21
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ubername on 2012-05-21
Hi

Recently I have had a number of situations where the message 'ubuntu 12.10 has encountered an internal error' or similar is displayed (mostly involving indicator-weather, as it happens, but my question is not about that). There is an option to show details, send a report to the developers, and continue. In the past I seem to remember the 'continue' option taking me to a web page where the details of the bug would be displayed and the chance to select an existing bug for which this may be a duplicate. 

Recently (since I upgraded to 12.10 toolchain?) nothing seems to happen after selecting continue - I am not sure whether anything is being reported - no browser opens indicating that a bug is being raised and nothing is appearing on my launchpad account (presuming the system had some way of detecting the bug was already known). Am I doing something wrong or has bug reporting changed in some way?

---

### Post by dino99 on 2012-05-21
some devs are genius :p when its time to set something confusing, like this "continue" button, which means everything except what you are believing ;)

---

### Post by philinux on 2012-05-21
> **ubername said:**
> Hi

Recently I have had a number of situations where the message 'ubuntu 12.10 has encountered an internal error' or similar is displayed (mostly involving indicator-weather, as it happens, but my question is not about that). There is an option to show details, send a report to the developers, and continue. In the past I seem to remember the 'continue' option taking me to a web page where the details of the bug would be displayed and the chance to select an existing bug for which this may be a duplicate. 

Recently (since I upgraded to 12.10 toolchain?) nothing seems to happen after selecting continue - I am not sure whether anything is being reported - no browser opens indicating that a bug is being raised and nothing is appearing on my launchpad account (presuming the system had some way of detecting the bug was already known). Am I doing something wrong or has bug reporting changed in some way?

It should behave like this. [http://ubuntuforums.org/showthread.php?t=1886233](http://ubuntuforums.org/showthread.php?t=1886233)

---

### Post by grahammechanical on 2012-05-21
I find that it asks me if this is a bug due to upgrading. Which of course it isn't as it is an install from the 12.10 daily ISO image.

During the PP cycle I used to get the "we already know about this" message or the "this is due to obsolete packages" message but I have not seen either of these in QQ.

Regards.

---

### Post by mc4man on 2012-05-21
Don't really understand completely here, nor need to but I believe what your currently seeing is related to whoopsie, whoopsie-daisy, & errors.ubuntu.com
In those cases nothing will be shown on screen after the process runs

Whether anything changes in 12.10 around or at A1 don't know, atm bugs can still be filed with ubuntu-bug <whatever>, ex's the software center   & the nvidia ones were

---

### Post by ubername on 2012-05-21
> **philinux said:**
> It should behave like this. [http://ubuntuforums.org/showthread.php?t=1886233](http://ubuntuforums.org/showthread.php?t=1886233)

Cool, thanks

---

### Post by mc4man on 2012-06-01
Should be working now with new apport (2.1.1-0ubuntu2
 > etc/apport/crashdb.conf: Re-enable Launchpad crash reporting again.

---

### Post by jerrylamos on 2012-06-03
> **mc4man said:**
> Should be working now with new apport (2.1.1-0ubuntu2Much better, now even invokes launchpad and will generate a bug.  Well, a lot more of the time than it did before.

Thanks, Jerry

---

