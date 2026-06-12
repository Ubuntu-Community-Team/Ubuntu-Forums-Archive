---
title: "Error Number: 3633"
date: 2010-07-27
forum: Wine
---

### Post by RustyWyatt on 2010-07-27
I am trying to get my first program running on Wine.  I have previously used Virtualbox but 10.04 and/or Virtualbox keeps loosing the keyboard and rebooting every ten minutes is getting old...

I am trying to run the free version FileAmigo LE 7.3.

I am getting the following error:
"Error Number: 3633 Description: Cannot Load DLL: MSJET4x.DLL".

I have manually put the MSJET4.dll file in every location I can in the Wine C drive.  I have also tried all of the different Windows version emulations...

I have also tried to install the MS file that is supposed to fix this problem but the installation aborts saying that my Windows installation is newer than the patch (WindowsXP-KB829558-x86-ENU.exe).

The error persists ;-(

All comments Greatly Appreciated!

thanks,
Tom

---

### Post by asdfoo on 2010-07-28
open a terminal, type `wine --version`
it should print 1.2

the correct way to install jet (you should delete the version you copied) is to use the command `winetricks jet40`

---

### Post by RustyWyatt on 2010-07-28
Thanks for the help!

*"it should print 1.2"*
Yup! and up to date per the web site

*the correct way to install jet (you should delete the version you copied) is to use the command `winetricks jet40*

This worked and it got me to the next error:

---
Run-time error '3265' Item cannot be found in the collection

FixOrdinals
---

According to M$ "MDAC 2.7" causes this problem
( [http://support.microsoft.com/kb/q279651/](http://support.microsoft.com/kb/q279651/) )

However I have not gone any further pending any Wine specific advice...

Thanks again for your help!
Tom

---

### Post by bird_4321 on 2011-03-17
Thank you for answering this problem.  I had the same error message and corrected it with your answer!  

I am a new Linux- Zorin user and love it only because of Ubuntu Forums members help.

---

