---
title: "Wbar (an OS X like dock... smooth and easy)"
date: 2007-04-18
forum: The Cafe
---

### Post by igknighted on 2007-04-18
Does anyone else use the dock Wbar?  In my opinion it is the best OS X like dock there is for linux.  There is no delay, its very configurable (its a text file, but there are directions), and it is so smooth.  Heres a link to the fsf page about it, there's no real website to speak of, but the source tarballs are there to download and compile.  It comes by default on SAM Linux and I am using it on all my distro's because it is that good.

[http://directory.fsf.org/wbar.html](http://directory.fsf.org/wbar.html)

---

### Post by kwaanens on 2007-04-18
Care to share a screenshot?

- Ketil

---

### Post by Mateo on 2007-04-18
does it autohide?

---

### Post by notwen on 2007-04-18
I'm a avid AWN user, but this looks very nice.  I may hafta give this a try.  Does it organize launchers/open windows like AWN by chance?

---

### Post by BuffaloX on 2007-04-18
A couple of screenshots:

Nice one on freshmeat:
[http://freshmeat.net/screenshots/61844/66660/]("http://freshmeat.net/screenshots/61844/66660/")

And I think this is the right homepage, which doesn't say much, but it has a screenshot:
[http://wbar.warlockshome.com.ar/]("http://wbar.warlockshome.com.ar/")

---

### Post by igknighted on 2007-04-18
It does not autohide to my knowledge, but lets windows cover it if you want.

Screenshot:

---

### Post by Mateo on 2007-04-18
I don't see the point in a launcher that doesn't autohide.

---

### Post by Nils Olav on 2007-04-18
> **Mateo said:**
> I don't see the point in a launcher that doesn't autohide.

It's not like it doesn't serve its function.

---

### Post by igknighted on 2007-04-18
> **Mateo said:**
> I don't see the point in a launcher that doesn't autohide.

I suppose that is only an issue if you always maximize your windows, which I never do, so I always have a section of my screen free for it.

EDIT: Here is my config file with all the options listed so you can see:
```
sleep 5
wbar -isize 48 -j 1 -p bottom -balfa 40 -bpress -nanim 3 -z 2.5 -above-desk

#
# Options:
#   -config conf-file (eg: $HOME/.wbar)
#   -above-desk       run over a desktop app (ie: xfdesktop)
#   -isize  i         icon size (eg: 32)
#   -idist  d         icon dist (eg: 1)
#   -zoomf  z         zoom factor (eg: 1.8 or 2.5)
#   -jumpf  j         jump factor (eg: 1.0 or 0.0)
#   -pos    p         position:
#                        top | bottom | left | right | 
#                        center | <bot|top>-<right|left>
#   -dblclk ms        ms for double click (0: single click)
#   -bpress           icon gets pressed
#   -vbar             vertical bar
#   -balfa  i         bar alfa (0-100)
#   -falfa  i         unfocused bar alfa (0-100)
#   -filter i         color filter (0: none 1: hovered 2: others, 3: all)
#   -fc  0xAARRGGBB   filter color (default green 0xff00c800)
#   -nanim  i         number of animated icons: 1, 3, 5, 7, 9, ...
#   -nofont           if set disables font rendering

```

---

### Post by rai4shu2 on 2007-04-18
Looks nifty, but it doesn't interact well with panels and it seems like it steals focus any time you switch workspaces.

---

### Post by diskotek on 2007-04-18
i'm using it on SAM linux 2007 (pretty nice distro).... it comes default... i think it's nice, but i couldn't get comforted with it. when you open a web-page, it stays under...i couldn't configure it to place at bottom-bottom-center. result: it's cool, but...

---

### Post by igknighted on 2007-04-18
> **diskotek said:**
> i'm using it on SAM linux 2007 (pretty nice distro).... it comes default... i think it's nice, but i couldn't get comforted with it. when you open a web-page, it stays under...i couldn't configure it to place at bottom-bottom-center. result: it's cool, but...

Steal my config file if you want, mine is set at the bottom centered

---

### Post by Oki on 2007-04-18
Will I find Wbar in Synaptic with Feisty?

---

### Post by igknighted on 2007-04-18
Doubtful, although I am sure someone on a Ubuntu box could a quick .deb with checkinstall.  I would do it, but all my desktop's are RPM based atm

---

### Post by reacocard on 2007-04-18
> **igknighted said:**
> Doubtful, although I am sure someone on a Ubuntu box could a quick .deb with checkinstall.  I would do it, but all my desktop's are RPM based atm

Checkinstall is bad, but I'll give WBar a try and if I like it, I'll make a proper package for it.

---

### Post by diskotek on 2007-04-18
> **igknighted said:**
> Steal my config file if you want, mine is set at the bottom centered

hey thank you very much :) i'll try it when i'll open my sam linux box.. hmm may be i can try to port it to my ubuntu box :D

---

### Post by reacocard on 2007-04-18
WBar is nice, but the lack of autohide and composite make it useless to me. I built the deb anyway, it's attached.

---

### Post by aktiwers on 2007-04-18
It doesnt show up on Feisty.. atleast not for me?
> aktiwers@HAL:~$ wbar 
Using /usr/share/wbar/dot.wbar config file.



And it just stays there.. nothing happens?

---

### Post by rai4shu2 on 2007-04-18
wbar -above-desk

You guys realize that there's a 1.3, right?

---

### Post by Oki on 2007-04-18
Do you know of a bar that has option for "autohide" ? That would be nice. I know Dream Linux([http://www.dreamlinux.com.br/english/index.html](http://www.dreamlinux.com.br/english/index.html)) has a bar, but dont think it can hide(but very nice though). The bar is called "engage", from the xfce enviromet.

---

### Post by reacocard on 2007-04-18
> **Oki said:**
> Do you know of a bar that has option for "autohide" ? That would be nice. I know Dream Linux([http://www.dreamlinux.com.br/english/index.html](http://www.dreamlinux.com.br/english/index.html)) has a bar, but dont think it can hide(but very nice though). The bar is called "engage", from the xfce enviromet.

Engage is from enlightenment, not xfce.

---

### Post by PatrickMay16 on 2007-04-18
wbar certainly looks nice. But it doesn't function like the MacOS X dock, which is what it's trying to look like. The Mac OS X dock is more than just a launcher, you know.

---

### Post by Quillz on 2007-04-18
> **igknighted said:**
> Does anyone else use the dock Wbar?  In my opinion it is the best OS X like dock there is for linux.  There is no delay, its very configurable (its a text file, but there are directions), and it is so smooth.  Heres a link to the fsf page about it, there's no real website to speak of, but the source tarballs are there to download and compile.  It comes by default on SAM Linux and I am using it on all my distro's because it is that good.

[http://directory.fsf.org/wbar.html](http://directory.fsf.org/wbar.html)
I haven't read the rest of the thread yet. Is this in the repos? Every other dock I've tried, from KSmoothDock to KoolDock has just not worked.

---

### Post by rai4shu2 on 2007-04-19
You have to build it from source, but you probably only need build-essential and libimlib2-dev.

---

### Post by reacocard on 2007-04-19
> **Quillz said:**
> I haven't read the rest of the thread yet. Is this in the repos? Every other dock I've tried, from KSmoothDock to KoolDock has just not worked.

Not in the repos, but I posted a deb near the bottom of the first page. If you use beryl or compiz, you should also check out avant-window-navigator and kiba-dock for more options. IMHO, AWN is best right now.

---

### Post by Quillz on 2007-04-19
> **reacocard said:**
> Not in the repos, but I posted a deb near the bottom of the first page. If you use beryl or compiz, you should also check out avant-window-navigator and kiba-dock for more options. IMHO, AWN is best right now.
Ah, I'm running Ubuntu on a virtual machine, so I can't use Beryl yet. Will this run without it?

---

### Post by jiminycricket on 2007-04-19
> **PatrickMay16 said:**
> wbar certainly looks nice. But it doesn't function like the MacOS X dock, which is what it's trying to look like. The Mac OS X dock is more than just a launcher, you know.

I keep waiting for someone to make an exact replica of it, I do love it ;)  It makes dealing with multiple windows of one application really easy.  And pretty...

Poster above me: yes, AWN needs a composite manager running.

---

### Post by reacocard on 2007-04-19
> **Quillz said:**
> Ah, I'm running Ubuntu on a virtual machine, so I can't use Beryl yet. Will this run without it?

WBar will run without beryl. AWN and Kiba-dock will not.

---

### Post by Centx on 2007-09-12
well, you could use ttm (tint task manager) as your task manager, but better yet would be somebody integrating tint into wbar, and add the autohide functionality, if it could hold a tray too, it would be near perfect. (just pray it wont use too much resources though =/)

---

### Post by energiya on 2007-09-12
I used wbar for some time
[[img]http://pix.nofrag.com/c/0/2/84371bae4ce59d6de9c77b8807530t.jpg[/img]](http://pix.nofrag.com/c/0/2/84371bae4ce59d6de9c77b8807530.html)
very nice and resource friendly

---

### Post by aimran on 2008-01-26
Hi. Was setting up a lightweight Ubuntu installation for my old man and decided to use a dock for his 10.6" screen so he dont have to squint too much to find firefox :)

Problem is, installation went fine but runnig wbar yields:

```
 ... :~$ wbar
Using /usr/share/wbar/dot.wbar config file.
Using a Super Bar.
```

Which is similar to what this guy had [http://ubuntuforums.org/showthread.php?t=665432](http://ubuntuforums.org/showthread.php?t=665432)

I'm using Gutsy so any help would be appreciated.

---

### Post by aimran on 2008-01-27
I've solved the above problem. The wbar config file should be placed in the /home/username/ dir and named .wbar

Then start wbar with your initial settings: 
```
wbar -isize 48 -j 1 -p bottom -balfa 40 -bpress -nanim 3 -z 2.5 -above-desk
```

Or whatever the above settings you choose may be.


Thanks to m_gasior for this solution :)

---

### Post by dnns123 on 2008-01-27
I like it! I really think it looks better than AWN. I just hope it runs smoother. AWN is edgy in some cases.

---

### Post by DigitalDuality on 2008-01-27
d

---

### Post by aimran on 2008-01-27
> **dnns123 said:**
> I like it! I really think it looks better than AWN. I just hope it runs smoother. AWN is edgy in some cases.

It's much stabler to boot. Also without needing compiz, which i adore to use but hate to install.

This dock with the reflections icon set from styrizo (deviantart) rocks :)

---

### Post by equilibrium on 2008-06-08
I just put this on and it seems to segfault whenever you give it any arguments :(

If started with no arguments, it just doesn't seem to appear. :confused:

I'm running 8.04 64bit :(

So far I've tried kiba-dock which worked but didn't look right :( am currently just using a transparent bar at 48px for my icons :)

> ~$ wbar -isize 48
Using /usr/share/wbar/dot.wbar config file.
Using a Super Bar.
> ~$ wbar -isize 48 -j 1 -p bottom -balfa 40 -bpress -nanim 3 -z 2.5 -above-desk
Segmentation fault

---

### Post by LightB on 2008-06-08
> **DigitalDuality said:**
> i've lost all trust for Linux to get the dockbar right.

This is something that Apple has nailed and no amatuer project for Linux (or for Windows for that matter) has been able to properly duplicate it.

In Windows you lose your system tray and clock with each.  In Linux there's any multitude of problems.  The graphics aren't quite right, or aren't fluid enough, it doesn't handle workspaces or sys tray if you want it too, there's just always something missing.

the doc was nicely integrated into OS X and it pains me to say it but for once apple did something better than everyone else.

My opinion, the OSX dock is only slightly less slow and stupid. It's a nice idea whenever you can get it, but after a while, even when it works right it makes you sick that it's just trickling away resources all the time.

I don't know if this is strange or what, but back when gdesklets was alive and not scrap in the software junkyard, that dock worked better for me than anything. I used to replace desktop icons with it. Of course, it was just launchers, not a taskbar, but still, it was good. Or maybe I have the wrong hardware now, or it's just more complicated to make these thingers your taskbars, who knows.

---

### Post by diablo75 on 2008-06-08
I don't use Dock bars, but have tried AWN and Cairo Dock.  Cairo was better looking than AWN in my opinion, and from the sounds of it, very comparable to Wbar.

Here's [a blog I wrote about Cairo]("http://davestechsupport.com/blog/2008/04/10/make_ubuntu_look_like_mac_osx/"), which includes install instructions, a video and several screenshots of the different themes.

---

### Post by LightB on 2008-06-08
Cairo dock is still dependent on compiz though, wbar isn't.

---

### Post by rtom on 2008-08-06
I have an Ubuntu minimal install with openbox, wanted to try wbar. Downloaded and installed the .deb package from getdeb.net, but when I type ```
wbar -above-desk 
``` then the answer is 
***** Imlib2 Developer Warning ***** :
This program is calling the Imlib call:

imlib_free_image();

With the parameter:

image

being NULL. Please fix your program.
firefox -> Couldn't load font.

I guess I should remove firefox's font from the config file, but how to correct the image beeing null problem?

---

### Post by kirsis on 2008-08-06
> **rtom said:**
> I have an Ubuntu minimal install with openbox, wanted to try wbar. Downloaded and installed the .deb package from getdeb.net, but when I type ```
wbar -above-desk 
``` then the answer is 
***** Imlib2 Developer Warning ***** :
This program is calling the Imlib call:

imlib_free_image();

With the parameter:

image

being NULL. Please fix your program.
firefox -> Couldn't load font.

I guess I should remove firefox's font from the config file, but how to correct the image beeing null problem?

I had the same error. It went away when I removed any references to fonts from the config file.

Shame the dock's not in active development anymore.

---

### Post by rtom on 2008-08-06
> **kirsis said:**
> I had the same error. It went away when I removed any references to fonts from the config file.

Yes, I could also rule this problem by editing the config file.

Thanks!

---

### Post by starcannon on 2008-08-11
First off be sure to look at:
```
wbar --help
```
its got all the options listed there

Heres the line I use to open mine, look at the screen shot below:
```
 wbar -above-desk -pos bottom -isize 60 -nanim 1 -bpress -jumpf 0.0 -zoomf 1.5
```
note that if you want the "wave" effect just increase the -nanim value, I like the icons to just pop up so I don't use it, with 9 icons 5 is a nice "wave" effect.

Heres my .wbar file, use it to create your own or copy paste it and save to ~/.wbar, note the paths are all absolute, do that and your font and image problems are solved:
```

## Key
# i: location of the icon
# c: command to be run
# t: text to be displayed under your icon
## End Key

# The Bar && Font
i: /usr/share/wbar/iconpack/wbar.osx/osxbarback.png
t: /usr/share/wbar/iconpack/wbar.osx/font/12
c:
# End Bar && Font
i: /usr/share/wbar/iconpack/wbar.osx/nautilus.png
c: nautilus --no-desktop --browser
t: nautilus

i: /usr/share/pixmaps/gnome-terminal.png
c: gnome-terminal
t: terminal

i: /usr/share/wbar/iconpack/wbar.osx/firefox.png
c: firefox
t: firefox

#i: /usr/share/wbar/iconpack/wbar.osx/thunderbird.png
#c: thunderbird
#t: thunderbird

i: /usr/share/wbar/iconpack/wbar.osx/skype.png
c: skype
t: skype

#i: /usr/share/wbar/iconpack/wbar.osx/psi.png
#c: pidgin
#t: pidgin

i: /usr/share/wbar/iconpack/wbar.osx/ooffice.png
c: soffice
t: ooffice

#i: /usr/share/wbar/iconpack/wbar.osx/beagle.png
#c: beagle-search
#t: beagle

i: /usr/share/wbar/iconpack/wbar.osx/gimp.png
c: gimp
t: gimp

i: /usr/share/wbar/iconpack/wbar.osx/picasa.png
c: picasa
t: picasa

i: /usr/share/wbar/iconpack/wbar.osx/xmms.png
c: audacious
t: audacious

i: /home/tinman/games/ut2004/ut2004.xpm
c: aoss /home/tinman/games/ut2004/ut2004
t: Unreal Tournament 2004

i: /usr/share/wbar/iconpack/wbar.osx/nautilus.png
c: nautilus --no-desktop --browser --no-default-window /home/tinman/Desktop/.MyDesktopJunk/Top*500*Rock*And*Roll*Songs
t: Music

```

---

### Post by aktiwers on 2008-08-20
How can I make it stay "always on top" ?

The above-desk seams to work only for the desktop and other apps like Firefox ect..  Anyway to do this?

 I want it to be "always on top"

---

### Post by aktiwers on 2008-08-20
I just found this
[http://www.cypherbios.org/blog/?p=43&language=en](http://www.cypherbios.org/blog/?p=43&language=en)

Howto run awn avant without compiz

---

### Post by mishathegoat on 2008-09-03
Wbar is by far the best dock that I have used in linux. It does not require compiz or beryl or any stupid junk. It runs very smoothly and fluently. I would not recommend any other.

---

### Post by aktiwers on 2008-09-03
Like I posted above Avant AWN does not *require compiz like that..  it runs very smooth and nice here without, if you follow the instructions I posted in the link above. I would say Wbar is indeed a nice lightweight launcher app, but if you want a *real* dock you might be better off with Awn.

** Stars does not always mean something

---

### Post by agntsmyth on 2008-09-03
I dl'd wbar 1.3.3 and extracted then I used make command and got lots of errors, can anyone tell me what im doing wrong?

nate@frisk-dingonix:~/wbar-1.3.3$ make
g++ `imlib2-config --cflags` -Wall -O2    -c -o XWin.o XWin.cc
/bin/sh: imlib2-config: not found
XWin.cc:2:23: error: X11/Xutil.h: No such file or directory
XWin.cc:3:23: error: X11/Xatom.h: No such file or directory
In file included from XWin.cc:4:
XWin.h:5:22: error: X11/Xlib.h: No such file or directory
In file included from XWin.cc:4:
XWin.h:13: error: ISO C++ forbids declaration of &#8216;Display&#8217; with no type
XWin.h:13: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
XWin.h:14: error: ISO C++ forbids declaration of &#8216;Visual&#8217; with no type
XWin.h:14: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
XWin.h:15: error: &#8216;Window&#8217; does not name a type
XWin.h:16: error: &#8216;Atom&#8217; does not name a type
XWin.h:17: error: &#8216;Colormap&#8217; does not name a type
XWin.h:36: error: &#8216;XEvent&#8217; has not been declared
XWin.h:41: error: ISO C++ forbids declaration of &#8216;Display&#8217; with no type
XWin.h:41: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
XWin.h:42: error: ISO C++ forbids declaration of &#8216;Visual&#8217; with no type
XWin.h:42: error: expected &#8216;;&#8217; before &#8216;*&#8217; token
XWin.h:43: error: &#8216;Window&#8217; does not name a type
XWin.h:44: error: &#8216;Colormap&#8217; does not name a type
XWin.h:49: error: &#8216;Bool&#8217; has not been declared
XWin.h:49: error: &#8216;True&#8217; was not declared in this scope
XWin.cc: In constructor &#8216;XWin::XWin(int, int, int, int)&#8217;:
XWin.cc:9: error: &#8216;NoEventMask&#8217; was not declared in this scope
XWin.cc:14: error: &#8216;display&#8217; was not declared in this scope
XWin.cc:14: error: &#8216;XOpenDisplay&#8217; was not declared in this scope
XWin.cc:17: error: &#8216;display&#8217; was not declared in this scope
XWin.cc:17: error: &#8216;DefaultScreen&#8217; was not declared in this scope
XWin.cc:18: error: &#8216;visual&#8217; was not declared in this scope
XWin.cc:18: error: &#8216;DefaultVisual&#8217; was not declared in this scope
XWin.cc:20: error: &#8216;colormap&#8217; was not declared in this scope
XWin.cc:20: error: &#8216;DefaultColormap&#8217; was not declared in this scope
XWin.cc:22: error: &#8216;DefaultDepth&#8217; was not declared in this scope
XWin.cc:24: error: &#8216;window&#8217; was not declared in this scope
XWin.cc:25: error: &#8216;DefaultRootWindow&#8217; was not declared in this scope
XWin.cc:25: error: &#8216;XCreateSimpleWindow&#8217; was not declared in this scope
XWin.cc:29: error: &#8216;delWindow&#8217; was not declared in this scope
XWin.cc:29: error: &#8216;XInternAtom&#8217; was not declared in this scope
XWin.cc:31: error: &#8216;window&#8217; was not declared in this scope
XWin.cc:31: error: &#8216;XSetWMProtocols&#8217; was not declared in this scope
XWin.cc:33: error: &#8216;XClassHint&#8217; was not declared in this scope
XWin.cc:33: error: expected `;' before &#8216;ch&#8217;
XWin.cc:34: error: &#8216;ch&#8217; was not declared in this scope
XWin.cc:34: error: &#8216;XSetClassHint&#8217; was not declared in this scope
XWin.cc: In destructor &#8216;XWin::~XWin()&#8217;:
XWin.cc:38: error: &#8216;display&#8217; was not declared in this scope
XWin.cc:38: error: &#8216;window&#8217; was not declared in this scope
XWin.cc:38: error: &#8216;XDestroyWindow&#8217; was not declared in this scope
XWin.cc:39: error: &#8216;XCloseDisplay&#8217; was not declared in this scope
XWin.cc: In member function &#8216;void XWin::selectInput(int)&#8217;:
XWin.cc:44: error: &#8216;display&#8217; was not declared in this scope
XWin.cc:44: error: &#8216;window&#8217; was not declared in this scope
XWin.cc:44: error: &#8216;XSelectInput&#8217; was not declared in this scope
XWin.cc: In member function &#8216;void XWin::lowerWindow()&#8217;:
XWin.cc:48: error: &#8216;display&#8217; was not declared in this scope
XWin.cc:48: error: &#8216;window&#8217; was not declared in this scope
XWin.cc:48: error: &#8216;XLowerWindow&#8217; was not declared in this scope
XWin.cc: In member function &#8216;void XWin::raiseWindow()&#8217;:
XWin.cc:52: error: &#8216;display&#8217; was not declared in this scope
XWin.cc:52: error: &#8216;window&#8217; was not declared in this scope
XWin.cc:52: error: &#8216;XRaiseWindow&#8217; was not declared in this scope
XWin.cc: In member function &#8216;void XWin::mapWindow()&#8217;:
XWin.cc:56: error: &#8216;display&#8217; was not declared in this scope
XWin.cc:56: error: &#8216;window&#8217; was not declared in this scope
XWin.cc:56: error: &#8216;XMapWindow&#8217; was not declared in this scope
XWin.cc: At global scope:
XWin.cc:59: error: &#8216;bool XWin::nextEvent&#8217; is not a static member of &#8216;class XWin&#8217;
XWin.cc:59: error: &#8216;XEvent&#8217; was not declared in this scope
XWin.cc:59: error: &#8216;ev&#8217; was not declared in this scope
XWin.cc:59: error: expected &#8216;,&#8217; or &#8216;;&#8217; before &#8216;{&#8217; token
make: *** [XWin.o] Error 1
nate@frisk-dingonix:~/wbar-1.3.3$ 

I have no idea what to make of all this.

---

### Post by jimmah6786 on 2008-09-08
Did you install libimlib2-dev?

---

### Post by Harii on 2008-10-04
Tablaunch has auto-hide and looks much like wbar.
You can just use tabs with text as well-- if icons is not your thing.

---

### Post by ThaRabbit on 2008-10-23
> **agntsmyth said:**
> I dl'd wbar 1.3.3 and extracted then I used make command and got lots of errors, can anyone tell me what im doing wrong?

nate@frisk-dingonix:~/wbar-1.3.3$ make
g++ `imlib2-config --cflags` -Wall -O2    -c -o XWin.o XWin.cc
/bin/sh: imlib2-config: not found
XWin.cc:2:23: error: X11/Xutil.h: No such file or directory
XWin.cc:3:23: error: X11/Xatom.h: No such file or directory
In file included from XWin.cc:4:
XWin.h:5:22: error: X11/Xlib.h: No such file or directory
In file included from XWin.cc:4:
XWin.h:13: error: ISO C++ forbids declaration of ‘Display’ with no type
XWin.h:13: error: expected ‘;’ before ‘*’ token
XWin.h:14: error: ISO C++ forbids declaration of ‘Visual’ with no type
XWin.h:14: error: expected ‘;’ before ‘*’ token
XWin.h:15: error: ‘Window’ does not name a type
XWin.h:16: error: ‘Atom’ does not name a type
XWin.h:17: error: ‘Colormap’ does not name a type
XWin.h:36: error: ‘XEvent’ has not been declared
XWin.h:41: error: ISO C++ forbids declaration of ‘Display’ with no type
XWin.h:41: error: expected ‘;’ before ‘*’ token
XWin.h:42: error: ISO C++ forbids declaration of ‘Visual’ with no type
XWin.h:42: error: expected ‘;’ before ‘*’ token
XWin.h:43: error: ‘Window’ does not name a type
XWin.h:44: error: ‘Colormap’ does not name a type
XWin.h:49: error: ‘Bool’ has not been declared
XWin.h:49: error: ‘True’ was not declared in this scope
XWin.cc: In constructor ‘XWin::XWin(int, int, int, int)’:
XWin.cc:9: error: ‘NoEventMask’ was not declared in this scope
XWin.cc:14: error: ‘display’ was not declared in this scope
XWin.cc:14: error: ‘XOpenDisplay’ was not declared in this scope
XWin.cc:17: error: ‘display’ was not declared in this scope
XWin.cc:17: error: ‘DefaultScreen’ was not declared in this scope
XWin.cc:18: error: ‘visual’ was not declared in this scope
XWin.cc:18: error: ‘DefaultVisual’ was not declared in this scope
XWin.cc:20: error: ‘colormap’ was not declared in this scope
XWin.cc:20: error: ‘DefaultColormap’ was not declared in this scope
XWin.cc:22: error: ‘DefaultDepth’ was not declared in this scope
XWin.cc:24: error: ‘window’ was not declared in this scope
XWin.cc:25: error: ‘DefaultRootWindow’ was not declared in this scope
XWin.cc:25: error: ‘XCreateSimpleWindow’ was not declared in this scope
XWin.cc:29: error: ‘delWindow’ was not declared in this scope
XWin.cc:29: error: ‘XInternAtom’ was not declared in this scope
XWin.cc:31: error: ‘window’ was not declared in this scope
XWin.cc:31: error: ‘XSetWMProtocols’ was not declared in this scope
XWin.cc:33: error: ‘XClassHint’ was not declared in this scope
XWin.cc:33: error: expected `;' before ‘ch’
XWin.cc:34: error: ‘ch’ was not declared in this scope
XWin.cc:34: error: ‘XSetClassHint’ was not declared in this scope
XWin.cc: In destructor ‘XWin::~XWin()’:
XWin.cc:38: error: ‘display’ was not declared in this scope
XWin.cc:38: error: ‘window’ was not declared in this scope
XWin.cc:38: error: ‘XDestroyWindow’ was not declared in this scope
XWin.cc:39: error: ‘XCloseDisplay’ was not declared in this scope
XWin.cc: In member function ‘void XWin::selectInput(int)’:
XWin.cc:44: error: ‘display’ was not declared in this scope
XWin.cc:44: error: ‘window’ was not declared in this scope
XWin.cc:44: error: ‘XSelectInput’ was not declared in this scope
XWin.cc: In member function ‘void XWin::lowerWindow()’:
XWin.cc:48: error: ‘display’ was not declared in this scope
XWin.cc:48: error: ‘window’ was not declared in this scope
XWin.cc:48: error: ‘XLowerWindow’ was not declared in this scope
XWin.cc: In member function ‘void XWin::raiseWindow()’:
XWin.cc:52: error: ‘display’ was not declared in this scope
XWin.cc:52: error: ‘window’ was not declared in this scope
XWin.cc:52: error: ‘XRaiseWindow’ was not declared in this scope
XWin.cc: In member function ‘void XWin::mapWindow()’:
XWin.cc:56: error: ‘display’ was not declared in this scope
XWin.cc:56: error: ‘window’ was not declared in this scope
XWin.cc:56: error: ‘XMapWindow’ was not declared in this scope
XWin.cc: At global scope:
XWin.cc:59: error: ‘bool XWin::nextEvent’ is not a static member of ‘class XWin’
XWin.cc:59: error: ‘XEvent’ was not declared in this scope
XWin.cc:59: error: ‘ev’ was not declared in this scope
XWin.cc:59: error: expected ‘,’ or ‘;’ before ‘{’ token
make: *** [XWin.o] Error 1
nate@frisk-dingonix:~/wbar-1.3.3$ 

I have no idea what to make of all this.

Simply download the .deb :)

[http://code.google.com/p/wbar/downloads/list](http://code.google.com/p/wbar/downloads/list)

---

### Post by beameup on 2009-03-01
Nice write up here on setting up WBar

[http://www.deviceguru.com/adding-wbar-prism-and-gadgets-to-ubuntu/](http://www.deviceguru.com/adding-wbar-prism-and-gadgets-to-ubuntu/)

Got me to get off my butt and try LOL. 
I didn't do the Prism and Google stuff, just set it up with a few apps I have.

Used the wbar_conf to set it up but I found another called wbar_util that will actually do the startup script for you.

[http://linux.softpedia.com/get/Utilities/wbar-util-36331.shtml](http://linux.softpedia.com/get/Utilities/wbar-util-36331.shtml)

---

### Post by Tim.Baron on 2009-09-13
I know that this is an ancient thread, but wanted to chime in here, I am an avid user of wbar. I used it when I first started linux on ubunut, I used it with opensuse, and I now use it with my arch/fluxbox setup. People are commenting that it doesent match up to the apple dock, or that it doesent do this or that. The thing about wbar is that it does what its supposed to do, and it does it very well, its a quick launch dock. No matter what distro or type of hardware, wbar has ALWAYS been quick and smooth for me, I have never had a problem with it. 

I wanted a panel on my desktop that had centraly located quick launch icons, I wanted it to be painless to install and configure, and I REQUIRED that it was low on resources. Wbar delevers on all these things plus the added bonus that it adds hover over eye-candy.

---

### Post by pwnst*r on 2009-09-13
thanks for the advert

---

### Post by sertse on 2009-09-13
But wbar is *awesome*, and did you know it'll back into the official repos for karmic? Someone decided to maintain it :D So it is apt it was bumped.

---

### Post by hanzomon4 on 2009-09-14
gnome-do's docky is much better, it's better then the OSX dock

---

### Post by fabounet on 2009-09-15
you've probably never tried the real OSX dock to say such thing ...

---

