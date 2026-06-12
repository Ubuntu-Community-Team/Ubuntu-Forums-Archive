---
title: "Running Karmic Alpha 6 in Virtualbox changed settings in HOST OS (Ubuntu Jaunty x64)!"
date: 2009-10-03
forum: Virtualisation
---

### Post by martini1179 on 2009-10-03
Hello, 

I'm a virtualization noob, but I thought it wouldn't hurt to try to fiddle with Karmic Alpha 6 (sidenote: I know that the beta is out, but I was more interested in getting everything running before I upgraded the alpha to beta). 

So I ran the alpha today, and the strangest thing happened -- the icons, the controls, the colors on the *HOST* machine changed. The sounds scheme was differnt too. For the first time I could hear a bongo drum sounds when I minimized/maximized Chrome. 

Quitting the VM and restarting Chrome fixed the problem. 

But.... 

1) how can I be sure that no other settings or files were altered? 

2) after I rebooted the machine, I got a "routine check of drives," which I let run. This makes me wonder if, instead of it being a routine file check, that something didn't happen under the hood when Virtualbox messed up. Any thoughts?

---

### Post by timgood on 2009-10-19
Exactly the same thing happened to me running Karmic Beta under VirtualBox in Jaunty - settings changed included gnome-panel, Evolution Mail (lost account settings), Compiz settings (window manager set to default etc.) Surely this represents a major security headache? For your info my post on this matter is here: [http://ubuntuforums.org/showthread.php?t=1295280](http://ubuntuforums.org/showthread.php?t=1295280)

This is not good!

---

