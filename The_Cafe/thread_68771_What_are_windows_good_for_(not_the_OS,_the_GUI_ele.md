---
title: "What are windows good for? (not the OS, the GUI elements!)"
date: 2005-09-24
forum: The Cafe
---

### Post by Kvark on 2005-09-24
I don't understand the point in windows and have not been able to find a discussion that explains why windows are so popular in all graphical user environments.

After opening a Firefox, Nautilus, Open Office or [insert any other application] window I instinctively maximize it to emulate full screen and would perfer real full screen. But with the panels still visible. So just removing the titlebar and borders around the window and making maximized default would do the trick. It just seems like a waste of screen space and occationally uneccessary scrolling to not use the whole screen.

The only time I use non-maximized windows is when looking at a program other then the one I'm working with. In these situations I'm just trying to emulate split screen between two programs and would perfer real split screen over moving around and resizing windows until they fit half the screen each. For example reading from Firefox on the left half of the screen and typing in Open Office on the right half of the screen.

The small dialog pop-ups like the usual "are you sure?"-question is an exception of course since they belong to a bigger mother window and are simply too small and temparary to be full screen.

Why are windows so extreamly popular? Why not use the whole screen (minus the space panels use) or sometimes split screen?

---

### Post by Leif on 2005-09-24
I agree that some things starting up maximised might be a good idea, but not necessarily everything. I wouldn't like a maximised terminal, or file browser, or gaim, skype, because these are usually secondary programs, and I can keep an eye on whatever it is that I'm doing in the background. When I'm done with them, I don't have to fish around for firefox/oo/kile/eclipse in the taskbar to focus, I click on the majority of the screen.

---

### Post by PatrickMay16 on 2005-09-24
The idea you propose was used in the first version of windows, I think.
[http://toastytech.com/guis/win101.html](http://toastytech.com/guis/win101.html)
Though maybe I don't entirely understand what you meant.

Anyway, I think windows are an efficient way of managing things. Most work doesn't require a great amount of screen space anyway, and large monitors are getting cheaper.

---

### Post by zenwhen on 2005-09-24
I hate anything maximized. I work with a lot of applications and have to see part of them at all times. I have a lot of screen space. It doesn't hurt me to have windows of various sizes. I suppose it is all a matter of opinion. 

The answer to your question is simply that Windows exist in most desktop environments because most people like them.  It makes things easier for most people when dealing with multiple applications. You would probably like a window manager like [Ratpoison](http://www.nongnu.org/ratpoison/), which would give you almost exactly what you want.

---

### Post by Wolki on 2005-09-24
[QUOTE=Kvark]After opening a Firefox, Nautilus, Open Office or [insert any other application] window I instinctively maximize it to emulate full screen and would perfer real full screen.[/quote]

See, I don't. I rarely maximize, my windows are usually as big as they need to be and not bigger. I like having several windows (and a part of the desktop :) ) visible, so i can easily switch to another window if i still see it - No need to alt-tab through lots of windows or read the taskbar.

I think you can configure your gnome with devilspie to maximize everything you want.

---

### Post by papangul on 2005-09-24
What are the screen sizes of Kvark and Wolki? That might explain the differences in personal preferences.

---

### Post by Wolki on 2005-09-24
[QUOTE=papangul]What are the screen sizes of Kvark and Wolki? That might explain the differences in personal preferences.[/QUOTE]

1024x768 on a 17" here. It's the only resolution my monitor will do with a decent refresh rate... the thing's over 5 years old o_O

---

### Post by bsussman on 2005-09-24
[QUOTE=Kvark]I instinctively maximize it ...[/QUOTE]

You work in a linear fashion.

Not everybody does.

I work @1600x1200 on a 17" monitor and use 6 desktops to compartmentalize things.  I couldn't function with only 1 open window.  I do not even use the shade function, though it is a neat idea.

---

### Post by doclivingston on 2005-09-24
[QUOTE=Kvark]After opening a Firefox, Nautilus, Open Office or [insert any other application] window I instinctively maximize it to emulate full screen and would perfer real full screen. But with the panels still visible. So just removing the titlebar and borders around the window and making maximized default would do the trick. It just seems like a waste of screen space and occationally uneccessary scrolling to not use the whole screen.[/QUOTE]

Have you looked at "Toggle Fullscreen Mode", under Window Management, in the Keyboard Shortcuts preferences? (assuming that you are using Gnome). Using that you can have a keybinding that makes a window go into real fullscreen.

---

### Post by Kvark on 2005-09-24
[QUOTE=papangul]What are the screen sizes of Kvark and Wolki? That might explain the differences in personal preferences.[/QUOTE]
1024x768 on a 17" here, exactly the same as Wolki. And I have the same habits on bigger and smaller screens. So that doesn't seem to explain it.

Several replies say that the easiest way to switch between programs is to click on the windows. While I perfer the keyboard including alt-tab over the mouse unless I already have a hand on the mouse. Add that I often have so many windows open that some of them would be covered or in another workspace even if nothing was maximized so I end up at the taskbar or workspace switcher in either case when using the mouse. Perhaps this could be one of the things I missed about windows.

Yes doclivingston, I have toggle full screen on the left Windows button, but it hides panels.

Thanks for the tips PatrickMay16 and zenwhen. Now I want to try Windows 1 and maybe even use Ratpoison.

---

### Post by Wolki on 2005-09-24
[QUOTE=Kvark]
After opening a Firefox, Nautilus, Open Office or [insert any other application] window I instinctively maximize it to emulate full screen and would perfer real full screen. But with the panels still visible. So just removing the titlebar and borders around the window and making maximized default would do the trick. It just seems like a waste of screen space and occationally uneccessary scrolling to not use the whole screen.[/QUOTE]


OK Kvark, i played around a little. here's how to do it in Gnome:

1) Install devilspie from synaptic
2) Save the following as ~/.devilspie.xml
```
<?xml version="1.0"?>
<!DOCTYPE devilspie SYSTEM "devilspie.dtd">
<devilspie>
  <flurb>
    <matchers>
      <matcher name="DevilsPieMatcherWindowName">
        <property name="window-title" value=".*"/>
      </matcher>
    </matchers>
    <actions>
      <action name="DevilsPieActionResize">
        <property name="maximized" value="TRUE"/>
      </action>
    </actions>
  </flurb>
  
  <flurb>
    <matchers>
      <matcher name="DevilsPieMatcherWindowName">
        <property name="window-title" value=".*"/>
      </matcher>
    </matchers>
    <actions>
      <action name="DevilsPieActionDecorate">
        <property name="decorated" value="FALSE"/>
      </action>
    </actions>
  </flurb>
</devilspie>
```
4) Start devilspie with Alt-F2 or Terminal
3) Add devilspie to your Session startup if you like it.

