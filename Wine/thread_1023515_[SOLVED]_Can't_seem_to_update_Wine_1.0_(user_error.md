---
title: "[SOLVED] Can't seem to update Wine 1.0 (user error probably)"
date: 2008-12-28
forum: Wine
---

### Post by cabbiinc on 2008-12-28
Hello, I'm trying to update my Wine 1.0 to a newer version (doesn't have to be the latest and greatest). I have one program that when ran doesn't fit in the window. So I figured it's a decent time to upgrade.

I went here [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb) but when I try Adding the WineHQ APT Repository I got three errors (didn't think to copy and paste them before closing the window). Then when I try to download and save Scott Ritchies key it times out.

I tried the command line
```
sabryna@sabrynascomputer:~$ wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
gpg: no valid OpenPGP data found.
```

So what would you do next?

---

### Post by Seks on 2008-12-28
the wine repositories ([http://wine.budgetdedicated.com](http://wine.budgetdedicated.com)) seem to be down

---

### Post by cabbiinc on 2008-12-28
> **Seks said:**
> the wine repositories ([http://wine.budgetdedicated.com](http://wine.budgetdedicated.com)) seem to be down

Thanks. I'll try again in a day or so.

Updated just fine now that the repositories are back on line.

---

