---
title: "Looking for a window manager"
date: 2007-02-03
forum: The Cafe
---

### Post by atezun on 2007-02-03
One of the things I've never managed to find is a good window manager that suits my tastes in linux. I'm really only looking for pretty much one thing and that is a window manager that maximizes like the mac, some users call it zooming as opposed to maximize in windows where it only expands the window as far it's useful and no more. I don't like wasting my screen space and frequently use multiple windows. I also wouldn't mind one with the button layout of the old classic macs, but it's not necessary. Any suggestions?

---

### Post by jbtito03 on 2007-02-03
Try aigly7glx + beryl/compiz for the zooming thing. About looking like a mac - [www.kde-look.org](www.kde-look.org) or [www.gnome-look.org](www.gnome-look.org). There are some themes available that make your desktop just the same as a mac one.

cheers

JB

---

### Post by atezun on 2007-02-03
The zooming I'm refering to isn't quite how aiglx does it. I'm not looking to actually zoom in on my screen. I only refered to it as zooming because I know some people who refer to it as that to differentiate from maximize on windows. The maximize button on windows and most enviroments causes the window to fill the whole screen rather in the mac it only expands it to the edge of the content.

As for the skinning, nah It looks great until i have to sudo into some app like synaptic.

---

### Post by v8YKxgHe on 2007-02-03
> **atezun said:**
> As for the skinning, nah It looks great until i have to sudo into some app like synaptic.

Use these commands to make apps run in root the same as your current theme:

```

sudo ln -s /home/USERNAME/.themes /root/.themes
sudo ln -s /home/USERNAME/.icons /root/.icons
sudo ln -s /home/USERNAME/.fonts /root/.fonts

```

:) 

As for the maximizing thing, I know what you mean - normally in Windows and Linux when you hit the maximize button it will take up 100% height and 100% width, but with a mac it will only take up as much as it needs to display the content. I'm not sure of any which do this though,

---

