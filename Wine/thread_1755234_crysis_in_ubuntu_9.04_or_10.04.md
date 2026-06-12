---
title: "crysis in ubuntu 9.04 or 10.04?"
date: 2011-05-10
forum: Wine
---

### Post by BcRich on 2011-05-10
hi 
does anybody know of a specific guide to getting crysis (1) to work in ubuntu 9.04 or 10.04. the crysis winehq page is old and it seem to imply that crysis simply just installs through wine 1.2+ on 10.04, but this is not the case for me. this link says that wine needs to be patched 
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10107&iTestingId=58385&bShowAll=true](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10107&iTestingId=58385&bShowAll=true)
I'm using wine 1.2 do i still need to patch it?
in this link [http://ubuntuforums.org/showthread.php?t=712407](http://ubuntuforums.org/showthread.php?t=712407) poster pissedoffdude has instructions for patching an older version of wine, but i don't get it. ie how is this supposed to work with the patches listed in the first link?
i'm a noob, (just in case that's not painfully obvious)
thanks

---

### Post by bobwyajnr on 2011-05-11
Hi **BcRich**

I literally don't have space (!!) to install my copy of Crysis 1 (till I get some new HDs this week!). I wouldn't try and install (more) recent games without using the 1.3.xx 'unstable branch' of WINE ( which for me anyway - works fine :P ). I would try 1.3.19 to see what happens - before going to the hassle of compiling WINE from source (which is what you would have to do to apply that small 3D buffering patch). You will see if you need mouse warp overrides - in the latest WINE version - quite easily (e.g. you will not be able to turn 360 in the game using the mouse or your mouse cursor will get stuck in the middle of the menu screen).

[Add this PPA to get the WINE 1.3.xxx series...]("https://launchpad.net/~ubuntu-wine/+archive/ppa")

Don't be afraid to try things out! You can easily drop back to an earlier WINE release if you can't get the 1.3.xxx series to work for you! :popcorn:

Report back on progress and good luck!
Bob

---

### Post by BcRich on 2011-05-18
Hi bobwyajnr
thanks for the suggestions :) 
I decided to update my version of wine from 1.2 to 1.3.20 on ubuntu 9.04 32bit. the instructions here [http://www.wine-reviews.net/wine-reviews/news/three-ways-to-install-latest-wine-in-ubuntu-904-jaunty-jackalope.html](http://www.wine-reviews.net/wine-reviews/news/three-ways-to-install-latest-wine-in-ubuntu-904-jaunty-jackalope.html) where really useful. the ppa listed at that location only updates ubuntu 9.04 to wine 1.2 so in order to get 1.3.20 i had to compile it from the source files which can be downloaded from here [http://sourceforge.net/projects/wine/files/Source/](http://sourceforge.net/projects/wine/files/Source/) fortunately i didn't have any dependancy issues and wine compiled perfectly (actually i thought it was stuck in a loop cause it was taking such a long time to run make but after about an hour or less it finally completed make and it was ready to be installed).
unfortunately crysis still doesn't run in 9.04 32bit with wine 1.3.20 past the FMV intro which is pretty much the same issue other people have had with the game based on [http://appdb.winehq.org/objectManager.php?sClass=version&iId=10107&iTestingId=44018&bShowAll=true](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10107&iTestingId=44018&bShowAll=true)
I don't think it's my system I use a AMD 1075t with 8 GB RAM and Radeon 6850 OC which is much higher than the recommended specs on the crysis box.
maybe i do need to apply the patches 
[http://bugs2.winehq.org/attachment.cgi?id=27310](http://bugs2.winehq.org/attachment.cgi?id=27310)

[http://bugs.winehq.org/attachment.cgi?id=15638](http://bugs.winehq.org/attachment.cgi?id=15638)
but i still have no idea how to do this?

---

### Post by bobwyajnr on 2011-05-18
Hi

Sorry 'bout the delay (been busy).

I am going to try this patch tonight:
[Crysis Thread at WINE HQ Forums]("http://forum.winehq.org/viewtopic.php?p=61039")
for amusement :)

I'll report back on my luck!

Also I'll try to record the steps. It really isn't hard to apply a source code patch (especially one that is so tiny)! :popcorn:

Sorry that I advised you to use the Ubuntu PPA - it's just been updated to 1.3.20 which breaks a lot of games (due to the 'mouse input fix') :(

Bob

---

### Post by BcRich on 2011-05-18
hi bobwyajnr
No problems :) I hope you have better luck than I do (on this one).
thanks for the help I really appreciate it! and i look forward to hearing back from you.

---

### Post by bobwyajnr on 2011-05-18
> **BcRich said:**
> hi bobwyajnr
No problems :) I hope you have better luck than I do (on this one).
thanks for the help I really appreciate it! and i look forward to hearing back from you.

