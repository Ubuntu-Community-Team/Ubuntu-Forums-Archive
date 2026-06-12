---
title: "Simple question - but how!"
date: 2010-04-04
forum: Wine
---

### Post by Baldrick_NZ on 2010-04-04
Hi all,

I understand there is a bug in wine which prevents windows programs from being removed from 'applications>wine', once removed from Home/.wine.

I was wondering if there is a work around for this problem, and if so what is it please?

The problem is I actually wish to uninstall wine completely, but when I do the wine folder still shows up under 'applications', I suspect it's because it still has references to previous windows applications which have since been removed.

Any help would be much appreciated!

Using Ubuntu Lucid 10.04 beta1

Baldrick.

---

### Post by conradin on 2010-04-04
Go to synaptic package manager and try marking the wine packages for complete removal.

---

### Post by Baldrick_NZ on 2010-04-04
> **conradin said:**
> Go to synaptic package manager and try marking the wine packages for complete removal.

Tried that. Folders still remain under "Applications>Wine" :-(

Thanks anyway... Any other ideas?

Cheers.

---

### Post by kblft on 2010-04-04
try [http://ubuntuforums.org/showthread.php?t=1255193](http://ubuntuforums.org/showthread.php?t=1255193)

---

### Post by 3rdalbum on 2010-04-04
Maybe I'm missing the point of the question, but why don't you just delete ~/.wine and remove the corresponding "Wine" menu from the Applications menu? (right-click Applications and go to Edit Menus).

---

### Post by Bonster on 2010-04-04
go to menu> main menu, then remove it manually or hide it

---

### Post by Baldrick_NZ on 2010-04-04
> **3rdalbum said:**
> Maybe I'm missing the point of the question, but why don't you just delete ~/.wine and remove the corresponding "Wine" menu from the Applications menu? (right-click Applications and go to Edit Menus).

Could it have been that easy? Sure was! Thanks all for your help. Problem solved..

---

