---
title: "Serial Console Data Corrupted"
date: 2012-02-29
forum: Server Platforms
---

### Post by gdeeble on 2012-02-29
Hello,
 I have a home server that when connected to the on-board Serial Connector all I get is corrupted data on my client side. I have made sure that both the server and client both have matching rates, parity and flow control, but it doesn't seem to matter those settings(tried multiple rates, and different settings in bios to test with). The bios doesn't support console redirection so that's not something I can look at, but I'm looking to be able to see grub, kernel, and be able to manage the server over serial. I had an old board that did this but the new one(Asus M4A88T-M), refuses to work right. I've also gotten a serial card, but that seems to be a bust with it, as the system hangs during the boot if it's set to show the start up on it. 

So in this case, I have a few questions that might give me light on this situation. 
1) If the old board worked and this one doesn't(doesn't matter OS as I tried a live disc with serial port just enabled and it gave the same Corrupted data and keep just cycling), what can I try to  check to verify why it might be doing this, asides from seeing about an RMA on my board? I've already verified that setserial is configured right and USB Serial adapter works and serial card(only when not trying to display the start up)

2) Is it possible to use a USB or Serial Card to show the start up and where can I get information on this?

3) If reports are needed to identify the issue further, what all do I need? I can get the dmesg info, I/O Ports, interrupts, LSPCI info. Just let me know.

I'm not above searching for the answer, it's just that I might be searching using the wrong keywords, so If it's that, can someone direct me in the right direction please? If it's more in depth than searching that's fine too, but I appreciate any and all help, whether it be "You're(meaning me) Stupid!":lolflag:, here is what to search for, or try this. Thanks again.

-G.

---

