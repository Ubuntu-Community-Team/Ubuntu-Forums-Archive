---
title: "Autostart Messenger via Wine - wrong command?"
date: 2009-04-19
forum: Wine
---

### Post by JohnFante on 2009-04-19
I have installed Messenger 7.5 via Wine on my wifes PC (she is a recent Linux convert and doesn't like pidgin).

It runs ok but I can't get it to autostart on boot.

I have added this command ind startup-programs:

WINEPREFIX=/home/wife/Messenger wine /home/wife/Messenger/drive_c/Program\ Files/MSN\ Messenger/msnmsgr.exe

but that doesn't seem to do the trick.

My wife is running Jaunty.

Any suggestions?

Thank you in advance.

---

### Post by hikaricore on 2009-04-19
> WINEPREFIX=/home/wife/**Messenger** wine /home/wife/**Messenger**/drive_c/Program\ Files/MSN\ Messenger/msnmsgr.exe ?

Shouldn't that be:

> WINEPREFIX=/home/wife/**.wine** wine /home/wife/**.wine**/drive_c/Program\ Files/MSN\ Messenger/msnmsgr.exe

---

### Post by JohnFante on 2009-04-20
I have installed Messenger in the WINEPREFIX Messenger to keep it away from my other wine programs. It took some fiddling to get running.

The path is correct. And Messenger starts fine when I type in the command in a terminal.

Is there another way/command when you want to autostart!?!

---

### Post by ninjapirate89 on 2009-04-20
If you are talking about Windows Messenger (MSN) I would suggest you try emesene. It is very very similar to messenger. Plus it doesn't require WINE

---

### Post by JohnFante on 2009-04-20
Thanks for the heads up :-)

Any ideas if I am doing something wrong?? Besides keeping MSN Messenger ;-)

---

### Post by NightMKoder on 2009-04-20
Well this isn't really a wine problem...Try asking in gnome forums. I use KDE and putting wine programs in autostart works fine.

---

