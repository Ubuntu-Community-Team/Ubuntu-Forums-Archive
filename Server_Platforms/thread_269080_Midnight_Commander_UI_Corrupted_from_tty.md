---
title: "Midnight Commander UI Corrupted from tty"
date: 2006-10-01
forum: Server Platforms
---

### Post by southoz on 2006-10-01
I have a Ubuntu 6 LAMP server running on a Dell Optiplex GX260 SFF. The problem im having is when using tty the Midnight Commander UI is all messed up (incorrect ascii character for boarders and the trees move 2 characters to the right until i reselect the item, mc's pop up dialogues are unreadable). When using ssh from the tty on the LAMP server to another linux box (NSLU2 - Unslung 6.8 beta) the same problem persists (to a lesser degree).

If i ssh (putty) into both boxes from a windows machine the mc interface is fine. The term is xterm-color which i don't think is causing the problem.

I believe the problem is with the Linux tty output. I have tried 3 graphics cards, Onboard 8MB, Sis 630 32MB and Geforce 4 MX440 64MB.

Anyone else have this problem or a similar problem with Ubuntu Server tty output?

Cheers

---

### Post by karevn on 2007-11-12
Don't worry, it's easy. Try go to Putty's menu => Change Settings => Translation => and change encoding to UTF-8.
This must help :) Good luck!

---

