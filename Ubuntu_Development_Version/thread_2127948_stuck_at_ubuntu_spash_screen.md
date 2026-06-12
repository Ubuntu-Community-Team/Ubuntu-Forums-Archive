---
title: "stuck at ubuntu spash screen"
date: 2013-03-21
forum: Ubuntu Development Version
---

### Post by rburkartjo on 2013-03-21
just upgrade for 12.10 to 13.04 from the command line. all went great except after i reboot i get stuck at the ubuntu splash screen it wont go past that. any ideas how to fix. or what should i try. am in live cd 12.10 now. tks. it is something i am over looking cause i had a problem like this a few years ago when i was beta testing and fixed. but forgot>

---

### Post by ventrical on 2013-03-21
> **rburkartjo said:**
> just upgrade for 12.10 to 13.04 from the command line. all went great except after i reboot i get stuck at the ubuntu splash screen it wont go past that. any ideas how to fix. or what should i try. am in live cd 12.10 now. tks. it is something i am over looking cause i had a problem like this a few years ago when i was beta testing and fixed. but forgot>


While the USB is booting hit any <or F6> key and choose "nomodeset" and see if that helps.

---

### Post by grahammechanical on 2013-03-21
I am assuming that you get a Grub menu? Select Advanced Options for Ubuntu and in that sub-folder you will find Recovery Mode. Selecting Resume will sometimes get us to a desktop without a video driver loaded. You might need to experiment with the video drivers. There is also a FailsafeX mode in the Recovery Mode menu.

Regards.

---

### Post by rburkartjo on 2013-03-21
tks ya'll i think it was a problem with the video driver (radium). fixed by trial and error. booted up with live cd and ran sudo service lightdm restart.

---

### Post by ventrical on 2013-03-21
> **grahammechanical said:**
> I am assuming that you get a Grub menu? Select Advanced Options for Ubuntu and in that sub-folder you will find Recovery Mode. Selecting Resume will sometimes get us to a desktop without a video driver loaded. You might need to experiment with the video drivers. There is also a FailsafeX mode in the Recovery Mode menu.

Regards.

Thanks for jumping in .. for some reason i thought the user was booting froma USB . me Doh !  :)

---

