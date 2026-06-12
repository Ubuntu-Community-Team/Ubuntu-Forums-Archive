---
title: "Prompt for Password After Resume"
date: 2009-09-12
forum: Security
---

### Post by igb on 2009-09-12
On my laptop running standard Ubuntu Jaunty I am prompted to enter a password when I resume from Suspend. However, my Netbook running UNR doesn't prompt me. I am sure there is an option somewhere to set this, but I can't seem to find it. Can anyone help out?

Thanks,

Ian.

---

### Post by srudes2 on 2009-09-12
1. Start up the terminal (Applications->Accessories->Terminal)
2. Type: sudo gconf-editor
3. On the left tab goto: /apps/gnome-power-manager/lock and make sure that suspend is checked.

---

### Post by igb on 2009-09-12
Thanks. It would be good if this was in the main Power Manager Prefs. dialog.

Ian.

---

