---
title: "Graphical Remote Admin"
date: 2009-07-15
forum: Security
---

### Post by mlsquad on 2009-07-15
I have a headless Ubuntu box (the desktop edition) that I log in to through Cygwin.  Ubuntu's security policy doesn't allow me to use the graphical tools to do many admin functions, such as user administration.  It greyes out the Unlock button.  Is there any way around this?

---

### Post by XCan on 2009-07-15
You should be able to start the tools with gksudo in that case. The only thing tricky is to find out what the respective terminal commands are for starting the tools.

---

### Post by mlsquad on 2009-07-15
> **XCan said:**
> You should be able to start the tools with gksudo in that case. The only thing tricky is to find out what the respective terminal commands are for starting the tools.

Even running [FONT="Fixedsys"]gksudo users-admin[/FONT] doesn't work.
Finding the name of the command is easy.  Just go to edit the menu and find the command from the editor.

---

### Post by XCan on 2009-07-15
Hmm, that's strange. I just tried ssh -X to my remote machine, and the unlock button worked for me. :/

---

### Post by mlsquad on 2009-07-15
> **XCan said:**
> Hmm, that's strange. I just tried ssh -X to my remote machine, and the unlock button worked for me. :/

That is strange.  If I try it over ssh I get the same thing.

---

