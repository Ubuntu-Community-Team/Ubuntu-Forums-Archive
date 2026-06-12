---
title: "Shell Script problem using double quotes inside double quotes and storing in variable"
date: 2013-02-19
forum: Ubuntu Application Development
---

### Post by sanjay singh on 2013-02-19
Hi,
    I have a problem in using double quotes inside double quotes as follows:--
        **s1="-r printer:sanjay=\"HP LaserJet 1018\""**

  Whenever i am using the **value of variable s1** inside command as follows:--
        ** rdesktop -u administrator -p admin_ $s1_ ip-address**

   the command is not executing as expected..

But if i am writing it directly like:--
**rdesktop -u administrator -p admin -r printer:sanjay="HP LaserJet 1018"ip-address**

its working fyn..

plz help me to getting out of this stuff..

---

### Post by sandyd on 2013-02-19
**closed** -please do not post multiple threads on the same subject as this dilutes community effort.

Thanks!

[http://ubuntuforums.org/showthread.php?t=2117719](http://ubuntuforums.org/showthread.php?t=2117719)

---

