---
title: "How do I get my printer working when it does not have driver for linux ?"
date: 2007-12-06
forum: The Cafe
---

### Post by LinuxTryOut on 2007-12-06
How do I get my printer working when it is not listed in ubuntu driver database ?

I am having hard time to get my old printer working since i can't find the driver for Ubuntu.

---

### Post by rsambuca on 2007-12-06
Might help if you told us what it is.  Although some of them are, most of the forum community members are not psychic.

---

### Post by Seti on 2007-12-06
Why is it that I feel a thread about Canon printers coming on???

;)

---

### Post by SuperMike on 2007-12-06
My advice for a Linux noob:

* Avoid Canon or Lexmark printers (except the high-end Canon ones that emulate everything). Yes, I know they're cheap. Yes, I know it would be cool and seems reasonable that Linux support them, but, alas, I see no support.

* Stick with HP printers, primarily, and check compatibility on the [printer compatibility list]("http://www.linuxprinting.org/printer_list.cgi?make=Anyone"). And my experience has shown that postscript printers get the greatest support.

* On high-end systems used in offices, your best bet is postscript printers. I've also found that I can get Canon ImageRunners to work by using the Postscript driver for an HP 5MP and the thing emulates it perfectly.

Last, if you haven't updated your Ubuntu to the latest stable version, consider doing this in order to get the best printer compatibility.

---

### Post by rsambuca on 2007-12-06
> **SuperMike said:**
> My advice for a Linux noob:

* Avoid Canon or Lexmark printers (except the high-end Canon ones that emulate everything). Yes, I know they're cheap. Yes, I know it would be cool and seems reasonable that Linux support them, but, alas, I see no support.


It is actually Canon and Lexmark that don't support Linux.  Not the other way around.

---

### Post by Ocxic on 2007-12-06
look for a program callled turbo print it's cost about 30 or you could download load it from the right places..

that should allow you to get the drivers for your printer, i used it for my cannon i560 until now.
works great.

---

### Post by Steveway on 2007-12-06
Here is the repository I use for my unsupported Printer.
It uses some modified drivers that came with Canon-printers somewhere in asia.
You can use Turboprint, [www.turboprint.de](www.turboprint.de), wich is commercial and costs money.
Or you can add this to your sources.list:
deb [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu) ./
It works for my Canon IP Pixma something.

---

### Post by rsambuca on 2007-12-06
Why doesn't everyone just wait until we find out what printer it is.  These posts may be completely unnecessary and just confuse matters if it is a different printer.

---

### Post by popch on 2007-12-06
> **SuperMike said:**
> My advice for a Linux noob:

* Avoid Canon or Lexmark printers (except the high-end Canon ones that emulate everything). Yes, I know they're cheap. Yes, I know it would be cool and seems reasonable that Linux support them, but, alas, I see no support.

* Stick with HP printers, primarily, and check compatibility on the [printer compatibility list]("http://www.linuxprinting.org/printer_list.cgi?make=Anyone"). And my experience has shown that postscript printers get the greatest support.

* On high-end systems used in offices, your best bet is postscript printers. I've also found that I can get Canon ImageRunners to work by using the Postscript driver for an HP 5MP and the thing emulates it perfectly.

Last, if you haven't updated your Ubuntu to the latest stable version, consider doing this in order to get the best printer compatibility.

Also, check Dell printers. Some of them explicitly list Linux as supporting the device. Decent speed and costs as well, for some models.

---

### Post by Spr0k3t on 2007-12-06
If you get a laser printer, find one with really good postscript support and you can't go wrong.  Check against the information on [http://www.linux-foundation.org/en/OpenPrinting](http://www.linux-foundation.org/en/OpenPrinting) though just in case.

---

### Post by yatt on 2007-12-06
> **rsambuca said:**
> It is actually Canon and Lexmark that don't support Linux.  Not the other way around.Either way, the printer doesn't work.

Also, what happened to reverse engineering drivers?

---

