---
title: "Printer Install Fails"
date: 2013-09-22
forum: Ubuntu Development Version
---

### Post by sgage on 2013-09-22
Running a completely updated Saucy with Gnome. I go to the Printers setting, tell it to add a printer. It finds and properly identifies my printer (Epson C-86). I tell it to install, and after a second or two a box pops up "failed to add new printer". That's it - no indication of what might be wrong.

I'm almost positive I successfully installed this computer on an earlier install of Saucy. Any idea what might be going on?

TIA...

---

### Post by jbicha on 2013-09-22
You have system-config-printer-gnome installed right?

---

### Post by sgage on 2013-09-22
Yes, it is installed. I was able to successfully install the printer using system-config-printer - I guess it's just the "Printers" setting in the system settings that doesn't work.

Thanks for pointing me in the right direction...

---

### Post by sammiev on 2013-09-22
I have done a fresh install within the last week and my Epson Artisan 730 will not install in 13.10 and yes I have system-config-printer-gnome installed. I will maybe test to see if I can install it into Unity.

---

### Post by sgage on 2013-09-22
sammiev,

Did you try 'system-config-printer' from the command line? That worked for me when the system settings 'printers' item didn't.

---

### Post by sammiev on 2013-09-22
It installed using Unity and now works in gnome, I will have to remember the command line for my next install. :popcorn:

---

### Post by markbl on 2013-10-21
I did a fresh install of Ubuntu  GNOME 13.10 today and had this same problem. Just get "failed to add new printer" even though I see my printer transiently get identified. Finding this post, I see the advice here to run system-config-printer directly and that also worked for me. Thanks guys!

Somebody should raise a bug on this given it is in the formal 13.10 release so I will do that. Seems a bug with Ubuntu GNOME rather than cups as I imagine a bad bug like this will not be in the stock Ubuntu release.

PS edit: raised bug [https://bugs.launchpad.net/ubuntu-gnome/+bug/1242658](https://bugs.launchpad.net/ubuntu-gnome/+bug/1242658).

---

### Post by cariboo on 2013-10-21
This has nothing to do with Trusty. Closed.

---

