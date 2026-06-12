---
title: "Virtual Terminal/GDM in Ubuntu"
date: 2020-12-09
forum: Virtualisation
---

### Post by tushardesai on 2020-12-09
I was trying to play around with Virtual Terminals on my Ubuntu 20.04 guest running inside VirtualBox on Windows.

1. I was expecting the Graphics Environment to be running on VT#7 or may be VT#1. But, it seems to be running on VT#2. 
2. VT#1 shows the greeter but when I login, it punts me to VT#2, while VT#1 continues to display the greeter. 
3. Nothing shows up on VT#7 (i.e. no login prompt) after a momentary display of some text.

VT#3-6 show the expected login prompt.

Is this a bug?

---

### Post by slickymaster on 2020-12-09
Thread moved to **Virtualisation** for a better fit

---

### Post by tea for one on 2020-12-09
No, it is not a bug - this is the TTY access used in Ubuntu 20.04.

Ctrl Alt F1 > Login Page
Ctrl Alt F2 > GUI Desktop
Ctrl Alt F3 > TTY3
Ctrl Alt F4 > TTY4
Ctrl Alt F5 > TTY5
Ctrl Alt F6 > TTY6

Other members of in the Ubuntu family (i.e. Xubuntu etc) use different shortcuts.

---

### Post by tushardesai on 2020-12-10
Thanks for the response. If I want to play around with these, e.g. add more VT's or change the VT assignment for the greeter or GUI what is a good place to start?

---

