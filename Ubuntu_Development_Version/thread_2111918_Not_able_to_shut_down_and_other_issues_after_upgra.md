---
title: "Not able to shut down and other issues after upgrade from 12.10"
date: 2013-02-03
forum: Ubuntu Development Version
---

### Post by Mr.JJ on 2013-02-03
I was using ubuntu gnome 12.10 and upgraded to dev. version. The upgrade process was smooth and then I added gnome staging repo and upgraded again. This time gnome shell and some other packages were held back, so did a dist-upgrade. Only 4 account-plugin-(aim/yahoo/...) were removed and nothing else (metacity is not removed and so as the classic session). 

But now my computer do not shutdown. The screen goes blank just like it is shutting down, but the HDD keep working and laptop is not powered off  (I am able to login and gnome shelll works fine including extensions/run prompt etc.).

Also the auto lock seems to enable both the gnome shell lock screen and also the lock screen from metacity/classic gnome. I get the old ubuntu style password prompt, when trying to unlock. Once I enter the password in that the gnome shell lockscreen kicks in but without the password entry field and no way to unlock/logout/shutdown (Even the panel menu for shutdown is missing). 

Any ideas/help?

---

### Post by Harry33 on 2013-02-03
> **Mr.JJ said:**
> I was using ubuntu gnome 12.10 and upgraded to dev. version. The upgrade process was smooth and then I added gnome staging repo and upgraded again. This time gnome shell and some other packages were held back, so did a dist-upgrade. Only 4 account-plugin-(aim/yahoo/...) were removed and nothing else (metacity is not removed and so as the classic session). 

But now my computer do not shutdown. The screen goes blank just like it is shutting down, but the HDD keep working and laptop is not powered off  (I am able to login and gnome shelll works fine including extensions/run prompt etc.).

Also the auto lock seems to enable both the gnome shell lock screen and also the lock screen from metacity/classic gnome. I get the old ubuntu style password prompt, when trying to unlock. Once I enter the password in that the gnome shell lockscreen kicks in but without the password entry field and no way to unlock/logout/shutdown (Even the panel menu for shutdown is missing). 

Any ideas/help?

Force it to shutdown or reboot.
You can press the power button for 5 sec or remove the battery.
Then start the gnome session again.

---

### Post by Mr.JJ on 2013-02-04
Of course I am doing just that. I am asking what caused it or how to resolve it properly (not a quick fix). May be the question was not worded correctly. 
Also why the metacity password prompt kicks in in the lock screen?

---

### Post by Harry33 on 2013-02-04
> **Mr.JJ said:**
> Of course I am doing just that. I am asking what caused it or how to resolve it properly (not a quick fix). May be the question was not worded correctly. 
Also why the metacity password prompt kicks in in the lock screen?

Does your setup work OK, if you purge all additional PPA's and use only official RR repos?

---

### Post by Mr.JJ on 2013-02-04
Yes, the session works fine. Shell 3.7.4, nautilus 3.7.4, USC, everything is here and working good. The login process also without issues (It takes more time than 12.10 and there is a slight flickering in between but nothing major)

Even in the lockscreen, if I lock myself from the menu the unlock works fine. But If I leave it untouched and the auto lock kicks in thats when the fallback style password prompt shows up. Also, as you said, the restart works fine only the shutdown has issue.

Does the (old) gconf settings has any impact on shutdown? Or is it something to do with the kernel (3.8.0-4 generic)?

---

