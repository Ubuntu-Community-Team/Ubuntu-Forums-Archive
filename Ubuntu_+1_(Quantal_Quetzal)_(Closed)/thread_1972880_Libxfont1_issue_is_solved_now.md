---
title: "Libxfont1 issue is solved now"
date: 2012-05-04
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-05-04
The buggy libxfont_1.4.5-1 package is now replaced and a working version is published in Quantal repos.

Here:
[https://launchpad.net/ubuntu/quantal/+source/libxfont/1:1.4.5-2](https://launchpad.net/ubuntu/quantal/+source/libxfont/1:1.4.5-2)

> [B][SIZE=2]Changelog
libxfont (1:1.4.5-2) unstable; urgency=low     * Ease sync for Ubuntu: strip -Bsymbolic-functions from LDFLAGS     (LP: [#992745]("https://launchpad.net/bugs/992745")).
-- Cyril Brulebois <email address hidden>  Thu, 03 May 2012 19:59:46 +0200[/SIZE][/B]

                


---

### Post by chrismine on 2012-05-04
Thanks...

---

### Post by MG&amp;TL on 2012-05-04
Great, just pulled it in. I was just starting to think about an apt pin.

---

### Post by Cheesemill on 2012-05-04
Thanks,

Was wondering when this would be solved. Removing my apt-pin and updating now......

Edit - Running fine here after a reboot.

---

### Post by JMB74 on 2012-05-04
Working fine here, after having to downgrade to the precise package temporarily.

---

### Post by fjgaude on 2012-05-04
Yes, working fine here: an update overwrote the precise file.

---

