---
title: "Firewire...."
date: 2008-06-02
forum: Ubuntu Studio
---

### Post by Shugs81 on 2008-06-02
reet.... got a laptop using 4 pin firewire... was thinking about getting an expresscard with a 6 pin firewire port so that i don't need to plug in the firewire card...

any suggestions? would i get better results from my internal 4 pin firewire port or from an external 6 pin port via express card?

---

### Post by ronjouch on 2008-06-02
Getting an ExpressCard isn't necessary and won't bring better perfs. Just provide proper alimentation for your 4pin card and you'll be okay. What's more, adding an ExpressCard would add one more device to cope with.

And even for 6pin FW, it is advised to bring power through separate supply (I do it with my FA66).

Think of the ability of power through the firewire bus as a bonus, not an obligation.

---

### Post by prismatic7 on 2008-06-02
> **Shugs81 said:**
> reet.... got a laptop using 4 pin firewire... was thinking about getting an expresscard with a 6 pin firewire port so that i don't need to plug in the firewire card...

any suggestions? would i get better results from my internal 4 pin firewire port or from an external 6 pin port via express card?

Much more trouble than it's worth. FreeBoB only seems to evaluate devices on the first firewire hub, so you'd need to disable the internal firewire device to get your ExpressCard to work. Furthermore - and I don't necessarily expect this to happen, but consider it cautionary - I have an ExpressCard (because my internal RICOH FW doesn't work) and I have yet to convince it to play well with my Saffire LE. I think this may be to do with IRQ handlers, but that's a whole other topic of discussion.

Seriously, I think with the current state of FW audio support the rule should be 'If it works, don't fix it'.

---

