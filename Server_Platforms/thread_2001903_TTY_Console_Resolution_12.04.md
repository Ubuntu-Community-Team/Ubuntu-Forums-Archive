---
title: "TTY Console Resolution 12.04"
date: 2012-06-11
forum: Server Platforms
---

### Post by Toomanypcs on 2012-06-11
I have been at this for 5 hours now. I have edited configs, re-edited them, and tried every combination of solutions Google & this forum has offered. Currently stuck at 1920x1080, want 1024x640/1024x768 or similar.

I can get the screen res for Grub2 to change appropriately, I have been able to alter the boot messages resolution, but once the computer is booted, I simply cannot affect the final console resolution. 

Originally I just edited /etc/default/grub options:
[COLOR=Orange]GRUB_GFXMODE=
GRUB_GFXPAYLOAD_LINUX=
GRUB_GFXPAYLOAD=[/COLOR]
with different screen resolution values.  e.g. 1024x768, 1024x768x32, etc

None of that worked. So I edited: 
[COLOR=Wheat][COLOR=Orange]GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""[/COLOR]
[/COLOR]with vga=???. e.g. vga=824, vga=792

That failed, so I tried editing /etc/grub.d/00_header. No changes there affected the final console.

FYI, I ran [COLOR=SeaGreen]sudo update-grub[/COLOR] after all changes and rebooted.

Finally I tried editing grub.cfg directly, and rebooting (without using update-grub). I have gone through over 50 reboot cycles. Nothing I have done seems to work, and I cannot read the text from more than 5ft away on my monitor. I am at my wits end here. 

I have *some* console knowledge from other small distro's like Unslung. This is my first 'full-size' Linux based server, and something like making the console readable really should be extremely simple, and instead is making me wish I never downloaded it.

Suggestions? Please. :confused:

---

### Post by kridybel on 2012-06-17
Bump.

Sorry to put my wagon on your tail. I have a similar but different problem. My console resolutions (tty1-7) and grub start sceen are stuck on 640x350 and unreadable when my pc is connected to beamer. :(

Any help would be greatly appreciated.


Splash is darn ugly as well :(

But I succeeded to have my Nvidia geforce 6 working on ubuntu 12.04 :guitar:

---

### Post by Toomanypcs on 2012-06-19
If you read my post above, I pointed out that I could change the grub loader screen rez by altering the options I posted.

Anyone, at all, have a way to alter the tty rez?

---

