---
title: "Pangolin USB Printing"
date: 2008-02-24
forum: System76 Support
---

### Post by roscoetuff on 2008-02-24
Brand new Pangolin. Attached HP1020 to USB port. Seems to find it for specification, but nothing actually prints. Printing Qeue indicates "printed"... and done with the job. This happened once before on my old Dell... but can't remember the fix. Something about the port? Seems to think it's attached to "Ubuntu". I rmember on the old Dell printing everything through CUPS. Not sure that's what's happening. Where to start? Suggestions appreciated.

---

### Post by thomasaaron on 2008-02-25
After you go to File > Print in any given application, it should pull up a window that allows you to select your "Printer Name." This is usually a drop-down box that will contain something like "HP 1020".

---

### Post by roscoetuff on 2008-02-25
Actually, not. 

But looking at the specs, I get that it designates the printer something like //usb//hp1020....//serial...

and so I wonder whether it's confusing it's designation. This is set as a default printer. And even in the configuration box when you run a test page... which never prints by the way... it ID's the printer, sends the job out, and then notes that the job has printed. It is this last part that is wrong. It hasn't. So the fact that it's done suggests the communication through the port isn't working right.

I've hesitated to mess with the configuration... because you guys did something somewhere. But I don't see the same services running (like CUPS). 

Thanks for any other suggestions - Ihope you have some.

---

### Post by thomasaaron on 2008-02-25
We don't modify any configurations that pertain to printing.

Try going to System > Administration > Printing. Click the "New" button and
create/configure the printer.

You should also be able to tell if your printer is already present from that GUI. If it is, try deleting it. Then re-create it.

Best,
Tom

---

