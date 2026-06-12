---
title: "Ardour will not play"
date: 2010-01-15
forum: Ubuntu Studio
---

### Post by scovo78 on 2010-01-15
Ever since I upgraded to Karmic Koala, Ardour will no longer play. I have several projects from before I upgraded and none of them will play nor record, and also new projects will not play or record. Any ideas? The stop button is lit up constantly.

---

### Post by Stochastic on 2010-01-16
My first instinct is that this is a 'strange upgrade' bug.  I have not heard of any similar behavior reports.

-Have you tried uninstalling ardour and re-installing it?  
-Can you post the output of 'apt-cache policy ardour'?
-Does ardour's ins/outs appear in qjackctl or patchage?
-What happens if you start the jack transport then try playing in ardour?
-Do you have any PPA links in your repository sources?
-What process did you use to upgrade to Karmic and from which version did you upgrade?
-If you start ardour from a terminal do you see any error messages in that terminal?

---

