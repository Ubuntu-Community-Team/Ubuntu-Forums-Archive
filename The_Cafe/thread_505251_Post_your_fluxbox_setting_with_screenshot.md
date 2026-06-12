---
title: "Post your fluxbox setting with screenshot"
date: 2007-07-20
forum: The Cafe
---

### Post by tomcheng76 on 2007-07-20
idesk for desktop icon
adesklets for weather
conky for system monitor
rxvt-unicode for background terminal
Ximian Heaven style
any good style?
[[IMG]http://img530.imageshack.us/img530/8531/screenshot2007072015491yx4.th.png[/IMG]](http://img530.imageshack.us/my.php?image=screenshot2007072015491yx4.png)

---

### Post by kerry_s on 2007-07-20
rox -p=icons = aka: rox-filer pinboard for desktop icons
conky = monitor
rxvt-unicode-lite = terminal, mc, axel, i run it with the daemon(uxrvtd, use the client uxrvtc)

i try to recycle the resources, to ease the load on the crappy cpu. simple colored background from theme(cuthlain modified a little)
trim install only what i actually use, vaio pcg-f430 450mhz 256 ram 20gig hd
debian-minimal+fluxbox

---

### Post by Motoxrdude on 2007-07-20
> **tomcheng76 said:**
> idesk for desktop icon
adesklets for weather
conky for system monitor
rxvt-unicode for background terminal
Ximian Heaven style
any good style?
[[IMG]http://img530.imageshack.us/img530/8531/screenshot2007072015491yx4.th.png[/IMG]](http://img530.imageshack.us/my.php?image=screenshot2007072015491yx4.png)

WOW. I hella want to use fluxbox now. That is a pretty sweet setup you got going there.

---

### Post by Xappe on 2007-07-20
conky 
fbpager
black glass fluxbox style
qtcurve gtk/qt style
gnome-terminal
irssi

[[IMG]http://pici.se/thumbs/t_MHRRbdxtT.gif[/IMG]]("http://pici.se/90897")

---

### Post by tomcheng76 on 2007-07-20
rxvt and idesk provides me some transparency

and my pc cant afford beryl, although i can turn it on

and it is definitely faster the gnome which i used b4

the only problem is that thing on ~/Desktop are not really on Desktop ~~"

---

### Post by j.miller565 on 2007-07-20
> **Motoxrdude said:**
> WOW. I hella want to use fluxbox now. That is a pretty sweet setup you got going there.

Me too lol that screen is totally nuts!!!! :guitar:

---

### Post by urukrama on 2007-07-20
> **kerry_s said:**
> rox -p=icons = aka: rox-filer pinboard for desktop icons
conky = monitor
rxvt-unicode-lite = terminal, mc, axel, i run it with the daemon(uxrvtd, use the client uxrvtc)

i try to recycle the resources, to ease the load on the crappy cpu. simple colored background from theme(cuthlain modified a little)
trim install only what i actually use, vaio pcg-f430 450mhz 256 ram 20gig hd
debian-minimal+fluxbox

What is that 'to do list' thingy on your desktop?

---

### Post by Onyros on 2007-07-20
Here's my baby... I'm using idesk for the desktop icons and torsmo as system monitor.

Other than that I use "Dates" and "Tasks" as both a Calendar and To-Do List, but I uncluttered the desktop so it was more visible in its simplicity heh :)

As a file manager, I use PCManFM and can't recommend it enough.

---

### Post by happy-and-lost on 2007-07-20
Debian Etch on a 1GHz Duron with 386MB RAM. Boots fully into the Fluxbox "desktop" in 56 seconds. I keep it simple to keep it fast.

What you can see...
Theme: [Noir]("http://customize.org/fluxbox/themes/49534")
Conky for keeping an eye on things
XMMS with the ATER white skin, using the OSD song change plugin and "hotkeys" to enable my multimedia keyboard buttons
Thunar file manager, using gtk-theme-switch and the .gtkrc-2.0 to set MurrinaGraphiteGentle + Tango icons

[[img]http://xs217.xs.to/xs217/07295/avecmenuflux.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs217&d=07295&f=avecmenuflux.png)

Sadly most of the potential responsiveness is sabotaged by the faulty S3 graphics driver supplied with Etch :(

---

### Post by Onyros on 2007-07-20
> **happy-and-lost said:**
> Debian Etch on a 1GHz Duron with 386MB RAM. Boots fully into the Fluxbox "desktop" in 56 seconds. I keep it simple to keep it fast.

What you can see...
Theme: [Noir]("http://customize.org/fluxbox/themes/49534")
Conky for keeping an eye on things
XMMS with the ATER white skin, using the OSD song change plugin and "hotkeys" to enable my multimedia keyboard buttons
Thunar file manager, using gtk-theme-switch and the .gtkrc-2.0 to set MurrinaGraphiteGentle + Tango icons

[[img]http://xs217.xs.to/xs217/07295/avecmenuflux.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs217&d=07295&f=avecmenuflux.png)

Sadly most of the potential responsiveness is sabotaged by the faulty S3 graphics driver supplied with Etch :(Love it! But you should really look into PCManFM: it's Thunar with tabs, with far less dependencies. ;)

Check out the screenie with it in action :D

---

### Post by tomcheng76 on 2007-07-20
just switched from nautilus --no desktop --browser to pcmanfm
definitely faster
how to use gtk-theme-switch and the .gtkrc-2.0 to change look of pcmanfm ?

---

### Post by happy-and-lost on 2007-07-20
> **Onyros said:**
> Love it! But you should really look into PCManFM: it's Thunar with tabs, with far less dependencies. ;)

Nice! I've not tried that one before. I can get rid of all the XFCE clutter installed with Thunar now :D

> **tomcheng76 said:**
> 
how to use gtk-theme-switch and the .gtkrc-2.0 to change look of pcmanfm ?

Add the gtk-theme-switch to ~/.fluxbox/startup like this:

```
gtk-theme-switch2 /path/to/gtk/theme/folder/eg/MurrinaGraphiteGentle/ &

```

And because gtk-theme-switch will take control on your .gtkrc-2.0, you have to create a ~/.gtkrc-2.0.mine file and add the line: *gtk-icon-theme-name = "Tango"* (or whatever icon set you want) to change the icons. Works for Thunar and PCManFM

---

### Post by Onyros on 2007-07-20
I actually don't use gtk-themeswitch, I just created a gtkrc-2.0 file with my theme details and it's all good. Saves a few more resources, too ;)

in my case, it reads
```
gtk-font-name = "Bitstream Vera Sans 7"
gtk-theme-name = "Human-Graphite"
gtk-icon-theme-name = "nuoveXT-1.6"
```

and works perfectly for all GTK2 apps.

I have to add a disclaimer regarding PCManFM. I've done it elsewhere, but it's better whenever someone new finds PCManFM. Be careful with the deletion of files, make sure you have files selected when you have to delete something, otherwise it'll delete all contents of your folder and the folder itself.

Yep, I suppose it's a bug, but it's easily avoidable. Just be careful! Other than that it works perfectly, and the tabs are really handy. (even though I use Fluxbox's auto-tabs, too)

---

### Post by tomcheng76 on 2007-07-20
> **Onyros said:**
> I actually don't use gtk-themeswitch, I just created a gtkrc-2.0 file with my theme details and it's all good. Saves a few more resources, too ;)

in my case, it reads
```
gtk-font-name = "Bitstream Vera Sans 7"
gtk-theme-name = "Human-Graphite"
gtk-icon-theme-name = "nuoveXT-1.6"
```

and works perfectly for all GTK2 apps.

I have to add a disclaimer regarding PCManFM. I've done it elsewhere, but it's better whenever someone new finds PCManFM. Be careful with the deletion of files, make sure you have files selected when you have to delete something, otherwise it'll delete all contents of your folder and the folder itself.

Yep, I suppose it's a bug, but it's easily avoidable. Just be careful! Other than that it works perfectly, and the tabs are really handy. (even though I use Fluxbox's auto-tabs, too)

great, i am managed to change the look of gtk application
2nd question, how to add folder into side plane of PCManFM ?

---

### Post by Onyros on 2007-07-20
> **tomcheng76 said:**
> great, i am managed to change the look of gtk application
2nd question, how to add folder into side plane of PCManFM ?Those are Bookmarks!

Just browse to the folder you want to add, click on Bookmark > Add to Bookmarks :)

---

### Post by tomcheng76 on 2007-07-20
great brothers :)
[[IMG]http://img126.imageshack.us/img126/6913/screenshot2007072023024sk5.th.png[/IMG]](http://img126.imageshack.us/my.php?image=screenshot2007072023024sk5.png)
i think it is really last question , is there a way to change Trash icon ?

---

### Post by Freddy on 2007-07-20
> **Xappe said:**
> conky 
fbpager
black glass fluxbox style
qtcurve gtk/qt style
gnome-terminal
irssi

[[IMG]http://pici.se/thumbs/t_MHRRbdxtT.gif[/IMG]]("http://pici.se/90897")
I like the name of your comuter :). 

Ge mig ett schyst järnrör, så ska jag slå världen med häpnad.

/Freddan

---

### Post by Xappe on 2007-07-20
> **Freddy said:**
> I like the name of your comuter :). 

Ge mig ett schyst järnrör, så ska jag slå världen med häpnad.

/Freddan

:)

---

### Post by kerry_s on 2007-07-20
> **urukrama said:**
> What is that 'to do list' thingy on your desktop?

that's just xpad, i'm getting old and if i don't jot it down i forget what i was doing. :(
i just leave it there when i'm multi-tasking, it's very light and dead simple to use. I also use xcal a very simple scheduler. i try and use only very light applications, things that are very small and fast, they may not look fancy, but they get the job done and doesn't make me wait for it to load. I try and use what ever's built in if i can, things like xcalc that's part of xorg, there's also a clock, calendar, text editor already installed on every ones system, they may not look good but they are light.

oop's forgot to finish that note.: my mp3 player can be started and will continue to play when i close it, i can start it again to stop the music or switch to a different folder. time for sleep :)

---

### Post by urukrama on 2007-07-20
thanks, kerry. I've used xpad in the past, but I don't think I'll use xcal. But thanks to you I also discovered xcalc. Now I don't have to install the gnome calculator.

---

### Post by kerry_s on 2007-07-21
> **urukrama said:**
> thanks, kerry. I've used xpad in the past, but I don't think I'll use xcal. But thanks to you I also discovered xcalc. Now I don't have to install the gnome calculator.

here's my xcalc setting for the .Xdefaults file to get rid of the stock ugly grey.

```

xcalc*geometry: 200x275
xcalc.ti.bevel.background: #111111
xcalc.ti.bevel.screen.background: Green
xcalc.ti.bevel.screen.DEG.background: Green
xcalc.ti.bevel.screen.DEG.foreground: Black
xcalc.ti.bevel.screen.GRAD.background: Green
xcalc.ti.bevel.screen.GRAD.foreground: Black
xcalc.ti.bevel.screen.RAD.background: Green
xcalc.ti.bevel.screen.RAD.foreground: Black
xcalc.ti.bevel.screen.INV.background: Green
xcalc.ti.bevel.screen.INV.foreground: Red
xcalc.ti.bevel.screen.LCD.background: Green
xcalc.ti.bevel.screen.LCD.foreground: Black
xcalc.ti.bevel.screen.LCD.shadowWidth: 0
xcalc.ti.bevel.screen.M.background: Green
xcalc.ti.bevel.screen.M.foreground: Black
xcalc.ti.bevel.screen.P.background: Green
xcalc.ti.bevel.screen.P.foreground: Black
xcalc.ti.Command.foreground: White
xcalc.ti.Command.background: black
xcalc.ti.button5.background: orange
xcalc.ti.button20.background: red
xcalc.ti.button25.background: red
xcalc.ti.button30.background: red
xcalc.ti.button35.background: red
xcalc.ti.button40.background: green
xcalc.ti.button22.background: blue
xcalc.ti.button23.background: blue
xcalc.ti.button24.background: blue
xcalc.ti.button27.background: blue
xcalc.ti.button28.background: blue
xcalc.ti.button29.background: blue
xcalc.ti.button32.background: blue
xcalc.ti.button33.background: blue
xcalc.ti.button34.background: blue
xcalc.ti.button37.background: blue
XCalc*Cursor:                 hand2
XCalc*ShapeStyle:             rectangle

```

---

### Post by urukrama on 2007-07-21
> **kerry_s said:**
> here's my xcalc setting for the .Xdefaults file to get rid of the stock ugly grey.

Thank you. I don't know if I like your colour settings better (white text on black background doesn't work for me...), but thank you very much for posting that. I had no clue you could change the colours so easily. This is great!

---

### Post by kerry_s on 2007-07-21
> **urukrama said:**
> Thank you. I don't know if I like your colour settings better (white text on black background doesn't work for me...), but thank you very much for posting that. I had no clue you could change the colours so easily. This is great!

i just copied the colors from a actual calculator i use to do my bills. :)
but yeah it's very simple to change to what ever color you want, just count the keys from left to right for the button #, tip there grouped in 5, for easy counting. you can change any button with "xcalc.ti.button#.background: color" and "xcalc.ti.button#.foreground: color" so you can even mix the text color of each button. have fun.

