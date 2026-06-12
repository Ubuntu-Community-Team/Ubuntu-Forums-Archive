---
title: "Wine hack, how to type/insert hack/script?"
date: 2009-11-05
forum: Wine
---

### Post by Toke on 2009-11-05
I have found a solution on WineHQ for a problem with playing UFO-aftershock, but I don't know how to apply it.

> This game does interesting things with its cursor: it attempts to change it from different threads(at least 3 threads tries to do so). Such a behaviour completely confuses winex11.drv and leads to the cursor being hide and never shown again. 
I see no easy way to fix this, so i use following little ugly hack, that just prevents any cursor changes. 

diff --git a/dlls/winex11.drv/mouse.c b/dlls/winex11.drv/mouse.c 
index 5df71a7..70bee91 100644 
--- a/dlls/winex11.drv/mouse.c 
+++ b/dlls/winex11.drv/mouse.c 
@@ -915,6 +915,7 @@ #endif 
  */ 
 void X11DRV_SetCursor( CURSORICONINFO *lpCursor ) 
 { 
+    return; 
     struct x11drv_thread_data *data = x11drv_init_thread_data(); 
     Cursor cursor; 
  
This is NOT a correct solution, but game is playable.

Should I copypaste it into the console or are there some field in wine settings for it?

Ufo-Aftershock is currently the only thing I use my windows partition for and it is a bit of a drag to reboot every time I want to go from browsing to playing.

---

### Post by mrboojive on 2009-11-05
That appears to be a patch for the Wine source code. You would need apply the patch and then compile Wine from source. There is probably information at WineHQ about how to download and compile the Wine source, but if you're not sure how to go about doing that, you've got a rocky road ahead and it might be more trouble than it's worth.

---

### Post by Toke on 2009-11-05
> **mrboojive said:**
> That appears to be a patch for the Wine source code. You would need apply the patch and then compile Wine from source. There is probably information at WineHQ about how to download and compile the Wine source, but if you're not sure how to go about doing that, you've got a rocky road ahead and it might be more trouble than it's worth.

Thanks, sounds like I am in trouble.
I will look into it, maybe I will learn something.

---

### Post by Toke on 2009-11-05
> **Toke said:**
> Thanks, sounds like I am in trouble.
I will look into it, maybe I will learn something.

Looks like I would have to download something called GIT and then 175mb of source code for wine, and build a tree, and manage some patch files.

There are simply too many ways for me to get it wrong and damage something.

---

### Post by falconindy on 2009-11-05
> **Toke said:**
> Looks like I would have to download something called GIT and then 175mb of source code for wine, and build a tree, and manage some patch files.

There are simply too many ways for me to get it wrong and damage something.
You wouldn't need git, since WineHQ provides a PPA with source code.

Add the following line to etc/apt/sources.list:
```
deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu karmic main
```

From there, update your local repos, get the source and the build dependencies:
```
apt-get update
sudo apt-get build-dep wine
apt-get source wine
```
Note that the last line will download the source to your present working directory, so make sure it's relatively clean. After you have the source, locate the file that the patch file you have applies to and patch it:
```
patch filetobepatched.c < patch.file
```
Work your way back up to the "root" of the source (to where you see a file named "configure", and run the following commands:
```
./configure
make
```
You **should** end up with a .deb package at the end which can be installed by...
```
sudo dpkg -i name.of.created.package.deb
```
Very few instances of sudo in here, aka very few chances to seriously muck something up. Hmm, you'll also want to pin the wine package after this is done so apt-get doesn't overwrite it. Hmm, if memory serves me correctly:
```
echo "wine hold" | dpkg --set-selections
```

---

### Post by mrboojive on 2009-11-05
Awesome! I had no idea it was that easy for PPAs with source code.

---

### Post by Toke on 2009-11-06
Sounds like an interesting project for the weekend.
I just have to figure out where the patch is to be applied, what I got is the text in the 1. post. Hopefully source code is a directory where all files contain some text explaining what they are for. :)

Thanks for the explanation, it looks like I have a chance.

---

### Post by aoanla on 2009-11-06
> **Toke said:**
> Sounds like an interesting project for the weekend.
I just have to figure out where the patch is to be applied, what I got is the text in the 1. post. Hopefully source code is a directory where all files contain some text explaining what they are for. :)


