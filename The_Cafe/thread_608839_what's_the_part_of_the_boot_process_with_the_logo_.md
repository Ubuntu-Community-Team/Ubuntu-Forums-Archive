---
title: "what's the part of the boot process with the logo and orange bar called?"
date: 2007-11-10
forum: The Cafe
---

### Post by ice60 on 2007-11-10
i want to change my bootup to look like this mac boot process
[http://www.youtube.com/watch?v=z2QozxWhlwM](http://www.youtube.com/watch?v=z2QozxWhlwM)

i've done everything apart from that bit at the start of the video. i can't remember the name of that part of the bootup :( i don't think it's the GDM, or usplash, so what's it called??

---

### Post by Steveway on 2007-11-10
You can change it with something called startup-manager.
Just install it with Synaptic.

---

### Post by ice60 on 2007-11-10
> **Steveway said:**
> You can change it with something called startup-manager.
Just install it with Synaptic.
yeap, i've got that, there are a few options there that i have already changed and i still have the ubuntu default bootup. i was just wondering how to get that mac bootup bit like up there in the video. i don't know what it's called :(

---

### Post by dfreer on 2007-11-10
Well, GRUB handles the booting of the kernel, but generally you would use usplash to change the startup splash screen like that. GDM is the part where you login and enter your username/password.

Ah, I see the mac4lin howto recommends using gtweakui to change the splash. For more information, see this page of the howto:
[http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac_p2](http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac_p2)

EDIT: hmmm, it seems right below that they also recommend using usplash... lemme see if I can find that exact bootsplash on gnome-look.org really quick.

---

### Post by ice60 on 2007-11-10
great, thanks. i got twaekui but maybe i missed that bit. thanks for the help :D

this is how it looks now, i changed the dock now so it looks a bit more like leopard.
[http://att.macrumors.com/attachment.php?attachmentid=90509&d=1194453501](http://att.macrumors.com/attachment.php?attachmentid=90509&d=1194453501)

i posted it in the mac forums lol
[http://forums.macrumors.com/showpost.php?p=4457408&postcount=174](http://forums.macrumors.com/showpost.php?p=4457408&postcount=174)

---

### Post by dfreer on 2007-11-10
So does it boot up properly, with the mac splash screen and progress bar like the video?

---

### Post by ice60 on 2007-11-10
> **dfreer said:**
> So does it boot up properly, with the mac splash screen and progress bar like the video?
oh, i haven't tried it yet, i'm using my desktop atm - suse. but, everything else works perfectly - from the OSX grub background to the OSX GDM, the OSX system sounds etc, etc. just that bit i didn't know how to change.

i compiled that AWN dock from the development code and the computer was locking up totally every hour or so. so, i compiled a more stable release over the top last time i used it and it seemed to work fine 8)

i'll have a go now at changing that bit with tweakui :)

---

### Post by ice60 on 2007-11-10
that tweakui is just the usplash, i got that already. i've no idea how to change that bit of the boot process??? i don't even know what it's called :( it's not that tweakui bit.

does anyone know how to make my boot up look like that first bit in the video?
[http://www.youtube.com/watch?v=z2QozxWhlwM](http://www.youtube.com/watch?v=z2QozxWhlwM)

---

### Post by ice60 on 2007-11-10
it looks like it is the usplash i need to change. i was getting it muddled up with the splash screen that loads after the GDM, that shows nautilus etc loading. :-\"

---

### Post by dfreer on 2007-11-10
I asked because after downloading the mac4lin files, it didn't appear like gtweakui would actually modify the usplash screen. BTW, that first part in the video IS usplash, basically that video covers 3 parts:
(1) The bootup splash screen, with progress bar (Managed by usplash, seen after GRUB loads the kernel)
(2) Some sort of login, quite probably GDM with a MacOSX theme (where you enter your username/password)
(3) The actual desktop with dock (probably AWN).

Usplash is a program, that handles the boot screen and it isn't the splash screen itself. Try following the howto that I linked to, specifically the part regarding usplash, and if it doesn't work let us know.

---

### Post by reverend_HH on 2007-11-10
hey everyone, i installed startup manager and i was able to sucessfully change the grub  menu background but theres a slight problem. it is hard to see the highlighted entry because its black on black, on the preview from the site i got it from shows the entries are  highlighted blue. i already played with the colors in startup manager and even in the menu.lst but nothing seems to change. i tried a different background and it shows highlighted entries are still black. suggestions?

---

### Post by ice60 on 2007-11-11
thanks for the help :)

i found out it's a bug or something and that startup-manager doesn't work for everyone :(

but, don't get too upset because i used my skillz and made a fix for it, just like this -

install galternatives and make a new usplash option with the usplash i want, then select it
and
linked the usplash i want to /usr/lib/usplash/usplash-artwork.so
```
sudo ln -sf /usr/lib/usplash/osx-splash-wide.so /usr/lib/usplash/usplash-artwork.so
```it still doesn't work with the startup-manager so i stop using that program!

you can see the fix has worked when you run this -
```
sudo update-alternatives --config usplash-artwork.so
```
it should show your new option has the default option 

it might be a stupid fix, i don't know. it worked though :D

---

