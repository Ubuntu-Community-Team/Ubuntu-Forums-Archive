---
title: "Direct3D woes"
date: 2008-04-30
forum: Virtualisation
---

### Post by kragen on 2008-04-30
I've just tried out VirtualBox - its fantastic - fast, easy to use, integrates well with the desktop, the only bummer is that I really need some sort of direct3D virtualisation (not necessarily fast, just any at all), which doesnt look like its going to happen anytime soon :(

In contrast, VMWare server is horrible - The installation is longwinded with loads of pointless questions, plus I have to hack it to get it to work with ubuntus "cant login as root" philosophy. Its not fully working even after playing around with it for hours, and the direct 3d support is still experimental...

Any suggestions on alternatives to VMWare for getting windows apps to run with direct 3d? Wine is a no-go btw, visual studio doesnt play nicely with wine according to the app-db.

---

### Post by 10wattmindtrip on 2008-05-01
> **kragen said:**
> I've just tried out VirtualBox - its fantastic - fast, easy to use, integrates well with the desktop, the only bummer is that I really need some sort of direct3D virtualisation (not necessarily fast, just any at all), which doesnt look like its going to happen anytime soon :(

In contrast, VMWare server is horrible - The installation is longwinded with loads of pointless questions, plus I have to hack it to get it to work with ubuntus "cant login as root" philosophy. Its not fully working even after playing around with it for hours, and the direct 3d support is still experimental...

Any suggestions on alternatives to VMWare for getting windows apps to run with direct 3d? Wine is a no-go btw, visual studio doesnt play nicely with wine according to the app-db.

Well, I'm not entirely sure you'll get what you want. I heard that Parallels does some sort of 3D, but I'm not certain how well it works. Wine isn't exactly the best choice if you want to run Visual Studio in it. 
It sounds as though you're into 3D programming. Maybe try OpenGL under a native environment? Linux provides some really good IDE's for that sort of thing. It'll be cross-platform too.

Cheers.

---

