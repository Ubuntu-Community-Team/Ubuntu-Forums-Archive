---
title: "Need Help Decoding the Debugging log"
date: 2009-04-06
forum: Wine
---

### Post by mousestalker on 2009-04-06
I'm trying to get an obscure game (Computerized War In Europe) up and running in Linux with WINE. I have almost no Ubuntu/Linux Experience and even less WINE exposure.

I have figured out how to set a debugging log, so when my game crashes, which it does midway through turn one, I have lots of data that I do not understand.

I have 1.0.1 Wine. I am running Ubuntu 8.10 (Intrepid Ibex). Wie will start. The splash screen is missing and the speech does not play. After a while I get the main menu. If I select 'hot seat' then I can play for about a half a turn, then it crashes to desktop.

My debug log file shows the following:

fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!

err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000 {this repeats six times}

fixme:bitmap:SetDIBits shouldn't require a DC for DIB_RGB_COLORS
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

err:x11drv:X11DRV_CreateBitmap Trying to make bitmap with planes=1, bpp=8 {this repeats 430 times}

X Error of failed request:  BadIDChoice (invalid resource ID chosen for this connection)
  Major opcode of failed request:  55 (X_CreateGC)
  Resource id in failed request:  0x38e7e3b
  Serial number of failed request:  44923589
  Current serial number in output stream:  44923599 {this is the last entry in the log}
=======================================

Can anyone tell me what these things mean, or even better point me in the direction of a good explanation of error codes, what they mean and how to fix them?

---

### Post by 0cton on 2009-04-06
you should know/realize that wine is by far finished and it's still in beta and there are a lot of programs/software that can't run under wine at all.
Sometimes you don't have the choice but to wait for a new release :)
Meanwhile look at what can run very good in wine
[http://appdb.winehq.org/](http://appdb.winehq.org/)
and try that :P

---

### Post by asdfoo on 2009-04-06
> **mousestalker said:**
> I'm trying to get an obscure game (Computerized War In Europe) up and running in Linux with WINE. I have almost no Ubuntu/Linux Experience and even less WINE exposure.

I have figured out how to set a debugging log, so when my game crashes, which it does midway through turn one, I have lots of data that I do not understand.

I have 1.0.1 Wine. I am running Ubuntu 8.10 (Intrepid Ibex). Wie will start. The splash screen is missing and the speech does not play. After a while I get the main menu. If I select 'hot seat' then I can play for about a half a turn, then it crashes to desktop.

My debug log file shows the following:

fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!

err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
fixme:mountmgr:harddisk_ioctl unsupported ioctl 560000 {this repeats six times}

fixme:bitmap:SetDIBits shouldn't require a DC for DIB_RGB_COLORS
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

err:x11drv:X11DRV_CreateBitmap Trying to make bitmap with planes=1, bpp=8 {this repeats 430 times}

X Error of failed request:  BadIDChoice (invalid resource ID chosen for this connection)
  Major opcode of failed request:  55 (X_CreateGC)
  Resource id in failed request:  0x38e7e3b
  Serial number of failed request:  44923589
  Current serial number in output stream:  44923599 {this is the last entry in the log}
=======================================

Can anyone tell me what these things mean, or even better point me in the direction of a good explanation of error codes, what they mean and how to fix them?

Try a newer version of Wine [http://winehq.org/download](http://winehq.org/download)

---

### Post by mousestalker on 2009-04-06
I did. It still crashes :(.

I tried upgrading to Jaunty, but the install hung.

Today is not my happy software day.

---

### Post by Vadi on 2009-04-06
I'd file the bug report, Wine devs would look at them and know.

---

### Post by 0cton on 2009-04-07
> **Vadi said:**
> I'd file the bug report, Wine devs would look at them and know.

Considering that the game is not very popular i doubt the devs will get their hands/will on that game specifically
but in general newer versions of WINE swould implement winAPI better and increase the chances of it running, but don;t get your hopes high

---

### Post by mousestalker on 2009-04-08
I installed Kubuntu on my laptop (game had been on desktop). The game now plays on my laptop. I'm thinking something in it prefers KDE to GNOME.

---

