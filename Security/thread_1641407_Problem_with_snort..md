---
title: "Problem with snort."
date: 2010-12-09
forum: Security
---

### Post by craneman914 on 2010-12-09
I recently downloaded snort and it does not seem to recognize my wireless device. when i enter sudo snort -v -i wlano, I get this message: sudo snort -v -i wlano
Running in packet dump mode

        --== Initializing Snort ==--
Initializing Output Plugins!
Initializing Network Interface wlano
ERROR: OpenPcap() device wlano open: wlano: No such device exists (SIOCGIFHWADDR: No such device)
Fatal Error, Quitting..:

Does anyone have an idea as to how i can correct this problem? Thank you:popcorn:

---

### Post by OpSecShellshock on 2010-12-09
Shouldn't it be wlan0 (I mean with a zero on the end)?

---

### Post by idi0tf0wl on 2010-12-09
> **OpSecShellshock said:**
> Shouldn't it be wlan0 (I mean with a zero on the end)?

Yeah that'll do it... Considering the posted output includes that o/0 switch-up too, it's likely that's your problem.

---

