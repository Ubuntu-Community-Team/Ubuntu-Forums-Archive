---
title: "Collaboration Software and Tools"
date: 2007-03-01
forum: The Cafe
---

### Post by HumanAnarchist on 2007-03-01
Hello, 

I got some questions about collaboration software and tools. 

At my workplace we want to work at different physical locations, but still want to talk together, view the screen of each other and use webcams. The OS's at use are Ubuntu and Win XP 

I thought that 

[LIST]
[*] using Skype for voice, works fine on Linux and great on Windows
[*] VNC for remote viewing of screens on Ubuntu
[*] Windows Remote Desktop for viewing Windows XP from Ubuntu
[*] Ekiga [Ubuntu] + netmeeting [WinXP] for webcam
[/LIST]

I thought about using [www.stickam.com](www.stickam.com) for voice, chat and video, but it does not work that well. The lag is almost 15 sec... :(

I also thought about using Ventrilo [http://www.ventrilo.com/](http://www.ventrilo.com/) for voice, but the Linux client is still in development :(
Edit: TeamSpeak2 looks promising 

Are there other tools that I should look into? 

Any ideas to make this setup work better?

Best Regads,
-ha-

---

### Post by maniacmusician on 2007-03-01
Well, if you're using a KDE desktop, you can use the tools Krfb (Remote desktop server) and Krdc (Remote desktop client). It supports a bunch of protocols, including VNC, and it generally works flawlessly when done linux-to-linux. If you have a good VNC server set up on Windows, then you can use Krdc to connect to that as well (though then you might as well just use the VPN client that comes with Ubuntu)

Anyways, I've found that for Linux-to-linux remote desktop viewing, Krfb is quick and painless. I've never attempted to VNC into a Windows computer.

On another note; why not just use Ekiga for voice **and** video? Skype is a piece of junk on Linux. Of course, make sure you have webcams that work in Linux. That'll probably be the hardest part.

---

### Post by HumanAnarchist on 2007-03-03
Thanks for the info, I'll look more into your suggestions. Thanks mate!

-ha-

---

