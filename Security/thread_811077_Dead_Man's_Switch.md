---
title: "Dead Man's Switch"
date: 2008-05-28
forum: Security
---

### Post by bcamp929 on 2008-05-28
I am running Ubuntu Desktop 8.04, and I have been looking for days for some sort of "dead man's switch" software for Ubuntu. I have noticed that there are similar programs for Windows. Basically I am trying to protect personal data. I would like to have a script run on, say, the 3rd invalid password that will erase an encrypted disk, or change the password and send it to an email, etc....

 Does anyone know of any scripts or programs for Ubuntu that can do this for me?

PLEASE HELP!!! 

BC

---

### Post by Dr Small on 2008-05-28
It might be possible with some PAM configuration, but I am not that knowledgeable on that subject, so I can't help you there. Maybe someone else know's more about it.

Dr Small

---

### Post by bcamp929 on 2008-05-29
Thank you Dr. Small. This does not look like the right solution for me. Does anyone have any more suggestions???

---

### Post by Monicker on 2008-05-29
I would also look at swatch. It can monitor log files and execute scripts based on patterns found in them.

---

### Post by bcamp929 on 2008-05-30
Thank you so much! I think this is gonna do it, just need to figure out how to configure it now. Thanks again.

---

### Post by brian_p on 2008-05-30
> **bcamp929 said:**
> Thank you so much! I think this is gonna do it, just need to figure out how to configure it now. Thanks again.

In cased swatch doesn't fit your needs there is sec (Simple Event Correlator) to bear in mind.

---

