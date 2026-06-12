---
title: "Rant: getty leaves last screen of text"
date: 2005-02-10
forum: The Cafe
---

### Post by rkn on 2005-02-10
I notice that some distros have shells that are setup to clear the screen after logout while others leave the last screen of text.
I would like to always erase the screen when someone logs out.
 I took a look at a couple other /etc/inittab files. Some of the distro use mingetty and some have handled clearing the screen with a .bash_logout file. 

I installed mingetty & edited inittab to use mingetty. Now by default ths screen is cleared on logout.


Bob

---

### Post by jdong on 2005-02-10
Simple. Add a file "/etc/bash.bash_logout", with the command **clear**.

---

