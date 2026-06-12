---
title: "Upgraded... now printer problems"
date: 2016-08-15
forum: Ubuntu Studio
---

### Post by simon d w on 2016-08-15
Everything I have upgraded ubuntu has automatically found my printer and installed the software for it, this time it wont find the network printer to install the software. Ok it is an oldish type of printer but still. SX420W Epson 
I'm a novice user, I don't do anything fancy with ubuntu, but over the years I have managed to make it do exactly what I want it to do. Apart from now. I know bare bones terminal stuff. 

Also I hate the new software centre and I cant copy and past in the terminal any more, thinking of switching back to 14.04

---

### Post by SeijiSensei on 2016-08-16
Let's start with the CUPS manager.  Open a browser and point it at [http://localhost:631/](http://localhost:631/).  That will bring up the CUPS interface.  Choose "Adding Printers and Classes" and then click the Add Printer button. Enter your username and password when prompted. Do you see the printer in the "Discovered" list?

When you say it is a "network printer" is it connected directly to the network, or is it connected to a machine acting as a print server?  If the latter, you'll probably need to follow one of the other Network Printer choices that matches how the printer is served up.

If it's connected directly to the network, did you give it a static IP address?  If not, give that a try.  You'll probably need to do that through the printer's own interface.

---

### Post by simon d w on 2016-08-17
Thanks for replying. Yesterday I reinstalled 14.04 then upgraded through the automatic process when prompted, it now all works fine and I can copy and paste in the terminal again. It's now better than ever and I have the old software centre back, which seems to work better and looks better than when I did the fresh 16.01 install from the USB.  I don't understand why, but hay ho. Thanks for the help.

---