It will automatically maximize all your windows (except dialogs) and display them without title bar or borders.

---

### Post by drizek on 2005-09-24
i have 1400x1050 on a 19" and i hardly ever maximize a window.

---

### Post by Kvark on 2005-09-24
[QUOTE=Wolki]OK Kvark, i played around a little. here's how to do it in Gnome:

...instructions...

It will automatically maximize all your windows (except dialogs) and display them without title bar or borders.[/QUOTE]
Tried it on a pretty standard Hoary setup. It doesn't work and says this when a window is opened:
```
(devilspie:13917): Wnck-WARNING **: Received a timestamp of 0; window activation may not function properly.

fullscreen
devilspie: relocation error: devilspie: undefined symbol: _wnck_atom_get
```

---

### Post by Wolki on 2005-09-24
[QUOTE=Kvark]Tried it on a pretty standard Hoary setup. It doesn't work and says this when a window is opened:
```
(devilspie:13917): Wnck-WARNING **: Received a timestamp of 0; window activation may not function properly.

fullscreen
devilspie: relocation error: devilspie: undefined symbol: _wnck_atom_get
```[/QUOTE]

Hm... don't know what's wrong and I'm currently a little low on time... Maybe it has to do  with the new version in Breezy? Can someone else using breezy check if this works?

I'll take a closer look at it tomorrow.

---

### Post by GeneralZod on 2005-09-24
I have a 17" 1600x1200 setup and maximise almost every app I use - it's simply never really occurred to me to do otherwise :) Amazing how different people can be!

---