---

### Post by tigerpants on 2007-07-21
Theme: redstripe
Conky font: James Fajardo
Wallpaper: Dunno, found it on my harddrive

Fluxbox is da bomb.

---

### Post by Snocrash on 2007-07-22
gkrellm, gdesklets, sid_fluxarnation theme.

---

### Post by plb on 2007-07-22
debian sid w/ custom theme

---

### Post by ice60 on 2007-07-22
here's an old picture of my fluxbox desktop, i've got FB on my laptop but i'm not using it right now.

[[img]http://xs117.xs.to/xs117/07301/conkyru9.png.xs.jpg[/img]](http://xs.to/xs.php?h=xs117&d=07301&f=conkyru9.png)

---

### Post by Glenn Jones on 2007-07-23
Hi guys 

This may sound like a stupid question but do you mind letting me know the type of fonts you are using with your terminal? 
I'm finiding gnome-terminal heavy and sluggish and I want to change to aterm/eterm so long as I can make the fonts look nice

Cheers

---

### Post by ice60 on 2007-07-23
> **Glenn Jones said:**
> Hi guys 

This may sound like a stupid question but do you mind letting me know the type of fonts you are using with your terminal? 
I'm finiding gnome-terminal heavy and sluggish and I want to change to aterm/eterm so long as I can make the fonts look nice

Cheers

another option is the xfce terminal, that's what i was using in the screenshot, it might be called Terminal (with the capital T). i like these  fonts for the term. -
DejaVu Sans Mono
Monospace
Lucida Console

**[color=blue]EDIT[/color]** you can get the mac fonts, which include Lucida Console, from here -
[http://www.osx-e.com/downloads/misc/macfonts.html](http://www.osx-e.com/downloads/misc/macfonts.html)

in my ubuntu install i have the fonts copied to here - 
/usr/share/fonts/truetype/ttf-lucida

when that's done you run **fc-cache**

then log out and back in and the fonts should be available

---

### Post by RedSquirrel on 2007-07-24
> **Glenn Jones said:**
> Hi guys 

This may sound like a stupid question but do you mind letting me know the type of fonts you are using with your terminal? 
I'm finiding gnome-terminal heavy and sluggish and I want to change to aterm/eterm so long as I can make the fonts look nice

Cheers

If you don't want transparency, then xterm (or uxterm) is a nice terminal. ;)

This is what I'm using:

```
uxterm -bg black -fg white +sb -geometry 100x40 -fa DejaVuSansMono -fs 10

```By the way, transparency works well on urxvt (rxvt-unicode) if you want to use that instead of aterm or eterm. Up to you.


** EDIT:**

... and here's my screenshot as well. :grin:

- conky
- fbpager
- no toolbar
- no desktop icons
- [Noir]("http://customize.org/fluxbox/themes/49534") theme with a few modifications (many thanks to happy-and-lost for mentioning that one; great-looking theme)
- urxvt (rxvt-unicode) for a transparent terminal (eye candy)
- uxterm for my regular terminal (getting work done)

---

### Post by Glenn Jones on 2007-07-25
Thanks guys. I guess what I ideally want is a tabbed xterm. I really hate having 4 or 5 xterm windows open at the same time especially on my laptop which has a 12" screen. Do you know of a tabbed xterm??

---

### Post by kerry_s on 2007-07-25
> **RedSquirrel said:**
> If you don't want transparency, then xterm (or uxterm) is a nice terminal. ;)

This is what I'm using:

```
uxterm -bg black -fg white +sb -geometry 100x40 -fa DejaVuSansMono -fs 10

```By the way, transparency works well on urxvt (rxvt-unicode) if you want to use that instead of aterm or eterm. Up to you.


** EDIT:**

... and here's my screenshot as well. :grin:

- conky
- fbpager
- no toolbar
- no desktop icons
- [Noir]("http://customize.org/fluxbox/themes/49534") theme with a few modifications (many thanks to happy-and-lost for mentioning that one; great-looking theme)
- urxvt (rxvt-unicode) for a transparent terminal (eye candy)
- uxterm for my regular terminal (getting work done)

 
wow, your background looks like it was taken downtown in waikiki, hawaii. :)

---

### Post by kerry_s on 2007-07-25
> **Glenn Jones said:**
> Thanks guys. I guess what I ideally want is a tabbed xterm. I really hate having 4 or 5 xterm windows open at the same time especially on my laptop which has a 12" screen. Do you know of a tabbed xterm??

tabbed terminal try eterm, you get the best of all worlds.

---

### Post by Glenn Jones on 2007-07-25
So I decided to give rxvt-unicode a go and it seems to do everything I want it to do. I can get tabbs if I need them and the fonts look quite cool. 


> 

Originally Posted by RedSquirrel  
If you don't want transparency, then xterm (or uxterm) is a nice terminal. 

This is what I'm using:


Code:
uxterm -bg black -fg white +sb -geometry 100x40 -fa DejaVuSansMono -fs 10By the way, transparency works well on urxvt (rxvt-unicode) if you want to use that instead of aterm or eterm. Up to you.


EDIT:

... and here's my screenshot as well. 

- conky
- fbpager
- no toolbar
- no desktop icons
- Noir theme with a few modifications (many thanks to happy-and-lost for mentioning that one; great-looking theme)
- urxvt (rxvt-unicode) for a transparent terminal (eye candy)
- uxterm for my regular terminal (getting work done) 



Any chance you could post your .Xdefaults RedSquirrel??

---

### Post by RedSquirrel on 2007-07-25
> **kerry_s said:**
> wow, your background looks like it was taken downtown in waikiki, hawaii. :)
:grin:

