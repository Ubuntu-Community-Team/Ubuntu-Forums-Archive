---
title: "Monitor or Video Card?"
date: 2005-06-23
forum: The Cafe
---

### Post by CospeFogo on 2005-06-23
Hello people, this is a cry for help. Since it's not directly Ubuntu-related, I posted here to avoid messing the other sections of the forum. 

This morning I turned my computer on and saw no video output at all. The monitor's led was on, but the screen was blank. I thought it could be either my monitor or my video card, but I was almost sure it was my monitor because it's old (Syncmaster 3Ne). However, I plugged the monitor on another pc and it suddenly worked. "Alas, it's got to be the vga card" I thought, but then I plugged the same monitor on my main machine and it worked! 

So, I think it can be:

1 - My vga card could be "loose" into the slot
2 - The monitor is dying

When my 1st unsuccessful atempt occured, I checked my dmesg via ssh and got these lines:

```
Linux agpgart interface v0.100 (c) Dave Jones
agpgart: Detected AGP bridge 0
agpgart: Maximum main memory to use for agp memory: 439M
agpgart: AGP aperture is 128M @ 0xd8000000
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
```

and:

```
nvidia: module license 'NVIDIA' taints kernel.
```

which is the same output I got after a successful attempt. I imagine that a misplaced card wouldn't be recognized and the module would fail to be loaded.

So, what do you think about it?

Thanks a lot.

---

### Post by polo_step on 2005-06-23
[QUOTE=CospeFogo]
So, what do you think about it?[/QUOTE]
Wiggle the AGP card into the slot a little.  It's cheap.

The contacts in an AGP slot are more complex and trouble-prone than those in a PCI slot, in addition to the fact that a lot of manufacturer's AGP slots are standard non-compliant anyway.

I've had a lot of erratic errors and video crashes that were fixed for another year by wiggling the AGP card in a bit better.

Can't hurt.

---

