---
title: "nautilus-open-terminal broken"
date: 2012-09-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Hairy_Palms on 2012-09-13
gnome-terminal crashes instantly when used in the context menu, yet gnome-terminal runs correctly when run alone, is anyone else seeing this?

---

### Post by mc4man on 2012-09-13
The extension is broken in nautilus 3.5.x, has been for quite some time.

What does still work is nautilus actions - set up as in screen, the parameter is 
--working-directory=%d

(i also change the default preferences so actions show directly in context menu,

---

### Post by Hairy_Palms on 2012-09-13
ok didnt realise it was broken, i tried the nautilus actions way, thanks for that, seems almost the same, only thing i miss is when clicking in a folder with nothing selected, the ability to open a terminal there, is there anyway to do this like the extension did?

---

### Post by mc4man on 2012-09-13
Don't see a way thru NA
There is an add. 'flaw' that if using directly on a folder on the Desktop the prompt will be Desktop$, not the folder. (at least here using the latest git nautilus, though myself not an issue, always have folders inside any folder on Desktop

The could be a way using a nautilus script instead of NA, have one around somewhere but like NA better then nautilus scripts

Also maybe the nautilus actions ppa will become functional with nautilus 3.6, last I checked it wasn't (uses nautilus python scripts
[https://launchpad.net/~nae-team/+archive/ppa](https://launchpad.net/~nae-team/+archive/ppa)

---

### Post by mc4man on 2012-09-13
Well I thought it wasn't working right just on the Desktop - turns out anywhere was always opening 1 dir. up (bummer..

Fixed but can't figure out at all.

So this always opens 1 dir. up though previously that's what I've always typed
```
--working-directory=%d
```

This works perfectly except I don't have a clue what &#8211; is
*think I remember reading about but forget..
```
&#8211;working-directory=%d
```

So I guess NA **or something** used to turn a -- into a &#8211; but isn't on this new install

(NA stores actions as .desktops in ~/.local/share/file-manager/actions - again I can see the difference in a working vs. nonworking correctly action's .desktop

---

### Post by mc4man on 2012-09-14
Very weird, *at least here on this laptop
So it's an endash. An emdash will also work, but -- no longer does, always open terminal 1 dir. up.

At some point in the past NA turned -- into – no longer does on this machine..

---

### Post by stinkeye on 2012-09-14
You can add **open as root** and **open terminal here** easily from
the Nautilus actions extra ppa.
[**_[COLOR="DarkRed"]http://www.webupd8.org/2011/12/nautilus-actions-extra-pack-of-useful.html[/COLOR]_**]("http://www.webupd8.org/2011/12/nautilus-actions-extra-pack-of-useful.html")

---

### Post by mc4man on 2012-09-14
> **stinkeye said:**
> You can add **open as root** and **open terminal here** easily from
the Nautilus actions extra ppa.
[**_[COLOR="DarkRed"]http://www.webupd8.org/2011/12/nautilus-actions-extra-pack-of-useful.html[/COLOR]_**]("http://www.webupd8.org/2011/12/nautilus-actions-extra-pack-of-useful.html")I had tried some of the Dr's nautilus extensions last month with the 3.5.x nautilus & they didn't seem to work.
In any event they are ok now & the 'open terminal here' one is full featured.

---

### Post by Hairy_Palms on 2012-09-15
thanks thats great, just was i was after! :)

---

