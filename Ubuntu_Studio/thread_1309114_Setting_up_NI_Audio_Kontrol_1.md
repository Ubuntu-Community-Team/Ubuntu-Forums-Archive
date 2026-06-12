---
title: "Setting up NI Audio Kontrol 1"
date: 2009-11-01
forum: Ubuntu Studio
---

### Post by Vigh on 2009-11-01
Trying to set up my NI Audio Kontrol 1 but I am having some difficulties I tried following the complex guide on the ALSA website but have not had any success. Could someone show me a simple way to install the latest version of alsa and configure my NI card. Any help appreciated.

---

### Post by AutoStatic on 2009-11-01
Which guide did you follow? I don't think you need to compile new drivers since snd-usb-caiaq is included in the standard kernels. So simply plugging in your Audio Kontrol should do the trick. You could try **lsmod | grep caiaq** to check if the module gets loaded. If this command does not return anything then do a **modprobe snd-usb-caiaq** to load the module manually.

---

