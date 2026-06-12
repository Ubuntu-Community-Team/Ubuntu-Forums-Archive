---
title: "Login Loop On Removal of Fish Shell"
date: 2021-03-30
forum: Ubuntu/Debian BASED
---

### Post by kingfu on 2021-03-30
I'm running ubuntu 20.10 with regolith linux on top. Recently ran an apt update which caused Fish shell to go mental, every shell command met with pages and pages of incomprehensible errors. Even scrolling through the command history would spit out pages of errors. OK fine, uninstall Fish and return to bash. I think this is where I messed up as I forgot to run **chsh** first. I reboot, get past the disk unlocker and loading screen and am left with a blank screen, no login prompt. Run recovery, drop into root shell and it's complaining it can't find fish shell. I run a live usb, check fish isn't in```
 /etc/shells .bashrc .profile
```, check **/etc/passwd** and replace fish with ```
root:x:0:0:root:/root:/bin/bash

```

Reboot and once again I can't make it to a login screen am left with the blank screen. If I ctrl-alt-F3 and drop down into shell I get a login prompt, enter my username + pass and for a micro second I'm shown the cli welcome screen before being taken back to the login prompt.

I've pretty much ran out of ideas at this point and would appreciate some guidance?

---

### Post by TheFu on 2021-03-30
Ubuntu doesn't allow root logins directly.  We use and expect sudo to be used. No direct root access.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

If you want to use fish as the shell, don't do it for root and I'd think using it for any account with sudo would be problematic too.

Depending on other issues, the only solution might be to get your backups out and perform a system recovery following whatever method your backups require.  Mine begin with a fresh OS install.

---

