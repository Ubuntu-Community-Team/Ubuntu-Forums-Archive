---
title: "My Ubuntu CE v2.0 (Edgy-Beryl)!"
date: 2006-12-02
forum: Ubuntu Christian Edition
---

### Post by mhancoc7 on 2006-12-02
I have been tweaking my personal Ubuntu CE v2.0 (Edgy) installation. I decided to give Beryl a try. It is really awesome.

I really can't put into words how nice I think it is. I had hesitated trying Beryl, because I did not really know much about it and was concerned that my video card would not support it. 

I have attached a few screenshots of my current setup.

Jereme

---

### Post by gerbman on 2006-12-02
> **mhancoc7 said:**
> I have been tweaking my personal Ubuntu CE v2.0 (Edgy) installation. I decided to give Beryl a try. It is really awesome.

I really can't put into words how nice I think it is. I had hesitated trying Beryl, because I did not really know much about it and was concerned that my video card would not support it. 

I have attached a few screenshots of my current setup.

JeremeLooks nice. Do you have links to any guides for setting that up?

---

### Post by mhancoc7 on 2006-12-02
> **gerbman said:**
> Looks nice. Do you have links to any guides for setting that up?

Thanks!

Here are some links to the sites that I used. I made a few customizations to the theme and the Beryl splash screen. I may, if I get the time, put together a How to for it.

[http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/AiGLX)
[URL="http://www.gnome-look.org/content/show.php?content=49102"]
http://www.gnome-look.org/content/show.php?content=49102[/URL]

Jereme

---

### Post by Darrious on 2006-12-02
Looks pretty neat. I did have beryl installed once. It was great and all except for  a couple of things. 

It did not run video very well. I do know that there is a plugin to fix this problem though. 

Two, it just makes everything look cool. After a while I just don't seem to want it that much. 

Although it looks really cool!

---

### Post by HareBall on 2006-12-02
> **mhancoc7 said:**
> Thanks!

Here are some links to the sites that I used. I made a few customizations to the theme and the Beryl splash screen. I may, if I get the time, put together a How to for it.

[http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/AiGLX)
[URL="http://www.gnome-look.org/content/show.php?content=49102"]
http://www.gnome-look.org/content/show.php?content=49102[/URL]

Jereme

I am trying to install Beryl from the instructions on this page [http://christer.homeip.net/index.php/2006/10/29/beryl-with-latest-nvidia-drivers-aiglx-no-xgl-ubuntu-610/](http://christer.homeip.net/index.php/2006/10/29/beryl-with-latest-nvidia-drivers-aiglx-no-xgl-ubuntu-610/)
And every time I try to open my sources I get a permission denied message. I have even tried to go directly to the file and open it, but all I get is a quick flash like it opened and closed real fast. Any idea why I can't open my sources.list?](*,)

---

### Post by Darrious on 2006-12-02
You should try to check permissions on it. Maybe it does not allow you to access it with a regular user.

Become root.
```
su
```Then try to edit your sources.list and see if that works.

```
sudo gedit /etc/apt/sources.list
```

---

### Post by HareBall on 2006-12-02
> **Darrious said:**
> You should try to check permissions on it. Maybe it does not allow you to access it with a regular user.

Become root.
```
su
```Then try to edit your sources.list and see if that works.

```
sudo gedit /etc/apt/sources.list
```

Thanx Darrious, That got me what I needed. I don't know how It got that way. I am the only person using this computer. My wife don't like Ubuntu, so I bought her a laptop with XP on it so she would at least check her email:)

---

### Post by Darrious on 2006-12-02
Well I think that sources.list is only meant for root to edit. But I'm pretty sure that users can read it. You may have changed it in some way or another. 

Oh well

---

### Post by HareBall on 2006-12-02
> **mhancoc7 said:**
> Thanks!

I may, if I get the time, put together a How to for it.

