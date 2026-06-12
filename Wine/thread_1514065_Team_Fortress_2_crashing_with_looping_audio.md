---
title: "Team Fortress 2 crashing with looping audio"
date: 2010-06-20
forum: Wine
---

### Post by ucal on 2010-06-20
I can play TF2 up till about 5 or 10 minutes into the game, and then it freezes, and begins to loop the last half second of audio over and over again.  So far, the only way I know to stop this is to force a power off, which means I can't run TF2 in the terminal and read the error when it happens.  

I'm going to try running it in windowed mode to see if that will allow me to access force quitting, and alt tabbing to a terminal.  Any ideas on what could be causing this?  I didn't see any similar bugs on AppDB, but I did read some similar sounding issues on a windows based forum.  They mentioned that fragmentation might be an issue.

---

### Post by DoktorSeven on 2010-06-21
If you have an ATi card, sadly this is a normal condition.  I and many others are in the same situation you are in and it's basically just a matter of waiting until ATi and/or Wine to fix the issue for us.

If you're not using ATi/using nvidia, make sure you're using latest Wine (1.2rc4) and read down in some of the comments on the TF2 Wine AppDB for a few common issues.

---

### Post by asdfoo on 2010-06-21
system freezes like that are the fault of your video driver, most often due to buggy coding, othertimes hardware failure

---

### Post by ucal on 2010-06-25
> **DoktorSeven said:**
> If you have an ATi card, sadly this is a normal condition.  I and many others are in the same situation you are in and it's basically just a matter of waiting until ATi and/or Wine to fix the issue for us.

If you're not using ATi/using nvidia, make sure you're using latest Wine (1.2rc4) and read down in some of the comments on the TF2 Wine AppDB for a few common issues.

Well that bites.  I do have an ATi.  Do you think the open source driver is enough to run TF2, and if so, would it fix this issue?

---

### Post by asdfoo on 2010-06-28
> **ucal said:**
> Well that bites.  I do have an ATi.  Do you think the open source driver is enough to run TF2, and if so, would it fix this issue?

You can certainly try, you might have to look into using ubuntu edgers to get a relatively new version of components involved, so that you are as close to the latest developments.

---

