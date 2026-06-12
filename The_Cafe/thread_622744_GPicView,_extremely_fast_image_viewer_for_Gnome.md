---
title: "GPicView, extremely fast image viewer for Gnome"
date: 2007-11-25
forum: The Cafe
---

### Post by PCMan on 2007-11-25
GPicView is an extremely fast and user-friendly image viewer for Linux desktop.
_[http://www.gnomefiles.org/app.php/GPicView](http://www.gnomefiles.org/app.php/GPicView)_  (deb package for Ubuntu is provided)

There are already tons of feature-rich image viewers on Linux desktop, so why do we need a new image viewer here?
Try it yourself, and you'll know why.
GPicView is not aimed to be powerful. It tried to be as slim as possible, and features lightning fast start-up.
This is very important while you just want to see what's inside the image file.

Here is a screenshot:
[IMG]http://lxde.sourceforge.net/gpicview/screenshot.jpg[/IMG]

**Features:**
* Extremely lightweight and fast with low memory usage
* Very suitable for default image viewer of desktop system
* Simple and intuitive interface
* Minimal lib dependency: Only pure GTK+ is used
* Desktop independent: Doesn't require any specific desktop environment
* Open source, licensed under GNU GPL

GPicView is aimed to replace the default image viewer of current desktop systems.
Fast-startup, low memory usage, and simple user interface make it a good choice for default viewer.
The user interface is apparently inspired by the default image viewer of Windows xp.
So GPicView should be quite friendly to users previously using Windows.

**FAQ:**
How to make GPicView the default image viewer of the system?
Just run the following command line in terminal:
 ```
xdg-mime default gpicview.desktop `grep 'MimeType=' /usr/share/applications/gpicview.desktop | sed -e 's/.*=//' -e 's/;/ /g'`
```

NOTE: xdg-utils is needed here. It's a tool released by Portland project of Freedesktop.org. Most modern Linux distros have this tool installed by default.

---

### Post by dips_xe on 2007-11-25
did you help develop this?

---

### Post by PCMan on 2007-11-25
> **dips_xe said:**
> did you help develop this?
I'm the lead developer of this program.

---

### Post by masmre on 2007-11-25
Good work. Thank you :)

---

### Post by popch on 2007-11-25
It is very nice and fast. However, most of my pictures are in the network on SMB shares. I can view those with the viewer supplied with ubuntu. I have not yet succeeded doing so with yours.

---

### Post by meborc on 2007-11-25
i like gpicview as a small and fast program... but it still has some problems...

for example when i open a big picture (bootchart image i.e.) then the image is automatically resized to fit the window... when i zoom in with +, it gets reverted to fit windew in 3-4 sec...

now this does not happen 100% of the cases... only about 80% :) and when opening smaller images, this does not occur

thanks for a great program! :)

---

### Post by PCMan on 2007-11-25
> **meborc said:**
> i like gpicview as a small and fast program... but it still has some problems...

for example when i open a big picture (bootchart image i.e.) then the image is automatically resized to fit the window... when i zoom in with +, it gets reverted to fit windew in 3-4 sec...

now this does not happen 100% of the cases... only about 80% :) and when opening smaller images, this does not occur

thanks for a great program! :)
Thanks. I didn't get this kind of problems, but gpicview does have some performance-related issues when doing image scaliing.  
It can be more optimized.  However I don't know how to do it currently.
I'm a medical student, not a programmer.  So, help is needed, and any kind of patch highly appreciated.

---

### Post by aimran on 2007-11-25
Thumbs up and thank you for this neat program =)

Edit: Also I like the GUI...

---

