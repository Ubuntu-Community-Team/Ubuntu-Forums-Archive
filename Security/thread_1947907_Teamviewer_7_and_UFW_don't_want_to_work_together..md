---
title: "Teamviewer 7 and UFW don't want to work together."
date: 2012-03-27
forum: Security
---

### Post by IChooseLife on 2012-03-27
I set up the firewall as per: [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

I'm setting this laptop up for an uncle who is just going to be using this computer for internet surfing and maybe some light word processing. 

I installed Teamviewer 7 prior to setting up the firewall and everything worked fine. I installed it in case he needed help navigating Ubuntu or ran into some problem. Anyways, after I set up UFW I couldn't connect to the laptop anymore from my home computer.

Apparently as long as I have port 80 open on outgoing it should be fine according to this: [http://www.teamviewer.com/en/help/334-Which-ports-are-used-by-TeamViewer.aspx](http://www.teamviewer.com/en/help/334-Which-ports-are-used-by-TeamViewer.aspx)

I opened that port during the tutorial above, but Teamviewer will still not allow connections to it. Any help and/or ideas would help, thanks in advance.

Using Ubuntu 11.10 on the laptop.

---

### Post by IChooseLife on 2012-03-27
Never mind I fixed this monster I opened port 5938 TCP outbound and it fixed it.
:guitar:

---

