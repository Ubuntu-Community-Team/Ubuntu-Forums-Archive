---
title: "Custom non-standard configurations"
date: 2010-07-17
forum: The Cafe
---

### Post by linux18 on 2010-07-17
If your reading this, your probably thinking what do I mean "non-standard comfiguration" and the answer is simple: anything that you've configured completely different from what the nornal use is. For example, I want this particular session to be as stable as debian. What I did was start xterm, then run ```
 konsole & 
```

then in the terminal open five tabs each running one command:
```
 fluxbox --replace 
```
for lightweight window management
```
 nm-applet 
```
for networking
```
 alsa-mixer 
```
to set volume and such 
```
 uzbl 
```
a very lightweight web browser
```
 vlc 
```
to play music 

In the end, I have a desktop thats quite unique. Instead of opening programs in fluxbox and relying on that to control everything, I only need xorg to work. The beauty of this is that any program can fail or freeze ( except xorg ) and the session would be completely recoverable. If anything did freeze and become unresponsive I can just close the tab in the terminal and kill it then respawn it. If the terminal itself failed I can respawn through the xterm terminal. This kind of thing isn't normal ( I don't hear anyone else saying they're controlling every application they start from a terminal ) So what about you, do you have any weird configurations or scripts?

---

