---
title: "[SOLVED] Virtualbox - no seamless at max resolution?"
date: 2009-01-02
forum: Virtualisation
---

### Post by lowtolerance on 2009-01-02
I'll start off by saying that I'm not sure if this is a VirtualBox or a KDE issue. What I want is for my XP guest to run on my second desktop in KDE, with no KDE taskbar on that desktop. I've gotten as far as setting window specific behaviors to force the virtualbox session onto the second desktop, and forcing the KDE taskbar onto the first desktop. 

My problem is that no matter what i try, I cannot get my XP guest to run at 1440x900, instead it runs at 1440x864 - the dimensions of my screen, minus the KDE taskbar. I've tried running 'vboxmanage controlvm xp setvideomodehint 1440 900 32', but that doesn't do anything but garble the sessions video. I've also tried setting window specific behavior to force virtualbox to run at 1440x900, and that works for the virtualbox control panel, but not for the actual virtual machine session.

I'm sure I'm not the first person to try this kind of setup, but has anyone had any luck in getting it to work?

*EDIT:* Upgrading to KDE 4.2 and then uninstalling Guest Additions, then reinstalling it seemed to do the trick! So, to answer my own problem, this is(was) a KDE issue.

---

