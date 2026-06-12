---
title: "[KDE Neon] o2micro SD-card-reader doesn't work - how to edit sdhci.conf?"
date: 2019-12-16
forum: Ubuntu/Debian BASED
---

### Post by philippd2 on 2019-12-16
Hello,

                     I've got the latest KDE Neon on a Dell E7250. The o2-micro-SD-card-reader doesn't work after installation so I have to do

  ```
sudo rmmod sdhci_pci
sudo rmmod sdhci
sudo modprobe sdhci debug_quirks2="0x80000000"
sudo modprobe sdhci_pci

```  every time at startup.

  
How can I automate this? I created a sdhci.conf and tried
```

options sdhci debug_quirks2=0x80000000

```

and

```

options sdhci debug_quirks2="0x80000000"

```

 but it doesn't work.Kernel is 5.0.0-37
What can I do?

---

### Post by howefield on 2019-12-16
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

