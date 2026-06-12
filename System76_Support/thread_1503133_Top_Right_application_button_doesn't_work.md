---
title: "Top Right application button doesn't work"
date: 2010-06-06
forum: System76 Support
---

### Post by compu73rg33k on 2010-06-06
My top right application button doesn't work. I'm talking about the set of 3 buttons on the top left corner of the keyboard. The one with the M doens't work. I launched showkey and from left to right, the keycodes were 155 and 172. But the rightmost key doesn't give any output at all. Anybody else have this problem? Is there a way to activate the button i.e. map it to a keycode? I'd like t use it as a shortcut to opening the terminal.

---

### Post by watchpocket on 2010-06-06
Strictly speaking this isn't an answer to your question, just another alternative, but you could put terminal in your startup items & thus have it just be open at bootup.

---

### Post by isantop on 2010-06-07
Actually, the functionality of this button is tied directly to the System BIOS. This key, sometimes called the mode key, throttles back the CPU and slows down the fan, so that the system runs nearly silently. As far as I know, you can't reprogram this button (but only this one) since it performs a system function. 

The Silent Mode is nice if you are in a lecture, meeting, etc. when the ambient noise is low and you don't what the fan kicking in to make a lot of noise. The performance is slightly reduced, but for most things is still adequate for Productivity software, internet browsing, and chat applications.

---

### Post by compu73rg33k on 2010-06-07
> **isantop said:**
> Actually, the functionality of this button is tied directly to the System BIOS. This key, sometimes called the mode key, throttles back the CPU and slows down the fan, so that the system runs nearly silently. As far as I know, you can't reprogram this button (but only this one) since it performs a system function. 

The Silent Mode is nice if you are in a lecture, meeting, etc. when the ambient noise is low and you don't what the fan kicking in to make a lot of noise. The performance is slightly reduced, but for most things is still adequate for Productivity software, internet browsing, and chat applications.
Oh wow! Good to know. Does it only work on two modes so that it's toggle-able? Is there any indication which mode you're in?

---

### Post by isantop on 2010-06-08
Yep, two modes only, so fast and slow.

Unfortunately, there is no immediate indicator as to which mode you are in. I just press it and listen for a change in fan speed. If you don't hear one, it's not needed at the moment anyway.

If you do hear the fan get loud, you can press the button to see if it gets quieter. Usually, it will, and then you know you are in silent mode.

Hope this helps you out. I'm always here if you need more help. :wink:

---

### Post by Backharlow on 2010-06-08
There is also a way (I've now forgotten) you can, from the terminal, send the same message to the OS that a key press from the keyboard normally sends. So if you literally do not have some strange key, you can still trigger the effect of that key.

---

### Post by isantop on 2010-06-08
Yes, but this key isn't linked to the keyboard, rather to the Motherboard directly. It's a low-level function, so you can even do it in Legacy OS's like DOS. It also ensures uniform operation across any OS, so even if you had windows on it, it would operate exactly the same way. You do, however, lose the ability to reprogram this key. So, in a way, you could say that the inability to reprogram the key is a feature! :)

---

### Post by compu73rg33k on 2010-06-08
> **isantop said:**
> So, in a way, you could say that the inability to reprogram the key is a feature! :)
"It's a feature, not a bug!" :)

Thanks for the info. I can definitely hear the fan get quiet.

---

### Post by betrunkenaffe on 2010-06-09
Does silent mode use less power (hence battery would last longer)?

---

### Post by isantop on 2010-06-09
In theory, it should, since the fan is spinning less, and the CPU is running slower. However, we haven't tested it to give a definitive result.

In reality, the difference is probably pretty negligible, possibly as small as a few minutes. Consider that the CPU is almost always scaled back to save power, usually only running as fast as it needs to. That leaves only the fan. The fan is a spun a tiny electric motor that uses almost no electricity, so the difference is going to be pretty small. But the feature will save you the embarrassment of being in a quiet room with a super loud laptop fan running full blast. It's also nice if you want to listen to something on it, as the quieter fan is much less intrusive.

---

