---
title: "Known UID's to avoid in 1-999 range?"
date: 2009-03-02
forum: Server Platforms
---

### Post by mobcdi on 2009-03-02
I'm having trouble installing Plesk9 on ubuntu 8.04 and it seems plesk needs the UID 110 for to be free when installing. I've found a posting that says how to change the UID of an existing account but not what value I should use.

Is there a list of UID values I should avoid (besides those already in my passwd file) or does other software behave better than plesk when installing

---

### Post by samosamo on 2009-03-02
what do you mean "avoid?"  what is using 110 now?

---

### Post by mobcdi on 2009-03-02
> **samosamo said:**
> what do you mean "avoid?"  what is using 110 now?

110 is currently used by polkituser. At this moment the only solution I have to install plesk9 is to free up the uid 110 and hope the install finished without more errors.

I was wondering if it would be ok to select a random 3 digit number for "new" polkituser or is there a chance I will pick another known/required/hardcoded uid

---

### Post by samosamo on 2009-03-02
Wow that sucks.  I wouldn't change polkituser's, since it has some sort of important system function.  This is certainly Plesk's fault. Did it give you an option? Is 110 default?  

I quickly googled to try and help you but could not find a "registry" of userid's.  All I know is to keep users at numbers >1000.  Maybe someone else can be of assistance.

---

### Post by mobcdi on 2009-03-03
Nope Plesk doesn't give the option to pick a uid so its hardcoded in. 

Kinda strange to hardcode something like that but thought I'd ask people who know more about linux then me if it was normal behaviour and what I should do

---

