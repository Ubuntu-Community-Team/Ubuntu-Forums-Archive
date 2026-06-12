---
title: "bizarre keyboard and mouse problem"
date: 2017-01-09
forum: Virtualisation
---

### Post by Kestreln8144 on 2017-01-09
My keyboard and mouse partially stopped functioning.

[LIST]
[*]My mouse pointer still moved, but I could not click anything. The interface did not react to mouse hovering (like button highlighting on hover).
[*]I could not use most keyboard commands, for example, to open a window menu with alt + space. However, alt-tab still worked, and I could use F12 to open my guake terminal.
[*]Typing in the guake terminal still worked.
[/LIST]
I freshly installed Xubuntu 16.04 yesterday. This *never* occurred in my previous installation (Xubuntu 14.04).

What might've caused this? Is it possible to restart any components from the terminal to fix this issue when it occurs again, without restarting my desktop? (I restarted lightdm this time, but this closed all of my open programs which may cause data loss, so I don't want to do that in the future.)

---

### Post by ajgreeny on 2017-01-09
We need a lot more info to be able to help you.

What hardware are you using?

---

### Post by Kestreln8144 on 2017-01-09
I'm still a Linux novice, so I don't know what specs you need or how to get them. If you can tell me what commands to use, I'll paste the output for you.

It is a bug in VirtualBox. (VB 5.1.12 r112440)

I shut down my VM via the command line (VBoxManage controlvm <vm-id-or-name> savestate), and full function returned. It's probably a bug with mouse and keyboard capturing.

Thanks to everyone who read this. I know problems like this can be such a pain to troubleshoot.

---

### Post by howefield on 2017-01-09
Moved to the "*Virtualisation*" forum.

---

