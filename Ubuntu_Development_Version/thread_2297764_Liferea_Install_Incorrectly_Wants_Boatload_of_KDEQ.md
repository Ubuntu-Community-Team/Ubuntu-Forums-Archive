---
title: "Liferea Install Incorrectly Wants Boatload of KDE/QT Dependencies"
date: 2015-10-06
forum: Ubuntu Development Version
---

### Post by buzzingrobot on 2015-10-06
If you're installing Liferea (the RSS reader) today, you might want to use the "--no-install-recommends" flag.

Just did an install of the Gnome daily, ran updates, rebooted, and then a "sudo apt install liferea". That wanted to bring in 177 KDE and QT packages as "extras".  Liferea is strictly GTK. Presumably, there's a glitch in the dependency chain.

Adding the flag gets you the expected dependencies.

---

### Post by flocculant on 2015-10-06
Looks like kget causing the issue - it's a recommends.

Edit: actually recommends in vivid is steadyflow or kget, but steadyflow is not available in wily


[lpbug]1503352[/lpbug]

---

