---
title: "How I added my computer (firefox + noscript)"
date: 2010-05-01
forum: Ubuntu One (CLOSED)
---

### Post by lidmith on 2010-05-01
Hello. This probably will be obvious to many, but for a noob like me, it took a few minutes to figure out:

When I got to the step of adding my computer on Ubuntu One, noscript seemed to be acting up, so I allowed all the page. This didn't work, so I allowed scripts globally. This didn't work either, but there was an "Options" button on the blocked script notification. This button lead me to a screen of noscript options. 

In order to add my computer, I had to uncheck "Enable ABE", clicked "OK", and clicked the "add my computer" button in the browser window.

Afterwards, remember to disable scripts and also, to re-enable ABE (right click the noscript icon, select options, check "Enable ABE").

If you've left the page to add your computer, and are unable to get back to it (like I was), then the faq suggests putting this in your terminal window:

u1sdtool -q; killall ubuntuone-login; u1sdtool -c

Then you can select Ubuntu One from the "me" menu, and it will hopefully open the page again.

---

### Post by mixint27 on 2010-05-24
I was having trouble with this last night. Thanks so much for the fix!!

---

