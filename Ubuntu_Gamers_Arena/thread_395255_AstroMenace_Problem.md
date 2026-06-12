---
title: "AstroMenace Problem"
date: 2007-03-27
forum: Ubuntu Gamers Arena
---

### Post by bvone21 on 2007-03-27
Are there issues with AstroMenace 1.0 in Edgy?

I've installed it like the "how to" at UGA says.  Yet when clicking on the launcher in Apps > Games > AstroMenace , nothing happens.  Same when trying to launch it from the terminal.  Any ideas?  I'm not sure where to even start to look as I'm a complete beginner to linux.

---

### Post by compiledkernel on 2007-03-28
can you provide the output the terminal gives you after you try to run the game. 

Do you have 3d drivers running?

---

### Post by retrorob on 2007-05-07
> **bvone21 said:**
> Are there issues with AstroMenace 1.0 in Edgy?

I've installed it like the "how to" at UGA says.  Yet when clicking on the launcher in Apps > Games > AstroMenace , nothing happens.  Same when trying to launch it from the terminal.  Any ideas?  I'm not sure where to even start to look as I'm a complete beginner to linux.


I dont know if you are interested, but to launch the game go to the  /usr/share/astromenace directory and type:
./AstroMenace --noAA

There is a bug in the Anti-Aliasing detect that causes this.

---

### Post by Clay_Banger on 2007-05-08
> **retrorob said:**
> I dont know if you are interested, but to launch the game go to the  /usr/share/astromenace directory and type:
./AstroMenace --noAA

There is a bug in the Anti-Aliasing detect that causes this.thx a million! it worked for me.

---

