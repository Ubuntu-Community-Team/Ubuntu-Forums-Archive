---
title: "Problems with intergrated graphic card Ubuntu"
date: 2009-07-20
forum: The Cafe
---

### Post by heroidi on 2009-07-20
I booted from a live cd in my cousins computer and it seems to have problems with the graphic card and i am gonna install ubuntu on her pc may i have the same problems after the install and how do i fix them?

reply faster please...

---

### Post by calrogman on 2009-07-20
I thought everyone knew about this by now, we had a [performance regression in the Intel graphics drivers]("http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards").

---

### Post by ugm6hr on 2009-07-20
> **calrogman said:**
> I thought everyone knew about this by now, we had a [performance regression in the Intel graphics drivers]("http://www.ubuntu.com/getubuntu/releasenotes/904#Performance%20regressions%20on%20Intel%20graphics%20cards").

Also some ATI cards, which have lost support from ATI.

Hence, I'm having to use vesa driver to get TV-out on Jaunty.

---

### Post by moster on 2009-07-20
If you have ATI and your VGA is older than HD series you will have to stay on older ubuntu or use open-source driver.

Problem is that ATI mark every card which is not HD, old and do not support newer Xorg, so we must use open source driver which is weak for now. Basically, ATI stop producing drivers :)

---

