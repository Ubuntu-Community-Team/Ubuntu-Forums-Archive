---
title: "VirtualBox won't open OS as of today--Help"
date: 2011-06-02
forum: Virtualisation
---

### Post by SVEN1 on 2011-06-02
Running Ubuntu 10.04LTS
and have VB 4.0 installed. It was working perfect for the past 5 monts. As of today tried starting XP as well as Mint 9 and it will not run either. Error box comes up and tried entering code into the terminal and it can not find the file/directory of that command.

Any clue as to what updates may have caused this or is there a work around to fix this?

---

### Post by CharlesA on 2011-06-03
Sounds like there was a kernel update recently.

Try running this:

```
sudo /etc/init.d/vboxdrv setup
```

---

### Post by SVEN1 on 2011-06-03
Got it fixed with the terminal apparently Vbox was updated to 4.0.8, reverted it back to 4.0.6. All is fine.

---

