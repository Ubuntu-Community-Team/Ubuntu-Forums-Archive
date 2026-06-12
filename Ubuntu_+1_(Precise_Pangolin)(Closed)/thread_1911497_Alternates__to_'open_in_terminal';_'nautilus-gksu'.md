---
title: "Alternates  to 'open in terminal'; 'nautilus-gksu'"
date: 2012-01-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mc4man on 2012-01-19
There are 2 new package available 'nautilus-open-terminal-here', does the same things as nautilus-open-terminal though it's a python script instead of an extension.
May be useful at times with the extension's recent history of occasional issues

Also there is 'nautilus-open-as-root', again a python script, this replaces the defunct nautilus-gksu

Edit: - Not new ubuntu packages, forgot I was testing something for the Nautilus actions extra (Daily) ppa

---

### Post by ronacc on 2012-01-19
> **mc4man said:**
> There are 2 new package available 'nautilus-open-terminal-here', does the same things as nautilus-open-terminal though it's a python script instead of an extension.
May be useful at times with the extension's recent history of occasional issues

Also there is 'nautilus-open-as-root', again a python script, this replaces the defunct nautilus-gksu

Edit: - Not new ubuntu packages, forgot I was testing something for the Nautilus actions extra (Daily) ppa

Not to worry , if they work good we'll bitch, whine and moan until they get  moved the regular repo's .:lolflag:

---

### Post by lucazade on 2012-01-19
I'd like them too in ubu repos..
this should be the daily ppa:
[https://launchpad.net/~nae-team/+archive/daily](https://launchpad.net/~nae-team/+archive/daily)

---

### Post by lucazade on 2012-01-19
they work like a charm.. too bad are not translated in my language.. ghh :/

---

### Post by mc4man on 2012-02-06
if using the 'nautilus-open-as-root' & it's stopped working I've found function can be restored by - 
 ```
sudo gedit /usr/share/nautilus-python/extensions/open-as-root.py
```

change the "gnome-open" to xdg-open ( currently line 56) & restart nautilus

---

