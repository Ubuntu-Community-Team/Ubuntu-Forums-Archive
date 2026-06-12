---
title: "Evolution Fails To Remember Account Password; Auth Request PopUp on Check Mail"
date: 2014-03-18
forum: Ubuntu Development Version
---

### Post by buzzingrobot on 2014-03-18
Evolution 3.10.4 here on 14.04 is continually popping up an authorization request prompting for the mail server's password.  The "Add to keyring" option is checked.

The requests appear to be in synch with the configured "check for new mail" interval.

The popup also steals focus in that I can't enter text elsewhere -- any app, any workspace -- until I clear it.

I boot with the "No password" option so I dutifully authenticate to the keyring on each log in.

This appears to be an old and venerable annoyance with many old and venerable suggestions to fix it.  None that I've tried work.

I've considered that the server might be flaky. But, it is accessible from other devices when I see the authorization popup.

---

### Post by QDR06VV9 on 2014-03-18
Affects me also.

---

### Post by slickymaster on 2014-03-18
It sounds more like an issue with gnome-keyring, than with evolution itself. Could you install Seahorse and verify that your Default Keyring is unlocked?
Use View->By Keyring menu option in Seahorse (Passwords and Keys) to see your configured keyrings.

---

### Post by QDR06VV9 on 2014-03-18
> **slickymaster said:**
> It sounds more like an issue with gnome-keyring, than with evolution itself. Could you install Seahorse and verify that your Default Keyring is unlocked?
Use View->By Keyring menu option in Seahorse (Passwords and Keys) to see your configured keyrings.

That worked! Have also rebooted to verify! I had to tick the option to unlock while I'm logged in.
Thanks slickymaster.

---

### Post by slickymaster on 2014-03-18
Just glad you got it fixed.

---

### Post by buzzingrobot on 2014-03-18
> **slickymaster said:**
> It sounds more like an issue with gnome-keyring, than with evolution itself. Could you install Seahorse and verify that your Default Keyring is unlocked?
Use View->By Keyring menu option in Seahorse (Passwords and Keys) to see your configured keyrings.

Thanks!  That's working.  I'd looked at Seahorse but ignored the Gnome2 keyring, thinking it was, well, a holdover from Gnome 2.

I noticed that it is locked again after a new session starts.  Normal?

Now to convince Evolution to stop blocking loguts.

---

### Post by slickymaster on 2014-03-18
> **buzzingrobot said:**
> Thanks!  That's working.  I'd looked at Seahorse but ignored the Gnome2 keyring, thinking it was, well, a holdover from Gnome 2.
I noticed that it is locked again after a new session starts.  Normal?
...

Well, you could try to go into seahorse and just clear all your saved logins. After doing that re-enter your login info once more so to save it to your keyring persistently.

---

### Post by chris36 on 2014-07-09
I had the same problem again after a new install. 
The persisting password keyring issue was tyring. I ended up deleting all my keyrings for Evo and started afresh as Evo would ask for each email sign in. This seem to solve the problem.
Thanks for heads up on Seahorse.

---

