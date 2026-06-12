---
title: "ventrilo push to talk with pyvent strangeness"
date: 2009-03-13
forum: Wine
---

### Post by Ixonal on 2009-03-13
So yeah, I got my push to talk key working on ventrilo using wine using pyvent.py, however there's a lil something weird goin on. the setup says to list the push to talk hotkey (in setup) as "keyboard:a", which makes it so the push to talk key I set in the bindings window works, but also my a key starts it too. This is rather annoying considering my wsad controls. Any other key I set the hotkey to in the setup makes it fail working. So, I must ask, is there a line in the code I could change to make it, really, any other key? I don't really know python or I'd look through it more myself.

---

### Post by Ixonal on 2009-03-14
nobody else has this issue? should I use a different workaround?

---

### Post by daariil on 2009-03-17
It's the same for me. Although it's not really a problem for me since i only use Ventrilo when i play CS or WoW. The problem doens't occur in CS so then it's no a problem but in WoW i get this problem. However my PTT works without the script when i play WoW but not in CS.

---

### Post by Ixonal on 2009-03-18
pretty sure mine doesn't work in WoW without the script. I'll have to test later to find out for sure.

---

### Post by thradius on 2009-05-10
If you vi the file you can Change the program to accept another key.

class Settings:
    def __init__(self, event_type, keycode, display_name, window_name='Ventrilo', sim_key=XK.XK_**[COLOR=Blue]A[/COLOR]**):

The Blue Bolded "A" is the key I was successfully able to change it to "Z" It errors on symbols but letters work fine if you have a free one that does nothing in WoW.

[COLOR=Black]class Settings:
    def __init__(self, event_type, keycode, display_name, window_name='Ventrilo', sim_key=XK.XK_**[COLOR=Blue]Z[/COLOR]**):[/COLOR]

---

