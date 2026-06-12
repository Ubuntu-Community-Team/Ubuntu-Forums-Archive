---
title: "Fastest gaming desktop"
date: 2012-10-16
forum: The Cafe
---

### Post by MikeCyber on 2012-10-16
Hi
which is the fastest desktop for gaming? I want to use Gnome 3, but some old results at phoronix are bad.
Thanks

---

### Post by thatguruguy on 2012-10-16
If you've read the articles on phoronix, you know that the fastest gaming environment is apparently KDE with effects turned off. However, I notice that in the tests in [this article]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210beta_desktops&num=1") he uses Gnome Classic as one of the desktops, with no mention of whether it is running in "No effects" mode. In fact, he states as follows:
> Each desktop was tested in its default configuration and using  the packages available from the Ubuntu Quantal repository, the only non-default  run was the specified KDE SC 4.9 run when using the easily-exposed option of automatically  suspending desktop effects for full-screen applications.
I'd assume that the results if you ran Gnome Classic in "No effects" mode, you'd get results similar to KDE with desktop effects suspended.

However, if you ***really*** want the best performance for full-screen games, follow vexorian's guide [here]("http://vexfloss.blogspot.com/2012/09/why-and-how-i-use-single-terminal.html"). That will give you the fastest gaming environment available on your hardware.

---

### Post by MikeCyber on 2012-10-17
Thanks, I'll add that tomorrow. Well, I hope those old Gnome3 tests are not for Nvidia and 12.10. Maybe I install also KDE for testing. If Gnome 3 is as slow as Unity, I might even switch.

---

### Post by philinux on 2012-10-17
> **MikeCyber said:**
> Thanks, I'll add that tomorrow. Well, I hope those old Gnome3 tests are not for Nvidia and 12.10. Maybe I install also KDE for testing. If Gnome 3 is as slow as Unity, I might even switch.

Try this too. [http://www.webupd8.org/2012/10/lightweight-qt-desktop-environment.html?m=1](http://www.webupd8.org/2012/10/lightweight-qt-desktop-environment.html?m=1)

---

### Post by kaldor on 2012-10-17
From my own experience GNOME Fallback Mode (Classic No Effects) works the best. On fullscreen, GNOME Shell works at an acceptable level. Unity (and Unity 2d if you're on 12.04) is out of the question entirely if you are into multiplayer games. 

There's more to the quality of gaming than FPS. When I run benchmarks on my machine the difference in FPS is incredibly low, showing sometimes only a ~3 frame difference. However, the overall quality varies hugely despite showing similar FPS results.

---

### Post by cariboo on 2012-10-17
The Ubuntu +1 Quantal sub-forum will be closed soon, so moved to the Cafe.

---

### Post by Mikeb85 on 2012-10-18
If you want the fastest gaming desktop possible, don't use Ubuntu.  SUSE, Arch, Gentoo, etc..., are all a bit quicker.  

That being said, if you want Ubuntu to be as quick as it can be, install it on a Brtfs partition.  I don't think the DEs make a huge difference in performance on high end equipment - if you want a great gaming rig you're going to have a quad-core processor, a video card that will likely have 200+ cores and 2 GB of RAM, etc.., however many resources the DE takes up won't really affect the game you're playing.

---

### Post by zombifier25 on 2012-10-18
If you want the fastest possible environment for gaming, don't use an environment at all like vexorian's tutorial mentioned above :P

Or if you're not in the mood of writing scripts, use the "worst" possible window manager to play Wine games. I use twm.

---

### Post by MikeCyber on 2012-10-19
> **kaldor said:**
> However, the overall quality varies hugely despite showing similar FPS results.

What do you mean? So if I go with the latest Gnome 3.6 I should not get less than minus ~3 FPS compared to KDE? And compared to: [http://vexfloss.blogspot.ch/2012/09/why-and-how-i-use-single-terminal.html](http://vexfloss.blogspot.ch/2012/09/why-and-how-i-use-single-terminal.html) ?

---

### Post by thatguruguy on 2012-10-19
> **Mikeb85 said:**
> If you want the fastest gaming desktop possible, don't use Ubuntu.  SUSE, Arch, Gentoo, etc..., are all a bit quicker.  

Links, please.

---

### Post by Mikeb85 on 2012-10-19
> **thatguruguy said:**
> Links, please.

How about install them on your own PC, and run an intensive 3D benchmark like say, Unigine's Heaven?  

On my core 2 duo with nVidia GeForce GTX 560, Heaven runs about 10% quicker on SUSE (both Gnome and KDE) than on Ubuntu Unity...  It's no secret that SUSE is quicker, afterall it is the most popular Linux distro in a number of heavy-use applications.

For the record though, I do prefer Ubuntu for overall usability (SUSE is a dependency nightmare) , and I have Ubuntu running on all my PCs...  

In the end though , hardware > OS.  Something that runs smooth on SUSE will still run smooth on Ubuntu or Windows.

---

### Post by MikeCyber on 2012-10-20
I don't think it runs faster on other distros.- If you get different fps, probably less than 3fps or so, it's because of another combination/versions of the very same software.
I've used ~1998-2009 mostly Suse and once thought it to be good. I've switched as I couldn't get my soundcard working anymore and sticked to Ubuntu as it was the first to have online repos. (a very neat new feature at that time)
Now fxaa is broken in Gnome3.

---