Just to say I've got Crysis working - with only minimal graphical glitches. However the **mousewarpoverride=force** is causing a problem (unmoveable mouse cursor in the main menu). Without that I cannot turn more 360 degrees in game. I'll have to find a work around for that. I'll see if patching the latest Git version of WINE 1.3.20 fixes the mouse problem... But not tonight!

Bob

---

### Post by bobwyajnr on 2011-05-19
Ok **BcRich**

Exciting news! The **Git master** (no I'm not swearing!) of WINE works! Just leave the mouse warping at the default setting. You still need to apply the patch:
[http://bugs2.winehq.org/attachment.cgi?id=27310]("http://bugs2.winehq.org/attachment.cgi?id=27310")
which helps deal with a memory leak bug in Crysis.
Save this file as **crysis_patch.txt** in your **Downloads** folder.

Steps to compile WINE Git master and apply Crysis memory leak patch:
[LIST=1]
[*] Get **build-essential** (Synaptic)
[*] Get **git** (Synaptic)
[*] ```
git clone git://source.winehq.org/git/wine.git ~/wine-git
```
[*] ```
cd ~/wine-git/
```
[*] ```
git config --global format.suffix .txt
```
[*] ```
git checkout master
```
[*] ```
git apply -v ~/Downloads/crysis_patch.txt
```
[*] ```
./configure
```
[*] ```
nice -n 19 make
```
[/LIST]
(note: you can use **./configure prefix=????** to change the default WINEPREFIX for your Git master build of WINE)

I think I've pulled in enough tools to do the building (in steps 1 & 2). I've lost the Ubuntu Community documentation page for Git I used originally! (The community docs indexing is totally rubbish...)

The build process takes a long time (~15-30 minutes).

Assuming the build works you run Crysis by typing:
```
WINEPREFIX=$HOME/Crysis1 ~/wine-git/wine "C:\Program Files\Electronic Arts\Crytek\Crysis\Bin32\Crysis.exe"

```
(where I have installed my copy of Crysis in the WINEPREFIX=**~/Crysis1** directory)

I've run Crysis with most settings on Medium (Shaders I think I put on High). The game does suffer bad FPS drops on my 8800 GTX. I was quite impressed though overall - took a few screenshots for WINEHQ!

You can install the WINE version you have built by typing **make install** (while in the **~/wine-git** directory). To do this you would have to uninstall the PPA WINE first. [COLOR="Red"]I wouldn't advice doing this BTW and the WINE FAQ also advises against this![/COLOR] [-X[-X

Good Luck! Post here with the (inevitable) problems! :popcorn:
Bob

---

### Post by BcRich on 2011-05-21
hi bobwyajnr
that's awesome! thanks for the advise. i'll definitely give it a try and let u know :)

---

### Post by bobwyajnr on 2011-05-21
> **BcRich said:**
> hi bobwyajnr
that's awesome! thanks for the advise. i'll definitely give it a try and let u know :)

It's not really enough to say it works here and not detail the steps! :D

