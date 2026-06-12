---
title: "Remote access to a Windows box on Linux"
date: 2011-02-01
forum: Virtualisation
---

### Post by WitchCraft on 2011-02-01
Question:

I have a Linux server running VirtualBox, with Windows running in VirtualBox.

How can I remote-access the virtual windows box from another Linux PC ?
Does remote desktop work if I access the virtual windows box from Windows ?

And another question:
How can I start a virtual box OS from the command line, so I can do it from ssh without X-forwarding ? Is it possible ?

Oh, and another question: 
Is it absolutely necessary to run Xorg/Gnome if I want to run windows in a virtual box, or is it possible to do it with a console server ? Or would Xen be capable of that ?

---

### Post by Ankhwatcher on 2011-02-01
I have a solution that does this:

I run FreeNX on my linux box and from this desktop I run Windows XP in virtualbox.

This works fairly well while I'm at home. (Although I have never been able to get sound to stream over FreeNX).

But when I'm at work I encounter a strange issue with the mouse on the Windows XP session.

The mouse seems to lurch around the screen with much greater acceleration than my mouse. (both cursors can be seen)

The only way to use the mouse is too inch along so that is doesn't sprint away.

Obviously this system is not working very well for me, so if someone has a better suggestion I'm keen to hear it too!

---

### Post by CharlesA on 2011-02-02
If you don't have the guest additions installed, the mouse pointer of the host and the mouse pointer of the guest will be out of sync.

I haven't found a way around it yet.

@WitchCraft: I run VirtualBox headless and it works fine.

---

