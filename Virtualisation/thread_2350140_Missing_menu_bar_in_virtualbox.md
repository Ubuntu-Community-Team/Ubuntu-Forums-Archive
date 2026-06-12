---
title: "Missing menu bar in virtualbox"
date: 2017-01-21
forum: Virtualisation
---

### Post by spbach1234 on 2017-01-21
Does anyone have any idea what is causing this? It just dissappeard, and did not come back. Otherwise, VirtualBox works fine.


[ATTACH=CONFIG]273308[/ATTACH]

Thanks

---

### Post by wildmanne39 on 2017-01-21
*Thread moved to **Virtualisation**.*

---

### Post by wildmanne39 on 2017-01-21
Copy and paste this command into the terminal:

```
initctl restart unity-panel-service

```
does that bring the menu bar back?

---

### Post by spbach1234 on 2017-01-21
No unfortunately.  It is still gone. Restarting does not help.

Thanks

---

### Post by wildmanne39 on 2017-01-21
To be clear the bar you are talking about is the one that has the x, minus and maximize buttons on it right?

---

### Post by spbach1234 on 2017-01-21
No, I am talking about the one with the start, new and settings buttons. In my screenshot they are missing.

IlikeTech

---

### Post by wildmanne39 on 2017-01-21
Please go into the following file and make sure that both say true then save and exit.

XML config is located in: ~/.config/VirtualBox/VirtualBox.xml
```
sudo -H home/username/.config/VirtualBox/VirtualBox.xml
```
```
<ExtraDataItem name="GUI/Toolbar" value="true"/>
<ExtraDataItem name="GUI/Statusbar" value="true"/>

```

I hope the file is still located their I can not confirm it on the system I am on at the moment.

Make sure that you have virtualbox completely shut down before you do the above procedure.

---

### Post by &amp;KyT$0P# on 2017-01-21
> **wildmanne39 said:**
> XML config is located in: ~/.config/VirtualBox/VirtualBox.xml
...
```
<ExtraDataItem name="GUI/Toolbar" value="true"/>
<ExtraDataItem name="GUI/Statusbar" value="true"/>

```

I hope the file is still located their I can not confirm it on he system I am on at the moment.
That's where it is on my system.

---

### Post by wildmanne39 on 2017-01-21
> **halogen2 said:**
> That's where it is on my system.

Thanks for confirming the file is still in the same location.

---

### Post by spbach1234 on 2017-01-21
WOOT! fixed! I did not have the status bar option, but toolbar was false.  It is fixed now.

Thanks for your time!

---

### Post by wildmanne39 on 2017-01-21
Your welcome glad it is working now. 

Please use thread tools at the top of the page to mark the thread solved.

---

