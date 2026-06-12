---
title: "Best &amp; Updated Antivirus"
date: 2015-09-24
forum: Security
---

### Post by BigBig5 on 2015-09-24
I am looking for a really good gui Antivirus software that gets updated often. Is there any that are good?

---

### Post by CharlesA on 2015-09-24
No such thing. ClamAV throws false positives like crazy.

Have a read here:
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by TheFu on 2015-09-24
AV really isn't very useful on Linux systems.
The only reason to run it is:
* Contractual reasons - corporate insurance policies require it "on every computer"
* Lots of file sharing with Windows PCs.

Because of the Unix system architecture, running AV is really best left to the OS, not individual users. That means there isn't a GUI. The AV signatures are automatically updated daily. I've never seen one catch anything - except when running on an email server. We have a low-risk environment, however.  ClamAV is what we use on the email server. Nowhere else.  We don't allow Windows machines direct internet access.

bodhi.zazen's [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) (Sticky thread in the "Security" subForum) explains. The section in there on "**The Windows Mindset**" would be good to start.

---

