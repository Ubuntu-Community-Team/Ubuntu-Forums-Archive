---
title: "Regnum Online on Lemur UltraThin not working"
date: 2011-05-30
forum: System76 Support
---

### Post by Conzar on 2011-05-30
I have a System76 Lemur UltraThin upgraded to 11.04 from 10.10 (Just bought the laptop in March).  I am trying to get Regnum Online (64-bit) to work but I get an "unsupported video card" error when launching the application.  

I believe this is caused from the Intel drivers that are bundled with Ubuntu.  

Does anyone know how to install other drivers that would have better support for 3d?  Or would installing external libraries like s3tc be sufficient, if so, how do I do this?

Thanks

Update
[http://www.regnumonline.com.ar/forum/showthread.php?t=77686](http://www.regnumonline.com.ar/forum/showthread.php?t=77686)

---

### Post by Ebonwumon on 2011-06-01
Afaik this is an issue with Intel only partially implementing the OpenGL spec and you're kinda SOL with the intel gfx chip.

That might not be the case for your specific problem, but I know it definitely affects some things, for example Dolphin.

---

### Post by Conzar on 2011-06-01
Does anyone know how xorg-edgers works on Lemur?  I have installed this on my old macbook and used the information found [here]("http://ubuntuforums.org/showthread.php?t=1130582")

---

### Post by isantop on 2011-06-03
That might help, but it's probably more of a limitation of the graphics card. Were you able to play before the upgrade?

---

### Post by Conzar on 2011-06-03
> **isantop said:**
> That might help, but it's probably more of a limitation of the graphics card. Were you able to play before the upgrade?
I did not try before the upgrade.  I read that Intel didn't implement the entire OpenGL spec.  One method for determining if its a driver issue is to install windows and try the game.  Anyone else know of a better method?

---

### Post by isantop on 2011-06-06
That would be a good test, as f it doesn't work in Windows, it won't work in Ubuntu. However, if it *does* work, that doesn't really mean it can work in Ubuntu, since it's possible that the Windows drivers are more complete that the Ubuntu drivers.

---

### Post by Conzar on 2011-06-06
Actually I was able to find a solution found in [this thread]("http://www.regnumonline.com.ar/forum/showthread.php?t=77686").

Thank you for your help!

---

