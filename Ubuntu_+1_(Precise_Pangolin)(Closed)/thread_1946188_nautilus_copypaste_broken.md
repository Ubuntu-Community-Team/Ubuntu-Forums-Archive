---
title: "nautilus copy/paste broken"
date: 2012-03-24
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by dino99 on 2012-03-24
the "paste to that folder" is always greyed.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/963784](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/963784)

---

### Post by lucazade on 2012-03-24
affects me as well.. confirmed

---

### Post by mc4man on 2012-03-24
is it greyed out & doesn't work or greyed out & will work if clicked?

In unity* the later happens at random quite often - had a bug until someone screwed up the report to the extent it got invalidated, never bothered to refile (just one in a long list of minor inconsistencies that continue to plague 12.04

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/933744](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/933744)

---

### Post by dino99 on 2012-03-24
> **mc4man said:**
> is it greyed out & doesn't work or greyed out & will work if clicked?

In unity* the later happens at random quite often - had a bug until someone screwed up the report to the extent it got invalidated, never bothered to refile (just one in a long list of minor inconsistencies that continue to plague 12.04

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/933744](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/933744)

hm, Seb seems nervous sometimes :( As Bilal says that compiz/unity  cant be blamed, then cant thinks about something else but nautilus itself.

im logged as gnome-classic (without effects) and the menu item is always greyed out and never works

note: will not refer to your report because of Seb, but looks similar except that here its not random.

---

### Post by lucazade on 2012-03-24
here is always greyed out but works normally when clicked.
this happens in every sessions.

---

### Post by mc4man on 2012-03-24
> **dino99 said:**
> hm, Seb seems nervous sometimes :( As Bilal says that compiz/unity  cant be blamed, then cant thinks about something else but nautilus itself.

im logged as gnome-classic (without effects) and the menu item is always greyed out and never works

note: will not refer to your report because of Seb, but looks similar except that here its not random.

I wouldn't - no sense your bug getting off-tracked. I've got a new install, will have to try Classic/no effects, ect.

(Way OT - here's a report that is of absolutely no importance, only did to see what would happen, I actually now find it somewhat amusing - background - RT was in the group that split off from FFmpeg to form Libav
[https://bugs.launchpad.net/bugs/939863](https://bugs.launchpad.net/bugs/939863)

---

### Post by dino99 on 2012-03-24
from synaptic i've purged *compiz* then reinstall it. Then closed nautilus, reconfigure it and log out/in again as gnome-classic. And that menu item is no more greyed out :) and copy/paste works now again.

---

### Post by lucazade on 2012-03-24
> **dino99 said:**
> from synaptic i've purged *compiz* then reinstall it. Then closed nautilus, reconfigure it and log out/in again as gnome-classic. And that menu item is no more greyed out :) and copy/paste works now again.

lol... well spotted!
god bless compiz :/

---

### Post by dino99 on 2012-03-24
> **lucazade said:**
> lol... well spotted!
god bless compiz :/

thats against Bilal comments :( (which is fully skilled)
so  might be again some borked settings inside the hidden files (as usual :()

now i'm wondering about the report :( should i set it as invalid ? whats about your system Luca ?

thanks for the heads up mc4man :)

---

### Post by mc4man on 2012-03-24
In my orig. *which was at random, it affected both unity & unity-2d which would seem to preclude compiz as the problem

At this point who knows other than it still does occur.

---

### Post by FulciLives on 2012-03-24
Just wanted to point out that the PASTE is often "greyed out" but I've never had a problem using it.

In other words despite being "greyd out" it still seems to work A-OK for me.

Ubuntu 12.04 Beta 1 32-Bit Unitiy 3D

---

### Post by cariboo on 2012-03-24
> **FulciLives said:**
> Just wanted to point out that the PASTE is often "greyed out" but I've never had a problem using it.

In other words despite being "greyd out" it still seems to work A-OK for me.

Ubuntu 12.04 Beta 1 32-Bit Unitiy 3D

There is no Paste command,  The only problem I've had with the context menu, is very rarely the Rename command is greyed out, but still works.

I tried to create a screenshot, but the menu won't show when I do.

---

### Post by mc4man on 2012-03-24
Here it does occur more often on 'rename' than anything else & is something that just 'happens' on ocaasion. Never saw any way to yet to cause.

[Ex. of the 'paste' one]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/933744/+attachment/2746454/+files/Screenshot%20at%202012-02-16%2015%3A36%3A21.png"), had copied the document, was trying to paste onto Desktop

Reopened the bug previously mentioned though it's not that big a deal & maybe will just go away

---

