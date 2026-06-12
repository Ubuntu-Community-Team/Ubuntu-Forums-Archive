---
title: "can VBOX strech to full screen?"
date: 2008-09-13
forum: Virtualisation
---

### Post by Meow27 on 2008-09-13
hey, since i don't dual-boot often to windows, i sometimes use virtualbox to play windows games on it (hardy as host XP as guest) (for Wine's current lack of support for it)

the game i play runs only on 1024x768 (16 bit color) and when i try placing the monitor setting on xp to 1280x1024 it still reverts back to 1024x768 (even on full screen)

on windows it would stretch the screen to 1024x768 from my 1280x1024 monitor and am wondering how to make it happen

( i tried things like resizing the window but it doesn't help :? (host A, host g))

---

### Post by Pom2122 on 2008-09-13
Do you have Guest Additions installed? Have you also tried fullscreen mode (Host F)?

---

### Post by Meow27 on 2008-09-13
[IMG]http://i119.photobucket.com/albums/o144/flamehawk/Screenshot-2.png[/IMG]


thats what i get when i do host + f

im afraid this is what im talking about :/ i want this to be 1024x768 STRETCHED to 1280x1024

im not sure what you mean by guest addition Vbox..

again, im running ubuntu hardy(8.04.1) as a host and xp as guest,,,,,,,,,

---

### Post by bouncingmolar on 2008-09-14
push <right control> + <F> to get out of full screen mode. 

Click these 2 menu options up the top: 

1. Devices/Install guest additions
2. Machine/  Auto resize Guest Display


Load full screen again... tadaaa:)

---

### Post by Meow27 on 2008-09-14
followed your mini guide and thus have been struck by disaster (thanks to system restore i dont have to reinstall :D)

your solution works.... just not for games... this game im playing is full screened at 1024*768

when im running it, it goes back to the full screen mode viewable in the screenie i posted above

any other possibilities of stretching the screen? :D

---

### Post by bouncingmolar on 2008-09-15
Yeh... I have that problem too(small resolution for games). Let me know if you find a work around. I find these virtual machines aren't that great for running games anyway. 3d directx ones definately don't work.

At least the sound works properly for VBox compared to VMware. 

Glad you restored ur xp. Thats weird that disaster hit after installing guest additions... it worked for me without killing anything.

---

