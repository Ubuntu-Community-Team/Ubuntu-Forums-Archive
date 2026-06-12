---
title: "Thanks! Thanks! Thanks!"
date: 2005-06-29
forum: The Cafe
---

### Post by coolblue on 2005-06-29
THANKS! THANKS! THANKS!

WOW! I had asked for help on this forum if
anyone could send me the Ubuntu/Kubuntu CDs.
[http://www.ubuntuforums.org/showthread.php?t=31867&highlight=india](http://www.ubuntuforums.org/showthread.php?t=31867&highlight=india)

And Ubuntuguy agreed to send me the CDs...and guess what today I was so overjoyed when I recieved my CDs....the Ubuntu CD, the Kubuntu CD and the Add-on CD...WOW!!!
(Note: The add-on CD had not been discontinued then)

I wanna thank Ubuntuguy for his kindness!
Its a wonderful community here! :)

I've installed Kubuntu but my mouse ain't
working...it just won't budge. Can someone help me
in this regard?

And will the add-on CD work for Kubuntu as well?
And can I install Gimp or other gnome-based packages
from the Ubuntu install CD? If yes, then how?

Thanks

Love to all
Newbie

---

### Post by az on 2005-06-29
You are welcome.  I was beginning to wonder when you would get them.

For your mouse, CTRL-ALT-F1 and type

sudo modprobe usbmouse

If it is a usb mouse.  On some hardware you need to do this...

CTRL-ALT-F7 to get back into X


If not, try (from the CTRL-ALT-F1 console)

sudo /etc/init.d/kdm stop

sudo dpkg-reconfigure xserver-xorg
(If it does not autodetect your mouse, try the other options, one-by-one.)

sudo /etc/init.d/kdm start

Yes, you can use gimp and the other ubuntu apps in Kubuntu.  Good luck!

---

### Post by jiyuu0 on 2005-06-29
wow... i didn't know that ppl are actually exporting the add-on cd :)

>And will the add-on CD work for Kubuntu as well?
yes, the packages in the add-on-cd should work for kubuntu too

---

### Post by poofyhairguy on 2005-06-29
[QUOTE=coolblue]
And will the add-on CD work for Kubuntu as well?[/QUOTE]

Yep. Kubuntu is a distro INSIDE Ubuntu.

---

