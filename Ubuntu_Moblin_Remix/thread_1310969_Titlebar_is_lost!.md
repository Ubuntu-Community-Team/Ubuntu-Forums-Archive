---
title: "Titlebar is lost!"
date: 2009-11-02
forum: Ubuntu Moblin Remix
---

### Post by lalilali on 2009-11-02
When I run programs on netbook remix the titlebar of the program should be in the little black area above the program, but it is'nt. And an upgrade to 9.10 did'nt solve the problem. :(

Any suggestions on haw to get it back?

Lali, Sweden

---

### Post by cmcanulty on 2009-11-02
Try changing fast user switching. I disabled mine as only me uses computer and it made title bar disappear so I enabled it and title bar was back

---

### Post by ghostborg on 2009-11-02
I'm not familiar with remix as I am running the standard desktop edition.
Do not install the following if you are not running Compiz-fusion desktop.
The wobbly windows and cube.
In my case I am running the Compiz desktop and I use the Compiz-fusion icon to "Reload Window Manager" to get my titlebar back. The Icon can be found in the synaptic package manager by typing in fusion-icon. Once installed it will be under Applications==>System tools, then launch and a blue box with an arrow should appear on your upper panel, right click and select Reload Window Manager.

---

### Post by lalilali on 2009-11-02
I've tried switch to desktop mode and back, several times, it does'nt help, =/

I am not running compiz.

I remember I got an error-message just before the titlebar disapaired, but I cannot recall the message. I think it was a modul that crashed or something.

---

### Post by tenkara on 2009-11-04
Hi, Lali

I'm a total noob, but I just stumbled upon an answer to restoring the titlebar within UNR or Desktop. Enter gconf and navigate to maximus. There are not very many choices there, but the last choice is labeled "undecorate". If there is a check mark next to that label, simply remove it and Voila! the title bar is back. I hope this helps.

Take care,

Tenkara - USA

---

