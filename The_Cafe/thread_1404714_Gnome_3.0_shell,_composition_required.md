---
title: "Gnome 3.0 shell, composition required?"
date: 2010-02-11
forum: The Cafe
---

### Post by forcecore on 2010-02-11
Just simple question that i heard Gnome 3.0 shell works only when graphics driver is enabled, what happens when i have only poor driver or no driver??? that question has haunted me long time.

---

### Post by Psumi on 2010-02-11
mutter won't work without compositing, which is required to run gnome shell.

---

### Post by Kenny_Strawn on 2010-02-11
GNOME Shell does require compositing, that's for sure. However, any standard Microsoft DirectX 9-capable graphics card is capable of handling compositing. I even have it running on my Acer Aspire One AOA110-1545 netbook!

---

### Post by NightwishFan on 2010-02-11
The gnome 2 panel should be available for sometime to come.

---

### Post by Psumi on 2010-02-11
> **NightwishFan said:**
> The gnome 2 panel should be available for sometime to come.

However, if it is indeed to be the default of gnome, ubuntu will have it by default. People who wish to have gnome 2, or are forced to, will need to use the CLI in the mini.iso, which is not ideal.

---

### Post by NightwishFan on 2010-02-11
I think it would just fall back as does Compiz. Also, if it was really that big of a problem Ubuntu might **not** have it as default.

---

### Post by Psumi on 2010-02-11
> **NightwishFan said:**
> I think it would just fall back as does Compiz. Also, if it was really that big of a problem Ubuntu might **not** have it as default.

it can't. GNOME Shell kills all instances of gnome-panel. an extra script will have to be written to first kill gnome-shell if the graphics are not adequate, then start gnome-panel.

---

### Post by NightwishFan on 2010-02-11
I do not think it is impossible to enable fallback on gnome2. Gnome shell has a built-in option to close itself.

While running shell, just press alt+f2 and type: debugexit

Something like that could be implemented. (As debugexit does not entirely solve what you are saying.)

---

