---
title: "Pangolin Performance"
date: 2011-06-22
forum: System76 Support
---

### Post by Grelf on 2011-06-22
So I received my new laptop from System 76 and I'm running into some issues.

1) I'm trying to hook it up to my 24" lcd at home, and it seems the FN F7 button does absolutely nothing. When I try to have the monitor be the main screen and turn off the laptop lcd via monitor control, it turns off both monitors, so I have to hit escape to revert, and then it reverts to just a black screen where I have to hop over to tty and reboot manually to see anything.

2) Related perhaps to 1, but when I just plug in the monitor via hdmi, it distorts my laptop screen and just panels it ugly on the monitor.

3) The two finger swipe action is not working on anything. Browsers, desktop, anything.


System Specs:
Pangolin Performance PanP8
*Hard Drive : 750 GB 7200 RPM SATA II
*Memory : 8 GB Dual Channel DDR3 SDRAM at 1333MHz - 2 X 4GB
*Processor : 2nd Generation Intel Core i7-2720QM Processor ( 6MB L3 Cache, 2.20GHz)
*Wireless : Intel Centrino Advanced-N 6230 - 802.11A/B/G/N Wireless LAN + Bluetooth Combo Module


Any ideas? Honestly, this really is a very unhappy start to a new laptop.

---

### Post by isantop on 2011-06-23
We've seen a few issues with Unity and Intel Graphics. First, please try setting up Ubuntu to use both the built-in display and the external monitor. When you click apply, you'll probably get black bars on the top of the monitors. Go ahead and press Alt+F2, then run this command:

```
unity
```

This will reload Unity, and it should remove those black bars. Now, go ahead and disable the built-in monitor, then hit Apply. You may get the black areas on the screen again, and if so, press Alt+F2 and run the "unity" command again. that should clear that up.

For two finger scroll, it may come disabled by default. You can enable it by hitting the Ubuntu key on the keyboard and typing "mouse". Click on the "Mouse" application, which will take you to the mouse configuration dialog. Now, open the "Touchpad" tab and change the scroll method from edge scrolling to two finger.

---

### Post by Grelf on 2011-06-23
After talking to Ian, we got a few things working.

Seems the trackpad driver wasnt loaded originally and reinstalling did bring that up. So I have two finger dragging. Yay.

However, external monitors are still not working well.

I can, get both laptop and external monitors working side side in Ubuntu Classic (No Effects). However if I turn off the laptop monitor, the external monitor flickers and becomes unviewable.

In updated Ubuntu with unity and compiz and so on, it will work if I use both the laptop and external monitor at the same time, but if I turn off the laptop monitor, both monitors go black, I can see the mouse pointer, but nothing else.  Even though I do not accept the new configuration, it never reverts back. I have to do a full reboot to recover. Also while it works, the laptop screen thinks it's taller then it really is, there is no upper border.

I cannot  change ANY monitor settings in Fluxbox. None. At all. It mirrors at 1024x768, and gnome control panel laughs at me when I try to change it.


Through ALL and ANY of these processes, Function F7 seems to have absolutely no function whatsoever.

(edited to add behavior in classic ubuntu)

---

### Post by Grelf on 2011-06-24
Not to bump my own thread, but some added information in the hope SyS76 can fix this issue.

Seems that as long as I run in classic mode, with no extras, and keep the laptop monitor on, I can use an external monitor. I'm spanning from the laptop to the external, and I'm finding the laptop monitor seems to have dead space I cannot get to, (Although the mouse can get up there, and I see it when I hit the workspace switcher) that matches the height of the external monitor.

If I shut the lid of the laptop, it just shuts both monitors down, and hitting Function F7 does nothing still.

Still hoping for some kind of fix for this, since it's really not what I was hoping for with such nice external monitor options.

---

