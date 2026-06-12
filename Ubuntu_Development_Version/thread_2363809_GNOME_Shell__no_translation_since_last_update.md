---
title: "GNOME Shell : no translation since last update"
date: 2017-06-14
forum: Ubuntu Development Version
---

### Post by fthx on 2017-06-14
Hi,

All is in the title ! GS is in English (I'd like French !), as latest 3.24 Evolution but not Terminal or Synaptics or LibreOffice e.g. .
Language prefs (from prefs) crash at startup so I cannot check here.

Could anyone confirm this ?

---

### Post by ventrical on 2017-06-14
You have to install them. Settings/language

---

### Post by fthx on 2017-06-14
Could you read my post before answering ? :mrgreen:

Additionally, all needed French language packs are installed (all was ok before this last GS update). Are you running a non English language ?

---

### Post by ventrical on 2017-06-14
> **fthx said:**
> Could you read my post before answering ? :mrgreen:

Additionally, all needed French language packs are installed (all was ok before this last GS update). Are you running a non English language ?

No .. but I can apply the french language and see what happens .. to try and emulate your problem..nas pas? :)

---

### Post by ventrical on 2017-06-14
Even though I instqlled it crqshed qnd broke:

Even though I installed it crashed and broke.

---

### Post by ventrical on 2017-06-14
> **fthx said:**
> Could you read my post before answering ? :mrgreen:

Additionally, all needed French language packs are installed (all was ok before this last GS update). Are you running a non English language ?

sorry ... didn't see the bottom part.

:)

---

### Post by fthx on 2017-06-15
> ~$ locale
LANG=fr_FR.UTF-8
LANGUAGE=
LC_CTYPE="fr_FR.UTF-8"
LC_NUMERIC="fr_FR.UTF-8"
LC_TIME="fr_FR.UTF-8"
LC_COLLATE="fr_FR.UTF-8"
LC_MONETARY="fr_FR.UTF-8"
LC_MESSAGES="fr_FR.UTF-8"
LC_PAPER="fr_FR.UTF-8"
LC_NAME="fr_FR.UTF-8"
LC_ADDRESS="fr_FR.UTF-8"
LC_TELEPHONE="fr_FR.UTF-8"
LC_MEASUREMENT="fr_FR.UTF-8"
LC_IDENTIFICATION="fr_FR.UTF-8"
LC_ALL=
 
It seems that GS does not pay attention to that, maybe related to the GS language selector crash ?

---

### Post by fthx on 2017-06-15
[https://errors.ubuntu.com/?release=Ubuntu%2017.10&period=week&pkg_arch=amd64](https://errors.ubuntu.com/?release=Ubuntu%2017.10&period=week&pkg_arch=amd64)

this bug has some success...

---

### Post by jbicha on 2017-06-17
> **fthx said:**
> 
Language prefs (from prefs) crash at startup so I cannot check here.

That crash is fixed today with an update to gnome-control-center. Sorry about that!

You'll probably need to use the Language Support app to install the additional language packs since the Settings app [hasn't worked]("https://launchpad.net/bugs/1631750") for installing language packs since 16.04 LTS.

---

### Post by fthx on 2017-06-18
Thanks for the crash fix, I saw that yesterday with your upload.

Definitely, I do not need to install some other French language packs. My system was completely French before latest GS (or GDM ?) update. When I check with Ubuntu's language tool in control center, it shows me some language packs I should install, but only non-related stuff (thunderbird EN, hunspell ZA, etc.). Note that GDM is partially in English too (sign in, cancel buttons, e.g.).

---

### Post by fthx on 2017-06-18
Ok Jeremy, it's for sure a bug in **gnome-shell** package ***ubuntu6**.
The ***ubuntu5 **version is fine, French translations are ok (GS downgraded just now).

