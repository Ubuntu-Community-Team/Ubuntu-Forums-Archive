---
title: "64-bit vs. 32-bit Ubuntu studio"
date: 2008-11-07
forum: Ubuntu Studio
---

### Post by Coolbreeze... on 2008-11-07
Is there any difference between the 64bit and 32bit versions of Ubuntu Studio?  I'm thinking mostly in the area of available programs that come with the OS...are there programs that come with the 32bit that don't with the 64bit...or opposite.  Also, is there a major speed advantage with the 64bit? Thanks:)

---

### Post by cotcot on 2008-11-07
64 bit support is generally very good. Exceptions exist of course (for instance the printer driver for epson printers from epson avasys). There are programs that only exist in 32 bit  but you can run these on a 64 bit installation (search for tutorials how to do this). 
Speed gain depends on the application. Speed gain varies from 0 to 30 % as far as I could check on the apps I run.

---

### Post by Coolbreeze... on 2008-11-07
Do the have a List some where that I have not found that shows the different programs?

---

### Post by Stochastic on 2008-11-07
I was under the impression (from previous threads on this subject) that until you have 4GB+ of RAM there's no real performance difference on 64bit versions.

---

### Post by duffrecords on 2008-11-08
If you're planning to use VST plugins, you'd be better off using 32-bit Ubuntu Studio for now.  There are plenty of 32-bit VST clients available for Linux but the 64-bit versions are still very nascent.  Although the latest bleeding-edge 64-bit JACK now supports 32-bit clients, you will understand the true meaning of dependency hell when trying to compile 32-bit software on 64-bit architecture.  Also, consider [FST]("http://www.joebutton.co.uk/fst") (which is required in order to compile Ardour with VST support) hasn't developed since 2006.  It's unlikely we'll see a 64-bit version of that, unless the developer or someone else picks up the project again.

---

### Post by Ng Oon-Ee on 2008-11-09
> **Stochastic said:**
> I was under the impression (from previous threads on this subject) that until you have 4GB+ of RAM there's no real performance difference on 64bit versions.

Depends on who you listen to, of course. The big difference is of course from the RAM, but the underlying change to pointer-definitions and stuff do help with SPECIFIC programs.

I would think 64-bit is more for future-proofing, in a couple of years time it would be quite standard. Of course, if you're used to reinstalling your OS every 6 months to keep up with the Joneses (or the Ubuntus, as the case may be) that's less of an issue.

---

