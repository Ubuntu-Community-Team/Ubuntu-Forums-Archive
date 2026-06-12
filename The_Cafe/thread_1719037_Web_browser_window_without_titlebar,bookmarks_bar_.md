---
title: "Web browser window without titlebar,bookmarks bar etc?"
date: 2011-04-01
forum: The Cafe
---

### Post by cyb3r_sn4k3 on 2011-04-01
What I'm talking about is similar to what youtube now provides as pop-out video button can it be done through the terminal? (screenshot attached) 

Thanks In Advance :)

---

### Post by Sporkman on 2011-04-01
The "Hide caption titlebar plus" plugin for Firefox will remove the window titlebar. Then there are options within Firefox to remove the rest of the stuff.

---

### Post by Mmmbopdowedop on 2011-04-01
You mean like Firefox in full-screen mode? :s

What you've described seems to be just plain that.

Here's my Firefox attatched, think that's about as minimal as it's worth having, no title bar would be wierd in a non-maximized windowed mode.

You could customize your toolbars and remove most stuff, but I don't understand why you'd want to. :P

---

### Post by cyb3r_sn4k3 on 2011-04-02
> **Pey Tudor said:**
> You mean like Firefox in full-screen mode? :s

What you've described seems to be just plain that.

Here's my Firefox attatched, think that's about as minimal as it's worth having, no title bar would be wierd in a non-maximized windowed mode.

You could customize your toolbars and remove most stuff, but I don't understand why you'd want to. :P

Not exactly what I wanted(see my screenshot).

I want to do it cuz its much more space saving like when I'm testing out html/javascripts or smthin like that it gives me more space for my scripter :D

---

### Post by doorknob60 on 2011-04-02
Try this :)
```
chromium --app="http://google.com"
```

---

### Post by cyb3r_sn4k3 on 2011-04-02
> **doorknob60 said:**
> Try this :)
```
chromium --app="http://google.com"
```


Possible on firefox?

---

### Post by ve4cib on 2011-04-02
For something a little different you could try Mozilla Fennec (aka Firefox Mobile).  It's on the Ubuntu repos (sudo apt-get install fennec).

It's designed for touchscreens/tablets, but does work with a mouse as well.  There are no visible controls other than the address bar, and even that gets hidden when you scroll down.  Tab controls and the settings menu are hidden to the left and right of the page; you access them by clicking and dragging the page to the left or right.

---

### Post by spupy on 2011-04-02
> **cyb3r_sn4k3 said:**
> What I'm talking about is similar to what youtube now provides as pop-out video button can it be done through the terminal? (screenshot attached) 

Thanks In Advance :)

Haha, your picture took me quite a while to figure out what I'm looking at. :D

On topic: you can use Firefox's userChrome.css to modify its user interface to suit your needs.

Also have a look at Mozilla Prism. It is similar to Chrome's app mode, but I recall that it was discontinued. It still might work, though.

---

### Post by uRock on 2011-04-02
The default Firefox in 11.04 is almost like what you are describing.

---

### Post by earthpigg on 2011-04-02
> **spupy said:**
> Haha, your picture took me quite a while to figure out what I'm looking at. :D


i still do not understand what i am looking at. is he using the terminal to download and/or encode a youtube video (ffmpeg?)?

---

### Post by Random_Dude on 2011-04-02
If you're used to vim, you can always browse with firefox using this: [https://addons.mozilla.org/en-US/firefox/addon/pentadactyl/](https://addons.mozilla.org/en-US/firefox/addon/pentadactyl/)

Cheers :cool:

---

### Post by doorknob60 on 2011-04-02
> **cyb3r_sn4k3 said:**
> Possible on firefox?

Not directly through Firefox, but Mozilla offers a seperate program for the same purpose, Prism: [http://prism.mozillalabs.com/](http://prism.mozillalabs.com/) It's quite good :) It has a standalone version and a Firefox add on version. For me, the add on version never worked right, but it might work for you. The standalone version works just fine. I don't think there's a way to directly spit in a URL though, you have to set up launchers which takes just a second with its GUI but depending on what you're using it for it could be inconvinient, but for me it works great if you want launchers for like Gmail or Facebook or whatever.

---

### Post by cyb3r_sn4k3 on 2011-04-03
Here's a new screenshot :lolflag::oops: :-\"

I've also noticed that the manage attachments button also does the same thing :)

---

### Post by linuxnewb2 on 2011-04-03
lol ... like somebody else said ... why not hit F11 ? Full screen in firefox ?

---

### Post by cyb3r_sn4k3 on 2011-04-23
> **linuxnewb2 said:**
> lol ... like somebody else said ... why not hit F11 ? Full screen in firefox ?

True, But its not very convenient when you want multiple windows on your desktop :)

