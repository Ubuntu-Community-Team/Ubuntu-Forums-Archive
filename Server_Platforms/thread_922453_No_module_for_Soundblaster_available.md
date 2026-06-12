---
title: "No module for Soundblaster available ??"
date: 2008-09-17
forum: Server Platforms
---

### Post by pksings on 2008-09-17
Hello all

I went to record something, recent upgrade, no sound. A little digging and this is what I found. No module is provided for the emu10k1 at all for this kernel, it is for the previous server kernel but not this one.

Anyone know why? Or even better, how to fix it without compiling a kernel from scratch?   The old kernel locked up regularly and eventually corrupted my software RAID 5 beyond rescue. I have 4GB of RAM so that is why I use the server kernel, and no, re-installing from scratch to use 64bit is completely out of the question.

root@phred:/lib# find . -name emu*
./modules/2.6.24-21-generic/kernel/drivers/input/gameport/emu10k1-gp.ko
./modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/pci/emu10k1
./modules/2.6.24-21-generic/ubuntu/sound/alsa-driver/synth/emux
./modules/2.6.24-21-server/kernel/drivers/input/gameport/emu10k1-gp.ko
./modules/2.6.24-19-server/kernel/drivers/input/gameport/emu10k1-gp.ko
./modules/2.6.24-19-generic/kernel/drivers/input/gameport/emu10k1-gp.ko
./modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/emu10k1
./modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/synth/emux
./modules/2.6.15-29-k7/updates/alsa/pci/emu10k1
./modules/2.6.15-29-k7/updates/alsa/synth/emux
./modules/2.6.15-26-server/kernel/sound/pci/emu10k1
./modules/2.6.15-26-server/kernel/sound/synth/emux
./modules/2.6.15-26-server/kernel/drivers/input/gameport/emu10k1-gp.ko
root@phred:/lib# uname -a
Linux phred.pksings.com 2.6.24-21-server #1 SMP Mon Aug 25 18:06:43 UTC 2008 i686 GNU/Linux

---

