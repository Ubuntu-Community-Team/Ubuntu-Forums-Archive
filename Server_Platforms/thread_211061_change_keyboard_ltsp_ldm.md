---
title: "change keyboard ltsp ldm"
date: 2006-07-07
forum: Server Platforms
---

### Post by tomcoussement on 2006-07-07
I installed edubuntu today and tryed ltsp.

Everything works fine exept that I don't find where to change the keyboard layout for the graphical login (ldm?) on the clients.](*,) 

I want to change it to belgian keyboard layout (azerty).

Hope someone can tell me where to change that...

Thank you!

---

### Post by Kalif on 2006-10-31
Hi,

when your /opt/ltsp/i386 has been set up by
ltsp-build-client command, you will have to
create a lts.conf file in /opt/ltsp/i386/etc
in that file you may write a line with:
XkbLayout = xx
where xx is the country code for your prefered
keyboard layout.

There may be quite a lot of other options to
set when you are working at it :-)

Best,
K.

---

