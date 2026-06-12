---
title: "Diabetes Software"
date: 2009-05-03
forum: Wine
---

### Post by BarryM on 2009-05-03
Does anyone know of any software for Roche Diagnostics blood test meters that will operate under Ubuntu?

I have tried installing their own Accuchek Compass utility using WINE but cannot get it to run. I would need software that handles European standard readings (mmol/l).

---

### Post by asdfoo on 2009-05-03
> **BarryM said:**
> Does anyone know of any software for Roche Diagnostics blood test meters that will operate under Ubuntu?

I have tried installing their own Accuchek Compass utility using Wine but cannot get it to run. I would need software that handles European standard readings (mmol/l).


I'm guessing it didn't work because it uses USB?

If not, which Wine version did you use? 1.1.20 is the latest beta, you should try with that. [http://winehq.org/download](http://winehq.org/download)

please give detail of how you installed the application, how you are starting it and the output that shows when you try to do this.




[http://wiki.winehq.org/FAQ#head-8b4fbbe473bd0d51d936bcf298f5b7f0e8d25f2e](http://wiki.winehq.org/FAQ#head-8b4fbbe473bd0d51d936bcf298f5b7f0e8d25f2e)

---

### Post by BarryM on 2009-05-04
At the moment I have WINE 1.0 installed, from the synaptic package manager. I am using Ubuntu 8.04 with the 2.6.24-23-generic Kernel and Gnome 2.22.3

The Roche software uses an IR device to communicate with the meter, connected via COM1 (RS232).

I installed the software using the Add Application option in the WINE configuration dialog. This started the windows installer and installed the software as expected. At the end of installation the installer requested a restart. The installer has placed an icon on the desktop, with the following in the launcher dialog env WINEPREFIX="/home/barry/.wine" wine "C:\Program Files\Accu-Chek Compass\Bin\RdCompass.exe", and put the expected shortcuts in the programs folder.

When I attempt to start the program I get a Starting Accu-Chek Compass button in the bar at the bottom of my screen, which simply disappears. No error messages.

By the way, I have asked Roche whether they have any Linux software on offer, and they don't. I think the Accu-Chek Compass was built Microsoft Access, which may be relevant (as a Visual FoxPro developer, I personally would not be seen dead using Access, but that is a personal opinion).

Any suggestions would be gratefully received.

---

### Post by coffeeaddict22 on 2009-05-05
Hi,
Wine does have a few tricks to help it work.  Have a look at the FAQ; [http://wiki.winehq.org/FAQ]("http://wiki.winehq.org/FAQ")
In particular, it may be worth running the program from a terminal; that may give you enough info to sort the problem.  If that doesn't help, try WINEDEBUG; again, there's good instructions in the FAQ that I won't cut and paste :)
Post back if you need more help.

---

