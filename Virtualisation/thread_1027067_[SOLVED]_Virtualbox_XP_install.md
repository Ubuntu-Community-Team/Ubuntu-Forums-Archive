---
title: "[SOLVED] Virtualbox XP install"
date: 2008-12-31
forum: Virtualisation
---

### Post by kgriff on 2008-12-31
I have Virtualbox on a Hardy host.  I am trying to install Win XP as the guest.  This is my first time with Virtualbox and I'm having a problem that I can't seem to find a solution to.

During the Win installation process there are multiple steps that require user interaction, either to make a selection or click a button.  When I click on the virtual machine with my mouse I get a pop up stating:

(This is paraphrased)
You have clicked inside the virtual machine.  Do you want the virtual machine to capture the mouse?

If I click on the "Capture button" the pop-up disappears, but the virtual machine still does not capture the mouse.  This is not actually a problem for most of the installation process as the Tab and Enter keys suffice.  However, on the first "real" boot of Windows I have a pop up that does not have the focus, so I cannot use the keyboard to acknowledge.

I am using a PS2 mouse, so this is not a USB issue.

Anyone have any suggestions?

---

### Post by kgriff on 2008-12-31
Nevermind.  Ultimately, I solved the problem.  After I tried it 15 times or so, the guest did eventually capture the mouse.  Now I can install Guest Additions and, hopefully, that will take care of it.

---

