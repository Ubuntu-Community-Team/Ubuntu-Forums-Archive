---
title: "Duplicate plugins do not work"
date: 2008-11-25
forum: Ubuntu System Panel
---

### Post by santiagoward2000 on 2008-11-25
Hi!!
I've been playing around with my USP's config. Now I have 3 tabs, and in all of them I put a panel with the User and System Management plugins (duplicated in all 3 tabs). The thing is that these plugins only work on the upper tab, but on the other two, when I click on any button, nothing happens. I've also noticed that the fonts on the non-working tabs look a little different. The other plugins I have on those tabs work fine.
Is this a bug or something?
Thanks!!

---

### Post by Malac on 2008-11-26
> **santiagoward2000 said:**
> Is this a bug or something?
Yep you found another :)
I'll take a look as soon as possible.

---

### Post by santiagoward2000 on 2008-11-26
> **Malac said:**
> Yep you found another :)
I'll take a look as soon as possible.

YEAY! I found another one! \\:D/
If you need me to test something, just ask! :)

---

### Post by santiagoward2000 on 2009-02-11
Hi again!
I just wanted to add some new info. After I modified the **system_management.py** file to get it working as on Hardy, I see this only works on the working tab. The other 2 they still look as they do on Intrepid, with both **End Session** and **Quit...** buttons.
Cheers!

---

### Post by Malac on 2009-02-12
> **santiagoward2000 said:**
> Hi again!
I just wanted to add some new info. After I modified the **system_management.py** file to get it working as on Hardy, I see this only works on the working tab. The other 2 they still look as they do on Intrepid, with both **End Session** and **Quit...** buttons.
Cheers!
Yes this is part of the duplicate plugin bug.
It basically just doesn't do any of the code in the duplicated plugins.
I am working on this at the moment but it is proving a pain to defeat.

---

### Post by santiagoward2000 on 2009-02-12
> **Malac said:**
> Yes this is part of the duplicate plugin bug.
It basically just doesn't do any of the code in the duplicated plugins.
I am working on this at the moment but it is proving a pain to defeat.

I'm sorry to hear that. Thanks for all your work!

---

