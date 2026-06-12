---
title: "ubuntu 10.10 logs out automatially when wine is used"
date: 2011-04-11
forum: Wine
---

### Post by arctic_tux on 2011-04-11
hi im semi new to ubuntu (1 month) and i have been trying toget wine to run age of empires 2, but every time i try to use wine ubuntu logs out a few seconds after the installer for AOE pops up.

this problem also happens when i click on "configure wine" in the applications menu
i have tried wine on some other exe's with the same problem:confused:

"If using Wine causes very nasty problems like system freezes requiring a  hardware reset or the **xserver crashing and dumping you back to the  login screen **(is what happens), then there is a deeper problem with your system that Wine  is simply exposing.  The most common cause of this is problematic  drivers.  Upgrading to the latest Ubuntu release can often solve these  problems."

will upgrading to natty narwhal soon help?

thanks in advance:D

ps

i am running ubuntu 10.10
my pc has an amd processor(is this a problem?)
32mb graphics card lol
im using wine v1.2.2
PlayOnLynux also installed (same problem when it tries to start wine)

---

### Post by cogadh on 2011-04-11
Upgrading to Natty might not help much, that upgrade instruction/comment is more directed at people who are still running woefully out of date versions of Ubuntu, which you are not. 

As a general rule, the AMD processor should not be a problem.

What graphics card is it? Knowing the amount of vram it has doesn't really tell us much, the make and model would tell us more.

---

### Post by arctic_tux on 2011-04-11
on the side of my machine it just says "Integrated graphics with 32mb video memory"
it is an integrated card so i presume it is made by the same company as the motherboard.
it does not say what make the motherboard is but it is a compaq computer with an amd processor.

it is a compaq presarioS5020AN purchaced around 2002

i hope this is the info you are after

---

### Post by cogadh on 2011-04-11
Open a terminal and run this:
```
lspci | grep VGA
```
That will tell you exactly what video card/chipset you have.

---

### Post by arctic_tux on 2011-04-11
it says:

01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]

:KS

---

### Post by cogadh on 2011-04-11
That is likely your problem right there, I don't think Ubuntu has specific drivers for that video card (it's really old). There are some legacy drivers available for it, but I've never actually dealt with an S3 product in Linux, so I'm not sure what's involved with installing them:
[http://www.s3graphics.com/en/drivers/legacy_software_archive.aspx](http://www.s3graphics.com/en/drivers/legacy_software_archive.aspx)

You might also want to check the HP/Compaq website to see if they have any Linux drivers available for that card (doubtful).

---

### Post by arctic_tux on 2011-04-11
dang i cant find the drivers anywhere but thanks heaps for your help anyway
i will keep looking and do more google searches but i dont think i will ever find the driver.
but if i do will all of my problems go away or are there more pieces of the puzzle?
thanks again:KS:D
EDIT: i have found there are no available drivers (for lynux anyway) is there any other ways around this problem? or do i have to get a new graphics card. might be easier to go without games. or get a new computer

---

### Post by cogadh on 2011-04-12
Honestly, you would probably have a hard time finding a graphics card that would work in that machine; it only has a PCI or AGP slot for a replacement graphics card. Both PCI and AGP has been mostly replaced by PCI Express (in AGP's case, completely replaced). I don't think any graphics card manufacturers are still making PCI cards (some might, but PCI performance is terrible) and I know for certain that none of them are making AGP cards anymore. If you are serious about gaming in Linux, especially through Wine, you'd be much better off with a whole new PC, rather than trying to get that machine working as gaming system.

---

### Post by arctic_tux on 2011-04-12
ok thanks for your help anyway i cant believe another website wanted to charge me $50 for an answer for my question

thanks

---

### Post by Marco.75 on 2011-04-14
Hi, I saw this thread and I'm in the same situation:

- same card (actually same family: S3 Prosavage DDR, but the driver should be the same: note that it is supported by xorg: look at [http://www.x.org/wiki/savage](http://www.x.org/wiki/savage) and [http://dri.freedesktop.org/wiki/S3Savage](http://dri.freedesktop.org/wiki/S3Savage))

- same behaviour: black or mangled screen and log-out after a few seconds running winecfg or notepad, or any wine app.

- same ubuntu version (10.10) 

BUT: I can assure I used wine without any problem under ubuntu 10.04! As I am seeking also for a solution, as the OP, I'm wondering if this is really a graphics driver issue...:confused:

---

### Post by Marco.75 on 2011-04-15
UPDATE:

As I wanted to see the error messages I executed to the terminal:

winecfg > logfile.log 2>&1

the output in logfile.log is:&#8206; 

***XIO: fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"***

What does it mean?

---

### Post by cogadh on 2011-04-15
It means the video card drivers, which for whatever reason worked fine before, are not good enough or don't work right anymore. The problem is clearly some kind of lacking in the abilities of the video card drivers, other wise Wine would not generate errors in X.

---

### Post by Marco.75 on 2011-04-16
Doing some experiments...
I told Xorg to load the VESA drivers, now I can run wine... but of course with the limitations of the VESA standard drivers.

---

### Post by tormod on 2011-08-08
FYI, the S3 Savage cards are supported out-of-the-box in Ubuntu with the included savage xorg driver. There have been some issues though, so make sure you have all updates installed. For 3D acceleration you'd better install a 3.0 kernel as well.

Finally, there are many limitations in the hardware, so forget about compiz and such things. Also, many applications (games) depend on GL extensions that are not supported by these cards.

---

