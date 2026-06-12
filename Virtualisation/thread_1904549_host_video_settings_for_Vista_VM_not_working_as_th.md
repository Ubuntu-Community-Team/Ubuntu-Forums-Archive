---
title: "host video settings for Vista VM not working as they should"
date: 2012-01-04
forum: Virtualisation
---

### Post by jeliocranch on 2012-01-04
I've been running VirtualBox 4.1.6, installed from the website on first Natty then Oneiric.  I had a Win 7-64 VM that was working great on my host when it had 8GB ram, but I had trim down to 4GB, so a 64 bit VM is out of the question.  
I've got a Vista machine now, built with 3D acceleration and 256MB of video ram.  Trouble is, the Vista VM thinks it has only 24MB, non-3D accelerated video.
Anyone have any suggestions?

---

### Post by jeliocranch on 2012-01-05
as an update: I had installed guest additions, but not the "experminental" 3D acceleration.  booting into safe mode and re-installing guest additions worked OK.  so I think its solved, sort of.

---

