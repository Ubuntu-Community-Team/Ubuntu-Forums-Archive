---
title: "Should Stardict be included in the default repositories?"
date: 2006-12-03
forum: Repositories &amp; Backports
---

### Post by LinLenLap on 2006-12-03
I just noted after installing my favorites dictionary program the other day, Stardict, that the author has redesigned the site and created handicapped versions of the software available for free, while charging for fully functioning versions of the software and/or the dictionary.

Of course he/she is well within their rights to do so, and really, for a such a wonderful little program I am tempted to shell out a little money, but I have to wonder if it should still be included within the available software from Ubuntu repositories if this is truly the case.

L

---

### Post by adamkane on 2006-12-03
GNOME-Ding
[http://home.arcor.de/gkiwi/gnome-ding.html](http://home.arcor.de/gkiwi/gnome-ding.html)

Download source to desktop.

Extract files.

Install GNOME-Ding:
```

sudo apt-get install libgnomeui-dev libaspell-dev
cd ~/Desktop/gnome-ding-2.2
./configure
make
sudo checkinstall

```Enter the following at the Description prompt:
```

gnome ding is a translator and spellchecker for Gtk2/Gnome2.

```Cleanup:
```

cd ~/Desktop
sudo rm -r gnome-ding-2.2

```Run program:
```

gnome-ding

```

---

### Post by LinLenLap on 2006-12-03
Looks like an excellent alternative. Thank you!

L

---

### Post by Lord Illidan on 2006-12-03
The atrocious english on the website doesn't give me much confidence in the dictionary. Anything else?

---

### Post by adamkane on 2006-12-03
They're german.

---

### Post by The Warlock on 2006-12-04
> **LinLenLap said:**
> I just noted after installing my favorites dictionary program the other day, Stardict, that the author has redesigned the site and created handicapped versions of the software available for free, while charging for fully functioning versions of the software and/or the dictionary.

Of course he/she is well within their rights to do so, and really, for a such a wonderful little program I am tempted to shell out a little money, but I have to wonder if it should still be included within the available software from Ubuntu repositories if this is truly the case.

L

If an older version of Stardict was under a free license, then that older version is just fine for the repositories until a better alternative (or possible a free fork of that Stardict version) comes along.

EDIT: In fact, if the version the guy is charging money for is under an open source license, then there's nothing precluding Ubuntu from redistributing it for free.

---

### Post by LinLenLap on 2006-12-04
> **The Warlock said:**
> If an older version of Stardict was under a free license, then that older version is just fine for the repositories until a better alternative (or possible a free fork of that Stardict version) comes along.

EDIT: In fact, if the version the guy is charging money for is under an open source license, then there's nothing precluding Ubuntu from redistributing it for free.

Thanks Warlock. That's exactly what I was looking for, just a little clarification on the issue of what's included and under what circumstances.

L

---

