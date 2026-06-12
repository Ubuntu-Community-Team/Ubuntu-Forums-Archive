---
title: "System in &quot;spanglish&quot; after update"
date: 2012-04-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ayozito on 2012-04-13
After yesterday update, whole my system is in a mix of spanish and english.

I checked at language supported and at first there was spanish and english activated, but after disable english and apply and restarted, still the system is on spanglish.

Before yesterday there was any problem, whole system was in spanish without problem.

---

### Post by dino99 on 2012-04-13
if you have already fully checked "language" settings inside System Settings menu, then applied to whole system, maybe you have some borked settings : remove .local & .gconf folders inside your /home, they will be cleanly recreated after logout/in.

---

### Post by jbicha on 2012-04-13
English is the fallback language. The final language packs (for the release images) will be generated next week.

Make sure you have the Spanish language packs installed. In System Settings, click Language Support. Spanish should be at the top of your list above English.

---

### Post by ayozito on 2012-04-13
> **ayozito said:**
> After yesterday update, whole my system is in a mix of spanish and english.

**I checked at language supported and at first there was spanish and english activated, but after disable english and apply and restarted, still the system is on spanglish.**

Before yesterday there was any problem, whole system was in spanish without problem.
As I said..

---

### Post by ubuntu27 on 2012-04-14
This happened to me as well. Though in my case it is a mixture of Japanese and English.

I uninstalled the Japanese languages packs, but I still get some Japanese words here and there.


I suspect that this occurred because I uninstalled Japanese when I was using the desktop in Japanese itself. So perhaps, if my desktop was in English when I uninstalled Japanese, none of this would have happened.


I tried deleting .local and .gconf from the home directory, but it did not help.



The workaround for now is to create a new user. (Works)

Another workaround that I believe might work (I did not test), is to install the language pack again (in my case Japanese), restart X server (Log out), and then logging in English again. This time try uninstalling the language packs again. Hopefully it works.

---

### Post by ayozito on 2012-04-14
After today update, again is everything in spanish...

---

### Post by ubuntu27 on 2012-04-17
After installing apps in the terminal, I get this:

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = "ja:es_PE:es_ES:en_US:en",
	LC_ALL = (unset),
	LC_TIME = "en_US.UTF-8",
	LC_MONETARY = "en_US.UTF-8",
	LC_ADDRESS = "en_US.UTF-8",
	LC_TELEPHONE = "en_US.UTF-8",
	LC_NAME = "en_US.UTF-8",
	LC_MEASUREMENT = "en_US.UTF-8",
	LC_IDENTIFICATION = "en_US.UTF-8",
	LC_NUMERIC = "en_US.UTF-8",
	LC_PAPER = "en_US.UTF-8",
	LANG = "ja_JP.UTF-8"
    are supported and installed on your system.
```

Do you guys know how can we modify the language manually? I already uninstalled the language packs for Spanish and Japanese, but it is still showing it.

---

### Post by jbicha on 2012-04-17
You could try clicking the Help button in System Settings>Language Support for a little more info on what those LC fields mean.

---

