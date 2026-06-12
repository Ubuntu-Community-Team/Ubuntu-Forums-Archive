---
title: "evolution does not forget password...is it a bug?"
date: 2008-03-11
forum: Security Discussions
---

### Post by gsoundsgood on 2008-03-11
hi there!
i'm a gutsy user, evolution version 2.12.1

i used to keep my password saved in evolution, now trying to improve the level of security, i decided to disable the "remember password" option in the account options of my main e-mail account.

even after a reboot, evolution is not asking for my e-mail account password, and i see it is still stored in my ~/.gnome2_private/evolution file.

i guess i could just delete the two lines of that account from that file...but...isn't it a bug? isn't there a "proper" way to delete my stored password from evolution?

thank you

---

### Post by Oldsoldier2003 on 2008-03-11
> **gsoundsgood said:**
> hi there!
i'm a gutsy user, evolution version 2.12.1

i used to keep my password saved in evolution, now trying to improve the level of security, i decided to disable the "remember password" option in the account options of my main e-mail account.

even after a reboot, evolution is not asking for my e-mail account password, and i see it is still stored in my ~/.gnome2_private/evolution file.

i guess i could just delete the two lines of that account from that file...but...isn't it a bug? isn't there a "proper" way to delete my stored password from evolution?

thank you

you may have to dig around, it sounds like you gave evolution access to your keyring.

---

### Post by gsoundsgood on 2008-03-11
mm...i wouldn't know how to do that (even if i may have done it unwittingly). i'm in ubuntu, not in kubuntu (i have a feeling that keyring management is more straightforward in kubuntu).
anyway, i guess it's no big deal...deleting those two lines just works...

---

