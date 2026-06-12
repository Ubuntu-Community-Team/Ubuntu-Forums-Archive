---
title: "zenwalk 4.0 and firefox always running"
date: 2007-04-04
forum: Slackware and derivatives
---

### Post by STREETURCHINE on 2007-04-04
hi every time i boot into zenwalk and try to open firefox it tells me it is already running but not responding,
i have rebooted many times but it is always the same

any help would be appreciated

---

### Post by ThinkBuntu on 2007-04-04
Go to htop in your system menu (from the Dolphin on the lower panel). Kill the Firefox process(es) and tell us if that fixes it.

---

### Post by STREETURCHINE on 2007-04-04
> **ThinkBuntu said:**
> Go to htop in your system menu (from the Dolphin on the lower panel). Kill the Firefox process(es) and tell us if that fixes it.

sorry but i cant find htop,is there a command i can give to kill firefox

---

### Post by STREETURCHINE on 2007-04-04
ok i resolved this with 

     ```
pkill firefox
```

it seems firefox did not close properly and a zombie was running everytime i booted into zenwalk..:)

---

