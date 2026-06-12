---
title: "[Solved]Snap Circuits by Elenco"
date: 2015-01-13
forum: Ubuntu, Linux and OS Chat
---

### Post by pfeiffep on 2015-01-13
This past weekend I had the wonderful opportunity to help my 10 year old grandson with one of his Xmas gifts. Part of the Snap Circuit set included free software that enabled a computer to be used as an o'scope to monitor wave forms the circuits create. The software works by monitoring the microphone input jack. The software is "Windows" only that doesn't install in a traditional Windows method; there's an .exe file that one simply clicks - ie no registry entries. I'm wondering if anyone knows of Linux software that performs similar in function (o'scope presentation of microphone input).

---

### Post by tgalati4 on 2015-01-13
There is *xoscope*.  There may be others.  Understand that the sound card cannot take high voltages.  Use a 10:1 voltage divider to knock your signals down to protect the microphone input.

Check craigslist and ebay for working oscopes.  If your child has a real interest in circuits, then a real oscope is worth the investment.

```
sudo apt-get install xoscope
```

Grab yourself some 555 timers and use a computer simulator to compare the results:

[http://www.falstad.com/circuit/e-555square.html](http://www.falstad.com/circuit/e-555square.html)

[http://www.555-timer-circuits.com/](http://www.555-timer-circuits.com/)

Then look for a used Knight MiniLab:  [http://www.knightedu.com/products/labEqui/mini/ml2010.html](http://www.knightedu.com/products/labEqui/mini/ml2010.html)

You can pick up older kits for $80 to $100.  The new kits are pricey, but there are plenty of used ones to be found.

---

### Post by pfeiffep on 2015-01-13
Thanks[**[COLOR=#000000] tgalati4[/COLOR]**]("http://ubuntuforums.org/member.php?u=241895") 	  						[IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-online.png[/IMG]

---

