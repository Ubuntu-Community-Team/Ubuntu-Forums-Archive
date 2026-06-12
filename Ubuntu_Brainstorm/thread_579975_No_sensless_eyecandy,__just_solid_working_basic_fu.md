---
title: "No sensless eyecandy,  just solid working basic functions"
date: 2007-10-18
forum: Ubuntu Brainstorm
---

### Post by Black16V on 2007-10-18
It's fine to have some eyecandy. But in my opinion it's very important to have 99.9% solid working basic functions. Spend time on improving those functions / fixing bugs. If time is leftover, go an code eyecandy or other things.... :)

*Sample one of many:*
One of the basic and for many user essential functions are: [COLOR="Red"]**SUSPEND 2 HDD**[/COLOR]
Ubuntu is now 3 year old, and after that time I didnt see any progress. (where the time is gone:confused:) Launchpad is full of [bugs,]("https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=suspend+disk&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=") where user cant use suspend 2 hdd. 

I use Ubuntu for 2 years but suspend 2 hdd never worked, no on my three desktop pc's, nor on my notebook. :(

If I would  know how to code / fixing software, I would help you, but i can't.


ps: sry for bad english, I hope you understand me.

---

### Post by Zdravko on 2007-10-18
Suspend would be a nice feature.

---

### Post by DizzyTech on 2007-10-18
It sounds like it's new.

Suspend *should* work, but right now it's only with tweaks.  For me, it's noapic noacpi resume=/dev/sda5 in the grub options and post_video=false in acpi-support

---

### Post by bigboy_pdb on 2007-10-18
The title sounds like something that the Windows guy in the Mac commercials would say.

I agree that functionality is more important that unnecessary features. Programming and debugging new GUI interfaces is already complicated enough without adding additional unnecessary features that would need to be tested, and there are more important things to worry about.

On the other hand, it seems that a number of people have been drawn to Linux because of projects like Beryl and Compiz. Pushing projects like these might work in favour of the Linux community because if people switch to Linux for cutting edge graphics, they'll be displeased by video cards that cannot support those features but that have the capacity to support them. This could cause an increase in the number of people who complain to hardware manufacturers about poor APIs and documentation.

---

### Post by buntunub on 2007-10-18
Suspend works flawlessly for me on my HP laptop, but I totally agree with your point. Eye candy and useless utilities are nothing but fluff if they dont work for 75% of those that try them, or buggy at best. In the long run, its only going to drive folks away and into the loving arms of PCLos, Sabayon, Mepis, and Debian.

---

### Post by bigboy_pdb on 2007-10-18
I forgot to mention that suspend doesn't work for me.

---

### Post by gruvsyco on 2007-10-18
I think you'll find a lot more people that use the Eyecandy than stuff like Suspend.  I'm not saying it isn't important but, the Eyecandy is what's gaining more attention for Linux right now and I think "most" people either leave their machines on all the time or shut down.

---

### Post by 23meg on 2007-10-19
> **Black16V]Spend time on improving those functions / fixing bugs. If time is leftover, go an code eyecandy or other things.... [/QUOTE]

The flaw in this argument has been pointed to many times: the assumed homogeneity of the workforce. No, we have a very heterogeneous workforce said:**
> Suspend would be a nice feature.

Suspend *is* a nice feature. It exists.

> **DizzyTech]Suspend should work, but right now it's only with tweaks.[/QUOTE]

