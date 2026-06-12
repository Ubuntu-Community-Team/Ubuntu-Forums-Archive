---
title: "Can't Print using CUPS"
date: 2010-03-05
forum: Server Platforms
---

### Post by Chrisso101 on 2010-03-05
Using CUPS 1.4.1 in karmic i386 server package . Administering remotely thro' port 631. Adding networked Samsung ML-6060 parallel port printer on Netgear PS-101 print server.

Click on "add printer" from CUPS admin page. CUPS fails to find any printers.

I choose LPD/LPR host or printer and click 'continue'

I type in the ip address of my print server,  [http://192.168.1.100](http://192.168.1.100), in the connection box on the add printer page & click continue. I give it a name "samsung" and tick the sharing box then click 'continue'

I choose make and model Samsung ML-6060 foomatic/pxlmono(recommeded)(en) - I've also tried others. Click 'add printer' and accept defaults. When I choose 'Print test page' from the combo box nothing happens.

Error log entry gives:
SSL shutdown failed: Error in the push function

I had this printer working previously when I installed it from Gnome but now that I've re-installed karmic without Gnome I can't get it to print.

I don't know enough to know if it would have been using CUPS to print previously, but it definitely worked.

I've also tried connecting the printer directly to lpt1 on the server but still no joy.

Any idea where I'm going wrong?

---

### Post by Chrisso101 on 2010-03-05
prefix should read ubuntu

---

