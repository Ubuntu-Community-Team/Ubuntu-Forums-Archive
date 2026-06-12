---
title: "Backported Apps showing up as local or obsolete in Synaptic"
date: 2005-06-15
forum: Ubuntu Backports
---

### Post by AndyAWS on 2005-06-15
Several Apps including Firefox, gksu and Gnomebaker are showing up in Synaptic as "local or obsolete" does this mean that the backport has been pulled or downgraded?

Should I downgrade the Apps to the previous version?

---

### Post by Xian on 2005-06-15
Apps that show up in that section because there in no longer a matching version number in the repositorites that you have set up Synaptic to pull from. This could be because it has since been updated or that particular version was pulled. Do a search in Synaptic and see if the pkgs have already been upgraded, or if perhaps your repository list has changed.

---

### Post by AndyAWS on 2005-06-15
They must have been pulled, they haven't showed up as updates, and I haven't changed my sources.

---

### Post by rpgcyco on 2005-06-16
gksu and gnomebaker were pulled on the 10th. Firefox has been downgraded to 5.04ubp5.

- Rpg Cyco

---

### Post by AndyAWS on 2005-06-16
Thanks....also noticed that the latest amarok-arts in ubp has unresolved dependencies..artsbuilder and kdelibs4.

---

### Post by _MiniMe_ on 2005-06-16
[QUOTE=rpgcyco]gksu and gnomebaker were pulled on the 10th. Firefox has been downgraded to 5.04ubp5.

[/QUOTE]

What was the reason to pull gnomebaker? I've got the backport-version installed and I know it's pretty unstable. But I hope that its not removed "forever" from backport-project???

---

### Post by jdong on 2005-06-16
[QUOTE=_MiniMe_]What was the reason to pull gnomebaker? I've got the backport-version installed and I know it's pretty unstable. But I hope that its not removed "forever" from backport-project???[/QUOTE]
I was told that it crashes when doing Audio CD projects.

---

### Post by Mez on 2005-06-16
[QUOTE=AndyAWS]Thanks....also noticed that the latest amarok-arts in ubp has unresolved dependencies..artsbuilder and kdelibs4.[/QUOTE]
 I suggest adding the following line to your /etc/apt/sources.list - this will make sure you can have the latest version of kubuntu librarires (which things like amarok etc depend on)

```
deb http://kubuntu.org/hoary-kde341 hoary-updates main
```

---

### Post by _MiniMe_ on 2005-06-16
[QUOTE=jdong]I was told that it crashes when doing Audio CD projects.[/QUOTE]

Gnomebaker has a lot of bugs IMHO.It also crashes when burning .iso-images (for example).  I just wanted to know if it gets back to the backports when a new version is released. It definitly deserves it, since there are virtually no gnome burning-appz that have all the functionality of e.g. k3b and are easy to use. The only two candidates are IMHO gnomebaker and graveman.

---

