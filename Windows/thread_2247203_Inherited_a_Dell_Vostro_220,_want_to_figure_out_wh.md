---
title: "Inherited a Dell Vostro 220, want to figure out what's wrong with it"
date: 2014-10-06
forum: Windows
---

### Post by Funklink on 2014-10-06
I inherited a Dell Vostro 220 that apparently runs Windows 7. I plugged it in and the monitor shows no PC signal. The computer does this on the other monitors I've tried too. I can hear the fan run and the power light is on. I am a complete newbie at this kind of thing (I've replaced hard drives, power supplies, and keyboards, that's about it). I was wondering if anyone here could help me diagnose what the issue is and what might need to be replaced. I don't know what other information needs to be provided either, but please, just ask! I didn't know where else to post, but hopefully this is OK. You guys are always a good help. :D

---

### Post by mips on 2014-10-06
Was it working before you got it?
Any beeps coming from it anf what sequence if any?
Any cloured lights flashing?
Does it only have onboard gpu an additional dedicated gpu? I dedicated try swapping between the ports.
Reseat all ram, gpu's, connectors etc.

[http://www.l3jane.net/doc//vostro220mt/trouble.htm](http://www.l3jane.net/doc//vostro220mt/trouble.htm)

---

### Post by Funklink on 2014-10-06
I got it from some old folks who said it must be broken, worked for them previously but they said it stopped working one day. When I first plugged it in it was beeping twice, repeating this sequence. But I moved it to another part of the room and it never did it again, I don't know why. No light's except for the on/off button on the front and a green one on the back near the fan opening and power plug. The GPU is on board. Thanks for the link.

Edit: OK, I feel really stupid for not trying this in the first place, but I unplugged all of the internal connectors and plugged them back in. I also took out the RAM and put it back in. The computer now gets to the "Starting Windows" screen, then goes black and doesn't make anymore progress. I will look into this issue some more.

Unfortunately the folks who originally had the machine haven't told be yet what their issue was. I wish I knew if it was this Windows issue I'm stuck with now, or the no PC signal issue I had before.

---

### Post by varunendra on 2014-10-06
> **Funklink said:**
> When I first plugged it in it was beeping twice, repeating this sequence. But I moved it to another part of the room and it never did it again ...... I also took out the RAM and put it back in. The computer now gets to the "Starting Windows" screen....

99.99999.....% a case of loose RAM. The "two beeps.. repeating this sequence" means either a loose RAM or a loose CPU (depends on motherboard/BIOS). Not happening again means the RAM was probably detected later, but still not properly connected to function correctly, resulting in a 'stuck' POST (Power On Self Test) sequence.

The windows hang issue is, I believe, an indication of a corrupt windows installation, which might have happened due to this same 'loose RAM' problem - getting loose/disconnected while windows was running. Just a guess, but an educated one.

---

### Post by Funklink on 2014-10-06
I really appreciate that reply, makes a lot of sense to me. I think I will try to boot the computer to another OS and see if it functions.

---

### Post by mips on 2014-10-06
> **Funklink said:**
> I really appreciate that reply, makes a lot of sense to me. I think I will try to boot the computer to another OS and see if it functions.

Yeah boot from a livecd/usb. I'm sure it's gonna be fine.

Maybe check if there's any data on the HDD the old folks might appreciate before formatting it. Also check the HDD SMART status for bad sectors, bad sectors could also cause windows to hang like that.

---

### Post by Funklink on 2014-10-06
All right guys, here's what I tried:

I downloaded an ISO for Lubuntu 10.04 LTS and put that on a live USB. I tried to boot to the USB and I get the Lubuntu menu with the "Try without installing" options "Install" etc. Selecting any option will have the computer change screens to black with the blinking "_" in the corner, and then the screen stays black after that goes away. 

I wondered if it might've been a bad write, so I found an Ubuntu 10.04 CD I had lying around and any option you choose on this menu does the same thing. Not sure what to do at this point.

---

### Post by mips on 2014-10-06
I have not used ubutu in ages but on that screen there should be a vesa gfx mode as well as a failsafe/safemode option somewhere.

---

### Post by Funklink on 2014-10-06
Do you mean on the screens for the Live CD/USB? On the Lubuntu screen I have 5 options:

[LIST]
[*]Try Lubuntu without installing 
[*]Install Lubuntu 
[*]Check disc for defects 
[*]Test memory 
[*]Boot from first hard disk 
[/LIST]
The only option that works properly on this screen is test memory, of course.

On the Ubuntu 10.04 LTS Live CD I would tell you the options it gives me but that stopped booting properly (only worked once, now it gets to the purple-ish screen and shows the logo at the bottom), then it goes straight into the flashing "_" and to black screen. At which point I can Ctrl+Alt+Delete to reboot. (It doesn't provide me with a prompt, but it works)

Diagnostics works from the boot menu, and all tests are passed. I can enter the CMOS Setup utility, but I don't know what I'd need that for at the moment.

Edit: But I can safely say none of those options are present on these screens. From the Dell startup logo I get F2 for Setup and F12 for Boot Options (Where I select my CD ROM or USB etc).

---

### Post by mips on 2014-10-06
> **Funklink said:**
> 
Edit: But I can safely say none of those options are present on these screens. From the Dell startup logo I get F2 for Setup and F12 for Boot Options (Where I select my CD ROM or USB etc).

They are there, just not in plain sight, look closer.

EDIT: I did the googling for you [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Funklink on 2014-10-06
Apologies, I didn't see failsafe/safe mode or the other one explicitly, so it didn't click.

Edit: I got the PC to work with Lubuntu and it boots fine!

---

### Post by varunendra on 2014-10-06
Congratulations for a working 'brand new old system'. :D

Happy Ubunting !

---

### Post by mips on 2014-10-07
> **Funklink said:**
> Apologies, I didn't see failsafe/safe mode or the other one explicitly, so it didn't click.

Edit: I got the PC to work with Lubuntu and it boots fine!

Cool stuff, enjoy your 'new' pc!

---

