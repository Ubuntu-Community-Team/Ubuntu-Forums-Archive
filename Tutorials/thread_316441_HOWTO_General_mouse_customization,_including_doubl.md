---
title: "HOWTO: General mouse customization, including double click"
date: 2006-12-10
forum: Tutorials
---

### Post by tweedledee on 2006-12-10
The information in this thread have been moved to [https://help.ubuntu.com/community/MouseCustomizations](https://help.ubuntu.com/community/MouseCustomizations)

A thread for discussion of the wiki page only can be found here [http://ubuntuforums.org/showthread.php?t=2012401](http://ubuntuforums.org/showthread.php?t=2012401)
Thread closed.


This is yet another mouse button customization guide.  From reading these forums (and others on the net), I think the major unresolved issue for many users switching to Linux is the ability to set an arbitrary (usually the middle or thumb) button on a mouse to "double click" (typically double "left click").  I finally worked out a reasonable solution to this problem, and am including enough additional details that most people should be able to work out how to customize their mice.  This is not to take away from a wide variety of other guides in these forums, but they are perhaps too specific (i.e., it's hard to modify the command set the poster presents, which typically don't work at all with my Marble Mouse trackball).  These instructions rely only on X and distro-independent tools for it, so should work with most or all Linux distros with only minor changes.  I have personally used or seen other people use parts of these instructions without problem in multiple versions/releases of Ubuntu and Debian.

NOTE: Please keep all help questions public (i.e., post here rather than private messaging me), as any question you have is most likely one that will benefit other users, and I do have a full-time job, so can't act as private support for anyone.

You may wish to try the program btnx: discussion at [http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656) and download at [http://www.ollisalonen.com/btnx/](http://www.ollisalonen.com/btnx/).  For many users, this program is probably easier and sufficient, and provides an interface similar to that for Logitech mice under Windows.  However, btnx is still in development, so may not be entirely stable yet.  Btnx also does not allow for some of the more complex combinations discussed below, such as modifier keys with mice buttons.  **Note**: as of Sep 2008, btnx development has apparently ceased, due to something in Xorg 7.4 (released with Intrepid) permanently breaking the method btnx used to communicate with the mouse.

Updated 1 April 2008

SHORCUT: If all you want to do is set your four or five button mouse to use the extra buttons as "forward" and "back" buttons, you may have success with performing only a single action: edit /etc/X11/xorg.conf in the mouse section, and add the following two lines:
```
Option "Buttons" "7"
Option "ButtonMapping" "1 2 3 6 7"
```  Make sure to backup the file first, and restart X to have the effect take place.  Assuming you are one of the fortunate people who only wants these functions and whose mouse buttons map as the "standard" behavior, you'll be all set.  If it does not work, or you want other functions, you'll need to follow the longer details below.  (END SHORTCUT)

First, you need to install several programs.  xbindkeys allows you to map any mouse (or keyboard) event to some program.  xautomation is our gateway to setting up a "double click" event and mapping keyboard events to mouse buttons, and so it is not needed if you do not plan on using this.

NOTE: xvkbd seems to be the preferred tool in other threads instead of xautomation/xte, so if you wish you can use that instead of xautomation for all the same keyboard mapping tasks if you prefer that approach.  xmacro is another tool that may work to replace xte for double click.

Open a terminal and type:
```
sudo apt-get install xautomation
sudo apt-get install xbindkeys
```

**--Getting button numbers--**
Now we need to determine the "button number" of each physical button on your mouse.
```
xev
```

This will open a window.  Move your mouse cursor over it, and you'll see a lot of output in your terminal; don't worry about the output that happens when you move the mouse.  One at a time, single click each button inside the "event tester" window, and note the 3rd line of output from either (or both) of the "ButtonPress" or "ButtonRelease" notices that pop up.  The center item is "button X."  Make a note of the number that matches each physical button on your mouse.  Also note if one or more buttons do not respond.

**--Scroll Wheel and getting all buttons to respond--**
First, get your scroll wheel working, if you have one.  As I do not, this will be approximate, but the other guides available cover this in great depth if you need more help.  Basically, the "scroll up" and "scroll down"are 2 more buttons on your mouse, so you will need to identify this as well using xev.  Then type:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf
```

It is essentially to have a backup of xorg.conf, as messing it up can damage your ability to work to load your window environment.  Search for "mouse."  It should look something like this (although you may have additional lines):
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"6 7"
	Option		"Emulate3Buttons"	"true"
EndSection
```

The only two lines we are going to touch are the "Protocol" and "ZAxisMapping" lines.  Only change the Protocol line if one or more buttons did not respond.  If you have unresponding buttons, chances are that you are using the PS/2 or IMPS/2 protocols, which may not allow for as many buttons (or the configuration) that you have, in which case try the ExplorerPS/2 as shown above.  If you are already set to that and can't get buttons to respond (or get multiple button events in response to a single click), you probably need to use the "evdev" driver, described near the bottom of this post.

ZAxisMapping refers to the scroll wheel.  Basically, the simplest way to get the scroll wheel to work is to change the "6 7" above to match the two scroll button numbers from xev.
 
You will need to restart X (logout & press Ctrl + Alt + Backspace) to have these changes go into effect.  If you changed the protocol, you will need to resume at the beginning (getting button numbers) as they will probably have changed.  If your scroll wheel still does not work, try this in the terminal (the pointer should have as many numbers as from the -pp output, each only once):
```
xmodmap -pp
xmodmap -e "pointer = 1 2 3 4 5 X Y 6 7 ..."
```
This first outputs your current mapping of buttons.  Basically, this means that the number shown (in the pointer) is the button # that triggers the events normally associated with the button position (i.e., here X & Y should be replaced with your 2 scroll buttons, to get them to trigger the 6 & 7 events).  Note that if you use xmodmap, you will to auto-load this each time you start X (in Gnome, go to System -> Preferences -> Sessions -> StartUp, and add the xmodmap command.  Also note that xmodmap takes effect immediately; you do not need to restart.

You may also need to add a "buttons" option and try remapping in xorg.conf; see the other tutorials and [http://www.die.net/doc/linux/man/man4/mouse-driver.4.html](http://www.die.net/doc/linux/man/man4/mouse-driver.4.html) for more details.

**--Rearranging buttons--**
As mentioned above, you can use xmodmap to rearrange buttons.  This is useful if, as with my marble mouse, none of the buttons are set to be the "middle" button, which can be a problem in some programs.  The middle button is button position 2.  On my mouse, I have 4 buttons, which are assigned numbers 1, 3, 8, and 9.  I use this:
```
xmodmap -e "pointer = 3 8 1 4 5 6 7 2 9"
``` to assign button 8 to be the "middle button" (and assign position 8 to button 2, which does not exist).  Note that I am also using this left-handed, so my right- & left-click buttons are swapped ("normally" the 1 is left-click and 3 is right-click).  In my case, positions which are assigned numbers 2 & 4-7 do not have any function, since I do not have any of those button numbers. Again, you must run xmodmap each time you login for this to work.

**--Setting up double click--**
I know it's taken a while to get here, but the unique point to this howto: setting an arbitrary button to be a "double click."  To follow what we're going to do, understand that there is no such thing as a "double click" event.  What we are actually going to do is assign a button to give 2 "left-click" events.

Installing xautomation provided us with several tools (use "man xautomation" if you're curious), but the key one is "xte."  This allows us to send arbitray mouse (& keyboard) events to the kernel.  We will also make use of xbindkeys to first trap the button event.  First, create .xbindkeysrc, which xbindkeys uses for trapping events:
```
gedit ~/.xbindkeysrc
```
Now type:
```
"/usr/bin/xte 'mouseup Y' 'mouseclick 1' 'mouseclick 1' &"
b:Y
```
or
```
"/usr/bin/xte 'mouseclick 1' 'mouseclick 1' &"
b:Y + Release
```
(The difference is whether you want the double click to to respond when you first click the mouse, or only when you release the button, respectively.)
Replace "Y" in "b:Y" with the button number of the button you wish to assign to double-click.  Save & close this file.

```
xbindkeys -n -v
```
This starts xbindkeys running in the foreground, which means it will tell you if there are problems with your file.  If you click the button Y, you should see xbindkeys provide trapping feedback upon release, and see feedback as well from button 1.  Press "Ctrl + C" to stop this interface, then (if everything is working):
```
xbindkeys &
```
which will load xbindkeys in the background, and you should be set.  As with xmodmap (end of the Scroll Wheel section), you need to add xbindkeys to start when X loads for this to work long-term.

**--Additional keys--**
Basically, adding any other function to your mouse is going to use xbindkeys via the .xbindkeysrc file, except the command line will look something like this:
```

"/usr/bin/xte 'keydown Alt_L' 'key Left' 'keyup Alt_L' &"
b:Z
```

This example binds "Alt + Left Arrow" to button Z, which works as "back" in Firefox (and a variety of other applications).  You can read many more examples of key combinations here using "man xte" or at the xbindkeys site: [http://hocwp.free.fr/xbindkeys/xbindkeys.html](http://hocwp.free.fr/xbindkeys/xbindkeys.html) .  The examples there mostly show to how invoke programs, but you can still get the example keys and just substitute in the example above.  Also at the site are scripts (and at least one example of how to use in their config files, I think for invoking emacs two different ways) on mapping multiple events to a single button (e.g., if single click button Z, go back; if double-click, go forward).

For those wishing to set "scroll up" & "scroll down" buttons that repeat (i.e., advance multiple times instead of just once per click), it should be possible to set up a short script that loops the xte event & a short sleep event as long as the button is held down, and invoke that script in .xbindkeysrc, but I have not actually tested this.

EDIT: see the next few posts for how to get scroll working for multiple advances.

Also note that xbindkeys is a great way to get keyboard combinations working (e.g., that useless Windows key, the multimedia keys you may have, or other random combinations to load favorite programs).

**--Application specific settings--**
See this thread: [http://www.ubuntuforums.org/showthread.php?t=380927](http://www.ubuntuforums.org/showthread.php?t=380927).
Or post #30 below for an equivalent approach.

--Dealing with different settings for laptops when external mouse connected--
See this thread for a start: [http://www.ubuntuforums.org/showthread.php?t=350464](http://www.ubuntuforums.org/showthread.php?t=350464).

**--evdev driver--**
If you have multiple scroll wheels or buttons that are not recognized, you probably need to use the evdev driver.  This is a little more complicated to set up.  Much of this section is stolen from another mouse guide: [https://help.ubuntu.com/community/MX1000Mouse](https://help.ubuntu.com/community/MX1000Mouse).

**Note to Hardy users:** the evdev driver was changed significantly for Xorg 7.3, released with Hardy.  The below will not work.  You may be able to replace Option "Name" with Option "by-path" and choose the correct device from /dev/input/by-path/, but users are reporting mixed success with this on Launchpad.  Some of the other configuration options for evdev have also apparently been dropped.

If running pre-Gutsy releases, install evdev (it is install by default in Gutsy):
```
sudo apt-get install xserver-xorg-input-evdev
```
Then you need to identify the name of your mouse (or its receiver, if wireless):
```
cat /proc/bus/input/devices
```
Which will yield output something like this (on my computer):
> I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=05a4 Product=9998 Version=0100
N: Name="NOVATEK USB Keyboard"
P: Phys=usb-0000:00:1f.2-1/input0
S: Sysfs=/class/input/input58
U: Uniq=
H: Handlers=kbd event1 
B: EV=120003
B: KEY=10000 7 ff87207a c14057ff febeffdf ffefffff ffffffff fffffffe
B: LED=7

I: Bus=0003 Vendor=05a4 Product=9998 Version=0100
N: Name="NOVATEK USB Keyboard"
P: Phys=usb-0000:00:1f.2-1/input1
S: Sysfs=/class/input/input59
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=c000 100000 0 0 0

I: Bus=0003 Vendor=046d Product=c408 Version=0110
N: Name="Logitech USB Trackball"
P: Phys=usb-0000:00:1f.4-1/input0
S: Sysfs=/class/input/input60
U: Uniq=
H: Handlers=mouse1 event3 
B: EV=7
B: KEY=1f0000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=button_power/button/input0
S: Sysfs=/class/input/input61
U: Uniq=
H: Handlers=kbd event5 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input62
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=100000 0 0 0
You are looking for the one that implies a mouse, or the manufacturer of your mouse (not the Macintosh mouse buttom emulation) and generally would refer to "mouse" in the "Handler" line of the section; in my cases, this is the 5th entry with the name "Logitech USB Trackball".  Make a note of the name line, including all capitalization exactly.

Edit (after backing up!) your xorg.conf as described above, replacing the existing mouse section section (between the "Section..." and "EndSection" lines) with this:
```

        Identifier      "Logitech Trackball"
        Driver          "evdev"
        Option          "Name"          "Logitech USB Trackball"

```
replacing the Identifier to reflect what you wish to call your mouse, and the Option "Name" with the name of your mouse from the output desribed above.

Then replace the 
```
InputDevice     "configured mouse"
```
near the bottom of xorg.conf with this (replacing your name as needed):
```
InputDevice     "Logitech Trackball" "CorePointer"
```

NOTE: If you using a laptop where your mouse will not always be connected, use "SendCoreEvents" instead of "CorePointer".

Save & close xorg.conf and restart X, then resume the guide above (note that the ZAxisMapping trick won't work with evdev).

Also note with the evdev driver that some buttons will report two events (e.g., the "tilt wheel" of Logitech mice).  The first button, usually the higher number, is the "start/stop" signal for the event, while the second button, usually lower and repeating, is the button you usually want to modify to change a function.  I've not found a way on those mice to change which button is triggered (e.g., the "cruise" buttons on the Logitech MX1000 trigger buttons 4 & 5, which are the same as the scroll wheel, so you can't change the cruise effect separately from an effect on the scroll wheel).

**--Conclusion--**
So sorry for the marathon length, but hopefully this explains more of how things actually work, and will allow people to customize their mice in a fairly straightforward fashion.  I will attempt to key an eye on this if anyone wants to provide feedback, point out problems, or needs additional help, but I'm trying to finish up my PhD so I can move on with my life, so I won't have a lot of time (I've already spent far too much on this problem).  Feel free to re-post, abbreviate, correct, etc.  Finally, for those long-time Linux users who may respond "just use KDE" or other useless pieces of "advice" to avoid the need for a double-click altogther, I just want to say that there are plenty of good reasons to want a separate single & double click event for normal users, and especially for those who have trouble physically double-clicking (most Linux users seem to forget out the "accessibility" issue of computers, though I find these forums to be much better than forums elsewhere - Ubuntu users must just be nicer people. 8) )

---

### Post by ciscosurfer on 2006-12-10
I'm not sure if this helps any (by way of double-clicking versus single-clicking), but you can enable single clicking behaviour through gconf-editor.

Open gconf-editor and go to Apps > Nautilus > Preferences and click on the key called click_policy and change the word double to the word single.  Et, voila!

---

### Post by tweedledee on 2006-12-12
>  I'm not sure if this helps any (by way of double-clicking versus single-clicking), but you can enable single clicking behaviour through gconf-editor.

This approach is the wrong solution, at least for me.  While this avoids having to double-click in certain situations (e.g., starting a program), it does not address two basic issues:
1) I like to be able to select something without necessarily activating (e.g., when I want to delete something on my desktop - and, yes, I know you can right-click & select it, but I prefer to left-click & hit the delete key).
2) There are many cases within programs where double-clicking is required (e.g., to select a word), and the Nautilus preference has no effect there.  (Fortunately: imagine being unable to distinguish single- & double-clicking while trying to write a document!)

My personal primary motiviation comes from events falling into the 2nd case.

---

### Post by kobewan on 2006-12-13
> **tweedledee said:**
> 

For those wishing to set "scroll up" & "scroll down" buttons that repeat (i.e., advance multiple times instead of just once per click), it should be possible to set up a short script that loops the xvkbd event & a short sleep event as long as the button is held down, and invoke that script in .xbindkeysrc, but I have not actually tested this.


Can you possible explain how to do this, or even how to begin? I want to somehow set up xbindkeys to make it so that holding down Button 8 will continuously scroll down (Button 5). Unfortunately, I cannot figure out how to make xbindkeys repeat an event for as long as a button is held down, it only does the event once. Right now I just have it scroll down three times, and keep pressing it. An idea I have for this, but am unable to implement, is to create a script that will send an infinite number of button 5 events with a short delay, and have it execute when button 8 is pressed. Then, when button 8 is releases, the xbindkeys will kill the script. Would that even work?

Also, is there any way to use xmodmap to map a mouse button as an arbitrary keyboard button? For example, I want to map Button 2 as keycode 168....or any other button I specify to any other keycode.

---

### Post by tweedledee on 2006-12-13
> **kobewan said:**
> Can you possible explain how to do this, or even how to begin? I want to somehow set up xbindkeys to make it so that holding down Button 8 will continuously scroll down (Button 5). Unfortunately, I cannot figure out how to make xbindkeys repeat an event for as long as a button is held down, it only does the event once. Right now I just have it scroll down three times, and keep pressing it. An idea I have for this, but am unable to implement, is to create a script that will send an infinite number of button 5 events with a short delay, and have it execute when button 8 is pressed. Then, when button 8 is releases, the xbindkeys will kill the script. Would that even work?
Without having actually tried it, you've outlined the approach I was thinking of.  Basically, you could use the approach I've described for the double-click, only instead of use xte to send button 1, send a scroll event (i.e., the button mapped to the z-axis in xorg.conf).  Your xbindkeysrc would look something like this:
```
"~/.scrollscript &"
b:8
"~/.scrollscriptkill &"
b:8 + Release
```
You've then need a .scrollscript, which could look something like this:
```
#!/bin/bash
setenv SCROLLSCRIPTVALUE=0
while [ $SCROLLSCRIPTVALUE -eq 0 ]
do
    xte 'mouseclick Y'
    sleep 0.1
done
```
Changing 0.1 to match your desired speed, and 'Y' to match the appropriate button.  Here I'm using an environment variable to control the loop, so changing the value of SCROLLSCRIPTVALUE in .scrollscriptkill should stop the loop.  I'm sure there is a more graceful way to handle that, but the loop should work.  There is probably discussion of this in some of the threads about controls for Logitech mice as well.  If you're unfamiliar with bash scripts, a quick Google search on "bash shell script" turns up a bunch of guides.

EDIT: The method described does not quite work (at least not for mouse buttons), see the next post for a better implementation.

> **kobewan said:**
> Also, is there any way to use xmodmap to map a mouse button as an arbitrary keyboard button? For example, I want to map Button 2 as keycode 168....or any other button I specify to any other keycode.
Not using xmodmap.  It should be possible using xbindkeys & xvkbd - use xbindkeys to trap the button event and send the desired keycode to xvkbd (or xte, actually, which also handles keyboard events).  What you'd probably need to do is send the whole sequence of keys you'd ordinarily press (i.e., ctrl+shift+u, ctrl+shift+#, ctrl+shift+#, etc.) to type a unicode character not available on the keyboard.  If you don't know the  relevant unicode, you can find it in the character map (you probably are looking for something in the Latin-1 Supplement block - select View -> By Unicode Block, then the Latin supplement group & scroll down to find it).

Post if you can either of these to work, especially the last - while I haven't read every post on this subject, that seems like an unusual (but clever, for mice with a huge number of buttons) use for a button.

---

### Post by kobewan on 2006-12-14
Alright, after trying out a bunch of things, as well as receiving several blinding flashes of the obvious, I have recorded the following results:-

Unfortunately the cruise button doesn't work properly as described above. It seems that xbindkeys is not able to properly handle button releases, and can't map an action to a button and its release if the button sends mouse events while pressed. It works fine if you map the script's kill to a different button, but that's not quite the point. 

However : although a button release can't be mapped to kill the script if said button is sending another mouse button, it maps just fine if button in question is sending keyboard events. I'm using the same method to make the volume up and volume down buttons on my mouse repeating, and it works just fine. Now, you'd think that immediately after find this out, I would figure out how to do it. Unfortunately, it took me several hours (and a few games of Super Smash Brothers) before nearly being blinded by the obvious ; map the mouse button to send key Down, instead of mouse Scroll Down. Granted, this won't work in all the same places, but for general use it should be fine (it will scroll the browser window, the Agrekator window and PDFs.  So I created a simple script in my home directory, called .scrolldown, containing:

```
#!/bin/bash
#
DO=1000000

for ((a=0; a < DO ; a++))  # do the loop number of times that is in DO
do
  /usr/bin/xte 'key Down'
  sleep 0.15
done     
```  

Then, I put this into the xbindkeys configuration file:

```
# scroll down
"~/.scrolldown"
   b:8

# kill scroll down
"killall .scrolldown"
   release + b:8   
```                  

Also, I've figured out how to make a "modifier" button. It doesn't work if you simply try to simply map a modifying key (down on press, up on release) on a button as again 'Release + b:*' wouldn't work properly. So I mapped this to button 17:

```
# button becomes modifier Alt+Control (m:0xc)
"/usr/bin/xte 'keydown Alt_R' 'keydown Control_R'; sleep 1 ; /usr/bin/xte 'keyup Alt_R' 'keyup Control_R'"
  b:17
```

It works like this : hit the modifier button and then hit a different button within 1 second to generate a different event. The best part about the way that it is set up is that you could even set up a button to be a kind of modifier toggle, so that hitting it once makes it send mod1+event, hitting it twice sends mod2+event, three times sends mod3+event etc. All you have to do is something like this : the first time you hit modifier button (button 17 for me) it sends 'keydown Alt+Ctrl' for one second. Hitting Button17 within that one second will make it send 'keyup Alt' followed by 'keydown Ctrl+Shift' for one second.  This means that you can create a pretty much infinite number of keys (or at least more keys than you can keep track of). 

An example of how this is useful in my current configuration: mod + the Volume Down button I mentioned above sends the mute button. Another way that it could be useful is to basically create different xbindkeys profiles for different applications. Hit mod twice, and then change your profile depending on what button you press (for example, a seperate amaroK profile could be quickly mapped by hitting Mod2+Button8). This would probably be even cooler with an on screen display, and I'm looking into that right now...it should be fairly easy to implement using OSD programs from Synaptics.

It's for reasons like this that Linux is so awesome, and really shows the power of it. Sure, doing things like this might not matter to your average Windows user, but I would've killed for this kind of functionality for Windows. On top of that, I'm sure that this is only scratching the surface of what can be done ; I only started using Linux about 2-3 weeks ago. When I was switching, the thing that I thought I would miss the most would be my mouse's extra keys (I was using Setpoint, hacked with uberOptions to make almost anything configurable). Now, if I have to switch back to Windows the thing that I will miss the most would be my mouse's configurability. I can definitely do so much more than I could come close to with Windows. 

Also, I don't need to "use xmodmap to map a mouse button as an arbitrary keyboard button" anymore. I originally wanted to do it because I didn't like xbindkeys very much, due to a few shortcomings like not properly catching button releases and not having any autorepeat setting (also because xvkbd is one seriously strange piece of software, only doing what it wants to do. xte is so much better than it.) Unfortunately, all other key binding applications that I found only worked for keyboard events, and they detected them using keycodes. This would mean that remapping a mouse button to a key would in xbindkeys would not work, and would also not get around the above problems. Fortunately, I've pretty much been able to work around those problems now.  I would still look over any alternative I could find, since it would be less annoying and time consuming, but I'm loving my mouse right now.

---

### Post by tweedledee on 2006-12-15
> **kobewan said:**
> Alright, after trying out a bunch of things, as well as receiving several blinding flashes of the obvious, I have recorded the following results:-

Unfortunately the cruise button doesn't work properly as described above. It seems that xbindkeys is not able to properly handle button releases, and can't map an action to a button and its release if the button sends mouse events while pressed. It works fine if you map the script's kill to a different button, but that's not quite the point. 

I'd just discovered the problem of the "release won't kill" as well, trying to do something entirely unrelated, and have made a note in my previous post.  However, you seem to have found an extraordinarily clever use of your mouse, I'm impressed.  I agree with you - I'm finding the customizability of my mouse much superior to Windows (which I have completely dropped except for 2 programs that I can't for research purposes), and I'm finding xte much more reliable and easier to use than xvkbd.  Supposedly they make use of the same library for communicating events, but xte is much cleaner for this purpose, plus you can send mouse events.

Since you have obviously taken this further than I have, if you have a chance it may be worth trying to get my initial steps with your supplements into the wiki; I don't anticipate having time for that any time soon.

---

### Post by kobewan on 2006-12-15
I may look into updating the wiki, but before that I want to configure it to perfection and I'm unfortunately still a couple of steps off. I'm not going to be able to figure these things on my own though, I've been trying for a long time now. In order of difficulty, easiest first:

1. Setting up an OnScreen Display : *solved*

2. Real, application-specific settings. Right now,  I've created a few different settings files for xbindkeys, and keep a drawer on my panel with the icons of 5 or 6 different apps in it. Whenever I want to change my bindings, I just select the appropriate icon. That runs a script which kills the open xbindkeys and tells it to restart using that apps settings 

Although this works reasonably well, I think it should be possible to do better than this. I was using [devilspie]("http://freshmeat.net/projects/devilspie/") yesterday, and it has pretty good window matching capabilities. Basically, I want a program that can do something like this:

if (application name = Firefox) and (focused = true) then (*run command*). 

I think programs like this *should* exist, but I haven't had any success in finding anything.

3. Setting sensitivity of second mouse : based on the information that I've found, I think this might not even be possible. I'm using an IBM Thinkpad, and my eraser nub/mouse thing in the middle of the keyboard is set as my primary mouse. Using the 'Mouse' applet in Gnome Control Center as well as 'xset m'  in the terminal only change the setting for my eraser nub. My Logitech mouse has a higher acceleration than I would like, but I am unable to change it. Setting the resolution in lomoco doesn't help either.

---

### Post by paridoth on 2006-12-17
i installed the listed programs via apt, and created the xbindkeysrc, editing it so that i can map my two side buttons to use them as back and forward buttons in Firefox and nautilus, however after starting xbindkeys -n -v and pressing the "back button" on my mouse i get the following output.

```
paridoth@paridoth-desktop:~$ xbindkeys -n -v
displayName = :0.0
rc file = /home/paridoth/.xbindkeysrc
rc guile file = /home/paridoth/.xbindkeysrc.scm
getting rc guile file /home/paridoth/.xbindkeysrc.scm.
WARNING : /home/paridoth/.xbindkeysrc.scm not found or reading not allowed.
2 keys in /home/paridoth/.xbindkeysrc

min_keycode=8     max_keycode=255 (ie: know keycodes)
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]" &"
    m:0x0 + b:8   (mouse)
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]" &"
    m:0x0 + b:9   (mouse)
starting loop...
Button press !
e.xbutton.button=8
e.xbutton.state=16
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]" &"
    m:0x0 + b:8   (mouse)
Start program with fork+exec call
Catch CHLD signal -> pid 7349 terminated
Button release !
e.xbutton.button=8
e.xbutton.state=16
```

and it is not working, i'm sure i missed something in your tutorial, but i'm not sure what it is.

---

### Post by tweedledee on 2006-12-20
> **paridoth said:**
> i installed the listed programs via apt, and created the xbindkeysrc, editing it so that i can map my two side buttons to use them as back and forward buttons in Firefox and nautilus, however after starting xbindkeys -n -v and pressing the "back button" on my mouse i get the following output.

Try these solutions in your xbindkeys.src, in the order listed (assuming the previous step didn't work):

1) Change your "left" and "right" to "Left" and "Right" (capital first letters).
2) Try adding " + Release" to the b:8 & b:9 lines.
3) Install xautomation, and replace your xvkbd lines with these:
```
"/usr/bin/xte 'keydown Alt_L' 'key Left' 'keyup Alt_L' &"
b:8
"/usr/bin/xte 'keydown Alt_L' 'key Right' 'keyup Alt_L' &"
b:9
```

---

### Post by tweedledee on 2006-12-20
> **kobewan said:**
> 2. Real, application-specific settings. Right now,  I've created a few different settings files for xbindkeys, and keep a drawer on my panel with the icons of 5 or 6 different apps in it. Whenever I want to change my bindings, I just select the appropriate icon. That runs a script which kills the open xbindkeys and tells it to restart using that apps settings 

Although this works reasonably well, I think it should be possible to do better than this. I was using [devilspie]("http://freshmeat.net/projects/devilspie/") yesterday, and it has pretty good window matching capabilities. Basically, I want a program that can do something like this:

if (application name = Firefox) and (focused = true) then (*run command*). 

I think programs like this *should* exist, but I haven't had any success in finding anything.

I haven't tried, but looking at devilspie suggests to me you could implement this behavior, although it'd take some work.  Basically, have each mouse button map to a script.  In that script, use devilspie to get the focused application name, and then select a command to send to xte from that information.  In effect, the construct you describe, only self-implemented as a shell script.  I may have some time to play with that idea in a few days, if you haven't succeeded before then.

> **kobewan said:**
> 3. Setting sensitivity of second mouse : based on the information that I've found, I think this might not even be possible. I'm using an IBM Thinkpad, and my eraser nub/mouse thing in the middle of the keyboard is set as my primary mouse. Using the 'Mouse' applet in Gnome Control Center as well as 'xset m'  in the terminal only change the setting for my eraser nub. My Logitech mouse has a higher acceleration than I would like, but I am unable to change it. Setting the resolution in lomoco doesn't help either.

I unfortunately agree - as far as I can tell this is impossible.  I have seen no indication that you can truly configure two mice independently.  Although some people have suggested you can do so if your laptop built-in mouse works with the Synaptics driver, I've not found this to be the case (perhaps because even though mine is recognized as a Synaptics Touchpad, it is actually just an eraser nub).  I've not even found a good way to set my USB mouse as left-handed and my eraser nub as right-handed, because they share the same xmodmap.  I even tried remapping my "scroll" buttons for my laptop using xbindkeys/xte to be buttons 1 & 3, but have had only mixed success.

---

### Post by paridoth on 2006-12-21
capatalizing the leters did it thanks so much =D

---

### Post by kobewan on 2006-12-21
I've been a little busy recently, but I basically decided to give up the idea of application specific settings. Although I know that it should be possible, I can't find any program that will get the information. devilspie can only set focus to a window, it can't actually check if the window is focused. I'm pretty sure that nobody has implemented the simple ability to check which window is focused (even though it should be technically possible) under Metacity. It's not a huge deal, and I decided that it was really not worth the time that I was spending on it. 

On an unrelated note, for some reason xbindkeys decided to not let me switch workspaces with my mouse anymore. It used to work before, and now it suddenly doesn't even though I didn't change anything. When Alt+Control+Right (or Left) is mapped to a keyboard key, there is no problem. However, when I map it to a mouse button, xev shows that the 'Right' button is not being sent, for whatever reason...

---

### Post by tweedledee on 2006-12-22
> **kobewan said:**
> I've been a little busy recently, but I basically decided to give up the idea of application specific settings. Although I know that it should be possible, I can't find any program that will get the information. devilspie can only set focus to a window, it can't actually check if the window is focused. I'm pretty sure that nobody has implemented the simple ability to check which window is focused (even though it should be technically possible) under Metacity. It's not a huge deal, and I decided that it was really not worth the time that I was spending on it. 

It appears that the library libwnck is the interface required to get at the appropriate information.  While devilspie makes use of that library, it doesn't provide a means for doing what you describe.  I'd write my own front-end to handle calls to libwnck, except I'm useless for C programming, and don't have the time to learn enough to get a reliable interface.  I found a variety of programs that almost work, but nothing that just returns the name of the focused window for another script/program to make use of.  Until someone writes something like that, I think application-specific settings are not possible, except as you've already described.

> **kobewan said:**
> On an unrelated note, for some reason xbindkeys decided to not let me switch workspaces with my mouse anymore. It used to work before, and now it suddenly doesn't even though I didn't change anything. When Alt+Control+Right (or Left) is mapped to a keyboard key, there is no problem. However, when I map it to a mouse button, xev shows that the 'Right' button is not being sent, for whatever reason...

I haven't encountered that, though I have seen that xbindkeys is a little finicky with mouse buttons.  For example, while I have no trouble at all mapping an arbitrary button to a "double click," I can't seem to get it to reliably remap an arbitrary button (outside of 1, 2, or 3) to be the "left click" - sometimes it works and sometimes it doesn't.  It's a little frustrating, actually - I know all the tools are available and ALMOST work as I want them, but not quite close enough - and since it's all coded in C, the "go write your own program" solution doesn't work in this case (though I've had to do that often enough).

---

### Post by bsalt on 2007-01-05
I also have a Marble Mouse, but when I entered

xmodmap -e "pointer = 1 2 3 4 5 8 9 6 7"

the up and down arrows began acting as forward and back buttons - and in my xorg.conf file, the zaxis buttons are the default "6 7".

What's up with this?

---

### Post by bsalt on 2007-01-05
Ok, so I was messing around with xmodmap, and I typed in:

xmodmap -e "pointer = 1 2 3 8 9 6 7 4 5 10 11"

and now they are acting as scroll buttons.

---

### Post by Absurd on 2007-01-08
Would it be possible to map a minimize event to mouse button 8?

or

should I instead set a keyboard shortcut to minimize a window then map that shortcut to button 8? For example, if Alt_R+Control_R+Down minimizes a window, will it work if I mapped those keys to button 8 in my .xbindkeysrc file?

---

### Post by kobewan on 2007-01-09
> **Absurd said:**
> Would it be possible to map a minimize event to mouse button 8?

or

should I instead set a keyboard shortcut to minimize a window then map that shortcut to button 8? For example, if Alt_R+Control_R+Down minimizes a window, will it work if I mapped those keys to button 8 in my .xbindkeysrc file?

It should work if you use xte (from xautomation) for sending events. xvkbd might have some problems with it.

---

### Post by Absurd on 2007-01-09
What would the sintax look like? I tried the second option (setting a keyboard shortcut) and that did not seem to work.

---

### Post by tweedledee on 2007-01-09
> **Absurd said:**
> What would the sintax look like? I tried the second option (setting a keyboard shortcut) and that did not seem to work.

If you have a keyboard shortcut set, it should work.  I'm using Ubuntu, and metacity's default shortcut to minimize is Alt+F9.  If I enter the following into .xbindkeysrc, button 2 will minimize the active window:
```
"/usr/bin/xte 'keydown Alt_L' 'key F9' 'keyup Alt_L' &"
b:2
```
Make sure you've killed & restarted xbindkeys after you modify .xbindkeysrc, though, it doesn't re-read .xbindkeysrc.  For the keys you've suggested, your code would be:
```

"/usr/bin/xte 'keydown Alt_R' 'keydown Control_R' 'key Down' 'keyup Control_R' 'keyup Alt_R' &"
b:2
```

Make sure you have the "keyup" statements, otherwise your Alt & Control keys will be down until you physically press them.

---

### Post by Absurd on 2007-01-09
Thank you. I didn't know that the key entries ('keydownn Alt_R' 'keydown Control_R' etc) had to be monospaced.

---

### Post by Maki_doda on 2007-01-16
this doesent work for me

---

### Post by tweedledee on 2007-01-16
> **Maki_doda said:**
> this doesent work for me

If you provide a little detail about your hardware and what you've tried, I can try to provide additional help.

---

### Post by tweedledee on 2007-01-23
For the curious, I've modified the original post to include what appears to be the most-requested behavior, forward & back buttons, as a quick fix in xorg.conf, as this:
edit /etc/X11/xorg.conf in the mouse section, and add the following two lines:
```
Option "Buttons" "7"
Option "ButtonMapping" "1 2 3 6 7"
```  Make sure to backup the file first, and restart X to have the effect take place.

This won't work for all mice, and only works for a specific behavior, but may help out some people who want a quick fix.

---

### Post by tweedledee on 2007-01-31
Another update - see this thread for those interested in application-specific mouse (or keyboard) settings: [http://www.ubuntuforums.org/showthread.php?p=2089118](http://www.ubuntuforums.org/showthread.php?p=2089118) .

---

### Post by tweedledee on 2007-02-07
One more (final?) update, in case someone else has had the frustration I have with using an external mouse left-handed and therefore having a messed up built-in laptop mouse when the external mouse is disconnected (or otherwise wants different behavior when a mouse is/isn't connected): see this thread: [http://www.ubuntuforums.org/showthread.php?t=350464](http://www.ubuntuforums.org/showthread.php?t=350464).

---

### Post by mattym on 2007-03-11
Thanks for the post tweedledee, this worked great! :D

---

### Post by Demogorge on 2007-03-18
The behavior of the double-click here was a little frustrating for me. The Logitech Windows drivers that I am used to would double-click on button **press** and not button release. I found that I missed the double-click a lot because I had moved the mouse off the icon by the time the specified button was released.

I found an easy way to fix this. Simply replace this:

```
"/usr/bin/xte 'mouseclick 1' 'mouseclick 1' &"
b:Y + Release
```

With this:

```
"/usr/bin/xte 'mouseup Y' 'mouseclick 1' 'mouseclick 1' &"
b:Y
```

Replace "Y" with the button number you are mapping. This sends a button release event which allows the double-click to pass through. I find the double-clicking to *seem* a lot more responsive now since the action initiates right when you press the button.

---

### Post by tweedledee on 2007-03-18
> **Demogorge said:**
> The behavior of the double-click here was a little frustrating for me. The Logitech Windows drivers that I am used to would double-click on button **press** and not button release. I found that I missed the double-click a lot because I had moved the mouse off the icon by the time the specified button was released.

I've noted your tweak, thanks for the feedback.

---

### Post by bryan.taylor on 2007-03-19
I liked this howto because it allowed me to get the back/forward buttons working in firefox AND nautilus.  However, I missed imwheel's ability to specify different key events for different applications/windows.  So I decided to write my own hack to solve this problem.

First I wrote a little program to query window information.  If anyone is interested and know of a free file storage location I'll upload the program.

For the curious/ambitious, the source is posted at the end.  The name of the program is 'qawn' (Query Active Window Name).

So this is what my .xbindkeysrc looks like:
```
# Back Button
"/usr/local/bin/mouse-back-button.sh"
   b:8
# Forward Button
"/usr/local/bin/mouse-forward-button.sh"
   b:9
```

And here is the mouse-back-button.sh script:
```
#!/bin/bash
#
# generate key events based on window criteria

# Control_L + Page_Up
qawn -p | egrep -i "gnome-terminal"
if [ $? -eq 0 ]; then
	/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Page_Up]" &
	exit 0
fi

# Default: Alt_L + Left
/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]" &
exit 0
```

The mouse-forward-button.sh looks identical except for the key events that it generates.  So now when I want to bind the back/forward buttons for a new application I just have to edit these two scripts.  It's pretty nifty because I can have my cake (firefox + nautilus) and eat it too (gnome-terminal et al). :)



Here is the source:
```
#include <string.h>
#include <stdlib.h>
#include <stdio.h>
#include <X11/Xlib.h>
#include <X11/Xutil.h>

void usage(char *progname)
{
	char *shortname = rindex(progname, '/');
	if (!shortname) {
		shortname = progname;
	}
	else {
		shortname++;
	}
	printf("%s <options>\n", shortname);
	printf("  -p  --process-name   Query for the active window's process name\n");
	printf("  -c  --process-class  Query for the active window's process class\n");
	printf("  -n  --name           Query for the active window's name (title)\n");
}


typedef enum {
	PROCESS_NAME,
	PROCESS_CLASS,
	NAME,
	UNKNOWN
} QUERY_TYPE;

int main(int argc, char **argv)
{
	if (argc != 2) {
		usage(argv[0]);
		exit(1);
	}

	QUERY_TYPE qt = UNKNOWN;
	if (!strcmp(argv[1], "--process-name") || !strcmp(argv[1], "-p")) {
		qt = PROCESS_NAME;
	}
	else if (!strcmp(argv[1], "--process-class") || !strcmp(argv[1], "-c")) {
		qt = PROCESS_CLASS;
	}
	else if (!strcmp(argv[1], "--name") || !strcmp(argv[1], "-n")) {
		qt = NAME;
	}

	if (qt == UNKNOWN) {
		usage(argv[0]);
		exit(1);
	}

	Display *display;
	char *envDisplay = getenv("DISPLAY");

	if (!envDisplay) {
		fprintf(stderr, "Unable to query DISPLAY environment variable!\n");
		exit(1);
	}
	display = XOpenDisplay(envDisplay);
	if (!display) {
		fprintf(stderr, "Unable to open display (%s)!\n", envDisplay);
		exit(1);
	}

	Window w;
	int rtr;
	XGetInputFocus(display, &w, &rtr);

	if (qt == PROCESS_NAME || qt == PROCESS_CLASS) {
		XClassHint xch;
		Status rc = XGetClassHint(display, w, &xch);
		if (rc == BadWindow) {
			fprintf(stderr, "XGetClassHint returned BadWindow error!\n");
			exit(1);
		}
		// output what we've found
		if (qt == PROCESS_NAME && xch.res_name) {
			printf("%s\n", xch.res_name);
		}
		else if (xch.res_class) {
			printf("%s\n", xch.res_class);
		}

		if (xch.res_name) {
			XFree(xch.res_name);
		}
		if (xch.res_class) {
			XFree(xch.res_class);
		}
	}
	else if (qt == NAME) {
		char *name;
		Status rc = XFetchName(display, w, &name);
		if (rc == BadWindow) {
			fprintf(stderr, "XFetchName returned BadWindow error!\n");
			exit(1);
		}
		// output what we've found
		if (name) {
			printf("%s\n", name);
			XFree(name);
		}
	}
	
	// cleanup
	XCloseDisplay(display);

	return 0;
}
```

Here is the makefile:
```
all:
	g++ main.cpp -g -o qawn `pkg-config --cflags --libs vte`

clean:
	rm -f qawn

install: all
	cp -f qawn /usr/local/bin

uninstall:
	rm -f /usr/local/bin/qawn
```

---

### Post by tweedledee on 2007-03-19
Your application specific settings solution is both easier and more complicated than this alternative: [http://www.ubuntuforums.org/showthread.php?t=380927](http://www.ubuntuforums.org/showthread.php?t=380927) (which was only recently added to the end of the original post as a link).  Whichever approach works best for you.

---

### Post by bryan.taylor on 2007-03-20
Either way works, but it's good to have options.  If I have time I might think up a way to clean mine up some more so it's easier to manage (e.g. remove the bash part).  It would be a good way to learn some linux GUI programming too. ;)

---

### Post by tweedledee on 2007-03-20
> **bryan.taylor said:**
> Either way works, but it's good to have options.  If I have time I might think up a way to clean mine up some more so it's easier to manage (e.g. remove the bash part).  It would be a good way to learn some linux GUI programming too. ;)

Agreed - kind of like having your cake and eating it, but after learning to decorate it first.  One of my goals is to write a GUI to assign functions to buttons as well (being a highly popular request on these boards), but first I need to invent a time machine or a way to extend holidays....  Maybe one of these days, if someone else doesn't do it first.  If you do put something together, be sure to post it somewhere, and I'll point the original post to it.

---

### Post by zhinker on 2007-07-07
This looks like an excellent post, but I'm having trouble getting it to do what I want.

I've got a three button mouse and I'm trying to add buttons 6 & 7 to it by moving the scroll wheel up and down (values 4 & 5)while holding down the right click button (3).  

Is there any way to do this?

---

### Post by zhinker on 2007-07-07
Here's the code I'm using to try to add buttons 6 & 7 to my mouse, I put it in the .xbindkeysrc file :

```
"/usr/bin/xte 'mouseclick 6' &"
b:1 / 4 + Release

"/usr/bin/xte 'mouseclick 7' &"
b:1 / 5 + Release
```

When I try to press mouse button 1 + 4, it seems to go into and endless loop outputting both buttons 6 and 7.  This is part of the looping terminal output:

```
Catch CHLD signal -> pid 11373 terminated
"/usr/bin/xte 'mouseclick 7' &"
    m:0x0 + b:1   (mouse)
Start program with fork+exec call
Button release !
e.xbutton.button=1
e.xbutton.state=272
"/usr/bin/xte 'mouseclick 1' &"
    Release + m:0x0 + b:1   (mouse)
Start program with fork+exec call
Catch CHLD signal -> pid 11375 terminated
Catch CHLD signal -> pid 11376 terminated
Button press !
e.xbutton.button=1
e.xbutton.state=16
"/usr/bin/xte 'mouseclick 6' &"
    m:0x0 + b:1   (mouse)
Start program with fork+exec call
```

Any idea what I can do to fix this?

---

### Post by bryan.taylor on 2007-07-07
My only idea was to try:
```
"echo 1 + 8"
b:1 + b:8 + Release
```

but what happens here is that "1 + 8" is only output when I press button 8.  This makes me think that xbindkeys only understands buttons and modifiers.  It reads b:1, then, since both are buttons, it overwrites it with b:8.  I haven't found any helpful info online, so maybe it's just not possible with xbindkeys?

---

### Post by tweedledee on 2007-07-09
> **zhinker said:**
> This looks like an excellent post, but I'm having trouble getting it to do what I want.

I've got a three button mouse and I'm trying to add buttons 6 & 7 to it by moving the scroll wheel up and down (values 4 & 5)while holding down the right click button (3).  

Is there any way to do this?

As already pointed out, there is apparently not a way to make xbindkeys recognize two button events at once; it really is much better at keyboard events.  Imwheel or some other custom program suggested in the various other mouse guides may do this.  Alternatively, take a look at post # 6, where Kobewan explains how to set up modifier buttons.  It wouldn't be a "mouse-only" solution, but it would allow you to simulate additional buttons.

---

### Post by tweedledee on 2008-01-19
I have revised and updated this guide, especially to include the "evdev" driver for mice with many buttons not recognized by the standard drivers.

---

### Post by gubbas on 2008-02-13
I have the Logitech G5 and I can not get the thumb button to work at all.  When I use xev to see what the button is it reports the following for each button:

Left = button 1
Middle = button 2
Right = button 3
Roll up = button 4
Roll dn = button 5
Thumb = button 2 <<< !

Shouldn't my thumb button be 6?  How can I change this?

Gub

---

### Post by tweedledee on 2008-02-13
> **gubbas said:**
> I have the Logitech G5 and I can not get the thumb button to work at all.  When I use xev to see what the button is it reports the following for each button:

Left = button 1
Middle = button 2
Right = button 3
Roll up = button 4
Roll dn = button 5
Thumb = button 2 <<< !

Shouldn't my thumb button be 6?  How can I change this?

Gub

If you haven't already, try different protocols and/or evdev.  Doubling up like that occurs because either the button sends a singal the protocol doesn't handle well (in my experience, often with IMPS/2, less often with ExplorerPS/2, and never with evdev), or the mouse is in fact generating the same signal for two different buttons (this happens with some buttons on the Logitech MX1000, for instance).  However, in the latter case, Logitech mice seem to generate two events, only one of which may be identical to something else - when this is happening, only evdev can properly handle the button.

You can also look at btnx, which is a project specifically to help with many-button mice and reduce the effort in setting them up.  I've not yet tried it, but there is a thread about it in the forum and you can download it from the web (it is not yet in the repositories).

---

### Post by gubbas on 2008-02-13
Thanks for sending me down the right path!  evdev worked perfectly for isolating the buttons on my G5 Logitech mouse.  I used the following page to then completely configure all the buttons.  Success!  Thanks again!

[http://ubuntuforums.org/showthread.php?t=219894](http://ubuntuforums.org/showthread.php?t=219894)

---

### Post by blazoner on 2008-04-06
> **tweedledee said:**
> You can also look at btnx, which is a project specifically to help with many-button mice and reduce the effort in setting them up.  I've not yet tried it, but there is a thread about it in the forum and you can download it from the web (it is not yet in the repositories).
tweedledee, I honestly cannot recommend [btnx and btnx-config]("http://ubuntuforums.org/showthread.php?t=455656") highly enough. Both are currently on release 0.4.8, and are very stable. Although btnx-config was initially designed for 1 or 2 mouses, it now works with virtually all USB mouses, and has a laundry list of additional features, including:
```
revoco (for functionality with MX and VX Revolution)
multiple configurations
command execution
hot plugging included
```Most of the things included in this tutorial can be accomplished through btnx.
I sort of adopted this project, and love to see when it changes for the better. Please feel free to come take a look. Another informed opinion is always welcome!

---

### Post by tweedledee on 2008-04-06
> **blazoner said:**
> tweedledee, I honestly cannot recommend [btnx and btnx-config]("http://ubuntuforums.org/showthread.php?t=455656") highly enough. Both are currently on release 0.4.8, and are very stable. Although btnx-config was initially designed for 1 or 2 mouses, it now works with virtually all USB mouses, and has a laundry list of additional features, including:
```
revoco (for functionality with MX and VX Revolution)
multiple configurations
command execution
hot plugging included
```Most of the things included in this tutorial can be accomplished through btnx.
I sort of adopted this project, and love to see when it changes for the better. Please feel free to come take a look. Another informed opinion is always welcome!

Actually, since the time I last updated this, I have tried btnx.  Personally I prefer the manual configuration, especially since btnx lacks the ability to trap button+modifier (e.g., alt+button 4), which I make use for my trackball (4 buttons, 8 functions).  I have tried btnx for my wife's mouse, which isn't as demanding a setup, and haven't had any great success (compared to manual configuration).  I agree that for "basic" configuration, btnx is probably the way to go for most people, but it has a long way to go to replace everything.  Btnx still needs more polish before I would advocate it even for standard users, especially with regards to handling command execution and error messages.

---

### Post by quadra on 2008-12-06
Btnx is apparently broken in Ubuntu 8.10.
This thread is a bit cluttered by now. If you're just interested in the **double click** on the middle button, check this short version: **[http://ubuntuforums.org/showthread.php?t=1003720](http://ubuntuforums.org/showthread.php?t=1003720)**

---

### Post by deFlNE on 2009-01-02
Hey.

Thanks for your howto.

I try to bind Alt key for a mouse button, to move and resize windows at KDE, but I' ve got some problems. Try to do it like this in my ~/.xbindkeysrc:

```

"/usr/bin/xte 'keydown Alt_L'"
  b:8
"/usr/bin/xte 'keyup Alt_L'"
  Release + b:8

```

It works like that. I press my mouse button 8 and Alt is pressed constantly also when I relise the mouse button, so I have to switch it by pressing Alt on my keyboard. The realese binding for keup do nothing.

And I need, that it just work as a key on my keyboard. I press the modifier bind on my mouse button with some key, then realese it and it works in usual mode.

How that can be done?

---

### Post by tweedledee on 2009-01-02
> **deFlNE said:**
> Hey.

Thanks for your howto.

I try to bind Alt key for a mouse button, to move and resize windows at KDE, but I' ve got some problems. Try to do it like this in my ~/.xbindkeysrc:

```

"/usr/bin/xte 'keydown Alt_L'"
  b:8
"/usr/bin/xte 'keyup Alt_L'"
  Release + b:8

```

It works like that. I press my mouse button 8 and Alt is pressed constantly also when I relise the mouse button, so I have to switch it by pressing Alt on my keyboard. The realese binding for keup do nothing.

And I need, that it just work as a key on my keyboard. I press the modifier bind on my mouse button with some key, then realese it and it works in usual mode.

How that can be done?

What you are trying to do can't be done as you describe, due to some limitation (in xbindkeys and/or the mouse driver, I haven't spent the time to track it down).  There's a discussion of a related issue in some of the early posts.  What it boils down to is that you can't directly assign both a press and release event to a single button; the release event will be ignored.  To work around this, you'd need to trap only one of them, and have that call a script.  It would then be up to the script to determine whether it should send a "down" or "up" key signal, depending on some variable, current state of key, etc.

You could also try playing with the evdev driver, which does seem capable of the "press+hold, then release" type behavior.

Alternatively, there's a discussion in some of the earlier posts about "modifier keys" that result in a keypress for a fixed amount of time, but I don't know if that solution is appropriate for the situation you describe.

But my experience has been that the kind of behavior you want, where a mouse button substitutes for a single key (especially a modifier key) based on "click+hold" simply isn't worth the effort it would take to make it work.

---

### Post by unimatrix on 2009-06-24
> **bryan.taylor said:**
> My only idea was to try:
```
"echo 1 + 8"
b:1 + b:8 + Release
```

but what happens here is that "1 + 8" is only output when I press button 8.  This makes me think that xbindkeys only understands buttons and modifiers.  It reads b:1, then, since both are buttons, it overwrites it with b:8.  I haven't found any helpful info online, so maybe it's just not possible with xbindkeys?

I wanna know this too. I did it by a hacky workaround, explained on LQ: [http://www.linuxquestions.org/questions/linux-newbie-8/two-mouse-buttons-to-trigger-an-action-734917/](http://www.linuxquestions.org/questions/linux-newbie-8/two-mouse-buttons-to-trigger-an-action-734917/) but no answers for now. What we really need is to make one of the mouse buttons act as a modifier. So far nobody knows how to do it.

---

### Post by loomsen on 2009-06-26
This seems really hard to acomplish. I wasted some time searching for similar behavior as in opera. I use the buttons all the time, Sometimes even on other apps and then wonder :D When using midori for some reason, I trigger the menu at least every 5 seconds :D 

However, Opera too is only able to get events triggered in by holding the right button (this nonetheless is more than any other app provides)

This would add a whole new way to handle the Desktop in general, at least if you're a Notebookuser like I am without an extra keyboard. I'm adoring this so much, but even the compiz devs told me this is harder to accomplish than one would think.


-----   BUT   ----

Just read through this thread again, and this
```

"/usr/bin/xte 'mouseup Y' 'mouseclick 1' 'mouseclick 1' &"
b:Y
```
particular snippet kinda got some synapses connected and my old ideas revived. 
Isn't this what we're actually looking for, or more likely what keeps us from triggering button only gestures?

Problem: Klick recognized as Klick event, release not recognized so no way to get the time in between.
--> Isn't this the fix?
> Replace "Y" with the button number you are mapping. This sends a button release event which allows the double-click to pass through. I find the double-clicking to seem a lot more responsive now since the action initiates right when you press the button.

Just flushing my thoughts, I haven't really thought about it, so pls correct me if I'm wrong...

---

### Post by unimatrix on 2009-06-26
SOLVED:

Using [easystroke]("http://easystroke.wiki.sourceforge.net/") you are able to bind almost any mouse button combination to anything.

Goodbye xbindkeys!

---

### Post by loomsen on 2009-06-26
Really? Button only events? I stumbled upon easystroke a couple of times, but never figured out how to enable button only events.

---

### Post by unimatrix on 2009-06-26
> **loomsen said:**
> Really? Button only events? I stumbled upon easystroke a couple of times, but never figured out how to enable button only events.

YES, but you have to configure it right.
1) make sure "Ignore strokes leading to  advanced gestures" is checked
2) THEN go bind the keys (if you've already done so, you must REbind them).
3) The trick when binding is to make sure you're MOVING your mouse while you're binding the keys. A single number should show up in the Stroke column.

You will also want to disable "Show popups" and "Show OSD", and change the "Method to show gestures" to None.

---

### Post by soumo on 2009-07-20
Hi all, any help you can provide would be appreciated!

I am trying to get the scroll wheel working and have tried the xmodmap & xinput methods to set the keys, to no avail.

Here are some outputs that may be of use:

This is my button map from xinput get-button-map 6:
> 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 10  

cat proc/bus/input/devices:
> I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
U: Uniq=
H: Handlers=event1 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/devices/virtual/input/input3
U: Uniq=
H: Handlers=mouse0 event3 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=120013
B: KEY=400c 2002000 3803078 f810d001 feffffdf ffefffff ffffffff ffffffff
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/devices/platform/pcspkr/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/device:02/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: EV=3
B: KEY=3f000b 0 0 0 0 0 0 0

I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input9
U: Uniq=
H: Handlers=mouse2 event9 
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

I: Bus=0003 Vendor=0a5c Product=4502 Version=0111
N: Name="Broadcom Corp BCM2045B3 ROM"
P: Phys=usb-0000:00:1d.0-1.2/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.2/2-1.2:1.0/input/input12
U: Uniq=
H: Handlers=kbd event5 
B: EV=120013
B: KEY=10000 7 ff800000 7ff febeffdf f3cfffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=0a5c Product=4503 Version=0111
N: Name="Broadcom Corp BCM2045B3 ROM"
P: Phys=usb-0000:00:1d.0-1.3/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input13
U: Uniq=
H: Handlers=mouse1 event6 
B: EV=17
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3
B: MSC=10


I believe 
I: Bus=0003 Vendor=0a5c Product=4503 Version=0111
N: Name="Broadcom Corp BCM2045B3 ROM"
is my mouse connected via bluetooth.

xinput list:
> "Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"AT Translated Set 2 keyboard"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Broadcom Corp BCM2045B3 ROM"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Video Bus"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=5	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Broadcom Corp BCM2045B3 ROM"	id=6	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1


xinput list-props 6:
> Device 'Broadcom Corp BCM2045B3 ROM':
	Device Enabled (89):		1
	Evdev Axis Inversion (226):		0, 0
	Evdev Reopen Attempts (223):		10
	Evdev Axis Calibration (224):		
	Evdev Axes Swap (225):		0
	Evdev Middle Button Emulation (227):		2
	Evdev Middle Button Timeout (228):		50
	Evdev Wheel Emulation (229):		0
	Evdev Wheel Emulation Axes (230):		0, 0, 4, 5
	Evdev Wheel Emulation Inertia (231):		10
	Evdev Wheel Emulation Timeout (232):		200
	Evdev Wheel Emulation Button (233):		4
	Evdev Drag Lock Buttons (234):		0

xinput watch-props 6:
> Device 'Broadcom Corp BCM2045B3 ROM':
	Device Enabled (89):		1
	Evdev Axis Inversion (226):		0, 0
	Evdev Reopen Attempts (223):		10
	Evdev Axis Calibration (224):		
	Evdev Axes Swap (225):		0
	Evdev Middle Button Emulation (227):		2
	Evdev Middle Button Timeout (228):		50
	Evdev Wheel Emulation (229):		0
	Evdev Wheel Emulation Axes (230):		0, 0, 4, 5
	Evdev Wheel Emulation Inertia (231):		10
	Evdev Wheel Emulation Timeout (232):		200
	Evdev Wheel Emulation Button (233):		4
	Evdev Drag Lock Buttons (234):		0



"SynPS/2 Synaptics TouchPad"	id=7	[XExtensionPointer]
	Num_buttons is 12
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 1472
		Max_value is 5472
		Resolution is 1
	Axis 1 :
		Min_value is 1408
		Max_value is 4448
		Resolution is 1

xmodmap -pp:
> There are 32 pointer buttons defined.

    Physical        Button
     Button          Code
        1              1
        2              2
        3              3
        4              4
        5              5
        6              6
        7              7
        8              8
        9              9
       10             10
       11             11
       12             12
       13             13
       14             14
       15             15
       16             16
       17             17
       18             18
       19             19
       20             20
       21             21
       22             22
       23             23
       24             24
       25             25
       26             26
       27             27
       28             28
       29             29
       30             30
       31             31
       32             32


xinput query-state 6:
> 2 classes :
ButtonClass
	button[1]=up
	button[2]=up
	button[3]=up
	button[4]=up
	button[5]=up
	button[6]=up
	button[7]=up
	button[8]=up
	button[9]=up
	button[10]=up
	button[11]=up
	button[12]=up
	button[13]=up
	button[14]=up
	button[15]=up
	button[16]=up
	button[17]=up
	button[18]=up
	button[19]=up
	button[20]=up
	button[21]=up
	button[22]=up
	button[23]=up
	button[24]=up
	button[25]=up
	button[26]=up
	button[27]=up
	button[28]=up
	button[29]=up
	button[30]=up
	button[31]=up
	button[32]=up
ValuatorClass Mode=Relative Proximity=In
	valuator[0]=913
	valuator[1]=71

My xorg.conf has no mention of mouse:
> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	DefaultDepth	24
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection


If I use the xev command, in the event tester window, the three buttons are recognized as well as motion, but not the scroll wheel.

I have tried swapping 4 5 with every combination of 6 7, 7 8,...31 32 to naught.

Any ideas?

I'm using a rocketfish bluetooth optical mouse, model RF-BTMSE, the LR and middle (clipboard paste behaviour) buttons function well.

---

### Post by soumo on 2009-07-22
Ok, so I got it working, if anyone else needs a hint:
[http://ubuntuforums.org/archive/index.php/t-355695.html](http://ubuntuforums.org/archive/index.php/t-355695.html)

It has to do with a bluetooth not pairing correctly issue...

if anyone can figure out how to script this, that would be helpful...

---

### Post by chrisisbd on 2010-08-22
The double-click emulation described here no longer works in Ubuntu 10.04.

I have a logitech trackball with four buttons and I had it set up in 9.04 and 9.10 so that the fourth button emulated a double-click of button 1.  Exactly the same set up fails to work in 10.04.  I ahve tried regressing xbindkeys and xte to the previous versions but it still doesn't work.

Something in the 'insides' of 10.04 seems to have changed to break this.

---

### Post by tweedledee on 2010-08-22
> **chrisisbd said:**
> The double-click emulation described here no longer works in Ubuntu 10.04.

I have a logitech trackball with four buttons and I had it set up in 9.04 and 9.10 so that the fourth button emulated a double-click of button 1.  Exactly the same set up fails to work in 10.04.  I ahve tried regressing xbindkeys and xte to the previous versions but it still doesn't work.

Something in the 'insides' of 10.04 seems to have changed to break this.

An update to either Xorg or udev (I've not had time to investigate which) this spring caused some problems with this.  Specifically, the actions only seem to work when in conjuction with the release action (i.e., you can't force a button up and then double-click, so the triggers should all be B: ? + Release format), and some of the button numbering shifted around.

However, it should still be possible to get double-click and other triggers associated with buttons if you re-evaluate the numbering and always tie events to the release of a button rather than the click.  At least that's the case for my assorted computers and trackballs/mice.

---

### Post by chrisisbd on 2010-09-02
Thanks, I've added '+ Release' to my .xbindkeysrs file and now I have my double-click back, it feels a little odd working on button release but it's a whole lot better than not working at all.

Thanks again!

---

### Post by dargaud on 2012-04-26
I know this is an ancient thread, but there's plenty of great stuff in it. I have a slightly different problem: I'd like to eliminate multiple spurious clicks from the wheel buttons. 

It stated recently after an ubuntu update and now when I click the wheel button, I get 2 or 3 events at once. It makes straditional X11 copy/paste or opening links in new tabs next to impossible.

Anybody has an idea on how to eliminate multiple clicks from that button ?

---

### Post by tweedledee on 2012-04-27
> **dargaud said:**
> I know this is an ancient thread, but there's plenty of great stuff in it. I have a slightly different problem: I'd like to eliminate multiple spurious clicks from the wheel buttons. 

It stated recently after an ubuntu update and now when I click the wheel button, I get 2 or 3 events at once. It makes straditional X11 copy/paste or opening links in new tabs next to impossible.

Anybody has an idea on how to eliminate multiple clicks from that button ?

Sounds like a repeat timing issue, which apparently crop up from time to time with certain devices.  I don't have a solution, but I suggest you look for ways to control the timing or frequency of repeat clicks when holding down a button.  It may even be in a general mouse configuration tool.

---

### Post by artshark on 2012-04-29
can someone help me with xbindkeys? in windows my extra buttons are 4 and 5 but I cannot confirm this is such with xbindkeys. Does it have a discovery mode where I press a button and it reveals ID?

---

### Post by tweedledee on 2012-04-29
> **artshark said:**
> can someone help me with xbindkeys? in windows my extra buttons are 4 and 5 but I cannot confirm this is such with xbindkeys. Does it have a discovery mode where I press a button and it reveals ID?

xev does what you want.  Type xev in a terminal, then click the buttons inside the window that pops up; diagnostic information including which button # will appear in the terminal window.  It is part of the x11-utils package, and is probably installed on your system.

---

### Post by Elfy on 2012-06-29
This thread is closed. 
 
The information is now held on the community wiki at  
 
Thank you for your thread and the work you have done in keeping it current and of use to the community. 
 
A thread for discussion of the wiki can be found at  [http://ubuntuforums.org/showthread.php?t=2012401](http://ubuntuforums.org/showthread.php?t=2012401)
 
 
Support threads regarding the wiki and it's content should be created in a suitable forum.

---

