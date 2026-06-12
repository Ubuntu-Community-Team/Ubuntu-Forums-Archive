---
title: "Minimum Graphics"
date: 2005-05-21
forum: Server Platforms
---

### Post by sciurus on 2005-05-21
I have a ubuntu system at home running Samba for my family to use as file storage. My university has blocked peer-to-peer programs, so I'd like to be able to run them at home and access them remotely. The problem is that the only soulseek clients are graphical. What is the bare minimum set of packages that I will need to install to vnc into my server at home and run Nicotine*? I want to keep the system booting to the console and only running anything X when I start a vncserver.

*I may run aMule as well, since i'm stuck using one program with a GUI already and mlDonkey is such a mess.

---

### Post by sethmahoney on 2005-05-21
[QUOTE=sciurus]I have a ubuntu system at home running Samba for my family to use as file storage. My university has blocked peer-to-peer programs, so I'd like to be able to run them at home and access them remotely. The problem is that the only soulseek clients are graphical. What is the bare minimum set of packages that I will need to install to vnc into my server at home and run Nicotine*? I want to keep the system booting to the console and only running anything X when I start a vncserver.

*I may run aMule as well, since i'm stuck using one program with a GUI already and mlDonkey is such a mess.[/QUOTE]
 aMule 2.0 has a non-graphical daemon, but I have no idea how to work it.  You might look into that.

---

### Post by sciurus on 2005-05-21
[QUOTE=sethmahoney]aMule 2.0 has a non-graphical daemon[/QUOTE]
Cool. The official edonkey client has one as well, but not with a web interface. Still, unless someone more experienced than me can package [museekd](http://museek.thegraveyard.org/) (the daemon part of museek, an alpha-quality soulseek client) and [mucous](http://thegraveyard.org/daelstorm/mucous.html) (a curses interface to museekd) I'm stuck with my original question.

---

### Post by sciurus on 2005-05-23
My solution was xfonts-base, tightvncserver, and xfce4.

---

