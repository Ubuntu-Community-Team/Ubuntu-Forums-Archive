---
title: "Realtek R8101 driver in 3.15 kernel..."
date: 2014-06-15
forum: Ubuntu Development Version
---

### Post by zika on 2014-06-15
I've just sent a message to Realtek:
> [FONT=arial]Hello,[/FONT][FONT=arial]I'm using Your r8101 driver and in 3.15 kernel there were some changes in syntax so:[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]file: src/r8101_n.c
1.
PREPARE_DELAYED_WORK change to INIT_DELAYED_WORK
2.
SET_ETHTOOL_OPS(dev, &rtl8101_ethtool_ops); change to dev->ethtool_ops = &rtl8101_ethtool_ops;
[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]With those changes Your driver compiles OK and works nicely still... ;)[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Regards.[/FONT]

This might help someone wanting (as I do) to still use r8101 driver for appropriate NIC... ;)

---

