---
title: "[SOLVED] kdesudo sudo firefox &amp;amp;"
date: 2007-11-04
forum: Ubuntuzilla
---

### Post by Fintan on 2007-11-04
HI out there, I just got a update message to update FF tp version 2.0.0..9
running:kdesudo firefox & in a terminal (gutsy kubuntu) openss FF fine but the update firefox line is blended out. I understand this the defautlt ubuntu setting. Fine.

When I restart FF as user then I get this error message: "component returned failure code:0x80004005 (NS_ERROR-FAILURE)[NS|StringBundle.formatStringFromName]

FF works fine (at least for now) after clicking on OK but how do I get rid of this message?

Any ideas?

---

### Post by nanotube on 2007-11-05
let's clarify something first...

are you rinning the firefox as installed with ubuntuzilla, or the official ubuntu repository version?

---

### Post by Fintan on 2007-11-05
Yes I am. I found the reason for the error message. It was forecasterfox enhanced. I don't know why but it seams to be borked. So deleted the forecaster file from /home/username/.mozilla/firefox/defaults...... and reinstalled. It seems to work fine now.

Thankx al lot :)

---

### Post by nanotube on 2007-11-05
cool :)

---

