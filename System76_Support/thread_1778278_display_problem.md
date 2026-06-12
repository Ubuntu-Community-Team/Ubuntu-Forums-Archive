---
title: "display problem"
date: 2011-06-08
forum: System76 Support
---

### Post by dsyskowski on 2011-06-08
I have had a Meerkat NetTop for two months now and everything out of the box has been running fine.  I have it attached to an HP 22" monitor through a KVM switch.  Under Ubuntu 10 I was able to achieve the full resolution of 1680 x 1050.

Just the other day I bit on the upgrade to Natty and since then I have had monitor and display problems.  The system seems to think that I have two monitors attached one being named laptop. And it sets that laptop to 1024 x 768. But I only have one.  Any attempt I make to switch to the HP 22 (and the system knows it is there by that name) results in either a black screen or once I was able to achieve the higher resolution but with a black band across the top quarter.

I sense a driver problem but have not been able to find anything that would seem to help in the forums.

Any suggestions about what to do would be appreciated.

---

### Post by isantop on 2011-06-09
We've seen several issue with natty an Intel graphics. In order to fix this, first make sure your system is fully up to date, then turn on the "External Monitor" and disable the "Laptop" monitor. You should see the black bands, which is okay. Just confirm that you want to keep the new resolution. Then, press Alt+F2, and enter the word unity in the text box, followed by enter. That will reload the desktop environment, and leave it free of the black borders. Now, simply hit "Make Default" to make the change permanent and system-wide.

---

### Post by dsyskowski on 2011-06-20
Thank you.  This fixed the problem.

---

