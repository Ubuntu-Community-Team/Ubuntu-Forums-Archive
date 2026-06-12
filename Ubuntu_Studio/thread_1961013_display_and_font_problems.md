---
title: "display and font problems"
date: 2012-04-18
forum: Ubuntu Studio
---

### Post by savankiran on 2012-04-18
i ve ubuntu 11.10 and along wid unity shell, i ve also got the gnome shell installed.
for some reason there's huge trouble with the display and fonts. the google webpage and facebook appears in a weird font size. the gnome shell dash doesn't look as it is suppossed to be.i installed d canterella font to make it look like the fedora gnome settings in my lab system..but it jus wouldnt look anything close the lab system gnome shell...whats more annoying is that, sometimes, very rarely, it suddenly corrects itself n looks exactly the way i want it to...but once i restart the system, it goes back to the same freaky annoying look...the major problem is its extremely hard to explain in words...i would appreciate any help.

also is it, by anyway, possible remove the unity shell without affecting ubuntu(since it is provided along with it) now that i ve gnome shell.

---

### Post by cortman on 2012-04-18
In the web browser, fonts are determined by browser settings. If you're using Firefox go to Options>Content.
For Gnome shell, you can change the system font with Gnome-tweak. Install via

```
sudo apt-get install gnome-tweak-tool
```

[Here's]("http://linux-software-news-tutorials.blogspot.com/2011/10/ubuntu-1110-oneiric-remove-unity-and.html") information on removing Unity.

---

### Post by savankiran on 2012-04-18
i ve already installed the gnome tweak tool, but still it doesn't seem to give the desired result. everything jus seems a lil _stretched_ to be more specific.and about the browser font settings, ive already done it in d past n also tried it now.but still the same result.not wat i expected.

---

### Post by cortman on 2012-04-18
If everything seems a little stretched, are you sure your monitor resolution is set correctly? You can find out the GUI way in Settings>Displays, or run

```
xrandr
```

---

