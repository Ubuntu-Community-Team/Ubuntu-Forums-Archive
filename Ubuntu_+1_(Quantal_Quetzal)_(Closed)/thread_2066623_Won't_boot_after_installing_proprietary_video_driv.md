---
title: "Won't boot after installing proprietary video drivers"
date: 2012-10-05
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by mjzanga on 2012-10-05
My computer has an AMD Radeon HD6890 graphics card, and when Precise was running I had installed the proprietary drivers from AMD's website. After I updated to Quantal, Ubuntu would not detect my monitor's correct resolution, among other things. I went back on AMD's website to see if there were updated drivers and found some. Then I uninstalled the old drivers (which seemed to fix the resolution issue, but prevented Unity from running properly since the dock was no longer displayed). I installed the new drivers, following the instructions on this page: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu). After rebooting, before I reached the login screen I get stuck at a terminal window that I can't type in. Not really skilled with linux enough to know what to do next at this point. Any help would be appreciated.

---

### Post by pqwoerituytrueiwoq on 2012-10-05
try booting with nomodeset in your kernel boot line
hold shift to get menu to edit
if that does not work what happens when you run 
[FONT=Courier New]sudo service lightdm start[/FONT]

---

### Post by mjzanga on 2012-10-05
Nomodeset was no different than before. I can't run the command since I can't open a command prompt. When I mentioned a terminal earlier, it really appears to be kernel output when starting up the os (or at least something like that, not entirely sure). In any case, I can't do anything from that screen aside from pressing the power button, which will start the system shutting down and displaying output along the way. Sorry if I'm not quite clear with what I'm saying, I'm still relatively new to linux os

---

### Post by pqwoerituytrueiwoq on 2012-10-05
when it boots hit ctrl+alt+f1

you can hold shift while booting to get to a menu with recovery mode in it

---

### Post by mjzanga on 2012-10-05
Recovery mode booted already using tty1. Typed the command in the prompt and it took me to a blank screen with a cursor flashing. Back in tty1, it said that the service had started.

---

### Post by Rukiri on 2012-10-05
okay, at this point uninistall the proprietary driver and install the open source driver.  Than dual boot between 12.04/12.10 see if the proprietary work in 12.04.

Amd doesn't know how to write decent drivers but they'll develop excellent hardware..such a shame.  But it's the opposite with Nvidia, just stick with the drivers from nvidia as they develop linux drivers.  Amd does as well but even there windows drivers are gawd awful.

If you have no real work done in 12.10 test the proprietary driver in 12.04, if it works it's an xorg server problem which means you have to downgrade xorg server to what it was in 12.04.

---

### Post by mjzanga on 2012-10-05
I did try and uninstall the drivers earlier, but lo and behold the uninstall script is missing. Probably wouldn't work anyways though, since the only usable command prompt I can access is in recovery mode when the filesystem is read only.

---

### Post by drremulak on 2012-10-08
hey mjzanga - any luck? just ran into the same issue last night (same AMD Radeon HD6890 graphics card). Pretty stuck here..

---

### Post by mjzanga on 2012-10-08
No luck, not sure where to go with this now. Gonna ask around and see if I can get tips though

---

### Post by joiseystud on 2012-10-08
I had this happen too.  I finally just did

sudo ssh -X user@hostname

then ran sudo synaptic

I uninstalled the drivers and rebooted.  

Would have had to drop into a term

---

### Post by QIII on 2012-10-08
> **Rukiri said:**
> Amd doesn't know how to write decent drivers 

Pardon the expression, but ... Bull!  The drivers work very well.  What AMD has not yet done is expose the APIs for more hardware acceleration via the xvba back end for VA-API.   NVIDIA uses what used to be its own proprietary VDPAU (which has been open sourced), which works only with NVIDIA GPUs.  But given the fact that AMD, unlike NVIDIA, works with open source developers to create the open source Radeon driver, it's hard to get too unhappy with them -- although they really need to expose those APIs.  The flame wars really need to stop.  NVIDIA and AMD both produce good hardware and they both take the Linux community seriously.  Considering that the drivers work at all for a segment that comprises 2 or 3% of the market and that it takes roughly the same amount of effort and resources to create the Linux driver as the Windows driver, I'd say both companies are giving Linux more than a fair shake.

AMD also has a very close relationship with Canonical, too close according to some in the industry. 

The issue with Quantal is that the AMD 12.10 driver, which will handle the new xorg, is not in the Ubuntu repo yet -- AMD releases the xx.4 and xx.10 drivers to Canonical before the rest of the general Linux public.

The 12.9 "Ubuntu Preview Beta" currently in the repo from AMD is close, but still has some problems with artifacts even when it works.  

AMD is working on their 12.10 driver and, if the last four years are any indication, it will be released to the Canonical repo shortly -- and before anyone else gets it.  Phoronix whines about Ubuntu "getting the candy before anyone else" every April and October.

In short:  The 12.9 "Ubuntu Preview Beta" is a preview and a Beta.  The 12.10 driver is expected to work every bit as well with Ubuntu as any xx.4 or xx.10 driver.

Uninstall the proprietary driver and use the Radeon driver until Catalyst 12.10 drops into the Canonical repo.

---

### Post by mjzanga on 2012-10-16
sorry I haven't been on in about a week, I've been really busy. I still haven't figured out how to fix this problem, I've tried everything listed here. My main problem is that I can't get to a usable command prompt that doesn't mount the filesystem as read-only. Probably just going to reinstall, and wait until AMD gets the 12.10 drivers out.

---

