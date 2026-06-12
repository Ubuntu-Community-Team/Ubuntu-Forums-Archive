---
title: "most productive GUI?"
date: 2010-04-11
forum: The Cafe
---

### Post by cespinal on 2010-04-11
So, 

I am trying to find out which GUI/Desktop layout is best for cluttered workflow. We have panels, docks, compiz/kwin, plasmoids and screenlets... there are so many options out there its difficult to fin which selection of options suits a heavy workload layout best. 

Im currently opting for a single panel with taskbar. Window grouping is enabled and Expo and Scale (in KDE) enabled in the desktop corners. 

Im using 4 workspaces at the time. One of them, for office stuff is usually cluttered with 5 or more PDF docs, 2 or more spreadsheets and a file browser window. I sometimes find the task manager rather inefficient for this. Being alt+tab the best opcion for navigating through windows... 

What are your options on this?

---

### Post by HermanAB on 2010-04-11
Hmm, if any of those things make any difference to your productivity, then you are playing instead of working...
;)

I find that the only important thing is to have virtual desktops, since I'm always working on many different things at the same time and the virtual desktops help me to keep separate jobs separated.

---

### Post by cespinal on 2010-04-11
i do play sometimes :)

---

### Post by K.Mandla on 2010-04-11
This probably isn't what you want to hear, but in my opinion, the most *productive* desktop has been [no desktop at all]("http://kmandla.wordpress.com/2009/05/10/do-more-with-less/"). If you want to trim out distractions and actually get things done, then my suggestion would be to move to a CLI-only arrangement. 

But I say that to everything. :roll:

---

### Post by del_diablo on 2010-04-11
CLi can get way to barebone to get anything done.
Openbox + systray that minimizes when + some altering of the hetkeys will work.

---

### Post by SecretCode on 2010-04-11
Forget menus, desktop icons and docks for finding and launching apps: just use GNOME-Do or an equivalent.

For managing open app's windows, multiple workspaces are a must. Beyond that, it's up to you. Alt-tab is pretty limited. Taskbars are pretty limited. Expo / scale plugins in compiz can be handy.

---

### Post by Khakilang on 2010-04-11
Get 2 monitor in this way you can see what the other application is doing.

---

### Post by rottentree on 2010-04-11
Gnome Shell?

Maybe it isn't the fastest answer but for me it helps from an organization point of view so I can see where is what and I don't have to spend time finding it.

---

### Post by Sporkman on 2010-04-11
Besides multiple workspaces, I find that keeping launchers for my most commonly used apps in the panel are very handy. 95% of the time I'm using either the terminal. a text editor, or firefox, so with those launchers + multiple workspaces, when something comes up I just switch to an empty workspace, click a launcher or two & I'm in business.

---

### Post by chucky chuckaluck on 2010-04-11
> **cespinal said:**
> Im using 4 workspaces at the time. One of them, for office stuff is usually cluttered with 5 or more PDF docs, 2 or more spreadsheets and a file browser window. I sometimes find the task manager rather inefficient for this. Being alt+tab the best opcion for navigating through windows...

the middle click menu of open windows in openbox might work better if you have a bunch of stuff open on different workspaces. just set the margin on one side to 5, or 10 pixels (in order have room to middle click) and you're all set.

---

### Post by jpkotta on 2010-04-11
I use Fvwm, and I've come up with several tricks that I really miss when I'm using other window managers.  I'm not sure if it's possible to do some of these in other environments, but most of them probably are possible.

