---
title: "LiveUSB booting to unusable screen"
date: 2014-03-28
forum: Ubuntu Development Version
---

### Post by SuperFreak on 2014-03-28
I tried a Live USB of 14.04 when the first betas(beta 1 if it is called that) came out and it booted (on try Ubuntu)to a full desktop then froze. Today I booted a Live USB of Final Beta and got to Try Ubuntu or Install, chose try and it booted to screen with no cursor just diaganal dots across a black screen.
The computer is a little old (HP Pavillion a6502f I believe it has Integrated graphics using nVidia GeForce 6150SE) and presently 12.04 64 bits installed and working although at one point I had to roll back to an earlier kernel to get a usable screen. Not quite sure how to do this in the "Try Ubuntu" mode and also not sure what I will need to do when I install.

Tried F6 but no luck

---

### Post by sudodus on 2014-03-31
I'm glad 12.04 64 bits is installed and works for you. I suggest that  you check which proprietary nvidia driver you are running there, and if  that driver is available in Trusty.

- Did you try the boot option ***nomodeset*** at F6?

- Maybe it works in text mode (with the boot option ***text***)
. Would it be possible to install a proprietary nvidia driver when in text mode, and then start graphics mode?
. If that is not possible, maybe you can start the installation from the Ubuntu ***mini.iso***, install Ubuntu and then install a proprietary nvidia driver when in text mode. After reboot you might have working graphics.

---

### Post by SuperFreak on 2014-03-31
Thanks for your answer and I am sorry I took so long to respond. At first I didn't understand how to get to the screen where nomodeset could be set. But now having done that it works fine.
I followed this link  to get there [http://askubuntu.com/questions/135515/set-nomodeset-in-usb-installation-efi-loader-with-iso]("http://askubuntu.com/questions/135515/set-nomodeset-in-usb-installation-efi-loader-with-iso")

---

