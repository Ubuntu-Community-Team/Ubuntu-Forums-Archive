---
title: "Will a motherboard BIOS update solve a screen problem?"
date: 2015-09-28
forum: Ubuntu Development Version
---

### Post by lee295012-gmail on 2015-09-28
Rotation is broken for me in Wily using a radionsi driver, i made a bug report and was told to upgrade my mobo bios.
even when my report said it was working correctly before on previous versions is it likely an update will fix it?

seems to me a risky option for an unlikely chance it will fix anything.



EDIT: this is more of a question about what the ubuntu staff are asking people to do rather that finding a solution, until i'm shown otherwise i believe this is a driver problem as arch has the same Xorg version and works correctly.

---

### Post by buzzingrobot on 2015-09-28
I'd want to know what, specifically, in the BIOS update fixes the rotation problem, and then I'd want to see if my motherboard/BIOS vendor lists that fix in a README or a changelog.

---

### Post by Yellow Pasque on 2015-09-28
I used to be a member of bug triaging, and I will tell you this: Don't bother trying to debate relevant BIOS changes (or lack thereof) with the person triaging that bug. You're just wasting your time.

---

### Post by jimmy-frydkaer on 2015-09-29
Would be a lot less risky to try another graphics card than mess up your mobo with a BIOS update - Chances are, like you said it yourself, that it's a driver problem. Simply try if you can downgrade your installed driver (or get a newer one) before anything else.

---

### Post by lee295012-gmail on 2015-09-29
> **buzzingrobot said:**
> I'd want to know what, specifically, in the BIOS update fixes the rotation problem, and then I'd want to see if my motherboard/BIOS vendor lists that fix in a README or a changelog.

From all my years on the net i've read you should never update the bios unless you know an update will fix your specific problem.
getting people to do this as its on your triage tick list is irresponsible imo.
what would have been next in the tick list, update the radeon card bios? another great risk.

---

### Post by jerrylamos on 2015-09-29
Wily Xorg is a real mess on this Lenovo M58P dual 3GHZ 64 bit.  Display images and most text is hashed sideways unreadable.  Now wallpaper is hopelessly smeared, but displaying the jpg with browser is O.K., sometimes turining on screen capture fixes some of the display.

A while back one of the ubuntu bug shooters found a bios update pointer from a couple years ago - note, my opinion screw up flashing the bios I've got a dead computer.

Solution with Wily is install a kernel example 3.17.1 which works just fine.  Since November 2014 ubuntu development did something to the kernel that messed up xorg.

---

### Post by lee295012-gmail on 2015-10-20
The "Driver" problem is now fixed in git :)

---

### Post by jerrylamos on 2015-10-20
I'll keep updating daily - wonder when the git fix will hit update....

Currently Wily still a mess, but using Trusty LTS inux-image installed into Wily works.

---