It's Vancouver, British Columbia, Canada. It's hard to beat in terms of sheer physical beauty. Every view is a postcard. You should see the view looking West (into the picture) from the midpoint of that bridge!

I change my backgrounds a lot, but I think I'll be sticking with this one for a while. :)

---

### Post by RedSquirrel on 2007-07-25
> **Glenn Jones said:**
> So I decided to give rxvt-unicode a go and it seems to do everything I want it to do. I can get tabbs if I need them and the fonts look quite cool. 




Any chance you could post your .Xdefaults RedSquirrel??
I'm not using one at the moment. I just tweaked the settings on the command line and then I made a shortcut in my ~/.fluxbox/keys file. Here are the settings I used (or something close to this):

```
urxvt -tr -tint white -sh 50 -fg white -bg black +sb -geometry 100x40 -fn "xft:DejaVuSansMono:size=10" -sl 1000
```

---

### Post by BOBSONATOR on 2007-07-25
This one was one of my personal favorites.

[http://ubuntuforums.org/attachment.php?attachmentid=34488&d=1181103273](http://ubuntuforums.org/attachment.php?attachmentid=34488&d=1181103273)

---

### Post by Glenn Jones on 2007-07-25
Thanks. 

Ok my final question on the whole configuration thing of urvxt is how do I make the colors the same as in xterm? I use ls -G so I get coloured output, but the xterm highlighting of directories(/folders) is a lighter than in urxvt (or linux). The darker blue outpured is quite difficult to see in on a black background. How can I change the output in urxvt so it is the same as in xterm

Cheers

---

### Post by ghandi69_ on 2007-07-25
This is my VERY first screenshot post (for flux, or anything for that matter).. I want to thank  all of you for helping me by answering my questions and coming on here to share your original ideas...

So here it is..

I use black_harmony theme from a flux-look.org type site
deviant art wallpaper
(tango icons in thunar... looking for a better 'black/grey' alternative)
conky

and thats it....

---

### Post by RedSquirrel on 2007-07-25
> **Glenn Jones said:**
> Thanks. 

Ok my final question on the whole configuration thing of urvxt is how do I make the colors the same as in xterm? I use ls -G so I get coloured output, but the xterm highlighting of directories(/folders) is a lighter than in urxvt (or linux). The darker blue outpured is quite difficult to see in on a black background. How can I change the output in urxvt so it is the same as in xterm

Have a look at the file:
/etc/X11/app-defaults/XTerm-color

For now, I just borrowed them from there and put them in ~/.Xdefaults.

```
URxvt*color0: black
URxvt*color1: red3
URxvt*color2: green3
URxvt*color3: yellow3
URxvt*color4: blue2
URxvt*color5: magenta3
URxvt*color6: cyan3
URxvt*color7: gray90
URxvt*color8: gray50
URxvt*color9: red
URxvt*color10: green
URxvt*color11: yellow
URxvt*color12: rgb:5c/5c/ff
URxvt*color13: magenta
URxvt*color14: cyan
URxvt*color15: white

```Do have a look at this too:

[http://gentoo-wiki.com/TIP_Linux_Colors_in_Aterm/rxvt](http://gentoo-wiki.com/TIP_Linux_Colors_in_Aterm/rxvt)

 It's very good. :grin:

---

### Post by RedSquirrel on 2007-07-25
> **ghandi69_ said:**
> This is my VERY first screenshot post (for flux, or anything for that matter).. I want to thank  all of you for helping me by answering my questions and coming on here to share your original ideas...

So here it is..

I use black_harmony theme from a flux-look.org type site
deviant art wallpaper
(tango icons in thunar... looking for a better 'black/grey' alternative)
conky

and thats it....

Nice one. You sure have lots of info in that conky. :)

---

### Post by ghandi69_ on 2007-07-26
> **RedSquirrel said:**
> Nice one. You sure have lots of info in that conky. :)


