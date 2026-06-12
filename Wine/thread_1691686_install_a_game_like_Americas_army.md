---
title: "install a game like Americas army"
date: 2011-02-20
forum: Wine
---

### Post by Luckyjfl on 2011-02-20
Hi Guys,
I am a complete Noob as far as Linux is concerned, ok. But, I am getting there and  shout loud and clear to everyone about how good linux is compared to  the other, ie Windows.  Now I decided to try out one or two games on my Unbuntu system and downloaded  "America's Army  and Urban Terrorist ".

For the love of me, I cannot find out how to install them on my system. I also downloaded the Wine program.  The Game exe file is there but it does not work that way on Ubuntu. Any ideas please.

All the best.

Lucky:(

---

### Post by howefield on 2011-02-20
Moved to the *"Wine"* forum before your thread is deleted.

---

### Post by yanom on 2011-02-20
Are you thinking of Urban Terror? That has a native linux version. It's included with the Mac version in one download, on the UT site.

---

### Post by Omegaham on 2011-02-20
> **Luckyjfl said:**
> Hi Guys,
I am a complete Noob as far as Linux is concerned, ok. But, I am getting there and  shout loud and clear to everyone about how good linux is compared to  the other, ie Windows.  Now I decided to try out one or two games on my Unbuntu system and downloaded  "America's Army  and Urban Terrorist ".

For the love of me, I cannot find out how to install them on my system. I also downloaded the Wine program.  The Game exe file is there but it does not work that way on Ubuntu. Any ideas please.

All the best.

Lucky:(

America's Army 3 doesn't work in Wine. Punkbuster just doesn't work well with Wine. It's the same reason why the Battlefield games don't work very well.

America's Army 2 had a Linux distribution up until 2.7. It got replaced by the Deploy Client, which is sadly Windows only.

Urban Terror, on the other hand, is much easier.

Download the file. If you're running a 32-bit system, use the ioUrbanTerror.i386 file.
If you're running a 64-bit system, use the ioUrbanTerror.x86_64 file.

You'll have to make the file executable. You can either right-click on the file, click Properties, and check the "Allow Execution" box, or you can go to the terminal.

```
cd ~/[extracted folder] (For example, if you extracted the .zip to a folder called UrbanTerror, you would type in "cd ~/UrbanTerror")
chmod 777 ioUrbanTerror.i386
```

From there, you can either run it in the terminal or just double-click on the file.

Hope this helps!

---