I am no expert on the matter... But I have noticed that running Wine applications using your compiled version alongside/ at the same time as your regular PPA/repository installed Wine version causes problems (application and library paths get crazy mixed up). I am too lazy to find an adequate solution! Just run all your applications from the installed Wine version **or** the compiled Wine.

If you want to switch between running Windows application(s) with the installed version of Wine, and your self-compiled version(s!!) of Wine, you need to make sure the Wineserver process, and associated processes, from the installed version of Wine are shutdown (and visa-versa). Sound complicated? :D

Nop! :popcorn: Just shutdown the Windows applications as you normally (the Wineserver process _should_ shutdown...) [Q4Wine]("http://sourceforge.net/projects/q4wine/") (in the repositories) is a totally brilliant Qt-based GUI tool that aggregates all the currently running Linux Wine-associated processes that are running on your system. It separates them out by WINEPREFIX. I couldn't live without it! You can use it to check that no Wine-associated zombie processes are lurking about!

Not a big deal for running fullscreen games anyway (where you will probably only want to play one at a time - right?!!) :D

Do post back if you get any problems...
Bob

---

### Post by BcRich on 2011-05-24
Hi Bob
Thanks for the help! I've really learned alot from this exercise and I'm very grateful to you for your time and effort in imparting your knowledge to us noobs. Thanks a million times over :)
things have improved with getting crysis to run on ubuntu 9.04, at least the game actually works now when it did not before trying your suggestions. Unfortunately I cannot at this time completely follow your instructions as, my internet data is about to get capped (due to archaic telecommunications pollices that are still in practice in South Africa (which is where i'm posting from)). So I'll only be able to download the full wine-git version as per the suggestion in your previous post next month when my data cap gets reset.
So what I did in order to get an adhoc (make-shift) Crysis running through wine 1.3.20 in ubuntu 9.04 is the following:
Because i couldn't download wine from the git repository as it's about 140MB I had to use the source that I downloaded as indicated in my previous post from winehq i.e. the source for wine 1.3.20. I unpacked the file to my home directory, then changed the unpacked directory name to wine-git... (you can probably guess what I'm going to do from here on). Then with git and build-essentials installed:
```
cd ~/wine-git/
```
```
git config --global format.suffix .txt
```
I had to skip step 6 (from your post) as obviously the version of wine I'm using and the git version would not have matched.
I downloaded the patch [http://bugs2.winehq.org/attachment.cgi?id=27310](http://bugs2.winehq.org/attachment.cgi?id=27310) then saved it with the correct name in Downloads, then 
```
git apply -v ~/Downloads/crysis_patch.txt
```
```
./configure
```
```
nice -n 19 make
```
Thanks for warning me against make install
> You can install the WINE version you have built by typing make install (while in the ~/wine-git directory). To do this you would have to uninstall the PPA WINE first. I wouldn't advice doing this BTW and the WINE FAQ also advises against this!
I ommitted this step! 
wine configured without any errors and make ran smoothly (it took about 30mins)
I had to use a slightly different path to get Crysis running
```
WINEPREFIX="/home/bcrich/.wine" ~/wine-git/wine C:\\Program\ Files\\Electronic\ Arts\\Crytek\\Crysis\\Bin32\\Crysis.exe
```
and to my amazement Crysis actually got past the intro FMV!!!!!! unfortunately with only the audio as while this was happening I was simply starring at a blank screen waiting for some OMG hawt visuals to kick in... this didn't happen. So I exited the game, Crysis bumped my screen's res down to 800x600. even after I exited the game, I just decided to leave the screen at that res and fire Crysis up again, and this time it actually worked with visuals (not just sound) and finally I was playing the game (I was shocked, to say the least!) too bad that shortly after running around in the beach scene I realized that I could not turn more than 180 degrees. The mouse warp issue. Which is the first problem rendering the game unplayable. The other issue is that the in-game screen is constantly tweaking out, random polygons appear acorss the screen regularly they flash for about a split second (about every 20 to 30 seconds, sometimes more or less) then dissappear. it kind of looks like geometry intersecting the camera, if you know what I mean?
So I tried to fix the mouse warp issue but git complained about not being able to find the code it was supposed to patch, I searched the mouse.c file the patch refered to and I couldn't find the code either that this patch refers to 
```
--- a/dlls/dinput/mouse.c
+++ b/dlls/dinput/mouse.c
@@ -330,7 +330,7 @@ static void dinput_mouse_hook( LPDIRECTINPUTDEVICE8A iface, WPARAM wparam, LPARA
             }
 
             This->need_warp = This->warp_override != WARP_DISABLE &&
-                              (pt.x || pt.y) &&
+                              (hook->pt.x<2 || hook->pt.y<2 || hook->pt.x>((2 * This->win_centerX)-2) || hook->pt.y>((2 * This->win_centerY)-2) ) &&
                               (dwCoop & DISCL_EXCLUSIVE || This->warp_override == WARP_FORCE_ON);
             break;
         }
```
I don't know C, and even if I did trying to make heads or tails of this file (mouse.c) would have been beyond me.
Other than the random intersecting polygons and mouse warp issue, I'm definitely getting closer to getting Crysis to work in 9.04.
I guess I'll just have to wait till next month to find out if the git version works out for me.
Thanks again for the help bobwyajnr, I don't feel like I'm totally overwhelmed anymore and that I at least have some options.
Will post back soon, hopefully with some improved results :)

---

### Post by bobwyajnr on 2011-05-25
> **BcRich said:**
> 
...
The other issue is that the in-game screen is constantly tweaking out, random polygons appear acorss the screen regularly they flash for about a split second (about every 20 to 30 seconds, sometimes more or less) then dissappear. it kind of looks like geometry intersecting the camera, if you know what I mean?
...

Hi **BiRich**

After all that I realised I forgot to ask what hardware you were trying to run Crysis on! I guess I am guilty of assuming you knew it's a GPU melter and you probably will need a high-end Nvidia Card (8800 GTS/X or newer ideally). You mileage with a new ATI card (preferably 3870/4650+) will probably be less - generally the Linux ATI drivers are less polished than Nvidia's (but are catching up slowly).

You will need to be using the latest proprietary Linux drivers on an ATI or Nvidia graphics card (Nvidia 250+, ATI - probably want the latest Catalyst 11.5). I think you need to be able to set the shader setting above medium - to avoid visual glitching - when running through Wine (I'll check out which setting).

I wouldn't want to see you trying to achieve the impossible - well without knowing that it's impossible anyway! :popcorn:

There were some minor issues with the game (the odd surface that flickers the slightly wrong colour, etc.) I didn't perceive any geometrical errors though on my rig (which has an Nvidia 8800 GTX btw). I'll have to 'test' it further in the day scenes though! Like I said I actually took some screenshots to post on WineHQ as I was so pleased to get it working!

Bob

P.S. I would try and upgrade to Lucid. That is a good solid release and you won't run into the problem of PPA's not supporting earlier releases. Perhaps someone could mail you the DVD from abroad? Or contact Conical for a freebie?  :)

---

### Post by BcRich on 2011-05-25
hi [bobwyajnr]("http://ubuntuforums.org/member.php?u=683222")
Thanks again for the reply :)
I just upgraded my system to a hex core AMD, with 8GB RAM and a 6850 RadeonHD. I'm running the latest catalyst 11.x proprietary drivers. I realize that running a system like this in 32bit mode is a bit of a waste (as my ubuntu 9.04 installation is 32bit), so I also upgraded to ubuntu-studio 10.10 64bit. unfortunately because of my data cap issue (as mentioned in my previous post) I don't have wine installed on this new system, yet. At the moment I only have wine in 32-bit on 9.04 which is what i've been trying to get crysis to work in (I used to have wine on ubuntu 10.04 32bit when I fist started this thread (thus the title of the thread), but that has been replaced with my ubuntu 10.10 installation). I totally agree with you that running a more recent version of ubuntu might actually solve the problems I've been having, when my data cap get's reset one of the first things I plan on doing is to try to get crysis to work on my 64bit system :) Hopefully that works out a bit better for me.
> Or contact Conical for a freebie?
It would seem that Cononical, Launchpad and shipit have stopped shipping free cd's according to their website, sorry I don't have a link to post here regarding this topic. Well, the end of the month is about a week away and by then my data cap should have been reset. So it looks like I'll be in limbo till then...
Nonetheless, I'm very grateful for your correspondence and help!
Kind Regards
BCR
PS I'll try bumping up the shader settings to see if this has any effect on the geometry intersecting issue (mentioned in my previous post) Thanks for the suggestion! currently i'm running the game settings on "low" at 800x600 cause this seems to be the only settings that allow me to get past the intro FMV, but this might have changed since the memory leak patch seemed to apply successfully. 
BTW have you ever tried running this version of Crysis through gametree (AKA ex-Cedega)? I was thinking that if I can't get Crysis to work in wine I might give this a try, but that is perhaps a topic for another thread :)

---

### Post by BcRich on 2011-06-01
Hi 
I am currently trying to get crysis (the first one) working on ubuntu through wine 1.3.21.
I am using ubuntu 10.10 64bit and wine 1.3.21 with an amd 1075t (hexcore) 8 GB RAM and RadeonHD 6850. After folowing previous suggestions from bobwyajnr (which seemed to be working)
> 
[LIST=1]
[*] Get **build-essential** (Synaptic)
[*] Get **git** (Synaptic)
[*]  	Code:
 	git clone git://source.winehq.org/git/wine.git ~/wine-git 
[*]  	Code:
 	cd ~/wine-git/ 
[*]  	Code:
 	git config --global format.suffix .txt 
[*]  	Code:
 	git checkout master 
[*]  	Code:
 	git apply -v ~/Downloads/crysis_patch.txt 
[*]  	Code:
 	./configure 
[*]  	Code:
 	nice -n 19 make 
[/LIST]

I got up to step 8 and got the following error
```
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for cpp... cpp
checking whether gcc -m32 works... no
configure: error: Cannot build a 32-bit program, you need to install 32-bit development libraries.

```
Does this mean that I've downloaded wine for the wrong architecture?
I also have wine 1.3.21 installed the normal way (i.e. through Synaptic, but crysis does not work with this version of wine, it simply crashes just after the first FMV)

---

### Post by BcRich on 2011-06-01
after reading this page [http://wiki.winehq.org/Wine64](http://wiki.winehq.org/Wine64) i changed the command 
```
./configure
```
to 
```
./configure --enable-win64

```
and I managed to get past the different architecture problems however when running configure i ran into several dependancy issues such as missing dev files. I managed to track most of them down through synaptic and got configure to complete but with several warnings. amongst these warnings is a > OpenGL and Direct3D won't be supported. warning I'm obviously no expert but this seems like it could be a problem when the reason I trying to get wine to work is to play crysis, which is know to be a 3D extravaganza (or something like that). anyway here's the warnings from ./configure. I hope i can get this to work.
```
configure: OpenCL development files not found, OpenCL won't be supported.
configure: libsane development files not found, scanners won't be supported.
configure: libgphoto2 development files not found, digital cameras won't be supported.
configure: liblcms development files not found, Color Management won't be supported.
configure: gstreamer-0.10 base plugins development files not found, gstreamer support disabled
configure: OSS sound system found but too old (OSSv4 needed), OSS won't be supported.
configure: libcapi20 development files not found, ISDN won't be supported.
configure: libcups development files not found, CUPS won't be supported.
configure: fontconfig development files not found, fontconfig won't be supported.
configure: libtiff development files not found, TIFF won't be supported.
configure: libopenal development files not found (or too old), OpenAL won't be supported.

configure: WARNING: prelink not found, base address of core dlls won't be set correctly.

configure: WARNING: No OpenGL library found on this system.
OpenGL and Direct3D won't be supported.

configure: WARNING: libxml2 development files not found (or too old), XML won't be supported.

configure: WARNING: libxslt development files not found, xslt won't be supported.

configure: WARNING: OpenSSL development files not found, SSL won't be supported.

configure: WARNING: No sound system was found. Windows applications will be silent.

configure: Finished.  Do 'make' to compile Wine.

```

---

### Post by disabledaccount on 2011-06-01
"./configure --enable-win64"
You went wrong way - You don't want to built 64bit wine, because it won't run 32bit win apps.

"Cannot build a 32-bit program, you need to install 32-bit development libraries." - means that there are not resolved dependacies.

Here is the solution:
> [I]apt-get build-dep wine
look here: [http://wiki.winehq.org/Recommended_Packages#head-4b5211d3fa4652eb9cfa2c8ebd369073a62cba57](http://wiki.winehq.org/Recommended_Packages#head-4b5211d3fa4652eb9cfa2c8ebd369073a62cba57)

[/I]This will allow to built "normal" 32bit wine on both 32 and 64bit os.

---

### Post by bobwyajnr on 2011-06-01
@**BcRich**

Opps.. My bad ;)

Also I should add my guide was 'no wiki/stickie' and needs a bit of tidying up if you plan to recompile/get build errors or move about on the Git tree...:popcorn:

Main dependencies:
```
sudo apt-get install build-essential
sudo apt-get build-dep wine
sudo apt-get install git

```

Clone current Wine Git repository:
```
git clone git://source.winehq.org/git/wine.git ~/wine-git

```

Build Wine Git (selected branch) and apply a patch:
```
cd ~/wine-git/
git init
git clean
git config --global format.suffix .txt
git checkout <TAB>
git apply -v ~/Downloads/crysis_memory_wine.patch
./configure
make clean
nice -n 19 make

```
At the checkout point you can press the **TAB** key to view all the current build-able versions of Wine. Type out the one you want to build.

NB If you have a Git Clone of the Wine source already then you should not need to re-download it!! (Thinking of your precious bandwidth.)

I would recommend checking out version **1.3.21** for Crysis. It's only going to complicate things if you try to build with the Git **master**. This may change day-to-day and be unstable/ generate results unreproducible on another system (since they may have a different version of the Wine Git source tree).

Bob

---

### Post by bobwyajnr on 2011-06-01
@**BcRich**

Just occurred to me...

You mentioned you have a hex-core CPU. You might like to try:
```
nice -n 19 make -j 6
```
to speed up the Wine build process :popcorn:

Bob

---

### Post by bobwyajnr on 2011-06-02
Hi **BcRich**

Honest I'm not spamming this thread :popcorn:

I've tested out Crysis on my laptop which has a ATI HD4650M graphics card.
I'm using Wine 1.3.21 (compiled with 'the patch') and Catalyst 11.5 . Mouse warping appears to be OK.

I can corroborate the random white polygons appearing every so often in Crysis. So this appears to be an ATI driver issue... Bet you're wishing you had a 560 now! :D

Do you want to check it's working at your end and perhaps close the thread with a **[SOLVED]** tag?

Bob

---

### Post by jakejw93 on 2011-06-02
checking for X... no
configure: error: X development files not found. Wine will be built
without X support, which probably isn't what you want. You will need
to install development packages of Xlib/Xfree86 at the very least.
Use the --without-x option if you really want this.


I've come across this problem after step 8 ( ./configure )

any help??

---

### Post by BcRich on 2011-06-03
@bobwyajnr
> Honest I'm not spamming this thread
Ha ha more like the opposite of spamming, which is being exceptionally helpful! so thanks for that.
> I've tested out Crysis on my laptop which has a ATI HD4650M graphics card.
I'm using Wine 1.3.21 (compiled with 'the patch') and Catalyst 11.5 . Mouse warping appears to be OK.
I did actually manage to get crysis pseudo- "working" on ubuntu 9.04 32bit wine1.3 with the memory patch applied, using catalyst 11.5. except that the mouse warp issue was not resolved for me. this issue along with the epileptic-fit-inducing random polygons renders crysis unplayable for me. I tried to get wine 1.3 (the version "worked" best with crysis) to compile with the mouse warp patch. but it would seem that the mouse.c file (I think that's what it was called) had been changed since the patch was written, so git was unable to patch the appropriate wine C file. This was the brick wall I hit in 9.04 and subsequently decided to try to get crysis to work in ubuntu 10.10 64bit. Currently, where I'm at is I cannot install all of the dependencies needed for wine 1.3. running this code
```
sudo apt-get build-dep wine1.3
```
results in the removal of these packages
```
jackd2 jackd2-firewire libjack-jackd2-0
```
which I cannot uninstall because I use JACK for just about all the music I make on ubuntu. for [example]("http://www.lyndondaniels.com/2010/music.html")
Currently I'm looking at alternatives like maybe to install the 32bit (normal version) of wine in place of the 64bit version I have installed on my 64bit OS. This page explains it pretty well [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)
> Do you want to check it's working at your end and perhaps close the thread with a **[SOLVED]** tag?
So I'm getting there but still can't quite mark the thread as solved yet, however the results you have had are very encouraging so I feel there is still hope for me. even with my 6850 (which i am totally happy with :D ).
thanks again for the feedback bobwyajnr I can't express how grateful I am for your help, I mean that most sincerely.

@jakejw93
> checking for X... no
configure: error: X development files not found. Wine will be built
without X support, which probably isn't what you want. You will need
to install development packages of Xlib/Xfree86 at the very least. I had this problem too which was resolved after installing libx11-dev through synaptic. nonetheless I think that bobwyajnr suggestion of running 
```
sudo apt-get build-dep wine

```
or 
```
sudo apt-get build-dep wine1.3
```
depending on which version of wine you wish to install would be a more practical solution (given that you don't have any conflicting pre-installed software which needs to be removed *beware*) than installing one missing dependency at a time. hope that helps?

---

### Post by bobwyajnr on 2011-06-03
> **BcRich said:**
> 
```
sudo apt-get build-dep wine1.3
```


Does:
```
sudo apt-get build-dep wine
```
work? The build dependencies for Wine 1.2 aren't any different! Or can you reinstall the packages that get removed?

> **BcRich said:**
> 
Currently I'm looking at alternatives like maybe to install the 32bit (normal version) of wine in place of the 64bit version I have installed on my 64bit OS. This page explains it pretty well [http://wiki.winehq.org/WineOn64bit](http://wiki.winehq.org/WineOn64bit)


Like MAYBE! The 64-bit version of Wine is only for testing really. It's only been around a few months (versus the lifespan of Wine).

> **BcRich said:**
> 
nonetheless I think that bobwyajnr suggestion of running 


Credit there, for the Wine build dependencies, should go to **tomazzi** really! :popcorn:

If I ever get through Mr Torvald's Git Manual I'll let you know how to discard a patched branch of Wine!

You probably want Wine 1.3.21 (32-bit), with only the Wine memory leak patch, for optimal chances of success!

Happy to help out btw :P

Bob

---

### Post by bobwyajnr on 2011-06-24
> **bobwyajnr said:**
> 
If I ever get through Mr Torvald's Git Manual I'll let you know how to discard a patched branch of Wine!


I presume this is caused by Git assuming you want to start a new source code branch.

Found this in the Wine regression testing guide:
```
git reset --hard HEAD
```
That appears to discard any patches you have applied to your local Git Wine source. ;)

Bob

---

