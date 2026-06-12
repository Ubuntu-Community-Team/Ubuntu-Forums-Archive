---
title: "Simple lxde lubuntu aero snap with working obkey keyboard editor"
date: 2012-10-26
forum: Tutorials
---

### Post by ronniew on 2012-10-26
Aero snap is actually pretty cool, and I despise Windows so that says a lot for the feature... In lxde / lubuntu its not really available.

So after scouring the internet again I came up with a pretty cool solution.

**OBKEY is optional** if you don't wish to install it you can skip over this section and jump down to the "time for aero snap feature"

*****

Editing keyboard shortcuts is easy in lxde with obkey.. however obkey doesn't work out of the box with lubuntu... but a minor tweak gets it going.

download the best version for you from [here]("https://launchpad.net/~gld1982ltd/+archive/ppa/+packages") or maybe try sudo apt-get install obkey  ... it might be in there... depending on your system and repos.

After install go to your run menu or in the terminal and paste the following

gksu leafpad /usr/bin/obkey

find the line

/.config/openbox/rc.xml

change it to

/.config/openbox/lubuntu-rc.xml

save file and close

*****

OK now although obkey is install and working.. we are not actually going to use it to setup aerosnap.... why not?  because its a bit too hard to explain but its nice to have and you will use it at the end. (kinda)

*****

**Time for the aero snap feature**

open run or a terminal and enter the following

gksu leafpad ~/.config/openbox/lubuntu-rc.xml

find the line 

<chainQuitKey>C-g</chainQuitKey>

underneath that line copy and paste the following

```
<!-- Aero Snap for Openbox Begin Code-->
    <keybind key="W-Left">        # HalfLeftScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <height>97%</height>
        <width>50%</width>
      </action>
    </keybind>
    <keybind key="W-Right">        # HalfRightScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>-0</x>
        <y>0</y>
        <height>97%</height>
        <width>50%</width>
      </action>
    </keybind>
    <keybind key="W-Up">        # HalfUpperScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>0</y>
        <width>100%</width>
        <height>50%</height>
      </action>
    </keybind>
    <keybind key="W-Down">        # HalfLowerScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>0</x>
        <y>-0</y>
        <width>100%</width>
        <height>50%</height>
      </action>
    </keybind>
<!-- Aero Snap for Openbox End Code-->
```

*****Minor update applied so the panel does not cover any portion of the expanded windows, code above has been updated*****


save and close

now open up obkey (preferences menu) and you will notice four new entries for the super key and arrows..

go ahead and close it,,, (obkey is really easy to edit your shortcuts although we really didn't use it in this situation but it is nice to have)

*****

Now open run or copy and paste this in the terminal:  **openbox --restart**

Now how do you use it??  Well you can't drag you windows to a corner and expect them to snap in place... It won't work but what you can do is pretty sweet even though it manual

Select any window and hold the super key (windows key) and press either left, right, up or down...

and you'll get the hint immediately..

work very well,

ad no extra bloat to the system either..

enjoy.

[IMG]http://www.unleashpc.com/aerosnaplxde.png[/IMG]

*****
**I will be providing a series of easy solutions and linking to them below**
[URL="http://ubuntuforums.org/showthread.php?t=2076351"]
lxde simple weather[/URL]
[lxde wallpaper changer]("http://ubuntuforums.org/showthread.php?t=2076417")
[expose feature for lubuntu]("http://ubuntuforums.org/showthread.php?p=12318587")

---

### Post by vasa1 on 2012-10-26
> **ronniew said:**
> ...
Now open run or copy and paste this in the terminal:  **openbox --restart**
...
I use ```
openbox --reconfigure
```

---

### Post by ronniew on 2012-10-26
did openbox --restart not work? if not I'll change the above instruction to what you used.

---

### Post by vasa1 on 2012-10-26
> **ronniew said:**
> did openbox --restart not work? if not I'll change the above instruction to what you used.
Sorry, I never tried that. It just so happened that I've usually seen the code I use recommended to get changes to lubuntu-rc.xml to take effect and have been using that. Maybe the two are equivalent?

One more point, I've been messing with various things in Lubuntu 12.10 to get things the way I want and haven't yet needed to install obkey.

---

### Post by vasa1 on 2012-10-26
This is what openbox --help has:
```
[06:13 PM] ~ $ openbox --help
Syntax: openbox [options]

Options:
  --help              Display this help and exit
  --version           Display the version and exit
  --replace           Replace the currently running window manager
  --config-file FILE  Specify the path to the config file to use
  --sm-disable        Disable connection to the session manager

Passing messages to a running Openbox instance:
  --reconfigure       Reload Openbox's configuration
  --restart           Restart Openbox
  --exit              Exit Openbox

Debugging options:
  --sync              Run in synchronous mode
  --startup CMD       Run CMD after starting
  --debug             Display debugging output
  --debug-focus       Display debugging output for focus handling
  --debug-session     Display debugging output for session management
  --debug-xinerama    Split the display into fake xinerama screens

Please report bugs at http://bugzilla.icculus.org

```

BTW, both "UnmaximizeFull" and "Unmaximize" seem to work equally well. Do you know of any difference that may be significant?

[s]Since Lubuntu 12.10 has Openbox 3.**5**, I was searching for documentation for 3.5, but most of what I found is for 3.**4**.[/s]

Edit: It was 3.5. For some reason, I thought it was 3.4 :(
And 3.5 has Unmaximize rather than UnmaximizeFull and that seems logical to me.

---

### Post by vanlong441 on 2012-11-15
Thank you for the guide, waiting patiently for this to be published on [http://lubuntublog.blogspot.com/p/tips-tricks.html](http://lubuntublog.blogspot.com/p/tips-tricks.html)

One question: Is it possible to restore a snapped window to its original size and position, or just any size but place it in the center of the screen instead?

---

### Post by kdford on 2012-12-10
> **vanlong441 said:**
> Thank you for the guide, waiting patiently for this to be published on [http://lubuntublog.blogspot.com/p/tips-tricks.html](http://lubuntublog.blogspot.com/p/tips-tricks.html)

One question: Is it possible to restore a snapped window to its original size and position, or just any size but place it in the center of the screen instead?

I think this is not possible, using this trick, as LXDE doesn't really recognize the "snapped left" as another STATE, it sees it the same as if you had manually moved it there, so there's nowhere to restore to.  I assume the other wm's are maintaining two states for each window (snappedOrMaxed, userState) so you can go between the two... Once you use this method it is as if you have dragged the window there with your mouse...

This is a far from perfect solution, but I added another keybinding using the author's method, that makes a 50%x50% window somewhere close to the middle of the screen.

    <keybind key="W-space ">        # middleScreen
      <action name="UnmaximizeFull"/>
      <action name="MoveResizeTo">
        <x>500</x>
        <y>300</y>
        <height>50%</height>
        <width>50%</width>
      </action>
    </keybind>

It isn't perfect, but on my resolution it's not too bad.

---

