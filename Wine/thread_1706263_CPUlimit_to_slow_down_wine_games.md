---
title: "CPUlimit to slow down wine games"
date: 2011-03-13
forum: Wine
---

### Post by pieman711 on 2011-03-13
I've recently installed dune2000 using wine (after a lot of playing around trying to mount the iso properly!) and it almost runs fine...
My processor is far too fast for teh game and even with teh settings on minimum scrolling and icons are too fast to use properly. 
I've been looking into using cpulimit (available in repos) but I cant get it to work with out a PID. To do that I need to come out of the game and use 'top' or play aroud using extra virtual desktops using "ctrl+alt+F4 to F8" 
Does anyone know how to use the -e or -P options in cpulimit to get readfy to slow a ps down before it has been started?

---

### Post by lykeion on 2011-03-13
I might suggest another path:
Run it via DOSBox (I think you can set nr of cpu cycles in it)
or maybe setup a win95/win98 emulation in VirtualBox.

---

### Post by cogadh on 2011-03-13
DOSBox doesn't work for Windows games, only DOS games.

---

### Post by lykeion on 2011-03-13
> **cogadh said:**
> DOSBox doesn't work for Windows games, only DOS games.Yes, you are right of course. DOSBox is made to run DOS games/apps, however I found some links where people claiming to run both Win 3.x and Win95 in DOSBox:
[http://www.armchairarcade.com/neo/node/1725](http://www.armchairarcade.com/neo/node/1725)
[http://forum.dune2k.com/index.php?/topic/21040-dune-2000-vista-and-windows-7-fix/page__view__findpost__p__353251](http://forum.dune2k.com/index.php?/topic/21040-dune-2000-vista-and-windows-7-fix/page__view__findpost__p__353251)

Did a little Dune researching and found out that Dune 2000 is a remake for Windows of the old 1992 DOS game Dune II. 
Also found [Dune Legacy]("http://sourceforge.net/apps/mediawiki/dunelegacy/index.php?title=Main_Page") which is a remake of Dune II for Linux plus [Dune 2 TGP]("http://drackbolt.blogspot.com/") a multiplayer remake for Win/Linux.

---

### Post by cogadh on 2011-03-13
So you are suggesting that he go out and find a copy of Windows 98 or 95 to install within DOSBox, then try to install the game within that and hopefully get it to work, just to use the DOSBox cpu settings, rather than find out how to use cpulimit correctly with an already working installation of the game within Wine? Talk about taking the long way from point A to point B.

On that subject (cpulimit), it doesn't only work with PID, you can also use a specific executable name:
```
cpulimit --exe <executable name> --limit 40
```

---

### Post by lykeion on 2011-03-13
People owning Windows games that old usually also have a CD with old Win OS too. But no I wouldn't say it was the easiest way to solve his problem, I just thought it was cool that you actually could boot old Windows versions in DOSBox. 

This thread has some more suggestions on handling games running too fast in wine: [http://ubuntuforums.org/showthread.php?t=791811](http://ubuntuforums.org/showthread.php?t=791811)

---

### Post by pieman711 on 2011-03-13
Cheers for all the info. Been playing around with cpulimit a bit more. I knew about the -e and -P options of it. for some reason I can't get it to work with for example "cpulimit -e DUNE2000 -l 5" where it would wait for a program called dune2000 to run then throttle that.

"
pieman@pieman-desktop:/$ cpulimit --exe Dune2000 -l 10
Warning: cannot renice.
To work better you should run this program as root, or adjust RLIMIT_NICE.
For example in /etc/security/limits.conf add a line with: * - nice -10

Warning: no target process found. Waiting for it...
"

 It should jump in as soon as it starts (it does when I use wineserver instead of DUNE2000 but that doesn't appear to affect the game speed)
Loading the game with wine pressing ctrl+alt+f4 and finding the ps id then using that with cpulimit using the -p option works but is far from ideal. 

Unfortunatly another problem I've run into using my cpulimit workaround method is that now I've got the sound working it comes out quite choppy and broken, especially if i throtle the cpu to anything less than 50%.

Has anyone tried dune legacy? it says 'playable' on the sourceforge website but by no means finished!

Also looking at the thread suggested by lykeion it suggests using system-->admin-->services. I don't have that on my menus (10.04, lucid lynx) is there an alternative in this distro?

---

### Post by cogadh on 2011-03-13
Your answer is in that error message. Cpulimit requires sudo or root permissions to do its thing, so if you used sudo to run it, it should jump in when the game is actually launched with Wine like it is supposed to. NOTE: don't use sudo to run Wine itself.

---

### Post by lykeion on 2011-03-14
> **pieman711 said:**
> Also looking at the thread suggested by lykeion it suggests using system-->admin-->services. I don't have that on my menus (10.04, lucid lynx) is there an alternative in this distro?
I think it was removed in Karmic. You can use the service command to manage services:
```
sudo service --status-all
sudo service <service_name> stop
```
I think the actual name of the CPU Frequency Manager service is *powernowd*

And actually I thought that happyhamster's tips in that thread seemed most useful: [http://ubuntuforums.org/showpost.php?p=4949343&postcount=6](http://ubuntuforums.org/showpost.php?p=4949343&postcount=6)

Also I came to think of an applet called CPU Frequency Selector. Have you tried it? See here: [http://geeksok.com/blog/2008/07/ubuntu-cpu-frequency-selector/](http://geeksok.com/blog/2008/07/ubuntu-cpu-frequency-selector/)
It might work to set set your CPU frequency lower, but it depends on your motherboard/processor if it supports power-stepping or not.

---

### Post by pieman711 on 2011-03-14
Forgot to mention that I was trying cpulimit with sudo and without and with all combinations of DUNE2000 uppercase and lower case and with .dat and .exe and without to no avail. 

using the cpu freq moniter in panel says i dont support it:

 You will not be able to modify the frequency of your machine.  Your machine may be misconfigured or not have hardware support for CPU frequency scaling.

I think I'll have a look at dune legacy later.

---

### Post by lykeion on 2011-03-14
EDIT: removed link to "abandonware"

Since Dune II is the "granddaddy" of all RTS games, there are lots of other remakes, see here: [http://forum.dune2k.com/index.php?/topic/20346-list-of-dune-ii-clones-and-remakes/](http://forum.dune2k.com/index.php?/topic/20346-list-of-dune-ii-clones-and-remakes/)

---

### Post by pieman711 on 2011-03-18
I gave up on Dune 2000 as the gameplay wasn't great and the graphics were a bit of a halfway stop between the retro dune II graphics and the Emperor:dune ones. I've got Emperor running great now and would recommend anyone to use this or the original dune II (or better yet contribute to getting dune legacy to fully functioning) 

One thing with my emperor installation though...
to get it to run it needs -c flag in command (ie. wine /PATH_TO_FILE/Emperor.exe -c)
Can I set it so i can run it from the menu... Applications>>wine>>westwood>>emperor I've had a look at what's there if you right click on the menu and change the settings but it doesn't look quite as simple as copying and pasting the command line as above...

---

### Post by cogadh on 2011-03-18
> **lykeion said:**
> You can download original DOS Dune II from here: link removed
Run it in DOSBox or use the PAKs for it to load Dune Legacy.

You might want to remove that link. So-called abandonware is actually pirated software and is very much illegal. It is definitely one of those "not allowed" things here on the Ubuntu forums.

---

### Post by lykeion on 2011-03-20
> **cogadh said:**
> You might want to remove that link. So-called abandonware is actually pirated software and is very much illegal. It is definitely one of those "not allowed" things here on the Ubuntu forums.

Okay link removed. I hadn't looked into abandonware before and assumed software classed as abandonware was in the public domain.
Personally though I can think it's kind of greedy to still demand people to pay for a game that's almost 20 years old and no longer available for purchase/download.

---

### Post by cogadh on 2011-03-20
> **lykeion said:**
> Okay link removed. I hadn't looked into abandonware before and assumed software classed as abandonware was in the public domain.
Personally though I can think it's kind of greedy to still demand people to pay for a game that's almost 20 years old and no longer available for purchase/download.
The concept of "abandonware" was created to justify the public release of copyrighted works without any of the legal rights to it, simply because it is difficult (but not actually impossible) to find legal copies of that software. It might be greedy to keep that stuff out of the public domain, but it is the law and you don't change the law by breaking it. 

Almost no video games have entered the public domain (yet). Thanks to the screwed up state of copyright law, it takes at least 50 years before a copyright "expires" (assuming nobody tries to extend or renew it), so it will be quite a while before we see anything from the computer age available publicly and legally. 

However, there are legal options for getting some of that old software, like Good Old Games (gog.com). Their prices are reasonable (nothing over $10), compatibility with modern (Windows) operating systems is guaranteed, they include tons of extras with the games and they are constantly adding "new" old games to their library. Who knows, maybe someday they will add the Dune games (fingers crossed).

---

### Post by pieman711 on 2011-03-22
It may be worth pointing out there are quite a few of the original C&C games like red alert and tiberium sun available free (as in beer) from their website and a few currently active projects porting them to be native in linux. Most of these are multiplayer based though

---

### Post by kompadre on 2012-07-11
Just in case somebody runs into same problem with this or another game: cpulimit looks for the /proc/$PID/exe link to correspond with what you put in -e (--exe=) argument. Now, a process that runs a windows executable seems to link to **wine-preloader** thingy. So running something like 

```
cpulimit -l nn -e wine-preloader &
```

should slow down your game once you load it. One mustn't forget to kill cpulimit afterwards though.

---