In an ideal world, suspend should work for everyone. In the present non-ideal world, it works **for you** with tweaks, and for someone else with a different machine  it has always worked out of the box without tweaks, and for me, with three different laptops it has never worked in any Ubuntu release (and I've used every Ubuntu release), with or without tweaks. 

Without proper support from manufacturers and unless the ACPI mess is cleared up, it's always going to be hit and miss said:**
> In the long run, its only going to drive folks away and into the loving arms of PCLos, Sabayon, Mepis, and Debian.

Which happen to use the same kernel, Linux, and will fail or succeed at more or less the same rate with some negligible variation.

---

### Post by Zdravko on 2007-10-19
[23meg]("http://ubuntuforums.org/member.php?u=11472"), does Ubuntu support the suspend feature?

---

### Post by 23meg on 2007-10-19
As in giving you the option to suspend if your computer seems to support it, yes. However, the real question is how well the Linux kernel supports it on your particular hardware. It's impossible for distro developers to test each and every piece of hardware in existence before shipping the OS, so improving things depends on the ability of the actual users of the hardware to report whether things are working for them, and individual developers to find ways (, workarounds, hackish fixes) of making things work, most of the time with little in the way of hardware specs or assistance from the manufacturer.

Compare this to the situation with Apple, who both assemble the hardware and produce the software, and thus can make sure every hardware-dependent bit in the software works 100% well, or to the situation with Microsoft, who either have agreements with or direct support of all major hardware manufacturers, and bundle their OS with machines which the vendors test to be working with it, and you get a more realistic picture of the situation.

---

### Post by Zdravko on 2007-10-19
[23meg]("http://ubuntuforums.org/member.php?u=11472"), I don't understand why software devs need to test the HW, but not the hardware devs to build their hardware in an appropriate manner.

---

### Post by 23meg on 2007-10-19
A big part of the problem is that many hardware vendors basically don't care enough about Linux. Besides, software constantly changes, whereas the hardware, once it's manufactured, remains the same.

---

### Post by Zdravko on 2007-10-19
What??? But this is terrible! Ubuntu must punish them! They must be forced to work hard on producing Ubuntu-compatible hardware!
No, really - I am serious.

---

### Post by 23meg on 2007-10-19
The way to punish them would be not buying their products. Preferring supported hardware from manufacturers that do care also saves you headaches, and gives you "solid working basic functions".

---

### Post by Zdravko on 2007-10-19
How do I know which are the "good" and which are the "bad" guys to buy from?

---

### Post by bethaviv on 2007-10-19
> **Zdravko said:**
> How do I know which are the "good" and which are the "bad" guys to buy from?

Find something you're thinking about buying. Check their home page to make sure they have linux drivers, check the forums to make sure those drivers work (this is the important part) and then decide if it will be a hassle for you or not.

If the drivers have issues, I'm sure the forums will also show different options that are supported fully in Linux.

---

### Post by Zdravko on 2007-10-19
Okay. Thanks for the advice.

---

### Post by SunnyRabbiera on 2007-10-25
another topic on stability vs. flashy stuff.
is getting things like compiz and flashy graphics really more important then having a stable OS?
personally I dont think so, I think the next ubuntu should have a balance of flash and stability as opposed to just one or the other.

---

### Post by 23meg on 2007-10-25
[QUOTE=SunnyRabbiera]another topic on stability vs. flashy stuff.[/QUOTE]

No need to have two topics on the same subject; merged.

---

### Post by SunnyRabbiera on 2007-10-25
it is an issue though...

---

### Post by smartboyathome on 2007-10-26
> **SunnyRabbiera said:**
> another topic on stability vs. flashy stuff.
is getting things like compiz and flashy graphics really more important then having a stable OS?
personally I dont think so, I think the next ubuntu should have a balance of flash and stability as opposed to just one or the other.

I like Compiz as it is. Not too heavy, yet still gives you some eye candy. Also, Cube is not turned on by default, so there is no worrying about 3D graphics not being supported. How much more balance should there be?

---

### Post by SunnyRabbiera on 2007-10-26
the thing is that i personally feel that ubuntu is more focussed on making flashy things then making a usable and stable system, its almost microsoft like in that respect and i think we need to focus more on stability then how much flash ubuntu has by default.
i personally prefer stability.

---

### Post by 23meg on 2007-10-26
See post #8.

---

### Post by Choad on 2007-10-26
@21
if compiz is enabled, you need 3d acceleration. just because the 3d cube is the only effect that "looks" 3d, doesn't mean it's the only thing that *uses* 3d

---

### Post by VCSkier on 2007-10-26
FWIW, suspend and hibernate both work on my laptop when running openSUSE 10.3, but have never worked on the same laptop when running Ubuntu 5.10 through 7.10.  I deal with it though.  It would be a nice feature to have, but not critical for me.

With regard to stability, I find Ubuntu's balance of stability and cutting edge features ideal for me.  That does not mean that it is ideal for everyone.  Those of you that are dissatisfied with Ubuntu's perceived instability might be happier running Debian.  IMHO, the bottom line is this: Support F/LOSS, and use what works best for you.

---

### Post by SunnyRabbiera on 2007-10-26
> **Choad said:**
> @21
if compiz is enabled, you need 3d acceleration. just because the 3d cube is the only effect that "looks" 3d, doesn't mean it's the only thing that *uses* 3d

yes I know, but forcing people to use hyper 3d cards just to use the OS sounds no better then what microsoft is doing with vista.
ubuntu should have not just two versions but three.
a version that has all the hyperactive eye candy
a version for computers without hyperactive eye candy
and of course the alternate CD.
by focusing more on eye candy then functionality we are no better then the very evil we are trying to fight.

---

### Post by Whiffle on 2007-10-26
Hyper 3d cards just to run the OS?  My laptop has a intel 910 GMA, probably one of the weaker 3d chipsets on a modern computer.  Works great w/ compiz.  I havn't gotten aroud to playing with the vga and svideo output though.  Nonetheless, it doesn't take much of anything to run ubuntu.  And if what you have still isn't enough, just uninstall the eyecandy.  No big deal.

On stability, it depends heavily on the hardware I think.  Given the wide range of hardware on the market today, I think its flat out amazing that most hardware is supported rather well, especially in an operating system that is developed and maintained entirely in peoples free time, and then distributed for free.  In the end, I think it comes down to the individual user.  When you're buying hardware, do a little legwork and figure out how well its supported under linux.  I did that before I bought my Thinkpad and have been very pleased with its linux performance.  Nearly everything works out of the box, its only got one restricted driver (for the modem), and it runs great overall.

---

### Post by SunnyRabbiera on 2007-10-26
but you have to install the OS just to uninstall the eyecandy, and that in itself might be hard for older computers.
I have a intel 915 video card, not top of the line and it does seem to work relatively fine with compiz but that is not the point.
I think there should be a version of ubuntu that does behave well with older computers, that is all... plus even i with my semi decent specs had a LOT of issues getting ubuntu just right.
I had issues with usplash, xorg and the hardware configuration tools given in gutsy, i think all these three areas are the cause of the other issues I had in the past...
lets not be like microsoft here people, lets not blindly bog down the system with mindless eyecandy, if Hardy is the next LTS then we should make every effort that its just as stable and reliable as dapper.

---

### Post by smartboyathome on 2007-10-26
> **SunnyRabbiera said:**
> but you have to install the OS just to uninstall the eyecandy, and that in itself might be hard for older computers.
I have a intel 915 video card, not top of the line and it does seem to work relatively fine with compiz but that is not the point.
I think there should be a version of ubuntu that does behave well with older computers, that is all... plus even i with my semi decent specs had a LOT of issues getting ubuntu just right.
I had issues with usplash, xorg and the hardware configuration tools given in gutsy, i think all these three areas are the cause of the other issues I had in the past...
lets not be like microsoft here people, lets not blindly bog down the system with mindless eyecandy, if Hardy is the next LTS then we should make every effort that its just as stable and reliable as dapper.

Compiz isn't really bogging down the computer like people said, and for those WITH older computers, there is Xubuntu. No need to make two distros for the same purpose.

---

### Post by SunnyRabbiera on 2007-10-26
yeh but xubuntu isnt as good in some areas in my opinion, XFCE still has issues on her that I dont like.

---

### Post by smartboyathome on 2007-10-26
> **SunnyRabbiera said:**
> yeh but xubuntu isnt as good in some areas in my opinion, XFCE still has issues on her that I dont like.

Like what? I have not had any issues with it yet besides there not being a good menu editor.

---

### Post by bmt on 2007-10-26
On the original topic, it has been disappointing to find regressions in some of the everyday stuff.  I'm thinking of SD card readers and photo import, for example, both of which worked on Dapper, but have been broken along the way and stayed that way through at least one upgrade.

Personally, I don't see the point of most of the Compiz/Beryl effects, but if it draws the crowds, all well and good.  It's just a bit embarrassing to have to plug in an external card reader instead of using the internal one -- and having to use the same external card reader to import photos instead of just plugging in the camera.

---

### Post by 23meg on 2007-10-26
[QUOTE=SunnyRabbiera]but you have to install the OS just to uninstall the eyecandy,[/QUOTE]

Compiz doesn't get activated on unsupported hardware or hardware with buggy drivers. If it does, that's a bug, which you're supposed to file as the owner of the hardware.

[QUOTE=bmt]
On the original topic, it has been disappointing to find regressions in some of the everyday stuff.[/QUOTE]

Regressions suck. But the problem is with establishing casuality between regressions and "eye candy", in other words, assuming automatically that regressions happened because "eye candy" that was developed elsewhere by different people than those who work on the kernel and Ubuntu was integrated into Ubuntu. Again, see post #8.

---

### Post by bmt on 2007-10-28
> **23meg said:**
> ... But the problem is with establishing casuality between regressions and "eye candy" ...
I'm not even suggesting that regression is caused by eye candy.

I am saying that headline-catching features (e.g., Compiz et al) working out of the box is all very nice.  Regressions of fundamental features (e.g., internal card readers, import photos from camera), which have been reported through early beta or even the previous version, is extremely disappointing.  New users, attracted by the visual features, will soon drift away again when they find some of the other 'features'.

I'm not pointing a finger at anyone in particular, just making an observation.

Before someone tells me I should have stayed with Dapper, I upgraded to fix a couple of printing problems and to use more recent versions of some applications (which needed newer libraries).

---

### Post by 23meg on 2007-10-28
[QUOTE=bmt]I'm not even suggesting that regression is caused by eye candy.[/QUOTE]

I didn't mean to say that *you* were; it's just a common misconception.

---

