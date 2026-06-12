---
title: "Ubuntu Server has wierd error on boot."
date: 2011-07-12
forum: Server Platforms
---

### Post by DubIsLife on 2011-07-12
I recently got a 2gig ram upgrade from the previous 1 gigabyte. Ubuntu server does not seem to like this because now when i boot with the new ram in it gives a long error ending with
```
[    0.031281] [<ffffffff81426a29>] start_kernel+0x352/0x35b
[    0.031281] [<ffffffff81426a29>] x86_64_start_reservations+0x125/0x129
[    0.031281] [<ffffffff81426a29>] x86_64_start_kernel+0xfa/0x109
```

I have no idea what this means. I have tried installing the 32bit os and the 64bit and am currently on the 64bit. My computer model is a gateway 04024. If you need any more information(Sorry im not so technical) please tell me. Thanks

---

### Post by ian dobson on 2011-07-12
Hi,

That looks like the end of a kernel oops or panic, without seeing the rest it's hard too say.

Try only running the old or new ram module. It could well be that the ram modules have different timing parameters and the BIOS is getting the ram configuration wrong. Maybe also try resseting the BIOS to defaults and swapping the order of the to ram modules.

Regards
Ian Dobson

---

### Post by volkswagner on 2011-07-12
You can get bad RAM out of the box.  Be sure to run Memtest for the full cycle.

---

### Post by DubIsLife on 2011-07-13
> **ian dobson said:**
> Hi,

That looks like the end of a kernel oops or panic, without seeing the rest it's hard too say.

Try only running the old or new ram module. It could well be that the ram modules have different timing parameters and the BIOS is getting the ram configuration wrong. Maybe also try resseting the BIOS to defaults and swapping the order of the to ram modules.

Regards
Ian Dobson
sorry im late to reply. What i got was 2x1gb sticks so their the same ram sticks. It just does not want to work. I think ill retry with some new ram.

---

