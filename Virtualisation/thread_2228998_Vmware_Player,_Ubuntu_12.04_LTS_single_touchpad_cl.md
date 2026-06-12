---
title: "Vmware Player, Ubuntu 12.04 LTS single touchpad click does not release"
date: 2014-06-10
forum: Virtualisation
---

### Post by kennzors on 2014-06-10
Hi

I'm having a bit of trouble with my touch pad on my Asus UX301.

I currently am running Vmware Player 6 on a Windows 8.1 host with a Ubuntu 12.04 Guest (I need this version of Ubuntu for my office's dev environment). The touchpad single click works perfectly, but when I tap the touch pad, the click doesn't release. This isn't a hardware issue because on Windows 8.1, the touchpad click works perfectly, as well as my other Vmware Player with Ubuntu 14.04.

The Mouse and Touchpad UI on Ubuntu is no help, as the settings there are quite limited and have no useful options as to solve this problem.

I've used xev to debug, using the touchpad button:

```

ButtonPress event, serial 36, synthetic NO, window 0x4000001,
    root 0x165, subw 0x4000002, time 867178, (40,39), root:(106,91),
    state 0x0, button 1, same_screen YES


EnterNotify event, serial 36, synthetic NO, window 0x4000001,
    root 0x165, subw 0x0, time 867147, (40,39), root:(106,91),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 256


KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  101 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   


ButtonRelease event, serial 36, synthetic NO, window 0x4000001,
    root 0x165, subw 0x4000002, time 867276, (40,39), root:(106,91),
    state 0x100, button 1, same_screen YES




```

But when I use my touchpad with a tap:

```

ButtonPress event, serial 36, synthetic NO, window 0x4000001,    root 0x165, subw 0x4000002, time 832042, (48,28), root:(114,80),
    state 0x0, button 1, same_screen YES


EnterNotify event, serial 36, synthetic NO, window 0x4000001,
    root 0x165, subw 0x0, time 832034, (48,28), root:(114,80),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 256


KeymapNotify event, serial 36, synthetic NO, window 0x0,
    keys:  101 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   



```

I've also tried setting different xorg.conf protocols (PS/2, ExplorerPS/2 and IMPS/2) and restart lightdm service with no results.

Would anyone be able to recommend me any possible solution?

Thanks in advanced.

---

### Post by kennzors on 2014-06-11
For anyone who may encounter this problem, I seem to have found a solution.

Adding these two lines to your .vmx file on your host machine:

```

mouse.vusb.enable = "TRUE"
mouse.vusb.useBasicMouse = "FALSE"

```

seems to fix the issue.

---

