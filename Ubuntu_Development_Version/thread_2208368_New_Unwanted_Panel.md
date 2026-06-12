---
title: "New Unwanted Panel"
date: 2014-02-27
forum: Ubuntu Development Version
---

### Post by PJs Ronin on 2014-02-27
When I updated Ubuntu 14.04 this morning I got a new panel after reboot.   The attached images show the panel hiding under the normal top panel and yet in the second image you can see that conky shows on top of this new panel.

From what I can see of the selection on this panel it appears to be a Nautilus Menu.   Anyone else got this?   Any ideas how I would go about removing it?
[ATTACH=CONFIG]250753[/ATTACH][ATTACH=CONFIG]250754[/ATTACH]

---

### Post by PJs Ronin on 2014-02-27
Sometimes, my stupidity amazes even me.

Problem fixed by removing global menus viz:
```
sudo apt-get autoremove appmenu-gtk appmenu-gtk3 appmenu-qt
```

---

### Post by Eddie Wilson on 2014-02-28
> **PJs Ronin said:**
> Sometimes, my stupidity amazes even me.

Problem fixed by removing global menus viz:
```
sudo apt-get autoremove appmenu-gtk appmenu-gtk3 appmenu-qt
```

That's no way to be. You're not stupid and you did the proper thing by asking in the forums. Furthermore you provided a solution to help others who could have the same issues. Nice job.
=d>

---

### Post by PJs Ronin on 2014-02-28
^^ ty for the kind words.

---

### Post by Mateusz Stachowski on 2014-02-28
I think that you should install appmenu-qt back. Atleast if you want to have global menu for Qt programs.

The other appmenu packages have been replaced with unity-gtk2-module and unity-gtk3-module respectively.

---

### Post by PJs Ronin on 2014-02-28
> **Mateusz Stachowski said:**
> The other appmenu packages have been replaced with unity-gtk2-module and unity-gtk3-module respectively.

Yes, I noticed that.   I'm also getting this additional panel returning after a cold boot but I recently installed Terminator and have a feeling that may be the culprit.   I'll remove the 'solved' for the moment until I do some further checking.

Edit:   Yep, that was it... once I updated my script to unity-gtk2-module and unity-gtk3-module the panel stayed gone.   Thank you.

---

### Post by PJs Ronin on 2014-03-01
So I shutdown for the night, reboot this morning and that unwanted panel / global menu thing is back.   Any suggestions?

---

