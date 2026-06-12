---
title: "Custom keyboard shortcuts"
date: 2013-04-02
forum: Ubuntu Development Version
---

### Post by Elfy on 2013-04-02
I've had to set up keyboard shortcuts in system settings for media control.

I have to reset them on each boot.

Any ideas how to get them to work properly?

---

### Post by dino99 on 2013-04-02
Thats a real issue now, as gsettings already write/overwrite so many shortcuts for GS & Unity (becomes a nightmare to remember that crappy design :mad: )

---

### Post by Elfy on 2013-04-02
No idea then - just a random comment.

---

### Post by mc4man on 2013-04-02
I've had a couple of custom shortcuts set for a couple of months, they stay persistent (2 in keyboard, one in compiz/commands
May be worth posting one or two that don't stay for you, binding & command, former May be more relevant.
(& what session you use, thread tagged ubuntu so would assume unity or gnome-shell

---

### Post by Elfy on 2013-04-02
This is Unity - all completely updated. 

All shortcuts that are failing are for Sound and Media

Alt +F5 - Previous
Alt +F6 - Stop
Alt+F7 - Play/Pause
Alt+F7 - Next

All work fine when I've rebooted, gone back to settings and reset them.

If I had a keyboard with all media keys I guess they'd work, the vol up/down/mute all work fine, but they're still default

---

### Post by mc4man on 2013-04-02
> **Elfy said:**
> This is Unity - all completely updated. 

All shortcuts that are failing are for Sound and Media


See what you mean, see 2 workarounds atm
1. use an add. modifier, ie., shift+alt+F5
2. open ccsm > unity > general > 'key to show hud' & either disable entirely or give Hud a new key that's  'free'

---

### Post by Elfy on 2013-04-02
I'll try disabling HUD from the moment, if that 'fixes' it I'll look for a 'free' key.

Not going to try using an additional modifier - I want a combo I can use with one hand without anymore thinking than I already have to do  :)

WIll report back once I've rebooted.

---

### Post by mc4man on 2013-04-02
Giving it a moments add. thought - 
You could also just not use alt for media sc's, maybe try shift+F5, ect. ??

---

### Post by Elfy on 2013-04-02
> **mc4man said:**
> Giving it a moments add. thought - 
You could also just not use alt for media sc's, maybe try shift+F5, ect. ??

Disabling hud worked it seems. 

I can live with that. 

But the fact that you can't use things for custom shortcuts isn't so good I guess in the long wrong.

---

### Post by mc4man on 2013-04-03
Seems to be longstanding & likely to remain so.
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/964270](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/964270)

 not sure if the last comment works out well or not. (in general that is,

---

### Post by Elfy on 2013-04-03
Thanks for finding that mc4man.

I think I'll go to admincp and add a "Sort of half solved" prefix and mark the thread as such :)

---

### Post by mc4man on 2013-04-03
At least here shift seems to be the best free key, tap for Hud, press for shift
Haven't yet found a conflict, haven't looked too hard..
(**if** there isn't any then would be a better choice for Hud than alt, certainly in context of  an 'unsolvable' bug.

---

### Post by Elfy on 2013-04-03
> **mc4man said:**
> At least here shift seems to be the best free key, tap for Hud, press for shift
Haven't yet found a conflict, haven't looked too hard..
(**if** there isn't any then would be a better choice for Hud than alt, certainly in context of  an 'unsolvable' bug.

Agree with that :)

---

