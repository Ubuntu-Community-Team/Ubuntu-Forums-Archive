---
title: "Uncontrolled Fingers"
date: 2017-12-06
forum: The Cafe
---

### Post by electrosteam on 2017-12-06
I am not a touch typist, and make frequent mistakes on the keyboard.
During my working life doing engineering documents on Windows, loose fingers were never a real problem because nothing serious happens, just a 'damn' and then a correction.

On Lubuntu with the LXDE desktop, keyboard mistakes cause the cursor to jump wildly around the document.

Does anyone else have this problem, and is there a way of preventing, or at least reducing the effects.

Is removal of shortcut combinations the way to fix it ?

Learning proper keyboard etiquette at 74 years is probably not an option.

Is there a log of received key-strokes that I could examine to see just what it was that I had mistakenly entered ?.

Only on my first bean, and loving every drop.
John

---

### Post by wildmanne39 on 2017-12-06
I have the same issue with ubuntu 17.10, the touch pad is to sensitive in my case I did find a way to help it but I do not have that information handy and it only worked until I rebooted so I just keep my wrists off the laptop and only touch the keys but it is a serious issue.

---

### Post by electrosteam on 2017-12-07
wildmanne39,
Thanks for the suggestion, I had not thought of the touchpad.

Both my Windows XP and Linux machines are similar vintage Dell laptops without external keyboards.
The XP is at a much lower height than the Linux, raised to get some air underneath to prevent suspected shut-down due to overheating.
I may consider using a protective cover as the external mouse works well.

John.

---

### Post by mastablasta on 2017-12-07
or just disable the touchpad when the mouse is plugged in, if it is causing the cursor to jump.

---

### Post by cc1984 on 2017-12-07
I'm using Gnome and had the same issue of accidentally hitting the touchpad with the palm of my hand. Unfortunately Gnome doesn't have a setting to disable the trackpad that I could find. So, I wrote a script and mapped it to a key combo. Now I can enable/disable my trackpad with ctrl+m easily when needed. That might work for you if you are using an external mouse anyway.

---

### Post by makitso on 2017-12-07
Try

xinput set-prop 15 "Device Enabled" 0

You know, xubuntu has a lot more gui-based applications for configuration than lubuntu -- just a thought.

---

### Post by electrosteam on 2017-12-21
makitso,

Installed xinput, thanks for the suggestion.

~$ xinput
    SynPS/2 Synaptics Touchpad id=11 [slave pointer (2)]

~$ xinput disable 11
Touchpad no longer responds

~$ xinput enable 11
Touchpad now responds

I recently added simple desktop icons to change the MENU key to/from ESC when using Librecad.
Looks like a similar facility to switch the Touchpad Off/On ( available only when the mouse is connected ) might be useful.

The automatic disabling of the Touchpad when typing is taking place sounds interesting, but my first investigations got nowhere, still looking.

John

---

