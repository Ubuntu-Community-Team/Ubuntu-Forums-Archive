---
title: "Mouse not working in virtualbox"
date: 2008-10-26
forum: Virtualisation
---

### Post by alecjw on 2008-10-26
I've got a standard ubuntu intrepid system host running a server ubuntu intrepid system with xdm and fluxbox, with virtualbox guest additions and all ubuntu updates installed. Whether i start the xserver by the startx command or through the xdm daemon, the mouse doesnt work (doesnt detect mouse movements, cursor stays at the middle of the screen). I've tried dpkg-reconfigure xserver-xorg to no avail.
My xorg.conf seems to have no entry for InputDevice, i'm not sure if this is the problem, or what i need to put there if it is.


Anyone know how to fix this?

---

### Post by alecjw on 2008-10-26
Bump?

---

### Post by oldsoundguy on 2008-10-26
check to see if USB keys/mouse are enabled in bios.

((just a thought))

---

### Post by alecjw on 2008-10-26
This is virtualbox, it has no BIOS

---

### Post by oldsoundguy on 2008-10-26
then I take it, the mouse works outside of virtual box. (if not, well!!)

Have you checked xorg for the mouse specifications?

---

### Post by alecjw on 2008-10-26
Yeah it does and yep i have. As i said in the original post, there's no InputDevice entry and I dont know if there should be, or what entry i need if anything.

---

### Post by alecjw on 2008-10-26
Bump..........

---

### Post by oldsoundguy on 2008-10-26
according to this thread, there should be entries for the mouse.
[http://ubuntuforums.org/archive/index.php/t-530617.html](http://ubuntuforums.org/archive/index.php/t-530617.html)

---