Changes link : [http://launchpadlibrarian.net/322719235/gnome-shell_3.24.2-0ubuntu5_3.24.2-0ubuntu6.diff.gz](http://launchpadlibrarian.net/322719235/gnome-shell_3.24.2-0ubuntu5_3.24.2-0ubuntu6.diff.gz)

I can file a bug if you think it's necessary.

---

### Post by copify on 2017-06-18
How can i Help Ubuntu to contribute my language?

---

### Post by jbicha on 2017-06-18
I feel like there's a lot I still don't understand about Ubuntu's translations process, but here's what I think I know:

Generally, packages in universe get their translations directly from the upstream developers. Generally, packages in main get their translations from language packs generated on Launchpad. One benefit to this system is that translations can be updated without upstream having to make a new release.

gnome-shell was recently promoted from universe to main as a requirement for it to be included in the default Ubuntu install.

Generally, the first language pack is not produced until later in Ubuntu's development cycle.

This means that gnome-shell will be untranslated until that language pack is created or some workaround is found. (Because even if you installed the language packs, they still won't have gnome-shell translations until the language packs are generated *after* gnome-shell was in main).

By the way, gdm3 is not in main yet, but most of the user interface comes straight from gnome-shell so that's why you have the new issue on the login and lock screens too.

---

### Post by fthx on 2017-06-18
Ok !
Thanks for the explanation.

---

### Post by cariboo on 2017-06-18
> **copify said:**
> How can i Help Ubuntu to contribute my language?

You can join the translation team here:


[https://wiki.ubuntu.com/Translations/Contact/Teams](https://wiki.ubuntu.com/Translations/Contact/Teams)

---

### Post by jbicha on 2017-06-19
If you want to get involved in translating the default desktop, I recommend that you look into [contributing to GNOME]("https://wiki.gnome.org/TranslationProject") directly. Your work will benefit Ubuntu users and users of all other distros that use GNOME.

Ubuntu has a few unique apps so it's useful to contribute to Launchpad translations. But most universe apps are not translated in Launchpad at all; you will need to contribute the translations to the original projects to get them into Ubuntu. Even for the stuff in main that can be translated at Launchpad, the original "upstream" translations are used as the base.

---

### Post by dino99 on 2017-06-20
> **couponzila said:**
> That is fixed[COLOR=#24292E][FONT=-apple-system] in gnome-3.16 branch, I updated po/POTFILES.in file.[/FONT][/COLOR]

Dont know which distro you are using, but 3.16 is not one of the genuines  [https://launchpad.net/ubuntu/+source/gnome-shell](https://launchpad.net/ubuntu/+source/gnome-shell)

---

### Post by jbicha on 2017-06-22
The first language pack for Artful is being worked on now. Thank you for letting us know about the issue. :p

---

### Post by jbicha on 2017-07-06
New language packs for Artful were released today so I think this issue is SOLVED now.

Thank you for helping to make Ubuntu better by letting us know about this issue!

---

### Post by fthx on 2017-07-06
Yes, all GS is now back in French, except (I can only check what I use !) Evolution which is still in English.
Thanks !

---

### Post by jbicha on 2017-07-06
@fthx, please reboot your computer just in case some Evolution process was still running in the background. If Evolution is still untranslated after that, please file a bug

```
ubuntu-bug evolution
```

Thanks!

---

### Post by fthx on 2017-07-06
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/1702759](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/1702759)

---

### Post by Wise Ferret on 2017-07-07
gnome-shell translation is still broken for me in Hebrew.
My locale is: > LANG=he_IL.UTF-8
LANGUAGE=he:en
LC_CTYPE="he_IL.UTF-8"
LC_NUMERIC=he_IL.UTF-8
LC_TIME=he_IL.UTF-8
LC_COLLATE="he_IL.UTF-8"
LC_MONETARY=he_IL.UTF-8
LC_MESSAGES="he_IL.UTF-8"
LC_PAPER=he_IL.UTF-8
LC_NAME=he_IL.UTF-8
LC_ADDRESS=he_IL.UTF-8
LC_TELEPHONE=he_IL.UTF-8
LC_MEASUREMENT=he_IL.UTF-8
LC_IDENTIFICATION=he_IL.UTF-8
LC_ALL=

This is especially annoying because Hebrew should have right-to-left directionality, and now I have to work with a shell that is aligned in the opposite direction.
I submitted this as [bug #1703010]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1703010").

---

### Post by fthx on 2017-07-08
ok I unslove the thread...

---

### Post by fthx on 2017-07-14
Hi,

Is it normal that Evolution is still not translated after *ubuntu3 bug solving ?

---

### Post by jbicha on 2017-07-14
Yes, you'll need to wait for the next language pack update for both issues (Hebrew for GNOME Shell and translations for evolution).

Hopefully that will be next week and hopefully language packs will then be updated weekly automatically after that for the rest of the artful development cycle.

---

### Post by fthx on 2017-07-14
Ok thanks !

---

### Post by fthx on 2017-07-26
Solved today with new langpacks.

---

