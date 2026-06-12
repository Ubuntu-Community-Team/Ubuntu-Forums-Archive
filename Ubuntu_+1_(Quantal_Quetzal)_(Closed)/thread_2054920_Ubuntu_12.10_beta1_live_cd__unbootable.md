---
title: "Ubuntu 12.10 beta1 live cd  unbootable"
date: 2012-09-08
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by macstevejb on 2012-09-08
2 machines; one laptop with Intel graphics, one desktop with nvidia graphics.

Live cd boots fine in the laptop but displays weird graphical glitches when attempting to boot with nvidia machine.

Conclude that there must be a problem with nvidia graphics right now.

Tried nomodeset but only gets as far as login screen then freezes in low graphics mode.

Have had problems with every new iteration of Ubuntu that comes along where nvidia graphics are concerned.

Sure hope this gets fixed before final release.

Bug refers:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1039202](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1039202) 

regards:(

---

### Post by vasilbelarus on 2012-09-08
I had the same problem, but then find the solution.
You should only delete "quiet splash" from boot options and all will be fine. :)

---

### Post by grahammechanical on 2012-09-08
Or select nomodeset from the F6 menu options. That is what works for me. But this should not be needed.

I do not need to set nomodeset with any of the other live CDS, such as 10.0.4, 11.10 and 12.04.1. I have just run tests on this.

So, I agree with your comment that it is unbootable.

Regards.

---

### Post by macstevejb on 2012-09-08
Ok problem solved.

Downloaded the latest daily build (64bit), used the nomodeset option and successfully booted the live cd albeit in low graphics mode.

Then installed, reboooted into desktop with nouveau graphics.

Installed latest nvidia driver by installing nvidia-current via apt and bingo..now up and running.

This thing rocks even in Beta!

regards :)

---

### Post by vasilbelarus on 2012-09-08
When I used nomodeset screen was in low resolution and only wariant with out "quiet splash" worked.

---

### Post by amikot on 2012-09-12
Problem with NVidia is not limited only to splash screen.
I have tested on three different nvidia graphics cards and all of them, i noticed crashes (total freezes) when runing liveCD (one time when selecting install or try).  

Even when upgrading from 12.04 to 12.10 there is problem with nvidia. 
Everything looks fine but when trying to play WOW on wine,  after few seconds/minutes i have total system crash (freeze). 

When changed to nouveau i have smaller FPS with low quality, but its stable.

---

### Post by humanisfood on 2012-09-12
> **vasilbelarus said:**
> I had the same problem, but then find the solution.
You should only delete "quiet splash" from boot options and all will be fine. :)
worked for me.

---

