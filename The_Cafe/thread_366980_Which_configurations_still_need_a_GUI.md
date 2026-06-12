---
title: "Which configurations still need a GUI?"
date: 2007-02-21
forum: The Cafe
---

### Post by bastiegast on 2007-02-21
Editing config files nowadays has become a rare occasion but still is necessary sometimes. So with the upcoming feisty release I wonder how many times do you still _have_ to edit config files?
To start off, Whenever your kernel gets updated a new item will be added to your boot menu, which is annoying as it soon becomes cluttered (it already is with the safe mode and memtest which I never use). But where's the GUI to remove the items from your grub menu? There isn't. You will still need to edit menu.lst, although it is a very well commented file, try to explain it to a newbie. What if you accidentally edit it wrong? Your PC won't boot.
Or what if I am behind a router with DHCP but I want to set my DNS servers manually. I will have to edit /etc/dhclient3/dhclient.conf (something like that).

So here are the first two:

- /boot/grub/menu.lst desperately needs a GUI.
- The networking config GUI could be improved.
- /etc/security
- any more?

I heard xorg.conf is going to disppear, but that might still take a while.

Note that I'm not particularly against config files, I just think if ubuntu aims to be "for human beings" common tasks should be doable by GUI only.

---

### Post by Sqwishy on 2007-02-21
Actually there is a GUI for grub. I don't think it comes with ubuntu but i know it exists because my brother has one in gentoo!

---

### Post by Tomosaur on 2007-02-21
<shameless self promotion>
There are several grub GUI programs out there - one in my sig in fact!
</shameless self promotion>

That being said - Feisty supposedly has a new 'Control Panel' type thing, which should make system configuration a lot easier. I haven't tried it myself, but I hope it's better than what is currently available in Edgy. The tools are there - they're just not readily avaiable.

---

### Post by bastiegast on 2007-02-21
> **Tomosaur said:**
> <shameless self promotion>
There are several grub GUI programs out there - one in my sig in fact!
</shameless self promotion>

That being said - Feisty supposedly has a new 'Control Panel' type thing, which should make system configuration a lot easier. I haven't tried it myself, but I hope it's better than what is currently available in Edgy. The tools are there - they're just not readily avaiable.

Yeah I've seen it, I think it does make the tools accessible. Although I find it easier to just maneuver my mouse through the menu than starting a control center. 

I might try one of those grub GUI utilities, menu.lst always frustrated me.

---

### Post by Nikron on 2007-02-21
/etc/security/

stuff needs a UI as far as I know

---

### Post by bastiegast on 2007-02-21
> **Nikron said:**
> /etc/security/

stuff needs a UI as far as I know

After one and a half year of intense linux usage I've never heard of that :p 
Maybe just because it doesn't have a gui. Anyway, added to list.

---

