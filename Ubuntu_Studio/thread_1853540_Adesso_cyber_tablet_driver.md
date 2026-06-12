---
title: "Adesso cyber tablet driver"
date: 2011-10-02
forum: Ubuntu Studio
---

### Post by Metal Hed on 2011-10-02
I was wondering if any one out there has found a compatible driver for Adesso cybertablets? The model I have is an M14, sure would love to use this damn thing in Ubuntu

---

### Post by Favux on 2011-10-02
Hi Metal Hed,

I believe the WizardPen drivers work for the Adesso's.

Let's collect some information on your tablet.  With it plugged into a USB port run the following commands in a terminal and post the output.
```
xinput list
```
and
```
lsusb
```
For lsusb you can just post the line that has the tablet in it.

---

### Post by sgx on 2011-10-02
[http://ubuntuforums.org/archive/index.php/t-312948.html](http://ubuntuforums.org/archive/index.php/t-312948.html)

Bodhi linux is working on an E17 debian install for Archos tablets, the second alpha is due shortly.

[http://jeffhoogland.blogspot.com/2011/09/bodhi-linux-powered-tabletnetbook-give.html](http://jeffhoogland.blogspot.com/2011/09/bodhi-linux-powered-tabletnetbook-give.html)

[http://www.bodhilinux.com/forums/index.php?/forum/25-archos-gen8-tablets/](http://www.bodhilinux.com/forums/index.php?/forum/25-archos-gen8-tablets/)

not sure about ubuntu, sometimes we have to switch hardware to get the desired results.
Cheers

---

### Post by Dbl1HandR on 2012-10-09
hey, this is metal head.... I sort of put my tablet down for a while but I want to get it back up and running. this is what the info is when i punch those commands in:

xinput line:    &#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Mouse                                  id=12    [slave  pointer  (2)]
&#9116;   &#8627; AlpsPS/2 ALPS GlidePoint                    id=13    [slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Media Tablet     id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Acer Crystal Eye webcam                     id=10    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=11    [slave  keyboard (3)]
    &#8627; ENE eHome Infrared Remote Receiver          id=14    [slave  keyboard (3)]
    &#8627; WALTOP International Corp. Media Tablet     id=16    [slave  keyboard (3)]
    &#8627; WALTOP International Corp. Media Tablet     id=17    [slave  keyboard (3)]
and for lsusb: Bus 003 Device 002: ID 172f:0500 Waltop International Corp.

not sure what you make of it but to me it looks like my comp is recognizing it but it still isn't acting like a tablet. Hope some one can help

cheers

---

### Post by Favux on 2012-10-09
Hi Dbl1HandR,

Your Adesso CyberTablet M14 is called by the DIGI*mend* project the Waltop Media Tablet 14.1" (172F:0500):  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)  And it should be working depending on your release of Ubuntu.  Are you using Precise (12.04)?

What is the output of:
```
xsetwacom list
```
It isn't acting like a tablet but how is it acting?

---

### Post by Dbl1HandR on 2012-10-12
the pen works, but when I go in to the preferences of either inkscape or gimp, it won't allow me to make it an active devise, which means the tablet is essentially acting as a mouse and not a tablet. I can't use my zoom and toggle buttons that are on it, nor can i store tools to the preset buttons that are around the edge of the tablet.  I'll get it eventually, or I'll get a new tablet. I haven't really been happy with it from the get go. I've used it on mac os, and windows too and it's just not what I thought it was going to be. I think i'll spend a bit more money and do more research. Probably a wacom tablet, they seem to be the most user friendly with Linux. I'm running 11.04 for 2 reasons, 1) I have an older computer and 2) I HATE!!! the unity interface. It's set up too much like new windows and mac, I really like the old interface and as far as I know 11.04 is the last version that keeps the classic interface

---

### Post by Dbl1HandR on 2012-10-12
when i put in code xsetwacom list it shows me nothing

---

### Post by Favux on 2012-10-12
> the pen works, but when I go in to the preferences of either inkscape or gimp, it won't allow me to make it an active devise, which means the tablet is essentially acting as a mouse and not a tablet.  when i put in code xsetwacom list it shows me nothing 
OK Natty, that gives us something to work with.  The problem is most likely your tablet's pen is currently on the evdev driver, not the Wacom X driver.  That's further bolstered by the fact we don't see stylus appended to the device name in **xinput list**.  It should say:
```
&#9116; &#8627; WALTOP International Corp. Media Tablet stylus id=15 [slave pointer (2)]
```
I forget Natty's default version of xf86-input-wacom:
```
xsetwacom -V
```
But it lacks a match for the Waltops in 50-wacom.conf.  So you create a custom .conf that does match to the Waltop and places it on the Wacom driver.  See the [Waltop HOW TO]("http://ubuntuforums.org/showthread.php?t=1595648").
> I can't use my zoom and toggle buttons that are on it, nor can i store tools to the preset buttons that are around the edge of the tablet.
The preset buttons or hotkeys aren't supported in linux.  The description on the DIGImend site doesn't mention frame buttons.  But I see the entries for them in your xinput list:
```
&#8627; WALTOP International Corp. Media Tablet id=16 [slave keyboard (3)]
&#8627; WALTOP International Corp. Media Tablet id=17 [slave keyboard (3)]
```
If supported those will be on the evdev driver and treated as keyboard keys.  See if the custom .conf gets them working.  It could be you need a more recent evdev than the one in Natty.
> I'm running 11.04 for 2 reasons, 1) I have an older computer and 2) I HATE!!! the unity interface. It's set up too much like new windows and mac, I really like the old interface and as far as I know 11.04 is the last version that keeps the classic interface 
I think you're correct.  I came to terms with Unity by installing Cairo Dock as usual but moving it to the right edge of the screen rather than along the bottom.  Tweaked it to look like the Unity taskbar and stuck on it the missing Gnome 2 features like the Gnome Menu.  Also have Gimp, Inkscape, MyPaint, my weather applet, etc. on it.

But if you can't come to terms with Unity you should consider Linux Mint.  Mint 13 is basically Ubuntu Precise (12.04) but instead of Unity it uses a Desktop that more closely emulates Gnome 2's look and feel.  In fact you have your choice of two Desktops, MATE or Cinnamon, both Gnome 2 like.

---

### Post by Dbl1HandR on 2012-10-13
just installed and running Mint, so far so good

---

