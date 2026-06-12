---
title: "I want to try MeeGo in a virtual box, will it work on laptop?"
date: 2010-06-14
forum: The Cafe
---

### Post by Legendary_Bibo on 2010-06-14
Also, do I have to burn it to a CD?

---

### Post by infinitejones on 2010-06-14
On the download page, it says:
> Supported Hardware
In general MeeGo v1.0 for Netbook will run on Atom® based Netbooks
so I guess it comes down to whether the packages have been compiled for Atom processors specifically, which I assume they have, and whether that makes them incompatible with the Intel processors you get in laptops, which I don't know.

I'm downloading the .img now to have a go myself, but it's 800MB so it might take a while...

With VirtualBox, it doesn't seem to recognise .img files when you try to mount them as the CD drive for a virtual machine from the settings dialogue. But as described on this page:

[https://help.ubuntu.com/community/ManageDiscImages]("https://help.ubuntu.com/community/ManageDiscImages")

you can use ccd2iso to convert them to an iso, so you shouldn't have to burn it to a CD to use it in VirtualBox.

---

### Post by infinitejones on 2010-06-14
I've found more on the website:
> System Requirements
CPU: Intel Atom or Intel Core 2 CPU (support for SSSE3)
Note: MeeGo will not work on non-SSSE3 CPUs
Platforms with the GMA-500, Nvidia, or ATI Graphics chipset are not supported.

You can check if your processor supports SSSE3 by typing this at the commandline:
```
cat /proc/cpuinfo | grep ssse3
```

If nothing appears when you hit enter, it doesn't!

As for the graphics chipset:
```
lspci | grep VGA
```

However I don't know what the "graphics adapter" in VirtualBox is, and I don't have a working Linux virtual machine currently, so I can't check.

650MB left on the download...

---

### Post by pwnst*r on 2010-06-14
Just boot it from a flash drive like I'm doing.  Posting from it right now on a Lenovo X200.

---

### Post by Legendary_Bibo on 2010-06-14
Ah yeah it won't work, too many issues. I don't have an intel CPU, I have AMD. Also converting the .img to .iso didn't work.

---

### Post by amitabhishek on 2010-06-14
Meego was the first distro I tried on my EEEPC. It installed in under two minutes and boots in 20secs. If you want to use your netbook for stuff that you normally do from your smart phone (except phone calls) then Meego is the way to go! 

On the contrary I had to struggle a lot to get wifi working when I tried Lucid.

---

### Post by LMP900 on 2010-06-14
> **Legendary_Bibo said:**
> Also, do I have to burn it to a CD?

You have to convert the .IMG to .VDI. It will likely not work though due to a graphics issue. I managed to install it, but could not get it to boot. You might have better luck installing the SDK instead if you want to play around with it within your OS: [http://wiki.meego.com/Getting_started_with_the_MeeGo_SDK_for_Linux](http://wiki.meego.com/Getting_started_with_the_MeeGo_SDK_for_Linux)

---