Yep, I defintiely need it to tell me what kind of processor and video card I have running in there, just in case they try switching on me, I'll catch them right away!!

(or at least in 1.0 seconds(conky update time))

---

### Post by Xappe on 2007-07-27
[[img]http://pici.se/thumbs/t_mXDZnCyqQ.gif[/img]](http://pici.se/94562)

[[img]http://pici.se/thumbs/t_QybVACJrF.gif[/img]](http://pici.se/94580)

fluxpanel
fbpager
conky (two instances)
idesk (for the icons to the right)
gnome-panel

fluxbox style: slightly modified black_glass
gtk/qt - qtcurve

---

### Post by spupy on 2007-08-15
[My Fluxbox]("http://www.stud.uni-karlsruhe.de/~uibxn/Screenshots/screens8/2007-08-15-153029_1280x800_scrot.png") (link)

- aterm (to be changed with urxvt)
- rox-filer
- rox-pinboard for icons and background
- conky, of course
- fbpager
- xcompmgr
- theme is called Mysta;  icons are from the GAIA pack; for gtk i use Tango icons and the GAIA-ECO theme.

---

### Post by blithen on 2007-08-15
Wow! FluxBox pwns Gnome or KDE in my opinion, are you guys using Ubuntu with that? 'Cause...hoooow? T__T

---

### Post by JMO707 on 2007-09-19
> **spupy said:**
> [My Fluxbox]("http://www.stud.uni-karlsruhe.de/~uibxn/Screenshots/screens8/2007-08-15-153029_1280x800_scrot.png") (link)

- aterm (to be changed with urxvt)
- rox-filer
- rox-pinboard for icons and background
- conky, of course
- fbpager
- xcompmgr
- theme is called Mysta;  icons are from the GAIA pack; for gtk i use Tango icons and the GAIA-ECO theme.

That's just beautiful (except for the green bar at top =P)

I'll fork it and make my own, haha.

---

### Post by Onyros on 2007-09-19
Here's my "baby" (updated):

[[IMG]http://img131.imageshack.us/img131/9673/fluxscreenlx6.th.png[/IMG]](http://img131.imageshack.us/my.php?image=fluxscreenlx6.png)

Once you go *box, you'll never go back.

---

### Post by nest on 2007-09-26
> **spupy said:**
> [My Fluxbox]("http://www.stud.uni-karlsruhe.de/~uibxn/Screenshots/screens8/2007-08-15-153029_1280x800_scrot.png") (link)

- aterm (to be changed with urxvt)
- rox-filer
- rox-pinboard for icons and background
- conky, of course
- fbpager
- xcompmgr
- theme is called Mysta;  icons are from the GAIA pack; for gtk i use Tango icons and the GAIA-ECO theme.

this is by FAR, the best desk i ever see.

---

### Post by rjmdomingo2003 on 2007-09-27
> **spupy said:**
> [My Fluxbox]("http://www.stud.uni-karlsruhe.de/~uibxn/Screenshots/screens8/2007-08-15-153029_1280x800_scrot.png") (link)

- aterm (to be changed with urxvt)
- rox-filer
- rox-pinboard for icons and background
- conky, of course
- fbpager
- xcompmgr
- theme is called Mysta;  icons are from the GAIA pack; for gtk i use Tango icons and the GAIA-ECO theme.

Where did you get that GAIA icon pack?

---

### Post by bapoumba on 2007-09-27
[http://ubuntuforums.org/showthread.php?t=539991](http://ubuntuforums.org/showthread.php?t=539991)
Please use the screenshot thread, thanks. Closing here.

---

