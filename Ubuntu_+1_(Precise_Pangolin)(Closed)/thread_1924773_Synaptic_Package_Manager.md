---
title: "Synaptic Package Manager"
date: 2012-02-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Bobhuber on 2012-02-13
Any one have any idea as to when the Quick Filter search function in synaptic will be
 fixed ? Still not working on my system and it's been quite a while now with quite a few updates. Is this a Nvidia problem ? Just assuming everyone else still has the problem ?

---

### Post by cariboo on 2012-02-13
> **Bobhuber said:**
> Any one have any idea as to when the Quick Filter search function in synaptic will be
 fixed ? Still not working on my system and it's been quite a while now with quite a few updates. Is this a Nvidia problem ? Just assuming everyone else still has the problem ?

Have patience, it will be fixed before the final release. :)

---

### Post by dino99 on 2012-02-13
there is 2 close pending bugs with stacktraces, so it will be fixed. Its not a big deal and devs have greater priorities right now. You still can use the "search" icon, or simply browse the archives.

---

### Post by Harry33 on 2012-02-14
There is new update in Precise repos very soon 
to fix the guick search function.

Here:
[https://launchpad.net/ubuntu/precise/+source/synaptic/0.75.5~exp6](https://launchpad.net/ubuntu/precise/+source/synaptic/0.75.5~exp6)

> synaptic (0.75.5~exp6) experimental; urgency=low
  * unless the config option "Synaptic::InlineScreenshots" is set
    to true do not show the tiny screenshot thumbnails inline but
    instead download the big screenshot and show it in a window when
    clicking on the "Show screenshot" button
  * gtk/gtkbuilder/window_main.ui:
    - fix "can_focus" property of entry_fast_search from false to
      true. Looks like glade messed this up.
 -- Michael Vogt <email address hidden>  Mon, 13 Feb 2012 17:50:45 +0100

---

### Post by dino99 on 2012-02-14
> **Harry33 said:**
> There is new update in Precise repos very soon 
to fix the guick search function.

Here:
[https://launchpad.net/ubuntu/precise/+source/synaptic/0.75.5~exp6](https://launchpad.net/ubuntu/precise/+source/synaptic/0.75.5~exp6)

Quick Filter is back :) (need to close then reopen synaptic)
As the crash looks close, maybe its fixed too, wait & see.

---

### Post by dino99 on 2012-02-14
Still get crash with latest exp6 :(

---

### Post by PaulW2U on 2012-02-14
> **dino99 said:**
> Still get crash with latest exp6 :(

Yes, me too. :(

Three updates out of four have ended with synaptic crashing.

---

### Post by Harry33 on 2012-02-14
Here also, crashing.

---

### Post by Quackers on 2012-02-14
Mine crashes, but only sometimes. Other times it will refresh and stay running.

---

### Post by ventrical on 2012-02-14
Yep.. crashes just after reload.

---

### Post by Harry33 on 2012-02-14
Yes it still crashes all right, but this update (0.75.5~exp6) was about quick search.
And that one works now.

---

