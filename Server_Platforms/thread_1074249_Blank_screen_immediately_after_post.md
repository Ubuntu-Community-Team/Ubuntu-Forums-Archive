---
title: "Blank screen immediately after post"
date: 2009-02-19
forum: Server Platforms
---

### Post by Raunok on 2009-02-19
Hello all!

I am not too unfimiliar with Ubuntu, but i am actually having a bit of a problem at the moment.  I installed ubuntu server edition on an older desktop, install went fine and accidentally left the cd in after install, was lazy and just chose boot from first hard-disk when it booted the cd, i then installed ubuntu-desktop to give me a gui (im still not that great at the command line alone just yet) setup webmin and a few other things and rebooted, removed the cd as well and immediately after post i have a black screen with an underscore in the upper lefthand corner just blinking (not a command line, or shell of any sort) it is completely non-interactive, from what i can gather its not even getting to grub to boot.  

If i put the cd in, i can boot from the menu (boot from first hard-disk) just fine, all my stuff is there everything works great.  i have tried re-installed grub as well as getting a gui manager for grub and neither of them have had any affect, if anyone could give me any help or guidance it would be greatly appreciated!!

Thanks!
Raunok

---

### Post by Raunok on 2009-02-19
any help at all?

---

### Post by cariboo on 2009-02-19
Do you see the grub menu?

Jim

---

### Post by Raunok on 2009-02-21
Actually I did not but it turns out that for some reason grub installed on the swap partition I have no idea why but after I cleaned that up and reinstalled grub again it worked!

---

### Post by mistypotato on 2009-02-21
[SIZE="5"]Good Call cariboo907[/SIZE]  :D

Nice work.

---

### Post by cariboo on 2009-02-21
Thanks

---

