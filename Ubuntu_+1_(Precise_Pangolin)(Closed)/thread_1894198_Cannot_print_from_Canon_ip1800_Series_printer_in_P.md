---
title: "Cannot print from Canon ip1800 Series printer in Precise"
date: 2011-12-12
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Robertjm on 2011-12-12
Recently installed Precise Alpha 1 on a new computer and am having issues with printing.

Using a Canon ip1800 Series inkjet printer. The printer had been working fine under Lucid Lynx 32-bit flavor. The Precise Pangolin I am running is 64-bit flavor.

Added a new PPA repository to my Sources file:
[http://ppa.launchpad.net/michael-gruz/canon-trunk/ubuntu](http://ppa.launchpad.net/michael-gruz/canon-trunk/ubuntu)
as well as the sources PPA he maintains.

Ran sudo apt-get update
Ran sudo apt-get install cnijfilter-ip1800series
Did the same for the ip1900 Series, which had worked on my Lucid install too.

Opened Printers and selected Add
This detects Canon IP1800 (746AAB)
Hitting forward it starts to look for a driver
Select Canon (recommended) and hit forward
It recommends Pixma IP1000 and the driver:
Canon PIXMA IP1000-CUPS+Gutenprint v5.2.7 Simplified
After hitting forward it auto fills Printer name, description and location.
Hit Apply, which adds the printer and then offers me to print a test page.

The printer dialog box pops up. Says this is Job #7. Gives me progress that it's printing. After about 25% is displayed that goes away and says "idle-rendering complete. However, nothing is ever printed.

If I repeat the printing of the test page, it is now Job #8, with the same results.

Is the problem that these are 32-bit drivers only, and not universal drivers for either bit rate? Or is there a printing problem in general with the Alpha 1 version? I haven't seen anything in the forums I expect it's not the latter.

Thanks!

Robert

---

