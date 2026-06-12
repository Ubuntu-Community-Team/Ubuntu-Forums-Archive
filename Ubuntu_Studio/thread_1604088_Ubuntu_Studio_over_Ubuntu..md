---
title: "Ubuntu Studio over Ubuntu."
date: 2010-10-23
forum: Ubuntu Studio
---

### Post by imnotanerd on 2010-10-23
How can I install Ubuntu Studio over Ubuntu 10.04?

---

### Post by cchhrriiss121212 on 2010-10-23
Open software center (or synaptic package manager) and search for ubuntu studio, then click install on the packages you want.

---

### Post by imnotanerd on 2010-10-23
I mean the whole Ubuntu Studio. Like the look of it, the cool animations, and other stuff. Not just the programs.

---

### Post by cchhrriiss121212 on 2010-10-23
Yes it is all there in the repositories.

---

### Post by imnotanerd on 2010-10-23
Just downloaded them. Thanks :)

---

### Post by grahammechanical on 2010-10-24
Imnotanerd

Can you now access the internet?  Either through wireless or wired? I am trying out Ubuntustudio on it own partition and I am finding it very difficult to get internet access. The settings are correct, eth1 is listed as Active but disconnected.  I wanted to set Ubuntustudio as my main working installation. If your way works I might try it myself.

Regards.

---

### Post by perspectoff on 2010-10-24
Another alternative, if you only want certain parts of Ubuntu Studio, is to start tasksel from a command-line interface Terminal or Konsole:

 sudo tasksel

You will see a list of automated installations. I think the components for Ubuntu Studio are among them:

Video creation and editing suite
Audio creation and editing suite
2D/3D creation and editing suite

Tick the boxes for the stuff you like and hit ok. They will be installed for you. Easy.

---

### Post by trulan on 2010-10-24
> **grahammechanical said:**
> Imnotanerd

Can you now access the internet?  Either through wireless or wired? I am trying out Ubuntustudio on it own partition and I am finding it very difficult to get internet access. The settings are correct, eth1 is listed as Active but disconnected.  I wanted to set Ubuntustudio as my main working installation. If your way works I might try it myself.

Regards.
I would recommend that you try installing WICD network manager.  You'll probably need to manually set it to use eth1 as well, but I have found it much better at getting things right than gnome network manager, or worse yet, no network manager at all like Ubuntu Studio gives by default.  WICD does't support dsl/PPPoe authentication or whatever (I may be mixing my terms here, sorry), but it's the only network manager I've found that doesn't make me reboot just to turn my wireless card on.  For wireless internet you can't beat it, IMO.

---

