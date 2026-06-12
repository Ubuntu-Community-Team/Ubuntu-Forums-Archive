---
title: "Impress won't start slideshow"
date: 2007-06-06
forum: Ubuntu Christian Edition
---

### Post by TravMan63 on 2007-06-06
I've installed Xubuntu, and converted to Ubuntu CE.

(unsuccessful in installing dansguardian, but that's a different issue)

I cannot make impress start a slide show.  When I click start slideshow, it freezes.
I have to hit control-alt del - and reboot

I have also installed 
java-1.4.2-gcj-4.1  -1.4.2.0
java-1.5.0-sun
java-1.5.0-sun-1.5.0.11
java-6-sun
java-6-sun-1.6.0.00
and
java-gcj

(this is an attempt to remove an error when I start impress in a terminal
: javaldx: Could not find a Java Runtime Environment! ) - 
(I'm not sure if this has anything to do with the presentation starting or if it's for macros)

I have tried to tell Impress where the JRE is /usr/lib/jvm - but it won't accept any of the folders

Other installs:
gedit
various codecs
fspot
movie player (totem)


Manually edited xconfig... (for the bit depth, to fix an error with Open Office  title bars) (change 24 to 16)
(don't change it to 12 or you won't be able to start x :) )


I have tried starting an empty presentation, or just typing 'hello' on the 1st slide.... nothing -

Please advise....
TIA

TM

---

### Post by TravMan63 on 2007-06-06
Update: (better but buggy)

I completely removed the core of open office (which removed many things),
and reinstalled Impress.

Now - still receive the java error as well as

(process:5066): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:5066): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

-- that pair of errors repeats about 2-3 times until I hit 'recover' - then it repeats a few more times.

Impress now has icons on the bottom (before I'm sure it was just text buttons (for inserting text etc) - I can create slides with text and they start fine.... HOWEVER... when I put in a movie file (mpg)... it starts to play for about 3-5 seconds - and then stops.

.... still plugging away at this...

TM

---

### Post by shane2peru on 2007-06-06
> **TravMan63 said:**
> Update: (better but buggy)

I completely removed the core of open office (which removed many things),
and reinstalled Impress.

Now - still receive the java error as well as

(process:5066): GLib-GObject-CRITICAL **: gtype.c:2242: initialization assertion failed, use IA__g_type_init() prior to this function

(process:5066): Gdk-CRITICAL **: gdk_screen_get_font_options: assertion `GDK_IS_SCREEN (screen)' failed

-- that pair of errors repeats about 2-3 times until I hit 'recover' - then it repeats a few more times.

Impress now has icons on the bottom (before I'm sure it was just text buttons (for inserting text etc) - I can create slides with text and they start fine.... HOWEVER... when I put in a movie file (mpg)... it starts to play for about 3-5 seconds - and then stops.

.... still plugging away at this...

TM

TravMan,  Not sure if this will help, but how are you doing your install and uninstall?  The best thing for you to do is to run this in the terminal ```
sudo aptitude install openoffice.org2 openoffice.org2-base openoffice.org2-calc openoffice.org2-common openoffice.org2-core openoffice.org2-draw openoffice.org2-writer openoffice.org2-impress 
```  That should cover the whole basis.  aptitude is a little more inclusive than apt-get that is why I would recommend that.  I'm just shooting in the dark here.  Hope that helps.

Shane

---

### Post by TravMan63 on 2007-06-07
I believe I have installed using both add/remove and synaptic... (on xubuntu)

However - I'm running ubuntu-ce now from live cd...
and everything is working fine - I can play wmv, mpg, mp3, ogg files fine in impress.

Perhaps there is something to the 'full install' (which exists on ubuntu-ce - but not on xubuntu...) - when OO write was installed, then I installed impress, I had the 'not starting issues, and no icons ... )

I'll give that a try and report back.

Thanks!
TM

=====
edit
I attempted running impress from console with
ooffice -impress %U
- I had none of the errors listed above, but an error 'home/ubuntu/%U does not exist' (perhaps from running from live cd?)

=====

---

### Post by shane2peru on 2007-06-07
> **TravMan63 said:**
> I believe I have installed using both add/remove and synaptic... (on xubuntu)

However - I'm running ubuntu-ce now from live cd...
and everything is working fine - I can play wmv, mpg, mp3, ogg files fine in impress.

Perhaps there is something to the 'full install' (which exists on ubuntu-ce - but not on xubuntu...) - when OO write was installed, then I installed impress, I had the 'not starting issues, and no icons ... )

I'll give that a try and report back.

Thanks!
TM

=====
edit
I attempted running impress from console with
ooffice -impress %U
- I had none of the errors listed above, but an error 'home/ubuntu/%U does not exist' (perhaps from running from live cd?)

=====

I'm sure there are some missing lib files or all the dependencies are not solved.  Synaptic should make sure that you get all those dependencies, but sometimes you have to install some other things.  I'm no expert just trying a few thought to get things working for you.  And especially running Xubuntu, that means you are not running Gnome desktop.  Perhaps your upgrade from Xubuntu to CE removed a few packages that you need?  I know that CE is developed and run on Gnome mostly.  There have been a few that have run it on Xubuntu and KDE I think.  Let me know what you find out about running that in the terminal.

Shane

---

### Post by TravMan63 on 2007-06-07
Thanks for the replys

I have it working! (on (a different) machine with live cd)
(no audio - hmmmm) - on the system running live cd - xubuntu
(I didn't have audio with ubuntu ce - live cd on this machine - until I rebooted... (I have 2 sound cards))

I have not 'converted' (this machine) to CE - that may be a factor

Installed totem player (not the xine .... one - well I did- didn't work, then did the other)
Installed gedit
Installed the gstreamer codecs (2 from add/remove)

I did NOT install all (or any other part of) the oo suite (it may have been installed on the xubuntu system by default? it (and automatix) - are not on the live cd...)

I STILL receive the same errors - java and etc - BUT - it works (other than the usual (but not always) crash when exiting - that appears to be a 'common error')

NOW the hope is it will work on the machine where xubuntu is installed...
Funny (or NOT funny) - I'm sure I did the same config on that machine - perhaps I have the wrong totem player installed?

I would run a full gnome ce version - if the machine had more ram (256)...
there were some graphic issues with gnome as well (the gnome desktop didn't render properly - may be a xorg.conf issue ?... bit depth worked on a problem with ooffice title bars being distorted...)

TM

=====
update:

I just installed the CE 'conversion'
it still plays fine...
(firefox was changed - but can't see anything else - I did log off and on - but obviously can't reboot)

=====

---

### Post by TravMan63 on 2007-06-07
Simple solution:

Install Totem with gstreamer - Remove other Totem (that works with xine - note that add/remove does this for you)

It's a bit laggy - but is working fine now.

Thanks for your help

TM

---

### Post by shane2peru on 2007-06-08
> **TravMan63 said:**
> Simple solution:

Install Totem with gstreamer - Remove other Totem (that works with xine - note that add/remove does this for you)

It's a bit laggy - but is working fine now.

Thanks for your help

TM

Sounds like you solved it yourself!  Sorry I couldn't be of more help.  :popcorn:  Glad it is fixed!

Shane

---

### Post by stairwayoflight on 2007-06-15
> **TravMan63 said:**
> I've installed Xubuntu, and converted to Ubuntu CE.

Haha, you converted :-)

---

### Post by shane2peru on 2007-06-15
> **stairwayoflight said:**
> Haha, you converted :-)

Perhaps you should consider doing the same.  :)  ha ha.  :)

We do have a sense of humor.

Shane

---

