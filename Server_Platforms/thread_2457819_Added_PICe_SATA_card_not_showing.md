---
title: "Added PICe SATA card not showing"
date: 2021-02-10
forum: Server Platforms
---

### Post by mattiash on 2021-02-10
I am running Ubuntu server 20.04.1 on a self-built server, I need more than the 6 SATA ports that the motherboards offer, so I bought and added a PCIe SATA card ([https://www.delock.com/produkte/1117_SATA---eSATA/89384/merkmale.html](https://www.delock.com/produkte/1117_SATA---eSATA/89384/merkmale.html)).
Powered on the machine and no disk connected to the card is showing.
I am not sure where to look to see if the card is detected at all. After some googling it is suggested that all the PCIe are configured to be graphic in the bios, can this be it?

Please help. :)

---

### Post by ameinild on 2021-02-10
Try and run the lspci command:

```

lspci
```

This will show you if the card itself is detected.

More info about the command here: [https://www.thegeekstuff.com/2014/04/lspci-examples/](https://www.thegeekstuff.com/2014/04/lspci-examples/)

---

### Post by mattiash on 2021-02-10
Thanks - I cannot see the card in any way, for that matter, no PCI card added shows up.
Would that be a driver issue - would it be useful to reinstall the server OS?

---

