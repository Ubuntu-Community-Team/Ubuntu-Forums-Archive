---
title: "Ubuntustudio: Why group all graphics apps into one package?"
date: 2008-12-19
forum: Ubuntu Studio
---

### Post by dfro on 2008-12-19
I have UbuntuStudio installed on my computer. The current version of blender is 2.48a, which I want to use, but the ubuntustudio-graphics package is only up to 2.46. 

So, in order to remove blender 2.46 and unstall 2.48a, I have to remove the entire ubuntu-graphics package and all of the different graphics programs, correct?

I think the grouping of many applications into a giant graphics or audio package is very cumbersome and blocks people from easily customizing their computer setup to how they would like it. Why not just have UbuntuStudio install all the .deb packages separately? I don't get it.

Thanks.

---

### Post by Stochastic on 2008-12-19
To remove blender all you need to do is ```
sudo apt-get remove blender
``` and it will only remove blender and the ubuntustudio-graphics meta package (the other programs will still be installed).  But you might not even need to remove blender to install a newer version, I'm pretty sure you just need to do a normal install and it should write over any old files etc... (I'm no blender expert though, so take that with a grain of caution).

---

### Post by rixtr66 on 2008-12-20
Well ive had ubuntu studio and i just installed the blender 2.48 deb.pkg
from get deb,no problems,it worked fine for me.
give it a go and let me know how it works out!!
hope this helps!
Rick

---

