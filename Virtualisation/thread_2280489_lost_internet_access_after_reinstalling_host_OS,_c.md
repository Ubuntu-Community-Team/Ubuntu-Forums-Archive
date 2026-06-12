---
title: "lost internet access after reinstalling host OS, can someone help?"
date: 2015-05-31
forum: Virtualisation
---

### Post by stupidquestion on 2015-05-31
I'm running Ubuntu 14.04 in VMWare Player. The OS is Windows which I just reinstalled. Problem is, now the Ubuntu VM has no connection to the internet. In the VM settings, under network adapter, the setting was NAT. If I changed it to Bridged, it wouldn't work either. Under Bridged mode, if I check "Replace physical network connection state", that still doesn't work. If I click "Configure Adapters" under Bridged mode, it doesn't allow me to select any host network adapter. 

Does anyone have some ideas?

---

### Post by coldraven on 2015-05-31
Nope, but I'll bump you to the top :) 
(I only know VirtualBox)

---

### Post by stupidquestion on 2015-05-31
Found the culprit: VMWare Player should be installed As Administrator in Windows. Re-installing with the repair option fixed the problem.

---

