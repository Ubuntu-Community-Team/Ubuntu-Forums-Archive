---
title: "Winelib and Winemake"
date: 2010-06-04
forum: Wine
---

### Post by Axolotl9250 on 2010-06-04
I've just been reading about these as it was said that doing this to windows applications make them more likely to work without altering them or even without wine (I think). I'm reading through the guide on WineHQ and trying to make sense out of it. Can anyone tell me any experiences or personal opinions regarding this and whether it's a good idea and a rough summary of what the process involves. Thanks.

---

### Post by cogadh on 2010-06-04
Winelib and winemake are developer tools. If you are the developer of a particular piece of Windows software and you want to make sure that your application will both run on Windows and on Linux through Wine without any issues, then you can compile your software using winemaker and winelib. For regular users of Wine, they are pretty much useless, since you need the source code to the application to even try to use them.

---