---

### Post by leviathan8 on 2011-04-23
> **doorknob60 said:**
> Try this :)
```
chromium --app="http://google.com"
```

The correct syntax is:
```
chromium-browser --app="http://google.com"
```

Chromium is a game in linux. :p

---

### Post by TheNessus on 2011-04-23
One word: Opera

---

### Post by cyb3r_sn4k3 on 2011-04-23
> **leviathan8 said:**
> The correct syntax is:
```
chromium-browser --app="http://google.com"
```Chromium is a game in linux. :p
  Would u know hw to do it in firefox?

---

### Post by markp1989 on 2011-04-23
how about something like the screen shot I attached?

I used the tiny menu addon to make the menu bar become on button, and moved the address bar and navigation buttons to be next to it.

in preferences i unticked the "always display tab bar" option and hid the status bar 

is that close to what you were looking for?

edit, you can also install the "omnibar" addon to merge the search and address bar (See 2nd attachment)

---

### Post by arzali on 2011-04-23
Make a new folder and rename it for example testprofile

now put this into a text file named testfirefox.sh

```

#!/bin/sh
export MOZ_NO_REMOTE=1
firefox -profile "Path/to/testprofile" $1

```make it executable

```
chmod +x testfirefox.sh
```now start it like ./testfirefox.sh youtube.com

for the first time you need to remove the ui element you dont want

---

### Post by CraigPaleo on 2011-04-23
> **cyb3r_sn4k3 said:**
> True, But its not very convenient when you want multiple windows on your desktop :)

The best use of vertical space with multiple windows and easiest way to obtain it, is to use KDE with the menubar widget in button mode and the panel to one side.

Here are two windows, one snapped to each side. It saves more vertical space with multiple windows than even Unity.

---

### Post by neu5eeCh on 2011-04-23
I've maxed out vertical space using Emerald & the following theme:

[http://compiz-themes.org/content/show.php/Minimal+LittleGlass?content=139829](http://compiz-themes.org/content/show.php/Minimal+LittleGlass?content=139829)

I can best Unity and KDE (though the latter is close). Essentially, the theme more or less eliminates the title bar (for which I've never seen a purpose). That's cool to know about KDE, though, as I may be adopting it or XFCE (liking neither Gnome 3 nor Unity).

---

### Post by CraigPaleo on 2011-04-23
> **VTPoet said:**
> I've maxed out vertical space using Emerald & the following theme:

[http://compiz-themes.org/content/show.php/Minimal+LittleGlass?content=139829](http://compiz-themes.org/content/show.php/Minimal+LittleGlass?content=139829)

I can best Unity and KDE (though the latter is close). Essentially, the theme more or less eliminates the title bar (for which I've never seen a purpose). That's cool to know about KDE, though, as I may be adopting it or XFCE (liking neither Gnome 3 nor Unity).

That's a good theme but it's probably a close tie. You still have the global menu on top instead of to the side. 

If we could find or make a KDE window decoration theme similar to your emerald theme, we'd have a real winner!

---

### Post by cyb3r_sn4k3 on 2011-04-23
> **arzali said:**
> Make a new folder and rename it for example testprofile

now put this into a text file named testfirefox.sh

```

#!/bin/sh
export MOZ_NO_REMOTE=1
firefox -profile "Path/to/testprofile" $1

```make it executable

```
chmod +x testfirefox.sh
```now start it like ./testfirefox.sh youtube.com

for the first time you need to remove the ui element you dont want

Thank you Very much, It was exactly what I was looking for.

---

### Post by del_diablo on 2011-04-23
You can do this with Opera at the least <3

---

### Post by urukrama on 2011-04-23
You mean something like this (see attached image)? In Opera that isn't too hard to accomplish.

---

### Post by cyb3r_sn4k3 on 2011-04-24
Arzali's post did the trick thnx anyways :)

---