### Post by Steveway on 2007-11-25
Nice but I prefer ristretto.
Ristretto is aimed at the XFCE-Desktop so it's very lightweight.
It supports many filetypes, including animated .gif and .mng files, I now only two more viewers on Linux that support that.
And it has many more nice features.
The Homepage: [http://goodies.xfce.org/projects/applications/ristretto](http://goodies.xfce.org/projects/applications/ristretto)
My Thread about it, including a little guide for the installation: [http://ubuntuforums.org/showthread.php?t=554009](http://ubuntuforums.org/showthread.php?t=554009)

---

### Post by Polygon on 2007-11-25
good program, i like it alot

some suggestions:

make it so when you start gpicview but it doesnt have any images loaded, you either have it just show the title bar and the icons (best example of this is VLC)...the big white box hurts my eyes cause im on a darkish theme.

and also, make it a preference to have it open new images in a new window, or the same window that is already open.

thirdly, when you are viewing a small image, you still have the whitebackground problem. maybe make it follow the gtk+ theme?

and fourthly, having it support animated GIF's would be amazing.

---

### Post by -grubby on 2007-11-25
this is nice. I love it!

---

### Post by Vadi on 2007-11-25
I use it too.

A small suggestion though - do you think you could make the degree-turning buttons look nicer? :/

---

### Post by aimran on 2007-11-26
> **Vadi said:**
> I use it too.

A small suggestion though - do you think you could make the degree-turning buttons look nicer? :/

I guess they could work on that =)

---

### Post by PCMan on 2007-11-26
> **aimran said:**
> I guess they could work on that =)
Here is a big problem.
We can bring our own nice icons for these 2 buttons, but can the icons compatible with the icon theme used by the user?
For example, if the user uses Crystal SVG icon theme for his/her Gnome, and we give them Human-style orange icons, that will be a disaster and really hurts the user's eyes. If the user uses icons from Mac OS X, and we give them Gnome/Tango-style icons and mix our icons with those OSX ones, I cannot imagine how ugly it will be.
Any suggestion?
I have no idea how can make this better.

---

### Post by aimran on 2007-11-26
> **PCMan said:**
> Here is a big problem.
We can bring our own nice icons for these 2 buttons, but can the icons compatible with the icon theme used by the user?
For example, if the user uses Crystal SVG icon theme for his/her Gnome, and we give them Human-style orange icons, that will be a disaster and really hurts the user's eyes. If the user uses icons from Mac OS X, and we give them Gnome/Tango-style icons and mix our icons with those OSX ones, I cannot imagine how ugly it will be.
Any suggestion?
I have no idea how can make this better.

Personally I think the "90" is blurry on the rotate buttons. I've attached a screenshot for reference. I think it's a minor inconvenience however - there are much more important things to do like gif support, or maybe even swf ;). So sorry if we had to take up your time with such trivialities. 

I'm working to create a very responsive system so kudos for your good work so far =)!

Edit: A quick image search on google for "arrows" reveal a lot of nice circular arrows,albeit without "90". I do realise the reason for putting the "90" there is for users to not confuse between refresh and rotate.

---

### Post by Polygon on 2007-11-26
> **PCMan said:**
> Here is a big problem.
We can bring our own nice icons for these 2 buttons, but can the icons compatible with the icon theme used by the user?
For example, if the user uses Crystal SVG icon theme for his/her Gnome, and we give them Human-style orange icons, that will be a disaster and really hurts the user's eyes. If the user uses icons from Mac OS X, and we give them Gnome/Tango-style icons and mix our icons with those OSX ones, I cannot imagine how ugly it will be.
Any suggestion?
I have no idea how can make this better.

i believe there are set icons for rotating left and right

for example, here is a screenshot of Eye of Gnome...note the Left and Right rotate buttons, those would be much better choices...and since this is the default gnome viewer im sure the icons exist somewhere.

---

### Post by Vadi on 2007-11-26
Yeah, even those scaled down would be nice.

---

### Post by aimran on 2007-11-26
Another note: Scrolling up seems to be the more intuitive way to zoom into images. GPV has scrolling down as zoom in.

To check this I've asked around for opinions.

Edit: Also it would be nice if the empty area around the image were available for scrolling when being zoomed in. Currently the only way to view other parts of the image are via scrollbars.

---

### Post by cinematography on 2007-11-28
Very nice, fast, image viewer! I've made it my default.

---

### Post by imon9 on 2007-12-16
hi PCman,

i have some question and request:

(1) why didn;t Gpicview view pic by the sequence of the filename? i got the photos randomly jumping for 1 file to the next when i press the next button. Is there a place to setup?

(2) can u add quick resize funtion? i hate to fire-up other application just for the sake of resizing the photo :) much appreciated

---

### Post by PCMan on 2007-12-18
> **imon9 said:**
> hi PCman,

i have some question and request:

(1) why didn;t Gpicview view pic by the sequence of the filename? i got the photos randomly jumping for 1 file to the next when i press the next button. Is there a place to setup?
It's a fixed bug. Please upgrade to the latest version.

(2) can u add quick resize funtion? i hate to fire-up other application just for the sake of resizing the photo :) much appreciated
I'd like to.
However, I don't know how to add this and keep the user interface clean and simple at the same time. Any suggestion?
Some GUI mock-up will be helpful.

