---
title: "qmon DialogStyle warning and Ubuntu freezes"
date: 2011-09-29
forum: Server Platforms
---

### Post by toontu on 2011-09-29
Hi, I installed SGE on Ubuntu Server 11.04. Start qmon on the master node. Everything is fine thus far. Then when I click Host Configuration, two identical warnings pop out:

Warning: Cannot convert string "DIALOG_APPLICATION_MODAL" to type DialogStyle
Warning: Cannot convert string "DIALOG_APPLICATION_MODAL" to type DialogStyle

As soon as these warnings come out, Ubuntu freezes. But if I ssh to the master node from another machine (Ubuntu desktop), I still get the warnings but SGE seems working.

Also, clicking User Configuration (don't dare to do this on the master node) will give this warning:

Warning: XmtMenu: no items specified for widget uc_menu

I googled the first warnings with no luck, which suggests its rarity. Very unfortunate for me.
 
Anyway, any suggestions and solutions will be deeply appreciated. Let me know if any system configuration info is required for diagnosis.

---

