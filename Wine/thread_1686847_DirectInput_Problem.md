---
title: "DirectInput Problem?"
date: 2011-02-13
forum: Wine
---

### Post by suzy223 on 2011-02-13
Hi, everyone! I've been trying to get another visual novel to work on Ubuntu again and so far, I'm running into DirectX issues. I get a 'DirectInput' error every time I attempt to load the game. Installation (via AutoRun.exe) works fine, though.

In the Terminal, I get this:
```
fixme:imm:ImmGetOpenStatus (0x133850): semi-stub
fixme:imm:ImmReleaseContext (0x3002c, 0x133850): stub
err:ole:CoGetClassObject no class object {25e609e4-b259-11cf-bfc7-444553540000} could be created for context 0x1
err:dinput:DirectInput8Create CoCreateInstance failed with hr = -2147221164

```Now, I'm not sure whether I need to update the DirectInput or not, since the game apparently needs DirectX 9... anyway, in the Wine Registry Editor I created '25e609e4-b259-11cf-bfc7-444553540000' key and set the value to 0. Is that the correct value? If not, what do I need to set for it, etc? 

Also, I found this [patch]("http://web.archiveorange.com/archive/v/yf1aCLozX5UipdcfUimv") for CoCreateInstance. Is it relevant to my problem? If so, how do I apply it to Wine?

Thank you in advance!

---

### Post by suzy223 on 2011-02-13
Bump.

Okay, this is getting weird... now I get the same error for all of my other games as well. :( What the heck is going on?! They were playing perfectly before!

---

