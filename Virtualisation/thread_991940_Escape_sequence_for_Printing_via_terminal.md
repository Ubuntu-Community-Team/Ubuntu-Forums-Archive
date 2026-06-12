---
title: "Escape sequence for Printing via terminal"
date: 2008-11-24
forum: Virtualisation
---

### Post by mrsrini on 2008-11-24
I was using PUTTY terminal to connect to host computer to run application. The applucation used to run and generate some reports which I was able to direct it to the printer (either connected to PC or a network printer) using the escape sequence "\E[5i" and "\E[4i". It is observed that, after the echo of "\E[5i" sequence, the following STDOUT operations goes to the printer. To reset, "\E[4i" being used.

Now I am trying to replace PUTTY with Ubuntu VMware terminal and trying to accomplish the same printing behaviour. But, I could not get these escape sequences work. That is, it does not get printed and the STDOUT is treated as STDOUT only.

Is it possible to redirect the print this way? OR am I doing something wrong? 

Any immediate help will be highly appreciated!

Thanks for your time !

Regards,
Srinivasan R Mottupalli

---