[LIST]
[*] Clicking in a window gives it focus but doesn't raise it.  This is great when I have a maximized window that I'm typing in, but I want to look at a smaller window while I'm typing.  Clicking on the titlebar or super-click (super is usually the "Windows key") will focus and raise.
[*] Clicking on the top edge of the screen is like clicking on the root window (the desktop).  Clicking on the root window gives me various menus, so all of my menus are easily accessible while at the same time I don't have a panel to steal screen real estate.
[*] Mouse wheel on the root window works like Alt-Tab.
[*] Lots of virtual desktops.  Multiple monitors if possible.
[*] Chained keybindings which are easy to remember.  For example, super-x c closes the current window, super-s w starts a new web browser window.
[*] One or two terminals (I've found that if the screen is big enough, two is much better) that are very easily hidden or shown.  These are used for random things like launching a not-so-frequently-used app.  It is so handy to have a (persistent) terminal one keystroke away.
[/LIST]

The best thing is to step back periodically and see things that you're repeating, and try to think of ways to make them faster or automated.  Then when you have some time, try to implement your idea or see if someone else already has.  Unfortunately, implementing these ideas usually takes far longer than any time you'll save, but sometimes it's just fun to try to get something to work.

---

### Post by red_Marvin on 2010-04-11
I would like to vote for tiling window managers.

---

### Post by johnb820 on 2010-04-11
Openbox with multiple workspaces and simple ways to move windows between them, and keyboard shortcuts to essentials (text editor, browser, terminal, etc.).

---

### Post by kellemes on 2010-04-11
> **red_Marvin said:**
> I would like to vote for tiling window managers.

agree.

---

### Post by phibxr on 2010-04-11
I've felt most productive when using Awesome WM actually. Sane window management without me having to do it for the window manager (a window manager SHOULD be there to manage my windows, not to let me manage them) and no bells and whistles that are fighting for my attention. :)

[http://awesome.naquadah.org/]("http://awesome.naquadah.org/")

On older days I've just began using the standard Gnome desktop though. :P

---

### Post by urukrama on 2010-04-11
> **chucky chuckaluck said:**
> the middle click menu of open windows in openbox might work better if you have a bunch of stuff open on different workspaces. just set the margin on one side to 5, or 10 pixels (in order have room to middle click) and you're all set.

I use Windows-Tab for that, with the following settings in my rc.xml (they might be default, I don't remember):

```
<keybind key="W-Tab">
      <action name="NextWindow">
        <allDesktops>yes</allDesktops>
      </action>
    </keybind>
    <keybind key="W-S-Tab">
      <action name="PreviousWindow">
        <allDesktops>yes</allDesktops>
      </action>
    </keybind>
```

---

### Post by dyltman on 2010-04-11
I would say if not Awesome wm then gnome-shell as they're kinda the same (or well, not that much) except that gnome-shell is not tilling.

---

### Post by jedi453 on 2010-04-14
> **K.Mandla said:**
> This probably isn't what you want to hear, but in my opinion, the most *productive* desktop has been [no desktop at all]("http://kmandla.wordpress.com/2009/05/10/do-more-with-less/"). If you want to trim out distractions and actually get things done, then my suggestion would be to move to a CLI-only arrangement. 

But I say that to everything. :roll:

I agree with you in the spirit of what you said, but not in what you said word for word.

Here's where I'm not so sure: 
I have tried my share of Window Managers, Desktop Environments, Panels, and lack there-of's. I have found that for me nothing is perfect. I am no computer expert, so feel free to take this opinion however you want to, but I found everyone-else's attempt to capture what I want hasn't been exactly what I was looking for. 

If no-one else can provide for you exactly what you need, some way or another you have to provide it for yourself. My theory (and it's just a theory), is that like with building yourself a computer, which I have some experience with, you can put in more of what you're looking for than anyone else can because no matter how hard you try to tell someone else what you want, the sad truth is, you'll never be able to express all of your opinions perfectly for one reason or another. For this reason, you can't expect them to provide for you exactly what you need. So if you are provided with all the tools needed to make yourself what you need, you will be much better off than someone who is forced into a certain choice or certain working environment. "Give a man a fish, and you feed him for a day. Teach a man to fish and you feed him for a lifetime."

In my opinion, this is quite possibly a major reason for operating systems that are sold as one unchangeable package to never be quite what end-users need. No, cost is not the only reason people choose Free Operating Systems. Freedom is what drives many of us to choose Open Source.

Maybe I'm of this opinion because I've followed your (K. Mandla's) blog and found your post leading to this forum-post. Maybe it's also because I've been a huge fan of yours ever since I first discovered your blog, but I've been patient enough to hold back my opinions for quite some time. This time, however, my opinion is stronger, and my stance is firmer.

Long story short, I don't think anyone will ever be able to tell you what you want, they can help you find it, but in the end, you'll be the one doing the majority of the searching.

Wow, I'm long-winded today... :lolflag:

(P.S. Thanks for the awesome blog K. Mandla)
:popcorn:

---

### Post by sudoer541 on 2010-04-14
The most productive GUI IMO I think its 1) Mac OS X 10.6  2) Windows 7 and 3) Gnome (ubuntu)

I have used my cousins macintosh and awwwwwwwwwwwwwwwwww its so cute, gentle and easy to use. Windows comes second (cuz am used to it) and Ubuntu-gnome is third (needs some usability improvment...they should focus more on drag and drop etc) but I still love it.... CANT WAIT FOR LUCID!!!!!!!!!!!!!!

---

### Post by vbd on 2010-04-15
Try guake and Compiz window tiling feature. As alternative switch to xmonad or awesome.

---

### Post by AllRadioisDead on 2010-04-15
Dwm :d

---

