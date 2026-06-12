---
title: "Ubuntu-desktop gone after yesterdays updates"
date: 2013-03-28
forum: Ubuntu Development Version
---

### Post by ventrical on 2013-03-28
On two different machines used for testing Mir. Updated yesterday . Will boot into lighdm , etc.. but then goes blank after logon - no desktop or terminal - forced to reboot. I do get Grub menu.

1 Intel Graphics.EDIT* This one solved (forgot to remove type=mir from lighdm.conf)
1 Nivida graphics (nouveau).

---

### Post by ventrical on 2013-03-28
On nvidia machine .. what happened was I was trying to remove  type=mir from lightdm.conf using nano in terminal. The things was that 'type=mir' was not in  lighdm.conf so when I tried to close nano (exit) it told me it would destroy all the contents. This happened before and it took all of the info. I was able to restore it. The thing was is that rather than close nano I rebooted ctrl+alt+del. I still have that info in lightdm.conf but do not have my my Ubuntu desktop.

---

### Post by ventrical on 2013-03-28
Also .. yes .. I removed Xauthority as suggested :

rm .Xauthority

 but still no desktop

---

