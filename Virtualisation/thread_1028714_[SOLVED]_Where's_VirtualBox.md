---
title: "[SOLVED] Where's VirtualBox ?"
date: 2009-01-02
forum: Virtualisation
---

### Post by Drakkor on 2009-01-02
I just installed VirtualBox 2.1.2.1.0 with the .deb package, but can't find how to start it. I had previous versions,and they usually where located in
Applications>System, but I have no System tab in Applications. I tried in
terminal,but it says I don't have it installed !! :confused:

---

### Post by amauk on 2009-01-02
I had a minor issue upgrading to vbox 2.1
the menu item got deselected

don't know if this is your problem,
but try System > Preferences > Main menu
and seeing if the menu item is disabled

Just tick the box to enable, and click close

---

### Post by albinootje on 2009-01-02
> **Drakkor said:**
> I just installed VirtualBox 2.1.2.1.0 with the .deb package, but can't find how to start it. I had previous versions,and they usually where located in
Applications>System, but I have no System tab in Applications. I tried in
terminal,but it says I don't have it installed !! :confused:

To see whether it's installed :
```

dpkg -l|grep -i virtualbox

```
In the terminal : 
```

VirtualBox

```

---

### Post by Drakkor on 2009-01-02
Thanks,guys, I went to the Main Menu and it was selected, so I unselected and reselected it , and now "System Tools" and Virtualbox shows up ! Thanks
:D

---

