---
title: "Grub error 18 after power failure"
date: 2009-02-02
forum: Server Platforms
---

### Post by QuimNuss on 2009-02-02
hello lads!

I hope somebody can help me on this... I've been running my own server since summer and there's some stuff I'll like to recover. I'm not really optimistic right now...

So, I had the electricist at home and I think he short-circuited the power, three times. I wasn't there at the moment, and I know I should have given my few bloggers on the dark for a few days and disconnect the server... (he was supposed to know where electricity cables where before drilling :^o)

Now I get Error 18 on GRUB... At first, I though it was just a gurb problem, but now I'm not that sure.

Quote: "Error 18" means that the Selected cylinder exceeds maximum supported by BIOS.

Most posts about that error are due to reinstalling Windows (which I didn't) and because HDD is not supported for the BIOS (which can't be either, as it worked right before the power failures)

I tried running the live-cd (server and desktop) to drop to a shell prompt so I could follow some instructions I had found on GRUB recovering, with no success at all, as the boot gets stuck looping on some statements DRDY error similar to the ones stated in
[http://ubuntuforums.org/showthread.php?t=937872](http://ubuntuforums.org/showthread.php?t=937872)

So no luck on that. To get the prompt I had to unplug the HDD... it didn't work plugging it again afterwards :P Probably it was nonsense, the drive was not listed under fdisk -l.

:/ the HDD is a ST3120026AS and the computer is actually quite old, near the 2002.

I don't know what else could be helpful on this... My main priority is trying to recover the data, although I have a backup on most of it. If it isn't possible, I hope the drive is still usable!

A hand on this would be grateful! I admire the power of the community wisdom =)

---

### Post by lucaspr on 2009-02-03
Have you tried to connect the HDD to another pc to see if it recognizes the HDD (in windows or linux doesn't matter)?

And if you own an external USB HDD (which is out of warranty) you could try opening it up and putting the server HDD in the case. 

and you did: ```
sudo fdisk -l
```;)

---

### Post by QuimNuss on 2009-02-03
Yep, I'm onto it, I don't have any other PC box at home, so I'll try this afternoon or tomorrow at university. I do own an external box, but the HDD has different connections than the external box (and the other drive). Srry, I'm really bad at hardware :/

Thanks for your help, I'll come back as soon as I get some more news...

---

### Post by QuimNuss on 2009-02-04
Okei, I've just learn I have a SATA connection drive while my usb box has IDE connection. Can I buy a conversor on typical stores?

---

