---
title: "How do you find if the chipset you bought is the chipset you have?"
date: 2009-02-14
forum: The Cafe
---

### Post by argie on 2009-02-14
How does lspci identify what chipset a PCI Network card has when it's plugged into the PC?

The reason I'm saying this is that there are many network cards sold by Intex and Zebronics (two local brands) that have RTL8139D (implying they're Realtek chipsets or similar to them) printed on them but when I plug them into my motherboard and run lspci they report as cheap Chinese chipsets (ha ha, alliteration).

Is lspci accurate in this respect?

---

### Post by BuffaloX on 2009-02-14
If you Google "RTL8139D lspci" you can see what others get as output,

Seems that lspci detects this NIC just fine, but it's not very good for Linux...

---

### Post by argie on 2009-02-14
Ah, but that's not the problem. You see, I suspect the chipset is actually not an RTL8139D chipset because lspci reports it to be something else. What I want to know is, how reliable is this information from lspci. Can I use it to claim compensation from the company which sold me this card?

---

### Post by BuffaloX on 2009-02-14
Show us what you get as output from lspci, and maybe we can identify it.

You may get a bit more detailed info with this command:
```
sudo lshw
```


I suspect that in your case it's a NIC that has a Realtek chip but is produced by 3rd party vendor.

---

### Post by BuffaloX on 2009-02-14
> **argie said:**
> How does lspci identify what chipset a PCI Network card has when it's plugged into the PC?


Actually I don't know for sure, but I guess it just gets it from the kernel, and the kernel uses the hardware identification string.

If your adapter is some sort of total fake, this string could also be faked, but that would render the card totally useless, and they might as well have made cards with just little bits of plastic on them...

---

