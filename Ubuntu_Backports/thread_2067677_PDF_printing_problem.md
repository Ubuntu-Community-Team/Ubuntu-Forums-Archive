---
title: "PDF printing problem"
date: 2012-10-07
forum: Ubuntu Backports
---

### Post by GijsWillem on 2012-10-07
Hello Forum,
I am stuck with a PDF printing problem. I am using Ubuntu 12.04 and have a HP LaserJet 1000 and a Samsung SCX 4300 connected.
Both printers work fine when printing anything using Libreoffice.
However if I try to print using acrobat I get following error message:

The following error occurred while printing...
'/usr/local/bin/lpr: 15: /usr/local/bin/lpr: /usr/local/bin/lpr.app: not found'

Anyone out there who can help me with a solution here?

many thanks
Gijs

---

### Post by TenPlus1 on 2012-10-07
You could try using a different PDF program to print in the meantime like epdfview or evince...

---

### Post by GijsWillem on 2012-10-08
Hello TenPlus1

I have tried bot viewers as you suggested but both are viewers only who unfortunately don't let me print any of the content. Maybe I miss something but in this form they're not very usable for me.
Anyone out there with a suggestion?
BTW I looked in the /usr/local/bin/ directory and I can't find the lpr.app file
Any suggestion here?

Many thanks

Gijs

---

### Post by cwsnyder on 2012-10-08
In evince, did you try the File >> Print menu item, or were you looking for an icon?  Or was it not printing when you tried File >> Print?

---

### Post by GijsWillem on 2012-10-09
Hello cwsnyder,
I looked for an icon which I evidently could not find. Classic beginners error. 
Using the file print menu it works fine on both printers.
So I removed Acrobat and will use the other tools.
Many thanks for the help here.
Problem closed

Gijs

---

