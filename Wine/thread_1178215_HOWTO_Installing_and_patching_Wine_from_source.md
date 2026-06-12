---
title: "HOWTO: Installing and patching Wine from source"
date: 2009-06-04
forum: Wine
---

### Post by clenched_sphere on 2009-06-04
Hi all,

My first post on here.
I've registered purely to post this HOWTO, as I have spent many hours last night figuring out how to do it for myself. There isn't an in-depth enough tutorial or HOWTO that I could find, and manual patching with wine seems to be one of those things where if you don't know how, nobody will tell you.
Thats about to change! :)

I did this on Jaunty with Wine 1.1.22 (latest dev version) on a laptop with ATI HD1250, 4GB of ram and a dual core 2.5 GHZ intel.
I used this method to get Eve Online working on Wine, the patch I used here is necessary for alot of ATI cards when they can't render models properly in-game, and apparently also works for some Nvidia cards.

First step is to acquire the source of the wine version that you need, which was easiest for me to procure from sourceforge - [http://www.sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449](http://www.sourceforge.net/project/showfiles.php?group_id=6241&package_id=77449)

Download and unpack into a directory, somewhere on your desktop or home folder will be fine.

It's all command line from here :)
Assuming you named the directory "wine" and placed it on your Desktop:
```
cd ~/Desktop/wine
```
Heres where I patched, before you compile or anything.
You will need the patch text saved to a file, in this case I'm calling it ati.patch. You can copy & paste, or use wget for this - example: ```
wget http://www.winehq.org/patch_for_your_game
``` - that will save it to your current directory.
To patch, assuming patch file in your wine directory:
```
patch -p0 ati.patch
```
the "0" may need to be changed, depending on where the patch file is, and where it is intended to be run from. Start with 0, if that reports errors with finding files try 1 or 2, etc. I had to use 1.
```
man patch
``` will explain it better than I can :)
Now that it's patched, the rest is easy, if slow. We need to compile it and install, to start:
```
./configure
```
This may spit out some things that you need (dependencies), I didn't have any of those problems as I had previously installed then uninstalled an older version of wine. That's a quick fix / workaround if you don't want to install each dependency by hand :)
```
make depend
```
```
make
```
This last one needs root privelages -
```
sudo make install
```
It's now installed, you can double check by typing
```
wine --version
```
It should spit out whichever version you downloaded.
Hopefully, if you got to this point with no major issues, your patch will work. If your previous version of wine had the game in question installed, you should be able to just use wine to run the executable, which will still be in your ~/.wine directory somewhere.

I know this is far from perfect, and comments / corrections are welcome, but if I had found what I have just typed last night, I probably would have spent 3 less hours banging my head on the desk :)

---

### Post by AnomalyDetected on 2009-06-30
Great guide! One quick edit, though... I believe you need the "<" character for patch to use the diff file. Otherwise you'll just sit at an inactive, blank line.

Also, most patches for wine are designed with the expectation that you are going to use -p1 (according to their wiki, anyway, and from the ones I've tried).

So the patch line would end up looking more like:

```
patch -p1 < ati.patch
```

---

### Post by clenched_sphere on 2010-02-05
> **AnomalyDetected said:**
> Great guide! One quick edit, though... I believe you need the "<" character for patch to use the diff file. Otherwise you'll just sit at an inactive, blank line.

Also, most patches for wine are designed with the expectation that you are going to use -p1 (according to their wiki, anyway, and from the ones I've tried).

So the patch line would end up looking more like:

```
patch -p1 < ati.patch
```


Hi, 
First, sorry for the unbeleivable lateness of my reply, I haven't checked this since I wrote it :D

Second, thanks for your compliment & corrections, well spotted.
I didn't think anyone had run into the same issue as me when trying to patch wine, I'm glad it was of use to someone though :D

thanks

---