Not even that hard - the first line of the patch itself tells you the file it applies to.
(and the patch command the helpful earlier poster included in his instructions actually applies it, once you're in the source code directory itself).

---

### Post by Toke on 2009-11-06
I got a malformed patch at line 6.

Then after some checking I found this.

> Patch you are asking about was generated by "git diff" and must be applied by "git apply". 
But it should be noted that when code structure changes, patch became invalid and i dont have an intent to syncronize it with the current git. 

Anyway the purpose of this "patch" is just to show the idea, that we may skip cursor manipulation stuff completely to prevent cursor from disappearing. 

So open needed file in wine sources(dlls/winex11.drv/mouse.c), find function "X11DRV_SetCursor" and add "return;" statement just after opening brace. Then "make && make install" from the folder where you was runnig configure script and start the game.


So I have been through mouse.c and added a +return; 
Now I am downloading the dependencies (158mb) something I remembered after typing ./configure and getting an error.

This is interesting even if a bit complicated.

---

### Post by falconindy on 2009-11-06
Ahh, I was working on the assumption that the patch was created using the POSIX diff utility, not git diff. Sounds like you're moving in the right direction though.

---

### Post by Toke on 2009-11-06
Most annoying, I got a pubkey failure after 138mb, and keyserver error when trying to get them manually, then tried ./configure again to see what was missing it was "flex" and "bufalo". I got those through synaptic package manager but still had some error messages.

I tried make anyway and got this.
> C -Wall -pipe -fno-strict-aliasing -Wdeclaration-after-statement -Wstrict-prototypes -Wwrite-strings -Wtype-limits -Wpointer-arith  -g -O2  -o mouse.o mouse.c
mouse.c: In function ‘X11DRV_SetCursor’:
mouse.c:954: error: expected expression before ‘return’
mouse.c:955: warning: ISO C90 forbids mixed declarations and code
make[2]: *** [mouse.o] Error 1
make[2]: Leaving directory `/home/toke/wine-1.1.32/dlls/winex11.drv'
make[1]: *** [winex11.drv] Error 2
make[1]: Leaving directory `/home/toke/wine-1.1.32/dlls'
make: *** [dlls] Error 2

The last part looks specific to my adding a +return; in mouse.c
I will go back and try to make sure I have the dependencies solved, and remove my change in mouse.c If I can get it to work then I just have to learn how to get a line regarding cursor in wine ignored without error message.


> Ahh, I was working on the assumption that the patch was created using the POSIX diff utility, not git diff.
I have next to no idea what those are. :)
>  Sounds like you're moving in the right direction though.
Absolutely, it is compiling somewhat. Still some fine tuning needed though.;)

Ok, I am pretty clueless, but this is fun.

---

### Post by falconindy on 2009-11-06
Hrmmm, how did you do the checkout from git for your source code? Did you try and compile off the master branch? If you did, then you'll want to do a checkout of a tag. You can do 'git tag | more' to see what tags are available and then pick one that sounds like a real release -- maybe match it up with a version from winehq.com. Once you have that tag name, do "git checkout tag-name-here -b winepatched". Winepatched can be anything really -- just an identifier for your new branch.

POSIX is the set of standards that Unix follows. Very often, basic Linux programs (such as diff), will aim for POSIX compliance. git's diff functions differently (in the output) from the built in Linux command (actually GNU's diff utility) and you'll find that the output generated by the two programs differs. That's probably more than you needed to know.

Poking around like this can be a lot of fun. Or at least I think it is... Maybe it's just a slippery slope towards insanity.

---

### Post by Toke on 2009-11-08
I found the source code through sourceforge, and found script on winehq that downloaded/installed dependencies when copied into terminal.

I looks like it compiles, with ./configure, make depend, and make, but there are no *.deb file to be found anywhere. 

Guess I will have to read up on the accompanying readme files again.

Ships net have been down, there is a lot of forums to catch up on.

---

### Post by oedipuss on 2009-11-08
> **Toke said:**
> 

The last part looks specific to my adding a +return; in mouse.c
I will go back and try to make sure I have the dependencies solved, and remove my change in mouse.c If I can get it to work then I just have to learn how to get a line regarding cursor in wine ignored without error message.



I believe the '+' in that line is simply indicating that a new line is added to that file. 

Try adding 'return;' without the plus mark.

Also, this might help with source packages : [http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html)

It seems like 'dpkg-buildpackage -rfakeroot -uc -b' compiles the source and builds the deb file.

---

### Post by Toke on 2009-11-09
:D IT WORKS!

The wine source code comes with it's own compiler/installer program/script, so after noticing the part about uninstalling the previous wine things went smooth.
One types ./tools/wineinstall

And, as suggested, the > +return; should be>  return;
 
Now I can play UFO aftershock in full screen with mouse visible.

Thanks for the help everybody. :D

---

