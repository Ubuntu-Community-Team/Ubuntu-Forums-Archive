---
title: "X won't start after today's update on ubuntu 14.04"
date: 2014-04-03
forum: Ubuntu Development Version
---

### Post by jatinps on 2014-04-03
Hi all - I posted a bug 1302309 but unsure if it's just an issue and someone here can help. Thanks for any guidance!

[https://bugs.launchpad.net/ubuntu/+bug/1302309](https://bugs.launchpad.net/ubuntu/+bug/1302309) 

"I'm using a Lenovo x230 laptop and have been on ubuntu 14.04 alpha/beta for last few months. Everything was fine with daily updates, till I updated today and now X won't start up. The screen just hangs on the ubuntu logo screen and sometimes gives a message "waiting for network configuration" or "waiting for 60 more secs for network configuration". However it goes nowhere and does not give me a login screen. If I change display manager to lightdm, I get a login screen but nothing happens post login - just the wallpaper n mouse pointer. I've checked and I do have network connectivity from the terminal (ctrl-alt-f1). I've also tried uninstalling and reinstalling xserver-xorg and then doing a dpkg-reconfigure xserver-xorg but didn't help. Booting in fail safe graphics also doesn't bring up X. Seems like an upgrade issue or bug. Let me know if logs are needed."

---

### Post by obake2 on 2014-04-04
I'm also experiencing the same problem. Beside the "waiting for network configuration" and "giving up fo network configuration" (writing from memory, the quote is not verbatim), I also get
" /dev/mapper/cryptswap1 is not ready yet or not present"

---

### Post by zika on 2014-04-04
Try booting with &#8222;text&#8220; in kernel-boot-line and then investigate (in tty) what is happening...
There is trouble with pixbuf [http://ubuntuforums.org/showthread.php?t=2214867](http://ubuntuforums.org/showthread.php?t=2214867) so get sure You're not affected with that bug...

---

### Post by jatinps on 2014-04-04
its fixed after today's updates!

---

