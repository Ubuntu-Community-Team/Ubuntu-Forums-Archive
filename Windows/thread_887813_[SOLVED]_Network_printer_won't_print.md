---
title: "[SOLVED] Network printer won't print"
date: 2008-08-12
forum: Windows
---

### Post by ertrules22 on 2008-08-12
I have installed a new network printer on four new machines in a remote location.  They are all Windows XP (not sure which SP).  The printer prints and works just fine on three machines, but the fourth printer just says pending and then comes up with an error and doesn't print.  The printer is an HP LaserJet P4515, and is a network printer, added to the computers under a new TCP/IP port.
*Note: I am not able to access this computer until I have a solution, and that is pretty much all the info I have, as these computers are in a different state.:confused:

---

### Post by dca on 2008-08-12
> **ertrules22 said:**
> 
*Note: I am not able to access this computer until I have a solution

What does that mean?  Until you have a solution?  Can that workstation at least ping the network printer in question?  Is the printer connected to a jet direct (little print server box), connected directly with internal NIC on printer, or through print server?

---

### Post by ertrules22 on 2008-08-12
Sorry, I should have been more specific about that point.  I can connect to the computer, through GoToAssist, but no until I have something to tell the user.  I don't want to just sit on their computer all day and wait.  I am not sure what it's plugged into.  I know it is not directly into the computer NIC card...

---

### Post by ertrules22 on 2008-08-12
Oh, sorry, I misread something you wrote.  I think it is through a print server, if I'm not mistaken.

---

### Post by rickyjones on 2008-08-12
> **ertrules22 said:**
> Oh, sorry, I misread something you wrote.  I think it is through a print server, if I'm not mistaken.

Have you compared the configuration on a working PC against the non-working PC? Something must be different. Have you tried reinstalling the drivers on the non-working PC?

-Richard

---

### Post by dca on 2008-08-13
Well if you can connect to that workstation via GoToWhatever, that would show that their workstation is properly connected to the network which would mean the only two things you can do is delete/reinstall necessary printer drivers and delete/re-add TCP/IP printer port.
 
If all these workstations connect to the same print server and it's just one that is having an issue I would've leaned toward that workstation not even being connected to any network or not properly config for any network.

---

