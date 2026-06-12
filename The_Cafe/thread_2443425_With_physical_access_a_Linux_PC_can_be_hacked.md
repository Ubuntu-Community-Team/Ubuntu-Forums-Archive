---
title: "With physical access a Linux PC can be hacked"
date: 2020-05-15
forum: The Cafe
---

### Post by pretty_whistle on 2020-05-15
Here's a recent article that's interesting.  It applies if the PC is a 2019 or older model:

[https://www.wired.com/story/thunderspy-thunderbolt-evil-maid-hacking/](https://www.wired.com/story/thunderspy-thunderbolt-evil-maid-hacking/)

---

### Post by EuclideanCoffee on 2020-05-15
Good article. It certainly makes laptops seem less desirable, as they are easier to lose.

---

### Post by crip720 on 2020-05-15
Physical access has always been the weak link in security.  This seems to make it faster to copy info.  Did not read, maybe not noticed, if encrypted drive  defeats it as it would if you used a Linux ISO instead to copy info.  Read over again, so I was blowing smoke.  Guess best advice is to lock computer to your body with chain.

---

### Post by EuclideanCoffee on 2020-05-15
Full disk can be bypassed.

> 
[COLOR=#1A1A1A][FONT=BreveText]On Thunderbolt-enabled Windows or Linux PCs manufactured before 2019, his technique can bypass the login screen of a sleeping or locked computer&#8212;and even its hard disk encryption&#8212;to gain full access to the computer's data. 
[/FONT][/COLOR]

But only when the computer is on.

> 
[COLOR=#1A1A1A][FONT=BreveText]Ruytenberg points out that the flaws he found extend to Intel's hardware and can't be fixed with a mere software update. "Basically they will have to do a silicon redesign," he says. Nor can users change the security settings of their Thunderbolt port in their operating system to prevent the attack, given that Ruytenberg discovered how to turn those settings off. Instead, he says that paranoid users may want to disable their Thunderbolt port altogether in their computer's BIOS, though the process of doing so will be different for every affected PC. On top of disabling Thunderbolt in BIOS, users will also need to enable hard disk encryption and turn their computers off entirely when they leave them unattended, in order to be fully protected.
[/FONT][/COLOR]

---

### Post by TheFu on 2020-05-15
There are mitigations for the evil-maid attack.  Whole disk encryption with 2FA and a separate boot device that never leaves your person are part of it.  Do not use standby or hibernation if you don't maintain physical control of the computer.  The only way for the system to be safe is to have to completely at rest, unmounted storage when not in use.

That physical access is a security problem has been known since at least the early 1990s.  Nothing new.  The fact that direct memory access through external ports is a security problem has been known at least since the first PCMCiA and Firewire implementations.  There are always people who seem surprised, but that is their own ignorance.  We are all ignorant about lots of stuff.  Just too much to know in the world.

USB devices are dangerous too, BTW.

---

