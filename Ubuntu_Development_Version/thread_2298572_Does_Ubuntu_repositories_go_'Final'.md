---
title: "Does Ubuntu repositories go 'Final?'"
date: 2015-10-12
forum: Ubuntu Development Version
---

### Post by jimmy-frydkaer on 2015-10-12
If I have Wily Beta 2 installed, and keep it updated will I then end up with a Wily final, or just an updated wily beta? And will the repos be the same in both Beta and Final release?

Or more precise: Will an updated Wily be using the exact same repos as Final will be using?

---

### Post by sudodus on 2015-10-12
The repos will be the same, but some cruft may remain in the installed system from the development phase.

---

### Post by grahammechanical on 2015-10-12
The repositories only get "fixed" or frozen or closed when the version reaches the end of its support life. During the support period updated packages are moved into the repositories. That how we get updates. The code in the ISO image is fixed at the time of release. That is why when we install we tick the box "Install updates." If we do not install updates during the installation there will be updates waiting for us after installation.

The ISO image of 15.10 we get after the 22nd October will not be Beta but Release Candidate from the 15th October. Images get built & tested daily. So the image available on 22nd might be an updated and newly built Release Candidate image.

[https://wiki.ubuntu.com/WilyWerewolf/ReleaseSchedule](https://wiki.ubuntu.com/WilyWerewolf/ReleaseSchedule)

If we had installed the very first wily ISO image and then did nothing to it but update daily we would end up with an updated 15.10 by release day and it will be the same OS 15.10 that is on the released ISO image.

Regards.

---

### Post by jimmy-frydkaer on 2015-10-13
Thanks for the answers 

I have a wily install that I updated from Vivid 'The Debian Way' by editing my /etc/apt/sources.list which always has worked fine - Thanks again for your help.

---

