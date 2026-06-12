---
title: "Server for Newbe"
date: 2009-10-23
forum: Server Platforms
---

### Post by bloggus on 2009-10-23
Hi all,
 
So, I'm really new at Linux servers, and it as long time ago I used Unix/Linux.
 
I have discovered that Ubuntu is distributed with "No X server by design", and that is probably what most of administrators like, but for somebody that would like to learn in the process, X server or any graphical desktop applications would be of much help.
 
I could go with RedHat, but Ubuntu is what I would like to try.
 
What do you suggest to do? Is is hard to install X server or any graphical desktop applications on the server version??

---

### Post by sahabcse on 2009-10-23
Just to make sure run sudo apt-get update Then run
sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo /etc/init.d/gdm start
sudo dpkg-reconfigure xserver-xorg
Gdm is what handles your x system starting automatically instead of entering start x at the command line each time you boot. The reconfigure runs the xserver setup so you can configure your system monitor, video card etc.
sudo /etc/init.d/gdm.start

---

### Post by Iowan on 2009-10-23
The [semi-official]("https://help.ubuntu.com/community/ServerGUI") version.

---

### Post by windependence on 2009-10-24
You will, however be seriously handicapping yourself by providing a "crutch". A GUI does not help you learn the CLI in any way, it's just something that let's you cheat without learning anything. If you really need a GUI, just use the desktop version. Unless you are using server class hardware that can take advantage of the optimizations in the server kernel, there is no difference between the two for "learning" purposes.

-Tim

---

### Post by KeithEckstein on 2009-10-24
Totally agree with **windependence** - you'll learn so much more if you try to do stuff at the command line.  

Hey, you might want to have another machine with a graphical desktop so that you can Google stuff and document stuff in an easy way but, the more effort you put into learning the command line, the better you will be with Linux.


In a way, it's the being confused that helps!  You end up having to use *man* to work out what's going on and, by doing that, you learn so much! 

If you must have a graphical interface on your "Server" (and I do on one of my servers - so it can act as a "Disaster Recovery/Business Continuity" machine) - I detail two tried and tested ways of installing a lightweight GUI on Ubuntu/Debian at [http://www.kmeckstein.com/server_with_x.html](http://www.kmeckstein.com/server_with_x.html) (a Server with X Appeal)

Try the first way first (xfce) - I think it's stunning, how fast it is.  

The only trouble for me is, I do need use Gedit and Nautilus (especially Nautilus scripts) so I tend to end up installing minimal Gnome.

All the best

Keith

---

### Post by bloggus on 2009-10-24
Thanks for all help and suggestions. My intention was to have a graphical interfcae but run command line to learn and see what happens. I have to start somewhere. I used to use Unix-systems back at University, 13 years ago, but it was a long time ago :)
 
Any newbe book you recommend to have on the side? Exspecially one for learning how to manage linux server the best way?

---