### Post by 311005901 on 2010-02-11
Oh my. GNOME Shell is so ugly. :(
/troll

---

### Post by FuturePilot on 2010-02-11
> **311005901 said:**
> Oh my. GNOME Shell is so ugly. :(
/troll

Ancient screenshots are ancient

---

### Post by 311005901 on 2010-02-11
> **FuturePilot said:**
> Ancient screenshots are ancient
I've installed and used it.
:p

---

### Post by NightwishFan on 2010-02-11
[http://ubuntuforums.org/showpost.php?p=8809254&postcount=670](http://ubuntuforums.org/showpost.php?p=8809254&postcount=670)

---

### Post by Psumi on 2010-02-11
> **NightwishFan said:**
> [http://ubuntuforums.org/showpost.php?p=8809254&postcount=670](http://ubuntuforums.org/showpost.php?p=8809254&postcount=670)

You forgot to show the notification area. :(

---

### Post by sudoer541 on 2010-02-11
for those who want gnome3 picz look @ OMG !!!!! ubuntu blog!!!!

btw I know the site takes forever to load plus its too bloated....ewwww but I love that site!!!!

---

### Post by AllRadioisDead on 2010-02-12
> **sudoer541 said:**
> for those who want gnome3 picz look @ OMG !!!!! ubuntu blog!!!!

btw I know the site takes forever to load plus its too bloated....ewwww but I love that site!!!!
Looks fine to me, and it loads pretty much instantly. If you have trouble loading that site, you may want to get your connection looked at.

---

### Post by Kenny_Strawn on 2010-02-12
Like I said before: GS does require compositing, but I assume it will be no different in Ubuntu than Aero is in Windows: activating [color="Red"]only[/color] when it sees a compositing graphics card or when you activate a proprietary driver.

---

### Post by WinterMadness on 2010-02-12
With all this hooplah over gnome 3, im thinking maybe Ubuntu should have a KDE or Gnome option when you install it. Kind of like how Opensuse does it, instead of having two separate whatevers. Some people will try ubuntu with gnome 3 and be turned off by it, might as well give them some choices.

of course, this would mean that the  Ubuntu implementation would have to be done *well* as opposed to how its done with kubuntu.

---

### Post by 3rdalbum on 2010-02-12
> **Kenny_Strawn said:**
> Like I said before: GS does require compositing, but I assume it will be no different in Ubuntu than Aero is in Windows: activating [color="Red"]only[/color] when it sees a compositing graphics card or when you activate a proprietary driver.

Gnome Shell is based on Mutter/Clutter, which is OpenGL at the core. So, if you don't have OpenGL drivers then your desktop will be unusably slow. You can emulate this by turning on Metacity compositing in gconf-editor and then switching on Gnome Shell, but DO NOT do this on a production machine, and make sure you close all your programs before doing this.

I have no idea what Gnome is going to do as a fallback, unless they can add a non-GL backend to Mutter.

---

### Post by rahilm on 2010-02-12
isn't there an option for compiz...i don't like to leave compiz..

---

### Post by juancarlospaco on 2010-02-12
*I like things like gnome-shell and eagle-view more than kde 4.x/XFCE*

---

### Post by skymera on 2010-02-12
I used Gnome Shell for a while.

Must say, the worst step in software development i've seen in a long time.

Ps. Gnome lover, KDE hater :)

---

### Post by Merk42 on 2010-02-12
> **rahilm said:**
> isn't there an option for compiz...i don't like to leave compiz..

Nope, compiz isn't compatible with GNOME Shell

*[shameless plug for the GNOME Shell thread in the testing subforum](http://ubuntuforums.org/showthread.php?t=1305154)*

---

### Post by Kenny_Strawn on 2010-02-12
> **3rdalbum said:**
> Gnome Shell is based on Mutter/Clutter, which is OpenGL at the core. So, if you don't have OpenGL drivers then your desktop will be unusably slow. You can emulate this by turning on Metacity compositing in gconf-editor and then switching on Gnome Shell, but DO NOT do this on a production machine, and make sure you close all your programs before doing this.

I have no idea what Gnome is going to do as a fallback, unless they can add a non-GL backend to Mutter.

Not to mention: Any standard DirectX 9 graphics card can handle compositing just fine. The only way GNOME Shell won't work is with a 4-year-old card.

---

### Post by Satoru-san on 2010-02-12
> **Kenny_Strawn said:**
> Not to mention: Any standard DirectX 9 graphics card can handle compositing just fine. The only way GNOME Shell won't work is with a 4-year-old card.
I did a quick google search. I am not sure about what the requirements for compositing are, but I checked into directx 9 and forund this 
```
DirectX 9.0 4.09.00.0900 (RC4) 
December 19, 2002
```
Seems that it came out in 2002, which is good thing too because I can composite on my laptop from 2003.

---

### Post by forcecore on 2010-02-12
what happens if i use Ubuntu for rescue on computer where no driver available or i install Ubuntu on pc where i must later download and install for example atidriver.run driver??? i got terminal only with no menus...???

---

### Post by Jesus_Valdez on 2010-02-12
What happens if im on a dessert island with only a 386 pc computer and 1 ubuntu cd, would be able to run it? I DONT THINK SO GNOME-FAIL.

---

### Post by Satoru-san on 2010-02-12
> **Jesus_Valdez said:**
> What happens if im on a dessert island with only a 386 pc computer and 1 ubuntu cd, would be able to run it? 
[IMG]http://i8.ebayimg.com/01/s/07/b5/1e/b8_2.JPG[/IMG]Thats my kind of island, especially if it has power. If you swap out the ubuntu cd for a openBSD cd, I think you could actually be pretty happy, you could even code your own programs :)

---

### Post by rahilm on 2010-02-13
> **Merk42 said:**
> Nope, compiz isn't compatible with GNOME Shell

*[shameless plug for the GNOME Shell thread in the testing subforum](http://ubuntuforums.org/showthread.php?t=1305154)*

well they better find a way to get compiz compatible..even if it means disabling the shell by giving an option...i think that's possible. It does that now when i tested gnome shell few days back..

else, make gnome shell kick compiz in the teeth.

---

### Post by Tibuda on 2010-02-13
> **rahilm said:**
> well they better find a way to get compiz compatible..even if it means **disabling the shell by giving an option**...i think that's possible. It does that now when i tested gnome shell few days back..

else, make gnome shell kick compiz in the teeth.

like running compiz as a standalone window manager?

---

### Post by Psumi on 2010-02-13
> **danielrmt said:**
> like running compiz as a standalone window manager?

It still won't work.

Compiz is fundamentally incompatible with GNOME Shell. (Because Mutter is the window manager, with Metacity as the decorator)

Also note that compiz development has halted or slowed considerably. So much so that there hasn't been a new compiz version in a little while.

---

### Post by Tibuda on 2010-02-13
> **Psumi said:**
> It still won't work.

Compiz is fundamentally incompatible with GNOME Shell.
It will work, or I misunderstood him. I thought he asked for a way to disable gnome-shell to run compiz. Just don't run gnome-shell at all.

> Also note that compiz development has halted or slowed considerably. So much so that there hasn't been a new compiz version in a little while.
I know, that's sad.

---

### Post by Psumi on 2010-02-13
> **danielrmt said:**
> It will work, or I misunderstood him. I thought he asked for a way to disable gnome-shell to run compiz. Just don't run gnome-shell at all.

Since, I'm sure, ubuntu will use GNOME 3 by default after 10.10, this will not be possible for average users who don't or can't use GNOME Shell. Average users will be forced to learn how to use the CLI through the mini.iso, like I did. (I never knew you could configure a wireless connection through it until I tried.)

---

### Post by Tibuda on 2010-02-13
> **Psumi said:**
> Since, I'm sure, ubuntu will use GNOME 3 by default after 10.10, this will not be possible for average users who don't or can't use GNOME Shell. Average users will be forced to learn how to use the CLI through the mini.iso, like I did. (I never knew you could configure a wireless connection through it until I tried.)

I agree, setting alternate wms is not for avg users. People unsatisfied with Gnome-Shell will have to switch to Xubuntu/Kubuntu/etc or install from CLI.

---

### Post by Psumi on 2010-02-13
> **danielrmt said:**
> I agree, setting alternate wms is not for avg users. People unsatisfied with Gnome-Shell will have to switch to Xubuntu/Kubuntu/etc or install from CLI.

Xubuntu is too intensive for old computers such as the ThinkPad T41 with only 512 MB of RAM, 32 MB Video Card (ATI FireGL) and 40 GB of Space (1.4 GB of SWAP on default installs) and a 1.60 GHz single-core NON-HT (so no precious logical second core to save me.) With default ubuntu, Compiz slows the machine to a stop by doing ANYTHING but right-clicking the desktop or viewing tooltips on the panels. Sadly, compiz is enabled by default due to the fact that the open-source ATI drivers are capable of handling this card's 3D functions.

As I said in another thread about RAM usage: My current usage of RAM is about 180 / 496 MB of RAM (using no swap.) This is a predicament as Firefox can take up, easily, 100+ MB of RAM, and Pidgin taking up 17-30 MB of RAM depending.

In all, I have to swap totem for parole, as parole is lighter (not much, only by about 1-4 MB of RAM usage less.) I would use Ayttm, but the current version in karmic can't connect to MSN, and stay connected for more than 5 minutes, and YIM doesn't even connect in ayttm. And I can't compile ayttm too as I've said in another thread, nor can I get alien to convert their RPM to a deb (wrong arch.) However, ayttm still used about 17 MB of RAM.

I AM glad that slim is being put back in lucid, and that parole is being considered for inclusion for repo status starting with lucid+1.

---

I have to stay with this computer as long as I don't have 1000+ USD, which will take a year or so to save up. But first, I need a new TV, so it may take more than a year or two. which is fine, since I plan to stick with the LTS throughout its cycle.

---

### Post by NightwishFan on 2010-02-13
I have a machine that runs well on Ubuntu 8.04 at those specs. A bit better card I believe, but Intel.

On 64-bit I set my machines to use vm.swappiness=100, which seems to help.

---

### Post by Merk42 on 2010-02-13
> **rahilm said:**
> well they better find a way to get compiz compatible..even if it means disabling the shell by giving an option...i think that's possible. It does that now when i tested gnome shell few days back..

else, make gnome shell kick compiz in the teeth.

I don't see why they'd need to. Two different groups of people.

Best case scenario the various utilities you use in Compiz will be ported via extensions to Mutter.

---

