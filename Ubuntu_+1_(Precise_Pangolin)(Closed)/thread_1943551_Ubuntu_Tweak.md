---
title: "Ubuntu Tweak"
date: 2012-03-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Baldrick_NZ on 2012-03-19
Anyone having any problems with Ubuntu Tweak 0.6.1?

Just since this mornings updates, when I click on the icon, I get the splash screen as normal, but nothing else happens.

When I run in terminal, I get:
```
bryan@bryan:~$ ubuntu-tweak
Traceback (most recent call last):
  File "/usr/bin/ubuntu-tweak", line 72, in <module>
    window = UbuntuTweakWindow(feature=options.feature, module=options.module)
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/main.py", line 292, in __init__
    tweaks_page = FeaturePage('tweaks')
  File "/usr/lib/python2.7/dist-packages/ubuntutweak/main.py", line 178, in __init__
    viewport = Gtk.Viewport(shadow_type=Gtk.ShadowType.NONE)
TypeError: __init__() got an unexpected keyword argument 'shadow_type'

```

When it first happened this morning, apport registered it as a bug, but then promptly told me it was a third-party app, not supported by Canonical, that I should un-install it and then re-install. I tried this but didn't change anything.

Any ideas?

Cheers.

---

### Post by neu5eeCh on 2012-03-19
Interesting. Ubuntu Tweak stopped working for me too. (Same error.) Must have been something in the previous update? 

I would report it to Ubuntu-Tweak. Odds are, they already know about and are working on a fix, but it never hurts.

---

### Post by neu5eeCh on 2012-03-19
OK. I just reported (being a bug-filing fool).

[https://bugs.launchpad.net/ubuntu-tweak/+bug/959785](https://bugs.launchpad.net/ubuntu-tweak/+bug/959785)

Click on the "affects me too" option when you visit the site and add anything you want to add.

---

### Post by Baldrick_NZ on 2012-03-19
> **VTPoet said:**
> OK. I just reported (being a bug-filing fool).

[https://bugs.launchpad.net/ubuntu-tweak/+bug/959785](https://bugs.launchpad.net/ubuntu-tweak/+bug/959785)

Click on the "affects me too" option when you visit the site and add anything you want to add.

Thanks for that. Have followed suit.

---

### Post by mcellius on 2012-03-22
After some updates this evening, including one from the Ubuntu Tweak ppa, it's now working again for me.

---

### Post by Baldrick_NZ on 2012-03-22
> **mcellius said:**
> After some updates this evening, including one from the Ubuntu Tweak ppa, it's now working again for me.

Yep, got that. All sorted now. Thanks!

---

