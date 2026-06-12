---
title: "Can't install seterra"
date: 2010-03-16
forum: Wine
---

### Post by snaggles on 2010-03-16
I'm trying to install an educational freeware called seterra. I've had in installed earlier when I used intrepid but after formatting my computer I don't seem to be able to install it again. I'm rather unaccustomed to using ubuntu (go figure) so any help would be appreciated.

What I have done is to download the program from; [http://www.wartoft.nu/program/seterra/](http://www.wartoft.nu/program/seterra/)

And when I try to open the .exe file using wine I get;

tmp/seterra-1.exe could not be opened, because the associated helper application does not exist. Change the association in your preferences.

---

### Post by asdfoo on 2010-03-16
> **snaggles said:**
> I'm trying to install an educational freeware called seterra. I've had in installed earlier when I used intrepid but after formatting my computer I don't seem to be able to install it again. I'm rather unaccustomed to using ubuntu (go figure) so any help would be appreciated.

What I have done is to download the program from; [http://www.wartoft.nu/program/seterra/](http://www.wartoft.nu/program/seterra/)

And when I try to open the .exe file using wine I get;

tmp/seterra-1.exe could not be opened, because the associated helper application does not exist. Change the association in your preferences.


open up terminal, type:

wine --version


Report back here, if it says 1.0.1 then you're using an old version of Wine and should update to the latest development release.

See here: [http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

Once you have confirmed that, go back to terminal, if the program is saved to your desktop:

cd Desktop
wine seterra-1.exe

---

