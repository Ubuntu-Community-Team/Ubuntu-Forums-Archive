---
title: "Software Updater upgrades without asking for the password"
date: 2017-08-08
forum: Ubuntu Development Version
---

### Post by Chanath on 2017-08-08
I always update/upgrade from the terminal. This time I saw the Software Updater wiggling on the (autohidden) Unity Launcher in Ubuntu 17.10, so I clicked on it to start upgrading. Only, it didn't ask for the password. Is it the default behaviour of the Software Updater? Isn't any app changing the installation without getting permission a security problem?

---

### Post by deadflowr on 2017-08-08
> Only, it didn't ask for the password. Is it the default behaviour of the Software Updater?
Yes.
Because the updates you are installing are for existing packages on your system.
If the updater required installing any new packages, then you would have to authenticate those.

This has been the behavior for years now.

If however you see any updates which were never installed on the system before included, then that may be a bug.
But the behavior you see is normal and expected.

Edit: adding this nugget:
[https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates]("https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates")

---

### Post by Chanath on 2017-08-08
> **deadflowr said:**
> 
Edit: adding this nugget:
[https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates](https://wiki.ubuntu.com/SecurityTeam/FAQ#Update_Manager_doesn.27t_prompt_for_security_updates)

Thanks. I read that link. Not very convincing reasoning, at least for me. I'll stick to upgrading through the terminal.

---

