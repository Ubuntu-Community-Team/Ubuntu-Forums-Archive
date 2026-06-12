---
title: "Screenshots with virtualbox-ose?"
date: 2008-07-05
forum: Virtualisation
---

### Post by altonbr on 2008-07-05
I'm used to VMware Server 1.0.x allowing me to take a screenshot of the guest, only showing the guests screen, as if I took the screenshot from within the guest and then saving the screenshot on the host.

Is there anyway I can do this with virtualbox-ose in Hardy? (1.5.6)

I have a lot of server screenshots I'd like to take and it'll become annoying to have to use xwd and then ssh all of them.

Thank you!

---

### Post by siepo on 2008-07-07
I use GIMP on the host: File, Acquire, screenshot. You can select the virtualbox window and ask GIMP to exclude window decorations.

If you start vms with VBoxSDL then you shouldn't get any vbox controls, just the vm and the window decorations.

---

### Post by altonbr on 2009-07-23
I'm amazed that VirtualBox 3.0 (even the non-ose edition) still does not have a 'screenshot' feature.

---

### Post by biriani on 2010-01-20
For those with Windows guests that may stumble across this a very primitive work around is to use the on-screen keyboard and hit alt+print screen.  It worked for me when I had to prepare some documentation and needed some Windows screen shots that I did not want to crop.

---

