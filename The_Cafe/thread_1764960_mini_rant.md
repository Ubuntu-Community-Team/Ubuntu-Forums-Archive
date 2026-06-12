---
title: "mini rant"
date: 2011-05-22
forum: The Cafe
---

### Post by decoherence on 2011-05-22
sorry... just gotta get this off my chest.

WHY is it that APC's console management interface is stuck in the freaking 60s!?!? The login only takes alphanumeric characters, even for the password, it locks you out after three failed attempts and if you typo and try to backspace, the backspace actually gets sent as a character, further bungling your password attempt! Holy crap, APC! Isn't it 1990 yet!?

OK rant over. The console should have unlocked itself by now and I can bash in three more login attempts...

---

### Post by Joe of loath on 2011-05-22
If you can't backspace, try ctrl-h ;)

---

### Post by decoherence on 2011-05-24
> **Joe of loath said:**
> If you can't backspace, try ctrl-h ;)

Yeah, ctrl h works fine.... when I remember to use it! ;) but I usually don't because most of the systems I console in to aren't STUCK IN THE FREAKING 60s!!!! lol

---

### Post by Dustin2128 on 2011-05-24
EDIT: I mentally skipped the APC. What exactly is APC, searches return many results.

---

### Post by decoherence on 2011-05-24
Top hit: American Power Conversion. They're UPSes. The ones my company has have serial consoles and web interfaces, both of which suck terribly.

---

### Post by Artemis3 on 2011-05-25
Many serial terminals don't like delete, it's a very old thing and probably not related to the device. Back in the day, most terminal software used to have an option to remap delete into ctrl-h.

As for APC, they will probably tell you to use their (windows) software...

If you log into another serial device, say, a cisco router, you will find the experience to be very similar.

The only thing i could think of changing in my ups, would be the sensitivity, and that can be done from the outside without login in... The other thing i could use with a connection to the ups (in my case usb) is to report its status so the machine knows when to turn off, etc.

That said i rather have an archaic yet serviceable serial link than a fancy but proprietary alternative...

---

### Post by decoherence on 2011-06-15
Nah, the APC is the only one I use that is this finicky. I also frequently console in to WTi bootbars, Cisco switches and routers, IDirect modems and probably other things that I'm forgetting. They all manage to provide a reasonable command line interface where keys do what you expect them to.

Why it's so difficult for APC to get this right, I don't know. But I guess it's better than that old Cisco PIX we have kicking around whose web-based configuration will only work with Netscape 4.8! ;) Now THAT is hi-freakin-larious!

---