Jereme
Please do, I have been trying for about two hours and Each time I find a how-to something somewhere along the way won't install. I started one and Their server had been down so they lost the repo's. Then I started another and when it got to where it was going to get some part it got a 404 error. Then another the people had upgraded their server and forgot to reset the link to some other part.
I wouldn't have thought it would be this hard. According to what I have read, it should be up and running in about 15 minutes:mad:

---

### Post by Darrious on 2006-12-02
I think that it is just the matter of finding the right tutorial.

---

### Post by HareBall on 2006-12-02
> **Darrious said:**
> I think that it is just the matter of finding the right tutorial.I wouldn't care if it took half the day, if it would just work;)

---

### Post by Darrious on 2006-12-02
Why don't you just try the tutorial on the beryl website. It is for Aiglx and 
Edgy. It works like a charm. I've never been able to get beryl working in dapper. But for Edgy it works great. Edgy comes with AIGLX installed so that now when I follow that guide it works great. I actually tried  that guide for Edgy  about 5 to 6 different times just to get it to work. :D

---

### Post by HareBall on 2006-12-02
> **Darrious said:**
> Why don't you just try the tutorial on the beryl website. It is for Aiglx and 
Edgy. It works like a charm. I've never been able to get beryl working in dapper. But for Edgy it works great. Edgy comes with AIGLX installed so that now when I follow that guide it works great. I actually tried  that guide for Edgy  about 5 to 6 different times just to get it to work. :D

Do you have a link to this site?

---

### Post by Darrious on 2006-12-02
Yea here it is.
 
[http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/AiGLX)

---

### Post by mysticrider92 on 2006-12-02
That looks pretty awesome. I can't wait until I get a new video card to try that out (I can't really get any eye candy to work with intergrated graphics).

---

### Post by HareBall on 2006-12-03
> **Darrious said:**
> Yea here it is.
 
[http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/AiGLX)

Thanx, I got it to run from there. This is so cool!!:KS 
The only thing I want to know is how to start it without having to start it from terminal each time I reboot. I would have thought there would be something in the Applications menu.

---

### Post by HareBall on 2006-12-03
> **HareBall said:**
> Thanx, I got it to run from there. This is so cool!!:KS 
The only thing I want to know is how to start it without having to start it from terminal each time I reboot. I would have thought there would be something in the Applications menu.

OK, now I have a problem. sometimes when I play with Beryl my title bars will disappear and I can't get them to come back until I reboot. Then everything is OK. Except when I reboot I have to press ESC to get my Grub to show up. Otherwise I have to keep hitting enter until it decides evrything is alright and goes to the signin screen](*,)

---

### Post by Darrious on 2006-12-03
Well I will look into the other problems, but I know the answer for the first question.

Go to System -> Preferences -> Sessions
Then go to the StartUp Programs tab and click Add.

Type in
 
```
beryl-manager
```
 then click add again and type in 
```
beryl
```

---

### Post by HareBall on 2006-12-03
> **Darrious said:**
> Well I will look into the other problems, but I know the answer for the first question.

Go to System -> Preferences -> Sessions
Then go to the StartUp Programs tab and click Add.

Type in
 
```
beryl-manager
```
 then click add again and type in 
```
beryl
```

Unless I get the problems worked out, I don't guess I really weant to run this on startup:rolleyes: 
I have been wondering if my video just isn't up to it. It is onboard my Dell Dimension desktop. I think it is Intel, but not really sure.
As far as my problem with the rebooting, I found that I don't have to do anything as long as I want to boot back into Ubuntu. It ends up at the login screen anyway. But I would still like to have the choice without pressing ESC.

---

