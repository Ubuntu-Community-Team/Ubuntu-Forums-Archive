---
title: "Another Nvidia driver"
date: 2012-10-12
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by cariboo on 2012-10-12
This email came from Bryce Harrington on the ubuntu-devel mailing list:

> We are introducing new 'experimental' driver packages for NVIDIA, which
will be available via the Additional Hardware Drivers setup tool for
12.04 user (and 12.10 too).  These packages will provide NVIDIA's beta
drivers, which are required for certain commercial games.

There is an nvidia-experimental-304 package which isn't really a beta
driver, just what we've been using for testing.  The first real beta
package will be nvidia-experimental-310; it should be coming some time
later this month.

For Intel, there will be a PPA upgrade available for 12.04 gamers.

For more details, see my blog:
  [http://www.bryceharrington.org/wordpress/?p=91](http://www.bryceharrington.org/wordpress/?p=91)

Bryce

---

### Post by VinDSL on 2012-10-13
Hrm...

Seems like a lot of trouble, to go to, just to play video games.

Is there some clarion call for drivers like this?!?!?

---

### Post by cariboo on 2012-10-13
Maybe the devs are gamers in their off hours. :) Actually I saw a post by Martin Ownes (DoctorMo) on the Planet, where he'd been playing Linux compatible games using the nouveau driver without realizing it.

---

### Post by bird1500 on 2012-10-13
> **VinDSL said:**
> Hrm...

Seems like a lot of trouble, to go to, just to play video games.

Is there some clarion call for drivers like this?!?!?

All users of all OSes face the trouble of having to install newer video drivers (manually) to correct game glitches, even on win 7, though to a lesser extent.

For example with my GeForce 560Ti I still have issues with Crysis 2 on win 7, after I updated the Nvidia driver (manually obviously) it became more stable.

It makes sense that Canonical is trying to automate this process since on Linux it's a lot harder to install a video driver cause ATI/Nvidia/Intel have various (weird) requirements, e.g. to install Nvidia I normally have exit X first, to update the Intel driver you have to update other packages too, etc.

Currently Canonical's solution isn't good enough though, e.g. in that dialog it doesn't show up what driver version is in each option, etc.

---

