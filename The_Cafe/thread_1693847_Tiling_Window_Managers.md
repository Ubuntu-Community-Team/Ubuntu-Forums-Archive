---
title: "Tiling Window Managers"
date: 2011-02-23
forum: The Cafe
---

### Post by BrokenKingpin on 2011-02-23
I have never used a tiling window manager, but am interested in trying one out. What is the best tiling window manager out there (in your opinion), or one you recommend starting with? Thanks!

---

### Post by gutterslob on 2011-02-23
If you started this thread looking for a definitive answer, you're going to be a tad disappointed.

Short answer: There is no 'best' tiling window manager.

Here's a brief comparo;
[https://wiki.archlinux.org/index.php/Comparison_of_Tiling_Window_Managers](https://wiki.archlinux.org/index.php/Comparison_of_Tiling_Window_Managers)

They all have their pros, cons, quirks and idiosyncrasies.
Some might be easier to configure than others, but may suffer from reduced modularity as a result. Some are highly configurable, but may require a bit of familiarity with a certain programming language, or might require a lot of dependencies. Some are just awful and tend to break their syntax with every version change. Some can be scripted/configured in any language you want, but might suffer from instability every now and then. Some are just too tedious to take seriously. Some are just crap.

---

### Post by Spice Weasel on 2011-02-23
AwesomeWM, WMii, DWM, Ratpoison, ion3 are some of the more popular ones.

---

### Post by ilovelinux33467 on 2011-02-23
Xmonad is another good one.

---

### Post by BrokenKingpin on 2011-02-23
> **gutterslob said:**
> If you started this thread looking for a definitive answer, you're going to be a tad disappointed.


I am just trying to get an idea of the more popular ones as a place to start.

---

### Post by urukrama on 2011-02-23
Awesome is a good one to start with.

---

### Post by tjwoosta on 2011-02-23
I started with Awesome. It was great, but back then they would change the configuration syntax with just about every update requiring me to rewrite my config every time. This was a couple years ago so I have no idea if its still relevant.

After a while I tried xmonad, dwm, and eventually wmii where I fell in love with its manual method of tiling. Ive been using wmii for well over a year now and am very happy with it. I dont see myself switching agian any time soon.

Basically it all comes down to personal preference. Try out a few of them and dont be afraid to give it some time to see how you adjust.

---

### Post by beastrace91 on 2011-02-23
I use Enlightenment with tiling daily. Works well.

~Jeff

---

### Post by aaaantoine on 2011-02-23
KDE 4.5+ also offers a tiling mode, as seen here:
[http://www.youtube.com/watch?v=faOQAgapQYQ](http://www.youtube.com/watch?v=faOQAgapQYQ)

Looks like a lot of space is wasted on the window decorations though.

---

### Post by beastrace91 on 2011-02-23
> **aaaantoine said:**
> 
Looks like a lot of space is wasted on the window decorations though.

Lots of things are wasted in KDE 4.x - why not add a little screen space?

~Jeff

---

### Post by BrokenKingpin on 2011-02-25
Has anyone tried Bluetile? It is a WM that is suppose to integrate well with Gnome. Or does anyone know of any other tiling window managers that integrate well with Gnome or XFCE?

I would like the full desktop experience as well as a tiling window manager. As mentioned above, KDE now has tiling support, but I really don't like using KDE.

---

### Post by aeiah on 2011-02-25
> **BrokenKingpin said:**
> Has anyone tried Bluetile? It is a WM that is suppose to integrate well with Gnome. Or does anyone know of any other tiling window managers that integrate well with Gnome of XFCE?

I would like the full desktop experience as well as a tiling window manager. As mentioned above, KDE now has tiling support, but I really don't like using KDE.

i believe xmonad works well with gnome, and pytile mayyy work with xfce, but id check if i were you.

i used to use awesomewm, which is pretty easy to get the hang of but ive gone back to using openbox with some custom placement shortcuts that work like the compiz grid. i realised i rarely have that many things to look at all at once and its much more convenient to have shortcut keys to resize to 100,50 or 25% of the screen and stick it against a corner or edge.


another one to consider is scrotwm, which also allows you to combine windows together and access them with tabs a la pekwm.

---

### Post by urukrama on 2011-02-26
> **aeiah said:**
> ive gone back to using openbox with some custom placement shortcuts that work like the compiz grid. i realised i rarely have that many things to look at all at once and its much more convenient to have shortcut keys to resize to 100,50 or 25% of the screen and stick it against a corner or edge.

Could you elaborate (here or in a pm)? I'm not entirely sure what you mean, but it sounds interesting.

---

### Post by meow9th on 2011-02-26
Does anyone know of a window manager with Eclipse-like tiling? In Eclipse (an MDI app), any tab (called 'view' in Eclipse) can be dragged to any container in the screen. If you drop the tab on top of the container, the tab is stacked with the other tabs in the container. If you drag the tab to an edge of the container, a new container is created, tiling the old container. (Eg, if you drag to the left side of a container, the old container is split vertically and you have two new containers, vertically tiled, with the new one on the left.) Empty containers collapse. A given configuration of tabs (not just their location, but what is open and not open) can be saved as a 'perspective'.

I find this tiling behaviour dynamic, flexible and intuitive. Are there comparable window managers?

---

### Post by jerenept on 2011-02-26
> **BrokenKingpin said:**
> Has anyone tried Bluetile? It is a WM that is suppose to integrate well with Gnome. Or does anyone know of any other tiling window managers that integrate well with Gnome of XFCE?

I would like the full desktop experience as well as a tiling window manager. As mentioned above, KDE now has tiling support, but I really don't like using KDE.

Have you used a KDE distro other than KUbuntu? you may be pleasantly surprised by OpenSUSE or Sabayon.

---

### Post by BrokenKingpin on 2011-03-01
> **jerenept said:**
> Have you used a KDE distro other than KUbuntu? you may be pleasantly surprised by OpenSUSE or Sabayon.
Yes, both actually. OpenSUSE was just too bloated for me. Sabayon was nice and I generally liked what they have done, but too many bugs with things like package management. I really prefer a debian/ubuntu based distro. I have though about doing a debian barebones install and trying KDE on top of that, and configure it myself without all the extra bloat.

If XFCE has tiling support I would be in heaven, but from most of my searching it is a huge pain to get anything working.

---

### Post by Ant. on 2011-03-01
> **BrokenKingpin said:**
> I have never used a tiling window manager, but am interested in trying one out. What is the best tiling window manager out there (in your opinion), or one you recommend starting with? Thanks!

Well I started out with Xmonad, but for the sake of trying and learning new things, I also gave Awesome and DWM a try. To be honest I didn't find any one superior over the other, but ended up going back to Xmonad due to familiarity.

I think the main thing is to just start using a TWM, because once I started, floating windows just seemed so inefficient to me, couldn't believe I had gone so long dragging, resizing and maximising windows.

> **ilovelinux33467 said:**
> Xmonad is another good one.

+1 for Xmonad :)

> **BrokenKingpin said:**
> ...Or does anyone know of any other tiling window managers that integrate well with Gnome...

For a while I was using Xmonad with xmobar and dmenu, then I was using it with dzen and conky. While it worked nicely with the way I customised it, I still missed some of the basic Gnome functionality and applets, so decided to go down this route - I have Xmonad working as the Window Manager inside Gnome. It wasn't too hard to get working, but took me a while to customise it how I wanted it to work. 

A lot of the methods on the Haskell wiki such as an xmonad.desktop file, or a modified .xsession didn't work properly for me, and I found that making the default Window manager as Xmonad instead of metacity through Gconf editor done the trick.

Once I had Xmonad running successfully inside Gnome, the next thing I wanted to do was replace the window list selector that sits in the panel, with something that works similar to xmobar. Through google'ing I stumbled upon the [Xmonad log applet](http://uhsure.com/xmonad-log-applet.html). It was kind of tricky to get set up (for me anyway :P) but once I did I was pleased with the result.

The final thing was getting Gnome-Do to work with Xmonad nicely. This is as simple as adding the line:
```
managementHooks :: [ManageHook]
managementHooks = [
    resource  =? "Do"        --> doIgnore
]
```

To your xmonad.hs file, so that xmonad doesn't treat Gnome-Do as a tiled window (the results are horrible :P). Apparently according to google searches this isn't the "best" way of getting Do to work nicely, but it works fine for me. And to use different skins in Do you need compositing, but you can't enable compiz and Xmonad at the same time, so I installed and use xcompmgr instead, so I the glass Do theme fits in nicely with my desktop.

And I am pleased with the final result and Xmonad works inside Gnome :)
[http://img140.imageshack.us/img140/443/2141clean.png](http://img140.imageshack.us/img140/443/2141clean.png)
[http://img140.imageshack.us/img140/8120/2672dirty.png](http://img140.imageshack.us/img140/8120/2672dirty.png)

---

### Post by aeiah on 2011-03-03
> **urukrama said:**
> Could you elaborate (here or in a pm)? I'm not entirely sure what you mean, but it sounds interesting.

i was directed towards [subtle](http://subforge.org/projects/subtle) yesterday which does a similar thing (but in a very tiling wm kinda way), but i got the idea from compiz grid so i use the ctrl+alt modifiers for my shortcuts.

if you imagine your keypad as representative of a grid on your screen, Ctrl+Alt+kp_9 resizes my focused window to 50% height/width and places it in the top right:
[[img]http://ompldr.org/tN24xdA[/img]](http://ompldr.org/vN24xdA)

Ctrl+Alt+kp_3 , bottom right:
[[img]http://ompldr.org/tN24xcg[/img]](http://ompldr.org/vN24xcg)

Ctrl+Alt+kp_4, left 50% (full height)
[[img]http://ompldr.org/tN24xcw[/img]](http://ompldr.org/vN24xcw)

makes it very quick to arrange a maximum of 4 windows, without having tiling an inherent part of my desktop experience.
[[img]http://ompldr.org/tN24xcQ[/img]](http://ompldr.org/vN24xcQ)


both compiz grid plugin and subtle also allow for some kind of toggle resizing (first resize will be width 50%, then 33%, then 66%), but this isnt really available with openbox. its probably possible with some if/else statements in an external bash script though (wmctrl?).


these are the configs i use. my res is 1440x900 and ive allowed for 18px tint2 panel on the bottom and 20px window decorations. it takes some fiddling to get right :P

~/.config/openbox/rc.xml
[php]
    <keybind key="C-A-KP_6">
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>720</x>
        <y>0</y>
        <width>720</width>
        <height>860</height>
      </action>
    </keybind>
    <keybind key="C-A-KP_4">
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <width>720</width>
        <height>860</height>
      </action>
    </keybind>
    <keybind key="C-A-KP_8">
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <width>1440</width>
        <height>420</height>
      </action>
    </keybind>
    <keybind key="C-A-KP_2">
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>440</y>
        <width>1440</width>
        <height>420</height>
      </action>
    </keybind>
    <keybind key="C-A-KP_9">
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>720</x>
        <y>0</y>
        <width>720</width>
        <height>420</height>
      </action>
    </keybind>
    <keybind key="C-A-KP_3">
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>720</x>
        <y>440</y>
        <width>720</width>
        <height>420</height>
      </action>
    </keybind>
    <keybind key="C-A-KP_1">
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>440</y>
        <width>720</width>
        <height>420</height>
      </action>
    </keybind>
    <keybind key="C-A-KP_7">
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <width>720</width>
        <height>420</height>
      </action>
    </keybind>
    <keybind key="C-A-KP_5">
      <action name="ToggleMaximizeFull"/>
    </keybind>
[/php]

---

### Post by BrokenKingpin on 2011-03-03
> **Ant. said:**
> I have Xmonad working as the Window Manager inside Gnome. It wasn't too hard to get working, but took me a while to customise it how I wanted it to work. 

That looks awesome. I will have to give that a try. You should write up an official how to on this, I think a lot of people would be interested in that.

---

### Post by Ant. on 2011-03-04
> **BrokenKingpin said:**
> That looks awesome. I will have to give that a try. You should write up an official how to on this, I think a lot of people would be interested in that.

Maybe if there were demand, I would write something. However I am not the most competent with Ubuntu or Linux in general - I would still class myself as a beginner in any aspects of linux. The finished result I got was really a mixture of different tutorials I found through google searches.

If you do give it a try and need any help, I'll do my best. What are you interested in doing, fully integrating Xmonad (or another TWM) into Gnome like mine?

---

### Post by krapp on 2011-05-05
Anybody interested in writing a short defense of tiling? Why do you use it? How has it made you more productive, etc.?

---

### Post by tjwoosta on 2011-05-05
First and foremost tiling wm's are not for everyone and I would never recommend them to casual everyday users, so this isnt really a defense but more of a casual explanation of why I use them.

I use a tiling wm (wmii) because I love the keyboard. Everything about tiling wm's is designed around using key binds, whether its navigating windows and workspaces, or opening apps, or whatever, the mouse is secondary. On top of that every app that I use including my web browser (uzbl) is keyboard oriented, and most are cli. 

If your familiar with vim you probably understand where Im coming from. I navigate and utilize every app on my system without ever touching a mouse. Over time Ive built up a muscle memory of all the keys, so its second nature to me, just touch typing. And since I use vi navigation keys (h, j, k, and l) for everything, its all very quick and ergonomically sound, compared to reaching down to use the arrow keys.

This is more productive for me because I can speed through everything much quicker with key binds than I ever could moving a mouse around and clicking things, and resizing/moving windows, or whatever. Its basically just a much more efficient human to machine interface than a mouse/floating wm, at the sacrifice of having a longer learning curve.

If you use point/click apps for everything then tiling wm's dont really make sense becuase youd probably be switching back and fourth between the mouse and the keyboard even more so than you would just using a floating wm. It really just comes down to what type of user you are.

---

### Post by krapp on 2011-05-06
I wonder if replacing Metacity in Gnome 2.X with xmonad or dwm would be wise.

---

### Post by meow9th on 2011-05-06
I use tiling for a very different reason, but which is also specific to what I do and how I do it. I use tiling because it's the most efficient way for me to look at many windows at once (or with minimum cost in switching), which I often need to do as a student/research assistant. For example, when programming an assignment, I need to look at: IDE, help/documentation, lecture notes (often more than one document), web browser, and assignment write-up. I may also need to look at graphics or datasets, perhaps multiple of each.

Another example is graphic design: layout program + tool panes, graphics program (perhaps multiple instances) + tool panes, document previewer, calculator, web browser, etc.

There are just too many windows involved for me to arrange manually by clicking and dragging. Even with two monitors and tiling, I can't expose everything, but if I had only one monitor and no tiling, I would probably quit school.

When I'm 'casually' using my computer, I don't usually tile (... except when I need to compare 16 shoes at once). Tiling only becomes necessary when I'm using my computer 'seriously'.

---

### Post by krapp on 2011-05-06
> **meow9th said:**
> When I'm 'casually' using my computer, I don't usually tile (... except when I need to compare 16 shoes at once). Tiling only becomes necessary when I'm using my computer 'seriously'.

Do you switch between WMs or is there a tiling WM that does floating reasonably well?

---

### Post by meow9th on 2011-05-08
> **krapp said:**
> Do you switch between WMs or is there a tiling WM that does floating reasonably well?

I use the Compiz grid plugin instead of a real tiling WM. It was more user-friendly for me, and as you pointed out, has no odd side-effects on floating windows (since it's not a tiling WM).

When I was investigating tiling WMs, I know I came across more than one which handled floating windows in one way or another. I don't know about 'reasonably well', though.

---

### Post by Random_Dude on 2011-05-08
> **krapp said:**
> Do you switch between WMs or is there a tiling WM that does floating reasonably well?

Awesome WM does floating very well the only difference is that, since you don't have window decorations, you have to press and hold the super key on your keyboard while you drag (left mouse bottom) or resize (right mouse bottom).
I've tried different tilting window managers and awesome wm is by far my favourite. It has a taskbar, supports applets out-of-the box and the defaults are great. However, it is a pain to customize (if you don't know Lua), so I'm now back to floating window managers (trying Openbox for two weeks).

Cheers :cool:

---

### Post by krapp on 2011-05-08
> **Random_Dude said:**
> Awesome WM does floating very well the only difference is that, since you don't have window decorations, you have to press and hold the super key on your keyboard while you drag (left mouse bottom) or resize (right mouse bottom).
I've tried different tilting window managers and awesome wm is by far my favourite. It has a taskbar, supports applets out-of-the box and the defaults are great. However, it is a pain to customize (if you don't know Lua), so I'm now back to floating window managers (trying Openbox for two weeks).

Cheers :cool:

Thing is, I know little more than a handful of HTML tags so I'm a bit intimidated by the prospect editing config files and all that. Though I won't shy away from it before giving it a shot. I've been leaning in the direction of xmonad as it seems to be the most full featured in terms of multi-display support and stability but apparently its written in some esoteric language; dwm I find attractive because it's supposedly less than 2000 lines of code so if there's something to decipher I'll get it done sooner or later. And wmfs I understand from reading the Arch forums has configs legible to lay people as well.

---

### Post by Random_Dude on 2011-05-09
> **krapp said:**
> Thing is, I know little more than a handful of HTML tags so I'm a bit intimidated by the prospect editing config files and all that. Though I won't shy away from it before giving it a shot. I've been leaning in the direction of xmonad as it seems to be the most full featured in terms of multi-display support and stability but apparently its written in some esoteric language; dwm I find attractive because it's supposedly less than 2000 lines of code so if there's something to decipher I'll get it done sooner or later. And wmfs I understand from reading the Arch forums has configs legible to lay people as well.

If you intend to change the keybindings in awesome, it is fairly simple and you can deduce most of the stuff. However, if you want to change themes or edit the menu it might get a little more complicated.

But the fact that it supports applets out-of-the box is a huge plus for me. The defaults are very good and probably the only thing you might want to do is change a few keybinds and set some programs that you use to boot on startup (network manager, mail client, sound manager, etc.). With tilting window managers you'll always have to edit config files. So awesome might be the one for you since the defaults are pretty good (IMHO) and you won't have to do that much editing.

Cheers :cool:

---

