---
title: "what's best for managing partitions?"
date: 2005-08-08
forum: The Cafe
---

### Post by jnoreiko on 2005-08-08
I've installed gparted and used it successfully, but it won't modify the partitions ubuntu is installed on, and since ubuntu is on a logical partition, any operations on other logical paritions cause it to warn me I should reboot.

I thought of booting from the Live CD and then installing gparted, but I ran into dependency hell :(
qtparted seems to have fewer dependencies, but when I tried running it, I got the message that all my drives and paritions were in use. Even though they weren't mounted! I guess this is because they appear in the Computer window.

What are your recommendations for working non-destructively with partitions? I'd prefer a GUI :)

---

### Post by hardwarder on 2005-08-08
Well, using the knoppix live-cd seems to work fine for me, not sure how it'll fare you though.

---

