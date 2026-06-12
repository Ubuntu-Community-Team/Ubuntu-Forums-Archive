---
title: "How do you consolidate your networks into one?"
date: 2006-11-09
forum: Windows
---

### Post by user1397 on 2006-11-09
if i go to network places, and click on "view workgroup computers" and then I click on "Microsoft Windows Network", i see that there are 3 total networks at my home.  in one, there are 3 computers; my mom's, my dad's, and my sisters'.  in another, only my computer shows.  in yet another, my brother's macbook is the only one there.

how can i have just one network, so that all of the computers in my house are under one network?

---

### Post by user1397 on 2006-11-10
nothing? :(

---

### Post by deanlinkous on 2006-11-10
set the same workgroup name on every computer

---

### Post by user1397 on 2006-11-10
> **deanlinkous said:**
> set the same workgroup name on every computer
thanks for replying.

so how do you do that?

---

### Post by deanlinkous on 2006-11-10
windows computers?
uh.. system properties--->network identification

---

### Post by user1397 on 2006-11-10
> **deanlinkous said:**
> windows computers?
uh.. system properties--->network identificationah arite thanks.  im starting to forget basic windows stuff...because of all my ubuntu activity:)

---

### Post by deanlinkous on 2006-11-11
yea, I had to think for a while myself! No idea about the mac??

---

### Post by user1397 on 2006-11-11
> **deanlinkous said:**
> yea, I had to think for a while myself! No idea about the mac??actually, i remember setting up a different network for the mac, i just didn't think what it was at the time.  if i look around in the preferences, im sure i can fix it for him.  thanks again

---

### Post by deanlinkous on 2006-11-11
no probs! It takes all of us working together to remember how that *other* OS works. ;)

---

### Post by user1397 on 2006-11-11
> **deanlinkous said:**
> no probs! It takes all of us working together to remember how that *other* OS works. ;)yea i know, its as if the "easy" OS is getting harder as time goes by...o well! :)

---

### Post by user1397 on 2006-11-19
does anyone know how to do this on a mac?  (i didnt want to start a whole new thread just for that)

---

### Post by deanlinkous on 2006-11-19
Open the Directory Access utility (under Applications -> Utilities).

If the window is locked (padlock closed on the lower left), click on the padlock to unlock it.

Select SMB and click Configure...

Type in the name of the desired Windows workgroup in the Workgroup field, enter a WINS server (if appropriate) and click OK, then Apply.

********google guessing**********

---

### Post by user1397 on 2006-11-19
> **deanlinkous said:**
> Open the Directory Access utility (under Applications -> Utilities).

If the window is locked (padlock closed on the lower left), click on the padlock to unlock it.

Select SMB and click Configure...

Type in the name of the desired Windows workgroup in the Workgroup field, enter a WINS server (if appropriate) and click OK, then Apply.

********google guessing**********k, thanks.

---

