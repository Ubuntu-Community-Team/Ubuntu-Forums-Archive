---
title: "Firefox in Wine has become my default browser"
date: 2009-01-25
forum: Wine
---

### Post by stopsatgreen on 2009-01-25
I recently installed Firefox under Wine, but it has somehow become my default browser! When I launch Firefox in the menu, or under Gnome Do, it always launches Firefox/Win. There's no option in Wine to uninstall; I have to open the program launcher and run Firefox-3.0 in order to get the Linux version. How can I change this?

---

### Post by xc1024 on 2009-01-25
why did you install it under wine? i believe there's native version of firefox included in ubuntu.

anyway, try launching your native ff, go to preferences, main and set firefox as default web browser.

---

### Post by x33a on 2009-01-25
edit the firefox properties under the menu. delete the old command (related to wine) and type firefox %u.

---

### Post by stopsatgreen on 2009-01-25
Thanks for both your replies, but neither works. I already have Firefox installed under Ubuntu, but installed the Win version in Wine for compatibility with a video convertor I'm also running under Wine; the Ubuntu howto said I needed FF/Wine to make it work.

However, I've tried setting FF/Linux as default browser in Preferences, and used Alacarte to change the launch command; STILL getting FF/Win as the default.

---

### Post by stopsatgreen on 2009-01-25
OK, it was because I have CrossOver Games installed; once I uninstalled FF from there, I had my Ubuntu default back. Thanks anyway.

---

### Post by VladNistor on 2009-04-24
> **x33a said:**
> edit the firefox properties under the menu. delete the old command (related to wine) and type firefox %u.

That is the default command for running ubuntu firefox, and that command starts CrossOver/wine firefox when it is installed and set default. I thought it would become default under the "bottle" created, not the whole system.

I personally installed Crossover/wine FF to be able to watch a Romanian tv station live, it doesn't work under Ubuntu FF. I guess I'll uninstall the CrossOver FF to get the Linux one and then reinstall it. Thanks for the help.

---

