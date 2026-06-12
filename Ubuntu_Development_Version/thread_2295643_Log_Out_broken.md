---
title: "Log Out broken"
date: 2015-09-20
forum: Ubuntu Development Version
---

### Post by sgage on 2015-09-20
When I log out of Gnome Shell, I am dumped to a log in prompt on VT 1.

I can log in there, and then

```
sudo service gdm restart
```

launches a new session (bypassing the greeter).

Anyone else seeing this behavior?

---

### Post by QDR06VV9 on 2015-09-20
Randomly!
On unity(lightdm) it also can be a bit sluggish to login.
Bug Report?

---

### Post by sgage on 2015-09-20
> **runrickus said:**
> Randomly!
On unity(lightdm) it also can be a bit sluggish to login.
Bug Report?

I browsed launchpad but didn't see anything. How do you even file a bug report any more? I couldn't figure out any obvious way...

---

### Post by mc4man on 2015-09-20
Have noticed continuing log in issues that aren't cut & dry. Lately no issue *in general* with log out/in on Ubuntu-Gnome unless I change from Intel to Nvidia or Nvidia to Intel via nvidia-prime. Then a log out/in fails & just either black screens or loops back to greeter. A restart is required to get a login for either.
15.10 is shaping up to be as crappy as 14.10, hopefully 16.04 is decent

---

### Post by QDR06VV9 on 2015-09-20
**[COLOR=#222222][FONT=Verdana][SIZE=2] [/SIZE][/FONT][/COLOR]**[COLOR=#222222][FONT=Verdana][[SIZE=2]Reporting Bugs[/SIZE]]("https://help.ubuntu.com/community/ReportingBugs")
I usually wait for apport to show up but this wont do in this case.
[/FONT][/COLOR]**[COLOR=#222222][FONT=Verdana][/FONT][/COLOR]**I just login with my SSO account.

---

