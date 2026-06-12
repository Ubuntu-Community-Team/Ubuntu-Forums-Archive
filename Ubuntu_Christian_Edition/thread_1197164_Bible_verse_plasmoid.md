---
title: "Bible verse plasmoid"
date: 2009-06-25
forum: Ubuntu Christian Edition
---

### Post by StephanG on 2009-06-25
Hey guys, I'm not really using Ubuntu CE, I'm actually using Kubuntu 9.04, but didn't know where else to post this.

I've recently found that its possible to display a daily bible verse on a fortune plasmoid.

If anyone else is interested here's the code:

```

sudo apt-get verse
sudo apt-get plasma-widget-fortunoid
sudo rm -rf /usr/games/fortune
sudo mv /usr/bin/verse /usr/games/fortune
sudo mv /usr/bin/verse-dialog /usr/games/

```

This will essentially replace the fortune file with the verse file.  Then you just have to add the fortunoid plasmoid to your desktop.  And the plasmoid will display a verse instead of a random quote.  

I haven't tested the code as posted.  Please let me know if it works.

**Note:**  This will only work with the kde 4 desktop...  I think.

---

### Post by david_kt on 2009-06-25
> **StephanG said:**
> Hey guys, I'm not really using Ubuntu CE, I'm actually using Kubuntu 9.04, but didn't know where else to post this.

I've recently found that its possible to display a daily bible verse on a fortune plasmoid.

If anyone else is interested here's the code:

```

sudo apt-get verse
sudo apt-get plasma-widget-fortunoid
sudo rm -rf /usr/games/fortune
sudo mv /usr/bin/verse /usr/games/fortune
sudo mv /usr/bin/verse-dialog /usr/games/

```

This will essentially replace the fortune file with the verse file.  Then you just have to add the fortunoid plasmoid to your desktop.  And the plasmoid will display a verse instead of a random quote.  

I haven't tested the code as posted.  Please let me know if it works.

**Note:**  This will only work with the kde 4 desktop...  I think.

First of all, the codes are wrong as you omit the "install"

> sudo apt-get install verse
sudo apt-get install plasma-widget-fortunoid

Second, you might face some issue when upgrading or uninstalling, as you move around the package. It would break the package structure.

Third, off course it would work in gnome/ubuntu, but it will pull 59 new packages or 58.2 MB, and 180 MB extra space would be used.

If there is fortunoid for gnome, I might be interested to edit the code to work with verse.

DK

---

### Post by StephanG on 2009-07-21
Thanks for pointing it out :)

---

