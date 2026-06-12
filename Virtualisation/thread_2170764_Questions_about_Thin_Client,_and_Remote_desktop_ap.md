---
title: "Questions about Thin Client, and Remote desktop applications."
date: 2013-08-27
forum: Virtualisation
---

### Post by relink2013 on 2013-08-27
Ive been trying to research different ways to stream apps and games from a windows computer to my Ubuntu machines. I've looked into things like VGWare from LucidLogix (unfortunately I don't think this was ever released), StreamMyGame, XenApp. Unfortunately for me I don't really know anything about this, and I don't even really know what to look for, so I thought I would ask here. 

Basically what I would like to do is have my gaming rig act as my server, with all my games and important software (e.g AutoCAD) installed, and then be able to open or "stream" those apps to any of my other computers. I've seen it done, specifically with Microsoft office, where someone has the Microsoft Word icon right on their Unity launcher, and when they click on it, it looks as if Office is just running natively in Ubuntu, but its not, its actually being streamed from a Windows computer somewhere else in the building, but it runs so seamlessly you'd never know it. I have also seen people do this with games as well.

What programs would allow me to accomplish this? Hopefully free or at least affordable, but Ill take any options. Also what is this technology called, and where can I read more about it? And which option would give me the most seamless experience, that's the only thing I don't like about StreamMyGame is that you have to use their player to access your apps, I would like this to be as seamless as possible.

EDIT: I have also found an  app called Kainy, but the full version seems to only work on Android, they have a chrome app, but it seems to only work in demo mode.

Also what about Hyper-V?

---

### Post by relink2013 on 2013-08-28
Anyone? I know this is possible, Im just trying to find the best way to do it. 

Also I have found nVidia GRID.

---

### Post by relink2013 on 2013-08-29
I have also come across the [nvidia Shield]("http://shield.nvidia.com/"), which is open source, so we may see a Linux port eventually. But for now, does anyone have any input on currently available options?

---

### Post by TheFu on 2013-09-07
I can only guess that your terminology is not exact and expectations seem a little high for what is possible.
[http://www.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://www.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) explains the ways that Linux/UNIX systems do this sort of stuff.  For lite games, it can probably work.  Don't expect video streaming to work very well.  Going the other way - is much farther along.  There's a remote desktop protocol called "spice" that can be impressive, but not with Windows as the host.

For Office-like apps, VNC or RDP is fine. Review that link.

---