### Post by mysticrider92 on 2006-12-04
To get the grub menu up without pressing escape,  boot into Ubuntu and open a terminal. Type > sudo gedit /boot/grub/menu.lstThis will open the configuration for grub. Look for a line that says something like "hidden menu" (I'm not on my Linux computer, I can check it later, just look for at the comments above it) and put a # sign in front of the line to show the menu at boot. There is also a line that tells the seconds until the first entry is booted, you may also want to raise that a bit. Remember to be careful with this file, messing it up could make your system unbootable. I hope that helps.

---

### Post by HareBall on 2006-12-04
> **mysticrider92 said:**
> To get the grub menu up without pressing escape,  boot into Ubuntu and open a terminal. Type This will open the configuration for grub. Look for a line that says something like "hidden menu" (I'm not on my Linux computer, I can check it later, just look for at the comments above it) and put a # sign in front of the line to show the menu at boot. There is also a line that tells the seconds until the first entry is booted, you may also want to raise that a bit. Remember to be careful with this file, messing it up could make your system unbootable. I hope that helps.
I checked this and hidden menu has 2 #'s in front of it. Do I need to get rid of one or add a third?
Here is my menu.lst:
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		15

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=234db7b6-ba61-414e-9ca2-8e7d94261540 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=769

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-386
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=234db7b6-ba61-414e-9ca2-8e7d94261540 ro quiet splash vga=769
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=234db7b6-ba61-414e-9ca2-8e7d94261540 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=234db7b6-ba61-414e-9ca2-8e7d94261540 ro quiet splash vga=769
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=234db7b6-ba61-414e-9ca2-8e7d94261540 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by mysticrider92 on 2006-12-04
On the section that looks like this:
> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
You want to make it look like this:
> ## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
The line that says "##hiddenmenu" is just saying that that is what the following value is. The part that the computer acually reads is two lines below that (without the "#" sign). Just put the "#" sign there on the third line. 

The # sign tells the computer that what follows is a quote and to ignore whatever is on the rest of that line (like // in C++ or /* in C).

---

### Post by Darrious on 2006-12-04
> **mysticrider92 said:**
> That looks pretty awesome. I can't wait until I get a new video card to try that out (I can't really get any eye candy to work with intergrated graphics).

To reply to this post, that was a few posts back, I have an integrated graphics card. I have beryl running pretty good. I is not perfect, but it really does run pretty well.

My graphics card is an Intel Integrated Graphics 82865G Card. It is not actually supposed to work with this type of card, I think, but it does.:D

What is your graphics card model. Check device manager.

---

### Post by HareBall on 2006-12-04
> **mysticrider92 said:**
> On the section that looks like this:

You want to make it look like this:

The line that says "##hiddenmenu" is just saying that that is what the following value is. The part that the computer acually reads is two lines below that (without the "#" sign). Just put the "#" sign there on the third line. 

The # sign tells the computer that what follows is a quote and to ignore whatever is on the rest of that line (like // in C++ or /* in C).

Thanx, when I get home I will change this and see what happens.

---

### Post by mysticrider92 on 2006-12-04
> **Darrious said:**
> To reply to this post, that was a few posts back, I have an integrated graphics card. I have beryl running pretty good. I is not perfect, but it really does run pretty well.

My graphics card is an Intel Integrated Graphics 82865G Card. It is not actually supposed to work with this type of card, I think, but it does.:D

What is your graphics card model. Check device manager.
Mine is the SiS chip on the MSI 761GM2 (something like that) motherboard. I have tried a few different things, but it doesn't seem to support things like transparency and good 3D stuff. I will get a new nVidia card this Christmas anyway, so I should be able to try more then.

---

### Post by Darrious on 2006-12-04
It should work if your getting nvidia. 

Actually I was going to ask what is the most recent nvidia graphics card that you can get.

---

### Post by HareBall on 2006-12-04
> **HareBall said:**
> Thanx, when I get home I will change this and see what happens.
Thanx, this worked:KS

---

### Post by mysticrider92 on 2006-12-26
Here is my Edgy CE/Beryl setup so far. The first picture is before I changed any beryl settings.

[Unchanged;]("http://img299.imageshack.us/img299/2366/beryl1mu8.png")                                   [ Kind of similar, but personalized.]("http://img73.imageshack.us/img73/1385/screenshotiu3.png")
[Proof that paying over $200 for Windows Vista is not necessary to get cool looking black glassy window borders.]("http://img78.imageshack.us/img78/6337/beryl2sk1.png")
I'm sure you have seen this before, but I just think it looks crazy. [Well, here it is.]("http://img149.imageshack.us/img149/235/berylcubeob3.png")
[Expose-like]("http://img45.imageshack.us/img45/8318/exposecloneto2.png")

These pictures don't really show what Beryl really looks like, but they are close enough.

I hope you don't mind if I got your nickname in the first picture.

---

### Post by Darrious on 2006-12-26
What can you use to take a picture of your cube.

---

### Post by mysticrider92 on 2006-12-26
To take a picture of the cube, zoom out to it (enable desktop cube in the beryl settings manager and use whatever the keybinding is to see it), and press Print Screen on your keyboard (on mine it looks like PrtScn/SysRq) to take a screenshot. You can also use this for menus and induvidual windows (press <alt><prtscn>).

---

### Post by HareBall on 2006-12-27
> **mysticrider92 said:**
> Here is my Edgy CE/Beryl setup so far. The first picture is before I changed any beryl settings.

[Unchanged]("http://img299.imageshack.us/img299/2366/beryl1mu8.png")

[Proof that paying over $200 for Windows Vista is not necessary to get cool looking black glassy window borders.]("http://img78.imageshack.us/img78/6337/beryl2sk1.png")

I'm sure you have seen this before, but I just think it looks crazy. [Well, here it is.]("http://img149.imageshack.us/img149/235/berylcubeob3.png")

These pictures don't really show what Beryl really looks like, but they are close enough.

I hope you don't mind if I got your nickname in the first picture.
Doesn't bother me, but I am jealouse of you for getting it to work. I just re-installed beryl and I still lose my title bars on all open windows.
I give up:( I ain't going to mess with it anymore.

---

### Post by mysticrider92 on 2006-12-27
Did you install the Emerald theme manager? You have to do that to get the title bars. Here is a link to the guide I followed: [http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit). And here is Pricechild's thread with links to guides for most systems: [http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104). The first one worked for me on my first try.

---

### Post by HareBall on 2006-12-27
> **mysticrider92 said:**
> Did you install the Emerald theme manager? You have to do that to get the title bars. Here is a link to the guide I followed: [http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit). And here is Pricechild's thread with links to guides for most systems: [http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104). The first one worked for me on my first try.
OK, I am good. I went ahe4ad and tried the first link and it works. I have title bars and everything. THANK YOU:p

---

### Post by Cows on 2006-12-27
> **mhancoc7 said:**
> Thanks!

Here are some links to the sites that I used. I made a few customizations to the theme and the Beryl splash screen. I may, if I get the time, put together a How to for it.

[http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/AiGLX](http://wiki.beryl-project.org/index.php?title=Install/Ubuntu/Edgy/AiGLX)
[URL="http://www.gnome-look.org/content/show.php?content=49102"]
http://www.gnome-look.org/content/show.php?content=49102[/URL]

Jereme

You desktop is really good btw. I went to the gnome-look.org website and downloaded a theme pack .. how do I install this?

---

### Post by mysticrider92 on 2006-12-27
@Cows
If it is a Beryl theme, you will need the Emerad theme manager (if you have titlebars on the windows, you already have it). Go to System>Preferences>Emerald Theme Manager. This window will let you select the theme you want from all of your installed themes. Click on the button to the left that says "Import Theme" and select the theme you want to install. This will be a file with the extention .emerald or .theme, I can't remember. Also, they may be in a tarball, you will need to unzip them first.

---

### Post by Cows on 2006-12-27
I just found out that you can just System > Preferences > Theme.

---

