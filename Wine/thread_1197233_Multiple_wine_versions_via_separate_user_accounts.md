---
title: "Multiple wine versions via separate user accounts?"
date: 2009-06-25
forum: Wine
---

### Post by myrtle1908 on 2009-06-25
I would like to know if the following is possible.  I'm not at home so cannot try it for a while.

I have wine 0.9.15 installed in my current user account home directory ie ~/.wine.  I need 0.9.15 as it is the only version which seems to work well for me with Infinity Engine (IE) games eg. Baldur's Gate 1, BG2 etc.

If I were to create a new user account and login as the new user would I be able to install a newer wine without affecting my 0.9.15 for the other user?

Thankyou

---

### Post by jerrrys on 2009-06-25
how bout this instead

[http://ubuntuforums.org/showthread.php?t=942269](http://ubuntuforums.org/showthread.php?t=942269)

---

### Post by myrtle1908 on 2009-06-25
Thanks jerrrys.  Looks interesting however I don't want to uninstall my existing wine because I've spent so much time configuring and installing several games for 0.9.15.  Unfortunately to use the multi wine version installer I would have to start again.

I suppose I'll just try my other idea with different user accounts etc.  I see no reason why it wouldn't work.  Was just hoping someone could confirm or deny.

Thanks again.

---

### Post by NightMKoder on 2009-06-25
Different user account will give you different PREFIXes (which you don't need an account for; just use `WINEPREFIX=/home/mike/.wine_weird wine notepad`). Having different versions of wine is however considerably harder.

---

