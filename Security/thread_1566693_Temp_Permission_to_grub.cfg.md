---
title: "Temp Permission to grub.cfg"
date: 2010-09-02
forum: Security
---

### Post by Microsoft Hater on 2010-09-02
Hi everyone:

I'm looking to edit my grub.cfg file to add the "pci=routeirq" code to the kernel line so I can configure my modem in Ubuntu. 

Please help! I'm happy with assigning a temporary permission to myself over the root file so I don't accidently alter it later. 

Thanks for any help and advice!

---

### Post by Bachstelze on 2010-09-02
You should never edit grub.cfg directly. The correct way to go is to edit /etc/default/grub and add your kernel parameters to GRUB_CMDLINE_LINUX.

To edit the file, run your editor as root, e.g.

```
gksudo gedit /etc/default/grub
```

Then run

```
sudo update-grub
```

to regenerate grub.cfg with the new settings.

---

### Post by Microsoft Hater on 2010-09-02
Thanks for the quick reply!

That sounds even safer - perfect! I'll try that and post back here with how it goes.

---

### Post by Microsoft Hater on 2010-09-02
Thanks for the help Bachstelze - your advice was precisely what I was looking for: the right way to make adjustments to my computer.

I'm fairly new to Linux and I'm probably going to continue to need help from users like you who make this community what it is. Thanks again.

---

