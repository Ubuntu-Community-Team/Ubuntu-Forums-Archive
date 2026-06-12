---
title: "Deus Ex through Wine"
date: 2010-05-14
forum: Wine
---

### Post by MikeT89 on 2010-05-14
My old copy of Deus Ex is ruined, so I had to get the ISO through other means. I've got it burned to a disc, but I have no idea how to install it through Wine. I've tried to run the setup.exe or deus ex.exe but I always end up with an error message:

Setup:Missing version number
(I take it this means the serial number?)

History: USetupDefinition::Init <-WFilerWizard::WFilerWizard<-Setup

I'm very new to Ubuntu, so I'm really confused. I'm on Lucid, sorry but I don't know what Wine version number I'm using (no idea how to check).

Did I just get a bad copy? Any suggestions? Thanks.

---

### Post by asdfoo on 2010-05-14
open a terminal, type:

wine --version

Wine 1.1.44 is the most recent.

---

### Post by MikeT89 on 2010-05-14
I'm on 1.1.42

---

### Post by lightstream on 2010-05-15
don't know if it'll help but in Linux you can mount an ISO directly so you don't need to actually burn it to disc:
```
sudo mount -o loop /path/to/iso /path/to/mount/point
```

---

