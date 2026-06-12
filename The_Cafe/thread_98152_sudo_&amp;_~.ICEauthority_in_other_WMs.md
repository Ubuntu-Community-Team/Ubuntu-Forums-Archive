---
title: "sudo &amp; ~/.ICEauthority in other WMs"
date: 2005-12-02
forum: The Cafe
---

### Post by gingermark on 2005-12-02
Hey there,

I've been trying out some Window Managers, and have fallen in love with Window Maker.

I have a question about sudo-ing apps such as Synaptic within these Managers. Basically I have fallen foul of the 'ole ~/.ICEauthority login problem in the past, and want to make sure I don't again.

When dealing with Synaptic, I'd use the command "gksudo", with Adept (or other KDE apps needing SU priviledges) I'd use "kdesu". Neither seem to work in Window Maker.

If anyone could post a link that unequivically states when these commands should be used, that would be wonderful, but basically I'm wondering if typing "sudo synaptic" is acceptable in WMs such as Window Maker, Fluxbox, FVWM etc, or if there are better ways to do things?

Many thanks,
gingermark.

---

### Post by Stormy Eyes on 2005-12-02
[QUOTE=gingermark]If anyone could post a link that unequivically states when these commands should be used, that would be wonderful, but basically I'm wondering if typing "sudo synaptic" is acceptable in WMs such as Window Maker, Fluxbox, FVWM etc, or if there are better ways to do things?[/QUOTE]

If you do "sudo synaptic", then you'll have to do it from a terminal in order to punch in your password. I see no reason why gksudo won't work in Window Maker. Did you try running gksudo from a terminal to see if it was throwing an error?

---

### Post by gingermark on 2005-12-02
My apologies, I think I've realised my mistake. Synaptic's entry in the menu uses gksudo, but I don't have GNOME installed. In KDE this still worked (I assume it automatically substitues the kdesu command) and led me to the misunderstanding that kdesu was for KDE apps and gksudo for GNOME ones.

I'm guessing that in fact they simply differ in what toolkit the "Enter password" dialog box uses?

At any rate, kdesu worked (I obviously didn't try it before, although I thought I had). I'll change the menu entry for Synaptic to kdesu, and I'm sure all will be well.

Still not 100% sure on how the .ICEauthority problem can arise, but I'm sure with a bit of searching I can find out.

Thanks for your time, and once again my apologies for wasting it.

Best regards,
gingermark.

---

