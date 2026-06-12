---
title: "Hp 1410 AllinOne Printer - Compatibility &amp; Quality?"
date: 2005-10-12
forum: The Cafe
---

### Post by baRRacuda on 2005-10-12
I'm planning to buy this one, and in the ubuntu wiki, it says " Detected (and works) as PSC 1400. Both scanning and printing work." But i wonder if any of you has/had this printer? (Is it a good one? :) )

---

### Post by Goober on 2005-10-12
Yes, I have the HP PSC1410 Printer, all in one (ok, my parents own it, but its on my computer since theirs is Windoze-only, and old and crappy).  Hoary automatically recognized it, and everything works fine.  

Breezy is another story.  I know which driver it is, but it won't work for some reason.  Hoary recognizes it as the PSC 1400.  I need to fiddle with settings, I guess.

The Printer is, well, it works.  I like the photocopy feature, since our old one didn't have one.  It works, that's good enough for me.  Its awefully big though, it takes up more space then I would like it to . . .

Never tried scanning it, I need to look at the Wiki, I guess.

---

### Post by Suzan on 2005-10-12
I've got the HP 1410 (the entry in the Wiki is mine) and it works fine for me. Printing and scanning (with XSane) works very well!

It was detected as an 1400. An I've downloaded a PPD-file for it from linuxprinting.org.
(see [http://linuxprinting.org/show_printer.cgi?recnum=HP-PSC_1400](http://linuxprinting.org/show_printer.cgi?recnum=HP-PSC_1400))

I am very satisfied with the printing quality.

The only tricky thing: if you want to print with GIMP, you have to delete an wrong option, which is set from GIMP. You have to go to the print dialouge, than to "printer settings" (or what is called in english). Then you have to remove the "- oraw" from the command line. And printing works very well!

If you want to have the nice tool, called "HP-Toolbox", you have to install the package "hplip" from universe first, than install your printer. With that tool you can see, how much ink is left and many more.

---

### Post by Goober on 2005-10-12
Ok, did you get yours to work in Breezy?  Mine works like a charm in Hoary, but won't work in Breezy, for some very annoying reason.  I have the correct driver installed, but it still won't detect. I downloacded that PPD from LinuxPrinting.orf, but I believe that is the same driver as the one provided in the Printing Wizard.

I started a thread asking for help on it in Absolute Beginners.

---

### Post by Suzan on 2005-10-12
Yes, I've got Breezy and it works perfectly.

---

### Post by Goober on 2005-10-12
Ok, I got mine working with Breezy.  It didn't want to recognize the fact that the printer was plugged in, for some reason.  For the record, this model printer does work with breezy.  I am not sure about the Scanning thing though.

---

