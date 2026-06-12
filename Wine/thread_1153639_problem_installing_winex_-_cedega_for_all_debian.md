---
title: "problem installing winex - cedega for all debian"
date: 2009-05-09
forum: Wine
---

### Post by ivanhoe75 on 2009-05-09
I need python2.4-dbus it is not available in repos Where can I obtain it

---

### Post by rcayea on 2009-05-09
> **ivanhoe75 said:**
> I need python2.4-dbus it is not available in repos Where can I obtain it


I recall needing that file(s) for something to do with my computer audio setup I think. If I remember correctly another version of python has replaced it. I checked launchpad and I don't see it there for Jaunty so you might have to just google and hope you can find it somewhere.

---

### Post by cogadh on 2009-05-09
Are you trying to compile winex from the out-of-date source that Cedega provides, or are you using actual Cedega? If you are compiling, don't bother, you will get much more up-to-date and better gaming support from Wine.

---

### Post by ivanhoe75 on 2009-05-28
I'd like to obtain cedega freely any way whether compiling or not. I`ve visited site, I have to pay to get cedega

---

### Post by asdfoo on 2009-05-28
I think you'll find Wine works better too.

---

### Post by ivanhoe75 on 2009-05-28
Only additional thing I want from wine - directX support, making this to free wine is so difficult...

---

### Post by hikaricore on 2009-05-28
WINE had support for most directx calls.
I get the feeling you have no idea what you're talking about.

---

### Post by zeroo on 2009-05-29
CD into the place that cedega is in and run:
[COLOR="Red"]$mkdir -p cedega_000133_all/DEBIAN [/COLOR]
This will create an "all folder."
Then simply run all of these: 
[COLOR="Red"]$ar p cedega_000133_all.deb data.tar.gz | tar zx -C cedega_000133_all/
$ar p cedega_000133_all.deb control.tar.gz | tar zx -C cedega_000133_all/DEBIAN/
$mv cedega_000133_all.deb cedega_000133_all.prerebuild.deb
$perl -pi -e 's/python2.4-dbus/python-dbus/' cedega_000133_all/DEBIAN/control
$dpkg-deb --build cedega_000133_all
$rm -rf cedega_000133_all
$sudo dpkg -i cedega_000133_all.deb[/COLOR]

And you should be set (:

---