### Post by John Nilsson on 2005-09-24
For a non overlaping WM I have grown quite fond of [ION](http://modeemi.cs.tut.fi/~tuomov/ion/). The only problem is that it takes some configuration and usage time before it becomes comforatble.

I have noticed that my productivity is at a peak when I work in ION compared to when I  work in GNOME.

Another project I havn't given the time to learn is [WMI](http://wmi.modprobe.de/). It seems like an improvment upon ION... I shall give it another try. =)

I agree with the OP that windows can't be that good. Would tabbed browsing ever been so popular if windows was so good? Take a look at an IDE like Eclipe. There isn't an overlapping windows in sight. Instead panes are the container of choice...

On another note, I recently got a WUXGA monitor. It's the first time I've been confotable with non maximized windows. Actually maximized windows just feels silly now. To be able to DnD between an open window and the desktop is quite nice. I wonder how I would implement that in a paned environment like Eclipse...

---

### Post by doclivingston on 2005-09-24
I tend to use maximised windows for most things on Linux, because I usually have one application per workspace. On other OSs I don't use maximised windows, especially on  a Mac.

---

### Post by poofyhairguy on 2005-09-24
Ever played with ION?

[http://modeemi.cs.tut.fi/~tuomov/ion/](http://modeemi.cs.tut.fi/~tuomov/ion/)

---

### Post by Lux Perpetua on 2005-09-24
You seem to be looking for something like ION or wmii. I emphasize "something like" because I can't recommend those window managers on their merits (yet?). Their concept is right, but neither has really addressed the problem of usability. The idea is that the user shouldn't have to waste time managing windows, but with those, I usually end up spending even more time messing around with the 'windows' (largely due to lack of good documentation, which is essential for a keyboard-based interface). Give them a try anyway, though; YMMV.

---

### Post by UbuWu on 2005-09-24
You might be interested in [Exigo](http://exigo.distrotalk.net/index.php)

---

### Post by gord on 2005-09-24
i think the main reason the whole world uses 'windows' as a gui system is because of HCI, or Human Computer Interaction. tis a very important thing. you have to immagen what desktop systems were created for... being on top of desks, so people can work on them. when you sit at a desk without a computer, chances are you'll have a whole load of paper spread all over the place that you can put wherever. thus, windows were created to emulate what people like to use :)

most every day computer terms were brought about in the same way, files, folders.. still no half broken coffee machine that makes the worst coffee imaginable though... 

you could also say that multi-tasking was started to be used in a proper way and people wanted to show off though ;) 


i personally like maximised windows combined with multiple workspaces, unless im coding and need more than one thing for debugging or whatever.

---

### Post by darkmatter on 2005-09-24
I think something similar to this [[IMG]http://img383.imageshack.us/img383/6269/30959gn.th.jpg[/IMG]](http://img383.imageshack.us/my.php?image=30959gn.jpg)samurize config for Windows would make an interesting alternative to a traditional windowing systems. ;-)

---

### Post by John Nilsson on 2005-09-24
[QUOTE=gord]i think the main reason the whole world uses 'windows' as a gui system is because of HCI, or Human Computer Interaction. tis a very important thing. you have to immagen what desktop systems were created for... being on top of desks, so people can work on them. when you sit at a desk without a computer, chances are you'll have a whole load of paper spread all over the place that you can put wherever. thus, windows were created to emulate what people like to use :)

most every day computer terms were brought about in the same way, files, folders.. still no half broken coffee machine that makes the worst coffee imaginable though... 

you could also say that multi-tasking was started to be used in a proper way and people wanted to show off though ;) 


i personally like maximised windows combined with multiple workspaces, unless im coding and need more than one thing for debugging or whatever.[/QUOTE]

I've never seen a window on top of anybodys desk.

I dont think you have really understood what we are talking about.

Windows are elements in the [WIMP](http://en.wikipedia.org/wiki/WIMP_%28computing%29) paradigm
WIMP is not the same thing as [GUI](http://en.wikipedia.org/wiki/Graphical_user_interface)  a GUI can be composed of any kind of elements.
[HCI](http://en.wikipedia.org/wiki/Human-computer_interaction) does not imply a GUI. The buttons on a simple calculator is a HCI element.

Windows as GUI elements means, potentially overlaping squares whith possibly scrollable content inside.

I've got the feeling that the OP wasn't only questioning the use of windows but actually the usefullness of the whole WIMP paradigm.

To see a radicly diffrent paradigm take a look at [Archy](http://rchi.raskincenter.org/aboutrchi/index.php).

---

### Post by Wolki on 2005-09-26
[QUOTE=Kvark]Tried it on a pretty standard Hoary setup. It doesn't work and says this when a window is opened:
```
(devilspie:13917): Wnck-WARNING **: Received a timestamp of 0; window activation may not function properly.

fullscreen
devilspie: relocation error: devilspie: undefined symbol: _wnck_atom_get
```[/QUOTE]

OK, I see hoary still has devilspie 0.7. According to the [devilspie web page]("http://www.burtonini.com/blog/computers/devilspie"), 0.10 is required for gnome 2.10 and it has several bugfixes concerning the wnck-functions. You'll probably need the new version to get the wanted functionality. I suggest either waiting a few weeks for breezy, upgrading now or asking for a backport. :)

---

