---
title: "PCMCIA Card Reader Driver for Flash Memory Card"
date: 2016-12-24
forum: Server Platforms
---

### Post by cook150 on 2016-12-24
On my Toshiba Satellite M55-S135 which has Ubuntu 16.04 LTS Server Edition, it has a PCMCIA Card Reader, which I intend to use to insert a flash memory card to help the server's RAM (currently only 512 MB at the moment). However, I'm not sure whether Ubuntu has identified the PCMCIA Card Reader or would even be able to use the flash memory from a PCMCIA Card when necessary. Is there some way to check whether the server has the drivers to use the PCMCIA Card Reader and is able to read PCMCIA Cards inserted into it?

---

### Post by darkod on 2016-12-24
Have you tied inserting a card and checking if it can be seen by parted?
```
sudo parted -l
```

---

### Post by cook150 on 2016-12-24
No, but the software recognizes the CardBus Connector in lspci, so I think I'm good!

---