---

### Post by Polygon on 2007-12-18
just have a button that looks like a scaling button (like a small box in a corner, then a larger box overlapping it in the right corner) and when you click that, it asks for dimensions, along with a box to keep aspect ratio and all that and a ok / cancel button. that would work.

---

### Post by pt123 on 2007-12-19
Love this app. too, very much like the Windows Image Fax Viewer on XP.

---

### Post by PCMan on 2008-01-29
Sorry, no exciting new features or important bug fixes.

But the ugly icons was replaced by better ones. (Good news!)
Besides, new locales fr and nl were added.
In addition, now you can set GPicView the default viewer of supported image types from the preference dialog, which is cool. (* xdg-mime is needed here)

So, GPicView 0.1.8 is released.
Ubuntu deb package for Feisty/Gutsy was provided here.
[http://www.gnomefiles.org/app.php/GPicView](http://www.gnomefiles.org/app.php/GPicView)

Cheers!

---

### Post by ubu-for on 2008-02-03
> **PCMan said:**
> GPicView is an extremely fast and user-friendly image viewer for Linux desktop.

I like your program!

But I miss two features. If I press the "F" key gThumb switches between fullscreen and the normal screen and if I press "Home"/"End" key gThumb jumps to the first/last picture.

I know you've set the fullscreen feature to the "F11" key, but maybe in your next version the user could change this hotkey in the preferences.

Thanks in advance!

---

### Post by graabein on 2008-02-23
Good stuff PCMan! I'm going to use this on my Xfce box and try it on my main also. One minor thing I can't get is the name, GPicView, cause it's pure GTK? Shouldn't it be called PCManPV or PCManPic or something? 

:lolflag:

I love your work. Keep it up!

---

### Post by Gen2ly on 2008-03-01
This is well done so far.  Except for feh this loads pictures faster than any other application I've tried.  It browses all images in a directory, and resizes them - about all I need.  A couple differing preference... perhaps.  I like it when the gnome theme defines the window background (see pic), and the control bar is Bill the Cat... Windows.

---

### Post by ubu-for on 2008-03-07
Do I have to compile the new version 0.1.9 or will there be a deb-file in the near future?

Is it possible to hide the (next, previous, zoom) buttons?

THX for your great work!

---

### Post by energy. on 2008-04-22
I like this.  thanks!

---

### Post by jackpipe on 2009-06-02
Nice and fast, good job, and thank you.

A couple of observations - obviously these are my own personal preferences, and I don't mean to criticize gpicview which I think is a really good job, but I've tried to state the reasons I think things should work the way I describe.
BTW, I'm using version 0.1.7-1, on ubuntu 8.04 - the build tools on here are not new enough to compile the 0.2 gpicview source.:


**The fit button should fit (ie stretch) images that are smaller than the window size.**
I see you are calling the fit function hardcoded with FALSE for the can_strech boolean:
```
main_win_fit_window_size( mw, FALSE, GDK_INTERP_BILINEAR );
```So images are not stretched to fit windows that are larger than the source image.  I know this is also the way other viewers work, but it makes no sense to me.  If I want to view the image at original size, I can use the "1:1" function.  But there is no way to stretch smaller images to fit the window size, without manually zooming.


**Mouse scroll-wheel should zoom.**  I tried version 0.1.10, but there is a major usability problem here, to me.  The mouse scroll wheel in 0.1.7 zooms in and out of the image.  In 0.1.10, the mouse wheel "scrolls" through the images in the current directory.  Can we change this back, or make it an option?

**first-person shooter zoom direction**To me, the mouse-wheel zoom works the wrong way also.  Moving the mouse wheel forward, ie scroll down, should zoom in.  The reason, is that moving the mouse wheel forward feels like "I want to move forward", sort of like a first-person shooter.  When I move forward the image should zoom in.  This is also the way the compiz zoom-desktop function works for example.  I know that's not intuitive to everyone though.


**Zooming should zoom into the mouse location, not keep the origin at 0,0.**  When you zoom into an image, when the image becomes larger than the window, further zooming always keeps the top-left of the image fixed to the top-left of the window.  Say you're trying to zoom in to a particular country on a big map.  You keep having to pan the image, because the position of the country changes as you zoom in.  The zoom should zoom in to the mouse position.  For the case where you really do want to keep the image at top-left, maybe the buttons should default to zooming in to 0,0.  But even here, the obvious thing is for the buttons to zoom in to the center of the window, and you cn pan the image in order to center the part of the image you want to zoom.  This is also another reason why the mouse-wheel should zoom - since it's impossible to zoom into the mouse location when you're using the mouse to press the zoom button.


**The control panel should be at the top.**  OK, maybe I'm weird in this way, but I think the research shows it's quicker when the controls are at the top.  The reason, is simply that application menu bars, and window controls (minimize/maximize/etc) are nearly always at the top, and if all the controls are near each other, you don't have to move the moouse so far, and you can keep your mouse movements accurate since you have a smaller area to cover.  I have my gnome panel (just one, with everything on it) set to be always at the top of the screen.  My firefox tabs, and url bar are at the top.  Application menu bars are at the top.  The alternative would be to have all the controls (including application menus, window controls etc) at the bottom, or the side.  All in the same place, anyway.  Maybe the control panel location could be an option?


**GPicView should stay focused as a viewer.**  I think you should avoid requests to add more image manipulation features, since this is after an an image VIEWER.  Image rotate is useful because many cameras screw up the image orientation, but I don't think other features are useful in a viewer.  I see you added flip_v, and flip_h, in 0.1.10, which were already present in the DCT transform routines, so I guess it didn't add much to the code, but I can't really see the value.  Perhaps "brightness" and "contrast" might be useful features, but I would strip out the save-file functionality entirely - if I want to edit an image, I want some control over the quality of the transformations, the compression quality, etc, etc, and I would use a proper image EDITOR for this.


**Animated gif support** would be fantastic.  I think gthumb shows animated gifs, but otherwise you have to load them into your browser, which isn't a great image viewer.


**Initial window size problem with tiff image.**  I have a tiff image that causes the initial window to open bigger than my screen  (1400x1024).  Everything else works fine, just the initial window opens with the control panel off the bottom of the screen (another reason the controls should be at the top?).



Anyway, thanks again for writing gPicView - once I get ubuntu upgraded here, I'll probably make some of these changes to the code myself - but I'm not clued in to open source development, so not sure how I'd submit code for your consideration.

---

### Post by jackpipe on 2009-06-02
OK, I see you altered on_scroll_event() to scroll if the mouse wheel is modified with the ctrl key, but default to "previous/next image".
Personally, I'd prefer the other way, ie zoom by default, use ctrl key for next/previous - especially since left/right scrolling already does prev/next, for those that have 7 button mice.

---

### Post by Polygon on 2009-06-02
yeah i agree, its usually custom with most image viewers to have zoom bound to the scroll wheel, and i find my self accidentally going to the next image while scrolling when i want to zoom.

or at least make it an option? =P

---

### Post by UbuWu on 2009-06-02
Another similar nice, small and fast image viewer is [Viewnior]("http://xsisqox.github.com/Viewnior/").

---

### Post by Orlsend on 2009-06-02
WoW it seems like winner!

I screenshots look good,slim and fast. now I was wondering it there was deb to this heavenly goodie?

keep it up.

---

### Post by Polygon on 2009-06-02
its in the jaunty repos

sudo apt-get install gpicview

---

### Post by jackpipe on 2009-06-03
Thanks for the viewnior recommendation; [http://xsisqox.github.com/Viewnior/](http://xsisqox.github.com/Viewnior/)

It's a really nice viewer, lightweight, fast, and just really well executed.
It fixes some, actually, all, the issues I raised about GPicView, except the stretching small images to fit - and I've changed the code to work the way I like, for that issue.
It's now my default image viewer.

---

### Post by Happy-Dude on 2009-07-09
I was just wondering; are there any keyboard shortcuts for GPicView? Like, a shortcut to maximize the image without the need to click on the button?

---

### Post by bashphoenux on 2009-09-21
it doesnt open gif images :(

---

### Post by birvis on 2010-01-04
Great viewer, but it would be nice to have status bar or something like that with basic image info (date, size, scale, etc.).

---

### Post by sashamoniker on 2010-04-04
this is a wonderful image viewer, i searched long for a good one before i found it,
then when i had to reinstall my OS and had forgotten what it was called,
i searched long again :)

one thing that would make it perfect for me would be
the option to open the currently viewed image in an editing programme,
the option being available from the context menu.
just an "Edit.." entry which opens a "start-program" dialogue.

i already recommend gpicview to everyone, but i'd be even more enthusiastic about it with that alteration.
regards

---

### Post by dragos240 on 2010-04-04
You know what's even better. Fbi.

---

