---
title: "Firefox &quot;latest release&quot; version for 64-bit"
date: 2010-01-26
forum: Ubuntuzilla
---

### Post by akwala on 2010-01-26
I still use the old script since I'm on a 64-bit system (Karmic).

Today, it reported the following:
```
Jan 26 20:00:05  UBUNTUZILLA: Retrieving the version of the latest release of Firefox from the Mozilla website...
Jan 26 20:00:05  UBUNTUZILLA: Latest release version of Firefox : 3.5.7
Jan 26 20:00:05  UBUNTUZILLA: Currently installed version of Firefox : 3.6
```I had updated my ubuntuzilla FF 3.5.7 to 3.6, using "gksudo firefox", following the ubuntuzilla update alert earlier this month. Seems odd that now it thinks that the last version is 3.5.7.

Can I reliably continue to use the old script in the future?

---

### Post by nanotube on 2010-01-27
Hi,
Indeed, that's odd - i just tested it on mine (using "ubuntuzilla.py -a checkforupdatetext") and it finds the latest version to be 3.6... 

something's weird - are you by any chance going through some kind of caching proxy, that could be throwing out an old version of the mozilla.com website? 

or maybe you're being redirected to an outdated country mirror... what country are you in?

at any rate - unless something significant changes, the old ubuntuzilla installer script should remain useable...

that said, they just recently created a 'firefox-stable' ppa, so you could consider switching to that, since it seems that it includes 64bit builds:
[https://launchpad.net/~mozillateam/+archive/firefox-stable/](https://launchpad.net/~mozillateam/+archive/firefox-stable/)

(only for firefox, though, not thunderbird/seamonkey)

---

### Post by akwala on 2010-01-27
> **nanotube said:**
> Hi,
Indeed, that's odd - i just tested it on mine (using "ubuntuzilla.py -a checkforupdatetext") and it finds the latest version to be 3.6... 
Just checked, it now reports 3.6.

> something's weird - are you by any chance going through some kind of caching proxy, that could be throwing out an old version of the mozilla.com website?

or maybe you're being redirected to an outdated country mirror... what country are you in?
I'm in the US. I do use a proxy in my browsers, but not system-wide -- wget, for instance, doesn't go through a proxy.

---

### Post by akwala on 2010-01-27
> **nanotube said:**
> ...they just recently created a 'firefox-stable' ppa, so you could consider switching to that, since it seems that it includes 64bit builds:
[https://launchpad.net/~mozillateam/+archive/firefox-stable/]("https://launchpad.net/%7Emozillateam/+archive/firefox-stable/")

(only for firefox, though, not thunderbird/seamonkey)
I'm not sure if this new firefox-stable repository will work if I also have the "daily" repository turned on. I thought this would give me 2 installations, e.g.:
- /usr/lib/firefox-3.6 (stable)
- /usr/lib/firefox-3.6.1pre (daily)
...but I can only get the latter despite adding the "stable" repo.

---

### Post by nanotube on 2010-01-27
> **akwala said:**
> I'm not sure if this new firefox-stable repository will work if I also have the "daily" repository turned on. I thought this would give me 2 installations, e.g.:
- /usr/lib/firefox-3.6 (stable)
- /usr/lib/firefox-3.6.1pre (daily)
...but I can only get the latter despite adding the "stable" repo.

yes indeed - both repos use the same package name, so the later one (the daily) will overwrite the stable. you can only use one.

---

### Post by nanotube on 2010-01-27
> **akwala said:**
> Just checked, it now reports 3.6.

can't complain when a problem fixes itself :)

> 
I'm in the US. I do use a proxy in my browsers, but not system-wide -- wget, for instance, doesn't go through a proxy.
hrm... not sure where that came from, then...

---

