---
title: "Problems upgrading dist via ssh?"
date: 2007-10-26
forum: Server Platforms
---

### Post by meighty on 2007-10-26
I have a remote file storage my friends house. Right now its running 7.04 and would like to upgrade to 7.10. I only have ssh access 90% of the time. Is it possible to upgrade via ssh? If so, are there any problems i should watch out for?

---

### Post by thelocust on 2007-10-26
I noticed after an upgrade your ssh key changes so you have to delete your "~/.ssh/some file" in order to connect. Theres probably other way to do it but just a heads up.

---

### Post by meighty on 2007-10-26
I see...so an upgrade via ssh is probably not the greatest idea. bummer.:(

---

### Post by Brazen on 2007-10-26
It shouldn't be a problem.  I've done dist-upgrades on Debian and Ubuntu servers through ssh and I don't remember running into any issues.  You'll probably want to do it in a screen session though (I always do, for everything really).

---

### Post by MJN on 2007-10-26
Just cross your finger's and hold your breath you should try a reboot! (which you ought to do (reboot that is!) even if it's not necessary - many a problem can only manifest itself during boot).

Mathew

---

### Post by meighty on 2007-10-26
I think i may give it a try this evening and just hope for the best. After that, just throw the reboot command wait in agony for it come back up. 

Thanks for the pointers!
:guitar:
Metal

---

