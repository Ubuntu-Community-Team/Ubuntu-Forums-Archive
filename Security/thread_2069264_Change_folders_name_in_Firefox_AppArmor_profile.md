---
title: "Change folders name in Firefox AppArmor profile?"
date: 2012-10-10
forum: Security
---

### Post by kleenex on 2012-10-10
Hello, short question: because default Firefox profile allows downloads to [COLOR=SeaGreen]~/Downloads [/COLOR]and uploads from[COLOR=SeaGreen] ~/Public[/COLOR], should I rename these folder names to language which I am using? Let say, that this language is Italy or whatever.

```
**# default **
[COLOR=Blue]owner @{HOME}Public/ r,[/COLOR]

**# change to?**
[COLOR=Blue]owner @{HOME}/Pubblico/ r,[/COLOR]
```

---

### Post by Hungry Man on 2012-10-10
If your @{HOME}Public/ folder is called Pubblico then yes. If not, no need.

---

### Post by kleenex on 2012-10-10
Hi **Hungry Man**! So, If the folders name are different from English (e.g. Public are Pubblico etc.) I should change (in profile of course) these names to language, which I am using, right? Just example to be 100 % sure:
```
**# default entries**...
[COLOR=Blue]owner @{HOME}/Public/ r,
owner @{HOME}/Public/* r,[/COLOR]

**# ...must be changed to**
[COLOR=Blue]owner @{HOME}/Pubblico/ r,
owner @{HOME}/Pubblico/* r,[/COLOR]
```This applies only to programs, that need to have access to user directories, because when it comes to access for example to the [COLOR=Green]/[/COLOR][COLOR=Green]etc/[/COLOR][COLOR=Green]firefox[/COLOR] or [COLOR=Green]/etc/xulrunner-2.0*[/COLOR] directories, the name is everywhere the same, right? I mean English language. As well as the location of files in e.g. [COLOR=Green]/usr/lib/firefox-addons [COLOR=Black]directory. Do I well understand it?
[/COLOR][/COLOR]

---

### Post by Hungry Man on 2012-10-10
Yes. Correct.

Someone should file a bug about this - this should be the default for the profile.

---

