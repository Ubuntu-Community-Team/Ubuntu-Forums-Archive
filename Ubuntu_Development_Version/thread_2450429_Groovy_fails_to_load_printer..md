---
title: "Groovy fails to load printer."
date: 2020-09-13
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2020-09-13
Previous daily iso's had no problem installing printer drivesr for my HP OfficeJet Pro 8740.  Did a fresh install of today's daily and can no longer install printer, error message is "Failed to install new printer".  Any workarounds?

Henry

---

### Post by Hewjr100 on 2020-09-13
Gave up, went back to 20.04 until Groovy is GA.  Keeping open just in case same issue with final.

Henry

---

### Post by Hewjr100 on 2020-09-19
Update:  Groovy does in fact install drivers for HP OfficeJet Pro 8740, it just does not show in the list of printers, and still indicates that installation failed.  Howver it shows up in the list of printers in Document Scanner app, and does scan correctly.  Also printing from Libreoffice also is working fine.

Henry

---

### Post by zebra2 on 2020-09-26
Since you know that it is working you may want to try an install with "system-config-printer" which is the retired printer config.  I had to use that to solve my Brother printer problems. It still works just fine but you will be doing it "the old way". Nothing odd about that in linux.

---

