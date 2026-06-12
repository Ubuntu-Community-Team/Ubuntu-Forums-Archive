---
title: "This mostly rocks! (long post)"
date: 2007-11-17
forum: Testimonials &amp; Experiences
---

### Post by Alexis Phoenix on 2007-11-17
Okey cokey (pig in a pokey) - this is how things look now.
The machine - Dell Inspiron 1501 laptop, 1 gig ram, 120 gig hd, dual core 64 bit Turion, ATI Radeon express graphics, pci express slot, broadcom wireless & wired ethernet.  Huge battery.  No ieee1394 :.(
The OS: Ubuntu Feisty (I think I´ll keep it just because I just like that it´s called Feisty Fawn!) with home cooked 2.6.22 kernel from kernel.org, and shiny new (8.42.3) fglrx driver from ATI.
The user: well, that would be me.  I´ve used Linux of one sort or another since 1999.

I installed Feisty from a live demo CD back in June and I´ve been tweaking it since.  Some things have gone weird.  I don´t know what I did but my keyboard has gone strange and European.  The keyboard is weird on this laptop anyway.  My cursor keeps getting placed in random places.  With the new kernel, usplash doesn´t work (yes I have the splash option in grub)

I like that I can still configure and edit config files by hand and it doesn´t change my settings because some graphical tool wants to, like in some distro´s.  Seems the nice Ubuntu people have got the right balance between easy to use tools and being able to do things the old fashioned way (though Gnome I still find intractable in this respect)

3d desktop effects and the broadcom wireless card didn´t work at first - however I downloaded the firmware for the wireless card and that works with the new kernel, and since I´ve installed the driver from ATI, the 3d effects work.  I now have wobbly transparent windows and cubular workspaces.  Thank goodness for the GL Desktop tool that makes it so easy to configure.

However, now I´ve got my funky 3d desktop to show my friends I think I will have to turn it off because it makes things slow (significant keyboard lag in Konsole, half speed on glxgears, screen savers just don´t display)

I still haven´t figured out how to actually create an ad-hoc wireless network though (with my wife´s XP laptop).

There is an external vga connector on the laptop - I tried using radeontool to turn it on and off but it´s always on.  Maybe I should play with the Catalyst control centre.

There appears to be an issue with the pci express slot and firewire - I´ve seen stuff about it on other forums.  I got a firewire card (Belkin) specially for it and it doesn´t work (the usb slot on the card does work though).  Hotplugging the card doesn´t work because Dell have provided a buggy bios for this laptop.   The ieee1394 and sbp2 drivers are loaded but I get an I/O error. (Vista doesn´t like it either.)  I´ve yet to find out if the card if faulty.

All in all, I love Ubuntu Feisty Fawn!!  But I wouldn´t have another Dell laptop (but OTOH, you.get a lot of bang for your buck with these).

---

### Post by Mazza558 on 2007-11-18
Hey, another 1501 user :)

I agree that they're a pain to get working properly, even more so with Gusty and the Wireless drivers. However, after tweaking a bit, they are lightning fast.

---

### Post by mendozaro on 2007-11-18
I am 6400 / 1505 user and it works perfectly (Gutsy).

Ofcourse the darn wireless (broadcom) driver is not loaded by default but it took me like less than 5 min to set it up.

I must say i am a very "noob" user for ubuntu. I am using it for 2 - 3 weeks now. Also i can say that at some point i got fed up and almost returned to windows. Here you can find the entire story:[http://ubuntuforums.org/showthread.php?t=613611]("http://ubuntuforums.org/showthread.php?t=613611")

---

### Post by Mazza558 on 2007-11-18
> **mendozaro said:**
> I am 6400 / 1505 user and it works perfectly (Gutsy).

Ofcourse the darn wireless (broadcom) driver is not loaded by default but it took me like less than 5 min to set it up.

I must say i am a very "noob" user for ubuntu. I am using it for 2 - 3 weeks now. Also i can say that at some point i got fed up and almost returned to windows. Here you can find the entire story:[http://ubuntuforums.org/showthread.php?t=613611]("http://ubuntuforums.org/showthread.php?t=613611")

It's more an issue with the stupid keyring manager and WPA for me. Switching to WEP solved it for me.

---

