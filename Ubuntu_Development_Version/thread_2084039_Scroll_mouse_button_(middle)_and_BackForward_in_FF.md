---
title: "Scroll mouse button (middle) and Back/Forward in FF"
date: 2012-11-14
forum: Ubuntu Development Version
---

### Post by zika on 2012-11-14
On my previous install of RR (obtained by relentless upgrade from OO) I was using ~/.xbindkeysrc```
# History Back & Forward
"xte 'keydown Alt_L' 'key Left' 'keyup Alt_L' "
b:6
"xte 'keydown Alt_L' 'key Right' 'keyup Alt_L' "
b:7
```and it worked like a charm...
Now, on my new RR install (obtained by clean install of QQ and immediate upgrade to RR) it doesn't. Any ideas? What did I forgot in the meantime...?
(Yes I've changed HUD trigger key...)

---

### Post by MWisBest on 2012-11-15
> **zika said:**
> On my previous install of RR (obtained by relentless upgrade from OO) I was using ~/.xbindkeysrc```
# History Back & Forward
"xte 'keydown Alt_L' 'key Left' 'keyup Alt_L' "
b:6
"xte 'keydown Alt_L' 'key Right' 'keyup Alt_L' "
b:7
```and it worked like a charm...
Now, on my new RR install (obtained by clean install of QQ and immediate upgrade to RR) it doesn't. Any ideas? What did I forgot in the meantime...?
(Yes I've changed HUD trigger key...)

Well I would download a daily Live image of RR rather than doing an upgrade of QQ. Not sure if it is related to your issue, but it's definitely the best way to do it.

---

### Post by zika on 2012-11-15
> **MWisBest said:**
> Well I would download a daily Live image of RR rather than doing an upgrade of QQ. Not sure if it is related to your issue, but it's definitely the best way to do it.As I wrote somewhere here, at the moment I was doing reinstall I've tried daily RR, it just brought me after boot into native old RR on my HDD...
I do not think that that is an issue here, but I might be wrong...

---

### Post by mc4man on 2012-11-15
I have a 2 week old " clean install of QQ and immediate upgrade to RR" & your ~/.xbindkeysrc works fine for back/forward in FF
Tried also on a freshly created add. user & again no issue
Also to note it doesn't matter if the HUD key is changed/removed or not.
(I usually remove HUD as have yet to find I use it much if at all

While likely not of use you could try renaming ~/.config/dconf/user to user.bak, do a log out/in & see
(to restore old user file then rename the new user file to user.bak1 or delete & rename user.bak to user

---

### Post by zika on 2012-11-15
> **mc4man said:**
> I have a 2 week old " clean install of QQ and immediate upgrade to RR" & your ~/.xbindkeysrc works fine for back/forward in FF
Tried also on a freshly created add. user & again no issue
**Also to note it doesn't matter if the HUD key is changed/removed or not.**
(I usually remove HUD as have yet to find I use it much if at all

While likely not of use you could try renaming ~/.config/dconf/user to user.bak, do a log out/in & see
(to restore old user file then rename the new user file to user.bak1 or delete & rename user.bak to userI know, I only wanted to prevent such kind of answers...
We'll see...

---

