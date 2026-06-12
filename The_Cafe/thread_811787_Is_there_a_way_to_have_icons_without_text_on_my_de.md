---
title: "Is there a way to have icons without text on my desktop in Hardy?"
date: 2008-05-29
forum: The Cafe
---

### Post by days_of_ruin on 2008-05-29
They seem to have gotten rid of the ability to have the text a space
like you could in previous version of ubuntu:mad:

---

### Post by jeffus_il on 2008-05-29
Open Nautilus.
Try Edit->Preferences->Views
See the Icon View Defaults section.

---

### Post by days_of_ruin on 2008-05-29
> **jeffus_il said:**
> Open Nautilus.
Try Edit->Preferences->Views
See the Icon View Defaults section.
Nope.

---

### Post by jeffus_il on 2008-05-29
OK...
In a terminal run
> gconf-editor
Navigate to apps->nautilus->desktop
In the text fields, add the text that you want or remove text

---

