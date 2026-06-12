---
title: "HOW TO: Install Ubuntu on a HP TC1100 tablet pc"
date: 2007-09-30
forum: Tutorials
---

### Post by phenest on 2007-09-30
I just bought a 2nd hand HP TC1100 tablet pc, and have to say, I'm impressed. It came with a docking station (although I don't have much use for it), with a DVD/CDRW drive which can be removed and placed in an external USB caddy. I'd say this is one of the better designed tablets around (I also have a Fujitsu ST4110).

Ok. Down to business. This is what I have so far, and will keep this guide updated as more information arrives.

[SIZE="3"]**Ubuntu 7.04**[/SIZE]

After installing, everything pretty much works out of the box.

**nVidia**
Enable the NVIDIA driver from the Restricted Drivers Manager.

**xorg.conf**
Then you need to update the xorg.conf file:
```
sudo nano /etc/X11/xorg.conf
```
Edit the Device section and add:
```
Option    "RandRRotation"    "on"
Option     "NvAGP"     "1"
```
This enables rotation capabilities. The 2nd line is to help suspend work properly.
Then edit the InputDevice  section- Driver wacom - Identifier stylus add:
```
Option    "Button2"    "3"
```
This enables right-clicking with the pen button.

**Rotation**
You will need to install wacom-tools:
```
sudo apt-get install wacom-tools
```
You will need a script and map it to a key. The script:
```
#!/bin/sh

# Change System Input orientation for Tablet Mode
# Depends on wacom-tools from repo

orientation=`/usr/bin/xrandr --query | /bin/grep "Current rotation" | /usr/bin/awk '{print $4}'`
if [ "$orientation" = "normal" ]; then
	/usr/bin/xrandr -o left
	/usr/bin/xsetwacom set stylus Rotate CCW
else
	/usr/bin/xrandr -o normal
	/usr/bin/xsetwacom set stylus Rotate none
fi
```

Save it as rotate.sh and put into the /usr/bin/ directory. The TC1100 has a 'Q' key on its edge. In Windows, this activates a popup menu, but the menu doesn't exist in Ubuntu. So we will use it for screen rotation. To map the key, open the Configuration Editor and browse to /apps/metacity/keybindings_commands. Edit command_1 (or the 1st available command) enter: sh /usr/bin/rotate.sh . Then browse to /apps/metacity/global_keybindings and edit the run_command_1 with 0x9f (or press the 'Q' button.

**OSK: On Screen Keyboard**
[Cellwriter]("http://risujin.org/cellwriter/") version 1.2.5 is the choice here for both OSK and hand-writing recognition. Under System>Preferences>Accessibility>Assistive Technology Preferences,  you need to check the following:
Enable assistive technologies
Password dialogues as floating windows (the on-screen keyboard can be used for root access)
Start on-screen keyboard at log in

I did find a problem with the pen operating erratically during login where the cursor would not follow the pen and kept jumping to the lower-right of the screen. To stop this behaviour, uncheck 'Enable accessible login' in System>Administration>Login Window - Accessibility tab. This is probably a bug in the wacom driver.

To enable Cellwriter at login:
```
sudo nano /etc/X11/gdm/Init/Default
```
At the bottom of the script, add:
```
cellwriter --keyboard-only --window-y=600 &
```
... so it reads ...
```
fi
cellwriter --keyboard-only --window-y=600 &
exit 0
```

If you wish to use xvkbd at login instead:
```
sudo apt-get install xvkbd
```
... then enter ...
```
xvkbd -geometry -300-100 -no-keypad &
```
...or onboard:
```
sudo apt-get install onboard
```
...then enter...
```
onboard &
```
... into the /etc/X11/gdm/Init/Default file instead of cellwriter.
**Kubuntu users: Put either onboard or xvkbd into the /etc/kde3/kdm/Xsetup file.**
**Also note: Login style must be changed from Themed to Plain in System>Administration>Login Window - Local tab**
**Another note: If you enable automatic login, do NOT amend this file as you will end up with 2 instances of the OSK!**

**Sleep & Suspend**
To make sleep and suspend work, follow the instructions [here]("https://help.ubuntu.com/community/NvidiaLaptopBinaryDriverSuspend")

**Miscellaneous**
To make the 3 pen activated 'soft keys' work, look [here]("http://ubuntuforums.org/showthread.php?p=3672701#post3672701")

Since Cellwriter 1.3.1, it is possible to use it when the screen is locked. Open Configuration Editor and browse to apps/gnome-screensaver and check embedded_keyboard_enabled and enter:
```
cellwriter --xid
```
under embedded_keyboard_command

Brigtness can also be adjusted. Look [here]("http://ubuntuforums.org/showthread.php?t=571696&highlight=tc1100+brightness")
----------------------------------------------------------------
That's about it.


**What doesn't work?**
The SD card reader -
However, the PCMCIA slot DOES work, so I bought a Jessops branded '6 in 1' card reader for it and now I can use my SD card with this tablet. But I would prefer it if the built-in card reader worked.

Everything else works or can be made to work in some fashion.


**Any other useful software?**
Xournal is an equivalent to Windows Journal.

[SIZE="3"]**Ubuntu 7.10**[/SIZE]

For those wanting to try Ubuntu 7.10 (Gutsy), I will say it works very well, but you won't get any better results than with 7.04 (Feisty). That is to say, what doesn't work with Feisty, still doesn't work with Gutsy. After installation, follow the above procedure.

**Suspend, hibernate, and sleep**
Although suspend and hibernate work fine, sleep only works once, and afterwards it may give this error:
```
Your computer failed to suspend.
```
...even though it did it perfectly. It then (without any warning), goes into hibernation. When it wakes from that, another error message:
```
Your computer failed to hibernate.
```
...even though it did it perfectly! If anyone knows the answer, please let me know.
**EDIT:** After this error, you may lose your wireless connection and have to set it manually (related?).

**Rotation**
The console shows different output in Gutsy for xrandr, so the above script won't work correctly. Please use the following:
```
#!/bin/sh
if [ -n "$(xrandr | grep 768x1024)" ]; then
        xrandr -o normal
        xsetwacom set "stylus" Rotate NONE
else
        xrandr -o left
        xsetwacom set "stylus" Rotate CCW
fi
```
...from post #16 by ronnystandtke. Thanks for that.

**Stylus not working?** While you are editing /etc/X11/xorg.conf, you will need to uncomment one line at the bottom to make the Stylus work. You do not need to uncomment Eraser or Cursor.

**Compiz**
Compiz works quite well on this tablet considering the low-end video card and limited video RAM. Edit this file:
```
sudo nano /usr/bin/compiz
```
...and comment out the line that reads:
```
NVIDIA_MEMORY="65536" # 64MB
```
...to read:
```
# NVIDIA_MEMORY="65536" # 64MB
```
This will allow you to start the desktop effects without it checking for a minimum of 64Mb of video RAM.
You may notice the 3 stylus activated 'buttons' stop working with Compiz running. It's because it's tampered with the key mappings. You need to add the key mappings in the CompizConfig Settings Manager under General Options and add the commands in the Commands tab, and the key mappings in the Actions tab>Commands.
Compiz is installed by default in Gutsy, so you just need the Settings Manager:
```
sudo apt-get install compizconfig-settings-manager
```

**Bluetooth**
If you have the model with bluetooth like mine, I can tell you it works fine. I'm using a HP Deskjet 460wbt printer using the bluetooth module.

[SIZE="3"]**Ubuntu 8.04**[/SIZE]

I'm skipping Hardy Heron because it shouldn't be much different from Gutsy. There are posts here concerning Hardy if you do a search.

[SIZE="3"]**Ubuntu 8.10**[/SIZE]

For anyone using Ubuntu version 8.10 (Intrepid Ibis), refer to [post 116]("http://ubuntuforums.org/showpost.php?p=6123218&postcount=116") by Aearenda.

---

### Post by francisco_athens on 2007-10-02
Nice tute, 
there is some more useful info here:

[http://wiki.linuxquestions.org/wiki/Tc1100#Onscreen_Keyboard_at_Login](http://wiki.linuxquestions.org/wiki/Tc1100#Onscreen_Keyboard_at_Login)

including how to get the onscreen keyboard at login 
the two things that confound me are getting sleep to function properly with the atheros wifi (known bug in madwifi) and getting the Onboard working when the screensaver has locked the screen.

there are also some general tablet apps here:

[http://wiki.linuxquestions.org/wiki/Tablet_PC](http://wiki.linuxquestions.org/wiki/Tablet_PC)

but the list is missing Xournal, the very good app you mentioned.

---

### Post by francisco_athens on 2007-10-03
BTW there is an AMAZING replacement for onboard/GOK called cellwriter:

[http://www.gnomefiles.org/app.php?soft_id=2127](http://www.gnomefiles.org/app.php?soft_id=2127)

this really needs to be a part of (X,K,*)Ubuntu!!

sorry for all the enthusiasm but it really is very good!

Francisco

---

### Post by phenest on 2007-10-03
> **francisco_athens said:**
> BTW there is an AMAZING replacement for onboard/GOK called cellwriter:

[http://www.gnomefiles.org/app.php?soft_id=2127](http://www.gnomefiles.org/app.php?soft_id=2127)

This looks very interesting. I'm gonna check it out.

The trouble I have with OnBoard during login, is the cursor behaves erratically with the pen although works fine with a mouse or the trackstick. When I use the pen, the cursor keeps jumping to the bottom-right of the screen. No idea why. Pen works fine after login.

---

### Post by phenest on 2007-10-04
> **francisco_athens said:**
> BTW there is an AMAZING replacement for onboard/GOK called cellwriter:

[http://www.gnomefiles.org/app.php?soft_id=2127](http://www.gnomefiles.org/app.php?soft_id=2127)

As a follow up to this app, I have emailed the author with some suggestions and also some bugs. He is very willing to implement my suggestions and to hopefully fix the bugs.

I have asked to add a couple of features so it's completely usable during login.

I would like to see this added to Ubuntu too, perhaps as default to replace OnBoard.

---

### Post by robnz on 2007-10-04
I use xvkbd on my TC1100 under kubuntu. To make it available during login simply add the following line to the end of /etc/kd3/kdm/Xsetup
```
xvkbd -geometry -300-100 -no-keypad &
```
It would probably work the same under gdm just find where Xsetup is located.
```
$ locate Xsetup
/etc/kde3/kdm/Xsetup
```

---

### Post by robnz on 2007-10-04
BTW I agree cellwriter shows great promise. For use at login it would need a dropdown to select the right user so that the appropriate strokes database can be accessed.

---

### Post by robnz on 2007-10-04
The xmodmap calls in the script from Linuturk are unnecessary on the TC1100. The script I use is as follows
```
#!/bin/sh
# Script created to toggle screen orientation on a Compaq TC1100 tablet
# Adapted by Rob Stockley from code found at
# http://www.koders.com/noncode/fidF6152D1225924664BF30DC6977DCD1E697FACD61.aspx
if [ -n "$(xrandr | grep rotation | grep left)" ]
then
xrandr -o normal
xsetwacom set "stylus" Rotate 0
else
xrandr -o left
xsetwacom set "stylus" Rotate 2
fi
```
To get the side keys working my .Xmodmap file looks like this
```
rob@rob-laptop:~$ cat .Xmodmap
! keysyms for buttons on edge of Compaq TC1100 Tablet
! mapped for use in Kubuntu 7.04
!
!  Jog shuttle
!    Left = 99
!    Right = 105
!    Press = 36
!  Escape = 9
!  Reset = 37
!  Tab = 23
!  Q = 159
!  Screen = 151
!
keycode 99 = Page_Up
keycode 105 = Page_Down
keycode 36 = Return
keycode 23 = Tab
keycode 9 = Escape
!
! The Q and screen buttons are mapped to XF86 launch
! events so they can be linked to scripts from within
! system settings
keycode 159 = XF86Launch0
keycode 151 = XF86Launch1
```

I have the screen button mapped to my rotate script and the Q button mapped to xournal which I use often.
HTH

---

### Post by phenest on 2007-10-05
> **robnz said:**
> BTW I agree cellwriter shows great promise. For use at login it would need a dropdown to select the right user so that the appropriate strokes database can be accessed.

I have asked that you only have a keyboard at login.

---

### Post by phenest on 2007-10-05
> **robnz said:**
> I use xvkbd on my TC1100 under kubuntu. To make it available during login simply add the following line to the end of /etc/kd3/kdm/Xsetup
```
xvkbd -geometry -300-100 -no-keypad &
```
It would probably work the same under gdm just find where Xsetup is located.
```
$ locate Xsetup
/etc/kde3/kdm/Xsetup
```

There doesn't seem to be an Xsetup file in gdm. Perhaps to put that line into the /etc/X11/gdm/Init/Default file instead of onboard. I will test this and modify my guide to include the different on-screen keyboards.

---

### Post by phenest on 2007-10-05
> **robnz said:**
> The xmodmap calls in the script from Linuturk are unnecessary on the TC1100. The script I use is as follows
```
#!/bin/sh
# Script created to toggle screen orientation on a Compaq TC1100 tablet
# Adapted by Rob Stockley from code found at
# http://www.koders.com/noncode/fidF6152D1225924664BF30DC6977DCD1E697FACD61.aspx
if [ -n "$(xrandr | grep rotation | grep left)" ]
then
xrandr -o normal
xsetwacom set "stylus" Rotate 0
else
xrandr -o left
xsetwacom set "stylus" Rotate 2
fi
```
To get the side keys working my .Xmodmap file looks like this
```
rob@rob-laptop:~$ cat .Xmodmap
! keysyms for buttons on edge of Compaq TC1100 Tablet
! mapped for use in Kubuntu 7.04
!
!  Jog shuttle
!    Left = 99
!    Right = 105
!    Press = 36
!  Escape = 9
!  Reset = 37
!  Tab = 23
!  Q = 159
!  Screen = 151
!
keycode 99 = Page_Up
keycode 105 = Page_Down
keycode 36 = Return
keycode 23 = Tab
keycode 9 = Escape
!
! The Q and screen buttons are mapped to XF86 launch
! events so they can be linked to scripts from within
! system settings
keycode 159 = XF86Launch0
keycode 151 = XF86Launch1
```

I have the screen button mapped to my rotate script and the Q button mapped to xournal which I use often.
HTH

That is a better script. Thanks for that. The one I used was simply the first one I found.

The side keys work 'Out-Of-The-Box' with Ubuntu. Did you not find this with Kubuntu?

---

### Post by robnz on 2007-10-05
> **phenest said:**
> The side keys work 'Out-Of-The-Box' with Ubuntu. Did you not find this with Kubuntu?

Actually they probably did work out of the box except for perhaps the Q and screen buttons. I've spent a long time trying to get the pen buttons working and some of my key mappings got a little broken along the journey. Chances are I could comment out the tab, esc, and jog shuttle mappings now and they would function normally.

---

### Post by robnz on 2007-10-05
```
Option    "Button1"    "1"
```
Also the above line in xorg.conf is unnecessary as that is already the default button mapping.

---

### Post by phenest on 2007-10-07
> **francisco_athens said:**
> ... things that confound me are getting sleep to function properly with the atheros wifi (known bug in madwifi) ...

If by 'sleep' you mean 'suspend', then it does work with some tweaking.

EDIT: I have edited the guide to show how.
Also, Suspend and Hibernate now work in Gutsy with the 2.6.22-14-generic kernel using the same method.

---

### Post by robnz on 2007-10-10
FYI. I've submitted a script to adjust LCD brightness on the TC1100 in [this thread.]("http://ubuntuforums.org/showpost.php?p=3511736&postcount=4")

---

### Post by ronnystandtke on 2007-10-15
I noticed that the script does not work with Ubuntu 7.10 because the console output of xrandr changed. Here comes my version of the rotate script:

```
#!/bin/sh
if [ -n "$(xrandr | grep 768x1024)" ]; then
        xrandr -o normal
        xsetwacom set "stylus" Rotate NONE
        xsetwacom set "cursor" Rotate NONE
        xsetwacom set "eraser" Rotate NONE
else
        xrandr -o left
        xsetwacom set "stylus" Rotate CCW
        xsetwacom set "cursor" Rotate CCW
        xsetwacom set "eraser" Rotate CCW
fi
```

---

### Post by phenest on 2007-10-16
> **ronnystandtke said:**
> ...the script does not work with Ubuntu 7.10 because the console output of xrandr changed...

I also found this. I will update the guide as soon as 7.10 is released officially.

---

### Post by robnz on 2007-10-16
> **ronnystandtke said:**
> I noticed that the script does not work with Ubuntu 7.10 because the console output of xrandr changed.
What has it changed to?
UPDATE: Disregard. I took a look at the xrandr source for Gutsy and saw the extensive changes.

---

### Post by robnz on 2007-10-22
The attached script below should work with both Feisty and Gutsy. There is an issue with screen dimensions that I have yet to address but this is half the solution.
```
#!/bin/sh
# Script created to toggle screen orientation on a Compaq TC1100 tablet
# Adapted by Rob Stockley from code found at 
# http://www.koders.com/noncode/fidF6152D1225924664BF30DC6977DCD1E697FACD61.aspx
# Updated 23 October 2007 to work with xrandr version 1.2 as 
# installed on Gutsy Gibbon.

if [ -n "$(xrandr --version | grep 'version 1.2' )" ]
then
  if [ -n "$(xrandr | grep 'left (')" ] 
    then ORIENTATION="left"
    else ORIENTATION="normal"
  fi
else
  if [ -n "$(xrandr | grep rotation | grep left)" ] 
    then ORIENTATION="left"
    else ORIENTATION="normal"
  fi
fi

if [ $ORIENTATION = "left" ]
then
  xrandr -o normal
  xsetwacom set "stylus" Rotate 0
else 
  xrandr -o left
  xsetwacom set "stylus" Rotate 2
fi
```

---

### Post by popch on 2007-11-06
Thanks for this nice HowTo.

I am just now trying to set up my TC1100.

First problem: enabling the restricted nvidia drivers will fail in Switzerland.

Solution: open ***Systems/administration/software sources***. Change *download from* ***Server for Switzerland***to *** main server*** (Hauptserver) before trying to enable the restricted drivers.

---

### Post by popch on 2007-11-06
Since Gutsy (7.10) three important lines in /etc/X11/xorg.conf have been commented out. The HowTo (first post) should mention that at least one of them (stylus and cursor?) need to be uncommented. Otherwise, the pen will not work:

# Uncomment if you have a wacom tablet
        InputDevice     "stylus"    "SendCoreEvents"
        InputDevice     "cursor"    "SendCoreEvents"
    #    InputDevice     "eraser"    "SendCoreEvents"

(Near the end of the file, in 
Section "ServerLayout"
    Identifier    "Default Layout"
  screen "Default Screen"

Since the TC1100's pen does not have an eraser, the third line can remain commented out.

The OSK (on-screen keyboard) seems to be working. Still no luck in the login screen. The login screen hides the virtual keyboard. Perhaps I have not understood all the settings properly. Will look again later.

Later (under 'Rotation' for Gutsy), the new script mentions xsetwacom. Does the HowTo mention that wacom-tools must be installed?

I am terribly pleased so far. Rotation works on first trial. The TC1100 is much more useful when rotated.

OK, time for bed. More tomorrow or some days after.

---

### Post by phenest on 2007-11-06
Good point. In fact, I only have Stylus uncommented. I left Cursor and Eraser commented out.

---

### Post by popch on 2007-11-06
> **phenest said:**
> Good point. In fact, I only have Stylus uncommented. I left Cursor and Eraser commented out.

I just edited the post you replied to. Thanks for the useful information.

---

### Post by phenest on 2007-11-07
> **popch said:**
> The OSK (on-screen keyboard) seems to be working. Still no luck in the login screen. The login screen hides the virtual keyboard. Perhaps I have not understood all the settings properly. Will look again later.

Later (under 'Rotation' for Gutsy), the new script mentions xsetwacom. Does the HowTo mention that wacom-tools must be installed?

Yep, I forgot a couple of things there:

To see the OSK during login, set the login style to Plain instead of Themed.

And yes, wacom-tools needs to be installed.

---

### Post by popch on 2007-11-07
Practically everything now works.
 

 /etc/X11/gdm/Init/Default 
appears to have been moved to
/etc/gdm/Init/Default

btw, the pcmcia slot works for me in gutsy.
sd slot does not work, but then, in XP it does detect my SD card but says it is not formatted.

---

### Post by phenest on 2007-11-07
> **popch said:**
>  /etc/X11/gdm/Init/Default 
appears to have been moved to
/etc/gdm/Init/Default
I'm glad you verified that. I thought I'd made a mistake.

> **popch said:**
> btw, the pcmcia slot works for me in gutsy.
I never had anything to test it with.
> **popch said:**
> sd slot does not work, but then, in XP it does detect my SD card but says it is not formatted.

Mine works perfectly in Windows, as it does on my Dell laptop with Ubuntu. I think it's always worth spending a bit extra on memory cards to get reliability.

Now I know the PCMCIA slot works, I'm going to try and get a memory card reader for it.

---

### Post by popch on 2007-11-07
> **phenest said:**
> 
Now I know the PCMCIA slot works, I'm going to try and get a memory card reader for it.

I use mine with a SanDisk CompactFlash PC Card adapter. I do not have any other PCMCIA cards to test it with.

---

### Post by timnicholson on 2007-11-09
Thanks for all the great info!

> **phenest said:**
> 
Then edit the InputDevice  section- Driver wacom - Identifier stylus add:
```
Option    "Button2"    "3"
```This enables right-clicking with the pen button.


I have a Fujitsu Stylistic Tablet PC and have xubuntu v7.10 installed, have the screen settings all set and have a script for screen rotation that works. However, I've added the above line for the "right click" and it doesn't seem to work. My pen has a rocker button on it where if you press the bottom I think its supposed to right click and if you press the top its supposed to erase. I don't care as much about the erase function, but I need to be able to right click since unlike in Windows you can't press-and-hold to pull up the context menu.

Is there documentation anywhere on this? Is this related to the wacom drivers or something else?

> **phenest said:**
> 
**Rotation**
You will need a script and map it to a key.
<SNIP>
Save it as rotate.sh and put into the /usr/bin/ directory. 


BTW, I needed to modify the one posted here to grep for "current 768 x 1024". The word current is needed because the 1024 x 768 string also exists in the output. Notice the space in front of and behind the x as well.

> **phenest said:**
> 
The TC1100 has a 'Q' key on its edge. In Windows, this activates a popup menu, but the menu doesn't exist in Ubuntu. So we will use it for screen rotation. To map the key, open the Configuration Editor and browse to /apps/metacity/keybindings_commands. Edit command_1 (or the 1st available command) enter: sh /usr/bin/rotate.sh . Then browse to /apps/metacity/global_keybindings and edit the run_command_1 with 0x9f (or press the 'Q' button.


I have researched this and found that what you are referring to is probably the gconf-editor. I've installed that successfully by typing 

sudo apt-get install gconf-editor

However, I don't see a menu option for it. I thought this was a program that let me changes things with a graphical UI, similar to Windows regedit function. 

I obviously want to be able to assign the screen rotation to a button and also would like to get the up/down/left/right arrows working and assign things the web browser to a button.

> **phenest said:**
> 
**OSK: On Screen Keyboard**

I haven't installed an onscreen keyboard yet. It looks like there is cellwriter and xvkbd. What's the consensus on which one is the best for me to try?

> **phenest said:**
> 
**Suspend, hibernate, and sleep**

Did anyone ever figure out how to get suspend and hibernation working properly in Gutsy 7.10? I'll want to get that working next as the whole reason I'm doing all this is to get this tablet where its quick enough that the kids can hop on quickly and not bellyache about how slow Windows is. So I'd like it to remain in suspend or hibernation mode all the time.

---

### Post by popch on 2007-11-09
> **timnicholson said:**
> Configuration Editor :
I have researched this and found that what you are referring to is probably the gconf-editor. I've installed that successfully by typing 

sudo apt-get install gconf-editor

That had me stumped, at first, too. I later found out about it and forget to mention it in my feedback.

In Ubuntu 7.10, the Configuration Editor apparently is installed by default. In order to make it visible, use System/Settings/Main Menu (or equivalent; I do not know what terms they use in the English language menues).

In the Menu editor, scroll to the System tools group. On the right hand side you should find an entry called Configuration Editor. Activate that.

Lo and behold! you can access it in the applications menu.

---

### Post by phenest on 2007-11-09
I would like to say you are wandering off-topic here. This thread is for a Hewlett Packard/Compaq TC1100 tablet pc. I also have a Fujitsu Stylistic ST4110 tablet pc, and all the things you mention can be made to work. There are other threads already in discussion about those.

Also, please note that this thread is for installing Ubuntu. Although it will work for Xubuntu and Kubuntu, you may have to make adjustments. Again, there is already information on this forum for you. But please stay on-topic here.

Many thanks.

P.S. I will make amendments to my tutorial for Kubuntu and Xubuntu users but only for Compaq TC1100 owners. I will be starting a tutorial for Fujitsu Stylistic ST4110 owners (unless someone beats me to it).

---

### Post by phenest on 2007-11-14
This is a breakdown of the Q Menu in Windows XP Tablet Edition. If anyone would like to help me program a Linux equivalent, please PM me to discuss it (programmers of C++ only).

The default popup menu consists of:
[LIST]
[*]Mute On/Off
[*]Brightness
[*]Wireless Off
[*]Internal Only
[*]Internal and External
[*]Volume
[*]Presentation Mode On
[*]Portrait-Primary
[*]Landscape-Primary
[*]Tablet PC Settings
[*]Q Menu Settings
[/LIST]
Brightness brings up a dialog box which says: Please use the Jog dial to adjust the brightness. Click OK button when you are done.
Wireless Off toggles wireless on and off.
Volume brings up the Volume Control (found in the Control Panel).
Presentation Mode sets Extended Desktop and sets Presentation power settings (something to do with NView Desktop Manager).
Tablet PC Settings opens a Control Panel applet.
Q menu Settings brings up an applet allowing you to choose which items to display on the Q Menu:

**Q Menu Settings**
Items to display on Q Menu
[LIST]
[*]Mute On/Off
[*]Brightness
[*]Internal Only
[*]External Only
[*]Internal and External
[*]Extended Desktop
[*]Volume
[*]Capture Screen
[*]Capture Window
[*]Power Control
[*]Presentation Mode
[*]Docked Profile
[*]Undocked Profile
[*]Write Profile
[*]Portrait-Primary
[*]Landscape-Primary
[*]Standby
[*]Hibernate
[*]Shut down
[*]Tablet PC Settings
[*]Q Menu Settings
[/LIST]
Most of the items are self explanatory.

Down the right of the list is 7 buttons:
[LIST]
[*]Add
[*]Modify
[*]Remove
[*]Move Up
[*]Move Down
[*]Execute
[*]About
[/LIST]
Add and Modify opens a dialog box:
**Add New Menu Entry**
Please enter Diplay name ane File name. Display name is limited to 25 characters.
Display Name (text box)
File Name (text box)
Buttons: Browse, OK, and Cancel.

Under the list is a text window showing a description for the highlighted list item. Under that is a checkbox: Display Q Menu Icon on system tray. Under that are the usual buttons: OK, Cancel, and Apply.

**Tablet and Pen Settings**
4 tabs: Setting, Display, Tablet Buttons, and Pen Buttons
[LIST=1]
[*]Settings
Handedness - to do with hand-writing recognition (Won't need this)
Menu location - You can select a menu position so that menus don't appear under your hand. (Useful and possible I think)
Calibration - Need Special Wacom tools installed from their site
[*]Display
Screen orientation - A bit pointless?
Screen brightness - Need this
[*]Tablet Buttons
Allows programming of the 3 screen buttons as well as the edge buttons
[*]Pen Options
Pen actions - such as Right-click etc.
Pen buttons - (checkbox) Use pen button to right-click - Use top of the pen to erase (where available)
[/LIST]

A linux equivalent doesn't have to be exactly the same, but this gives an idea.

I only program in C++ but have never written for Linux. So if you're up to the challenge, PM me and we'll put our heads together. If not, I'll have a bash myself.

---

### Post by Zolty on 2007-12-04
I have followed your guide, well written and easy to understand for even a noobie like me, I am having one problem binding my Q key to the rotate command.  It works fine With Compiz disabled, but as soon as I activate Compiz it stops working.

I noticed in your guide that I should expect this as Compiz will take over keybindings, so I go into the ccsm and check to make sure the command is bound to command 0, it is, then I check the actions tab to be sure the key is bound properly.  The Run Command 0 has a key value of DISABLED.  I can set it to a keyboard command like ctrl+alt+D, but it will not let me bind it to 0x9f as your guide suggests (it simply goes back to "disabled" when I hit OK).  I have also tried hitting the key when prompted for "New accelerator" and nothing happens when I hit any of the proprietary keys on the TC1100.  

Based on some advice from the #compiz-fusion irc channel on freenode I tried the Xen Command to see what is being returned from those key presses:

```
KeyPress event, serial 31, synthetic NO, window 0x6800001,
   root 0xc1, subw 0x0, time 2792056699, (276,-95), root:(283,464),
   state 0x0, keycode 159 (keysym 0x0, NoSymbol), same_screen YES,
   XLookupString gives 0 bytes:
   XmbLookupString gives 0 bytes:
   XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x6800001,
   root 0xc1, subw 0x0, time 2792056699, (276,-95), root:(283,464),
   state 0x0, keycode 159 (keysym 0x0, NoSymbol), same_screen YES,
   XLookupString gives 0 bytes:
   XFilterEvent returns: False
```

Any help is greatly appreciated.

---

### Post by phenest on 2007-12-04
> **Zolty said:**
> ...but it will not let me bind it to 0x9f as your guide suggests (it simply goes back to "disabled" when I hit OK)...

CCSM does not like you entering some key combinations. I also had this problem. Try entering them via the Configuration Editor instead.

---

### Post by cathectic on 2007-12-08
Would someone be able to post the DSDT from this machine?

Using sudo:

cat /proc/acpi/dsdt > dsdt

And then attach the dsdt file?

(I don't have the machine, but am planning to work on the tc1100-wmi driver, so it plays nice with some other upstream patches I'm working on).

**Edit:**You can safely disregard this - I've managed to get my hands on the DSDT for this machine.

---

### Post by timere969 on 2007-12-26
There is a program called Tabatha. Just do a Google search for tabatha and groundstate and it will pull up the page. It replicates must of the Q menu functions.

---

### Post by mgk on 2007-12-29
Hello
i ve got some problems with my xorg.conf
my screen rotate but not the cursor
this is my xorg.conf
i am on linux mint darina (gusti)
thanks a lot for help

xorg.conf (xorg X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "fr"
    Option        "XkbVariant"    "oss"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "mouse"
    Option        "CorePointer"
    Option        "Device"    "/dev/input/mice"
    Option        "Protocol"    "ImPS/2"
    Option        "ZAxisMapping"    "4 5"
    Option        "Emulate3Buttons"    "true"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"    "/dev/psaux"
    Option        "Protocol"    "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "stylus"
    Option    "Button2"    "3"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "stylus"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
    Option "Mode" "Absolute"
    Option "KeepShape" "on"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option     "Button2"     "3"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "eraser"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
    Option "Mode" "Absolute"
    Option "KeepShape" "on"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option     "Button2"     "3"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"    "cursor"
    Option        "ForceDevice"    "ISDV4"# Tablet PC ONLY
    Option "Mode" "Absolute"
Option "KeepShape" "on"
EndSection

Section "Device"
    Identifier    "nVidia Corporation NV17 [GeForce4 420 Go 32M]"
    Boardname    "nv"
    Busid        "PCI:1:0:0"
    Driver        "nvidia"
    Screen    0
    Option    "RandRRotation"    "on"
    Option     "NvAGP"     "1"
EndSection

Section "Monitor"
    Identifier    "Generic Monitor"
    Modelname    "Custom 1"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
    Gamma    1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia Corporation NV17 [GeForce4 420 Go 32M]"
    Monitor        "Generic Monitor"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1024    768
        Modes        "1024x768@60"    "800x600@60"    "800x600@56"    "640x480@60"
    EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
  screen 0 "Default Screen" 0 0
    Inputdevice    "Generic Keyboard"
    Inputdevice    "Configured Mouse"
   
    # Uncomment if you have a wacom tablet
        InputDevice     "stylus"    "SendCoreEvents"
        InputDevice     "cursor"    "SendCoreEvents"
        InputDevice     "eraser"    "SendCoreEvents"
    Inputdevice    "Synaptics Touchpad"
EndSection
Section "Module"
    Load        "wacom"
    Load        "glx"
    Load        "v4l"
EndSection
Section "device" #
    Identifier    "device1"
    Boardname    "nv"
    Busid        "PCI:1:0:0"
    Driver        "nvidia"
    Screen    1
EndSection
Section "screen" #
    Identifier    "screen1"
    Device        "device1"
    Defaultdepth    24
    Monitor        "monitor1"
EndSection
Section "monitor" #
    Identifier    "monitor1"
    Gamma    1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by phenest on 2007-12-29
It has nothing to do with the xorg.conf file. When you rotate the screen, it only rotates the video and not the wacom device. You need a script like the one I provided in the 'How To'.

---

### Post by mgk on 2007-12-30
hello 
thanks for help
I use your script and i map the "Q" 
when i press "Q" the screen don't rotate
i use Grandr 0.2 to turn left the screen rotate but not the cursor, if i use "Q" the screen come back right
from landscape to portrait don't work for me????

I use the script on first page, do i use the script on page 2?

---

### Post by phenest on 2007-12-30
Have you installed wacom-tools?

```
sudo apt-get install wacom-tools
```

---

### Post by mgk on 2007-12-30
yes wacom tools are install
i ve got : wacom kernel source, wacom tools and xserver xorg input wacom
thanks

---

### Post by mgk on 2007-12-30
All works fine
i am sorry i haven't use the good script
thanks again for help
happy new year for all
Marc

---

### Post by galileon on 2008-01-26
Hi, thanks for the nice tutorial!

Has anyone got Nvidia Propritary driver AND suspend and/or hibernate to work at the same time? I can do each separately, but not both.

I installed the NVIDIA driver through Restricted Manager  and added the option mentionned in the tutorial. The computer hibernates or suspends, but on wake up, the screen remains blank.

Any ideas?

Cheers

galileon

---

### Post by Markopolo123 on 2008-02-04
Heya guys, after seeing this guide I decided to take the plunge and install ubuntu 7.10 on my tc1100. 

Installation went fine, and it connects to my wifi network. I can ping websites from the terminal, but wget doesn't do anything. At first firefox wouldn't load up any pages, but after much talking with a friend we got firefox to come alive, I had to go into the about:config and change 

"network.dns.disableIPv6"  

to true. 

Rather annoyingly, apt-get doesn't work and neither does synaptic, whatever it tries to download fails. 
Other computers on the network (windows &mac) can access the net fine, and the DNS is the same on both the tc1100 and this machine.
I have no idea whats wrong (I am a linux n00b).

Any ideas or help would be appreciated
Thanks
Mark.

---

### Post by galileon on 2008-02-04
[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

---

### Post by Markopolo123 on 2008-02-04
> **galileon said:**
> [http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

Many thanks, just before reading your reply I had tried this guide from  

[http://ubuntuforums.org/showthread.php?t=161742](http://ubuntuforums.org/showthread.php?t=161742)

which didn't help. I gather the two methods achieve the same end?

I will reset the file and try the method you linked to.

Neither method has resolved this, I am quite tempted to reinstall the OS. 

Mark

---

### Post by Markopolo123 on 2008-02-11
I have managed to resolve the problem with apt-get [="http://ubuntuforums.org/showthread.php?t=206692&page=3"](="http://ubuntuforums.org/showthread.php?t=206692&page=3")
Other than that I am very happy with it, thanks for the guide!
Mark
:popcorn:

---

### Post by phenest on 2008-03-14
Has anyone tried the latest Hardy on this tablet to see if the memory card reader works. Apparently, there has been some fixes in this area.

If your able to reply, there is a bug report: [163345]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/163345")

An answer is needed for this bug as to whether the memory card reader now works.

---

### Post by popch on 2008-03-15
> **phenest said:**
> Has anyone tried the latest Hardy on this tablet to see if the memory card reader works. Apparently, there has been some fixes in this area.

If your able to reply, there is a bug report: [163345]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/163345")

An answer is needed for this bug as to whether the memory card reader now works.

I did a few perfunctory tests with Hardy Heron Alpha 6 (downloaded March 15, 2008 ) on my TC1100. There have been no changes with regards to the SD card reader. No card will be detected. The same card is detected, read and written when used in the other HP laptop both with Gibbon and Heron.

On the other hand, on the TC1100 not even Windows XP handles the card. It detects it and assigns it a drive letter (E: ). However, it can not read the card, offers to format it, fails to format if asked to. This is the XP wich was installed when I bought the PC. It is conceivable that the XP installation is somewhat flawed because the PC appeared to be refurbished when I bought it.

The SD slot does not appear to work on this PC. Period. I bought a 5$ SD to USB adapter which works at once without thinking about it.

---

### Post by phenest on 2008-03-15
Personally, my TC1100 worked fine with XP Tablet Edition including the card reader. But using Ubuntu Gutsy, I had to resort to a PCMCIA card reader which did the job.

I hope someone can give a Yes/No to the bug report so the devs can mark it as Fixed or whatever.

---

### Post by kpfade on 2008-03-22
use this for rotate and use pen:
Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS4"
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"
  Option	"Mode"		"Absolute"
  Option	"Button2"	"3"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS4"
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"
  Option	"Mode"		"Absolute"
  Option	"Button2"	"3"
EndSection

And add the following lines to the Server Layout section.

InputDevice    "cursor"    "SendCoreEvents"
InputDevice    "stylus"    "SendCoreEvents"

---

### Post by wsilk on 2008-04-19
I'd just like to say thanks for the great writeup.  I'm new to linux and managed to get Ubuntu 7.10 up and running on my tc1100 with all the features I need with relative ease.  I even managed to do it off a usb flash drive.  So far, I've seen a large increase in performance over XP tablet edition.  

The last tasks are to get the side button working for the OSK (using onboard) and figure out the "keyring" password prompt on boot.

---

### Post by sethtriggs on 2008-05-14
For some reason I can't get my pen to work correctly - this is a mothballed Tablet PC for work, and I'm trying to get the pen to work~! I'd hate to have to carry a keyboard everywhere with me!

I am hoping for the best here, heh heh...if any of you can tell me what could cause the attached stylus pen to do absolutely nothing in Ubuntu (yet the original pen calibration works just after POST), I'd be most grateful!

Thanks,


Seth

On edit: A restart fixed it after I changed the device to /dev/input/wacom and then restarted. It works beautifully! Just have to get the onboard keyboard to move out of my way, hehehe...

---

### Post by galileon on 2008-05-14
i get the feeling wacom users are being persecuted. Once upon a time, the required lines to make wacom work were there by default in xorg.conf. 

this seemed to break something on some systems, so the devs, in their infinite wisdom, decided to comment the required lines out.

that was not enough. so they removed the lines completely.

without ANY mention of the deliberate regression in the release notes!

Thankfully, you can still copy-n-paste them into your zorg.conf if have an old copy lying around...

so here goes:

$sudo nano /etc/X11/xorg.conf

add the following somwehere after your "mouse" bits:

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection



and also add the necessary lines in your server layout:

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection


hopefully this should help, it did in Gutsy. I havent tried Hardy yet, so they may have done something that would stop even that from working, I can't tell yet.

> **sethtriggs said:**
> For some reason I can't get my pen to work correctly - this is a mothballed Tablet PC for work, and I'm trying to get the pen to work~! I'd hate to have to carry a keyboard everywhere with me!

I am hoping for the best here, heh heh...if any of you can tell me what could cause the attached stylus pen to do absolutely nothing in Ubuntu (yet the original pen calibration works just after POST), I'd be most grateful!

Thanks,


Seth

On edit: A restart fixed it after I changed the device to /dev/input/wacom and then restarted. It works beautifully! Just have to get the onboard keyboard to move out of my way, hehehe...

---

### Post by phenest on 2008-05-18
> **galileon said:**
> ...
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection
...

I would like to point out here, that there is no need to a add the 'eraser' and the 'cursor' devices. You only need the 'stylus' device. Seeing as the TC1100's stylus' has no eraser (although there may be a rare one around), and I think the 'cursor' device is for external tablets (the type you may attach to the serial or USB port).

---

### Post by romana on 2008-05-29
Hardy has stylus working - Cellwriter and Xournal rock.

Tabatha, as suggested for mapping Q menu functionality, has errors and falls over, but am hoping a Q menu gets posted soon:)

Rotate script is fine,but having trouble mapping it to a key in KDE4. Suggestions?
I have tried in SystemSettings->Advanced->InputActions
But no matter what combo, nada. Zip.

---

### Post by ChaOConnor on 2008-06-06
I'm trying to install Hardy, but I can't because the linux-image-2.6.25-1-generic is gone.  any suggestions?  I can get Hardy installed, but no wacom, hence what the linux-image-2.6.25-1-generic was for.  Appreciate any thoughts you have!

---

### Post by Aearenda on 2008-06-06
2.6.25 is the Intrepid Ibex kernel! I have had wacom working on all the Hardy kernels in the 2.6.24 series, the latest being -18.

---

### Post by romana on 2008-06-19
Having got it all pulled together on Kubuntu Hardy running KDE4, I decided to howto MY setup, given all I learnt here and in other places. Naturally, duly credited:)

Could not have done it without all the info in this forum, thanks guys:)

[Kubuntu TC1100 Tablet Functions Howto]("http://timelady.com/blog/howtos-technical-guidestips/kubuntu-804-hp-tc1100-tablet-functions-howto/")

---

### Post by jdn-za on 2008-07-04
Ola,

I managed to get kubuntu 8.04 working well enough on my tc1100 with this guide, thanks for that :D

though managed to mangle it badly when forcing a change from kde to gnome and then back with various changes to nvidia drivers etc =\

going to be doing a clean install of ubuntu tomorrow.

One iss I havent managed to get past so far is after installing the nvidia drivers, via envyng or via the nvidia run file (legacy or new) my glxgears runs very slowly (500 fps+-) this is after having corrected the xorg.conf...

Is there any thing obvious I am missing? I noticed that load/cpu is high due to the glx thread.

Wont bother posting my xorg.conf until i have installed the clean ubuntu, nvidia drivers with enyng and compiz as per the guide above.


thanks again for the kewl guide :D

---

### Post by Aearenda on 2008-07-04
I think turning off 'sync to vblank' might fix this - in nvidia-settings, OpenGL settings (NOT the Xserver Xvideo settings). I get 1000+ fps with it off and <100fps with it on, but I'm using an external display atm so it might differ internally.

---

### Post by jdn-za on 2008-07-05
thanks will try that, just installed ubuntu and envyng is finishing up. default display drivers I get 200 - 300 fps

---

### Post by jdn-za on 2008-07-05
k after having installed the nvidia driver via envyng and having disabled the "sync to vblank" option I am getting 850 odd fps +-  =\ should still be higher than that though?

currently am on a default ubuntu 8.04 install with nvidia driver ver: 96.43.05

xorg.conf below:

> 
# xorg.conf (X.Org X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"UseDisplayDevice"	"DFP"
	Defaultdepth	24
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection


Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
    	Screen          0
    	Option          "NvAGP"     "1"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

b

---

### Post by Aearenda on 2008-07-05
Do you have a Celeron processor or a Pentium M? Some TC1100s have Celerons. Mine is a 1Ghz Pentium M.

For comparison, the TC1100-relevant bits of xorg.conf on mine are: ```

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
        Option          "Button2"       "3" # This is the line you need for the stylus button to right click
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
	Option		"RandRRotation" "on"
	Option		"NvAGP" "1"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen 		"Default Screen"
        InputDevice     "stylus"        "SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

This includes the settings to get the pen working. I'm not saying this is perfect - just that it works for me.

BTW, I don't think you need the touchpad entry, even though it's there in mine too.

---

### Post by jdn-za on 2008-07-05
The xorg.conf below is working fiarly well right now, have compiz effects on (still need to tweak them) 

What I was thinking of doing is once I have the full setup sorted out maybe I should make a live CD to help other folks in setting up a TC1100, any one interested in helping out with this?

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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"UseDisplayDevice"	"DFP"
	Defaultdepth	24
EndSection

Section "Module"
    	Load           "glx"
	Load           "v4l"
EndSection


Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
    	BoardName      	"vesa"
    	BusID          	"PCI:1:0:0"
    	Screen          0
    	Option          "RandRRotation"    "on"
    	Option          "NvAGP"     "1"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
   	Driver 	  	"wacom"
   	Identifier 	"stylus"
   	Option 	  	"Device" 	"/dev/input/wacom"
   	Option 	  	"Type" 		"stylus"
   	Option    	"Button2"    	"3"
   	Option 	  	"ForceDevice" 	"ISDV4"
EndSection

Section "ServerLayout"
    	Identifier     "Default Layout"
    	Screen      0  "Default Screen"     0 0
    	InputDevice    "Generic Keyboard" "CoreKeyboard"
    	InputDevice    "Configured Mouse" "CorePointer"
    	InputDevice    "Synaptics Touchpad"
    	InputDevice    "stylus"           "SendCoreEvents"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
    	VendorName     	"Generic LCD Display"
    	ModelName      	"LCD Panel 1024x768"
    	HorizSync       31.5 - 48.0
    	VertRefresh     56.0 - 65.0
    	Gamma           1
    	ModeLine       	"640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    	ModeLine       	"800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    	ModeLine       	"800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    	ModeLine       	"1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection


---

### Post by jdn-za on 2008-07-05
kewl have got compiz with all the nice effects working perfectly now :D

---

### Post by Aearenda on 2008-07-05
That's great - I find that Compiz tends to give black windows after a while - esepcially with Firefox. There just isn't enough video RAM in the TC1100. 

Enabling compositing in Metacity will be more suitable for the TC1100 once it works reliably - I keep getting brightness problems after screen savers kick in, and display corruption during animations, when I turn this on.

---

### Post by romana on 2008-08-11
Now runing Interpid Ibex Alpha 3 - and of course, much is broken. Not as much as you think:)

Rotate not working, nor is button mapping. So, xrandr/xbindkeys are an issue.

Stylus and related applications just fine. 

Will post/update my howto when solutions worked out, which may NOT be until at least beta/prerelease stage:)

---

### Post by phenest on 2008-08-11
As I've mentioned before, I don't have my TC1100 any more. But I am interested if anyone knows a solution to this problem:

The stylus only allows left or right click. How does one achieve a middle click?

---

### Post by okrichie on 2008-08-16
K am starting to get really upset about this.. I've installed Ubuntu on my tc1100, it worked fine apart from the usual; stylus, extra buttons etc.. 

I started messing with this tutorial and a couple of others such as for the 'soft buttons' and the hardware buttons like Q. 

This is the second time now, after hours of compiling stupid wacom drivers and messing in the xorg.conf, I have reached the same problem I got after a few hours of messing the first time; and I was honestly, really careful this time.

What's going on? Well the stylus still doesn't work. Now the graphics are set to only 800x600max and I can't change it. I tried restoring an original xorg.conf backup; it did NOT help at all..

Why is this such a demanding problem? Why are all the solutions to these issues so cryptic? Why do these solutions not seem to work and at the same time cause MORE trouble?

Has anyone encountered this? I'm obviously being a complete moron and doing it wrong. So take pity and help please?

I got the stylus to work once, using an xorg.conf file I downloaded that someone else made (I think for a slightly different distro of linux), but that seemed to cause the same graphics problem; so I formatted and tried over, being more careful to self-build my own xorg.conf rather than slap my name on someone else's but it hasn't worked!

---

### Post by olaoni on 2008-08-20
I have managed to get the pen stylus to work using the following url as reference [http://ubuntuforums.org/showthread.php?p=3672701#post3672701]("http://ubuntuforums.org/showthread.php?p=3672701#post3672701") both as a mouse and for invoking the three soft buttons to the left hand side of the screen. 
Starting from the top the buttons are mapped as "rotate screen" "xournal" and "cellwriter".

The problem I have is that when the screen is rotated the stylus pointer is all over the place when I move the pen to the screen.

I am currently using an xorg.conf file which I picked up from one of these forums on the subject. I have attached it below just in case any of you smart guys may see something wrong that I am doing many thanks in advance.

---

### Post by olaoni on 2008-08-20
I don't know what happened in my last post I attached my xorg.conf file but it has not shown up so I am doing a cut and paste job here.

# xorg.conf (X.Org X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Screen"
	Identifier "Default Screen"
	Monitor "Configured Monitor"
	Device "Configured Video Device"
	Option "AddARGBGLXVisuals" "True"
	Option "UseDisplayDevice" "DFP"
	Defaultdepth 24
EndSection

Section "Module"
	Load "glx"
	Load "v4l"
EndSection


Section "Device"
	Identifier "Configured Video Device"
	Driver "nvidia"
	BoardName "vesa"
	BusID "PCI:1:0:0"
	Screen 0
	Option "RandRRotation" "on"
	Option "NvAGP" "1"
    Option "NoLogo" "True"
EndSection

Section "InputDevice"
	Identifier "Generic Keyboard"
	Driver "kbd"
	Option "XkbRules" "xorg"
	Option "XkbModel" "pc105"
	Option "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier "Configured Mouse"
	Driver "mouse"
	Option "CorePointer"
EndSection

Section "InputDevice"
	Identifier "Synaptics Touchpad"
	Driver "synaptics"
	Option "SendCoreEvents" "true"
	Option "Device" "/dev/psaux"
	Option "Protocol" "auto-dev"
	Option "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
	Driver "wacom"
	Identifier "stylus"
	Option "Device" "/dev/input/wacom"
	Option "Type" "stylus"
	Option "Button2" "3"
	Option "ForceDevice" "ISDV4"
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	Screen 0 "Default Screen" 0 0
	InputDevice "Generic Keyboard" "CoreKeyboard"
	InputDevice "Configured Mouse" "CorePointer"
	InputDevice "Synaptics Touchpad"
	InputDevice "stylus" "SendCoreEvents"
EndSection

Section "Monitor"
	Identifier "Configured Monitor"
	VendorName "Generic LCD Display"
	ModelName "LCD Panel 1024x768"
	HorizSync 31.5 - 48.0
	VertRefresh 56.0 - 65.0
	Gamma 1
	ModeLine "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
	ModeLine "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
	ModeLine "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
	ModeLine "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

---

### Post by phenest on 2008-08-21
Are you using the rotation script in post #1? If not, then that's your problem. If so, check you have the necessary packages installed:

```
sudo apt-get install wacom-tools
```

---

### Post by olaoni on 2008-08-21
Thanks for your response phenest In answer to my stylus problems

**Are you using the rotation script in post #1**
the script in post #1 did not seem to work for me, I however found one that on as shown below

> 
!/bin/sh
if [ -n "$(xrandr | grep 768x1024)" ]; then
        xrandr -o normal
        xsetwacom set "stylus" Rotate NONE
else
        xrandr -o left
        xsetwacom set "stylus" Rotate CW
fi


I can either use F1 to rotate the screen or use the pen stylus.

**check you have the necessary packages installed:**
Yes I have the wacom tools installed

---

### Post by olaoni on 2008-08-21
A minor typo error the line in the else block is meant to read 

> xsetwacom set stylus Rotate CCW

---

### Post by phenest on 2008-08-21
That script is in post #1 too.

Does that mean it works now?

---

### Post by olaoni on 2008-08-21
Sorry for the late response, I was away from my pc. 

**No still not working**.
I can confirm that the script works by running the commands in shell and in addition to this. When I click the **rotate pen button** or when I press F1 on my laptop. 

The problem is when the screen is rotated I can't use the stylus to point to anything on the screen. Every time I try to point to icon or something on the screen the cursor moves far away from the tip of the stylus.

Just for the record I am using ubuntu Hardy and linuxwacom-0.8.1-3.

---

### Post by phenest on 2008-08-22
> **olaoni said:**
> The problem is when the screen is rotated I can't use the stylus to point to anything on the screen. Every time I try to point to icon or something on the screen the cursor moves far away from the tip of the stylus.

What does "...moves far away..." mean? Does the cursor move to a screen edge? Or moves as if the wacom has not rotated? Does it move correctly, but just not in the right place?

Could you please try and describe the cursors action in as much detail as possible, please?

---

### Post by olaoni on 2008-08-22
When the laptop is in the normal position if I place the tip of the sytlus to the screen the cursor follows the direction of the pen.

When I rotate the screen and holding the pc as a slate if I point the sytlus to the top middle of the screen the cursor appear to the left middle of the screen and if I run the pen from top to bottom the cusor goes from left to right.

Likewise if I run the pen from right to left of the screen the cusor goes from bottom to top of the screen.

Regards
Ola oni

---

### Post by olaoni on 2008-08-22
When the laptop is in the normal position if I place the tip of the sytlus to the screen the cursor follows the direction of the pen from top to bottom and left to right etc.

When I rotate the screen and holding the pc as a slate if I point the sytlus to the top middle of the screen the cursor appear to the left middle of the screen and if I run the pen from top to bottom the cursor goes from left to right.

Likewise if I run the pen from right to left of the screen the cusor goes from bottom to top of the screen.

Regards
Ola oni

---

### Post by phenest on 2008-08-23
Then the wacom has not rotated. What happens if you type:
```
xsetwacom set stylus Rotate CCW
```
from a terminal? Any error messages? If not, test the pen again. Any difference?

Report back with the results.

---

### Post by olaoni on 2008-08-23
> **phenest said:**
> Then the wacom has not rotated. What happens if you type:
```
xsetwacom set stylus Rotate CCW
```
from a terminal? Any error messages? If not, test the pen again. Any difference?

Report back with the results.
Running the above code through the terminal window did not make any difference. I can confirm that the pen works because it works under windows.

May I ask what version of wacom project and ubuntu are you using on your tablet?

---

### Post by phenest on 2008-08-23
> **olaoni said:**
> May I ask what version of wacom project and ubuntu are you using on your tablet?

I'm not. I sold my tablet a while ago, but someone here has reported the tablet works fine with Hardy and the rotate script works. I'm at a loss as to why yours does not.

---

### Post by olaoni on 2008-08-23
The problem seems to be that the following line of code
> 
xsetwacom set stylus Rotate CCW

I  don't think it is working correctly, do you know of any other command that can set the stylus pen.

---

### Post by Aearenda on 2008-08-23
Here is the script I use to toggle my TC1100 screen rotation on Ubuntu Hardy, both screen and tablet. I have it set to trigger when I click on a panel launcher.

```
#!/bin/sh
# Based on work from Patrick Coke & Tim Pope
# Modified for TC1100 by Francisco Athens
# Rewritten for current xsetwacom and xrandr vesrions by Krzysztof Kosi&#324;ski
# Adapted for me to work as a toggle - SCJ 1/3/08

# Rotate all detected wacom devices to the given direction,
# and the screen!

ROTATION=`xrandr --verbose --query | \
      grep 'default connected' | \
      sed -e 's/^.*(.*) \(.*\) (.*).*$/\1/'`

case $ROTATION in
    normal)	xsetwacom set stylus rotate ccw
		xrandr -o left ;;
    left)	xsetwacom set stylus rotate none
		xrandr -o normal ;;
esac

```

I use the stock wacom-tools 1.0.7.9.8-0ubuntu3 installed from the standard repositories. I don't have anything called linuxwacom installed. My /etc/X11/xorg.conf contains the following, **in addition to the entries required for the keyboard, screen and mouse** :
```

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"      
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
        Option          "Button2"       "3" # This is the line you need for the stylus button to right click
EndSection

Section "ServerLayout"
        [B]<other stuff goes here too - just add the following "stylus" line, 
        the Section/EndSection lines are shown here so you know where it belongs>[/B]
        InputDevice     "stylus"        "SendCoreEvents"
EndSection

```

---

### Post by olaoni on 2008-08-23
Hi Aearenda I just tried the script you proivded and things are still the same. I don't know if it is possible for you to try the copy of xorg.conf I posted in post #71 on you tc1100.
I was just wondering if the ordering of the entries in the xorg file play any role to this behaviour.
I am very new to linux so can you elaborate a bit more on the statement *stock wacom-tools 1.0.7.9.8-0ubuntu3 installed from the standard repositories*

I built the wacom_drv.so I am using from the wacom project website and it is labeled 
linuxwacom-0.8.1-3

---

### Post by phenest on 2008-08-24
> **olaoni said:**
> Hi Aearenda I just tried the script you proivded and things are still the same. I don't know if it is possible for you to try the copy of xorg.conf I posted in post #71 on you tc1100.
I was just wondering if the ordering of the entries in the xorg file play any role to this behaviour.
I am very new to linux so can you elaborate a bit more on the statement *stock wacom-tools 1.0.7.9.8-0ubuntu3 installed from the standard repositories*

I built the wacom_drv.so I am using from the wacom project website and it is labeled 
linuxwacom-0.8.1-3

The xorg.conf has nothing to do with rotation except to tell the X server to use the stylus. But seeing as you've mentioned that you're using a custom built driver, then that is your problem. This How To was not designed to be used with custom drivers. If you're using a driver obtained from the Wacom Project, then you need to discuss it with them, as it is outside the scope of this tutorial.

For someone who is new to Linux, I'm amazed you managed to custom build a Wacom driver, but you can't follow this How To.

If I were you, I would re-install Hardy fresh, and read post #1 again taking note of sections for Gutsy. It does work provided you don't try and add stuff that isn't there.

---

### Post by Aearenda on 2008-08-24
Olaoni, I agree with Phenest, your problem is most likely to do with the custom drivers you have installed. That's what I meant in my post - I haven't taken anything from Wacom's site, all I did was ```

sudo apt-get install wacom-tools
``` and this installed the required drivers for me with no further fuss.

EDIT: By 'no further fuss' I meant no need to compile anything - I stll had to modify xorg.conf as described earlier.

---

### Post by olaoni on 2008-08-25
Thanks for your support phenest and Aearenda. I will re-install ubuntu at the earliest opportunity I get and let you know how it went.

Just for the record when I installed wacom-tools I used is the above command. The reason for the custom build was to get get the pen buttons to work.

The tutorial I followed was from:-[http://ubuntuforums.org/showthread.php?p=3672701#post3672701]("http://ubuntuforums.org/showthread.php?p=3672701#post3672701")
And like I mentioned in my first mail I got the pen buttons working satisfactorily.

Moreover the tutorial used ***linuxwacom-0.7.8-3.tar.bz2***. Which when I built did not work under ubuntu Hardy. So I had to build with linuxwacom-0.8.1-3.tar.bz2 which does work (Pen button functionality at least).

---

### Post by Aearenda on 2008-08-25
Good luck! Just for the record, I have never bothered with trying to get the extra buttons to work as described in that thread.

---

### Post by phenest on 2008-08-26
olaoni: The thread you refer to is something I and another member were working on, and indeed, did get it working. We did both submit our findings to the Wacom Project, but heard nothing back. Of course, our fix was only a workaround and not a true fix. If I still had the tablet, I would have worked on it further. It's a shame those buttons still don't work 'out of the box'.

---

### Post by WebBuddha on 2008-09-12
Hello,

I've tried it also with > sudo apt-get install wacom-tools but it was'nt workling for me.
Did I have to run the How-To also? I thought that it should work with the wacom-tools only?

Regards
WebBuddha

---

### Post by phenest on 2008-09-12
> **WebBuddha said:**
> Hello,

I've tried it also with  but it was'nt workling for me.
Did I have to run the How-To also? I thought that it should work with the wacom-tools only?

Regards
WebBuddha

If you read the 'How To', you will see you need to amend the xorg.conf file.

---

### Post by trksh22 on 2008-09-22
Can someone help me? None of the changes are remaining in terminal. I cannot get the pen to work at all.

---

### Post by phenest on 2008-09-23
> **trksh22 said:**
> ...None of the changes are remaining in terminal...

Not sure what you mean by that. But if you follow the guide **exactly** as shown in the first post of this 'How To', it **will** work. Please persevere as the majority of people having problems have simply missed a step.

---

### Post by trksh22 on 2008-09-23
Thanks for replying. That's the thing, I don't know what I am doing wrong. I open up terminal, type in the nec things, close out. No changes saved. I reopened terminal, retyped everything, waited for it to "automatically save" closed out, then nothing. I tried looking at other tuts but nothing says what I should do after I am done editing something in terminal. There is no way to save my changes. 

After that the nest step is to type in some code and save it as (I forget what) but where would I do that?

Thanks in advance. I am a total newbie. I am reading, I promise I am.... just not getting anywhere. I just need it "dumbed down" LOL. 

Thanks in advance...

---

### Post by phenest on 2008-09-23
Ok. I think I know what you're getting at. Are you trying to edit files in a terminal? If you're using nano, Ctrl-X will prompt you to save. Press 'Y' and 'Enter', and it will be saved. If that confuses you, then use gedit, e.g.:
```
gksudo gedit /etc/X11/xorg.conf
```
Remember to use gxsudo for graphical apps and sudo for terminal apps.

---

### Post by Aearenda on 2008-09-23
Phenest means 'use gksudo for graphical apps', gxsudo is a typo. Gksudo is a way of gaining admin privilege while running a graphical application. Sudo is a way of gaining admin privilege when running a command-line application.

---

### Post by trksh22 on 2008-09-23
Yes! That is what I need. I promise I did read, tutorials and manuals but nothing I read (yet) had explained that. If you know of a basic tut that expounds upon what you just said then I would be happy to look at it (but no pressure, I am happy enough just knowing this!)


*Remember to use gxsudo for graphical apps and sudo for terminal apps.*

Yet another silly question, what would be considered a "graphical app"? Thanks!!

---

### Post by trksh22 on 2008-09-23
.....

---

### Post by trksh22 on 2008-09-23
The same thing has happened to me! It's so hard to get any consistant help. I am about ready to give up. I don't want to, but it looks like I don't have a choice now! I can't get the screen to change back, no matter what I do. I couldn't (and still can't) get the pen to work. This is depressing. I am at a lost. Help is ***very ***hard to come by, even on this site... I guess Ubuntu isn't for everyone...... :(


> **okrichie said:**
> K am starting to get really upset about this.. I've installed Ubuntu on my tc1100, it worked fine apart from the usual; stylus, extra buttons etc.. 

I started messing with this tutorial and a couple of others such as for the 'soft buttons' and the hardware buttons like Q. 

This is the second time now, after hours of compiling stupid wacom drivers and messing in the xorg.conf, I have reached the same problem I got after a few hours of messing the first time; and I was honestly, really careful this time.

What's going on? Well the stylus still doesn't work. Now the graphics are set to only 800x600max and I can't change it. I tried restoring an original xorg.conf backup; it did NOT help at all..

Why is this such a demanding problem? Why are all the solutions to these issues so cryptic? Why do these solutions not seem to work and at the same time cause MORE trouble?

Has anyone encountered this? I'm obviously being a complete moron and doing it wrong. So take pity and help please?

I got the stylus to work once, using an xorg.conf file I downloaded that someone else made (I think for a slightly different distro of linux), but that seemed to cause the same graphics problem; so I formatted and tried over, being more careful to self-build my own xorg.conf rather than slap my name on someone else's but it hasn't worked!

---

### Post by Aearenda on 2008-09-24
A graphical application is something that creates its own window on the desktop, and can lay out that window with buttons and pictures and other stuff anywhere it likes - a classic "Windows Program" - in contrast to applications which run in a terminal (or 'command-line') session, which are constrained only to use letters, not pictures - as if they were still running on an old-fashioned teletype terminal, or on MS-DOS before the days of Windows. 

Gedit is a graphical text editor. You start it by using the mouse to find 'Text Editor' in the Accessories menu. Then you have to click on 'File->Open' and select a file to get started.

Nano is a command-line text editor that runs in a terminal session. You start it by typing 'nano <filename>' in a command line session, which might have been started by using the mouse to fine 'Terminal' in the Accessories menu, for example. Nano runs inside the Terminal window. You can also use it from a text logon session, if the windowing system fails to start.

Giving instructions using terminal commands is usually much more succinct and exact than telling people to click on menus and buttons, which is why they come up so often in the forums.

Consistent help is hard to find simply because everyone is a volunteer here, and everyone has different experiences. We can only advise based on what we have encountered ourselves. Sometimes it takes a while to get an answer because we have to go out and earn money, or because we live in different time zones. Whether you find this good or bad depends on the level of your expectations. I recommend this as a way to get the best responses: [http://www.psychocats.net/ubuntucat/getting-the-best-help-on-linux-forums/](http://www.psychocats.net/ubuntucat/getting-the-best-help-on-linux-forums/)
Also see: [http://ubuntuforums.org/showthread.php?t=232059](http://ubuntuforums.org/showthread.php?t=232059)

Here's some help on using the terminal: [http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)

And here's some more general help on Ubuntu:
[http://book.opensourceproject.org.cn/distrib/ubuntu/official/](http://book.opensourceproject.org.cn/distrib/ubuntu/official/) especially Chapter 4 on the Terminal.


Having said all that, it is true that Ubuntu isn't for everyone. Being an Ubuntu user can be downright frustrating at times. I have used it for about 3 years now, yet last week I contemplated switching back to Windows XP - because I can't get my scanner to work on Ubuntu. But then I plugged my XP drive back into my TC1100, and started it up, and it reminded me of all the things I was trying to escape - and I fell in love with Ubuntu all over again. It's never going to be a completely smooth ride, simply because the hardware manufacturers don't all want to play. But then, neither is Vista, or XP, or OS/X. 

Anyway, I hope this helps you to make up your mind to be persistent! People WILL help, given time, if you are clear about what you need, what has happened, follow instructions carefully, and stay patient.

trksh22 said:> I can't get the screen to change back, no matter what I do. I couldn't (and still can't) get the pen to work.

I'd like to help you, but I don't know what you mean by "I can't get the screen to change back". What has it changed to? 

Also, you say you can't get the pen to work - can you summarise what you have done to try to make it work?

---

### Post by trksh22 on 2008-09-24
Thanks, I wrote my last email out of desperate frustration, lol. Thank you for taking the time to explain things and even provide other links. This is all so new, I knew that there was a learning curve, but I have become so accustomed to windows that I am only slightly overwhelmed by all that I need to know. But, I have to start somewhere, huh? ;)

As for the screen, I was able to just reinstall Ubuntu and now it works.

---

### Post by trksh22 on 2008-09-24
fixed with reinstall. Please ignore, I don't think I have the privileges yet to delete my own post.

---

### Post by trksh22 on 2008-09-24
Can anyone comfirm that Ubuntu tablet functions (use of the pen) will work with a replacement/non stock pen. Maybe that is why it won't work for me? This is the pen that I have (which worked fine in Xp):

[Pen with Eraser]("http://direct.wacom.com/stores/5/Penabled_Tablet_PC_Eraser_Pen_P1047C72.cfm")

---

### Post by Aearenda on 2008-09-24
I'm glad to hear you are making progress! That's good news.

I'm using the standard pen that came with the TC1100. I see no reason why your pen should not work, but since it has an eraser you will need extra stuff in your /etc/X11/xorg.conf. I suggest you do this:

1. Press ALT and F2 (this brings up the 'run' box, like Windows and R or Start->Run on XP).

2. Start the text editor and open the appropriate configuration file by pasting the text in this box:```
gksudo gedit /etc/X11/xorg.conf
```and then press <enter>. Fill in your password if you are asked for it.

3. In the text editor, do File->Save As and make a copy of the file somewhere where you can find it in an emergency!

4. Now close the Text Editor, and then re-open the original file exactly as in step 2.

5. Add the following to the file by copy and paste - in mine, it comes straight after the keyboard and mouse sections. It must follow an 'EndSection' line, unless it is at the very start of the file.
```

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"      # Change to
                                                        # /dev/input/event
                                                        # for USB
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
        Option          "Button2"       "3" # This is the line you need for the stylus button to right click
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"      # Change to
                                                        # /dev/input/event
                                                        # for USB
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
        Option          "Button2"       "3"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"    # Change to
                                                        # /dev/input/event
                                                        # for USB
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
        Option          "Button2"       "3"
EndSection


```
I'm not sure you need the third section here (the 'cursor' one), but it won't hurt. I used to run my TC1100 with all three sections enabled until somebody pointed out that the TC1100 pen doesn't have an eraser. You may already have the first section ('stylus') - if so, don't duplicate it.

6. Still in the text editor, make sure the section that links all the devices together looks something like this:```
Section "ServerLayout"
	Identifier	"Default Layout"
	screen "Default Screen"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection
```
It's the three 'InputDevice' lines that matter here - just add them if they are not there - **don't change anything else!**

7. Now save the file and close the text editor.

8. Start the package manager from the menu using System->Administration->Synaptics Package Manager.

9. In the list of packages, find 'wacom-tools'. You can do this by clicking once in the package list area, then typing 'wacom' - without the quotes - which make Synaptic do a stem match on the name. Click in the package list area again to dismiss the little stem-match box.

10. If the square box next to the wacom-tools package is empty, right-click on that line and choose 'install', accept any dependencies it might need, then click on 'Apply' in the tool bar, then click on 'Apply' in the confirmation box; wait for the installation to complete.

11. Close Synaptic Package Manager.
[Aside: steps 8 to 11 could have been done in a command-line terminal simply by pasting in the following command: 'sudo apt-get install wacom-tools' and then pressing Y to confirm - much easier!!]

12. Now log out, and when the login screen appears, press <CTRL> and <ALT> and <BACKSPACE>. This causes X-Windows to restart. X-Windows is the graphical subsystem we use on most Linux systems - without it, all we have are character-mode sessions. Doing this makes the changes we just made take effect, without doing a complete restart.

13. Log in again, and see if the stylus and eraser work, using gimp or another stylus-aware app. The stylus should work anywhere - the eraser may only work where it makes sense. If they work, you're done; otherwise, continue.

14. Diagnostic only: start a command-line session from Accessories->Terminal and type:```

xsetwacom list dev
```The output from this should be something like```

stylus     stylus
eraser     eraser
```

15. Recovery: If after step 12 all you get is a black text-mode screen, rather than the normal Ubuntu graphical login screen, you will need to log in in text mode with your normal username and password. 
15.1 If you see no writing on the black screen at all, try pressing <CTRL> and <ALT> and <F1> - this should switch to the first text-mode console, and you should be able to log on there.
15.2 Type ```

sudo cp <the-name-of-the-copy-you-made-in-step-3> /etc/X11/xorg.conf<ENTER>
```
15.3 Type ```
reboot<ENTER>
```

Please let us know how you get on! Good luck!

---

### Post by trksh22 on 2008-09-25
Aearenda, firstly, thanks for breaking everything down for me. I needed it to be dumbed down :) 

I did follow your directions exactly and got the same results as before. When I did Step 12 thing, I got the same error message as before "*Ubuntu is running in low graphics mode. Your screen and graphics card could not be detected. ... you need have to configure the display yourself."*


After I logged in, I ran the "Xsetwacom" thing and it did not return anything, just repeated the input line (name@blank etc)

I feel like I am so close :)


ETA: (**I have since restored my back up file so my graphics card and everything is recognized and back to the default settings.**)

---

### Post by Aearenda on 2008-09-25
Interesting - I guess the next step is for you to post the /etc/X11/xorg.conf file that you had as a result of step 7. Mine is below for comparison. Note that the cursor and eraser are commented out in mine, since I have a stock pen.

I wouldn't expect xsetwacom to return anything without the changes in that file being present.

Hmmm, I wonder - do you have the Nvidia driver installed (I do)?

```

# xorg.conf (X.Org X Window System server configuration file)
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
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"vmmouse"
EndSection

#Section "InputDevice"
#	Identifier	"Synaptics Touchpad"
#	Driver		"synaptics"
#	Option		"SendCoreEvents"	"true"
#	Option		"Device"	"/dev/psaux"
#	Option		"Protocol"	"auto-dev"
#	Option		"HorizEdgeScroll"	"0"
#EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"      # Change to
                                                        # /dev/input/event
                                                        # for USB
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
        Option          "Button2"       "3" # This is the line you need for the stylus button to right click
EndSection

#Section "InputDevice"
#        Driver          "wacom"
#        Identifier      "eraser"
#        Option          "Device"        "/dev/input/wacom"      # Change to
                                                        # /dev/input/event
                                                        # for USB
#        Option          "Type"          "eraser"
#        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
#        Option          "Button2"       "3"
#EndSection

#Section "InputDevice"
#        Driver          "wacom"
#        Identifier      "cursor"
#        Option          "Device"        "/dev/wacom"    # Change to
                                                        # /dev/input/event
                                                        # for USB
#        Option          "Type"          "cursor"
#        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
#        Option          "Button2"       "3"
#EndSection


Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
	# Option		"ConnectedMonitor"	"DFP"
	Option		"RandRRotation" "on"
	Option		"NvAGP" "1"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen "Default Screen"
        InputDevice     "stylus"        "SendCoreEvents"
#        InputDevice     "cursor"        "SendCoreEvents"
#        InputDevice     "eraser"        "SendCoreEvents"
#	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

---

### Post by trksh22 on 2008-09-25
Ok, I will redo everything and post what I get. I really did learn a lot from your tutorial so if this doesn't work out I didn't walk away empty handed. (I also have Ubuntu stored on my desktop.) I will post the results as soon as I finish....

---

### Post by trksh22 on 2008-09-26
> **Aearenda said:**
> 
       

6. Still in the text editor, make sure the section that links all the devices together looks something like this:```
Section "ServerLayout"
	Identifier	"Default Layout"
	screen "Default Screen"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection
```
It's the three 'InputDevice' lines that matter here - just add them if they are not there - **don't change anything else!**


Ok, wow. I got it to work. THANK YOU :) I know what I did wrong, too. You see what you put in bold up there, the "don't change anything else" part? 

That's what I didn't do!

I thought I was following the directions line by line but I wasn't! In the part of code you mentioned earlier, I had an extra line "InputDevice "touchpad" "Synaptics touchpad" (or something like that). I was removing that line, and then putting in the the three so that it looked like the one above. I think my reasoning was that it wasn't a regular laptop so it didn't have a touchpad so it was ok to remove it. Last night I took a break and decided to try again in the morning. It's weird because you made it clear several times throughout this topic that things should be "followed exactly". Anywho, this morning I retried without editing anything and it worked.

In case you were wondering, I AM very embarrased but happy it works and always has worked and lastly, very, very thankful to you and the others that tried helping me.

---

### Post by Aearenda on 2008-09-26
That's excellent news, and I'm glad to have been able to help! Don't be embarrassed, we are all learners here, and if you never get anything wrong, you never learn anything new.

The touchpad part isn't needed for the TC1100, but the 'screen' line most certainly is - and that's probably what led to your problem with the screen :-)

Anyway, I hope you enjoy using Ubuntu on your TC1100 - and don't hesitate to ask if you need more help! The difficult thing with the forums is having new messages seen by the right people - there are so many flowing by all the time, I'm sure I only see a very small portion of them. But I'll leave this thread subscribed, so if you need help with the TC1100, I'll definitely see that.

---

### Post by phenest on 2008-09-28
> **trksh22 said:**
> Ok, wow. I got it to work. THANK YOU :) I know what I did wrong, too. You see what you put in bold up there, the "don't change anything else" part? 

That's what I didn't do!

**Information for all:**

Please remember, that if you're going to follow any guide in the Ubuntu forums, you must do what the instructions tell you to do, and nothing else. It will save you a lot of time and bother of asking the same questions over, and over again, and getting nothing but headaches. ](*,)

As an example: some here seem to think that because the pen won't work, that maybe they need to install the drivers. If the guide doesn't tell you to install them, then that is because you don't need to. If you decide to install non-standard drivers, and things break, then that becomes outside of the scope of this guide. If you wish to use non-standard stuff, then do it (at the very least), after you have it working first. :-k

The guide is all you need to make this work. A lot of stuff (particularly drivers), already ships with a basic Ubuntu installation, so this guide is no more than a few 'tweaks'. So don't make it harder for yourself by adding stuff that isn't there.

Have fun. \\:D/

---

### Post by trksh22 on 2008-09-28
Yes, thanks!! I was definitely making everything MUCH harder than it needed to be. Had I just read what was there, then I wouldn't have had to go through days of feeling like I couldn't do it.

Hopefully someone new will come along, read what I went through, and make sure that they follow the directions and know what NOT to do :)

---

### Post by g0ldenchild562 on 2008-11-07
Hi I'm new, how do I edit the xorg.conf? I keep getting an error saying I dont have permission.

---

### Post by zoomy942 on 2008-11-07
> **g0ldenchild562 said:**
> Hi I'm new, how do I edit the xorg.conf? I keep getting an error saying I dont have permission.

open a terminal window and type

suod gedit

---

### Post by Aearenda on 2008-11-07
That's a mis-type - it should be```
sudo gedit /etc/X11/xorg.conf
```or better ```
gksudo gedit /etc/X11/xorg.conf
```which will ask for the password using a dialog box instead of the terminal.

You can also press ALT and F2 to bring up the 'Run application' box, and do the 'gksudo' version in there - this is the equivalent of start->run on Windows.

---

### Post by Aearenda on 2008-11-07
I have my TC1100 running Ubuntu 8.10 (Intrepid Ibex) reasonably well now. For the record, I had to...

1. Install the nvidia beta drivers from intrepid-proposed (now in intrepid-updates) to enable rotation (see earlier in this thread) and my external monitor. See [http://albertomilone.com/wordpress/?cat=2](http://albertomilone.com/wordpress/?cat=2) for comments and instructions. Alberto does a great job. This driver presently has a bug with KDE 3 (only affects me if I have compositing turned on) and Wine fonts but if you don't use these it's fine on the TC1100 ([http://www.nvnews.net/vbulletin/showthread.php?t=122350](http://www.nvnews.net/vbulletin/showthread.php?t=122350), and now there's a workaround at [http://nancib.wordpress.com/2008/11/02/does-anyone-know-what-borked-wine-this-week/](http://nancib.wordpress.com/2008/11/02/does-anyone-know-what-borked-wine-this-week/)). I tried nouveau but it was too slow. The nv driver works fine if you don't need to use external screens or projectors. The nvidia driver works fine with metacity compositing and even allows compiz to be turned on, but compiz wasn't stable.
UPDATE: The nv driver supports rotation too. If you don't need to use an external screen or projector, and you don't need 3D acceleration, the nv driver will be enough and it lets you use hibernate and standby properly. [Post 126]("http://ubuntuforums.org/showpost.php?p=6273546&postcount=126") tells how.

2. UPDATED - 21 November 2008: Install Ndiswrapper and the Windows XP driver for the wireless network, taken from HP's SP30102A update. This seems to be more reliable than ath5k and to associate quicker than ath_pci, for me. It doesn't introduce any of the mouse jerkiness I saw with the backported drivers installed, and doesn't need a newer Network Manager.

So, don't do this: [I]OLD STEP 2: Install the latest network-manager from PPA to overcome a wireless association timeout with ath_pci, and it is still much slower to associate than Hardy was. See [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/292054](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/292054).
UPDATE - 19 November 2008: I have installed linux-backports-modules-intrepid to see if the ath5k driver improves the association times. The process is described in many forum threads - the important bit is to blacklist ath_hal and ath_pci in /etc/modprobe.d/blacklist. This improves association time considerably, and ath5k performs much better than it did during the Intrepid alpha builds. However, there is collateral damage: a new version of ssb is installed as well, but no matching b44 driver, so we lose *wired* networking! Also, mouse responsiveness suffers for some reason I have yet to fathom. I have kludged a working system by overwriting the updated ssb driver with the stock ssb driver for the same kernel version and then doing 'update-initramfs -u -k `uname -r`' but I'm not recommending this change to anyone else.
LATER THE SAME DAY: There's an update to linux-backports-modules-intrepid in intrepid-proposed that fixes the b44 issue properly. It still leaves the mouse jerky every so often when wireless is enabled, and it seems that this coincides with when Network Manager is re-associating, which it does every two minutes![/I]

3. Install uswsusp to make hibernate worth the effort - otherwise it was slower to wake from hibernate than to do a cold boot. This prevents going to standby, but I've never been able to get it to resume from standby reliably with the nvidia driver anyway. See [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/246053/comments/18](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/246053/comments/18). I installed uswsusp in Synaptic and then modified /etc/pm/config.d/00sleep_module to contain ```
SLEEP_MODULE="uswsusp" # was "kernel"
SUSPEND_MODULES="ath_pci ath_rate_sample ath_hal"
```

UPDATE - 29 Nov 2008: Hibernate still fails randomly with the nvidia driver. I suppose it IS still a beta <sigh>. This overrides my comment on 16th about it not having failed. 
UPDATE - 16 Nov 2008: It seems the unreliability was associated with running the netbook-launcher - that is, it hasn't failed since I stopped running that. Also, to get wireless to resume after hibernation, I find I have to use tc1100-wmi to turn it back on (see below). I made a copy of /usr/lib/pm-utils/sleep.d/10NetworkManager in /etc/pm/sleep.d and added 'echo 1 > /sys/devices/platform/tc1100-wmi/wireless' before the 'thaw' dbus command to wake Network manager. Actually this probably ought to have gone in a separate entry, say '15TurnWirelessOn' with just the echo bit in it. The SUSPEND_MODULES list only needs ath_pci in it. I have blacklisted agpgart in /etc/modprobe.d/blacklist and set agp=off in /boot/grub/menu.lst (see the line starting '# defoptions', on mine it is '# defoptions=quiet splash resume=/dev/sda5 vga=791 agp=off' - note that the leading '#' is important here) and nvAGP="1" in /etc/X11/xorg.conf. Hibernate works for me, but standby won't work reliably with the nvidia driver, and if it does come back, the wireless hardware is clobbered until next reboot. 

UPDATED - 15 December 2008: I have found that putting 'Option "NvAGP" "0"' in the xorg.conf file allows standby to work reliably with the nvidia driver, and it doesn't clobber the wireless! I have to turn the wireless on though, using tc1100-wmi.

4. Turn off keypad control for the mouse, when using an external keyboard, from the keyboard preferences ([http://nancib.wordpress.com/2008/03/17/fixing-the-borked-numeric-keypad-in-ubuntu-hardy/](http://nancib.wordpress.com/2008/03/17/fixing-the-borked-numeric-keypad-in-ubuntu-hardy/) has simple intructions, bug is [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-keyboard/+bug/197589](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-keyboard/+bug/197589)).

5. Fix my external CD drive so it didn't close the drawer as soon as it was opened ([https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316/comments/34](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/283316/comments/34)).
UPDATE: This is now fixed automatically.

6. Load the tc1100-wmi module to gain control of screen brightness and the wireless kill switch (see earlier in this thread). This now works without the use of sudo. To turn wireless off do```
echo 0 > /sys/devices/platform/tc1100-wmi/wireless
``` and to turn it back on ```
echo 1 > /sys/devices/platform/tc1100-wmi/wireless
```to enable jogdial brightness do ```
echo 0 > /sys/devices/platform/tc1100-wmi/jogdial 
```and to return to normal (page up/down) do ```
echo 1 > /sys/devices/platform/tc1100-wmi/jogdial 
```
UPDATE - 19 November 2008: Brightness isn't working every time, neither is the jogdial doing its normal pageup/pagedown function reliably. Probably associated with the xmodmap experiment I have done (but not yet written up) to try to get the side button to control the internal/external screen as in Windows.
UPDATED - 15 December 2008: I have found that it is necessary to use tc1100-wmi to set the normal jogdial mode after waking from standby.

7. Installed wacom-tools and copied the pen details from my Hardy xorg.conf (see earlier in this thread). I believe there is a better way to do this using hal fdi files in Intrepid, but I haven't looked at that yet.

8. Enabled laptop-mode - see Intrepid comments in [https://wiki.ubuntu.com/PowerManagement#How%20to%20get%20disks%20idleing%20correctly%20(without%20excessive%20load%20cycling](https://wiki.ubuntu.com/PowerManagement#How%20to%20get%20disks%20idleing%20correctly%20(without%20excessive%20load%20cycling)) and then monitor the Load_Cycle_Count in smartctl to see if you need to do anything about your drive. 

UPDATE: I have a non-standard 7200 rpm Hitachi drive in my TC1100. I have set /etc/laptop-mode/laptop-mode.conf to use 254 for HDD power management on both battery and AC power, and to do idle spindown after 60 seconds on battery. I don't subscribe to the theory that battery power = increased likelihood of physical shock. YMMV.


9. [ADDED 25 November] Disabled input device hotplugging using evdev. This was crashing X whenever I plugged my keyboard in. I found this the hard way after taking a morning's handwritten notes on a course using Xournal, which does not have a timed-save feature. My notes were lost when I plugged the keyboard in during the lunch break. I reverted to Hardy again for the rest of the course (luckily I have a dual-boot setup). I later found that the X crash would occur if I put the tablet in the dock, or if I plugged in the normal keyboard. I don't know if this is related to my attempts to modify the side key map (which I have successfully done on Hardy, so that I can switch monitors using the same side key as the Windows XP driver uses), or whether it has had the potential to crash this way from day 1.
I added the following to xorg.conf:
```
Section "ServerFlags"
	Option "AutoAddDevices" "false"
EndSection

```And I set the keyboard layout to 105-key international.



Other stuff not specific to the TC1100:
I also upgraded to OpenOffice 3 (but see below) from the PPA ([http://www.theopensourcerer.com/2008/10/14/how-to-install-openofficeorg-30-on-ubuntu-intrepid-ibex/](http://www.theopensourcerer.com/2008/10/14/how-to-install-openofficeorg-30-on-ubuntu-intrepid-ibex/) has a simple how-to), Sunbird 0.9 from Mozilla (just follow their instructions - install in /opt/sunbird), and Thunderbird, xournal, vym, k3b and amarok from the standard repos. 

UPDATE: I find amarok stutters a bit - now trying banshee (It turned out not to be Amarok's fault - it works fine). I have also installed vym 1.12.0 by compilation from source to fix a bug on opening saved files when saved with embedded notes. This also allows landscape printing to work properly, which it didn't in Hardy. Xournal doesn't work properly with the pen unless the zoom factor is set to page width.

UPDATE - 21 Nov 2008: I have downgraded OpenOffice again, owing to slowness and some apparent corruption in saved writer documents.

25 Nov - I am beginning to think I need to re-install from scratch, as I have had to muck with so much to get Intrepid working that I no longer trust the installation. There have been too many failed attempts to fix things on my part, and I am not good at cleaning up after failed fixes; so now it keeps biting me, like with the keyboard X crash losing my course notes. Intrepid has been by far the hardest release to install on the TC1100 (note that I don't do upgrades - I do a fresh installation into a separate partition each time, so this isn't due to a long series of upgrades; and I've done every release since Breezy) and it's the first one I have seriously contemplated skipping (which also means Hardy set a high standard that is hard to match in a non-LTS release).

Jan 2009 - In the end, though, Intrepid has ended up being my best-performing release so far! This is because of getting suspend to work properly.

---

### Post by g0ldenchild562 on 2008-11-07
How do I enable the visaul effect? When I do try to enable it, it keeps telling me that the desktop can't enable.

---

### Post by Aearenda on 2008-11-07
g0ldenchild562: If you are running Hardy, it won't work because the code checks for 64Mb Video RAM and the TC1100 only has 32Mb. You can hack it, but it gives black screens all over the place and isn't worth the effort. In Intrepid, it will turn on, but it doesn't stay on for me.

You can try Metacity compositing - see [http://ubuntuforums.org/showthread.php?t=924124](http://ubuntuforums.org/showthread.php?t=924124) but see [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/218322](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/218322)

---

### Post by g0ldenchild562 on 2008-11-07
Hey thanks for the response, I actually have the original Ubuntu 8.10. I don't understand the difference between the hardy or the other versions out there. Anyways I manage to get it working by installing the Envyng driver. The effects are so cool!!!!

---

### Post by g0ldenchild562 on 2008-11-07
I'm still having problems getting the stylus to work. I did everything that was posted on the first page.

---

### Post by Aearenda on 2008-11-07
Please post (e.g. by copy and paste from a terminal session) the output from ```
cat /etc/X11/xorg.conf
```and the version number output from```
xsetwacom -V
``` Mine look like this for 8.10:

```
$ cat /etc/X11/xorg.conf
Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"      # Change to
                                                        # /dev/input/event
                                                        # for USB
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
        Option          "Button2"       "3" # This is the line you need for the stylus button to right click
EndSection

Section "Device"
	Identifier	"Configured Video Device"
#	Driver "nv"
	Driver "nvidia"
	Option "AddARGBVisuals" "True"
	Option "AddARGBGLXVisuals" "True"
	Option "NoLogo" "True"
	Option "RandRRotation" "on"
	Option "NvAGP" "1"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen "Default Screen"
        InputDevice     "stylus"        "SendCoreEvents"
EndSection

$ xsetwacom -V
0.1.7

```Ignore the nvidia stuff - concentrate on the stylus bits.

---

### Post by g0ldenchild562 on 2008-11-08
Hey thanks I got it working! Now i need to fix the hibernation error.

---

### Post by Aearenda on 2008-11-16
I've just added an update to post 116 concerning hibernation with Intrepid.

---

### Post by phenest on 2008-11-17
> **Aearenda said:**
> I've just added an update to post 116 concerning hibernation with Intrepid.

I've added a link to post #1 referring users to post #116. Perhaps you could keep that post up to date with new fixes, etc as they occur.

---

### Post by Aearenda on 2008-11-18
> Perhaps you could keep that post up to date with new fixes, etc as they occur.I will - but for now I have retreated to Hardy again as I am on a course where there is occasional access to the internet via wireless, and the slow association problem in Intrepid is unbearable!

EDIT: This was resolved using ndiswrapper and the XP wireless driver - so I'm now back on Intrepid again!
And then later back again to Hardy, because of keyboard hotplugging crashing X...

---

### Post by Aearenda on 2008-11-29
I have just discovered that in *Hardy* the default "nv" driver will support rotation, and that the striping it shows in colour gradients at times can be prevented. I have the following entries in the "Device" section of /etc/X11/xorg.conf:
```

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nv"
	Option		"Rotate"	"RandR"
	Option		"FlatPanel" "True"  # may not be needed
	Option		"FPDither" "True"
EndSection

```
With this, I can at last rotate the screen for use as a tablet AND use standby successfully! I found it in 'man nv' - too obvious!

I haven't tried it with Intrepid yet.

Now if only I could get it to switch to the external screen using the nv driver...

UPDATE: It does work with Intrepid too, so long as metacity compositing is turned off (and generates an X crash if it's on).

---

### Post by gdville on 2008-12-14
Help! I cannot get the pen working after installing nVidia and wacom-tools and updating xorg.conf:

```
Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"      # Change to
                                                        # /dev/input/event
                                                        # for USB
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
        Option          "Button2"       "3" # This is the line you need for the stylus button to right click
EndSection

#Section "InputDevice"
#        Driver          "wacom"
#        Identifier      "eraser"
#        Option          "Device"        "/dev/input/wacom"      # Change to
                                                        # /dev/input/event
                                                        # for USB
#        Option          "Type"          "eraser"
#        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
#        Option          "Button2"       "3"
#EndSection

#Section "InputDevice"
#        Driver          "wacom"
#        Identifier      "cursor"
#        Option          "Device"        "/dev/wacom"    # Change to
                                                        # /dev/input/event
                                                        # for USB
#        Option          "Type"          "cursor"
#        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
#        Option          "Button2"       "3"
#EndSection


Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
	Option		"RandRRotation" "on"
	Option		"NvAGP" "1"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen "Default Screen"
        InputDevice     "stylus"        "SendCoreEvents"
#        InputDevice     "cursor"        "SendCoreEvents"
#        InputDevice     "eraser"        "SendCoreEvents"
#	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load		"glx"
EndSection

```

When I query the device with xsetwacom, I get only a prompt back. 

I've tried uninstalling nVidia and wacom-tools and reinstalling in various combinations to no avail.

I'll confess to being a newbie, but I had this working on this machine a month ago with a different hard drive. I am nearing wit's end so any new ideas would be very much appreciated.

---

### Post by Aearenda on 2008-12-14
Xorg.conf looks right. Please post your /var/log/Xorg.0.log. To do that, start a command line, then paste in the following command:

```
zip  xlog.zip /var/log/Xorg.0.log
```

Then go into advanced mode on your forum reply, click the paperclip icon, click the top 'browse' button and find the xlog.zip file just created.

---

### Post by gdville on 2008-12-17
Wow, I can't believe you fixed it! I'm not sure what happened, but the pen has magically begun working again. I swear, I didn't do anything since posting, other than shutting down and running windows for a couple days. 

I have attached the log file (after stripping out all my passwords and bank account info:eek:). If you are able to tell what the problem was, it would be gratifying to know what the problem was. I'm sure I won't be the only one to find it useful. 

Thanks, it's folks like you that make me love linux!

---

### Post by Aearenda on 2008-12-17
That log file gets overwritten on each login, so now it shows the successful startup, as far as I can see. Oh well, if it's working then let's leave it working and enjoy Christmas!

---

### Post by rubbafishe on 2008-12-20
ok so i may sound like a moron here but im fresh to linux and have had too many problems just getting it running.

im trying to get ubuntu 8.10 *intrepid ibex* to run on my Compaq tc1100. unfortunately the install deleted my xp partition by accident and now i've lost all the functions i got the laptop for!

problems i'm having are as follows 

no wireless (no internet at all)
no pen functions
no tablet buttons functions
can't read from my regular usb drive (i had to dedicate one to the linux install)


i've been searching forums and websites for days now with no luck. just lots of jargon and patches etc that i cant understand or get to work in the way they seem to for everyone else.

i really love this laptop and need it to work properly as soon as possible. please help. im going insane with this.

---

### Post by Aearenda on 2008-12-20
Everyone feels that way when they first start - up the creek without a paddle, and with the water running fast! Patience is needed :-) I'm writing this from a docked TC1100 running Ubuntu 8.10 with the pen, side buttons, external monitor, screen rotation and wireless working, and with which USB drives work normally, so I assure you it can be made to work. The only thing I have difficulty with at present is hibernation, but I rarely want to use that since Linux hibernation is no faster for me than a full startup on the TC1100 - I just leave it in standby when I want to save power.

By the way, to reinstall Windows XP, you would need the recovery CDs and a USB CD drive. 

First, can you confirm my understanding of how things stand with Ubuntu. 

1. You're definitely using a TC1100 (made by HP really, since they took Compaq over after the TC1000 and before the TC1100), and not a TC1000. I have a TC1000 as well, and it is much slower than the TC1100 and significantly different inside.

2. There are variants of the TC1100 - from your recall of running Windows XP, does yours have a Celeron or Pentium-M CPU, and does it have an Atheros or an Intel Wireless card? Don't worry about this now if you don't know.

3. It sounds to me as though you have used a USB-drive installation method instead of the standard CD, probably because you don't have a USB CD drive. I think this because you say 'I had to dedicate one (USB drive) to the linux install'; but alternatively, you could be saying that you have actually installed Ubuntu on the USB drive. Which is it?

4. Somehow in the process the Windows partition has been deleted or become unbootable. Is this because the partition was really deleted, or perhaps because the boot sector on the hard drive was erased? You can explore this by pressing 'ESC' when the system says 'Press Esc to enter menu' as it starts up (if it does), and then selecting the Windows XP entry on the menu, if it exists. Ubuntu will always add such an entry if it finds an existing Windows partition.

5. Does the wired network interface work? It should just work without any fiddling, once you have logged on to Ubuntu, giving you Internet access using Firefox, assuming the network it is plugged in to will offer it an IP address using DHCP, just like with Windows. If you had to configure Windows specially to make it work when wired, then the same settings will be needed for Ubuntu.

I'll leave it there for now, since the next set of instructions depend greatly on how things stand, and I don't want to make it worse.

---

### Post by rubbafishe on 2008-12-21
Thanks for helping me out here Aearenda. unfortunately i bought the tc1100 second hand, so i didn't get the recovery disk or any of the authentic windows software. this was one of the reasons i want to switch to ubuntu. i hope its not a problem where i'll have to go and buy XP tablet pc windows to make this work.

let me clear this up a little.


> **Aearenda said:**
> 

1. You're definitely using a TC1100 (made by HP really, since they took Compaq over after the TC1000 and before the TC1100), and not a TC1000. I have a TC1000 as well, and it is much slower than the TC1100 and significantly different inside.

2. There are variants of the TC1100 - from your recall of running Windows XP, does yours have a Celeron or Pentium-M CPU, and does it have an Atheros or an Intel Wireless card? Don't worry about this now if you don't know.

3. It sounds to me as though you have used a USB-drive installation method instead of the standard CD, probably because you don't have a USB CD drive. I think this because you say 'I had to dedicate one (USB drive) to the linux install'; but alternatively, you could be saying that you have actually installed Ubuntu on the USB drive. Which is it?

4. Somehow in the process the Windows partition has been deleted or become unbootable. Is this because the partition was really deleted, or perhaps because the boot sector on the hard drive was erased? You can explore this by pressing 'ESC' when the system says 'Press Esc to enter menu' as it starts up (if it does), and then selecting the Windows XP entry on the menu, if it exists. Ubuntu will always add such an entry if it finds an existing Windows partition.

5. Does the wired network interface work? It should just work without any fiddling, once you have logged on to Ubuntu, giving you Internet access using Firefox, assuming the network it is plugged in to will offer it an IP address using DHCP, just like with Windows. If you had to configure Windows specially to make it work when wired, then the same settings will be needed for Ubuntu.


1.I'm definitely using a tc1100, with the cd dock and a usb keyboard and mouse.

2.i think it runs on a Celeron cpu. i managed to get the wireless card working. the problem was i had to turn it on in the bios. now i can connect online but still have no pen features.

3.For the install of Ubuntu, i downloaded ubuntu .iso image and burned it to a cd for install. that works fine when i need it to. the usb drive is just for shuffling all the patches around. its just 2gigs so it gets frustrating.

4.When installing Ubuntu *Intrebid Ibex*, where it asks to select or make a partition, i had the 'clear hard drive for fresh install' option selected. i didnt realise it until after the install.  There is no XP or windows option anywhere in the boot menu.

5. now that the wireless works, i'm not too concerned about the wired connection.

so far i have tried various patches, edits to some files like xorg.conf (i have backups of the original file)but the pen and side buttons get no response.

i'm shattered having this machine on my desk with no pen features as thats the main reaon i bought the thing.

---

### Post by Aearenda on 2008-12-21
Ok, well done in getting the wireless working - that makes the rest much easier!

Let's get the pen working then! 

1. Go to system->administration->synaptic package manager

2. When it has finished getting ready, find the package 'wacom-tools'. You can do this by clicking once anywhere in the top-right pane, and then typing 'wacom' (I'd suggest quick search but the index may not be ready yet). When you see 'wacom-tools' appear in the top-right pane, click once on it to clear the little stem-match window that will have appeared.

3. If the package is already installed, the little square on the left of its name will be green; you can skip to step 4 in this case. 

3.1 If it isn't green, double-click on wacom-tools, to get it marked for installation, and if a 'Mark additional changes?' dialogue pops up, click on the 'Mark' button to accept them.

3.2 Now click the 'Apply' button on the main toolbar. A confirmation window will appear; click the 'Apply' button, and wait for the changes to be made.

4. Close Synaptic Package Manager.

5. Now press ALT and F2 to bring up the 'run' dialogue.

6. Type (or paste) in the following command:```
gedit /etc/X11/xorg.conf
```

7. Press CTRL and A to select the whole file, and the CTRL and C to copy it to the clipboard.

8. Start Firefox and use it to start a 'quick reply' to this message. Begin by telling me whether you had to install wacom-tools or not.

9. Then press CTRL and V to paste the contents of /etc/X11/xorg.conf into the reply, so that I can see what we should do next.

10. Post the reply.

11. Close the text editor.

---

### Post by rubbafishe on 2008-12-22
Wacom-tools was already installed in the package manager.

here is my xorg.conf file:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder57)  Mon Oct 27 14:37:20 PST 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "stulus" "SendCoreEvents"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS4"
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"
  Option	"Mode"		"Absolute"
  Option	"Button2"	"3"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS4"
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"
  Option	"Mode"		"Absolute"
  Option	"Button2"	"3"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

---

### Post by Aearenda on 2008-12-22
Thanks, I think the pen device should be /dev/input/wacom not /dev/ttyS4. That xorg.conf looks 'old'. 

To prepare the way for getting the other TC1100 features working, I think it's probably a good idea for you to move your existing xorg.conf out of the way, and use a copy of mine. There are several differences, which should be clear from the comments.

To move the existing file, I suggest you do ALT and F2 and start gedit as before, then use 'Save As' to save the file in your own folder somewhere. Then close gedit.

Next, do ALT and F2 and this time add 'gksudo' to the front of the command, like so:```
gksudo gedit /etc/X11/xorg.conf
```Select All and remove the existing contents, then paste in the details below, and save the file.

```
Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
        Option          "Button2"       "3" # This is the line you need for the stylus button to right click
EndSection

# Don't need cursor or eraser devices on TC1100

Section "Device"
	Identifier	"Configured Video Device"
	Driver "nvidia"
	# Next two lines are recommended for nvidia beta on Intrepid
	Option "AddARGBVisuals" "True"
	Option "AddARGBGLXVisuals" "True"
	# Suppresses the nvidia logo at startup
	Option "NoLogo" "True"
	# Enable screen rotation
	Option "RandRRotation" "on"
	# NvAGP set to 0 makes standby work on TC1100
	Option "NvAGP" "0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen 		"Default Screen"
        InputDevice     "stylus"        "SendCoreEvents"
EndSection

Section "ServerFlags"
	# This option allows us to use the TC1100 side keys
	Option "AutoAddDevices" "false"
EndSection
```

This contains settings that remove blockers for standby, rotation and the side keys to work, but other things are needed as well for these - they won't all work for you yet. The important thing at this stage is to test the pen after putting this xorg.conf into place, and then rebooting (or doing 'sudo service gdm restart' from a console after logging out from the main session).

By the way, which version of Nvidia driver have you installed, and how? Mine is 96.43.09-0ubuntu1 which is now in the intrepid-updates repository.

---

### Post by rubbafishe on 2008-12-22
I replaced my xorg.conf files contents with yours. this has given me access to a 'rotate screen' option in my nvidia x settings menu. my driver version is the same version 96.43.09, from the repository.

unfortunately i'm still getting no response at all from the pen. ive been working with a usb keyboard and mouse, and i wonder if i should be disconnecting them while testing the pen or updating. maybe they're getting in the way of some sort automatic detection?
i don't know if this is the case thogh, just a thought.

---

### Post by Aearenda on 2008-12-22
No need to detach USB devices, it should work regardless.

Yes, rotate screen will work, but we need extra stuff to make the pen rotate, once we've got it working! You'll probably find you can go into standby as well, but the wireless may not work afterwards yet.

Now we need to know what the wacom driver is seeing. Please start a terminal session and enter the following command:```
grep [Ww]acom /var/log/Xorg.0.log
```Please post the output from this command here.

---

### Post by rubbafishe on 2008-12-22
here is the result from the terminal.

professor@Mandy:~$ grep [Ww]acom /var/log/Xorg.0.log
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
(II) Wacom driver level: 47-0.7.9-11 $
(**) stylus device is /dev/input/wacom
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(**) Option "Device" "/dev/input/wacom"
Wacom unable to read ISDV4 control data after 3 tries
Wacom unable to read ISDV4 control data after 3 tries

---

### Post by Aearenda on 2008-12-22
Your wacom driver level is old - mine is 47-0.8.1-4.

The Ubuntu xserver-xorg-input-wacom package showing in Synaptic for me is 1:0.8.1.4-0ubuntu3 and it comes from the standard Intrepid repository. I'm wondering how yours comes to be an older version - have you tried to install this from source?

This may not be the problem, but we'd better fix it. First, please post the output from the following terminal commands:
```
uname -a
apt-cache showpkg xserver-xorg-input-wacom
apt-cache showpkg wacom-tools
```

---

### Post by rubbafishe on 2008-12-22
i ran the commands and here are the results.

```
professor@Mandy:~$ uname -a
Linux Mandy 2.6.27-11-generic #1 SMP Fri Dec 19 16:29:52 UTC 2008 i686 GNU/Linux
professor@Mandy:~$ apt-cache showpkg xserver-xorg-input-wacom
Package: xserver-xorg-input-wacom
Versions: 
1:0.8.1.6-1ubuntu2 (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/dpkg/status
                  MD5: 2bd3c8ee2eda769c94b546d751232b99

1:0.8.1.4-0ubuntu3 (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_intrepid_main_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_intrepid_main_binary-i386_Packages
                  MD5: 2bd3c8ee2eda769c94b546d751232b99


Reverse Depends: 
  wacom-tools,xserver-xorg-input-wacom
  xserver-xorg-input-all,xserver-xorg-input-wacom
  xserver-xorg-core,xserver-xorg-input-wacom 0.7.8
  wacom-tools,xserver-xorg-input-wacom
Dependencies: 
1:0.8.1.6-1ubuntu2 - xserver-xorg-core (2 2:1.5.1-1ubuntu3) wacom-tools (0 (null)) wacom-tools (3 1:0.7.9.3-2) wacom-tools (3 1:0.7.9.3-2) 
1:0.8.1.4-0ubuntu3 - xserver-xorg-core (2 2:1.5.1-1ubuntu3) wacom-tools (0 (null)) wacom-tools (3 1:0.7.9.3-2) wacom-tools (3 1:0.7.9.3-2) 
Provides: 
1:0.8.1.6-1ubuntu2 - xserver-xorg-input-2.1 
1:0.8.1.4-0ubuntu3 - xserver-xorg-input-2.1 
Reverse Provides: 
professor@Mandy:~$ apt-cache showpkg wacom-tools
Package: wacom-tools
Versions: 
1:0.8.1.6-1ubuntu2 (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/dpkg/status
                  MD5: b5617785fb45ae13c791e945f0a78a65

1:0.8.1.4-0ubuntu3 (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_intrepid_main_binary-i386_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_intrepid_main_binary-i386_Packages
                  MD5: b5617785fb45ae13c791e945f0a78a65


Reverse Depends: 
  xserver-xorg-input-wacom,wacom-tools 1:0.7.9.3-2
  xserver-xorg-input-wacom,wacom-tools 1:0.7.9.3-2
  xserver-xorg-input-wacom,wacom-tools
  ubuntustudio-graphics,wacom-tools
  ubuntustudio-graphics,wacom-tools
  xserver-xorg-input-wacom,wacom-tools 1:0.7.9.3-2
  xserver-xorg-input-wacom,wacom-tools 1:0.7.9.3-2
  xserver-xorg-input-wacom,wacom-tools
Dependencies: 
1:0.8.1.6-1ubuntu2 - libc6 (2 2.4) libncurses5 (2 5.6+20071006-3) libx11-6 (0 (null)) libxi6 (2 2:1.1.3-1ubuntu3) tcl (0 (null)) tk (0 (null)) xserver-xorg-input-wacom (0 (null)) 
1:0.8.1.4-0ubuntu3 - libc6 (2 2.4) libncurses5 (2 5.6+20071006-3) libx11-6 (0 (null)) libxi6 (2 2:1.1.3-1ubuntu3) tcl (0 (null)) tk (0 (null)) xserver-xorg-input-wacom (0 (null)) 
Provides: 
1:0.8.1.6-1ubuntu2 - 
1:0.8.1.4-0ubuntu3 - 
Reverse Provides: 

```

i had downloaded and tried to install 2 wacom related patches from a help tutorial online, but i wasnt able to install them properly or at all to my knowledge.

---

### Post by Aearenda on 2008-12-22
You must be living on the edge with the intrepid-proposed repository enabled, since the 2.6.27-11 kernel hasn't gone to most users yet. I'm still using 2.6.27-9. However, that doesn't account for your wacom driver being *older* than mine! Can you tell me which help tutorial it was that you followed?

In the mean time, I think you should go into Synaptic, right-click on xserver-xorg-input-wacom and choose 'reinstall', and apply the change; then reboot, and see if the driver reported by 'grep [Ww]acom /var/log/Xorg.0.log' is now a later one than 47-0.7.9-11. If it isn't, then we may have to reinstall the kernel as well, since the underlying driver is part of that package.

I've come across material that suggests your tablet my have its pen interface appearing on a different serial port than is standard - I'm researching that at the moment.

UPDATE: it would be useful to see what output the following command gives:
```
ls /dev/ttyS*
```
After that, if you run the following command and move the pen over the screen, does anything appear on the screen? You should see a stream of characters when it is working, and you will need to press CTRL and C to quit. Try this for each device listed by the previous command until one works, or you get to the end of the list (on mine it lists /dev/ttyS0  /dev/ttyS1  /dev/ttyS2 and /dev/ttyS3, and produces output on ttyS0). 
```
xxd /dev/ttyS0
```When run for devices that do not function, xxd immediately exits, so just move on to the next one in that case.

Did your pen work with Windows before it was nuked?

---

### Post by rubbafishe on 2008-12-22
so i uninstalled the xserver-xorg-input-wacom package and reinstalled it. now the pen is working! seems like that older patch was the thing getting in the way.
thanks a million. 

i don't really care about the 3 buttons on the tablet screen  but the pressure sensitivity and eraser for my stylus are still inactive

---

### Post by Aearenda on 2008-12-22
Well done! 

Pressure sensitivity is usually controlled by the application - so in Xournal, for example, you have to turn it on in the options menu. In GIMP, you have to enable the stylus in preferences, otherwise it thinks its a mouse.

The TC1100 pen doesn't have an eraser, so you're out of luck there.

Other things I can steer you through if you want:
1. Make the Q and screen output selection buttons on the side of the TC1100, near the power switch, work
2. Make the table rotate with the screen - otherwise the pen is useless in portrait mode!
3. Test standby and fix wireless if it doesn't recover
4. Set up Cellwriter for on-screen keyboard and letter recognition.

I don't bother with the three pen-operated buttons near the USB sockets.

---

### Post by rubbafishe on 2008-12-23
well the 'esc' and 'tab' buttons on the side seem to work alright. even with XP i never really used the Q button or screen output buttons, or the screen rotation. i use it for image editing so keeping landscape is fine.
standby and wireless seem ok.

i understand the tc1100 doesn't necesarrily ship with a 2 ended stylus. since i bought mine second hand, the stylus i got with the thing had a working eraser. i can live without that though.

what would be useful is setting up cellwriter (i have it but cant really figure how it works yet)and change the q button to a shortcut.

 thanks for all your help, you've really saved my life here.

---

### Post by Aearenda on 2008-12-23
That's cool - Cellwriter is good once you get used to it. 

To get the eraser to work I think you need to add the following into xorg.conf, after the stylus section, using gksudo gedit as before:
```

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
        Option          "Button2"       "3"
EndSection

```Then restart GDM as before. However, I can't test this!

Below is how to get both side buttons working. You should write and test the scripts you want the buttons to trigger using a terminal, before doing this - I've called them '/full/path/to/your/script1' and '...2'. An example script to start Xournal might be:```
#!/bin/bash
xournal &
exit 0

```
The '&' makes the command start in a separate process, so that the button handler doesn't have to wait for it. Save the file and use the following command to make it executable:```
chmod u+x /full/path/to/your/script
```

Here's how to do the button mapping:
1. Create a text file in your home directory called '.Xmodmap' (the dot makes it hidden) containing these two lines: ```
keycode 159 = XF86Launch2
keycode 151 = XF86Launch1
```This does both the Q and the screen button. Next time you log on, it will ask whether to include these settings, but you can make it not ask after that. 151 is the screen button and 159 is the Q button.

2. Use ALT and F2 to start gconf-editor, and then use CTRL and F to find 'metacity' (this is the name of the window manager component)

3. Left-click on the arrow or double-click on 'metacity' in the left pane if it needs to be opened out (it probably does unless you've been here before).

4. Click on 'global_keybindings' in the left pane.

5. Double-click on 'run_command_1' in the right pane; enter the text 'XF86Launch1' (omit quotes) and save it.

6. Double-click on 'run_command_2' in the right pane; enter the text 'XF86Launch2' and save it.

7. Now click on 'keybinding commands' in the left pane.

8. Double-click on 'command_1', enter the text 'sh /full/path/to/your/script1' and save it; here, I enter 'sh /home/me/nvidia-toggle' which is my script to switch to the external screen. I don't know whether the 'sh' is really necessary here, but I do know that it works like this!

9. Double-click on 'command_2', enter the text 'sh /full/path/to/your/script2' and save it; here, I enter 'sh /home/me/rotate-screen' which is my script to rotate the screen and pen together.

10. For previous versions of Ubuntu, that was it. For Intrepid, I had to add the 'Option "AutoAddDevices" "false"' part to xorg.conf, which you have already done, and I had to do this kludge:```
sudo mv /etc/rc2.d/S20hotkey-setup /etc/rc2.d/S99hotkey-setup
```This prevents the hotkey setup from happening too soon.

---

### Post by rubbafishe on 2008-12-23
well thanks again for all the help. this stuff worked and now my tc1100 went from almost unusable to perfectly new in just 3 days! i can't thank you enough for your help.

---

### Post by Aearenda on 2008-12-23
I'm glad it's all turned out well in the end!

---

### Post by JHavok on 2008-12-28
This has been a very informative thread. Thanks to all the instructions here, I've been able to get my TC1100 99% working. I have 1 problem, my wireless does not work at all. I have the Pentium M 1100 with the Intel Pro 2100 wireless card. I already downloaded and installed NDISWRAPPER and the windows xp driver for that wireless card. 

I did not get any errors while installing the driver and I can see it as eth1 when I run ifconfig and iwconfig. The problem is that I can't seem to connect to a network and I can't find a way to do it other than via the terminal. The status light on the TC1100 is on for the wireless card but I can't figure out how to access it. When click on the network icon on the top menu bar, i see "wireless is disabled" under Wireless Networks. Also, dhclient fails to get an IP. I have configured eth1 with the essid, key, key type, mode, and rate. 

I am not sure if I am missing something here. Any help would be appreciated.

---

### Post by Aearenda on 2008-12-28
I'm glad everything else is working ok. It's worth knowing that wireless with Ubuntu can be done in several different ways, depending on your needs.

The basic architecture has a set of drivers for the different hardware - you have an Intel card, mine is Atheros. These manage the hardware and do basic tasks. Sometimes we use native Linux drivers, sometimes we use ndiswrapper with the relevant Windows driver.

When you use WPA security on the wireless network, a different bit of code called 'wpa supplicant' is used to manage the encryption keys.

The lowest level at which we can control thing is by using ifconfig and iwconfig, but that's hard work, as you have probably found. The next level involves settings in /etc/network/interfaces, which allows us to use ifup and ifdown to trigger wpa supplicant and the hardware driver to do the right things, get a DHCP address, and set routing and DNS so that it all works. This is good for diagnostics and for servers, but hard for laptops.

The top level uses either 'Network Manager' (which is standard in Ubuntu), or a different tool called 'wicd' to manage alternative settings and remember keys for different networks, and to do all the low level management for us. This is the best way for laptops. I use Network Manager (NM).

With the sketch of how it all links together out of the way, I'd like to suggest some checks on how you have everything configured. I'm assuming you're happy with the command line since the things you've tried need it.

1. When the computer starts, it needs to be told to load the ndiswrapper module. The usual way to do this is to add a line to /etc/modules, so that the file looks something like this:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

loop
# lp
fuse
ndiswrapper
```
This is the list from my TC1100 - I use ndiswrapper too.

2. Secondly, we need to prevent the native Linux driver from loading as well - otherwise it will interfere with ndiswrapper. This is done by adding a line to /etc/modprobe.d/blacklist - here is the last part of mine, after the standard entries:```
blacklist ipv6
blacklist pcspkr

# Nvidia hibernation
blacklist intel_agp
blacklist agpgart

# Using ndiswrapper
blacklist ath_pci
blacklist ath_hal
blacklist ath_rate_sample

```Here you can see at the end that I am blacklisting the three parts of the atheros driver. I'm afraid I don't know what the equivalent intel driver is called that you would need to use, but see the next step for a clue.
EDIT: Looks like it should be 'blacklist ipw2100'

3. When you install the Windows driver, you do something like this to register the driver, naming the relevant .inf file:```
sudo ndiswrapper -i driver.inf
```I believe you have done this - the way to check is to run ```
sudo ndiswrapper -l
```As a bonus, this will probably tell you the name of the native driver you need to blacklist :-) For me, the output of this command is```
net5211 : driver installed
	device (168C:0013) present (alternate driver: ath_pci)
```

4. To give Network Manager control over the wireless hardware, the file /etc/network/interfaces must look something like this:```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp
```
Note that on my system, the only used entry is that for the network loopback device 'lo'. The 'eth0' entry is commented out, and there is no entry for the wireless interface at all. This allows NM to take control. The message you are seeing suggests that on your system NM cannot control the wireless, and this might be a reason why. This behaviour varies a little between Ubuntu releases - which version are you using? (Mine is 8.10, called 'Intrepid Ibex').

5. With all that in place (for consistency, reboot if you have had to change things), Network Manager should be able to scan for networks. However, it is possible to tell NM to not use wireless at all, by right-clicking on its icon in the task bar and unchecking the 'Enable Wireless' checkbox. This checkbox is greyed out if no usable wireless hardware is found. Make sure that your system allows it to be checked.
EDIT: I should add that if NM finds a network, it will list it when you left-click on the icon in the task bar. If you then click on the network, it will ask you for the passphrase, and save it for future use, while attempting to connect. While it is doing that, the icon changes to a whirling dot with (eventually) two green indicators.

6. After doing all this, the next stage is to figure out what is going wrong. You can use the command 'dmesg | more' to look through the system log to see if ndiswrapper is complaining about the hardware, and you can look through '/var/log/daemon.log' to see what Network Manager is up to. Post anything suspicious here, or attach the log file if you wish. It would also be useful to see the output from ```
sudo lshw -C network
```

Please let us know how you get on!

EDIT: I just thought of something else. If you are using 8.04 (Hardy Heron), there is no way to turn the radio transmitter on or off - you have to do it from Windows XP and then reboot, unless there is a BIOS setting - but there isn't for mine. However, if you are using 8.10, you can turn it on like this:```
sudo modprobe tc1100-wmi # only needed once per restart
echo 1 > /sys/devices/platform/tc1100-wmi/wireless
```After this, to turn it off do ```
echo 0 > /sys/devices/platform/tc1100-wmi/wireless
```There's no need for sudo with the echo command. On my TC1100, this turns the wireless indicator on and off when using ndiswrapper, but not with the native drivers. Since the light is on with your TC1100, I suspect the wireless is already on. There may be a note in the logs about the kill switch if it is off - there's no other way to tell, since 'cat /sys/devices/platform/tc1100-wmi/wireless' always returns 0 regardless.

I added the 'modprobe tc1100-wmi' command to /etc/rc.local, and I can't really remember why now - it ought to be loaded by adding 'tc1100-wmi' to /etc/modules, like ndiswrapper. I suspect it was while I was testing the native driver, and I wanted to have tc1100-wmi loaded and usable, with the wireless turned on, before loading the native driver.

---

### Post by JHavok on 2008-12-28
I am very happy to report that I was able to get my wireless working with very minimal effort. I was following everything you suggested and had pretty much tried all of it already before posting last night. The one part I had not seen was "echo 1 >...." while the status light on the TC1100 had been on the whole time, I figured I'd give it a shot. When I ran those commands, the light flickered for a second and then I was able to see the several wireless networks. I am still new to Linux so pardon my ignorance in asking; how do I make sure that the wireless turns on when the system boots up? Also, I would be interested to know if there was a way that I could script this to turn the card on or off by using one of the pen activated button on the TC1100. My thought is to create a script and bind it to the button for the OSK. 

thank you for all the help.

EDIT: I forgot to mention that I am on 8.10.

---

### Post by Aearenda on 2008-12-28
That's great! Well done. 

You can add the echo command to start the radio to the file /etc/rc.local, which gets run late in the startup process. It will only work if tc1100-wmi is loaded first - I suggest you add that to the end of /etc/modules.

I have never bothered with the pen-activated buttons, since I don't use the pen very often. This was also true using XP. I have seen discussions of how to make them work, so you should be able to find a way (EDIT: See [http://ubuntuforums.org/showthread.php?p=3672701](http://ubuntuforums.org/showthread.php?p=3672701) as linked in Phenest's original howto at the top of this thread). I do use the side buttons, as described earlier in this thread, one for rotation and one for switching the screen to external or projection. I have been experimenting with a wireless on/off toggle script triggered through the normal menu.

In it's simplest form it could look like this:```

#!/bin/bash
# Toggle TC1100 wireless on or off

if [ -a ~/.wireless-on ] ; then
	echo "Switching wireless off"
	echo 0 > /sys/devices/platform/tc1100-wmi/wireless
	rm ~/.wireless-on
else
	echo "Switching wireless on"
	echo 1 > /sys/devices/platform/tc1100-wmi/wireless
	touch ~/.wireless-on
	sudo service NetworkManager restart
fi

```
This uses a hidden flag file in the home directory to remember the state of the wireless, since the kernel won't tell us. It's not really satisfactory without adding a session-start script to do 'touch ~/.wireless-on' assuming /etc/rc.local has turned the wireless on (or doing that in rc.local too, but you can't use the '~' abbreviation there so it would have to be 'touch /home/your-user/.wireless-on' followed by 'chown your-user /home/your-user/.wireless-on' so that you own it not root); and even then, it needs to be made aware of what happens during standby and hibernate. 
I find that NM gets confused if the radio is turned off, and needs to be restarted when the radio is turned back on by 'sudo service NetworkManager restart' in order to reconnect properly, and this needs a password - but here's a way round that:

1. In a terminal run 'sudo visudo'. 

2. At the end of the file that is presented, add:```
your-user ALL=(ALL) NOPASSWD:/home/your-user/.NMrestart
```Replace 'your-user' with your username :-)
EDIT: Take care here! If you are not familiar with the 'vi' editor, it is easy to mess this up and lose admin access. Remember that to exit vi without saving changes you press :q! and to add a new line, simply move the cursor to the last line by holding <cursor-down>, press A, then type <enter> and the new line, and finish with <esc>:wq

3. Create the file .NMrestart in your home directory containing:```
#!/bin/bash
/etc/init.d/NetworkManager restart
```

4. Make root own that file (otherwise you have a security hole) and set permissions:```
chown root.your-user .NMrestart
chmod 750 .NMrestart
```750 is full for root, read and execute for the owning group (which contains you), and nothing for anyone else. From now on, you'll have to use sudo to edit this file.

5. Replace 'sudo service NetworkManager restart' in the script with 'sudo ~/.NMrestart'

Now you should be able to toggle the network and restart NM without a password. I should add that I haven't tested these instructions!

---

### Post by serversphere on 2009-01-04
Great thread! Successfully running 8.10 on my ebay-acquired TC1100. Thanks to everyone who contributed to this thread.

In a video outlining the TC (HP promotional I believe), it showed someone rotate the tablet on a desk and the orientation changed without them hitting a button. Is this something the tablet did in Windows? I installed Ubuntu on the machine as soon as I received it, so I have no experience with this function (if it is one). I'm left wondering if this is something that can be tapped and applied to the rotate shell script here?

---

### Post by Aearenda on 2009-01-04
It used to work like that in Windows XP for me (I have had a TC1100 from new, in 2004), until one day the nvidia drivers got updated, and after that it did strange things like start up normal, rotate when it shouldn't, and then take ages to rotate back again when told to. I gradually began to hate it, and then I discovered Ubuntu :-)

AFAIK, nobody has ever worked out how to detect the hardware rotation state automatically in Linux, either from the docking station or from the keyboard. If we could, then it would be easy to do the script automatically.

---

### Post by serversphere on 2009-01-06
Just sent mine back to my ebay seller, as it had some screen burn in and he agreed to replace it with another. When I get mine back figuring out what switches when you rotate will become my new mission this weekend. :D

---

### Post by serversphere on 2009-01-09
Got my TC back and after doing some research, looks like there was a driver for the accelerometer in Windows called *sensor.dll*. I have just ordered recovery disks from HP, so again the waiting game on the delivery man...

---

### Post by kdub on 2009-01-22
Just got a tc1100 and am trying to install 8.10, I'm stuck at step 1 tried this command after alt f2:
sudo nano /etc/X11/xorg.conf-
and got this what am I doing wrong?
  GNU nano 2.0.7           File: /etc/X11/xorg.conf                             

# xorg.conf (X.Org X Window System server configuration file)
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
                               [ Read 42 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell
thanx
ken

---

### Post by Aearenda on 2009-01-22
Hi kdub - you're not doing anything wrong - that's what the top of that file looks like. 'nano' is a text editor for use inside terminal sessions. You may be more comfortable by doing```
gksudo gedit /etc/X11/xorg.conf
```instead of using nano - gedit is more like 'notepad' on Windows in how you use it.

Please note that the top post of this thread was written for 7.04, but you are installing 8.10. There will be differences. You will find my notes on 8.10 in [post 116]("http://ubuntuforums.org/showpost.php?p=6123218&postcount=116") but I'm afraid that's not really a how-to but rather a set of notes for those who have a bit of experience already. I haven't got time right now, but I will look through Post 1 and add some comments about it here if I see anything that need attention.

EDIT: Three things that come to mind so far: 
1. [Post 136]("http://ubuntuforums.org/showpost.php?p=6420225&postcount=136") contains an up to date version of what should appear in /etc/X11/xorg.conf for a standard TC1100 on Intrepid.
2. Standby is different in 8.10 from 7.04 - you should modify /etc/pm/config.d/00SleepModule as discussed in [Post 116]("http://ubuntuforums.org/showpost.php?p=6123218&postcount=116") step 3.
3. In spite of what it currently says in Post 116, I have resumed using ath_pci for the wireless driver; ndiswrapper was crashing on suspend sometimes. The Network-Manager updates seem to have fixed the association delay problem in the meantime. I need to fix Post 116.

---

### Post by kdub on 2009-01-23
Aearenda,
 Thanks.I was starting to feel retarded!
ken

---

### Post by kdub on 2009-01-23
So,
I cut and pasted  your print out, reinstalled the wacom drivers and now my pen works , and my wireless has worked fine since the initial install.
Next is  how do I  get rotate, and my buttons to work. After that I need to find a Tablet Journal type program (is that what cellwriter is?) and work on some way to hibernate/sleep.
thanks,
kdub

---

### Post by Aearenda on 2009-01-23
Well done! You should be able to get rotation to work based on the earlier posts in this thread.

Cellwriter is a pen input tool for non-pen-aware programs. Take a look at Xournal for a Journal equivalent!

---

### Post by kdub on 2009-01-24
Aearenda,
So the commands from before #116 will work with 8.10?
thanks for the help, I really didn't think that I'd ever be able to get this thing up.
thank you,
ken

---

### Post by Aearenda on 2009-01-24
Yes, rotation itself hasn't changed - the assignment of side buttons (I use the 'Q' button for rotation) has though, it needs the hotkey setup shifted later in startup - like this:
```
sudo mv /etc/rc2.d/S20hotkey-setup /etc/rc2.d/S99hotkey-setup
```EDIT: [Post 146]("http://ubuntuforums.org/showpost.php?p=6421826&postcount=146") has more on the side buttons.

Also note that you need to rotate both the screen and the tablet!

To rotate the tablet sensors and screen to portrait mode use ```
xrandr -o left
xsetwacom set stylus rotate ccw
```ccw means counter-clockwise.
To set it back do```
xrandr -o normal
xsetwacom set stylus rotate none
```

I also reset the tablet calibration after hibernate or suspend, like this for portrait:
```
xsetwacom set stylus BottomY 21240
xsetwacom set stylus BottomX 15980
```
And landscape:
```
xsetwacom set stylus BottomY 15980
xsetwacom set stylus BottomX 21240
```
Your calibration may be different - here's how to check, do this after a normal boot and before any hibernate or standby:
```
xsetwacom get stylus TopX BottomX TopY BottomY
```This will list the co-ordinates in order.


Here is the full script I now use for rotation - on my TC1100 it is called without parameters by the 'Q' button.
```
#!/bin/bash
# Based on work from Patrick Coke & Tim Pope
# Modified for TC1100 by Francisco Athens
# Rewritten for current xsetwacom and xrandr vesrions by Krzysztof Kosi&#324;ski
# Adapted to work as a toggle - Aearenda

# Takes one parameter:
# normal = go to landscape
# left = go to portrait
# fixcalib = just reset the tablet calibration, don't rotate
# fix = set rotation as it was before standby or hibernate, based on the ~/.screen-rotated flag file
# If absent, toggles rotation based on current X settings
# 
# This is the Ubuntu 8.10 version

# Usually we will want to set X rotation
SKIPX="no"


# Look at parameters and fix things up for later
case $1 in
     normal)	# Pretend we found left-rotation
		ROTATION="left"
		;;
     left)	# Pretend we found normal rotation
		ROTATION="normal"
		;;
     fixcalib)	# Just fix the wacom calibration
		SKIPX="yes"
		if [ -a ~/.screen-rotated ] ; then
			# Remember this is reversed...
			ROTATION="normal"
		else
			ROTATION="left"
		fi
		;;
     fix)	# use the flag and reset
		if [ -a ~/.screen-rotated ] ; then
			# Remember this is reversed...
			ROTATION="normal"
		else
			ROTATION="left"
		fi
		;;
     *)		# Detect what it is now so we can toggle it
		ROTATION=`xrandr --verbose --query | \
		grep 'default connected' | \
		sed -e 's/^.*(.*) \(.*\) (.*).*$/\1/'`
		;;
esac

# Now do the required action
case $ROTATION in

     normal)	xsetwacom set stylus rotate ccw
		xsetwacom set stylus TopX 0
		xsetwacom set stylus TopY 0
		xsetwacom set stylus BottomY 21240
		xsetwacom set stylus BottomX 15980
		[ "$SKIPX" = "yes" ] && exit 0
		touch ~/.screen-rotated
		xrandr -o left ;;

     left)	xsetwacom set stylus rotate none
		xsetwacom set stylus TopX 0
		xsetwacom set stylus TopY 0
		xsetwacom set stylus BottomY 15980
		xsetwacom set stylus BottomX 21240
		[ "$SKIPX" = "yes" ] && exit 0
		rm ~/.screen-rotated
		xrandr -o normal ;;

esac

```

---

### Post by kdub on 2009-01-24
So I would open up a terminal and cut/paste this script in?
thanx
ken

---

### Post by Aearenda on 2009-01-24
Sorry, I keep assuming you know things - you can do that with the individual commands I gave - but the script at the end needs to be saved in a file. One way would be to: 
1. Start the text editor (gedit) from the menu, paste it in there, then save the file as 'rotate-screen'. 
2. Then find the 'rotate-screen' file in your home folder using the File Browser (Nautilus), right-click on it and choose 'Properties', select the 'Permissions' tab, and click on 'Allow executing file as a program'. 
3. Now you can create an entry for it using the Menu Editor (there's a shortcut to starting that by right-clicking on the Ubuntu logo that opens the menu), by clicking on the menu folder where you want the menu entry to be, and then adding a new item. Give it a meaningful name and comment, browse to the file 'rotate-screen' for the command, and click on the icon button to find a suitable icon - look in /usr/share/icons for lots of choices.

I hope that makes sense - I've got to go out.

---

### Post by kdub on 2009-01-24
A,
the screen rotates on Q button!!! Thank You!! How did you get cell writer to work to fill in name and password at the login screen?
thanks,
Ken

---

### Post by Aearenda on 2009-01-25
Well done again! I don't bother with a logon password, I just set it to log me on automatically in 4 seconds so I can choose a different user if I want to by typing quickly. That's on the 'Security' tab in 'Login Window' under 'Administration' from the 'System' menu - except that it only goes to 10 seconds minimum. But do it anyway, and then do 'gksudo gedit /etc/gdm/gdm.conf-custom', find the line that now reads 'TimedLoginDelay=10' and change it to 5, then save the file.

If you don't want to do that, there is a way - see Post 1! But I haven't tried that with 8.10.

Also, you'll want to allow cellwriter to supply gksudo passwords - one way should be to enable 'password dialogs as normal windows', which is now under 'Preferences'->'Assistive Technologies', but I haven't tried that method with 8.10. It is ticked on my system, so maybe I'm just setting the underlying feature. Anyway, here's how I allow this:
1. Press ALT/F2, type 'gconf-editor' and press <ENTER>.
2. Find and click once on 'gksu' under 'apps' in the tree on the left.
3. On the right, check 'disable-grab'.
4. Close gconf-editor

Like most GNOME settings, it takes effect straight away. This opens a possible security hole, in that other malicious apps could intervene and capture your password, but frankly, I think it is extremely unlikely. You'll notice that the screen no longer dims when passwords are requested.

---

### Post by groadin on 2009-01-25
Hello thanks for this great topic but I have strange problem with stylus.

Everything that should work is working, except stylus sync after rotation. When I rotate the screen, it seems like stylus still have old axis (which should be X now, is still Y and vice versa).

I searched a lot but with no luck. I have full updated ubuntu 8.10. I tried to use wacom-tools from repo, or self compiled using instructions from this forum, or from [here]("http://wiki.linuxquestions.org/wiki/Tc1100"). I also tried to use different xsetwacom commands (like xsetwacom set stylus rotate ccw, or xsetwacom set "stylus" Rotate CCW), but no luck.

I dont know what is the problem. I had installed ubuntu 8.10 on TC1100 before, and then rotation was working. Please help, where should I search, and what should I check to get the problem solved?

---

### Post by Aearenda on 2009-01-25
Groadin, the wiki page you linked hasn't been updated for 8.10. It seems likely to me that the version of xserver-xorg-input-wacom you have installed is confused. I have never installed anything but the standard version of this or wacom-tools in the repository, and it just works on my TC1100. 

I would make sure all traces of the non-standard wacom-tools packages are removed, then reinstall wacom-tools and xserver-xorg-input-wacom using Synaptic.

---

### Post by kdub on 2009-01-25
> **Aearenda said:**
> Well done again! I don't bother with a logon password, I just set it to log me on automatically in 4 seconds so I can choose a different user if I want to by typing quickly. That's on the 'Security' tab in 'Login Window' under 'Administration' from the 'System' menu - except that it only goes to 10 seconds minimum. But do it anyway, and then do 'gksudo gedit /etc/gdm/gdm.conf-custom', find the line that now reads 'TimedLoginDelay=10' and change it to 5, then save the file.

If you don't want to do that, there is a way - see Post 1! But I haven't tried that with 8.10.

Also, you'll want to allow cellwriter to supply gksudo passwords - one way should be to enable 'password dialogs as normal windows', which is now under 'Preferences'->'Assistive Technologies', but I haven't tried that method with 8.10. It is ticked on my system, so maybe I'm just setting the underlying feature. Anyway, here's how I allow this:
1. Press ALT/F2, type 'gconf-editor' and press <ENTER>.
2. Find and click once on 'gksu' under 'apps' in the tree on the left.
3. On the right, check 'disable-grab'.
4. Close gconf-editor

Like most GNOME settings, it takes effect straight away. This opens a possible security hole, in that other malicious apps could intervene and capture your password, but frankly, I think it is extremely unlikely. You'll notice that the screen no longer dims when passwords are requested.

Aearenda,
WoooHoooo! I emailed Mike Levin and asked him about his Cellwriter program.He emailed me this link:
[http://www.krizka.net/2008/01/02/cellwriter-handwritting-recognition-for-gnome/](http://www.krizka.net/2008/01/02/cellwriter-handwritting-recognition-for-gnome/)
Seems to work great!!
Now to reread and figure out how to map the monitor button to rotate and Q
to Xournal.
thanks for all your help and patience with this know nothing newbie (gotta give props to my youngest-15-he gave me the look,sat me down and held my hand step by step also) Man this thing is like using a GIANT version of my Nokia n800 now! 
Again 
  THANK YOU!!!,
ken
- Show quoted text -

---

### Post by Aearenda on 2009-01-25
Kdub, I'm glad it's all good. I use the monitor button to tell X to toggle the output to the external screen and/or projector, just like on Windows - that's why I use Q for rotation. IIRC the Q button keycode is 159 (9f in hex), the monitor is 151 (0x97) - this should be enough info for you to set the other button as you desire, since you already have Q doing rotation!

---

### Post by kdub on 2009-01-25
> **Aearenda said:**
> Kdub, I'm glad it's all good. I use the monitor button to tell X to toggle the output to the external screen and/or projector, just like on Windows - that's why I use Q for rotation. IIRC the Q button keycode is 159 (9f in hex), the monitor is 151 (0x97) - this should be enough info for you to set the other button as you desire, since you already have Q doing rotation!

Wellll,
Not so fast-guess there is a "small problem" with cellwriter the way I have it set up.Seems that when I need to put in an admin password for say synaptic the password window comes forward and will not allow the cell keyboard to function. Anyone got any ideas?
ken

---

### Post by Aearenda on 2009-01-25
See the 3rd paragraph in [Post 167]("http://ubuntuforums.org/showpost.php?p=6612730&postcount=167") :-)

---

### Post by kdub on 2009-01-26
> **Aearenda said:**
> See the 3rd paragraph in [Post 167]("http://ubuntuforums.org/showpost.php?p=6612730&postcount=167") :-)

Aearenda,
 In your debt again! Thankyou that worked!
ken

---

### Post by groadin on 2009-01-26
> **Aearenda said:**
> Groadin, the wiki page you linked hasn't been updated for 8.10. It seems likely to me that the version of xserver-xorg-input-wacom you have installed is confused. I have never installed anything but the standard version of this or wacom-tools in the repository, and it just works on my TC1100. 

I would make sure all traces of the non-standard wacom-tools packages are removed, then reinstall wacom-tools and xserver-xorg-input-wacom using Synaptic.

Thank you. I've just done a clean install, without bothering about compiling wacom-tools. All just updated from repo, and wacom-tools installed by synaptic. Now rotate works perfect.

Almost all works - except stylus buttons. Earlier, I followed instructions from [this topic]("http://ubuntuforums.org/showthread.php?t=574310"). It's a little messy but I managed to get stylus buttons working, but rotation wasn't. 

Could you post some instructions about enabling these three stylus buttons? How to do it with Ubuntu 8.10 in the proper way?

---

### Post by Aearenda on 2009-01-26
Unfortunately, I don't know how to make them work on 8.10 - I never used these three buttons on Windows either, they felt too far out of the way. It's easy to set up launchers on the task bar that do the same job, just by right-clicking on the relevant entry in the menu and choosing 'add this launcher to panel'.

---

### Post by galileon on 2009-01-31
Dear Aearenda, Thanks a lot for the tidbits, I managed to get my TC1100 working in perfect shape with Intrepid using your notes :). On another note, I've just cobbled together a Q Button, here [http://galileon.co.uk/qbutton/qbutton.php](http://galileon.co.uk/qbutton/qbutton.php), hope this helps.

Anyways, I've tried to get the wacom buttons to work, using the tutorial here: [http://wiki.linuxquestions.org/wiki/Tc1100#Hibernate_and_suspend_to_RAM](http://wiki.linuxquestions.org/wiki/Tc1100#Hibernate_and_suspend_to_RAM), but it fails with some undeclared constants or something. I'm not in the mood to go driver hacking atm, but I'll look into it when I have some time. :D

---

### Post by Aearenda on 2009-01-31
That's great, I'm sure people will find your Q-button program useful! The use of sudo that way isn't a complete security hole so long as the executable file belongs to root and is execute-only for ordinary users.

---

### Post by justnice980 on 2009-01-31
if you can find the time. i could really use you help in this issue. i am having similar issues in getting pen functionality. i followed the steps of this tutorial as best i could, but as i am new to ubuntu and the whole linux community i fear i may have done something wrong. i still have xp running on my machine so it's not a huge issue, but i would very much like to get full functionality if i could.  thanks for your consideration in this matter. i'm sure you get many questions from noobtards such as myself, so any help at all would be greatly appreciated.

---

### Post by Aearenda on 2009-01-31
justnice980: Welcome to Ubuntu! I'm happy to help, but I need you to tell us a bit more to get started. Don't worry about everything feeling awkward at first, Linux is not Windows and several things are quite different.

Start a reply to this message now, so you can fill in the answers as we go on.

First what version of Ubuntu do you have? You can check by pressing ALT and F2 to bring up the 'Run Application' box, and then typing (or copying and pasting)```
gedit /etc/lsb-release
```and pressing <ENTER>. On mine it looks like this: ```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
```The most recent is 8.10; tell us what version you have in your reply message. Close gedit without saving by pressing ALT and F4 or using the mouse.

Next, please tell us what version of wacom-tools is installed. You can do that this way:
1. Start 'Synaptic Package Manager' from the system->administration menu, and supply your password if asked.
2. In the 'Quick Search' box type **wacom** and press <Enter> - it should show two packages in the top-right pane. If not, 
  2.1. Click once on the 'search' button.
  2.2. Type **wacom** and press <Enter>
4. You should find that the wacom-tools and xserver-xorg-input-wacom packages are showing in the top-right pane. Do they both have a green box next to them, indicating that they are installed?
5. What is the version number showing as installed and as latest for each of the two packages? The version for Ubuntu 8.10 is currently 1:0.8.1.4-0ubuntu3 for both. If you have different versions, or if either package is not installed, please tell us in your reply.
6. Close Synaptic - don't change anything in there yet.

Finally, please post the contents of your /etc/X11/xorg.conf file, like this:
1. Press ALT and F2 and then type or paste the following command, followed by <ENTER>```
gedit /etc/X11/xorg.conf
```
2. In the text editor, press CTRL and A to select all, then CTRL and C to copy it.
3. In your reply to this message, click on the 'quote' button above the reply box (it looks like a cartoon speech balloon) and then press CTRL and V to paste the file contents between the markers that appeared.
4. Now switch back to the text editor and press ALT and F4 to close it.

Then post your reply, and we'll see what needs to be done next!

---

### Post by MyR on 2009-02-01
Hello!
So no one has been able to get the soft buttons working?
I patched the drivers following the instructions on the wiki mentioned above with no luck.
I know I can map the side buttons or add a launcher, but those aren't as "cool".
Thanks

---

### Post by mr_deimos on 2009-02-14
> **Aearenda said:**
> It used to work like that in Windows XP for me (I have had a TC1100 from new, in 2004), until one day the nvidia drivers got updated, and after that it did strange things like start up normal, rotate when it shouldn't, and then take ages to rotate back again when told to. I gradually began to hate it, and then I discovered Ubuntu :-)

AFAIK, nobody has ever worked out how to detect the hardware rotation state automatically in Linux, either from the docking station or from the keyboard. If we could, then it would be easy to do the script automatically.

How exactly did the automatic rotating work in windows? Do you mean rotating to portrait mode after folding/detaching the keyboard and using the tablet in slate mode, and rotating back to landscape as soon as you opened up the keyboard? Or was it rotating based on device's actual orientation, as modern pda-phones do?

If you mean the second option, there is a dirty way of detecting if tc1100 is in  laptop or slate mode. As you might have noticed, the tc1100 fan runs faster when you use it in slate mode. That's because it has hardcoded thermal thresholds that are different for laptop and slate mode. By reading the /proc/acpi/thermal_zone/THRM/trip_points file you can determine this thresholds, and therefore the state of the keyboard.
A script/daemon that would periodically monitor these values and rotate the screen accordingly shouldn't be hard to make.
I found this info by looking for some workaround preventing the fan from speeding up:
[http://tabletpcbuzz.com/showpost.php?p=203353&postcount=19](http://tabletpcbuzz.com/showpost.php?p=203353&postcount=19)

Personally, i don't really like this feature and i'll probably hack the keyboard to disable the position sensor and have the fan run a bit slower in slate mode. But if someone likes the auto rotation and isn't bothered by the fan, checking thermal trip points be the way to go.

And one more thing about rotation: there's a nice daemon written by author of easystroke (great gesture recognition software, highly recommended). It monitors current screen orientation and sets digitizer orientation and subpixel font smoothing (aka cleartype) mode appropriately (works only for gnome).
You can grab it here:
[http://easystroke.wiki.sourceforge.net/TipsAndTricks](http://easystroke.wiki.sourceforge.net/TipsAndTricks) (scroll down to "Don't use Rotate Scripts" section). The great advantage of using it is that the digitizer will always be properly aligned, no matter how you rotated the screen (by a script, by xrandr panel applet, by hand from console).
I think i'll try to modify it a bit to make it remember digitzier calibration data for every screen orientation, since it seems that wacom driver doesn't support different calibration for portrait and landscape modes (or am i wrong?).


Anyway, thanks to everyone contributing to this tread - it was really helpful :D And here's a small contribution from me, a simple wireless toggle script. I have it inserted as a a launcher in gnome-panel:
```

#!/bin/bash
WIRELESS_STATE=`lsusb|grep Bluetooth`
if [ "x$WIRELESS_STATE" == "x" ] ; then
	echo "WiFi Off, turning on"
	echo 1 > /sys/devices/platform/tc1100-wmi/wireless
else
	echo "WiFi On, turning off"
	echo 0 > /sys/devices/platform/tc1100-wmi/wireless 
fi

```
As you might have noticed, doing cat /sys/devices/platform/tc1100-wmi/wireless returns 0 no matter if wireless is on or off, so it's not possible to determine wireless state with that. But disabling wifi also disables bluetooth, and we can detect this easily :D I guess it's a better solution than doing a toggle based on existence of some file, as proposed earlier in this tread.

---

### Post by Aearenda on 2009-02-14
> How exactly did the automatic rotating work in windows? Do you mean rotating to portrait mode after folding/detaching the keyboard and using the tablet in slate mode, and rotating back to landscape as soon as you opened up the keyboard? Or was it rotating based on device's actual orientation, as modern pda-phones do?
It was the keyboard way. I experimented years ago with the connector link that thread discusses but in the end didn't bother with it as my fan was relatively quiet. I was still using Windows then.

Thanks for that great info about detecting the fan settings and the wireless - it's much better than what I was doing! Though I still think I need a flag file for persistence of the wireless on/off setting across reboots.

---

### Post by mr_deimos on 2009-02-14
> **Aearenda said:**
> It was the keyboard way. I experimented years ago with the connector link that thread discusses but in the end didn't bother with it as my fan was relatively quiet. I was still using Windows then.

Ok, thanks for the info. I was beginning to think that maybe threr was another way of detecting rotation and i just screwed up something with windows drivers (using dual boot) ;)

> 
Though I still think I need a flag file for persistence of the wireless on/off setting across reboots.
But why? If you boot up with wireless disabled, bluetooth will be disabled as well and 'lsusb|grep Bluetooth' command will return an empty string. So you can use bluetooth's presence as a flag. Not very clean solution, but does the trick ;)
I actually came up with it, because a simple flag file wasn't enough - if i changed wireless setting in windows, the toggle script needed to be run twice, since the flag wasn't matching real wireless state.

---

### Post by Aearenda on 2009-02-14
Hmm, I think it might depend on which drivers are in use, but I'm sure I found the wireless was getting switched on automatically on reboot in Intrepid, regardless of its previous state. Maybe I'm wrong. I don't dual boot so it isn't an issue for me.

EDIT: I just tried it again, and the state does persist over a reboot using ath_pci or ndiswrapper. Maybe it was the ath5k driver that reset it every time, or maybe I was dreaming it. I've modified my script to use lsusb to detect the state and it works fine.

---

### Post by MyR on 2009-02-18
I got the wireless to turn on automatically after a resume from suspend.

```
sudo gedit /etc/pm/sleep.d/15-TurnWirelessOn
```
and enter:
```
sleep 1
echo 1 > /sys/devices/platform/tc1100-wmi/wireless
```
save and exit
then
```
sudo chmod +x /etc/pm/sleep.d/15-TurnWirelessOn
```
and you should be all set

Thanks everyone!  Your posts have been helpful.

---

### Post by mr_deimos on 2009-03-02
> **MyR said:**
> Hello!
So no one has been able to get the soft buttons working?
I patched the drivers following the instructions on the wiki mentioned above with no luck.
I know I can map the side buttons or add a launcher, but those aren't as "cool".
Thanks

I got these screen buttons to work. I just needed to follow instructions in post #1 and #4 of this tread:
[http://ubuntuforums.org/showthread.php?p=3672701#post3672701](http://ubuntuforums.org/showthread.php?p=3672701#post3672701)
Are you sure you patched both src/xdrv/wcmCommon.c and src/xdrv/wcmISDV4.c?
What exactly doesn't work for you?

---

### Post by MyR on 2009-03-03
> **mr_deimos said:**
> I got these screen buttons to work. I just needed to follow instructions in post #1 and #4 of this tread:
[http://ubuntuforums.org/showthread.php?p=3672701#post3672701](http://ubuntuforums.org/showthread.php?p=3672701#post3672701)
Are you sure you patched both src/xdrv/wcmCommon.c and src/xdrv/wcmISDV4.c?
What exactly doesn't work for you?

I followed the *new* instructions on the [wiki]("http://wiki.linuxquestions.org/wiki/Tc1100#Stylus_buttons"). So now they work perfectly! Awesome! I can delete my xournal and rotate launchers.

Now.. any way to get the SD card reader working? ;]

peace

---

### Post by cstorozuk on 2009-03-04
Hi, don`t know if I should start a new post, but I was hoping you could help me with my TC1000. I can`t seem to find a USB flash drive boot option in my Select Boot Device window. The items available are:
Removable Devices
ATAPI CD-ROM
Hard Drive

Thanks,
Chris

---

### Post by MyR on 2009-03-04
> **cstorozuk said:**
> I can`t seem to find a USB flash drive boot option in my Select Boot Device window. The items available are:
Removable Devices
ATAPI CD-ROM
Hard Drive

The USB drive is a "removable device".

peace

---

### Post by Aearenda on 2009-03-04
I have a memory of failing to boot a TC1000 (not TC1100) from a USB flash drive - it would only boot from a Compact Flash device in the CF socket, or from a USB CD drive. This would be a BIOS limitation. Maybe it didn't apply to all BIOS versions, and maybe I'm wrong.

On a different note, my 5-year-old TC1100 is failing - the Nvidia GPU is not found on (re-)boot when it is warm, and the BIOS screen is corrupted along with all later text-mode screens. This is the second TC1100 I've had that did this. I suspect I'm going to have to retire it :-(

---

### Post by bigbamboo on 2009-03-21
Hi everybody,
I'm a beginner with Ubuntu and I have a problem in configuring 2 things:
1. when I try to install the software to handle the Q-Key, I get the following error:
```
ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
sh: cannot create /proc/acpi/wmi/WMID/bluetooth: Directory nonexistent
```
it seems I don't have the tc1100-wmi 'module but I don't Know How to get it (I'm on Ubuntu 8.10)
2. I have compiz running so xbindkeys doesn't work:
```
displayName = :0.0
rc file = /home/eugenio/.xbindkeysrc
rc guile file = /home/eugenio/.xbindkeysrc.scm
getting rc guile file /home/eugenio/.xbindkeysrc.scm.
WARNING : /home/eugenio/.xbindkeysrc.scm not found or reading not allowed.
3 keys in /home/eugenio/.xbindkeysrc

min_keycode=8     max_keycode=255 (ie: know keycodes)
"/usr/bin/rotate"
    m:0x0 + b:4   (mouse)
"xournal"
    m:0x0 + b:5   (mouse)
"cellwriter"
    m:0x0 + b:6   (mouse)
starting loop...

*** Warning ***
Please verify that there is not another program running
which captures one of the keys captured by xbindkeys.
It seems that there is a conflict, and xbindkeys can't
grab all the keys defined in its configuration file.
```  

but I don't know how to configure Compiz to make the pen-button work.

Any advice?

thanks

E.   .

---

### Post by MyR on 2009-03-22
> **bigbamboo said:**
> Hi everybody,
I'm a beginner with Ubuntu and I have a problem in configuring 2 things:
1. when I try to install the software to handle the Q-Key, I get the following error:
```
ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
sh: cannot create /proc/acpi/wmi/WMID/bluetooth: Directory nonexistent
```
it seems I don't have the tc1100-wmi 'module but I don't Know How to get it (I'm on Ubuntu 8.10)
2. I have compiz running so xbindkeys doesn't work:
```
displayName = :0.0
rc file = /home/eugenio/.xbindkeysrc
rc guile file = /home/eugenio/.xbindkeysrc.scm
getting rc guile file /home/eugenio/.xbindkeysrc.scm.
WARNING : /home/eugenio/.xbindkeysrc.scm not found or reading not allowed.
3 keys in /home/eugenio/.xbindkeysrc

min_keycode=8     max_keycode=255 (ie: know keycodes)
"/usr/bin/rotate"
    m:0x0 + b:4   (mouse)
"xournal"
    m:0x0 + b:5   (mouse)
"cellwriter"
    m:0x0 + b:6   (mouse)
starting loop...

*** Warning ***
Please verify that there is not another program running
which captures one of the keys captured by xbindkeys.
It seems that there is a conflict, and xbindkeys can't
grab all the keys defined in its configuration file.
```  

but I don't know how to configure Compiz to make the pen-button work.

Any advice?

thanks

E.   .
1. in a terminal enter:
```
gksu gedit /etc/modules
```
and on a new line add:
```
tc1100-wmi
```
then close and save
2. Turn off compiz because you don't really need it? (gasp) Or maybe you could use compiz to launch your apps instead of xbindkeys.
sudo aptitude install compizconfig-settings-manager
then system > preferences > compizconfig.
next general options > commands > key bindings.
enter the command such as  cellwriter.  This is just a suggestion; I don't use compiz on the tablet.

peace

---

### Post by bigbamboo on 2009-03-22
thanks MyR for the quick reply,

1. I already added the line but nothing changed, any further advice?

2. I'm  compiz-addicted :)  is it unstable on the tablet? I tried to add custom Key-bindings but I don't Know the correct values for pen-buttons (the key combination I have to bind with cellwriter, xournal and rotation script)


P.S. cellwriter Keeps asking me for training everytime I reboot, is there a way to save the training?

---

### Post by MyR on 2009-03-22
> **bigbamboo said:**
> thanks MyR for the quick reply,

1. I already added the line but nothing changed, any further advice?

2. I'm  compiz-addicted :)  is it unstable on the tablet? I tried to add custom Key-bindings but I don't Know the correct values for pen-buttons (the key combination I have to bind with cellwriter, xournal and rotation script)


P.S. cellwriter Keeps asking me for training everytime I reboot, is there a way to save the training?

1. in a terminal type: modprobe tc1100-wmi
to see if you have the module
then type: lsmod | grep tc1100
to see if it is loaded

2. I just tested it out and the stylus buttons work perfectly with compiz without needing to configure it.  Maybe you have some plugins enabled that I don't.  So I can't help you there, sorry

cellwriter: make sure you trained **all** the characters

peace

---

### Post by bigbamboo on 2009-03-22
> **MyR said:**
> 1. in a terminal type: modprobe tc1100-wmi
to see if you have the module
then type: lsmod | grep tc1100
to see if it is loaded

2. I just tested it out and the stylus buttons work perfectly with compiz without needing to configure it.  Maybe you have some plugins enabled that I don't.  So I can't help you there, sorry

cellwriter: make sure you trained **all** the characters

peace

well,
it seems that I managed to fix tc1100-wmi module (many many thanks for your support), now I can use Tabatha and q.py.

I still can't bind stylus buttons to something, I turned off Compiz but still the message is that there's "something else" is taking control of that buttons.
Moreover, I can't even bind the "Q" button (same error).

Is there any way I can check what is happening? there are no clues either on "top" command result and on "ps -ef|grep bind" command.

PS cellwriter also fixed!

---

### Post by bigbamboo on 2009-03-22
I made a little step ahead in figuring out what is happening.

I installed xbindkeys-config to create the xbindkeysrc file instead of writing it by hand (literally!).

Now the "q" key works (with Compiz running!), the correct configuration line is:
```

# Q-key
"path/to/script/"
m:0x0 + c:156
XF86Launch1

```

and not just "c:156"

I can't configure the stylus buttons because as soon as I try to get the configuration code by clicking on "get key" button (as made with the "Q-key") the application crashes with a IO error.

Can you post your .xbindkeysrc file?

---

### Post by MyR on 2009-03-22
my .xbindkeysrc looks like this:
```
"rotate"
b:30
"xournal"
b:31
"cellwriter"
b:32
```

---

### Post by bigbamboo on 2009-03-22
d'oh!

I have to give up.

---

### Post by alastair.mac on 2009-03-26
the trick is: xbindkeys-config screws up your manualy edited xbindkeysrc.

so use xbindkeys-config to set the Q key, save and exit, then use gedit to add the lines for the screen buttons.


Save a backup of xbindkeysr as xbindkeys-config will trash it if you use it again for anything else.

---

### Post by xobx on 2009-03-27
Hello
I am not using Linux and my English is very bad.
Is there a ready-made image of Ubuntu for HP TC1100?
I use it to read PDF and surfing.

Translate wit GOOGLE

---

### Post by xobx on 2009-03-29
No One??

---

### Post by MyR on 2009-03-29
> **xobx said:**
> Hello
I am not using Linux and my English is very bad.
Is there a ready-made image of Ubuntu for HP TC1100?
I use it to read PDF and surfing.

Translate wit GOOGLE

I doubt it

---

### Post by xobx on 2009-03-29
Why not? 
If there are many to work with but do not create themselves. 
It would be very nice. :P
Install is not difficult, but the Wacom digitizer with the keys is difficult, when dealing with the terminal can not start. 
Windows users also:(

---

### Post by pvhoward on 2009-03-29
Hey guys, can anyone offer any help regarding the tc1000?

---

### Post by Aearenda on 2009-03-29
I used to use a TC1000 before I got my TC1100, which is itself now retired, since it has become impossible to restart without losing access to the Nvidia hardware when warm. 

I have tried Debian on the TC1000, and Gentoo, and most recently an Ubuntu Intrepid minimal installation with LXDE; but there is no persistent translation service for the Crusoe processor, as there is in Windows, and as a result it is very slow to start up, and to start programs such as Firefox.

---

### Post by pvhoward on 2009-03-29
ya Im currently successfully running Ubuntu 8.10 and it is very slow (about 5.5 min boot time when my main laptop does hardy heron in about 30-45 seconds),but I was hoping you, or someone else could help me set it up so that it works in either ubuntu or xubuntu, but im not opposed to going what ever distro would work thanks for the reply

---

### Post by Aearenda on 2009-03-29
Take a look at the LXDE instructions at [http://ubuntu-lxde.wikidot.com/intrepid](http://ubuntu-lxde.wikidot.com/intrepid). It uses a lightweight desktop environment called LXDE instead of GNOME but underneath it is Ubuntu.See [http://www.lxde.org/](http://www.lxde.org/) for more details of LXDE.

I use this on the TC1000, and it is much faster than Gnome or Xubuntu. I don't use the built-in wireless on the TC1000, since it is not capable of 54g working. I have never been able to get the TC1000 pen working either.

Once installed, I recommend using hibernate rather than shut-down to speed up your power-on process - it works on mine, but I have to pull the PCMCIA wireless network card out and plug it back in to get it to work on restart.

Overall, though, I'm not sure it's all worth the bother, unless you enjoy trying things like LXDE!

---

### Post by pvhoward on 2009-03-30
ahhh... ill give it a try thanks, i appreciate it

---

### Post by pvhoward on 2009-03-30
Hey, when the instructions that you linked me to say...

"now we have to edit the slim settings, just as before. However, it can be done without having to log in at all:

sudo nano /etc/slim.conf
nano ~/.xinitrd                       "

where does the "nano ~/.xinitrd" command go?

---

### Post by Aearenda on 2009-03-30
Both of these steps assume that you are still using the console from which you did the installation of the lxde packages earlier. You can't use leafpad since there is no previously-installed GUI in the Intrepid instructions, unlike the Hardy instructions. After opening nano on /etc/slim.conf you should make the change from 'xfce4-session' to 'startlxde' as described on the linked page [http://ubuntu-lxde.wikidot.com/slim](http://ubuntu-lxde.wikidot.com/slim) (but nano uses different keystrokes from leafpad - F6 or CTRL and W are used for searching, and F2 (or CTRL and X) then Y and ENTER to save); then you save that file, and do the second command, which creates ~/.xinitrc (note, not ~/.xinitrd) containing the one line 'exec startlxde'. I hope this makes sense!

---

### Post by pvhoward on 2009-03-31
excellent thanks!... I have finished the LXDE install, I really like it, except that I cannot get my wireless working, can you offer any tips?

---

### Post by Aearenda on 2009-03-31
The TC1000 wireless is an Atmel device I think - it needs firmware. I remember getting it going and then giving up on it since it is so slow (10Mb/s max, not 54), and it always hung the machine on shutdown. I recommend you get an external wireless device (USB or PCMCIA), or buy a dead TC1100 on ebay and use the mini-pci wireless from that (which does work in a TC1000 - I've done it), or indeed get another wireless card from almost any source!

PS - you could try using ndiswrapper to run the wireless using the Windows XP driver, downloaded from HP's website. But again, it's slow, and it only does WEP not WPA, so I suggest you ditch the internal wireless.

---

### Post by pvhoward on 2009-03-31
Thanks man, I appreciate it.

---

### Post by mr_deimos on 2009-03-31
> **Aearenda said:**
> I recommend you get an external wireless device (USB or PCMCIA), or buy a dead TC1100 on ebay and use the mini-pci wireless from that (which does work in a TC1000 - I've done it), or indeed get another wireless card from almost any source!


Just run a search for intel pro wireless cards on ebay, they're 100% supported by ubuntu (and they're really solid hardware too):
[http://shop.ebay.com/?_from=R40&_trksid=p3907.m38.l1313&_nkw=intel+pro+wireless+mini-pci&_sacat=See-All-Categories](http://shop.ebay.com/?_from=R40&_trksid=p3907.m38.l1313&_nkw=intel+pro+wireless+mini-pci&_sacat=See-All-Categories)
You can get them as cheap as 9$ including shipping. TC1100 uses 2100 model, but if you get the newer 2200 - that's even better. Just make sure it's mini-pci, **not** mini pci-e

---

### Post by Aearenda on 2009-04-24
Just FYI - I did a fresh install of 9.04 (Jaunty) on my crippled TC1100, and it is working well - much faster start up.

I installed the Nvidia driver, copied my xorg.conf unchanged from Intrepid to get the tablet to work, and I installed the latest madwifi wireless driver from source. I added tc1100-wmi to /etc/modules. It still takes a long time to associate on wireless. Since I no longer use this away from home (it will not restart properly when warm - Nvidia goes AWOL), I didn't bother with the side buttons.

---

### Post by Rayaz on 2009-04-25
Hi all,

I've just installed Jaunty on my TC1100 and cannot seem to get the screen rotation going properly. With a rotate script I can get the screen to rotate by not the cursor nor stylus. Any help would be much appreciated.

Regards
Rayaz

---

### Post by Favux on 2009-04-25
Hi Rayaz,

The problem is that the callout in the 10-wacom.fdi file returns HAL/D-BUS names that are not recognized by linuxwacom.  So xsetwacom doesn't work.  No rotation of wacom devices or wacomcpl.  Rec discovered this and came up with a script to fix it here:  [http://ubuntuforums.org/showthread.php?t=1122952](http://ubuntuforums.org/showthread.php?t=1122952)

If you read Jaunty Users near the top here you'll see there seems to be two ways to go.  One is to use rec's script.  The link takes you to a HOW TO at post #104 on page 11:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  Since you have a serial tablet you shouldn't need to worry about the wacom.ko stuff.

Timo Aaltonen (who patched the "native" Jaunty 0.8.2-2 linuxwacom to work with HAL and Xserver 1.6) also has a ppa for xorg-xserver where he may have fixed the problem.  It's been up a few days so who knows when it'll be in an update.

---

### Post by bigbamboo on 2009-04-27
Hi Rayaz,
I've just installed Ubuntu 9.04 on my TC1100 to get rid of some issues with stylus button and a PCMCIA Aircard.

The rotation works properly, this is the code I used (get from internet): 
```

IFS=$'\n'
DEVS=`xsetwacom list dev | \
   sed -e 's/ *$//g' -e 's/\(.*\) .*/\1/g' -e 's/ *$//g'`
ROTATION=`xrandr --verbose --query | \
   grep 'default connected' | \
   sed -e 's/^.*(.*) \(.*\) (.*).*$/\1/'`

# Rotate all detected wacom devices to the given direction.
function rotate_devices()
{
   for DEV in $DEVS; do
      xsetwacom set $DEV rotate $1
   done
}

if [[ ! $ROTATION == "normal" ]]; then
   xrandr -o normal
   rotate_devices none
else
   xrandr -o left
   rotate_devices ccw
fi
exit 0

```

Initially I wasn't able to make the sylus rotate, but this was because the stylus wasn't recognized as mouse device in xorg.conf file.

here's the code I added to xorg.conf:

```
Section "InputDevice"
   Identifier "stylus"
   Driver     "wacom"
   Option     "Type"        "stylus"
   Option     "Device"      "/dev/input/wacom" 
   #Option     "Device"      "/dev/ttyS0"
   Option     "ForceDevice" "ISDV4" 
   Option     "Button2" 	"3"
EndSection

Section "ServerLayout"
   Identifier "Default Layout"
   Screen "Default Screen"
   InputDevice "stylus" "SendCoreEvents"
EndSection
```

A problem I have is that the stylus have to be activated by terminal command:
```
echo "1" > /dev/input/wacom 
```
So I'm trying to set this command on system startup (but I don't know how).

Another problem I have with 9.04 release is that xbindkeys doesn't work at all, so I'm still not able to have the stylus and Q buttons working.

@Aearenda
I didn't install the madwifi wireless driver since the wi-fi connection is fast and smoothly working, do you suggest to install this driver anyway?

---

### Post by Aearenda on 2009-04-27
If your wi-fi is working, don't mess with it! I installed the latest to see if it would associate faster, and it doesn't.

You can add system startup commands to /etc/rc.local - but I didn't have to do anything to make the stylus work apart from the xorg.conf change.

---

### Post by MyR on 2009-04-28
I added the command to /etc/rc.local and it doesn't work - I still have to manually enter it.

---

### Post by Aearenda on 2009-04-28
Maybe doing it in rc.local is too soon in the startup process - try making a file in your home directory called something like .start-wacom, like this:
```
#!/bin/bash
echo "1" > /dev/input/wacom
```
Make it executable with ```
chmod u+x .start-wacom
```
Then add it to your session start programs by creating an extra entry under system->preferences->Startup applications

---

### Post by MyR on 2009-04-28
> **Aearenda said:**
> try making a file in your home directory called something like .start-wacom

That did it! Thanks! Don't know why I didn't think of that..

peace

---

### Post by olaoni on 2009-04-28
Hi Aearenda,

I did a fresh install of ubuntu 9.04, but unlike your success story I can't get my stylus side buttons to work any longer.

Before I did this new install I had everything working as clock work but now I can't get any of the tablet function on my machine.

Unfortunately I did not save my previous xorg.conf file. So I had to edit the current one with the following entry
```

Section "InputDevice"
   Identifier "stylus"
   Driver     "wacom"
   Option     "Type"        "stylus"
   Option     "Device"      "/dev/input/wacom" 
   #Option     "Device"      "/dev/ttyS0"
   Option     "ForceDevice" "ISDV4" 
   Option     "Button2" 	"3"
EndSection

Section "ServerLayout"
   Identifier "Default Layout"
   Screen "Default Screen"
   InputDevice "stylus" "SendCoreEvents"
EndSection
```

When I restart my machine, the screen remains blank, and does not give me the opportunity to log in.

To continue I have to shut down and restart in "recovery mode" then remove the new entry from the xorg.conf file.


Any pointers will be appreciated.

---

### Post by Aearenda on 2009-04-29
By "stylus side buttons" do you mean the three buttons on the front of the tablet, or the right-click button on the side of the stylus?

Assuming you mean the three on the front, I have never bothered with them - they needed patches to the wacom driver - so I can't help there, sorry. 

Right-clicking with the stylus works fine for me. You need a complete xorg.conf file - I think yours is missing some bits. Here is mine:```
Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"      # Change to
                                                        # /dev/input/event
                                                        # for USB
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
        Option          "Button2"       "3" # This is the line you need for the stylus button to right click
EndSection
Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"      # Change to
                                                        # /dev/input/event
                                                        # for USB
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
        Option          "Button2"       "3" # This is the line you need for the stylus button to right click
EndSection


Section "Device"
	Identifier	"Configured Video Device"
	Driver "nvidia"
	Option "AddARGBVisuals" "True"
	Option "AddARGBGLXVisuals" "True"
	Option "NoLogo" "True"
	Option "RandRRotation" "on"
# Next line was "1", SET TO "0" TO SEE IF STANDBY WILL WORK
	Option "NvAGP" "0"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	screen "Default Screen"
        InputDevice     "stylus"        "SendCoreEvents"
	InputDevice	"cursor"	"SendCoreEvents"
EndSection

Section "ServerFlags"
	Option "AutoAddDevices" "false"
EndSection

Section "Extensions"
    Option "Composite" "Enabled"
EndSection

```This was copied straight from Intrepid.

---

### Post by olaoni on 2009-04-29
Aearenda,

Thanks the xorg.conf file you posted. The stylus is now working properly again.

Regards

---

### Post by Aearenda on 2009-04-29
Glad to hear it! I just wish my TC1100 was still reliable :-(

---

### Post by bigbamboo on 2009-04-29
Hi olaoni,
in ubuntu 8.10 it was possible to use the stylus buttons by patching the wacom tools 0.8.1.4 
([http://wiki.linuxquestions.org/wiki/Tc1100#Stylus_buttons](http://wiki.linuxquestions.org/wiki/Tc1100#Stylus_buttons)) 

By the way I wasn't able to patch the new wacom tool I use in ubuntu 9.04, so the buttons still doesn't work.

Did you find a solution?

---

### Post by MyR on 2009-04-29
> **bigbamboo said:**
> Hi olaoni,
in ubuntu 8.10 it was possible to use the stylus buttons by patching the wacom tools 0.8.1.4 
([http://wiki.linuxquestions.org/wiki/Tc1100#Stylus_buttons](http://wiki.linuxquestions.org/wiki/Tc1100#Stylus_buttons)) 

By the way I wasn't able to patch the new wacom tool I use in ubuntu 9.04, so the buttons still doesn't work.

Did you find a solution?

I just patched the new wacom-tools without any trouble.  The only difference is the version number (from 0.8.1.4 to 0.8.2.2) used in the commands.  The patch is exactly the same.

peace

---

### Post by olaoni on 2009-04-29
Hi bigbamboo,

In ubuntu 8.10 I did have the stylus buttons working (cellwriter, xournal and screen rotation). 
To get these buttons to work. The process involved downloading and compiling wacom source. The version I built was linuxwacom-0.8.2-2.
After the compilation is successful, copying the wacom_drv.so generated file to 
/usr/lib/xorg/modules/input/wacom_drv.so ( I have not tried this for 9.04 yet).
I will not be able to test this for the next 6 hours or so. But I will keep you posted on my progress. See [http://http://ubuntuforums.org/showthread.php?p=3672701#post3672701]("http://http://ubuntuforums.org/showthread.php?p=3672701#post3672701")

---

### Post by bigbamboo on 2009-04-30
MyR,
I tried to patch the new wacom-tools but the process ends up in a bunch of errors, maybe I miss something.

I'll try again.

---

### Post by bigbamboo on 2009-04-30
this is the error I get when trying to compile wacom-tools-0.8.2.2 :
```
admin@tc1100:/usr/src/wacom-tools-0.8.2.2/linuxwacom$ sudo patch -p1 < ~/wacom.patch
patching file src/xdrv/wcmISDV4.c
Hunk #1 FAILED at 231.
1 out of 1 hunk FAILED -- saving rejects to file src/xdrv/wcmISDV4.c.rej

```
the wacom.patch file I used is attached.

---

### Post by olaoni on 2009-04-30
Hey bigbamboo,

I am not an expert at building source, but I did manage to build the wacom-tools-0.8.2.2 driver.

I have attached to this reply my wcmISDV4.c file which I used to build my source.

I have renamed the file extension to a .txt to allow attaching to this reply I hope it helps.

---

### Post by MyR on 2009-04-30
bigbamboo
The patch you used is correct.  Sorry, I'm not sure what would cause that error.  One difference is that I upgraded from 8.10 rather than freshly installing 9.04.  If something goes wrong you can start over by deleting the source and starting again from the beginning:
cd /usr/src
sudo rm -r wacom*
sudo rm xserver*

Before I ran the commands I switched to root using:
sudo su
because nearly all of them need to be run as root.

One last thing: I'm not sure the wiki mentions but you need build-essential installed.
sudo aptitude install build-essential

hope this helps. peace

---

### Post by mu3en on 2009-05-02
fresh install of Jaunty actually does work out of the box. There are a couple of caveats though, as noted in the following entry.
[https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/358643](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/358643)
everything needed to get fully functional should be there. have not patched the wacom driver for stylus buttons but according to posts on this page, should not be an issue.
hope that gets everyone up & running.

---

### Post by ishtob on 2009-05-22
i got devscript and the debuild command worked like a charm. XEV is now reading the 3 buttons.

I am having issues with the screen rotation, it only rotates the screen, but not the stylus.
I think the problem is with my xorg.conf, i can't add the line:

Section "ServerLayout"
	Identifier	"Default Layout"
	screen "Default Screen"
        InputDevice     "stylus"        "SendCoreEvents"
	InputDevice	"cursor"	"SendCoreEvents"
EndSection

because that will cause the table to get stuck in a virtual terminal and unable to start X with the /etc/ini.d/kdm restart

help!

---

### Post by mr_deimos on 2009-05-28
> **ishtob said:**
> i got devscript and the debuild command worked like a charm. XEV is now reading the 3 buttons.

I am having issues with the screen rotation, it only rotates the screen, but not the stylus.


It's a normal behavior. screen rotation is done by xrandr and the digitizer rotation is done by wacom-tools. So whenever you rotate the screen, you also have to notify the wacom driver about this. One way is to create a script that will both rotate the screen and digitizer. But it will only work if you only rotate the screen using this script. If you use something else (like a gnome panel applet), you will once again have screen and digitizer in different orientations.
Much better solution is a simple daemon monitoring current screen orientation and setting digitizer orientation accordingly. This way the screen and cursor will always stay aligned, no matter how the screen got rotated.
There's a nice example of such a daemon written by author of easystroke, see here (scroll down to "don't use rotate scripts" section):
[http://easystroke.wiki.sourceforge.net/TipsAndTricks](http://easystroke.wiki.sourceforge.net/TipsAndTricks) 
Just compile the rotate.c program and add it to your session startup programs.
One feature i really miss from it is using different calibration data for portrait and landscape modes. I hacked this daemon a bit to support such a feature, but it's done in such a way that it's not even worth posting :P I did it by (manually) creating two bash scripts, one setting calibration data for portrait mode, and the other for landscape. After rotating the digitizer, the modified daemon launches the proper (portrait or landscape) calibration script.
I tried to make it read and store calibration data before rotating so that you wouldn't have to create additional scripts manually, but you would only need to calibrate the screen in landscape mode, rotate, calibrate it again in portrait mode and rotate again. However i've been unsuccessful with that so far. Maybe someone more familiar with coding for linux than me will be able to develop something like that?

---

### Post by ishtob on 2009-06-08
thanks, got the stylus buttons working and binded using xbindkeys. rotation also works thanks to that script :D

I do have one more question, what command do I use to bring up cellwriter's window? I tried in the .xbindlkeysrc
```

"cellwriter"
  b:32

```
nothing happens, then I tried
```

"cellwriter --show-window"
  b:32

```

no cellwriter poping up when the button is pressed.
I'm sure the buttons are working since the xournal and rotate scripts are working perfectly

---

### Post by MyR on 2009-06-08
> **ishtob said:**
> thanks, got the stylus buttons working and binded using xbindkeys. rotation also works thanks to that script :D

I do have one more question, what command do I use to bring up cellwriter's window? I tried in the .xbindlkeysrc
```

"cellwriter"
  b:32

```
nothing happens, then I tried
```

"cellwriter --show-window"
  b:32

```

no cellwriter poping up when the button is pressed.
I'm sure the buttons are working since the xournal and rotate scripts are working perfectly

Try entering "cellwriter" into a terminal and see if that works.  Otherwise it will probably tell you what the problem is.

peace

---

### Post by ishtob on 2009-06-09
looks like a reboot did the trick :P and just cellwriter works. I am wondering if there is a way so that if I press that button it will close cellwriter if its open

another thing, has anyone noticed that alignment of the stylus goes off on resume if you go on suspend to RAM in portrait mode? I tired using this script in /etc/acpi/resume.d/99-scripts.sh
```
#!/bin/bash

while true; do

        ## is X on?
       display=`echo $DISPLAY`
        ## Check if it is detected
       if [ "$display" = :0.0 ]; then
            
                ##get out of the loop 
                break
       fi
done



else

sudo -u *username* $/home/andy/scripts/calibrate.sh &
exit 0

``` replaceing *username* with your username
calibrate.sh script:
```

#!/usr/bin/env bash

IFS=$'\n'
DEVS=`xsetwacom list dev | \
   sed -e 's/ *$//g' -e 's/\(.*\) .*/\1/g' -e 's/ *$//g'`
ROTATION=`xrandr --verbose --query | \
   grep 'default connected' | \
   sed -e 's/^.*(.*) \(.*\) (.*).*$/\1/'`

# Rotate all detected wacom devices to the given direction.
function rotate_devices()
{
   for DEV in $DEVS; do
      xsetwacom set $DEV rotate $1
   done
}

if [[ ! $ROTATION == "normal" ]]; then
   xsetwacom set stylus BottomY 21240
   xsetwacom set stylus BottomX 15980
   xsetwacom set stylus TopY 0
   xsetwacom set stylus TopX 0
   xsetwacom set eraser BottomY 21240
   xsetwacom set eraser BottomX 15980
   xsetwacom set eraser TopY 0
   xsetwacom set eraser TopX 0
else
   xsetwacom set stylus BottomX 21240
   xsetwacom set stylus BottomY 15980
   xsetwacom set stylus TopY 0
   xsetwacom set stylus TopX 0
   xsetwacom set eraser BottomX 21240
   xsetwacom set eraser BottomY 15980
   xsetwacom set eraser TopY 0
   xsetwacom set eraser TopX 0

fi
exit 0

``` (i use an eraser stylus so you can omit the set eraser lines if u dont own one.)

but for some reason, this script doesn't take effect I come back from suspend. and the alighnment of the stylus would still be off. I;m sure my calibrate script works because that's what I use to get my sylus synced again, but I have to do that manually after every resume. (i bound it to one of the side buttons) I am still trying to find a way to have it run automatically after each resume.... anyone has an idea on how to do this?

update: i took out the "else" after done in the resume script, and now it will aligh the stylus to the landscape position regardless of the orientation of the screan (yes, even if it's in portrait)

---

### Post by MyR on 2009-06-09
I notice "andy" is the user hard-coded into the first script you have there.  Not sure if that's you or the original author.

Alternately you can use the script from a related thread on launchpad:
wget [http://launchpadlibrarian.net/23072115/03calibrate.sh](http://launchpadlibrarian.net/23072115/03calibrate.sh)
chmod +x 03calibrate.sh
sudo mv 03calibrate.sh /etc/pm/sleep.d/03calibrate.sh

I've been thinking about putting all the tweaks on a page on my website, but I don't know how many people it would help.

peace

---

### Post by ishtob on 2009-06-09
andy is my user name :P looks like I missed it, giving your script a shot

---

### Post by Aearenda on 2009-06-10
MyR said:> I've been thinking about putting all the tweaks on a page on my website, but I don't know how many people it would help.I think this would be a great idea - or on the Ubuntu Wiki, in the style of [this one]("https://help.ubuntu.com/community/AspireOne"). This thread has grown too long to be easily understood. I just wish my poor old TC1100 still worked properly!

---

### Post by MyR on 2009-06-11
Here's what I've put together:

[Set up Ubuntu 9.04 on the HP TC1100]("http://www.unifyingtheory.net/tabletbuntu.html")

Enjoy!

---

### Post by josemasaga on 2009-06-12
Thank you very much for this.
Now, I'll try to make it work...

---

### Post by kdub on 2009-06-14
Thankyou for the excellent how-to - [http://www.unifyingtheory.net/tabletbuntu.html](http://www.unifyingtheory.net/tabletbuntu.html) - It took me a couple tries-I way over think stuff.:D
Quit thinking, followed the instructions and all is good!
 agian thankyou,
ken

---

### Post by MyR on 2009-06-14
If you rotate the screen & then suspend, the stylus calibration is off upon resume.  
Does anyone have a workaround?

---

### Post by ishtob on 2009-06-14
MyR, that's the same problem I am having

I think it is off because the screen is oriented as landscape when the resume scripts are running, and X starts later on in the resume chain of scripts... I have tried doing loops and delay scripts, but none of them seems to work, resume seems to just waits for that to finish and then keeps going.

does anyone knows how to make a script activate after X has started on resume?

update: I written a script that I can run by manually pressing a button after X has started... but this is still not a real solution.

---

### Post by MyR on 2009-06-14
> **ishtob said:**
> does anyone knows how to make a script activate after X has started on resume?

update: I written a script that I can run by manually pressing a button after X has started... but this is still not a real solution.

Any executable in /etc/pm/sleep.d/ should run upon resume.
Would you mind sharing your script?

peace

---

### Post by Aearenda on 2009-06-14
I suspect the recalibration script has to run under your logged-on username, inside its X environment, rather than in root as it would from sleep.d. Some way to trigger that to occur from the restart code is needed.

Before my TC1100 died, I was mucking around with a polling script started at login, that tested the screen orientation using xrandr and reset the calibration to suit every few minutes. I didn't keep it after migrating to my netbook, sadly.

---

### Post by MyR on 2009-06-14
> **Aearenda said:**
> I suspect the recalibration script has to run under your logged-on username, inside its X environment, rather than in root as it would from sleep.d. Some way to trigger that to occur from the restart code is needed.

The script worked perfectly well in 8.10 though.  This is what confuses me.  I don't know what changed.

---

### Post by MyR on 2009-06-14
Here's the script that worked in 8.10:

```
#!/usr/bin/env bash

IFS=$'\n'
FILE=/tmp/calibration.tmp
USER=`ps aux | grep "x-session-manager" | grep -v grep | cut -d" " -f1 | head -n 1`
DISPLAY=:0.0
DEVS=`su $USER -c "xsetwacom --display $DISPLAY list dev | \
   sed -e 's/ *$//g' -e 's/\(.*\) .*/\1/g' -e 's/ *$//g'"`
XSETWACOM=/usr/bin/xsetwacom

function store_value()
{
    value=`su $USER -c "$XSETWACOM --display $DISPLAY get $1 $2"`
    echo "$XSETWACOM --display $DISPLAY set $1 $2 $value" >> $FILE
}

# Store calibration of all devices
function store_devices_calibration()
{
    >$FILE
    for DEV in $DEVS; do
	store_value $DEV "TopX"
	store_value $DEV "TopY"
	store_value $DEV "BottomX"
	store_value $DEV "BottomY"
    done
}

# Store calibration of all devices
function restore_devices_calibration()
{
    if [[ -e $FILE ]]
    then
	( sleep 2; su $USER -c "source $FILE")&
    fi
}

MODE=$1

case "$MODE" in
    hibernate|suspend)
	store_devices_calibration
	;;
    thaw|resume) 
	restore_devices_calibration
	;;
    *) exit $NA
        ;;
esac
```

This would be a lot easier if I knew bash scripting.  However it looks to me like 'sleep 2; su $USER -c "source $FILE"'  waits 2 seconds after resume (enough time for X to start) then runs the command as the user, not root.  However the configuration file (/tmp/calibration.tmp) is empty; I even experimented with a different path to the file in my home directory.  Thus the commands to re-set the proper calibration are not being written to the file.  So the problem in the script would appear to lie in the DEVS=`su $USER -c "xsetwacom --display $DISPLAY list dev | \
   sed -e 's/ *$//g' -e 's/\(.*\) .*/\1/g' -e 's/ *$//g'"` part, and I have no idea what's going on there.  Any ideas?

Edit: When I run the script manually it writes to the file correctly.  So .. />??!
Edit2: @Aearenda Looks like you were right yet again ;] If I just put my user name in for USER then it works as expected instead of letting it try to figure out what my user name is.  I shall update my guide.  thanks for the help!

---

### Post by Aearenda on 2009-06-15
I'm glad you've got it working, though I tried the line that gets USER and it works for me.

ps aux - lists all processes
grep "x-session-manager" | grep -v grep - cuts out all processes we are not interested in, including the one that was doing the grep
cut -d" " -f1 - using space as a delimiter, extract the first field (username)
head -n 1 - Just take the first line

I have no idea why the script would work with a hard coded username only.


Here's my guess at the sed regex process:
xsetwacom - prints a list of devices and types
's/ *$//g' Removes trailing spaces
's/\(.*\) .*/\1/g' Removes the second column
's/ *$//g' Removes trailing spaces again
The result is two lines, containing the names of the stylus and cursor devices.

Anyway, once again, it's working, we don't quite know why but we're happy!

---

### Post by Digitallysick on 2009-06-15
When the tc1100 is changed from portrait to landscape the stylus for me goes crazy and doesn't match on the screen, how can I fix this? 

I also cant get the rotate button to work =(

---

### Post by ishtob on 2009-06-15
myR this is what I use to manually calibrate the screen after suspending. I did try putting this in the sleep.d folder, but it only works when i suspend in landscape... it doesn't do anything when I suspend in portrait.. the pen still goes off when resuming from portrait

```

#!/usr/bin/env bash

if [ -n "$(xrandr | grep 768x1024)" ]; then
   xsetwacom set stylus BottomY 21240
   xsetwacom set stylus BottomX 15980
   xsetwacom set stylus TopY 0
   xsetwacom set stylus TopX 0
   xsetwacom set eraser BottomY 21240
   xsetwacom set eraser BottomX 15980
   xsetwacom set eraser TopY 0
   xsetwacom set eraser TopX 0
else
   xsetwacom set stylus BottomY 15980
   xsetwacom set stylus BottomX 21240
   xsetwacom set stylus TopY 0
   xsetwacom set stylus TopX 0
   xsetwacom set eraser BottomY 15980
   xsetwacom set eraser BottomX 21240
   xsetwacom set eraser TopY 0
   xsetwacom set eraser TopX 0

fi
exit 0


```

of course, you will need to find your own X and Y coordinates:
```
xsetwacom get stylus TopX BottomX TopY BottomY
```

---

### Post by MyR on 2009-06-15
> **Aearenda said:**
> I have no idea why the script would work with a hard coded username only.

I'm running xubuntu so I don't have x-session-manager.  

> **Digitallysick said:**
> When the tc1100 is changed from portrait to landscape the stylus for me goes crazy and doesn't match on the screen, how can I fix this? 

I also cant get the rotate button to work =(

Did you have a look at my [9.04 tutorial]("http://www.unifyingtheory.net/tabletbuntu.html")?

For screen rotation you need: the proprietary nvidia driver, the correct xorg.conf, and a rotation script that rotates both the screen AND stylus (like in my tutorial).  Following those step will get rotation via the rotate command

For the rotate button you need: the above plus properly configured xbindkeys running and the wacom driver patch, also explained in the tutorial.  I know it's a pain but it's just a lot of copy/pasting for it to work.
> **ishtob said:**
> myR this is what I use to manually calibrate the screen after suspending. I did try putting this in the sleep.d folder, but it only works when i suspend in landscape... it doesn't do anything when I suspend in portrait.. the pen still goes off when resuming from portrait

of course, you will need to find your own X and Y coordinates

Thanks for sharing! That doesn't sound **too** bad.  It only works in landscape because the values you hard-coded in are from landscape mode.  If you wanted you coould get the values for topx etc from portrait mode and then include something in your script that detects what mode the screen is in and uses the proper values.

However the script I have now works great for both portrait and landscape.  Make sure you have the nvidia driver and xorg.conf.

peace

---

### Post by Aearenda on 2009-06-15
> I'm running xubuntu so I don't have x-session-manager. 
There must be an equivalent process running that you can grep to make the script more generic - all that bit does is work out what username is logged on!

---

### Post by serversphere on 2009-06-20
> **Aearenda said:**
> Before my TC1100 died, I was mucking around with a polling script started at login, that tested the screen orientation using xrandr and reset the calibration to suit every few minutes. I didn't keep it after migrating to my netbook, sadly.

By 'didn't keep it', do you mean it's been deleted? Or is it something you could post here? If not, I might write one up myself.

KUDOS for your Jaunty how-to page. It's wonderful. I was running Windows for the longest time, but decided to try Jaunty on the TC this week when I grabbed a used hard drive from ebay. Now I just swap out the drive if I absolutely need Windows for a meeting. :)

---

### Post by Aearenda on 2009-06-20
> **serversphere said:**
> By 'didn't keep it', do you mean it's been deleted?Yes, sorry.

> KUDOS for your Jaunty how-to page. It's wonderful. I was running Windows for the longest time, but decided to try Jaunty on the TC this week when I grabbed a used hard drive from ebay. Now I just swap out the drive if I absolutely need Windows for a meeting. :)
It was MyR who did that, not me, and I think it's good too.
I'm glad Ubuntu is working so well for you!

---

### Post by ishtob on 2009-06-26
myR, my script works fine in both modes, not just landscape if I run it after a resume.but for some reason it doesn't work if I put it to automatically run on resume

---

### Post by MyR on 2009-06-26
> **ishtob said:**
> myR, my script works fine in both modes, not just landscape if I run it after a resume.but for some reason it doesn't work if I put it to automatically run on resume

try putting a "sleep 2" in your script before it sets the values.  This is what the author of the script I use had to do to keep the custom values from being overwritten.

peace

---

### Post by ishtob on 2009-06-28
do you think my KDE environment might be the difference? I am running kubuntu

---

### Post by MyR on 2009-06-28
> **ishtob said:**
> do you think my KDE environment might be the difference? I am running kubuntu

I'm not sure how to fix your script since I know very little about bash scripting.  If anyone else can help, then feel free.

However the script I have will now work on any Ubuntu flavor with the modification I made (entering the user name variable manually as described in my [Ubuntu 9.04 TC1100 guide]("http://www.unifyingtheory.net/tabletbuntu.html")).

peace

---

### Post by ishtob on 2009-06-29
i tried and it still not working right when i suspend on portrait mode

---

### Post by Favux on 2009-06-29
Hi ishtob,

Cyberfish came up with a couple of calibration scripts for Jaunty.  The second, more refined, version is in Section 4 of post #104 here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)  Even if you can't use it maybe it can give you some ideas.

---

### Post by setasai on 2009-07-11
I am having an issue with hibernation.

Everything else seems to work ok but when i hibernate from gnome... it gives a series of

Memory corruption detected in low memory...

errors...

Then when it boots up it stops at "waking up... please wait" and crashes...

Anybody know what that means?

---

### Post by extexmex on 2009-07-12
> **setasai said:**
> I am having an issue with hibernation.

Everything else seems to work ok but when i hibernate from gnome... it gives a series of

Memory corruption detected in low memory...

errors...

Then when it boots up it stops at "waking up... please wait" and crashes...

Anybody know what that means?

You need to blacklist intel_agp to get hilbernation working: As root, create the file /etc/modprobe.d/blacklist-agp.conf that just contains the line

blacklist intel_agp

You may still see the memory corruption errors though, but resume from hilbernation will work nevertheless.

But there seems to be a downside though: After that, suspend to ram does not seem to work reliable any more. Please post your experience with that workarround.

---

### Post by SilverTrumpet999 on 2009-07-18
Hi folks, I've read almost this entire thread and gotten Ubuntu working on my TC1100 almost to my liking.  I have a couple questions that need answering, though, mainly related to the extra hardware buttons by the jogdial.  

I believe the Q and indented screenshot buttons are mapped to keycodes c:151 and c:159 (not certain if that's respective or not) on my config.  They respond and are recorded by the OS, but when I try to bind them in the Keyboard Shortcuts GUI they are recorded as 0x97 and 0x9f... and they don't trigger the actions they are bound to.  It's worth noting that the Esc and Tab buttons have proper functionality, as does the jogdial (brightness + Enter if pressed).  

My config is pretty much shiny updated 9.04 with MyR's Tabletbuntu guide (Thanks much!) carefully and completely applied.

I want one to trigger Expo and the other the window picker.  I do have xbindkeys installed and running, and think I could bind them to a script with little effort using their keycodes - but I have had very little luck figuring out how to trigger these Compiz functions from a script, so that's of limited help.  

Really enjoying the rest of the experience, and this would help me get reasonably productive with multiple desktops while in slate mode away from the keyboard.

---

### Post by SilverTrumpet999 on 2009-07-19
Answering my own questions and passing along a few other comments.  

First, the good:
I got my bindings working like I wanted with xbindkeys and two custom scripts.  Not sure if anybody else has used the pyCompiz library but it seriously simplifies the dbus interface.  After installing pyCompiz, the script to activate Expo is the following:

```

#!/usr/bin/env python
import compiz
compiz.call('expo', 'expo_key')
```And to activate Scale in the current desktop:
```

#!/usr/bin/env python
import compiz
compiz.call('scale', 'initiate_key')
```Made both executable and moved to /usr/bin, and added the following to my .xbindkeysrc:

```

# Screenshot(?) button: Compiz Expo mode via custom script
"expo"
m:0x0 + c:151

# Q-button: Compiz Scale (Expose clone) via custom script
"scale"
m:0x0 + c:159
```Now, the annoying.  I had a recurrant problem where CellWriter would crash and then refuse to restart.  Engaging debug logging & logfile gave a message that said it was already running, and quitting... when it definitely wasn't in the process list.  This annoyed me to the point that I grabbed the source, commented out the 'check if already running' part of the main.c file, recompiled & reinstalled.  However, calling "cellwriter" out of xbindkeys wasn't an option any longer as it would spawn new instances every time.  So I made a script to toggle show/hiding the CellWriter main window called celltoggle, as follows (MyR I think this might be a better way to go about it, or at least I prefer having the toggle feature):

```

#!/bin/sh
echo -n T > ~/.cellwriter/fifo

```Made it executable, moved to /usr/bin, works like a charm.  

Now, the really annoying.  My TC1100 suspended exactly once, and in the config I had forgotten to set the 15-WiFi script in sleep.d executable.  WiFi didn't come back on, but that was easily fixed.  **However, all subsequent suspend attempts fail and come back with a locked screen** (even with screen lock disabled).  I'd really appreciate any thoughts on how to debug the suspend system and what might be going on here.

---

### Post by extexmex on 2009-07-20
> **SilverTrumpet999 said:**
> 
Now, the really annoying.  My TC1100 suspended exactly once, and in the config I had forgotten to set the 15-WiFi script in sleep.d executable.  WiFi didn't come back on, but that was easily fixed.  **However, all subsequent suspend attempts fail and come back with a locked screen** (even with screen lock disabled).  I'd really appreciate any thoughts on how to debug the suspend system and what might be going on here.

I assume you mean suspend to ram? Have you tried to run s2ram (available in package uswsusp) from a virtual console? You may even try this in single user mode first. And what is your BIOS version? I had to update my TC1100 BIOS to get suspend to ram working.

---

### Post by SilverTrumpet999 on 2009-07-20
> **extexmex said:**
> I assume you mean suspend to ram? Have you tried to run s2ram (available in package uswsusp) from a virtual console? You may even try this in single user mode first. And what is your BIOS version? I had to update my TC1100 BIOS to get suspend to ram working.

Yes, I meant suspend to RAM and am currently using s2ram with the -f flag as a workaround.  It works, but to my knowledge there's no way to queue up scripts to run on wake - so I have to manually start back up the wifi (not that bad, I made a wifion script).  If there IS a way to run scripts on wake with s2ram, I'd love to be wrong there - I'd change the system pm-tools suspend scripts over to using s2ram.  Bigger problem is that the calibration is off every time until I call up wacomcpl, regardless if I suspend in portrait or landscape.  I'd prefer to use the built in pm-tools, but they just refuse to function properly.  Yeah, I know I could just make a one-button script to turn wifi back on and pop up wacomcpl but I'd like to get the pm-tools running rather than depending on a band-aid.  

You might be onto something with the BIOS.  Not sure what mine is right now, I'll check and edit in what version it's running.

Edit - Running BIOS version: FirstBIOS Pro 2002 Q3 which seems to be a VERY early one if not the 'original.'  Never needed to update it.  I'll update after flashing up to the most current version HP offers...

---

### Post by MyR on 2009-07-21
> **SilverTrumpet999 said:**
> I had a recurrent problem where CellWriter would crash and then refuse to restart.  Engaging debug logging & logfile gave a message that said it was already running, and quitting... when it definitely wasn't in the process list.  This annoyed me to the point that I grabbed the source, commented out the 'check if already running' part of the main.c file, recompiled & reinstalled.  However, calling "cellwriter" out of xbindkeys wasn't an option any longer as it would spawn new instances every time.  So I made a script to toggle show/hiding the CellWriter main window called celltoggle, as follows (MyR I think this might be a better way to go about it, or at least I prefer having the toggle feature):

Now, the really annoying.  My TC1100 suspended exactly once, and in the config I had forgotten to set the 15-WiFi script in sleep.d executable.  WiFi didn't come back on, but that was easily fixed.  **However, all subsequent suspend attempts fail and come back with a locked screen** (even with screen lock disabled).  I'd really appreciate any thoughts on how to debug the suspend system and what might be going on here.

First off, thanks for posting your solutions. I'm also glad that you found my [guide]("http://www.unifyingtheory.net/tabletbuntu.html") useful!

CellWriter: I have not experienced the issues you describe.  It crashes occasionally but starts up again easily.  With my setup the stylus button either opens cellwriter if it's not running or shows it if it is running in the tray.  Though I agree the ability to show AND hide with the stylus button is useful. Do I just point the appropriate stylus button at the "echo -n T > ~/.cellwriter/fifo" script?

Suspend: I assume when you say "locked screen" you mean locked with a password prompt.  Have you tried the commands in the "Prevent the screen from locking" section of my guide?  They must be run as the user (not root/sudo); It looks like I forgot to mention that.  You can use the commands given just run as normal user.

The only thing I can think of that doesn't work perfectly for me is the card-reader.

One more thing: not that it matters but the "screenshot button" is probably window's button to switch video output between the built-in LCD and external.

Also if anyone is comfortable at bash scripting, you could easily make one script to include all (or almost all) necessary tweaks.  I didn't go this route because I hope that people might learn a thing or two in the process of manually fixing things.

Peace

---

### Post by SilverTrumpet999 on 2009-07-22
> **MyR said:**
> First off, thanks for posting your solutions. I'm also glad that you found my [guide]("http://www.unifyingtheory.net/tabletbuntu.html") useful!

The guide is amazing!  

I'm not sure what exactly is up with my CellWriter but after I recompiled without the check it works perfectly.  But either way the toggle script is exactly that easy - point it at the script with xbindkeys.  

> **MyR said:**
> Suspend: I assume when you say "locked screen" you mean locked with a password prompt.  Have you tried the commands in the "Prevent the screen from locking" section of my guide?  They must be run as the user (not root/sudo); It looks like I forgot to mention that.  You can use the commands given just run as normal user. 

I bet I ran them as root.  I'll go re-run them shortly.  That may fix the locked screen problem but I bet it still won't suspend with pm-tools... I've made a couple scripts that simplify suspend to ram and wake/calibrate when run.  It's an acceptable workaround for the short term.

> **MyR said:**
> One more thing: not that it matters but the "screenshot button" is probably window's button to switch video output between the built-in LCD and external.

Yes, the fact that I got this used and wiped XP off immediately shows.  I wasn't sure what that button did under XP, but it's conveniently located for rebinding.

> **MyR said:**
>  Also if anyone is comfortable at bash scripting, you could easily make one script to include all (or almost all) necessary tweaks.  I didn't go this route because I hope that people might learn a thing or two in the process of manually fixing things.

You're right, and I would keep it as it is.  I definitely learned quite a bit along the way (toyed with linux off and on but it never stuck up to now) and won't be going back.

Not quite sure how I'm going to get the BIOS flashed to a new version though, as I killed off XP and don't have a multibay to boot off floppy (those being the two options HP offers).  Usually I'd have a go at it with Wine but am not really comfortable emulating something like a BIOS flash...

---

### Post by MyR on 2009-07-22
> **SilverTrumpet999 said:**
> Not quite sure how I'm going to get the BIOS flashed to a new version though, as I killed off XP and don't have a multibay to boot off floppy (those being the two options HP offers).  Usually I'd have a go at it with Wine but am not really comfortable emulating something like a BIOS flash...

You can [flash BIOS without windows]("http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html"). I think there are other methods as well.  Perhaps extexmex can tell how he updated his BIOS.

---

### Post by DannyBiker on 2009-07-26
Hey,

First of all, thank you all for this fantastic thread. With these posts and MyR tutorial, I got my HP TC1100 fully working with Jaunty in a matter of minutes...:D

Still have several questions though :

- I use a stylus with an eraser and although it does work when using Ubuntu for the first time, the eraser function disappears after all the modifications. The thing is just not working.
Is there a way to bring it back ? Even better : could there be a way to have some programs (mainly Xournal but why not Gimp) recognizing it automatically as an eraser ? That would be awesome...

- How can I map the three buttons (esc, tab and Q) on the side ?

- A more general thought here : when a newer version of Ubuntu will be released, will updates cancel all the modifications  or is there a slight hope for some of them to continue working anyway. I guess that's "live and see" subject but maybe some of you have an answer...:P


Thanks !


- EDIT : the update manager is proposing me wacom-tools updates. Will they interfer with the TC1100 setup ?

---

### Post by MyR on 2009-07-26
> **DannyBiker said:**
> First of all, thank you all for this fantastic thread. With these posts and MyR tutorial, I got my HP TC1100 fully working with Jaunty in a matter of minutes...:D
Excellent! Glad to help!
> **DannyBiker said:**
> I use a stylus with an eraser and although it does work when using Ubuntu for the first time, the eraser function disappears after all the modifications...
Is there a way to bring it back?

Try adding this to your xorg.conf:

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"
EndSection

and your "serverlayout" section needs to say:

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"stylus"	"SendCoreEvents"
	InputDevice	"eraser"	"SendCoreEvents"
EndSection

(as per [these instructions]("https://help.ubuntu.com/community/WacomTroubleshooting"))
> **DannyBiker said:**
> How can I map the three buttons (esc, tab and Q) on the side?
You have to edit your .xbindkeysrc config file. Conveniently, you should have already installed xbindkeys and have it running on startup.

"rotate"
b:30
"xournal"
b:31
"cellwriter"
b:32
"customcommand1"
c:159
"customcommand2"
c:151

Where c:151 is the display switch button and c:159 is the Q button.  And you enter your custom commands. tab and esc cannot be changed due to their nature.
> **DannyBiker said:**
> when a newer version of Ubuntu will be released, will updates cancel all the modifications or is there a slight hope for some of them to continue working anyway.
Most or all of the tweaks should be preserved but it's impossible to say for sure at this point.
> **DannyBiker said:**
> the update manager is proposing me wacom-tools updates. Will they interfer with the TC1100 setup ?
No, do not install the wacom-tools updates. You compiled a custom version of wacom-tools to allow your stylus buttons to work.

Peace

---

### Post by DannyBiker on 2009-07-27
Hey MyR, thanks for your quick answer.

Unfortunately, the changes made to xorg.conf didn't do anything. To be sure, that I understood well : I have to add the Input Device section right after the first (the stylus one) and replace the serverlayout by what you mentioned ?
This how it looks for now : [http://membres.lycos.fr/mellow44/hpbimg/xorg.png](http://membres.lycos.fr/mellow44/hpbimg/xorg.png)

Is this correct ? Sorry, I'm still learning...:oops:

Thanks for the buttons mapping instructions. I'll try it when I'll have figured out what I want to remap them for...:biggrin:
Too bad the Esc and Tab buttons can't be changed, I would I love to use them for brightness ans keep the jogdial to scroll up and down..

---

### Post by MyR on 2009-07-27
> **DannyBiker said:**
> Hey MyR, thanks for your quick answer.

Unfortunately, the changes made to xorg.conf didn't do anything. To be sure, that I understood well : I have to add the Input Device section right after the first (the stylus one) and replace the serverlayout by what you mentioned ?
This how it looks for now : [http://membres.lycos.fr/mellow44/hpbimg/xorg.png](http://membres.lycos.fr/mellow44/hpbimg/xorg.png)

Is this correct ? Sorry, I'm still learning...

Thanks for the buttons mapping instructions. I'll try it when I'll have figured out what I want to remap them for...
Too bad the Esc and Tab buttons can't be changed, I would I love to use them for brightness ans keep the jogdial to scroll up and down..
Your xorg.conf looks correct. You have to login again for it to take effect. If that doesn't work then I have no idea; maybe there are settings in each application that you need to change for it to recognize the eraser.

I saw a script somewhere that temporarily makes the jogdial adjust brightness then returns it to function as pgup/pgdown. Alternately you could enter the command in a terminal yourself to change its function (echo 0 > /sys/devices/platform/tc1100-wmi/jogdial is brightness and echo 1 > /sys/devices/platform/tc1100-wmi/jogdial is pgup/pgdown)

Peace

---

### Post by DannyBiker on 2009-07-27
I did a reboot right after the changes. It doesn't work on the desktop so I doubt it has to do with setting up applications. I'll look more deeply on the web.

I am aware of the jog dial command but I find it not very convenient to use as I would switch to one function to another rather frequently. Is there a way to convert that command into a file or shortcut that would automatically execute it? I'll search the web again.

Finally, I'd like to map the "screen" button for sleep mode but I haven't find such a command. Does it exist or would it ask for a more complex code ?

Thanks...

---

### Post by MyR on 2009-07-27
For suspend make a script with the command in this thread:
[http://ubuntuforums.org/showthread.php?t=410570](http://ubuntuforums.org/showthread.php?t=410570)

---

### Post by DannyBiker on 2009-07-27
Okay, I got the eraser to work but God, was it strange !

What I did is replacing your "Input Device" entries by this, found on the wacom project website :

> Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Device"        "/dev/input/event0"   # USB ONLY
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  # USB ONLY
  Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
EndSection


It didn't work, so I experimented and deleted the USB ONLY lines. I logged out and the graphics went mad. Impossible to load my regular configuration and had to load a low-graphic session. But oh joy, the eraser worked! The right-click button didn't though so I found myself in the same stylus situation that on the first session after Ubuntu install. 

The graphics were still problematic with the rotate shortcut button not working either. I booted again and asked the troubleshooting section to load the basic graphic configuration. I reactivated the Nvidia driver after login and rebooted again. Graphics were back to normal but still, no right-click nor rotate button. So I gave up and just restored the xorg.conf file to what it looks like on the picture I posted this morning.
Miracle : everything is back to normal but the eraser is still recognized !

If you have any idea on what happened, I'd be glad to know so I could try to  make it a more logical next time...;)

---

### Post by MyR on 2009-07-28
> **DannyBiker said:**
> Okay, I got the eraser to work

So the xorg.conf edits I gave you were correct then (at least in theory)?

My reason for posting: I just though of something else. Does the eraser rotate properly when you rotate the screen? If not, you will have to edit your rotate script to include rotation of the eraser in addition to the stylus.

Peace

---

### Post by DannyBiker on 2009-07-28
It does. So yeah, basically your edits worked but I had to...well, do strange steps in addition to make it work.

Thanks ! ;)

---

### Post by SilverTrumpet999 on 2009-07-28
> **MyR said:**
> I saw a script somewhere that temporarily makes the jogdial adjust brightness then returns it to function as pgup/pgdown. Alternately you could enter the command in a terminal yourself to change its function (echo 0 > /sys/devices/platform/tc1100-wmi/jogdial is brightness and echo 1 > /sys/devices/platform/tc1100-wmi/jogdial is pgup/pgdown)

Here's such a script that works for me.  I named it 'jogtoggle', made it executable with chmod +x, and moved it to /usr/bin - can be bound to one of the optional keys or you can put a shortcut to it on one of the Gnome panels (tell it it's an "Application in Terminal").  A terminal should pop up for 3 seconds while you can adjust the brightness, then it will change it back to pgup / pgdn and the terminal will close itself.  It may not be the best way, but it works.

```
#!/bin/sh
# This should temporarily allow the jogdial to adjust 
# screen brightness, then return it after a few seconds
# to pgup / pgdn functionality.

echo 0 > /sys/devices/platform/tc1100-wmi/jogdial
sleep 3
echo 1 > /sys/devices/platform/tc1100-wmi/jogdial
```I've tested it to be working; adjust the number after 'sleep' to be the number of seconds you need to adjust the brightness (3 works pretty decent for me).

Edit: The ideal script would be a toggle that checks the jogdial's current status and changes it to the opposite.  I don't know how to do this check, however... there seems to be a text file at the location of these echo commands but attempting to read/edit it returns a "No Such Device" error.  If anybody can figure this out, the toggle would be a better solution.

---

### Post by DannyBiker on 2009-07-28
Great SilverTrumpet, I'll try your script later and will look on the net to see if I can find something to improve it...

Doesn't HP TC1100 came with Bluetooth ? I can't seem to make it work. Don't know if it's because my device just doesn't have it or because it doesn't work...

---

### Post by SilverTrumpet999 on 2009-07-29
> **DannyBiker said:**
> Doesn't HP TC1100 came with Bluetooth ? I can't seem to make it work. Don't know if it's because my device just doesn't have it or because it doesn't work...

Mine has an adapter and Ubuntu recognized it - though I have yet to use/test it.  There should be an icon in the notification area if you have it.  

Since we installed this stuff within like 10 days of each other on the same hardware, from the same guide, using 9.04, I think it's pretty likely that if Ubuntu didn't recognize it you don't have the chip.

---

### Post by SilverTrumpet999 on 2009-07-29
I think there needs to be a patch to the tc1100-wmi drivers to allow proper checking/reporting of the status of the jogdial, wireless, etc.  The proper such command should be ```
cat /sys/devices/platform/tc1100-wmi/jogdial
``` which only reports zero regardless of state for me.  A bit of rudimentary searching returned [this page]("http://linux.derkeiler.com/Mailing-Lists/Kernel/2008-12/msg08729.html") which mentions the problem and has code for a driver patch that will allow proper reporting.  

I'm going to try this later tonight by extending MyR's guide (which included a patch for another driver).  If it works, it might be worth adding to the tutorial... though the functionality it adds is admittedly minimal.

---

### Post by MyR on 2009-07-29
> **SilverTrumpet999 said:**
> Mine has an adapter and Ubuntu recognized it - though I have yet to use/test it.  If yours doesn't show it in the notification area you may either not have it or the icon may have defaulted to "Never Show."  Check to see if you have an entry named Bluetooth in System->Preferences; if not Ubuntu probably didn't find it.  

Since we installed this stuff within like 10 days of each other on the same hardware, from the same guide, using 9.04, I think it's pretty likely that if Ubuntu didn't recognize it you don't have the chip.

My TC1100 also has bluetooth and Ubuntu had no problem finding it. If yours does then the bt icon will be in the notification area. Bluetooth is always an option in system > preferences regardless of whether you actually have bluetooth.

Peace

---

### Post by SilverTrumpet999 on 2009-07-29
> **MyR said:**
> Bluetooth is always an option in system > preferences regardless of whether you actually have bluetooth.

Edited my post to reflect this and not spread misinformation, I didn't know that was always an option regardless of hardware.

---

### Post by DannyBiker on 2009-07-30
Well, my tablet hasn't Bluetooth then. Oh well, it's not like I'm using it everyday anyway...:)

---

### Post by rjb-356 on 2009-08-10
Excellent information.  It really got my tablet working in Ubuntu.  I am a bit more than a novice, not an expert, but I have usually been a good, copy cat programmer.  Through this site and another site, I have managed to get my HP tc1100 to do, in Ubuntu, pretty much all that can be done, as a tablet PC, when running the preload OS Windows XP Tablet.  But, after using my tc1100 in both portrait and landscape, I found I did not like the case flap down, in front, when working in landscape.  So, from the above information plus, I made the "Q" button on my tc1100, rotate (flip) my landscape display 18O degrees.  It sometimes doesn't always respond exactly as expected, but it always ends in landscape.  I did the following:

Oh, and before I start I want to restate that I am not an expert.  This worked for me, on my HP tc1100, and is, what appears to be, pretty basic stuff, but I cannot take responsility for it working on anyone elses computer.  I hope it works for you.  If any expert out there has an improvement to this, by all means, please, add to this.

1. Create a text file with the name "rotate180" (without quotation marks).  

2. In the text file place:

#!/bin/sh
if [ -n "$(xrandr | grep 768x1024)" ]; then
        xrandr -o normal
        xsetwacom set "stylus" Rotate NONE
else
        xrandr -o inverted
        xsetwacom set "stylus" Rotate HALF
fi


&#8206;3. Store/save to the /usr/bin folder.

4. In the folder (/usr/bin) with rotate180:  

sudo chmod +x rotate180

5. Add to the already made changes to the text file .xbindkeysrc in the users home folder:

"rotate180"
c:159

6. Reboot and, with any luck, you will be able to use the "Q" button on HP Tablets to rotate your landscape 180 degrees.

That's it.

RJB

---

### Post by melkor2.0 on 2009-08-23
Hi, I'm not an expert in linux so to get the tablet working I've just followed the tutorial of unifyingtheory... and I had a little problem, my nvidia was not recognized automatically, so I just searched with lspci and then looked which driver was the correct so I could apt-get it and now it works fine (was the nvidia-glx-96).
However I followed the tutorial to configure xbindkeys for custom key mapping, editing the .xbindkeyscr and it doesn't work, I also added the "jogtoggle" script to the Q key and this one works! so I guess perhaps I have to do something else if I want my tc1100 to recognize b:30, b:31 and b:32 keys, any idea?

thanks

---

### Post by MyR on 2009-08-23
> **melkor2.0 said:**
> ....I guess perhaps I have to do something else if I want my tc1100 to recognize b:30, b:31 and b:32 keys, any idea?
Welcome to the forum!

Did you follow the instructions under the section "Patch the drivers to enable the stylus buttons"?

If you have any problems feel free to ask!

---

### Post by melkor2.0 on 2009-08-29
thank you, it was that! However I have another problem, I use the tablet mainly as a reader for papers and the jog dial advances too much, far from being comfortable, is a minor detail, but do you have any idea of how this could be changed?
all the best

---

### Post by olaoni on 2009-08-29
Hi Group,

My HP PC Bluetooth card mouse still not working.
Ever since I upgraded my hp-tc1100 pc from ubuntu 8.10 to 9.04 I have been unable to use my bluetooth mouse successfully.

To clarify the above statement. I can pair the mouse to the pc without any problem which at this point the mouse works as expected.

The issue occurs if the mouse is left idle or I turn off the mouse. When I try to wake up the mouse by moving it or pressing any of its buttons, nothing happens.

The only way to get this working again is if I remove the device from the bluetooth device list and then go through the entire search and pair process all over again (This as you can imagine will be quite very annoying since this is not the case with windows or even the previous ubuntu).

When the device goes to sleep in windows or ubuntu 8.10 all you have to do is press either one of its button to return to normal operation.

I will very much appreciate any help on this.

Regards

Ola

---

### Post by MyR on 2009-08-29
> **melkor2.0 said:**
> ....However I have another problem, I use the tablet mainly as a reader for papers and the jog dial advances too much, far from being comfortable, is a minor detail, but do you have any idea of how this could be changed?
The jogdial is mapped to the pgup/pgdown/enter functions.  You may be able to change how the pgup/pgdown buttons behave but I would have no idea how to do that.  You might want to start a new thread [if you can't find anything on google].  Good luck!

> **olaoni said:**
> My HP PC Bluetooth card mouse still not working.
Ever since I upgraded my hp-tc1100 pc from ubuntu 8.10 to 9.04 I have been unable to use my bluetooth mouse successfully.
Would you mind posting what make/model mouse you have?

peace

---

### Post by melkor2.0 on 2009-08-30
Ok, problem solved, you have to use a program to know the interruption signal of the keyboard, like "xev", then

you can create the file ~/.Xmodmap and put there your xmodmap commands. Just telling the keycode like this
keycode 99 = Up
keycode 105 = Down

It should be run automatically. However in my case It didn't work automatically so I just put a startup command (in xfce it's in Settings->Session and Startup) 
xmodmap $HOME/.Xmodmap

---

### Post by DannyBiker on 2009-08-31
Hey, it's me again !

I was trying to install xp tablet edition for a while to compare with ubuntu and just gave up as it was just impossible, would it be from PXE or USB keys. I wanted to install ubuntu again but my HP TC1100 won't boot from USB anymore !
Everything is set up right in the BIOS but when I insert a bootable USB key (with WinXP or Ubuntu), the HP start-up logo boots for 30 seconds then proceed with the hard drive device.

What can I do ? If it doesn't work, I will try installing Ubuntu from PXE. Nonetheless, I'd like to give the removable disk method a few more tries as it is by far the easiest...

Thanks !

PS : I just realised that the USB Key is not listed in the Bios boot devices list; I just have the "Removable Device" option. If I remember correctly, it was possible to see the USB key in a sub-menu when everything was working fine. I already tried flashing the Bios again. Didn't work...

---

### Post by Joey Calamaro on 2009-08-31
I just picked up an HP TC1000 in an (ill advised?) attempt to get an internet tablet that's got more screen real estate and functionality than my Nokia N800. Ideally I'd like to install Ubuntu on this tablet once it arrives. However I'm open to any Linux variant (really anything other than XP tablet edition would be nice).

To this point I've done some Googling and searched the Ubuntu forums but virtually all information on this topic is for the TC1100 not the TC1000. Even within this thread the only thing I really saw was the recommendation to swap out the wireless card, which is already under way. So here's the question, is Ubuntu viable on the TC1000? I want to run this as a web tablet so I will need the stylus as well as the on screen keyboard to work. The tablet will be used for light web browsing and email only but I'm an interface designer (and a Mac user) by trade so I do like a nice looking desktop environment. ;-)

Any suggestions or advice? Can I follow the TC1100 install guide or would that be asking for trouble?

---

### Post by olaoni on 2009-08-31
> **MyR said:**
> 

Would you mind posting what make/model mouse you have?

peace

Hi MyR,

Sorry for the late response. I have been away from my PC and only just picked up your response.

Below is a link to the mouse technical spec.
[http://h18000.www1.hp.com/products/quickspecs/12618_div/12618_div.HTML]("http://h18000.www1.hp.com/products/quickspecs/12618_div/12618_div.HTML")

Many thanks in advance.

Regards

Ola

---

### Post by MyR on 2009-09-01
> **melkor2.0 said:**
> Ok, problem solved, you have to use a program to know the interruption signal of the keyboard, like "xev"
Thanks for sharing!

> **DannyBiker said:**
> I wanted to install ubuntu again but my HP TC1100 won't boot from USB anymore !
I have an external CD drive so I didn't have to install with a USB key but I have a few questions.
1. Did you press the jog dial during bios startup to manually select removable device as the boot option?
2. Does your usb key work to boot other computers?
3. Have you tried using both usb ports?
4. when you say you flashed the bios but it didn't work, do you mean flashing the bios didn't work? or just that it didn't solve your problem?
5. After you tried flashing the bios, did you make sure that the boot devices were properly configured again?
6. Does your usb key have a light that show it's being read from, and if yes, does it blink when you are trying to boot from it?
30 seconds is a very long time for bios to take, mine takes 10 seconds (still long in my opinion) so if nothing above helps, then perhaps you have a hardware problem (which may also explain why you couldn't install winxp).
You could always buy/borrow an external CD drive to try that out as well.

> **Joey Calamaro said:**
> I just picked up an HP TC1000...

To this point I've done some Googling and searched the Ubuntu forums but virtually all information on this topic is for the TC1100 not the TC1000. 

Can I follow the TC1100 install guide or would that be asking for trouble?
Much of my [ubuntu tutorial on the TC1100]("http://www.unifyingtheory.net/tabletbuntu.html") should apply to the TC1000.  The one thing I'm not sure of is the tc1100-wmi driver that controls the jogdial and wireless card status.

> **olaoni said:**
> Below is a link to the mouse technical spec.
[http://h18000.www1.hp.com/products/quickspecs/12618_div/12618_div.HTML]("http://h18000.www1.hp.com/products/quickspecs/12618_div/12618_div.HTML")
[http://ubuntuforums.org/showpost.php?p=6455956&postcount=7](http://ubuntuforums.org/showpost.php?p=6455956&postcount=7)

peace

---

### Post by Joey Calamaro on 2009-09-01
> **MyR said:**
> 
Much of my [ubuntu tutorial on the TC1100]("http://www.unifyingtheory.net/tabletbuntu.html") should apply to the TC1000.  The one thing I'm not sure of is the tc1100-wmi driver that controls the jogdial and wireless card status.


Thanks. I'll be sure to use that as a resource for my impending install. I'm trying to cobble together as much information as possible on the topic and to this point the only main roadblocks I've come across are:

1. The stylus is not the standard, supported Wacom type. I did find a fix here, however:
[http://ubuntuforums.org/showthread.php?t=1140065&highlight=tc1000](http://ubuntuforums.org/showthread.php?t=1140065&highlight=tc1000)

2. I've also read that Ubuntu has an awful time with the Transmetta CPU in the TC1000 however I have no idea how badly this impacts performance or if there's a fix.

3. There seems to be some general issues with screen rotation as well as video drivers. But again I can't say if this will negatively impact my experience. I don't intend to do any hefty 3D stuff but I'd like to run Compiz Fusion.

In retrospect I probably should have picked a more supported tablet however there really wasn't much in the sub $300 price range to select from (and certainly nothing at all for the $89 I ended paying for the TC1000).

---

### Post by olaoni on 2009-09-01
[http://ubuntuforums.org/showpost.php?p=6455956&postcount=7](http://ubuntuforums.org/showpost.php?p=6455956&postcount=7)

peace[/QUOTE]

Hi MyR,

I tried the suggestion on the link above but didn't make a difference.
I will however would like to say thanks for your help. I guess I just have to keep on searching for a solution.

What ever the ubuntu team did differently in 8.10 bluetooth stack that made things work. I hope it is reproduced in 9.10 or I have to shamefully return to the world of Windows :(

Regards

Ola

---

### Post by MyR on 2009-09-01
> **olaoni said:**
> What ever the ubuntu team did differently in 8.10 bluetooth stack that made things work. I hope it is reproduced in 9.10 or I have to shamefully return to the world of Windows :(

Did you read that entire thread? I would advise posting for help on that one.

Another thing you could try is removing the latest version of bluetooth and installing an older version.

Surprising that you would pick windows over ubuntu 8.10 but hey, at least you gave it a fair shot.

peace

---

### Post by olaoni on 2009-09-02
> **MyR said:**
> 
Surprising that you would pick windows over ubuntu 8.10 but hey, at least you gave it a fair shot.

peace

It is with great regret that I have come to be considering this. I have been constantly battling with one problem or another on ubuntu. Whilst I have lots of development work to be doing?


I will wait for the release of 9.10 before I make my final call.
Thanks for your support. One great thing about ubuntu I must admit is the friendly support that is given by the community. 

Regards

Ola

---

### Post by Aearenda on 2009-09-02
> **Joey Calamaro said:**
> I just picked up an HP TC1000 in an (ill advised?) attempt to get an internet tablet that's got more screen real estate and functionality than my Nokia N800. Ideally I'd like to install Ubuntu on this tablet once it arrives. 

<snip>

Any suggestions or advice? Can I follow the TC1100 install guide or would that be asking for trouble?

The TC1000 is different - it uses a Crusoe processor, an older Nvidia chip that crashes with recent kernels unless you only use the nv driver, the pen interface is much more problematic, and there are problems with standby and hibernate. I've tried it, and I can tell you you will not be satisfied. My best effort used LXDE with a Jaunty minimal install. I even tried using Gentoo so that I could compile everything specifically for the TC1000, but it was just too hard. Best recommendation is to get a TC1100 off ebay!

---

### Post by DannyBiker on 2009-09-04
> **MyR said:**
> Thanks for sharing!

I have an external CD drive so I didn't have to install with a USB key but I have a few questions.
1. Did you press the jog dial during bios startup to manually select removable device as the boot option?
2. Does your usb key work to boot other computers?
3. Have you tried using both usb ports?
4. when you say you flashed the bios but it didn't work, do you mean flashing the bios didn't work? or just that it didn't solve your problem?
5. After you tried flashing the bios, did you make sure that the boot devices were properly configured again?
6. Does your usb key have a light that show it's being read from, and if yes, does it blink when you are trying to boot from it?
30 seconds is a very long time for bios to take, mine takes 10 seconds (still long in my opinion) so if nothing above helps, then perhaps you have a hardware problem (which may also explain why you couldn't install winxp).
You could always buy/borrow an external CD drive to try that out as well.



Well, the short answer is that I'm an idiot : I thought that the usb disk should have appeared in the "Removable Disk" list but it appeared in the "Hard Disk" instead, a list that I didn't try to explore. I was fooled by my habits with another laptop of mine...:oops:

---

### Post by maydaydog on 2009-09-06
MyR,
 
I have a fresh install of Ubuntu 9.04 on a TC1100 using your excellect tutorial and I too am stuck at this point:
 
patching file src/xdrv/wcmISDV4.c
Hunk #1 FAILED at 231.
1 out of 1 hunk FAILED -- saving rejects to file src/xdrv/wcmISDV4.c.rej
 
I tried starting from source as you posted earlier, but no joy.
 
Do you have any other suggestions to get around this problem?

---

### Post by MyR on 2009-09-06
> **maydaydog said:**
> I have a fresh install of Ubuntu 9.04 on a TC1100 using your excellent tutorial and I too am stuck at this point:
 
patching file src/xdrv/wcmISDV4.c
Hunk #1 FAILED at 231.
1 out of 1 hunk FAILED -- saving rejects to file src/xdrv/wcmISDV4.c.rej
 
I tried starting from source as you posted earlier, but no joy.

You can try the tutorial on [LQ's quide]("http://wiki.linuxquestions.org/wiki/Tc1100#Stylus_buttons").  It's a little different than the one I use.  Please post your results.

---

### Post by maydaydog on 2009-09-14
> **MyR said:**
> You can try the tutorial on [LQ's quide]("http://wiki.linuxquestions.org/wiki/Tc1100#Stylus_buttons"). It's a little different than the one I use. Please post your results.
 
I tried the tutorial on LQ's guide, and I still got stuck at the same spot with the same error message.
 
I swapped out my hard drive and installed Ubuntu 8.04, ugraded in sequence to 8.10 and then to 9.04. After I updated 9.04, I started your tutorial and I ended up getting stuck at the same spot again.
 
I used xbindkeys for b:151 to rotate the screen, but this did not do me much good since the pen did not follow along in the correct orientation.
 
I think I can live without the 3 stylus buttons or the ability to use the tablet rotated. 
 
Thanks anyway for the suggestion, MyR.

---

### Post by Aearenda on 2009-09-28
Just FYI, I installed Karmic Alpha 6 on my rather erratic TC1100, and found that the xorg.conf file I used in 9.04 (Jaunty) works after installing nvidia-glx-96 and wacom-tools, with the exception of disabling the line that says ```
Option	"AutoAddDevices"	"false"
```In other words, for Karmic AutoAddDevices needs to be 'true' or absent, otherwise the keyboard, mouse and pen don't work.

---

### Post by MyR on 2009-10-09
I filed a [bug report]("https://bugs.launchpad.net/bugs/446943") for the stylus right-click issue.

---

### Post by Aearenda on 2009-10-09
I didn't spot that! I've confirmed that the workaround works. I'm now having trouble returning from hibernate on Karmic beta, but I have yet to figure it out.

UPDATE: I've also found that the Wacom rotation commands won't work unless you add the following lines to the end of /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi, just before </deviceinfo>:
```
  <device>
    <match key="input.x11_options.Type" contains="eraser">
      <merge key="info.product" type="string">eraser</merge>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="stylus">
      <merge key="info.product" type="string">stylus</merge>
    </match>
  </device>

```This is adapted from Favux's fdi file at [http://ubuntuforums.org/showpost.php?p=7234134&postcount=176](http://ubuntuforums.org/showpost.php?p=7234134&postcount=176). It has been quite difficult to test this, since my TC1100 fails to find the Nvidia graphics on restart when it is warm. This is a known problem, apparently caused by motherboard cracking due to physical strain on the adjacent keyboard connector. In order to get it to reboot when warm, I have to detach the keyboard and blow though the vent near the keyboard connector as it goes through the BIOS start, which causes the plastic sheeting inside to vibrate, sounding like a party blowout (one of those silly things you blow through and it unrolls) - much to the amusement of my wife and dog!

---

### Post by MyR on 2009-10-11
> **Aearenda said:**
> I didn't spot that! I've confirmed that the workaround works. I'm now having trouble returning from hibernate on Karmic beta, but I have yet to figure it out.

UPDATE: I've also found that the Wacom rotation commands won't work unless you add the following lines to the end of /usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi, just before </deviceinfo>:
```
  <device>
    <match key="input.x11_options.Type" contains="eraser">
      <merge key="info.product" type="string">eraser</merge>
    </match>
  </device>
  <device>
    <match key="input.x11_options.Type" contains="stylus">
      <merge key="info.product" type="string">stylus</merge>
    </match>
  </device>

```This is adapted from Favux's fdi file at [http://ubuntuforums.org/showpost.php?p=7234134&postcount=176](http://ubuntuforums.org/showpost.php?p=7234134&postcount=176). It has been quite difficult to test this, since my TC1100 fails to find the Nvidia graphics on restart when it is warm. This is a known problem, apparently caused by motherboard cracking due to physical strain on the adjacent keyboard connector. In order to get it to reboot when warm, I have to detach the keyboard and blow though the vent near the keyboard connector as it goes through the BIOS start, which causes the plastic sheeting inside to vibrate, sounding like a party blowout (one of those silly things you blow through and it unrolls) - much to the amusement of my wife and dog!
That did the trick for rotation.

Any luck getting stylus calibration to not get screwed up after rotation and suspend on Karmic? The script I was using on Jaunty no longer works.

You can get a tc1100 on ebay for under 200 USD. I could pitch in a little money.

peace

---

### Post by Favux on 2009-10-11
Hi MyR,

Now that you've modified the .fdi you could try cyberfish's settings daemon in "Section 4: Wacomcpl and settings" at post #104 here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)

---

### Post by Aearenda on 2009-10-11
MyR, thanks but I have way too many old laptops around already! (Actually two TC1100s, both with the same hot start-up fault, and a TC1000). I use a netbook for mission-critical stuff now, the battery lasts so much longer.

I found that the calibration commands also started working after that .fdi change, but the actual numbers are different. Previously all I had to do was change the "bottom" settings, now the "top" settings are needed too. Here's the script as it stands, activated by the 'Q' button on my system.
```
#!/bin/bash

if `xrandr | grep -q "current 768 x 1024"` ;  then
	xrandr -o normal
	xsetwacom set stylus rotate none
	xsetwacom set stylus bottomy "16119"
	xsetwacom set stylus bottomx "21225"
	xsetwacom set stylus topy "71"
	xsetwacom set stylus topx "31"

else
	xrandr -o left
	xsetwacom set stylus rotate ccw
	xsetwacom set stylus bottomy "21252"
	xsetwacom set stylus bottomx "16001"
	xsetwacom set stylus topy "111"
	xsetwacom set stylus topx "110"

fi

```I got the numbers from .xinitrc after using wacomcpl to calibrate in both orientations.

I have found that hibernation works again now!

PS. All I do after suspend is hit the 'Q' button twice to rotate and rotate again to fix the calibration using this script.

---

### Post by MyR on 2009-10-18
> **maydaydog said:**
> I tried the tutorial on LQ's guide, and I still got stuck at the same spot with the same error message.
Did you install dpkg-dev and devscripts? --> sudo apt-get install dpkg-dev devscripts
It's fine if you've given up and don't want to bother...
The good news is that 9.10 doesn't need the driver to be patched :D but karmic is still very unstable

Also after much debugging I got my stylus-resume-calibration script working on karmic.  No offense but I don't want to build a settings daemon, nor have to rotate my screen a few times to get the stupid cursor back where it should be -- does anyone know what is causing this problem?

peace

EDIT:
Here's my tentative work:
[Ubuntu 9.10 Karmic Koala on the HP/Compaq TC1100 tablet]("http://www.unifyingtheory.net/tabletubuntu9.10.html")
It looks like the kernel crashes every time I suspend and it randomly crashes occasionally, so I wouldn't recommend upgrading just yet.

---

### Post by Avalon2050 on 2009-10-22
Ho guys, new to the forums, and very new to Linux. I am wriggling my way through all the new stuff, and I am getting ahead, but I gotta admit, "hacking", or customizing Ubuntu so that it works on my TC1100 is way over my head. That's why I was so grateful for the Jaunty guide you posted, MyR, many thanks!

BBack then, I eventually decided to wait for the next iteration due to some problems with the suspend/resume and bluetooth. The bluetooth stuff seems to have been fixed now, thanks to the new kernel, but alas, I do not get the stylus working.

I tried to follow your script, MyR, but it wouldn't work. I wanted to give my feedback:

After installing the graphics driver and adding your modified xorg.conf, I only got the text login window -- x wouldn't start. After deleting the xorg.conf, I was able to boot without accelerated graphics, and modified the config file. I compared with the Jaunty one and found the stylus setup which the new version didn't have. My modified version looks like this now:

```
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
    Option        "AddARGBGLXVisuals"    "True"
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "nvidia"
    Option    "NoLogo"    "True"
    Option  "RandRRotation"    "True"
    Option  "NvAGP"        "1"
    Option    "RenderAccel"    "False"
EndSection

Section "InputDevice"
    Identifier    "stylus"
    Driver        "wacom"
    Option        "Type"        "stylus"
    Option        "Device"    "/dev/input/wacom"
    Option        "ForceDevice"    "ISDV4
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
    InputDevice    "stylus"    "SendCoreEvents"
EndSection
```

With this config file, x starts and works. I followed the rest of the script, but the stylus doesn't activate the three buttons for rotation, nor does the right-click work. The other buttons won't work either. I installed dpkg-dev and devscripts, and the wacom tools (with sudo apt-get install wacom-tools).

I probably didn't install or do something very basic which is not worth mentioning, so if you have any idea why it doesn't work, I'd appreciate your input.

And in case this topic is still not closed, I will gladly provide any info you guys might need to get it all working!

Greetings

---

### Post by MyR on 2009-10-22
> **Avalon2050 said:**
> I followed the rest of the script, but the stylus doesn't activate the three buttons for rotation, nor does the right-click work. The other buttons won't work either. I installed dpkg-dev and devscripts, and the wacom tools (with sudo apt-get install wacom-tools).

I probably didn't install or do something very basic which is not worth mentioning, so if you have any idea why it doesn't work, I'd appreciate your input.
Welcome to the forum!

For right-click
In the stylus inputdevice section you need:
```
	Option		"Button2"	"3"
```

For the 3 stylus buttons you will need to patch the drivers as described in my [jaunty guide]("http://www.unifyingtheory.net/tabletbuntu.html") at the bottom where it says "Patch the drivers to enable the stylus buttons"

peace

---

### Post by Avalon2050 on 2009-10-23
Thanks for the quick reply!

I'm not sure I understand, though. In your karmic guide, you left the entire stylus input device section out (which, as I said, made the x window hesitate). So should I throw the entire stylus input device section in then, as you stated in the Jaunty guide?

Second question: in an earlier post, you wrote:
"The good news is that 9.10 doesn't need the driver to be patched :grin: but karmic is still very unstable"

I figure you didn't mean the wacom tools drivers then, since you wrote in your answer to my post that I would have to patch then. So what did you mean by that?

Last question (for now): does your jaunty patch work on the 0.8.4.1 drivers of the wacom tools? If not, is there any way to download the 0.8.2.2 drivers?

Thanks in advance
Chris

PS: just found out that the patching doesn't work; when I try to install the debs (dpkg -i *.deb), I get this message:

dpkg: error processing *.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 *.deb

I am sure the debuilding didn't work as it should as well, looked hinky.

When I entered the command for downloading the build-deps (apt-get build-dep wacom-tools), I got the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 89 not upgraded.

Hope you can make anything out of it, and thanks for helping!

Chris

---

### Post by MyR on 2009-10-23
Chris,
> **Avalon2050 said:**
> So should I throw the entire stylus input device section in then, as you stated in the Jaunty guide?
You need it for Jaunty if that is what you are using. Just replace your entire xorg.conf with the one in my Jaunty guide as directed.

> **Avalon2050 said:**
> Second question: in an earlier post, you wrote:
"The good news is that 9.10 doesn't need the driver to be patched :grin: but karmic is still very unstable"

I figure you didn't mean the wacom tools drivers then, since you wrote in your answer to my post that I would have to patch then. So what did you mean by that?
Jaunty guide is for Jaunty and Karmic guide is for Karmic.  Follow the instructions in the guide only for the version you are using.

> **Avalon2050 said:**
> Last question (for now): does your jaunty patch work on the 0.8.4.1 drivers of the wacom tools? If not, is there any way to download the 0.8.2.2 drivers?
since you have wacom-tools 0.8.4.1 I would guess you installed Karmic.  I would not recommend it for beginners; the development version is generally for testing purposes only.  Regardless, that version of wacom-tools does not need to be patched.

---

### Post by Avalon2050 on 2009-10-24
Oops, I just reread my first post and saw that it was ambiguous. What I meant to say was that I tried the Jaunty guide, which worked great, but due to other shortcomings involving bluetooth and resume (after suspend sometimes the graphics driver wouldn't work, meaning the desktop reverted to the pre-nvidia quality), I didn't stay with it and wanted to wait for the next version, which is karmic koala. Now I tried again and found tthe same problems you guys have been having here, and with your karmic guide, it didn't work.

I have installed the wacom drivers with

```
sudo apt-get install wacom-tools
```I followed your karmic guide, but the buttons do not work. The rotate script works great when executed, but the buttons stay dead.

Any ideas? Did I maybe forget something basic, like build-essential? (Obviously, I didn't forget the build-essential, I am just using it as an example for something basic ;))


I installed the RC now, which should be, barring special occasions, the same as the final release. Even if not, I am still interested in testing my skills with linux and ubuntu ;) but thanks for the warning.

On the up side, everything else works great. I made launchers for brightness and rotate for now, and right-click, rotation and all that works great. I'm still testing and finnagling with the suspend trouble, maybe there's a setting that'll help there.

---

### Post by MyR on 2009-10-24
> **Avalon2050 said:**
> The rotate script works great when executed, but the buttons stay dead.

Any ideas? Did I maybe forget something basic, like build-essential? (Obviously, I didn't forget the build-essential, I am just using it as an example for something basic ;))

build-essential is only necessary for building packages (compiling), so you don't need that.

You need to install, configure, and automatically start xbindkeys to use the stylus buttons.  This is all in the [ubuntu 9.10 karmic guide]("http://www.unifyingtheory.net/tabletubuntu9.10.html") I made.
enjoy!

---

### Post by Avalon2050 on 2009-10-25
Oops, I have to apologize. I expected Ubuntu to save my xbindkeys settings. I added them to the start manager, but it didn't stay there. After starting it manually, it worked, though I can't seem to get the top/side buttons to work, but I'll work on that some more.

Anything new on the suspend trouble? I haven't found the right configuration yet...

Thanks again for your great guides!!

---

### Post by Rayaz on 2009-10-31
Hi,

I have successfully installed Jaunty on my TC1100 using MyR's wonderful guide. Now am planning on upgrading to Karmic. How is the suspend function working?

Regards

---

### Post by MyR on 2009-11-03
I've had a report that the xorg.conf in my [karmic guide]("http://www.unifyingtheory.net/tabletubuntu9.10.html") doesn't work and needs the InputDevice from Jaunty.  Can anyone confirm this?  I'm running jaunty.

---

### Post by FalconEyes on 2009-11-03
Initially it didn't work, the lack of a definition for InputDevice caused X to barf. After removing that line thinking the mod to the .fdi file would handle the tablet, everything works, from eraser to right-click. If you want to calibrate or control actions of your tablet, use ```
wacomcpl
```

More importantly, I can't seem to suspend my tc1100 anymore, but it worked fine in jaunty. What's up with that?

Thanks :D

---

### Post by MyR on 2009-11-03
> **FalconEyes said:**
> Initially it didn't work, the lack of a definition for InputDevice caused X to barf. After removing that line thinking the mod to the .fdi file would handle the tablet, everything works, from eraser to right-click.

So you take out this line
	InputDevice	"stylus"	"SendCoreEvents"
then X and the stylus work?
If not, please clarify.
Thanks!

---

### Post by Avalon2050 on 2009-12-06
Well I posted my input on that back in October, see post #318 for that. I explained that with your original xorg.conf, it wouldn't work for me, and after finnagling a little I found that the one I posted in #318 would work.

Anything on the suspend? I found that after the latest updates, the resume showed a screen, which is more than before, but it froze -- that's more than back when! Unfortunately, I have played so much with the settings that I don't know the original ones any more (I know, I should have made copies) -- does anyone know of a setting that will allow successful suspend/resume with the latest updates?

Greetz!

---

### Post by MyR on 2009-12-08
The only advantage that I could see for running 9.10 (karmic koala) was the on-screen keyboard at login working "out of the box".  Getting the stylus buttons to work is easier on 9.10 but they work just fine on 9.04.

Frankly I don't see any need to continue upgrading beyond 9.04 unless a future version offers 
1. dramatically decreased boot time,
2. dramatically increased battery life, or
3. a kernel supporting the card reader.

good afternoon, good evening, and goodnight.

---

### Post by DannyBiker on 2009-12-21
Hello,

I decided to upgrade to Karmic Netbook Remix and I experience major slowdowns of the netbook interface. Everything runs fine when it's hidden or uninstalled but with it, it's so slow that it becomes pointless to use it.
Does anyone know why, as the 9.04 netbook remix interface worked just fine ? Is there a way to resolve this ? If not, is there some kind of skin or program that could allow me to obtain the same look and tools (basically a large files, volumes and applications browser right on the desktop)?

Thanks...:P

---

### Post by DannyBiker on 2010-02-28
MyR, are you there ?

I'm having two problems with your Karmic guide...I did everything like you advise to but I still have one problem and a question.

1. While screen rotation works, the mouse cursor is not calibrate in the vertical position. West is South, East is North, etc. Why could I do ?

2. Where is the "Jack Sense" option you are mentioning at the end of your tutorial ? It was there in Jaunty but I can't find it in Karmic...

Thanks !

---

### Post by ashleynathomas on 2010-03-08
I have recently bought a tablet and it has Windows 7 as an OS. But the thing is I am familiar with Ubuntu as working on it from so many years and completely new to windows. So I was feeling lacking. Thanks for this help as it made my work really easy and my tablet very comfortable for me.:)

---

### Post by sloty on 2010-03-08
> **DannyBiker said:**
> MyR, are you there ?

I'm having two problems with your Karmic guide...I did everything like you advise to but I still have one problem and a question.

1. While screen rotation works, the mouse cursor is not calibrate in the vertical position. West is South, East is North, etc. Why could I do ?

2. Where is the "Jack Sense" option you are mentioning at the end of your tutorial ? It was there in Jaunty but I can't find it in Karmic...

Thanks !

1. 
Sudo apt-get install wacom-tools
This will fix the rotation of the wacom tablet

2.
Install GNOME Alsa Mixer From the software centre. There will you be able to enable the "jack sense"


I'm looking for a q-menu replacement but can find any? Can somebody help me with this?

Greetz,
Sloty

---

### Post by DannyBiker on 2010-03-08
Thanks. That solved it all ! ;)

---

### Post by MyR on 2010-03-11
> **sloty said:**
> I'm looking for a q-menu replacement but can find any? Can somebody help me with this?

Tabatha has vanished. I'd be willing to host it if someone can find it and send it to me...

I never used tabatha because it did not seem very useful; Instead I mapped the Q button to my web browser.


P.S. I am running jaunty on my tc1100 so I cannot provide support for karmic.  I will give lucid a try after its final release.

---

### Post by m_rkus on 2010-03-20
I followed the instructions on how to configure Ubuntu 9.10 on my TC1100, thank you by the way it was very helpful, but now I seem to have problems using Easystroke. Every time I try to record a stroke it does not capture the "flick" I do with the pen.

Any ideas? I am wondering if anyone like me has tried to get this program working. I know it worked using Kubuntu, but it does not seem to be as easy in Ubuntu. But I am new to the OS and am very willing to learn

---

### Post by DannyBiker on 2010-03-21
Has anyone tried gnome-shell with his hp tc1100? It's terribly slow on my device. If it's the future of Gnome, it looks like Ubuntu 10.04 will be the last release that our beloved tablet will be able to handle. Unless it gets optimized or it is just a bug...

---

### Post by Avalon2050 on 2010-04-27
> **DannyBiker said:**
> Hello,
I decided to upgrade to Karmic Netbook Remix and I experience major slowdowns of the netbook interface. Everything runs fine when it's hidden or uninstalled but with it, it's so slow that it becomes pointless to use it.
Does anyone know why, as the 9.04 netbook remix interface worked just fine ? Is there a way to resolve this ? If not, is there some kind of skin or program that could allow me to obtain the same look and tools (basically a large files, volumes and applications browser right on the desktop)?
Thanks...:PHiya Danny! I have just started looking at the netbook remix and I am impressed at the style and accessibility, but I have had the same problems with karmic. I had the normal installation and added the necessary programs via apt-get, and the ume interface was hellishly slow. No chance of using it normally. Unfortunately, shortly thereafter, I somehow destroyed the installation, seemingly with "desktop switcher", and will have to recover; but...

I put in a test hard disk and installed Lucid Lynx nbr, and it looked and ran beautifully... until I installed the nvidia graphics driver (the original via "restricted hardware driver" under Administration). Then it all looked garbled and didn't have a "bounce" in it as before. Somehow the graphics driver lessened the experience (the eye candy, if you will). Can anybody imagine why?

Maybe you can test some more as well, Danny, I'd love to get some more input to find a solution to this.


> **m_rkus said:**
> I followed the instructions on how to configure Ubuntu 9.10 on my TC1100, thank you by the way it was very helpful, but now I seem to have problems using Easystroke. Every time I try to record a stroke it does not capture the "flick" I do with the pen.

Any ideas? I am wondering if anyone like me has tried to get this program working. I know it worked using Kubuntu, but it does not seem to be as easy in Ubuntu. But I am new to the OS and am very willing to learnHiya. I think a button is missing! Easystroke wants you to press a button to make the gestures, and I put the button as the "right-click" button, so now when I record or use a gesture, I hold down the pen button and it works just fine. It doesn't hinder you to use the right-click as it only begins interacting when you begin moving the pen. Haven't had any difficulties with it. Let me know if that helped.

---

### Post by DannyBiker on 2010-04-28
I will definitely check Lucid, especially the netbook version. I'm still convinced that basic Ubuntu is not the greatest experience for our beloved TC1100. I'll give netbook remix a try when we get Lucid full support...:)

---

### Post by Avalon2050 on 2010-04-30
Okay, after fixing my Karmic installation, I removed "Desktop Switcher" and thought that the netbook remix was dead for me. I tried to find info whether you can install the Lucid netbook launcher instead of the karmic one (because it is efl-based and runs much faster than the karmic launcher), but found zilch, although I did find out that the new launcher is called "netbook-launcher-efl".

Then, in a fit of temporary insanity, I figured why not just try to add the lucid repos (main) and try to install the launcher. BINGO! Now, with an addition to the startup applications, the launcher works (and looks just GREAT!!). The best thing: compiz fusion and rotating still works (albeit in rotated screen, the launcher doesn't change, so it looks garbled; but the icons you can see still work).

Since I figured I might want to work with a normal desktop from time to time, I wrote a two-liner script that will kill the launcher and made it a Favorite, and put another script to start the launcher on the desktop. Works like a charm!

If you want to go that way, you might want to install the "window-picker-applet" which will show the active programs by icon and the title bar in maximized mode. If you want to cut off the normal title bar in maximized mode, install "maximus" (but DELETE or ## out the lucid repos before that, because you need to install the karmic variant), and if you don't like it maximizing everything, open gconf-editor and go to apps/maximus and check "no maximize". You can also use the "exclude class" to opt out single applications or sets of windows that should not be maximized).

I got rid of the "go-home-applet", which did slow everything down when used. I tried the normal "Show Desktop" for a while, but found that I don't need it, so I got rid of it and put the Gnome "Main Menu" up there, which has the same icon and will open the menus (which, incidentally, works out well since I sometimes switch to the normal desktop and still need access to the programs). I attached a desktop snapshot in case you're curious.

PS: If you want the desktop to not get in the way (which can happen when it is active, you might want to use the following line:
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false
as a standard user. This will disallow the desktop to show. If you want, you can add the opposite (true) for the script that deactivates the launcher, but I found that I don't need to deactivate the desktop, it hasn't happened yet that it got in the way. And even if it does, all you need do is kill netbook-launcher-efl and restart it.

---

### Post by DannyBiker on 2010-04-30
Avalon2050, would you marry me ?
I can't wait to test this. I'm finally getting an hard disk upgrade today and I am planning to install an Ubuntu/Win 7 dual boot (the two best OS for the device in my opinien) as soon as a Lucid tutorial is available.

Anyone tried Lucid yet ? Drastic changes in terms of optimizing the OS for the device or is it just basically the same steps than Karmic ?

---

### Post by Aearenda on 2010-04-30
I've tried Lucid on my crippled TC1100 (won't boot when hot - it's a regular visitor to the fridge at the moment!) - it mostly just works, but it works better with nvidia-96 installed, tc1100-wmi added to /etc/modules, and with the madwifi driver instead of ath5k. The side buttons and the extra buttons on the front need the usual attention, but I haven't done it.

---

### Post by Avalon2050 on 2010-04-30
> **DannyBiker said:**
> Avalon2050, would you marry me ?
I can't wait to test this. I'm finally getting an hard disk upgrade today and I am planning to install an Ubuntu/Win 7 dual boot (the two best OS for the device in my opinien) as soon as a Lucid tutorial is available.

Anyone tried Lucid yet ? Drastic changes in terms of optimizing the OS for the device or is it just basically the same steps than Karmic ?*g* Sorry, not my cup of tea ;) But I'm glad I could help the Ubuntu community for a change, as I still consider myself a newbie, I am usually looking for answers instead of giving them ;)

I installed Lucid but weren't able to get the wacom-tools running, so I figured I'd wait for a tutorial or some more info in general. I installed the nbr version of lucid, but as I posted earlier, something strange happened: WITH the 96 drivers, the icons on the launcher looked WORSE than before, and the "bouncy effect" of scrolling was gone. Couldn't find anything in the forums, so I let it slide. Now, with the lucid launcher in karmic, I am happy and completely content. I guess lucid will not come to my TC1100 in the near future even if MyR or others post a viable guide. ;)

@Aearenda: by tc1100-wmi did you mean the wacom-tools, resp. the wacom drivers? Did you try screen rotation? About cooling: did you open the case and have a look at the plating? There's a piece of metal that is supposed to transfer and dissipate the heat, maybe it is loose?

---

### Post by Aearenda on 2010-04-30
> **Avalon2050 said:**
> ...@Aearenda: by tc1100-wmi did you mean the wacom-tools, resp. the wacom drivers? Did you try screen rotation? About cooling: did you open the case and have a look at the plating? There's a piece of metal that is supposed to transfer and dissipate the heat, maybe it is loose?

Unfortunately it's not that simple to fix my TC1100. See [post 313]("http://ubuntuforums.org/showpost.php?p=8076329&postcount=313") for more details!

The pen just works in normal rotation; 'xsetwacom' is part of the wacom driver automatically loaded but doesn't work. There doesn't seem to be a separate wacom-tools package any more.

TC1100-wmi is a different thing, it enables the wireless switch in the same way as before and the ability to control screen brightness using the toggle switch as in previous versions.


UPDATE: I have found how to rotate the tablet. The name of the stylus is recognised as "Serial Wacom Tablet", so for example the stylus rotate counter-clockwise command is ```
xsetwacom set "Serial Wacom Tablet" rotate CCW
```This should be the key to sorting out the calibration and rotation scripts from earlier releases. I found it simply by using the -v option on xsetwacom, which lists all the devices it is matching the name against. xsetwacom --list is confusing because it appends text to the name, but does make sense once you know what the name is!

---

### Post by MyR on 2010-04-30
True to my word, I have tested 10.04 (actually since alpha 2)

The good news is that it boots in about 45 seconds on my tc1100 (from power switch to desktop).

If you just want the good news, you can stop reading.

Proprietary nvidia drivers can be installed as usual and work without any major problems as far as I can see.  It does give some distorted patterns on startup.
Screen rotation can be fixed by adding RandRRotation True to xorg.conf as in 9.10
I assume stylus rotation can be fixed by adding the appropriate lines to /usr/lib/X11/xorg.conf.d/10-wacom.conf and fixing the name of the stylus in the rotation script but I haven't actually tried this.
I have not been able to properly fix the stylus right click.  The button activates without the stylus tip being pressed.
I was very disappointed to see that the stylus buttons regressed and no longer work -- they probably need to be patched.  Good luck with that.
Screen brightness can be controlled as usual with tc1100-wmi & jogdial.
Doesn't resume from suspend.

9.04 is still my ubuntu release of choice for the tc1100 (because everything works) and 9.10 is the easiest to get working.

Have a great day & remember not to beat your head on the wall. ;] Linux should make life better.

---

### Post by Aearenda on 2010-05-01
More info from my experiments:  
I didn't need to fiddle with /usr/lib/X11/xorg.conf.d/10-wacom.conf at all to get stylus rotation to work. 
I didn't try the right-click button earlier - on mine it doesn't work at all, yet! Update: Yes it does, just as MyR described.
Suspend works for me (ath_pci has to be told to unload, ath5k works out of the box).
The screen distortion at bootup seems to be fixed by adding 'GRUB_GFXMODE=1024x768' to /etc/default/grub.

More: You can use the 'assistive technology' settings for 'mouse accessibility' to turn on simulated right click, which means the stylus button isn't needed - you just hold the stylus on an object for a delay period, then release, and the right-click menu will appear in a controllable fashion.

And more: Adding this line to /usr/lib/X11/xorg.conf.d/10-wacom.conf, below the line that says 'Option "ForceDevice" "ISDV4" ', seems to fix the right-button problem:
```
Option "TPCButton" "on"
```I rebooted to be sure this was seen. It may be sufficient to log out and in.

Note: The panels seem to go missing sometimes with this setting on. 'killall gnome-panel' puts them back.

---

### Post by Avalon2050 on 2010-05-01
Wow, this is interesting. I had seen this behaviour of the right button with my brief test of Lucid RC, and I was also saddened by the apparent regression of functionality, but after reading that you can turn on right-click by depressing the pen for a longer time, I figured: maybe we don't have to see it as a regression; after all, if means you can now turn the screen without mouse or keyboard, just by pointing, and you still got a right-click! That opens up many new possibilities in using the TC1100 in tablet mode; you can switch desktops without needing the desktop-switcher-applet, and WITH eye candy ;)

Anyway, great work finding out all these settings, I will give them a try tomorrow with my trusty 20 Gig testing HD and see if I can get it to work as you described.

Has anyone tried to install/start the netbook-launcher-efl from the normal Lucid desktop? I'm just anxious to find out whether the buttons still look garbled as they did with the Lucid nbr when I installed the nVidia driver... but I'll find that out tomorrow as well ;)

---

### Post by yeppp on 2010-05-01
Hey guys.  I have been using a hp tc1100 for about 4 months now.  I originally followed MyR's 9.10 guide and upgraded to 10.04 yesterday.  I can confirm that the command Aearenda found does rotate the stylus.  When I added that to the rotation script by replacing the lines that dealt with the stylus rotation I get 

```
#!/bin/sh
if [ -n "$(xrandr | grep 768x1024)" ]; then
        xrandr -o normal
        xsetwacom set "Serial Wacom Tablet" rotate none
else
        xrandr -o left
        xsetwacom set "Serial Wacom Tablet" rotate CCW
fi
```which seems to do the trick.

I am still having trouble with the stylus buttons up top.  If I remember correctly those were enabled through wacom-tools, which is no longer supported.  That means that my xbindkeys configuration isn't working.  Any thoughts on how to get those working again?

---

### Post by MyR on 2010-05-01
> **Aearenda said:**
> Suspend works for me (ath_pci has to be told to unload, ath5k works out of the box).
I don't have an ath_pci module loaded ('lsmod | grep ath' returns nothing). Help please?
> **Aearenda said:**
> The screen distortion at bootup seems to be fixed by adding 'GRUB_GFXMODE=1024x768' to /etc/default/grub.
I still experience the screen distortion with the 96 drivers loaded after adding this.
> **Aearenda said:**
> More: You can use the 'assistive technology' settings for 'mouse accessibility' to turn on simulated right click, which means the stylus button isn't needed - you just hold the stylus on an object for a delay period, then release, and the right-click menu will appear in a controllable fashion.
I suppose this can be useful if people (like Avalon2050) want both middle and right click functionality from the stylus.
> **Aearenda said:**
> And more: Adding this line to /usr/lib/X11/xorg.conf.d/10-wacom.conf, below the line that says 'Option "ForceDevice" "ISDV4" ', seems to fix the right-button problem:
```
Option "TPCButton" "on"
```I rebooted to be sure this was seen. It may be sufficient to log out and in.
FANTASTIC!  I figured this setting wouldn't help because I noticed TPCButton is turned on by default in xsetwacom, so I don't know why it works but it does!
> **Aearenda said:**
> Note: The panels seem to go missing sometimes with this setting on. 'killall gnome-panel' puts them back.
My panel (only have one) hasn't disappeared yet.

------------------------

> **yeppp said:**
> I am still having trouble with the stylus buttons up top.  If I remember correctly those were enabled through wacom-tools, which is no longer supported.  That means that my xbindkeys configuration isn't working.  Any thoughts on how to get those working again?
wacom-tools was never used for the buttons; it's all controlled by xbindkeys.
The button codes changed in 10.04.  The new ones are 156 and 157.

------------------------

I don't know how to go about patching the driver to get the stylus buttons working since there is no longer a wacom-tools.  Perhaps there's a way to do it without patching.  Please help if you can.

---

### Post by Aearenda on 2010-05-02
> **MyR said:**
> I don't have an ath_pci module loaded ('lsmod | grep ath' returns nothing). Help please?
ath_pci is part of the madwifi driver and would not be present if you are using ath5k (as you will be unless you have deliberately added madwifi).

---

### Post by Avalon2050 on 2010-05-02
Alright, I gave it the old college try. Installation, Updates, graph driver installation all works great.

- Rotation works with the script yeppp posted (thanks yeppp)!

- Top buttons work (thanks, MyR, for providing the new button codes; strangely enough, these codes are already in place in my Karmic installation; I put them in, and now I can finally use the top buttons in karmic again)

- I installed netbook-launcher-efl, and it works just as well as on karmic, looks beautiful. As in karmic, you can switch it on and off with one line of code.


Now the caveats:

- After the graph driver is installed, I experience the same distortions during startup as MyR mentioned, and I have tried every setting in /etc/default/grub. By comparison, in Karmic I can set screen resolution to anything and it looks good, even with color depth at 24

- Adding Option "TPCButton" "on" did not work for me. The only thing that happened was that depressing the pen button did not make the cube rotate BEFORE it touched the display (screen still rotated, but only after I touched the display with the pen, as with karmic before patching) -- do I have to specify that the pen button is supposed to be button 3 somewhere?

- Can confirm that the tablet buttons do not work, as was expected.

- Since it worked well before, I just figured I'd give it a try: I threw in the karmic repos and installed the old wacom-tools from them. That did NOT work; the pen didn't work at all after that, so I removed them and reinstalled the newer drivers



Aearenda: Since I don't exactly know what those drivers are and how they interact/work, I am not quite sure what you meant when you talked about ath_pci and madwifi in your last few posts; if my deductive skills still work, you meant:

- After install, ath5k is used, and with that, suspend does NOT work.

- We have to kill ath5k and load madwifi, then unload the part of madwifi that is called ath_pci, and then suspend will work.

Please correct me if I am wrong, and I would apprecieate a little step-by-step on how to do that (unload/kill ath5k and load madwifi, then unload ath_pci. Thanks a lot!

---

### Post by DannyBiker on 2010-05-02
I wish I could help you out guys but I'm useless when it comes to command lines.
I'm reading every post 'though and look forward for fixes and workarounds hopefully !

Thanks...

---

### Post by MyR on 2010-05-02
> **Avalon2050 said:**
> do I have to specify that the pen button is supposed to be button 3 somewhere?
yes, Option "Button2" "3"
right under where you put the other option.

> **Avalon2050 said:**
> - Since it worked well before, I just figured I'd give it a try: I threw in the karmic repos and installed the old wacom-tools from them. That did NOT work; the pen didn't work at all after that, so I removed them and reinstalled the newer drivers
wacom-tools was replaced by xserver-xorg-input-wacom and has the same file that needs to be patched. So it certainly *can* work, but I don't know how to make a patch for it.  I suppose I could edit the file myself and then compile it, but I filed a bug report instead.  [https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/573275](https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/573275)

My tc1100 has intel pro wireless 2200 (IPW2200), so my suspend issue will require a different fix.

I have a pretty workable installation besides the suspend issue.

---

### Post by Avalon2050 on 2010-05-02
> **MyR said:**
> yes, Option "Button2" "3"
right under where you put the other option.Right, shoulda seen that coming. Thanks!


> **MyR said:**
> wacom-tools was replaced by xserver-xorg-input-wacom and has the same file that needs to be patched. So it certainly *can* work, but I don't know how to make a patch for it.  I suppose I could edit the file myself and then compile it, but I filed a bug report instead.Well I have even less knowledge of that, so I'll follow that report! Thanks for the clarification.

> **MyR said:**
> My tc1100 has intel pro wireless 2200 (IPW2200), so my suspend issue will require a different fix.Yeah, got the same card. Couldn't the madwifi work with that one as well? As I understand it, the drivers provided in Ubuntu have a pretty wide range of hardware they can suit...

---

### Post by Aearenda on 2010-05-02
> **Avalon2050 said:**
> - After the graph driver is installed, I experience the same distortions during startup as MyR mentioned, and I have tried every setting in /etc/default/grub. By comparison, in Karmic I can set screen resolution to anything and it looks good, even with color depth at 24It's odd that I don't see this. However, it's certainly not as smooth as it was before adding the Nvidia driver. There's [another way to fix this]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/"), but I gather it makes the boot process slower. I haven't tried it.


> **Avalon2050 said:**
> 
Aearenda: Since I don't exactly know what those drivers are and how they interact/work, I am not quite sure what you meant when you talked about ath_pci and madwifi in your last few posts; if my deductive skills still work, you meant:

- After install, ath5k is used, and with that, suspend does NOT work.

- We have to kill ath5k and load madwifi, then unload the part of madwifi that is called ath_pci, and then suspend will work.

Please correct me if I am wrong, and I would apprecieate a little step-by-step on how to do that (unload/kill ath5k and load madwifi, then unload ath_pci. Thanks a lot!
I'm afraid I have assumed everybody knows this thread right from the beginning! Hopefully this will make things clearer:

- My TC1100 has an Atheros wifi card. If you have the Intel wifi, like MyR, then none of this applies to you. Madwifi only works with Atheros cards!
- ath_pci is part of the madwifi driver.
- Suspend WILL work for me with ath5k, which is installed as standard in Lucid. However, ath5k is problematic for me - it causes mouse jerkiness, and drops connections.
- If you choose to replace ath5k with madwifi, which works better for me, then you need to tell Ubuntu to unload ath_pci just before suspending, and reload it after waking; otherwise, wireless will be not working after putting the tc1100 to sleep.

Instructions for installing the madwifi driver [are in another thread]("http://ubuntuforums.org/showthread.php?t=1163380").

---

### Post by Avalon2050 on 2010-05-02
Okay, since I do have the Intel 2100B wireless driver I won't be able to use that info, but thanks a lot for the clarification!

...and for the link. I tried and dabbled a bit and finally found out that all you have to do to get the distorted startup going was commenting out one line and adding another; here is my version of /etc/default/grub, which works with normal quality and without distortion:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
#GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=7
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
#GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=800x600
GRUB_GFXPAYLOAD_LINUX=1024x768

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_LINUX_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```Of course you can change the GRUB_GFXMODE to 1024x768 if you prefer, I do like the grub loader in 800x600, that's why I did it. The next line seems to be important though, which determines the size of the splash screen; if you make grub appear in 1024x768, that line can also read "GRUB_GFXPAYLOAD_LINUX=keep

And do comment out the "GRUB_CMDLINE_LINUX=" ", even if there is something in there.

Hope that helps

---

### Post by yeppp on 2010-05-06
I hoped on board following that bug for the xserver-xorg-input-wacom that needs to be patched for us in hopes that the more of us showing the problem, the quicker there might be a solution.  Also, after rotation and then resuming from suspend, my stylus calibration is off.  MyR provided a script to fix this in 9.10, but it seems that that script isn't working now.  Any ideas on how to fix the calibration after suspending?

---

### Post by yeppp on 2010-05-06
I hoped on board following that bug for the xserver-xorg-input-wacom  that needs to be patched for us in hopes that the more of us showing the  problem, the quicker there might be a solution.  Also, after rotation  and then resuming from suspend, my stylus calibration is off.  MyR  provided a script to fix this in 9.10, but it seems that that script  isn't working now.  Any ideas on how to fix the calibration after  suspending?

---

### Post by DannyBiker on 2010-05-07
Yep, I subscribed too, hoping that a fix will be available in the following weeks...

So, if I understand correctly, what doesn't work is :
- Right-Click
- Screen Rotation
- Tablet Buttons
- Resuming from suspend

I could live without the last two but right-click and Screen rotation is a must-have...

BTW, I'm also experimenting ugly graphics with NetBook Remix with Nvidia drivers active. Works like a charm without it. Weird. I could open a bug report for that aswell...


Finally, I have been reading recently that Gnome 3.0 will not be ready for a while which is a great thing as it means that we will be able to upgrade to 10.10 and more; that is if things don't get worse in terms of support for the device.
Gnome Shell is really sluggish on a TC1100. Come to think of it, it is as slow as Netbook Remix was in 9.10 and as is Docky now. A graphic card issue maybe ? Too old ?

---

### Post by Avalon2050 on 2010-05-07
> **DannyBiker said:**
> BTW, I'm also experimenting ugly graphics with NetBook Remix with Nvidia drivers active. Works like a charm without it. Weird. I could open a bug report for that aswell...Yep, same here. Strangely enough though, when you install the standard (Desktop) version of 10.04  and then activate netbook-launcher-efl, it looks just as it should! I commented on that in an earlier post, though not in detail. If you prefer nbr, then install the standard version, do the update and install the nvidia driver, and once you're done, install the following:
sudo apt-get install netbook-launcher-efl maximus window-picker-applet go-home-applet
Then delete the bottom panel, add the window picker and the go-home-applet to the top panel and start netbook-launcher-efl (and add it to startup). If you don't want to switch between normal screen and netbook-launcher, you might want to deactivate the desktop so that the launcher will always be selected when windows are closed; it's a minor detail, but I guess some would prefer it that way:
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false


> **DannyBiker said:**
> Finally, I have been reading recently that Gnome 3.0 will not be ready for a while which is a great thing as it means that we will be able to upgrade to 10.10 and more; that is if things don't get worse in terms of support for the device.
Gnome Shell is really sluggish on a TC1100. Come to think of it, it is as slow as Netbook Remix was in 9.10 and as is Docky now. A graphic card issue maybe ? Too old ?I'm not quite sure what you mean... I haven't had ANY response/speed issues with ubuntu on the TC1100. The nvidia drivers do work fine, and everything is absolutely snappy, even with compiz fusion and the cube -- and I usually lock down the processor on 600 MHz! Where and when have you had issues, and after installing what kind of software?

---

### Post by DannyBiker on 2010-05-07
Thanks for the nbr tips !

About Gnome, I was talking about Gnome-Shell, the Gnome 3.0 preview that can downloaded from Synaptic. It's terribly slow on my device.
Docky, the hot dock of the moment is also terribly sluggish...

It can't be my Ubuntu installation, I installed it yesterday...

---

### Post by Avalon2050 on 2010-05-07
No problem! :)

Ah, I see. Well I haven't tried Docky, but I have two theories that could account for lack of "snappiness":

1) Docky is still in testing and development, so it stands to reason that it is going to be applicable more widely once all issues are ironed out, and

2) I had a similar problem with cairo-dock when I ran it on opengl -- maybe there's a switch on docky to make it work without opengl

If that doesn't work, have a look at Cairo-Dock. It is quite similar to the Mac dock, and can be customized to look and feel exactly like it, or can be made something completely new. It just entered 2.0 and works great on the TC1100. I had it on for some time, but I prefer the nbr look. Make sure to start it with the -c option (cairo-dock -c) to make it start without opengl support. As I said, that made it run very slow on my machine, but running it on machine power it works like a charm.

To get it, add the repository to your sources:
deb [http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu) karmic cairo-dock
and install the package: sudo apt-get install cairo-dock

As for gnome 3.0, I can't comment as I haven't tried it yet.

---

### Post by Aearenda on 2010-05-07
> **DannyBiker said:**
> ...

So, if I understand correctly, what doesn't work is :
- Right-Click
- Screen Rotation
- Tablet Buttons
- Resuming from suspend



Here's how it is for me:
- Right-click can be made to work, even if only by using the accessibility features to make a long click into a right click. I find this easier than using the silly button, which I can never find without looking at the pen!
- Screen rotation works for me with both the standard video driver and the nvidia proprietary driver. Wacom rotation still needs the scripts, and the device name has changed to "Serial Wacom Tablet" so the existing scripts need modification, as in [yeppp's post]("http://ubuntuforums.org/showpost.php?p=9210875&postcount=349") 6 days ago.
- Tablet buttons - needs work, keycodes have changed.
- Resuming from suspend - works for with the standard screen and wireless drivers. When using madwifi for wireless and the nvidia proprietary driver, the same workarounds as on previous releases are needed.

---

### Post by DannyBiker on 2010-05-08
Sorry but Ubuntu 10.04 is one big mess.
I'm forced to reboot the TC1100 manually every hour. After a while, the OS just stops responding ! I don't know what it is, I barely installed anything yet !

Installing 10.04 on my desktop computer was also a painful experience with terrible graphics and impossibility to detect any USB device...

It's just getting worse every 6 months.


EDIT : here I am again, forced to shut down manually my tc1100 after the OS stoping to answer after...1 minute ! Every time I try to access a program that asks the administrator password, the system freezes. Don't ask me to reinstall, I already did !

---

### Post by DannyBiker on 2010-05-08
> **Avalon2050 said:**
> Yep, same here. Strangely enough though, when you install the standard (Desktop) version of 10.04  and then activate netbook-launcher-efl, it looks just as it should! I commented on that in an earlier post, though not in detail. If you prefer nbr, then install the standard version, do the update and install the nvidia driver, and once you're done, install the following:
sudo apt-get install netbook-launcher-efl maximus window-picker-applet go-home-applet
Then delete the bottom panel, add the window picker and the go-home-applet to the top panel and start netbook-launcher-efl (and add it to startup). If you don't want to switch between normal screen and netbook-launcher, you might want to deactivate the desktop so that the launcher will always be selected when windows are closed; it's a minor detail, but I guess some would prefer it that way:
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop false

Doesn't work for me, it's still ugly...

---

### Post by Aearenda on 2010-05-08
> **DannyBiker said:**
> Sorry but Ubuntu 10.04 is one big mess.
I'm forced to reboot the TC1100 manually every hour. After a while, the OS just stops responding ! I don't know what it is, I barely installed anything yet !

Installing 10.04 on my desktop computer was also a painful experience with terrible graphics and impossibility to detect any USB device...

It's just getting worse every 6 months.


EDIT : here I am again, forced to shut down manually my tc1100 after the OS stoping to answer after...1 minute ! Every time I try to access a program that asks the administrator password, the system freezes. Don't ask me to reinstall, I already did !

It may be one big mess for you - but I leave all my computers on all day without any difficulty, including two desktops, two TC1100s and a TC1000 that acts as my music player, and Lucid has been absolutely the best release ever for me. It seems to depend on the state of your hardware.

---

### Post by DannyBiker on 2010-05-09
The new Netbook remix interface for 10.10 has been announced :

[IMG]http://static.arstechnica.com/assets/2010/05/shell-desktop-1-thumb-640xauto-13892.png[/IMG]

It is netbook oriented of course and could be a good fit for the tc1100. I'm looking forward to any improvements of the menu bar; it is just a nightmare in 10.04, where half of it is dedicated to the notification areas. Talk about wasted space !


It is possible to test the interface (still in early development for the moment):

    * ppa:canonical-dx-team/une
    * apt-get unity
    * Choose the Unity session at GDM login.


EDIT : alright don't install it; it doesn't work right now. I get a white screen and that's it.

---

### Post by DannyBiker on 2010-05-12
Hello,

am I the only one experiencing major freezes when it comes to downloading anything from the repos ? It doesn't matter what program I use to access them, it gets stuck and it is impossible to cancel the action. I'm stuck with an open repos access and I'm forced to restart the tc1100 to be able to download from the repos again. Quitting the session only doesn't work...:(

---

### Post by MyR on 2010-05-12
> **DannyBiker said:**
> Hello,

am I the only one experiencing major freezes when it comes to downloading anything from the repos ? It doesn't matter what program I use to access them, it gets stuck and it is impossible to cancel the action. I'm stuck with an open repos access and I'm forced to restart the tc1100 to be able to download from the repos again. Quitting the session only doesn't work...:(

Sounds like an ubuntu problem, not an "ubuntu on the tc1100" problem.

You could try using the terminal to install packages.  it may help determine what your issue is.

```
sudo aptitude install *packagename*
sudo aptitude remove *packagename*
```

---

### Post by DannyBiker on 2010-05-12
Yeah but I've had the same problem in every Lucid install I did. The same thing occurs in the latest MINT RC...

Also, the right-click simulation obtained through the Mouse setting doesn't work half the time. Some sessions it does, some others it doesn't...:confused:

---

### Post by altongary on 2010-05-12
Danny Boy:
This is going seem like it's coming out of left field, but what's your partitioning scheme? My TC1100 acted the same way with 9.04; it would lock up instead of hibernating or suspending to ram, or I'd have weird graphics and phantom slowdowns. I read somewhere that ext4 -- the default file system -- doesn't play well with suspend to ram or hibernation on systems with ide hard drives like the tc1100. When installing, I manually changed the partition scheme to separate my root [(/) formatted as ext4] and home [(/home) formatted as ext3] partitions and added a healthy swap area [at least 2.5 x your ram]. 
I'm running 10.04 with netbook remix (don't use the unr iso) and full eye candy enabled, and it runs fine (apart from the side button issues, but that's my fault for not waiting the requisite 30 days after a new release).

---

### Post by DannyBiker on 2010-05-13
Well, this how it looks like :
- 30 go of ext4 /
- 2 go of swap
- 50 go of ext4 /home
- windows 7

I never uses the suspend or hibernating mode.
The only difference from previous installations that I can think of is HDD upgrade I did recently. But I tried 9.10 since then and it worked perfectly so I doubt it is HDD related...
I'll give ext3 a try on my next installation. 

Thanks ! ;-)

---

### Post by Avalon2050 on 2010-05-13
> **DannyBiker said:**
> [...] The only difference from previous installations that I can think of is HDD upgrade I did recently. But I tried 9.10 since then and it worked perfectly so I doubt it is HDD related...
I'll give ext3 a try on my next installation.Just to be sure, put in the smaller HD and install Lucid again. As it seems, you are the only one with this particular problem in this thread, so it is not specifically TC1100-related; it could be the HD or the way you install Lucid...

I want to emphasize my suggestion from before (the same altongary gave you): do NOT install the NBR, but rather the normal live CD iso, either from CD or from a stick. And as a suggestion, wait a little before you install the nbr stuff; open up the other sources, update, install your other favorite software, enable the graphics and compiz fusion, and see what happens.

I agree that you might want to install from a terminal window. Just open one and install the packages with "sudo apt-get install" after that, you just have to type the name of the program, i.e.
sudo apt-get install acroread
or sudo apt-get install neverball
If something doesn't work right, the terminal will show what went wrong.
If it all works without the nbr stuff, then install it
sudo apt-get install netbook-launcher-efl maximus window-picker-applet
do not install go-home-applet, it seems to make everything slow down, at least after clicking on it.
Good luck

---

### Post by DannyBiker on 2010-05-13
Well, it took me days to finally be able to upgrade the HDD (the screws of the metallic protection around it were a pain to take off), so there is no way I'm going to put the old HDD back...:)

I always use the Desktop edition of Ubuntu, so it's not NBR related.

I'm using the terminal aswell but yesterday for example, I had to reboot manually after trying to activate the server synchronisation of the system clock. A window appeared but didn't show anything.

Oh well, I'll see how things evolve in the days to come then stick to 9.10 if I'm not satisfied...:(

---

### Post by Avalon2050 on 2010-05-13
Did you ever have any speed-related trouble with 9.10?

PS: When I test something new, I don't use the casing for the HDD, I simply plug in a "naked" HDD. If you treat the TC1100 carefully and put the lid back on, it is safe. And the test would be important in order to find out whether it is HD-related. Anyway, just a suggestion.

---

### Post by DannyBiker on 2010-05-13
I never got any speed problem with 9.10. I stress that 9.10 runs perfectly fine on the same HDD.

---

### Post by slef on 2010-05-14
Hi all,
10.04 is working great for me, thanks to all the info here.
I also got the right click to work thanks to a hint from my friend Seb:

xsetwacom set "Serial Wacom Tablet" button2 3
xsetwacom set "Serial Wacom Tablet" tpcbutton off

however, the setting is lost when waking up from suspend and I have to run the commands again. I haven't managed to get my script in sleep.d to do this automatically. Let me know if any of you figure it out.
the only thing missing after that are the stylus buttons.

---

### Post by MyR on 2010-05-15
Did you guys have to do something special to make suspend work or did it work out of the box?  Could someone post his xorg.conf?
I just get a black screen when I try to resume and have to manually power down.

If I can't get this working without reinstalling, I'll be switching to another distro.

---

### Post by Avalon2050 on 2010-05-15
Seconded. I am still having trouble with suspend as well. I do remember I had the same trouble when I first upgraded to Karmic. I googled, scoured the forums and found some promising settings, but it didn't fix it permanently. All I was able to get was a "hopeful wake-up", meaning half the time it worked, the other half it didn't.

Then, suddenly, after a few updates (a few weeks later) it suddenly just worked. Now I don't know if my settings had anything to do with it, but it makes me hope that it might work with Lucid someday. But until then, I'll stick with Karmic.

---

### Post by slef on 2010-05-15
Here is my xorg.conf:

```
Section "Screen"
        Identifier      "Default Screen"
        DefaultDepth    24
        Option  "AddARGBGLXVisuals"     "True"
EndSection

Section "Module"
        Load    "glx"
EndSection

Section "Device"
        Identifier      "Default Device"
        Driver  "nvidia"
        Option  "NoLogo"        "True"
        Option  "RandRRotation" "True"
        Option  "NvAGP"         "1"
        Option  "RenderAccel"   "False"
EndSection
```

I just installed, updated, installed nvidia driver, and modified xorg.conf as above. Reboot and suspend works.

I then just added the rotate script and the fix for right click I mentioned above. The top buttons and scrollwheel  work out of the box. I got it to fix the right click when waking up from sleep (just added --display :0.0 in the xsetwacom command).
Stylus buttons still don't work.

I hope this helps.

---

### Post by Avalon2050 on 2010-05-15
> **slef said:**
> [...] Reboot and suspend works. [...]Hi! Do you have a 2100 3B Mini PCi Adapter? (lshw)

---

### Post by MyR on 2010-05-15
> **slef said:**
> Here is my xorg.conf:
....
I just installed, updated, installed nvidia driver, and modified xorg.conf as above. Reboot and suspend works.
....
I hope this helps.

Thanks, this worked.  It must be the NvAGP setting that fixes suspend.  In a previous version I had added the RenderAccel setting to fix an issue with compiz not displaying text properly.

I will be posting a full guide by Wednesday.  Slef I believe the fix you need was already posted in this thread maybe 30-50 posts back, but it will be in my guide for sure.

Is anyone still experiencing the loss of stylus calibration?  I cannot reproduce this anymore.

---

### Post by DannyBiker on 2010-05-15
Great news ! Thanks !:)

---

### Post by Avalon2050 on 2010-05-16
By the way, two suggestions that are not distro-specific:

One: if you want the onscreen keyboard to launch only one instance when you press the appropriate pen key, then wmctrl will help you there. I have found a few situations in which the onboard keyboard was already started but not on top, and in those moments I clicked the button again and when I closed down the clutter, I found I had two or three instances of onboard running. So here's what you do:

sudo apt-get install wmctrl

copy and paste the following code into a file called "onboard-smartlaunch" or whatever strikes your fancy):

```
#! /bin/bash

WINTITLE="onboard" # Onboard's window name
PROGNAME="onboard" # This is the name of the binary for onboard

# Use wmctrl to list all windows, count how many contain WINTITLE,
# and test if that count is non-zero:

if [ `wmctrl -l | grep -c "$WINTITLE"` != 0 ] 
then
wmctrl -a "$WINTITLE" # If it exists, bring onboard to front
else
$PROGNAME & # Otherwise, just launch onboard
fi
exit 0

# (Script courtesy of "mannheim" from the ubuntu forums)
```
make it executable and move it to usr/bin:
chmod +x onboard-smartlaunch
mv onboard-smartlaunch /usr/bin/onboard-smartlaunch

And change the button #31 in the .xbindkeysrc to onboard-smartlaunch; done (remember to restart X after changing the button).

I usually use onboard for short commands and only fire up cellwriter for more complex writing; if you want to use the script with cellwriter, change WINTITLE to "CellWriter" (mind the capitals) and the PROGNAME to "cellwriter"; with wmctrl -l you can check the active windows and their titles at any given time. That tool is quite useful for a load of things, not just this.


Second: if you want to use the jog/dial for both brightness and for thumbing through pages, here is a little script from LQWiki I used:

```
#!/usr/bin/env bash

if [[ ! -f /sys/devices/platform/tc1100-wmi/jogdial ]]; then
	zenity --info --text="This kernel does not have TC1100 WMI support."
	exit 1
fi

echo 0 > /sys/devices/platform/tc1100-wmi/jogdial
zenity --info --text="Use the jog/dial to adjust the brightness. Press OK when done."
echo 1 > /sys/devices/platform/tc1100-wmi/jogdial

exit 0

# (Script courtesy of LQWiki: http://wiki.linuxquestions.org/wiki/TC1100)
```
I put it on one of the top buttons. When you press the button, the brightness control is activated, you can use the jog control to adjust, and when you depress the jog button, it ends brightness control, and the jog/dial issues PGUP and PGDN commands again.

I hope you can get some mileage out of these suggestions, they have helped me enjoy the TC1100 Ubuntu experience even more! ;)

---

### Post by yeppp on 2010-05-16
MyR,
I am still having trouble with the calibration after suspend, but I am also having trouble in general after resuming from suspend.  Performance crawls to a stop for me along with the calibration problem.  Since you aren't experiencing those issues,  maybe the two problems for me are related.  What could be the difference between our tc1100s that would cause this?

---

### Post by MyR on 2010-05-17
> **Avalon2050 said:**
> ....
And change the button #31 in the .xbindkeysrc to onboard-smartlaunch; done (remember to restart X after changing the button).
Just to be clear, afaik cellwriter itself checks to make sure there are no other instances before running, so this script isn't needed for cellwriter.  Also, the stylus buttons are not yet working in ubuntu 10.04.

> **yeppp said:**
> MyR,
I am still having trouble with the calibration after suspend, but I am also having trouble in general after resuming from suspend.  Performance crawls to a stop for me along with the calibration problem.  Since you aren't experiencing those issues,  maybe the two problems for me are related.  What could be the difference between our tc1100s that would cause this?
Don't have the slightest idea; possibilities are endless.  Top or system-monitor should show you what's eating your processor though.

FYI: if the system freezes, ctrl+alt+F2 opens a terminal. login, then type "top". you will see the processes sorted by % of processor use.  "q" will exit top and you can proceed to kill the naughty process with killall or kill -9 or whatever is your weapon of choice. "exit" logs you out of the terminal and ctrl+alt+F7 returns you to x.
If you cannot open a virtual terminal with ctrl+alt+F2, then you're all out of tricks.

Until next time...

---

### Post by Avalon2050 on 2010-05-17
> **MyR said:**
> Just to be clear, afaik cellwriter itself checks to make sure there are no other instances before running, so this script isn't needed for cellwriter.I didn't know that, thanks for the catch.

---

### Post by DannyBiker on 2010-05-18
I think I'm sticking with Linux Mint 9 for the moment. On such a small screen, Ubuntu 10.04 panels are a waste of space. And Netbook Remix is not optimal either.

However, 10.10 Netbook Edition could rock on the TC1100.:)

---

### Post by MyR on 2010-05-20
OK here it is:  [Ubuntu 10.04 Lucid lynx on HP TC1100 tablet]("http://www.unifyingtheory.net/ubuntu10.04tc1100.html")

I've been trying for hours to install joomla on my new site without success, so it's the same old layout.

Let me know if I messed anything up.  Enjoy.

---

### Post by DannyBiker on 2010-05-20
Thanks !
I'll look into that later today...
Hope the stylus button will be fixed ! :)

---

### Post by yeppp on 2010-05-22
Thanks for the guide and pulling all of that information into one location MyR!  Putting all of htat information in one location has been a huge help and has gotten many a person like myself going on their hp tc1100 without hardly any pain.  Thanks!

Unfortunately, I still have a few problems that I can't seem to diagnose.  Suspend is still giving me fits.  The computer will suspend and resume fine, or so it appears, but after a couple of minutes everything locks up.  Also with suspend, if I suspend after rotating upon resuming the calibration is off.  Below is a list of things that didn't work for me or I did a little different.  Hopefully someone can help me out with the problem and the things below will help.

Not using xbindkeys.  The system registers the side buttons, so I just made a keyboard shortcut for the q button, ect. that goes to the command I want. (ex: q button links to the brightness script)

Using MryR's guide wacomcpl is not available and can not be downloaded or installed.

The command to not lock the screen on suspend didn't work.  I don't know about hibernate as I haven't attempted it yet.


I am not sure where to go from here.  These are things that seem minor to me and wouldn't be affect suspend.  Any thoughts?

---

### Post by MyR on 2010-05-22
> **yeppp said:**
> Unfortunately, I still have a few problems that I can't seem to diagnose.  Suspend is still giving me fits.  The computer will suspend and resume fine, or so it appears, but after a couple of minutes everything locks up.  Also with suspend, if I suspend after rotating upon resuming the calibration is off.  Below is a list of things that didn't work for me or I did a little different.  Hopefully someone can help me out with the problem and the things below will help.

Not using xbindkeys.  The system registers the side buttons, so I just made a keyboard shortcut for the q button, ect. that goes to the command I want. (ex: q button links to the brightness script)

Using MyR's guide wacomcpl is not available and can not be downloaded or installed.

The command to not lock the screen on suspend didn't work.  I don't know about hibernate as I haven't attempted it yet.

I did a clean install using the full disk guided. I removed "check for new hardware drivers", "evolution alarm notifier", "gnome login sound", "personal file sharing", "remote desktop", "ubuntu one", "update notifier", and "visual assistance" from the startup applications.  I also installed opera, rearranged the panels, and changed the desktop background. That's all I did besides what's in my guide.

EDIT: All right, after I suspended in portrait mode, the calibration was messed up.  I could write a script for it but it'll be broken in 5 months.... Why should I spend more time fixing the tablet than using it?  So for now, don't suspend in portrait mode ;]

Don't use the panel applet for suspending. Slide the power button and choose suspend from that menu instead.

---

### Post by david_katona on 2010-06-22
Hi! I have some problem with my Ubuntu + TC1100 + bluetooth mouse combo described in [**_this topic_**.]("http://ubuntuforums.org/showthread.php?t=1510347") 

Does anyone has or had this problem or just can help me?

Thank you!

David

---

### Post by brotherlouie on 2010-07-30
ok, got ubuntu 10.04 on my tc1100
ran the update manager
downloaded the driver for the video card.
rebooted
then it gets stuck at ubuntu screen with red dots at the bottom.
what did i do wrong? or what did i forget to do?
please help!

---

### Post by ov10fac on 2010-07-30
I have installed Ubuntu 10.4 on my TC1100.  I have everything working great except the stylus/cursor.  When I rotate CCW the stylus and mouse seems to be 90 degrees out of phase with the screen.

I have seen something on this in the past but can't find it now.  Anyone have a fix for this?

Many thanks.

---

### Post by MyR on 2010-07-30
> **brotherlouie said:**
> ok, got ubuntu 10.04 on my tc1100
ran the update manager
downloaded the driver for the video card.
rebooted
then it gets stuck at ubuntu screen with red dots at the bottom.
what did i do wrong? or what did i forget to do?

I am not sure why you are experiencing difficulty.

If you can go into grub's boot menu and select a command line to boot to, you can run dpkg-reconfigure xserver-xorg
Otherwise, you can boot from a livecd or usb and go in and delete /etc/X11/xorg.conf from your hard drive
That ought to take care of your problem with not being able to boot. Then you can try to start over; you might have better luck the next time.

> **ov10fac said:**
> I have installed Ubuntu 10.4 on my TC1100.  I have everything working great except the stylus/cursor.  When I rotate CCW the stylus and mouse seems to be 90 degrees out of phase with the screen.

I have seen something on this in the past but can't find it now.  Anyone have a fix for this?

following the steps in [my guide]("http://www.unifyingtheory.net/ubuntu10.04tc1100.html") should be all that is needed.

Have a great day!

---

### Post by jeob on 2010-08-28
Hi,

First thank you for the guide/howto. 

I have follow the guide and now i have an ubuntu 10.04 on my tc1100 :).

Everything works except the left screen wacom button(for rotate, journal, and virtual keyboard). In fact no keycode return by the system when i clic on it(no b:30 b:31 b:32).

I used xev to see the return keycode but nothing happen when i clic on these buttons.

Have you got any idea ?

edit : just for information in your  guide you talk about wacomcpl package but i didn't find it in the 10.04 release.

---

### Post by MyR on 2010-08-29
> **jeob said:**
> First thank you for the guide/howto.
Welcome!

> **jeob said:**
> Everything works except the left screen wacom button(for rotate, journal, and virtual keyboard). In fact no keycode return by the system when i clic on it(no b:30 b:31 b:32).
The buttons require a patch in the ubuntu 10.04 release.  I don't have enough time to figure out to make a new patch; I hope someone else does.

> **jeob said:**
> just for information in your  guide you talk about wacomcpl package but i didn't find it in the 10.04 release.
I'll take that out. I don't remember what it was for anyway.

---

### Post by watchoutman on 2010-09-08
I'd also like to thank MyR for providing a very easy-to-follow guide for installing Ubuntu on a TC1100.  Finding that has saved me a lot of time trying to remember the tweaks to get everything working properly.

I did a clean install following the guide, however I have run into one snag I could use some help with.  The rotate script works great, except the mouse pointer doesn't rotate with the screen if I use the mouse control on the keyboard.  If I use the pen stylus, it's fine.

In the past I've run into the issue where the mouse pointer doesn't rotate with both the mouse control on the keyboard and the stylus, but I've never had one of them rotate properly while the other doesn't.  Any help would be greatly appreciated.  Thanks.

---

### Post by MyR on 2010-09-09
You use the keyboard in portrait mode??

---

### Post by watchoutman on 2010-09-09
> **MyR said:**
> You use the keyboard in portrait mode??
Haha...You've got a good point. I guess it's been a while since I messed with this. However, I could have sworn, in an earlier version, the rotation worked so controlling the mouse pointer with the keyboard button didn't make it move in the opposite direction.  Right now I can't think of a situation where I'd need that to work. Problem solved.

---

### Post by Randy Winchester on 2010-09-12
I just picked a TC1100 out of the trash.  It's a complete one with Bluetooth and keyboard.  It included all the disks, manuals, nice case. and a USB DVD drive.  Didn't look like it had ever been used and there was no OS on the drive (or the drive had been wiped).  I thought I'd go for the latest Maverick beta, but I kept running into snags with it.  I might try it again when it comes out in release.

Lucid works great though, except for the stylus buttons on the side of the screen.  No problem.  They are easy enough to duplicate on the panel.  I especially think that Compiz running on a seven year old laptop is pretty amazing, and the Compiz annotation tool is especially useful on a tablet PC. 

Thanks to all of you for figuring all this hard stuff out.  It made it easy and mostly fun for me to get mine up and running.

---

### Post by Randy Winchester on 2010-09-19
Very strange.  The pen suddenly stopped working today.  I don't know what happened.  I've tried a lot of things to get it working again, but no luck.  I've taken a couple of software updates in the last few days, but I'm not sure that caused it.  I tried completely removing and reinstalling xserver-xorg-input-wacom.  Anyone else ever experience this?  Any ideas?  

Randy

---

### Post by Randy Winchester on 2010-09-19
I still don't have pen functioning, but I think I'm a step closer.  It appears that Xorg is trying to load a "Serial Wacom Table eraser" that fails.  Later it tries to add "Serial Wacom Tablet" (type: STYLUS).  It can't initialize either device, so it reports an error and unloads  the Wacom module.  

Problem is, I can't locate where this is configured so I can comment it out.  Can anyone help me?

Here's the relevant portion of the Xorg.0.log:

(II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS0)
(**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.7.6, module version = 0.10.5
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/ttyS0"
(II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
(II) Serial Wacom Tablet: other types will be automatically added.
(**) Serial Wacom Tablet: always reports core events
(**) Option "TPCButton" "on"
(**) Option "Button2" "3"
(II) Serial Wacom Tablet: hotplugging dependent devices.
(**) Option "Device" "/dev/ttyS0"
(**) Serial Wacom Tablet eraser: always reports core events
(**) Option "Button2" "3"
(II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER)
(EE) Serial Wacom Tablet eraser: wcmWriteWait error : Input/output error
(EE) Serial Wacom Tablet eraser: wcmWriteWait error : Input/output error
(II) Serial Wacom Tablet eraser: serial tablet id 0x90.
(EE) Couldn't init device "Serial Wacom Tablet eraser"
(II) UnloadModule: "wacom"
(II) Serial Wacom Tablet: hotplugging completed.
(II) XINPUT: Adding extended input device "Serial Wacom Tablet" (type: STYLUS)
(EE) Serial Wacom Tablet: wcmWriteWait error : Input/output error
(EE) Serial Wacom Tablet: wcmWriteWait error : Input/output error
(II) Serial Wacom Tablet: serial tablet id 0x90.
(EE) Couldn't init device "Serial Wacom Tablet"
(II) Serial Wacom Tablet: removing automatically added devices.
(II) UnloadModule: "wacom"

Cheers,
Randy

---

### Post by MyR on 2010-09-20
Randy -- I doubt that the problem has to do with the eraser.  However, since the stylus works out-of-the-box I am unable to duplicate your problem.  Test to make sure your hardware is working by using a livecd.

Regards

---

### Post by Randy Winchester on 2010-09-20
Mi MyR,

I can do the BIOS pen calibration, so I know the hardware still works.

I'm just curious about what goes on in the X11 init as detailed in the log segment above.  Everything seems to go right until 

(II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER)

which causes an errror, then later

(EE) Couldn't init device "Serial Wacom Tablet eraser"
(II) UnloadModule: "wacom"

That just doesn't look good to me.  Do you have something similar in your Xorg.0.log?  Is something in X11 configured wrong, or does X get this from HAL?  Any ideas how to fix?

Cheers,
Randy

---

### Post by Aearenda on 2010-09-21
Here's the relevant part of my Xorg.0.log:
```
(**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 0.10.5
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 7.0
(**) Option "Device" "/dev/ttyS0"
(II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
(II) Serial Wacom Tablet: other types will be automatically added.
(**) Serial Wacom Tablet: always reports core events
(**) Option "TPCButton" "on"
(**) Option "Button2" "3"
(II) Serial Wacom Tablet: hotplugging dependent devices.
(**) Option "Device" "/dev/ttyS0"
(**) Serial Wacom Tablet eraser: always reports core events
(**) Option "Button2" "3"
(II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER)
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
(WW) Serial Wacom Tablet eraser: Waited too long for answer (failed after 3 tries).
(WW) Serial Wacom Tablet eraser: Waited too long for answer (failed after 3 tries).
(II) Serial Wacom Tablet eraser: serial tablet id 0x90.
(--) Serial Wacom Tablet eraser: using pressure threshold of 7 for button 1
(--) Serial Wacom Tablet eraser: Wacom General ISDV4 tablet speed=38400 maxX=21240 maxY=15980 maxZ=127 resX=2540 resY=2540  tilt=disabled
(--) Serial Wacom Tablet eraser: top X=0 top Y=0 bottom X=21240 bottom Y=15980 resol X=2540 resol Y=2540
(II) Serial Wacom Tablet: hotplugging completed.
(II) XINPUT: Adding extended input device "Serial Wacom Tablet" (type: STYLUS)
(--) Serial Wacom Tablet: top X=0 top Y=0 bottom X=21240 bottom Y=15980 resol X=2540 resol Y=2540
```

My /etc/X11/xorg.conf doesn't have anything at all for the pen, but this is what is in /usr/lib/X11/xorg.conf.d/10-wacom.conf:
```
Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
    Option "ForceDevice" "ISDV4"
    Option "TPCButton" "on"
    Option "Button2" "3"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

```

I hope this helps!

---

### Post by MyR on 2010-09-21
You could also try to load the module manually with
```
sudo modprobe wacom
```

---

### Post by Randy Winchester on 2010-09-21
> **MyR said:**
> You could also try to load the module manually with
```
sudo modprobe wacom
```

Thanks again, but still no luck.

The major difference in our Xorg.0.logs is that where your's shows a warning when trying to hotplug ERASER and STYLUS, mine give an error and unloads the driver.  Actually, I'm not sure that the driver quite gets unloaded.  If I do a "modprobe -l" I see:

kernel/drivers/input/tablet/wacom.ko
kernel/drivers/input/touchscreen/wacom_w8001.ko
kernel/drivers/hid/hid-wacom.ko

so it looks like I have drivers loaded in the kernel.  Attempting 

sudo modprobe -r wacom

doesn't remove the modules, and running modprobe again doesn't seem to change anything either.  

I'm using your xorg.conf.d/10-wacom.conf and was using it successfully for a week before the problem started.

I'm at a loss at this point.  I'd really hate to have to reinstall the OS, as I'm happy with the way everything else is set up, and it took a lot of time to get it that way. 

Cheers,
Randy

---

### Post by Aearenda on 2010-09-22
Randy, here are a few things to look at for clues...

What kernel are you using? Do you have any backport drivers installed? (I don't) 
Here's my kernel:
```
$ uname -a
Linux brainiac-2 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux

```

What version of xserver-xorg-xinput-wacom is installed? (Mine is 1:0.10.5-0ubuntu4)

I don't think 'modprobe -l' says the driver is loaded, it says it's available. Using 'lsmod' doesn't show any wacom drivers on my working system either, because it's an xorg driver.

Have you manually blacklisted any kernel modules in /etc/modprobe.d, or forced anything to load in /etc/modules?

---

### Post by Aearenda on 2010-09-22
Actually, skip this post - I've realised the failure messages are caused by the xorg.conf entries for /dev/input/wacom, which doesn't exist in 10.04. 

------------------IGNORE THIS POST AFTER THIS LINE--------------------------------

I've just made an interesting discovery. I have two crippled TC1100s, for historical reasons that I won't go into here. The one I use less often has two goes at loading the wacom driver showing in the Xorg log. The first time it shows the standard version numbers and so on, and then later on it comes up with this:```
(**) Option "Device" "/dev/input/wacom"
(WW) stylus: failed to open /dev/input/wacom.
(II) UnloadModule: "wacom"
(EE) PreInit returned NULL for "stylus"
(**) Option "Device" "/dev/input/wacom"
(WW) cursor: failed to open /dev/input/wacom.
(II) UnloadModule: "wacom"
(EE) PreInit returned NULL for "cursor"

```

Later on, it tries again, showing the same output as the other TC1100 I quoted above.
It has the following 'traditional' contents in /etc/X11/xorg.conf, which would be the reason for this I think, since it has the standard contents for /usr/lib/X11/xorg.conf.d/10-wacom.conf from MyR's howto:
```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"
    Option         "Button2" "3"
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"
    Option         "Button2" "3"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Nvidia Default Flat Panel"
    HorizSync       29.0 - 49.0
    VertRefresh     0.0 - 61.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce4 420 Go 32M"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    Option         "RandRRotation" "on"
    Option         "NvAGP" "1"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enabled"
EndSection

```
The metamodes part is because this TC1100 was damaged by lightning and always thinks there is an external monitor connected, so I have to override it.

Randy, I wonder if you were to add the stylus and layout data to your xorg.conf, your system would try to load the driver again?

It's worth a try, and so is MyR's live CD suggestion, so that we can see whether the issue is brought on by an Ubuntu update (it shouldn't be, as my TC1100s are both right up to date).

-----------------------END OF IGNORED POST--------------------------------------

---

### Post by Aearenda on 2010-09-22
Ok, so I'll try to get over the embarrassment of last post's obvious mistake and ask a serious question: Randy, does /dev/ttyS0 exist on your TC1100 and do you have the setserial package installed? I'm just wondering because the serial parameters don't show up in your Xorg.0.log.

---

### Post by Randy Winchester on 2010-09-22
> **Aearenda said:**
> Randy, here are a few things to look at for clues...

What kernel are you using? Do you have any backport drivers installed? (I don't) 
Here's my kernel:
```
$ uname -a
Linux brainiac-2 2.6.32-24-generic #43-Ubuntu SMP Thu Sep 16 14:17:33 UTC 2010 i686 GNU/Linux

```

What version of xserver-xorg-xinput-wacom is installed? (Mine is 1:0.10.5-0ubuntu4)

I don't think 'modprobe -l' says the driver is loaded, it says it's available. Using 'lsmod' doesn't show any wacom drivers on my working system either, because it's an xorg driver.

Have you manually blacklisted any kernel modules in /etc/modprobe.d, or forced anything to load in /etc/modules?

Hi Aearenda,

No backport drivers installed AFAIK.  
This is a pretty fresh install and I've kept it up to date.  I'm running the same exact kernel and xserver-xorg-xinput-wacom as you.  

I added tc1100-wmi to /etc/modules as per some instructions I saw early on.  It was working with it, but I also tried removing it and saw no change.  

There's nothing wacom related blacklisted in /etc/modprobe.d.

---

### Post by Randy Winchester on 2010-09-22
> **Aearenda said:**
> Randy, does /dev/ttyS0 exist on your TC1100 and do you have the setserial package installed? I'm just wondering because the serial parameters don't show up in your Xorg.0.log.

Hi Aearenda,

ttyS0 is created on my TC1100 and it does report as busy.  I also have setserial installed.  I just double checked the Xorg.0.log excerpt that I posted here, and it ttyS0 does show up.

Thanks for all your help.  It's a strange problem, and I'm not quite sure how to cook up diagnostics to see how it fails when others obviously don't.  I'll also try the live CD again.  I'm pretty sure that will work ok, but if it doesn't I might have something.

I might also try removing all of Xorg and reinstalling.  

Cheers,
Randy

---

### Post by Aearenda on 2010-09-22
Actually, I should have been clearer- I *don't* have setserial installed!

---

### Post by Randy Winchester on 2010-09-23
> **Aearenda said:**
> Actually, I should have been clearer- I *don't* have setserial installed!

Ka-Ching!  That's the correct answer! Thank you thank you!

I removed setserial and the pen is working again.  I appears that setserial tagged along as a dependency when I installed lirc, so I got rid of lirc also.  Now that I know what the problem was, I'm guessing that there is probably a way to get the pen working at the same time as lirc by tweaking setserial.

Is anyone here now using a TC1100 with lirc and is the pen still working?  If so, how did you do it?  Is anyone doing anything worthwhile / fun / cool with lirc on a TC1100?

I don't recall seeing this point in the forums or anywhere else discussing Linux on the TC1100, so if someone is keeping a knowledge base on the topic, they'll want to add this.

Cheers,
Randy

---

### Post by Aearenda on 2010-09-23
Good! I've never tried lirc. It seems to me though that it should be possible to use setserial to set the same parameters for /dev/ttyS0 as it uses without setserial, as seen in Xorg.0.log.

---

### Post by Randy Winchester on 2010-09-23
I didn't really set up lirc to do anything.  I just installed it thinking I would play with it later.  Should be able to make it play with the wacom somehow with setserial.

Thanks again for your help!  I'm going to back up this thing before I make any drastic changes.  I love this little tablet!  It's a great little computer, especially considering that it's seven years old!

---

### Post by Aearenda on 2010-09-26
I just happened to boot one of my TC1100s with Windows XP, and I noticed it's running a lot cooler. Has anyone else noticed heat or fan problems on a TC1100 with Lucid? 

I suppose it could be tied up with the hardware fault on both my TC1100s that prevents them from rebooting properly when hot - I have to shut down and put them in the fridge for 10-15 minutes instead of just rebooting. One of them was also damaged by a lightning power surge, but it's not that one that I'm concerned about. There's no appreciable difference in responsiveness between XP and Lucid.

---

### Post by Randy Winchester on 2010-09-26
> **Aearenda said:**
> I just happened to boot one of my TC1100s with Windows XP, and I noticed it's running a lot cooler. Has anyone else noticed heat or fan problems on a TC1100 with Lucid?

I've read about this on other forums / blogs.  I just left my TC1100 w Lucid running for the last six hours.  I just got back to it and it is hardly a few degrees above ambient temperature.  It certainly runs a *lot* (I mean a LOT) cooler than my 17" MacBook Pro running MacOS 10.5.  I could use that one for cooking pancakes.  It is almost hot enough to burn flesh sometimes, it's also a known problem.  The TC1100 is amazingly cool compared with my MacBook.

Cheers,
Randy

---

### Post by Aearenda on 2010-09-26
Good to know, thanks. I've been doing some experiments, and I suspect it's partly to do with CPU utilisation caused by the screensaver, which I've now disabled and set to turn the screen off instead. It's also better when not charging. Oddly, the lightning-affected one seems to run a little cooler when idle (48C according to lm-sensors rather than 51C).

---

### Post by Greylopht on 2010-09-28
Well so far for me 10.4 has been moderately painless.  Thank the gods for Easystroke since the Pen buttons are not working, and I have, when I have had time poked at that bit but come out with a big ol nothing.  So here are some things I can report on.

The good...

With things dimmed down to there lowest setting, WiFi/BT off things generally lightened up.  (Killing evolution and other services that do not need to run all the time)  I am drawing 9 watts to 10 watts of power while reading graphic novels using Comix.

Boot times are generally in the range of 15 to 20 seconds to desktop.  Pen, pen click, WiFi, BT, PCIMCIA, USB, Second video out, Ethernet all work out of the box with out so much as a glitch.  Things seem to run cool for the most part.   Battery life (I have a brand new OEM battery)  Seems to last 4.5 to 5 hrs reading graphic novels, or ebooks.  Videos play well for the most part.  (Lets face it these things are not bleeding edge Tech so don't ask them to do HD)  Sound as always is absolutely fabulous, and that is expected because the TC1100's have always had great sound.

The BAD!

After rotation I get some artifacting on the very upper and lower edges of the panels.  This happens every rotation and can be removed by just switching to another workspace and back.   Not really something huge but a annoyance.  Tied into this we have...

When rotated to portrait position and playing a flash video/normal video.  The video card seems over taxed, as if hardware is not accelerating to it's full potential.  I am looking into this as well, and so is another friend of mine who has my TC1100's sister machine.   This did not happen in 8.10 or 9.10 so I am wondering if there is something fishy with the Nvidia drivers.  I have noticed that with the Xorg.conf file we seem to be using it never fully activates the Nvidia driver set.  (Less it is me because hardware drivers shows it as disabled).  Any word on this?   Landscape works just fine for video however.

When using the disable WiFi script sometimes I get a snapping sound from the vicinity of the WiFi card.  Not amused by this and it is especially noticeable when initially booting up after forgetting to turn WiFi on before the previous shutdown.

Compiz takes a tone of runtime so I killed it with no remorse.

I am having some issues with my Sprint Cell card, but that is a completely different issue.

All in all I am pleased but I am leaning towards 9.10 as a more stable (more friendly) version at this point.  

The conclusion....

I like it, however I would like my Pen buttons back.  It runs as hot and the fan runs like it always.  Fan runs slow or is off when the screen is off or things are not being taxed.  (Screen saver on causes the fan to come on)  And the fan runs and it will cook your hand when running video and or charging.  I think this is a TC1100 thing.   When just reading graphic novels/books fan runs on medium and it does not get as hot.   Now with Win of course it will boil water as fast as a induction stove.

Some history on my TC is, well it has a 2 year old mother board.  I got a deal on a NEW one from HP but it still cost a packet.  And having learned the hard way never plug the keyboard in.  Just don't ever, this is a documented thing with the TC's the keyboard latch and the MB cracking and causing havoc with the video chip set.  Back before the new motherboard I used to have to push up on the USB port for the keyboard with something plastic out in the field to get the thing to boot cleanly with out video issues.  Or chuck it in the freezer for a couple hours.

So there it is, if anyone has a direction to look to for the pen buttons lemme know.  And for the WiFi snapping/sound issue.   I mention I miss Wacom-Tools?  Oh how I miss Wacom-Tools....

~Grey

---

### Post by Randy Winchester on 2010-09-28
> **Aearenda said:**
> Good to know, thanks. I've been doing some experiments, and I suspect it's partly to do with CPU utilisation caused by the screensaver, which I've now disabled and set to turn the screen off instead. It's also better when not charging. Oddly, the lightning-affected one seems to run a little cooler when idle (48C according to lm-sensors rather than 51C).

I just had to check mine tonight to see what it is up to... 49C.  Not bad.  The fan does come on at a very slow speed.  I can hardly hear it running.  This machine has never gotten even more than just slightly warm.  Every other laptop I've had gets a lot warmer than my TC1100.

Cheers,
Randy

---

### Post by DannyBiker on 2010-10-01
Has anyone tried the upcoming Netbook version yet, with Unity ? It feels like the perfect interface for the HP TC1100, now that JoliCloud won't run properly...:P

---

### Post by Randy Winchester on 2010-10-02
> **DannyBiker said:**
> Has anyone tried the upcoming Netbook version yet, with Unity ? It feels like the perfect interface for the HP TC1100, now that JoliCloud won't run properly...:P

Hi Danny,

Actually, I had tried it with Maverick 10.10 Netbook / Unity.  I encountered some major installation hurdles that brought me here.  The major deal stopper, and hopefully fixed, is that installation finishes normally, but without the proprietary NVidia drivers, Unity won't start and you're stuck on a wallpaper screen with no way out... well, you can always CTRL/ALT/F1 for a terminal session.  I then installed 10.04 netbook which had its own issues, nothing major, just a little clunky.  Then I installed 10.04 desktop that I have running on two other machines, and it's been great.

I've sort of been following the Maverick / Unity bug, and now that we know what it is, if you get stuck, you can always install the NVidia driver from a terminal and reboot.

Please let us know how you like it if you do it.  I'm curious about how smoothly it goes.

Cheers,
Randy

---

### Post by Randy Winchester on 2010-10-13
I upgraded to 10.10 a couple of days ago.  Be aware that the Nvidia-96 driver that we use for the TC1100 will not work with the Xorg 1.9 that installs with 10.10.  There's no real fix or workaround for now other than to downgrade Xorg to Lucid or to go with the nv driver, which is what I did.  If you need 3D, don't upgrade.

Strangely, I found that AWM and Screenlets work just fine without Compiz.  Funny, as I always thought Compiz was required to run them.

The screen rotate script also craps out with the following message:

xrandr: Failed to get size of gamma for output default
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14
Cannot find device 'Serial Wacom Tablet'.

Probably because the Nvidia driver is required, I'm guessing.

Everything else seems to work just fine so far.

---

### Post by mattlezeay on 2010-10-13
Ok, so I figured bugs would be worked out and I was feeling like jumping into 10.10 - not such a good idea. I removed the nvidia graphics after the update and now I just hang at the login screen. I'm sure I will get it going but be warned that 10.10 isn't just a walk in the park.

---

### Post by DannyBiker on 2010-10-14
Hmmm...every new version comes with new problems. I must say that I'm not too confident for the future.:(

---

### Post by 3ar9 on 2010-10-14
> **Randy Winchester said:**
>  to go with the nv driver, which is what I did.  If you need 3D, don't upgrade. 
 
hi, what do you mean by going with the nv driver? Does that mean to update my nvidia driver?

---

### Post by Randy Winchester on 2010-10-14
> **3ar9 said:**
> hi, what do you mean by going with the nv driver? Does that mean to update my nvidia driver?

The nv driver is an open source driver from Xorg.  It has very limited capabilities.  It will not work with the 3d desktop effects.  Upgrading the Nvidia driver doesn't work.  There's a basic incompatibility with the Xorg 1.9 xserver and the Nvidia 96 driver that we need for the TC1100.  It's best to stick with Lucid for now until Nvidia updates their driver.

---

### Post by jjaythomas on 2010-10-15
If You like Lubuntu you can install Peppermint OS (not Ice) have a current Kernel and the Nvidia proprietary driver and most everything works from this thread and install guides:P

JJay

---

### Post by arandomkiwi on 2010-10-16
Hey guys

Looking into purchasing a tablet, the TC1100 to be exact and im keen to put 10.10's unity on it. But im looking for opinions if this is a smart thing to do. The tablet is remarkably cheap second hand (30 nzd) but I have little experience installing ubuntu on anything other than a pc and reading the experiences you guys have had installing 10.10 beta on the tc1100, a buggy ubuntu is something I cant handle. 

help, opinions, recommendations?

Cheers guys. Ubuntu community has always been real helpful and strong. Also excuse the the newbieness, I never really got to deep into ubuntu.

---

### Post by redbook4574 on 2010-10-16
> **arandomkiwi said:**
> Hey guys

Looking into purchasing a tablet, the TC1100 to be exact and im keen to put 10.10's unity on it. But im looking for opinions if this is a smart thing to do. The tablet is remarkably cheap second hand (30 nzd) but I have little experience installing ubuntu on anything other than a pc and reading the experiences you guys have had installing 10.10 beta on the tc1100, a buggy ubuntu is something I cant handle. 

help, opinions, recommendations?

Cheers guys. Ubuntu community has always been real helpful and strong. Also excuse the the newbieness, I never really got to deep into ubuntu.

For now I would suggest sticking with lucid, do not enable visual effects in my experience they tend to leave artifacts, every thing else works great.
If you can afford it make sure you have at lease 1gb ram, it improves performance no end.

---

### Post by Aearenda on 2010-10-16
> For now I would suggest sticking with lucid, do not enable visual effects in my experience they tend to leave artifacts, every thing else works great.
If you can afford it make sure you have at lease 1gb ram, it improves performance no end.
+1 except that I don't get any significant artifacts from visual effects.

---

### Post by Randy Winchester on 2010-10-16
> **arandomkiwi said:**
> Hey guys

Looking into purchasing a tablet, the TC1100 to be exact and im keen to put 10.10's unity on it. But im looking for opinions if this is a smart thing to do. The tablet is remarkably cheap second hand (30 nzd) but I have little experience installing ubuntu on anything other than a pc and reading the experiences you guys have had installing 10.10 beta on the tc1100, a buggy ubuntu is something I cant handle.

You don't want to try 10.10 on the TC1100 just yet.  There is an incompatibility with the proprietary Nvidia driver and the Xorg Xserver 1.9 that comes with 10.10.  It's pretty much a show stopper for me, as you need the driver to do things like rotate the screen.  I also run visual effects (Compiz) and find that the screen annotation is ideally suited to a pen PC.  The only way presently to make 10.10 work on the TC1100 is to downgrade Xorg to the Lucid version, and reinstall the Nvidia drivers.  It's not easy, and if I knew in advance how much trouble it was I wouldn't have upgraded.  I say stick with 10.04 Lucid until Nvidia upgrades the 96 driver.

Reference:  [http://www.omgubuntu.co.uk/2010/10/nvidia-96-driver-ubuntu-10-10-fix/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28Omg!+Ubuntu!%29](http://www.omgubuntu.co.uk/2010/10/nvidia-96-driver-ubuntu-10-10-fix/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28Omg!+Ubuntu!%29)

Cheers,
Randy

---

### Post by buddytod on 2010-10-19
I installed v10.10 before realizing that it is not possible to enable screen rotation at present. I have now installed V10.4 and I do not seem to have any wireless function at all. Appreciate any advice please.

---

### Post by MyR on 2010-10-19
> **buddytod said:**
> I installed v10.10 before realizing that it is not possible to enable screen rotation at present. I have now installed V10.4 and I do not seem to have any wireless function at all. Appreciate any advice please.

Try this:

```
echo 1 > /sys/devices/platform/tc1100-wmi/wireless
```

---

### Post by krazyme on 2010-10-24
Hello,

Just posting to give my feeling after installing Ubuntu Netbook Edition 10.10 on TC1100. It is my first install of Ubuntu Netbook, and also first on a tablet PC.

Working out of the box :
  - Wifi
  - Bluetooth (at least icon is there, haven't trid connecting to anything)
  - Stylus
  - video card with nv drivers in 2D mode, not working in 3D

Working after a few changes :
  - virtual keyboard (used florence, pretty nice)
  - rotation (via standard script), see below

Not working after multiple tries :
  - nvidia drivers (as expected, I am now hoping for an update from nvidia)
  - stylus buttons (still working on those)

******************************************************

Regarding rotation, here  is what I've done :

First run "xsetwacom --list dev", it will return something like this :
Serial Wacom Tablet eraser ERASER    
Serial Wacom Tablet stylus STYLUS

Take everything in front of STYLUS, and write this script ("sudo gedit /usr/bin/rotate"):

#!/bin/sh

if [ $# -eq 0 ]
then

  mode=`cat /var/log/rotate`
  if [ "$mode" = "normal" ]
  then
    /usr/scripts/rotate "left"
  elif [ "$mode" = "left" ]
  then
    /usr/scripts/rotate "inverted"
  elif [ "$mode" = "inverted" ]
  then
    /usr/scripts/rotate "right"
  else
    /usr/scripts/rotate "normal"
  fi

else

  success=0
  if [ "$1" = "normal" ]
  then
    xrandr -o normal
    xsetwacom set "Serial Wacom Tablet stylus" Rotate normal
    success=1
  elif [ "$1" = "left" ]
  then
    xrandr -o left
    xsetwacom set "Serial Wacom Tablet stylus" Rotate ccw
    success=1
  elif [ "$1" = "inverted" ]
  then
    xrandr -o inverted
    xsetwacom set "Serial Wacom Tablet stylus" Rotate half
    success=1
  elif [ "$1" = "right" ]
  then
    xrandr -o right
    xsetwacom set "Serial Wacom Tablet stylus" Rotate cw
    success=1
  else
    echo "Wrong parameter"
  fi
  if [ $success -eq 1 ]
  then
    echo $1 > /var/log/rotate
  fi
fi

Make /usr/bin/rotate executable : "sudo chmod +xxx /usr/bin/rotate"

Create /var/log/rotate : "sudo gedit /var/log/rotate"

Make /var/log/rotate writable : "sudo chmod +www /var/log/rotate"

Now :
  - "rotate" to rotate screen
  - "rotate [normal,left,inverted,right]" for specific direction

******************************************************

For virtual keyboard using onBoard for passwords and Florence for the rest

For florence, I have followed instructions on howto install on ubuntu france

Made it run on startup in "System->Preferences->Assistive Technologies".
Here set "Password dialogs as normal windows", then in "Preferred Applications->Accessibility", set "Mobility" at "custom", "command=florence", and check "Run at start"

Florence settings :
  - Window : Transparent, always on top, opacity=50% (not sure this changes anything)
  - Behaviour : everything is unchecked
  - Layout : alternative keyboard, Function keys, Florence keys

******************************************************

That's all for the moment, will keep posted about stylus keys and video driver (I need this one because I want to test unity)

---

### Post by Randy Winchester on 2010-10-25
> **krazyme said:**
> Hello,
For virtual keyboard using onBoard for passwords and Florence for the rest

For florence, I have followed instructions on howto install on ubuntu france

It turns out to be pretty tough installing florence from source.  It wants some dependencies that don't show up in the repos.  I did find a binary package for Lucid here:

[http://code.google.com/p/ardesia/downloads/detail?name=florence-ramble_0.1-debian-1_i386.deb&can=2&q=](http://code.google.com/p/ardesia/downloads/detail?name=florence-ramble_0.1-debian-1_i386.deb&can=2&q=)

Cheers,
Randy

---

### Post by krazyme on 2010-10-26
From Ubuntu France forums :

*****************
Install Florence's dependencies

sudo apt_get install build-essential libxml2-dev libgconf2-dev libglade2-dev libatspi-dev libcairo2-dev gnome-doc-utils librsvg2-dev gettext libnotify-dev libxtst-dev intltool fakeroot checkinstall

*****************
Install florence after download

tar -xjvf florence-0.4.7.tar.bz2
cd florence-0.4.7
./configure &#8211;prefix=/usr --without-xrecord
make
sudo make install

---

### Post by yeppp on 2010-10-27
I know a little while ago we were looking at how hot the tc1100 was running.  Mine doesn't get hot enough to notice at all (less than 48 C at all times ) unless I am watching a flash video or doing something else cpu intensive for a descent amount of time.  Yesterday I turned on visual effects to see how it would handle them.  I didn't have any artifacts, but I did notice that the computer ran hotter, causing the fan to run at high speeds constantly.  With compiz enabled it would run at 52 C while idle.  If your looking to use less battery for the fan and run much cooler, it might be worth considering disabling visual effects.

I also noticed that after disabling the wireless, I couldn't re-enable it (I am using the ath5k driver).  It never bothered me since I always needed the wireless, but I gave the command MyR suggested tobuddytod and found it allowed me to re-enable my wireless card.  I think I was able to do this in the past (turn wireless on and off) just by loading the tc1100 module per MyR's guide:

modprobe tc1100-wmi
echo "tc1100-wmi" >> /etc/modules

But it hasn't been working for a while.  I don't know if it was a kernel change that caused loading the module to not be enough for the wireless card or if I had just entered the command MyR gave when ever I was setting up the computer originally and just didn't remember.  Either way, thanks MyR.

---

### Post by Randy Winchester on 2010-10-30
What package provides tc1100-wmi?  I had it on my drive before I backed it up and replaced it, and now it doesn't seem to be there any longer.  Also, the internal wireless card works.  Fortunately, I've got a Proxim card in the external slot that is working.

Cheers,
Randy

---

### Post by Aearenda on 2010-10-30
It's in the kernel.
/lib/modules/2.6.35-22-generic/kernel/drivers/platform/x86/tc1100-wmi.ko

---

### Post by Randy Winchester on 2010-10-31
> **Aearenda said:**
> It's in the kernel.
/lib/modules/2.6.35-22-generic/kernel/drivers/platform/x86/tc1100-wmi.ko

Thanks.  Yup, I've got it.

I'm still trying to figure out what I did wrong when I upgraded my HD.  I copied my /, opt and home partitions and restored them on the new drive using gparted.  I reinstalled Grub2 on the new drive.  It booted up with everything working except wireless.  I also upgraded RAM at the same time, so I was thinking I possibly distrubed the wireless card.  I tried a couple more wireless cards I had on hand and one of them wasn't on the BIOS whitelist (got an error 104 - please remove unapproved wireless card and reboot.).  I can boot with the original and other wireless card but I can't get wireless to work.  lspci and lshw both see both of the cards, but I can't get the cards to function.  I'm now wondering if I did something stupid simple like configuring something off that I have to turn back on.

BTW, I've got a Proxim 11b/g PCMCIA card plugged in and it's working fine.  I would still like to have an internal card though.

Cheers,
Randy

---

### Post by Aearenda on 2010-10-31
Did you accidentally knock the antenna wires off the internal wireless card, perhaps? Static shock? Any error messages in dmesg output?

---

### Post by Randy Winchester on 2010-10-31
> **Aearenda said:**
> Did you accidentally knock the antenna wires off the internal wireless card, perhaps? Static shock? Any error messages in dmesg output?


Antenna wires are still in place, as I had to remove and reattach them several times as I tried different cards.

I took reasonable precautions for static.  I first thought that maybe I shocked the card, but none of the others I have on hand work either.  They also all show up in lspci.

The DMESG stuff is a fascinating read, but the only thing that look like an error message for the internal card is:

[   20.402680] udev: renamed network interface eth1 to eth2

and later:

[   35.972026] eth2: This firmware requires an ESSID in IBSS-Ad-Hoc mode.
[   35.999905] eth2: This firmware requires an ESSID in IBSS-Ad-Hoc mode.
[   36.056719] eth2: This firmware requires an ESSID in IBSS-Ad-Hoc mode.
[   36.105231] eth2: This firmware requires an ESSID in IBSS-Ad-Hoc mode.
[   36.147660] eth2: This firmware requires an ESSID in IBSS-Ad-Hoc mode.
[   36.189101] eth2: This firmware requires an ESSID in IBSS-Ad-Hoc mode.
[   36.232018] eth2: This firmware requires an ESSID in IBSS-Ad-Hoc mode.
[   36.264700] eth2: This firmware requires an ESSID in IBSS-Ad-Hoc mode.
[   36.299011] eth2: This firmware requires an ESSID in IBSS-Ad-Hoc mode.
[   36.355241] eth2: This firmware requires an ESSID in IBSS-Ad-Hoc mode.

Don't know what that renaming is about.  The external card is named wlan0.

What do you think?  Is the above reason for it to not work?

Cheers,
Randy

---

### Post by Aearenda on 2010-11-01
The eth1/eth2 rename usually happens when a drive that has run first on one machine, is now inserted and booted in another; or when a previously-present interface is replaced, as in your case. In the first instance, the network interface is detected and a rule is created in /etc/udev/rules.d/70-persistent-net.rules so that the interface always gets the same name. When booted in the second configuration, the old interface is gone, the new one is detected at first as eth0, but is renamed when udev finds the rule for the old eth0 to avoid confusion with IP configuration. A new rule is added to the same file each time this happens.

What chipset does your internal card use? Mine is Atheros, and uses the ath5k driver, but some TC1100s have Intel. I've never seen a firmware message like the one you posted, but it suggests that your system is trying to establish an ad-hoc network rather than connect to a wireless access point.

I suspect we're going to have to see:
1. The output from 'dmesg'
2. The output from 'lshw -c network'
3. The output from 'sudo rfkill list'
4. The output from 'iwconfig'
5. The contents of /etc/network/interfaces

I expect there's more, but I can't think of it right now....

---

### Post by Randy Winchester on 2010-11-01
> **Aearenda said:**
> 

What chipset does your internal card use? 

The card that's in there now is a Dell TrueMobile 1150 Series PC Card, Version 01.01.  It uses Orinoco driverversion=0.15 firmware=Lucent/Agere 8.72.

The original card was the Intel.  The only problem is that if the Intel card is installed, I can't get a connection from it OR from the Proxim PCMCIA card (wlan0).  That's another strange issue.

> **Aearenda said:**
> 
I suspect we're going to have to see:
1. The output from 'dmesg'

$ dmesg|grep eth2

[   20.323014] udev: renamed network interface eth1 to eth2
[   20.542659] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   38.535054] eth2: This firmware requires an ESSID in IBSS-Ad-Hoc mode.
[   38.592763] eth2: This firmware requires an ESSID in IBSS-Ad-Hoc mode.
[   38.674091] eth2: This firmware requires an ESSID in IBSS-Ad-Hoc mode.
[   38.766478] eth2: This firmware requires an ESSID in IBSS-Ad-Hoc mode.
[   38.882565] eth2: This firmware requires an ESSID in IBSS-Ad-Hoc mode.
[   39.002093] eth2: This firmware requires an ESSID in IBSS-Ad-Hoc mode.
[   39.069593] eth2: This firmware requires an ESSID in IBSS-Ad-Hoc mode.
[   39.148824] eth2: This firmware requires an ESSID in IBSS-Ad-Hoc mode.
[   39.219449] eth2: This firmware requires an ESSID in IBSS-Ad-Hoc mode.
[   39.288805] eth2: This firmware requires an ESSID in IBSS-Ad-Hoc mode.

> **Aearenda said:**
> 
2. The output from 'lshw -c network'

  *-network               
       description: TrueMobile 1150 Series PC Card
       product: Version 01.01
       vendor: Dell
       physical id: 0
       slot: Socket 0
       resources: irq:15
  *-network
       description: 802.11g Wireless Upgrade Kit.
       product: CIS REV 1.2
       vendor: Proxim, Corp.
       physical id: 0
       version: Copyright 2003
       slot: Socket 1
       resources: irq:11
  *-network
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 01
       serial: 00:0b:cd:ad:02:ae
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: irq:12 memory:e0000000-e0001fff memory:6c000000-6c003fff(prefetchable)
  *-network
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 1
       bus info: pci@0000:07:00.0
       logical name: wlan0
       version: 01
       serial: 00:20:a6:52:1a:9d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.2.6 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:11 memory:74000000-7400ffff
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth2
       serial: 00:02:2d:6a:85:9c
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 8.72 link=no multicast=yes wireless=IEEE 802.11b

> **Aearenda said:**
> 
3. The output from 'sudo rfkill list'

0: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

> **Aearenda said:**
> 
4. The output from 'iwconfig'

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11b  ESSID:"hyenanet"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: None   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11bg  ESSID:"hyenanet"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:11:50:40:D4:13   
          Bit Rate=11 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-72 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

**Looks like for whatever reason, eth2 is not receiving RF from the access point.  It also does not appear to be transmitting.**

> **Aearenda said:**
> 
5. The contents of /etc/network/interfaces

$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback

> **Aearenda said:**
> 
I expect there's more, but I can't think of it right now....

I'm thinking I probably did some simple thing to disable the internal slot when I installed the RAM upgrade or new HD.  I booted from a USB pen drive (install CD image) while I was copying and restoring the partitions from my old to new drives and that was when I first noticed that I did not have wireless connectivity when running the live CD image.

Cheers,
Randy

---

### Post by Aearenda on 2010-11-01
Randy, I really wanted *all* the output from dmesg, maybe as an attachment, since your filter may be omitting useful stuff. But see below first...

See [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/498336") for something similar for the Dell/Orinoco.
Also [this unanswered question]("https://answers.launchpad.net/ubuntu/+question/109134").
I found these by Googling "This firmware requires an ESSID in IBSS-Ad-Hoc mode."

Your lshw output shows multiple wireless interfaces, and iwconfig shows two of them active. I really think you should just have one interface present at a time while we try to sort out why nothing works. I've never used an Orinoco card, so I'd rather drop that one for now. Your lshw lists an Atheros 5001X, which is what my TC1100 has, so I'm wondering why you say it's an Intel one?

Please would you remove all the extra cards, leaving only the internal card, restart, and attach the dmesg and lshw output again?

---

### Post by Randy Winchester on 2010-11-01
> **Aearenda said:**
> 
Please would you remove all the extra cards, leaving only the internal card, restart, and attach the dmesg and lshw output again?

I swapped the Intel card back in and ran dmesg, lshw and iwconfig again.  The card is recognized but disabled.  I have not figured out how to enable it.  Also, the PCMCIA card won't start when the Intel card is installed, so I had to shut down and remove the Intel card before starting up so I could send these.

---

### Post by Randy Winchester on 2010-11-01
> **Aearenda said:**
> See [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/498336") for something similar for the Dell/Orinoco.
Also [this unanswered question]("https://answers.launchpad.net/ubuntu/+question/109134").
I found these by Googling "This firmware requires an ESSID in IBSS-Ad-Hoc mode."

Hmmm, thanks!  I thought there was something up with the Dell TrueMobile Orinoco/Lucent card.  I gave one of the early reports on using this card with 10.04.  I actually got it to work for a very short time on the Dell, then it crapped out and never came back.  Looks like lots of people have had trouble with this particular card.

Cheers,
Randy

---

### Post by Aearenda on 2010-11-01
The dmesg output does say your wireless is turned off, and the 'rfkill list' output confirms this as the Bluetooth is off (otherwise, it would be listed as hci0 - but the wireless off switch on the TC1100 makes the Bluetooth hardware disappear altogether).

On my TC1100 I have the following in /etc/rc.local to make sure the wireless is enabled in the BIOS at startup:
```
echo 1 > /sys/devices/platform/tc1100-wmi/wireless
```This HAS to be done as root, so if you want to try it from the command line, first do: ```
sudo -i
```
But in your case, you'll need to reboot again without the other cards in, so you might as well just add the 'echo' command to /etc/rc.local and then shut down.

---

### Post by Randy Winchester on 2010-11-02
> **Aearenda said:**
> The dmesg output does say your wireless is turned off, and the 'rfkill list' output confirms this as the Bluetooth is off (otherwise, it would be listed as hci0 - but the wireless off switch on the TC1100 makes the Bluetooth hardware disappear altogether).

On my TC1100 I have the following in /etc/rc.local to make sure the wireless is enabled in the BIOS at startup:
```
echo 1 > /sys/devices/platform/tc1100-wmi/wireless
```This HAS to be done as root, so if you want to try it from the command line, first do: ```
sudo -i
```
But in your case, you'll need to reboot again without the other cards in, so you might as well just add the 'echo' command to /etc/rc.local and then shut down.

This works perfectly now!  Thank you!  The big mystery to me is how this got turned off in the first place.  It was working fine for the longest time, then simply stopped while I was upgrading the RAM and HD.  I was backing up and restoring entire partitions, not copying files, so I would expect that everything would be more or less duplicated exactly.  Do you have any ideas how this might have gotten corrupted?

Cheers,
Randy

---

### Post by Aearenda on 2010-11-02
Great! Two theories:
1) I suspect the TC1100 code in Lucid turns the switch off until it is explicitly turned on - hence the stuff in /etc/rc.local, which maybe you didn't copy across, though I don't see how not with a partition copy.
2) If it's not that, then normally the setting is remembered across reboots. It certainly is in Windows. During the disk copy process, what other operating systems did you boot (from CD or whatever)? Maybe one of these switched it off. This seems most likely.

In the early days of Linux on the TC1100, we didn't have control over the wireless switch, and had to reboot into Windows to turn it on or off!

---

### Post by Aearenda on 2010-11-02
Today was a holiday here, owing to a horse race, and on a whim I decided to see how Maverick would go on my TC1100. I knew there was no point installing the nVidia-96 driver yet (the bug says they are now working on it), but I wondered how it would go with the Nouveau driver. I used the alternate i386 CD as that is what I had handy.

The outcome so far is brilliant! I turned on Metacity compositing, and left the Nouveau driver in 2D mode (I'm not a gamer, so no need for 3D acceleration). It feels fast, the pen just works (including the right-click button), the wireless just works (mine's Atheros), and no need to turn it on at startup, screen rotation works (but not the pen - it still needs a rotate script, and the name of the stylus is now changed to "Serial Wacom Tablet stylus").

I've yet to test standby and hibernate, as I've yet to reboot for the updated kernel, and my TC1100 won't restart when hot so I've left these to last. I have to put it in the fridge for about 20 minutes before restarting, owing to a motherboard crack. I'll post again when that's done, probably tomorrow as it's getting late here.

UPDATE: Oh well, that dampened my enthusiasm. Neither hibernate nor suspend worked. I wasn't surprised about hibernate, as I don't think I've ever had it work in Linux on the TC1100. Suspend used to work with the old nv driver, and sometimes with the nVidia driver, if the moon was in the right quarter...

---

### Post by MyR on 2010-11-02
Well I tried to suspend today on ubuntu 10.04 and it resumed with some cryptic error and openoffice wouldn't work.  I thought rebooting would fix it but instead it shut down and never started again.  Guess it's time to reinstall.... depressing isn't it.

I might try Ubuntu 10.10 Mischievious Mayhem.  Moniacle mauler.  mangled monstrosity.

---

### Post by Randy Winchester on 2010-11-04
> **Aearenda said:**
> Great! Two theories:
1) I suspect the TC1100 code in Lucid turns the switch off until it is explicitly turned on - hence the stuff in /etc/rc.local, which maybe you didn't copy across, though I don't see how not with a partition copy.
2) If it's not that, then normally the setting is remembered across reboots. It certainly is in Windows. During the disk copy process, what other operating systems did you boot (from CD or whatever)? Maybe one of these switched it off. This seems most likely.

I was booting from a 10.04 image on a USB thumb drive.  I did notice the first time that I booted that way that the wireless wasn't available.

> **Aearenda said:**
> In the early days of Linux on the TC1100, we didn't have control over the wireless switch, and had to reboot into Windows to turn it on or off!

You mean that Windows is actually useful for something?  :P

Cheers,
Randy

---

### Post by Aearenda on 2010-11-04
> **Randy Winchester said:**
> You mean that Windows is actually useful for something?  :P

Not IS but WAS :-)

---

### Post by Randy Winchester on 2010-11-04
> **MyR said:**
> Well I tried to suspend today on ubuntu 10.04 and it resumed with some cryptic error and openoffice wouldn't work.  I thought rebooting would fix it but instead it shut down and never started again.  Guess it's time to reinstall.... depressing isn't it.

I might try Ubuntu 10.10 Mischievious Mayhem.  Moniacle mauler.  mangled monstrosity.

Good idea to keep a backup around just for this situation.  I keep the TC1100 around basically as a plaything, but if I blow away the OS (which I've done several times) it's always nice to have a backup.  I also put / in a separate partition with partitions for home and opt, which makes upgrades easier, I think.

I just booted my TC1100 from the "official" 10.10 CD (I collect Ubuntu CDs) and OpenOffice.org works fine.  I don't think I can test suspend from a live CD.  I have never been able to use suspend reliably on any Linux distro on any of my machines, and that includes 10.04.  I looks like it works, but it usually starts acting weird after a short time and requires a reboot.

BTW, I've been enjoying the TC1100 a lot more since I added a 1GB RAM to the empty slot and a 100GB 7200 RPM drive.  I haven't done speed tests.  It doesn't seem to boot much faster, but once it is up and running, the drive is really fast accessing files.

Cheers,
Randy

---

### Post by Randy Winchester on 2010-11-04
> **Randy Winchester said:**
> I just booted my TC1100 from the "official" 10.10 CD (I collect Ubuntu CDs) and OpenOffice.org works fine. 


This isn't my endorsement of 10.10 on the TC1100.  I'm pretty happy with 10.04 for now.  I won't upgrade to 10.10 until the Nvidia 96 driver is updated.

Cheers,
Randy

---

### Post by MyR on 2010-11-06
10.04 will no longer suspend. Is anyone else having this problem?

---

### Post by Aearenda on 2010-11-06
Throwing caution to the winds I [downloaded]("http://www.nvnews.net/vbulletin/showthread.php?t=122606") and manually installed the nVidia 96.43.19 pre-release driver, [using instructions found here]("http://ubuntuforums.org/showpost.php?p=10075666&postcount=45"). It reverts to the text mode Plymouth screen (on account of 'nomodeset') but does work, including compiz - and I have successfully gone into standby and resumed!

I'm not recommending this path - better to wait for the official package, as this driver is pre-release and installing it manually means you have to reinstall it every time the kernel changes version number, so if you try it, don't ask me for help! But at least there is a sign of improvement on the way.

---

### Post by MyR on 2010-11-06
After a fresh install of 10.10 **suspend and stylus work perfectly**.  I have not attempted to install the nvidia driver because I don't need compiz.

Sad that once again the stylus buttons don't work. Does anyone here know how to submit the patch upstream??

I will be posting a guide shortly.  Not many things to fix though.

---

### Post by Aearenda on 2010-11-06
That's interesting - Nouveau was reporting a GPU lockup on my 10.10 as standby took place. I wonder if it was related to my ongoing heat/motherboard problem, and today with the new nVidia driver it's just cooler all round! 

I'm so tempted to order a refurbished motherboard and a new battery. I can't find anything like the TC1100 at the moment, so in theory I'm using a netbook for mission-critical work while Android tablets come of age. Just imagine if HP had persisted with this form factor and got the price and weight down, there would have been no need for iPads to be invented at all!

Update: Another interesting discovery: echo 0 > /sys/devices/platform/tc1100-wmi/wireless now seems to only turn off Bluetooth, not wifi. The brightness jogdial works as before.

Also, xbindkeys does 10 cpu wakes per second. That's not good for battery life!

Update 2: a day later, I still haven't had to reboot because standby is working perfectly so far! I wonder whether the 'nomodeset' entry is part of the reason, and whether it was attempts to get Plymouth working properly on 10.04 that broke standby there. The side effect of this is that the console has reverted to 640x480, and it uses the text-mode Plymouth screen, but that only shows briefly anyway and it's a low price to pay for working standby & resume.

Update 3: echo 0 > /sys/devices/platform/tc1100-wmi/wireless seems to prevent wireless turning back on if turned off using the Network Manager, so it doesn't only affect Bluetooth, it has a delayed effect on wifi.

Update 4: I'm now using the Nvidia-96 driver from the PPA mentioned in [this bug]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/626974") comment 97. This should result in automatic updates when the kernel changes. So far so good! 
I think all TC1100 users should click on the "This bug affects x users" link on that bug if not already done so.

Update 5: It seems that going into standby with the screen rotated can often lead to an X crash on resume. Rotating back before standby works around the issue. Maybe this will be fixed when the Nvidia-96 driver is no longer 'pre-release'.

I just got a pair of new batteries for the TC1100, so now I'm set to see if this is reliable enough for mobile use again :-)

---

### Post by gauravm on 2010-11-09
if anyone is interested....i'm on 10.04 on the tc1100 with the netbook-launcher-efl package running.

I was getting REALLY ANNOYED that whenever i used MyR's rotate script [here]("http://www.unifyingtheory.net/ubuntu10.04tc1100.html") the launcher would not fit into the screen when I went from landscape to portrait.

my fix: 
```

#!/bin/sh
killall netbook-launcher-efl

if [ -n "$(xrandr | grep 768x1024)" ]; then
        xrandr -o normal
        xsetwacom set "Serial Wacom Tablet" Rotate NONE
else
        xrandr -o left
        xsetwacom set "Serial Wacom Tablet" Rotate CCW
fi

netbook-launcher-efl

```

not the most elegant solution I agree but I couldn't figure out how to edit the width and height of netbook-launcher-efl without delving into source code so I figured just shutting down and restarting it will force it into the new dimensions *automatigically* 

and it does =)

---

### Post by MyR on 2010-11-09
> **Aearenda said:**
> 
Also, xbindkeys does 10 cpu wakes per second. That's not good for battery life!

I was going to mention that too but my battery life isn't any better with it gone, so it must be inconsequential.

---

### Post by Aearenda on 2010-11-09
> **MyR said:**
> I was going to mention that too but my battery life isn't any better with it gone, so it must be inconsequential.

I suspect you're right. I was running my TC1100 on battery last night and it seems that screen blanking, turning wireless off and CPU speed stepping make a significant difference to power consumption, but overall it's unfair to expect a 7-year-old machine to match a modern netbook in power usage. 

Gauravm said> if anyone is interested....i'm on 10.04 on the tc1100 with the netbook-launcher-efl package running.I've never seen that launcher running - does it look significantly different from the standard 10.04 one? I guess you have to install a load of Enlightenment libraries along with it.

The issue of programs not responding to screen size changes is one of those things that annoys me too. It's sort of like those programs that won't work on Windows XP and later without admin privilege - the Windows 95/98 developer never foresaw a change in the circumstances of the running program, and should have revised programming practices to suit the new environment but didn't. Dynamic screen size changes, plugging in projectors and external screens, changes from landscape to portrait are all things that should be easily catered for now, I reckon. But then, I haven't done any serious programming for 20 years, so what would I know?

---

### Post by gauravm on 2010-11-09
> **Aearenda said:**
> I've never seen that launcher running - does it look significantly different from the standard 10.04 one? I guess you have to install a load of Enlightenment libraries along with it.
The dependencies I can't comment on but the beauty I can.

Enjoy video [here]("http://www.youtube.com/watch?v=IEcTGa-RoKE")!

---

### Post by yeppp on 2010-11-20
I downgraded back to 9.10 a good while ago so that I could get the tablet pen buttons working again.  I still have problems with seemingly random freezes after resuming from suspend (Aearenda were you refering to this when talking about not having to reboot after suspending?).  I was wondering how 10.10 was looking now that there is discussion of the nvidia driver finally coming out.

---

### Post by MyR on 2010-11-20
> **yeppp said:**
> I downgraded back to 9.10 a good while ago so that I could get the tablet pen buttons working again.  I still have problems with seemingly random freezes after resuming from suspend (Aearenda were you refering to this when talking about not having to reboot after suspending?).  I was wondering how 10.10 was looking now that there is discussion of the nvidia driver finally coming out.

Aearenda's tablet has trouble booting because of a crack in the motherboard or something.

In 10.10 the tablet buttons STILL aren't working.  I have had no trouble with freezes.  On the other hand I haven't installed the nVidia driver because I don't need it.

---

### Post by MyR on 2010-11-20
sorry, duplicate post

---

### Post by MyR on 2010-11-20
duplicate post :[

---

### Post by MyR on 2010-11-20
sorry, duplicate post.  There's a problem with ajax on the ubuntuforums server right now.

---

### Post by Aearenda on 2010-11-20
> **yeppp said:**
> I downgraded back to 9.10 a good while ago so that I could get the tablet pen buttons working again.  I still have problems with seemingly random freezes after resuming from suspend (Aearenda were you refering to this when talking about not having to reboot after suspending?).  I was wondering how 10.10 was looking now that there is discussion of the nvidia driver finally coming out.

Random freezes used to happen for me after suspend with a variety of versions using the nVidia driver. I'm now able to suspend reliably so long as the screen is in landscape mode, using Maverick with the nVidia driver mentioned [in bug 626974 comment 97]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/626974"), and 'nomodeset' in /etc/default/grub (the relevant line is GRUB_CMDLINE_LINUX="nomodeset" ).

My TC1100 has a common fault with the GPU/motherboard connections caused by mechanical stress on the keyboard connector (actually, I have two TC1100s, both with this fault, and the original one was also zapped by a lightning strike so that there is no red signal on the external video connector). Putting the TC1100 in the fridge for 15 minutes allows it to reboot, and so does pulling gently on the slate part against the keyboard at the moment of rebooting. Card packing between the GPU and screen worked for a while, but also produces lighter areas on the screen. If I was brave I would try the solder reflow techniques to be found elsewhere on the web. It is also possible to get a refurbished motherboard, but the fault is now manageable for the present. Until I figured all this out I have been using a netbook for mobile work, but I am gladly reverting to using the TC1100, and have even got two new batteries for it.

I wouldn't want to downgrade just to get the pen buttons working - it's easy enough to add launchers to the panel, after all!

---

### Post by yeppp on 2010-11-21
MyR, what is the temperature of your tc1100 like without the nvidia driver installed?  Does it seem to run much hotter than it did when you had the driver installed with 10.04?

---

### Post by chandra78 on 2010-11-23
Pardon the off-topic nature of the question but while trying to install Maverick on my new old tc1100, WUBI blew away the boot loader. The tablet won't boot from USB drive, but I did manage to PXE boot it off my laptop, also running Maverick. I can then run the maverick installer but what I'd really prefer to do is install grub to the drive and recover access to the XP partition. I gather it's a pxelinux config and grub-mkimage issue, but I'm out of my depth, sorry to be a pest. 

I'd rather not run the installer over pxe because then I have to use a bridged, slow wireless connection instead of the ethernet.

Has anyone else had issues booting to USB? the device is listed as a boot option in bios but is simply bypassed on boot-up.

---

### Post by Aearenda on 2010-11-23
I don't think the BIOS will boot off a USB memory stick, but it will boot off a USB CD-ROM. I don't use WUBI so it's better to see if anyone else has a clue how to recover it.

Another way out might be to use a Windows XP CD to reinstall its boot loader, and then reinstall WUBI.

---

### Post by yeppp on 2010-11-23
I tried to boot off a usb memory stick a few months back with the same results you are finding; even though it is listed as an option, the tablet ignores it. Aearenda is probably right that the usb option is for usb CD-ROM drives.  Hopefully someone else with more experience can help, otherwise you will probably have to go ahead and install ubuntu so that grub is installed along with it.

---

### Post by MyR on 2010-11-23
Here's how to boot the tc1100 with a USB drive: (Sorry, I don't have it in front of me & yeppp I haven't forgotten about you; I'll have an answer when I have more time to play with it.)

Plug in the USB drive
Turn on the tablet
press the jogdial while BIOS is coming up
go down to system setup or whatever
go over to boot order
go down to hard drive and hit enter to show options
change the order of the hard drives so that the USB drive is on top
save and exit

---

### Post by Randy Winchester on 2010-11-25
> **MyR said:**
> Here's how to boot the tc1100 with a USB drive: (Sorry, I don't have it in front of me & yeppp I haven't forgotten about you; I'll have an answer when I have more time to play with it.)

Plug in the USB drive
Turn on the tablet
press the jogdial while BIOS is coming up
go down to system setup or whatever
go over to boot order
go down to hard drive and hit enter to show options
change the order of the hard drives so that the USB drive is on top
save and exit

That's it!  I did my 10.04 install from USB a couple of months ago.  The TC1100 is the first computer I've had that will reliably boot from a USB thumb drive!  Even my Macbook Pro won't do it!

Cheers,
Randy

---

### Post by chandra78 on 2010-11-26
> **Randy Winchester said:**
> That's it!  I did my 10.04 install from USB a couple of months ago.  The TC1100 is the first computer I've had that will reliably boot from a USB thumb drive!  Even my Macbook Pro won't do it!

Cheers,
Randy
Fiddlesticks. That's exactly what I did. BIOS recognizes the device, even lists it by volume name, and I can move it up and down the boot order, even disable all other boot sources, and it skips it when actually booting. At power on I can see the thumb being accesses, but it quickly relaxes into LED snore mode, which is what happens when I have it plugged in but unmounted. I can boot my laptop with the thumb. Perhaps it's a specific hardware conflict with this thumb. I haven't got an external CD, but I'll borrow an external SATA disk from work and see if I can boot to that using USB.

Thanks for the responses~
nl

---

### Post by TheLegace on 2010-12-11
Has anyone successfully gotten the 10.10 Unity UI to work properly. I have been struggling at it for a while.

So far I installed the official Nvidia driver installer. I can get the unity to boot up, but it starts flashing and restarting and basically unusable. It's a shame, because the UI seems so nice. Does anyone know how exactly to get it working. This is kinda the whole reason I got the tablet in the first place.

Should I give pre-release drivers a chance. I don't really care about 3D acceleration, I just want unity to work. 

Thanks so much.

EDIT: After doing research, I think this is the bug problem.
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/626974](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/626974)
Now maybe I could go back to 1.7 or 8 of Xorg. Is there a way to do that?
TheLegace.

---

### Post by _BND on 2010-12-11
Reason why i registered here was this Tutorial and to say thanks for it. I read through the compete thread and i just want to say thanks for it :-)

:popcorn:

---

### Post by MattPurland on 2011-01-24
Hi All,

I've just managed to get hold of a TC1100 and have successfully installed 10.10 Netbook edition and have the nvidia-96 driver working but I can't seem to get Compiz working. I've not touched Linux in about 5 years so I'm a little rusty.

I've installed Simple CompizConfig after reading various walkthroughs and I can select the various options under Appearance > Visual Effects but when it goes to apply the settings it reverts back to the 'None' setting.

What's the best way to test that compiz can run? I'm guessing I need to change some options in the xorg.conf but I'm not sure what.

Any pointers would be appreciated!

Matt

---

### Post by Aearenda on 2011-01-24
I don't use the netbook edition, but if I recall correctly there was a clash between compiz and the netbook launcher (which uses clutter) in earlier versions, and this may still be true with Unity in 10.10. This problem will go away with natty, where the new version of Unity uses compiz anyway.

In the mean time, maybe you could switch over to a standard Gnome session - at the GDM login screen, look at the list of sessions available at the bottom of the screen. You may have to select a user name first. If it's not there I'm sure there is a way to install it alongside the Netbook session, probably by installing the 'ubuntu-desktop' package and all its dependencies, but I can't say I've tried it. If Compiz won't enable in the standard session, then there's something deeper wrong (assuming you've followed the instructions about the Nvidia settings in /etc/X11/xorg.conf in this thread already).

For reference, my /etc/X11/xorg.conf on 10.10 has just this:```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
	Option	"RandRRotation"	"True"
	Option	"NvAGP"		"1"
        Option  "AddARGBGLXVisuals"     "True"
EndSection

```
I reckon one of the 'AddARGBGLXVisuals' items is superfluous, but I'm not sure which one!

---

### Post by MattPurland on 2011-01-24
I'm actually using the normal desktop instead of the Netbook desktop and it doesn't work in either :(

The notebook desktop loads up but as soon as you over over an icon it reloads itself.

I did try the added options to the xorg.conf from this thread but couldn't get the driver to load - I'll try what you've provided and see what happens!

Thanks,
Matt

---

### Post by MattPurland on 2011-01-24
I've fixed it!

Ran it from command-line to see any output and I was just missing a window manager - installed Emerald and it works perfectly!

So it looks like The current release of the nVidia driver along with the automatically detected settings makes everything work out of the box!

---

### Post by Randy Winchester on 2011-02-05
> **MattPurland said:**
> So it looks like The current release of the nVidia driver along with the automatically detected settings makes everything work out of the box!

Matt,

Which version of Nvidia driver is this?  Is it in the Ubuntu repository, or was it downloaded from Nvidia?

Cheers,
Randy

---

### Post by jasonofx on 2011-02-08
I installed Netbook Remix 10.10 on a TC1100 tonight, and I still haven't seen the Unity interface. Got the wireless working, have been updating, etc. How do i switch to the Unity interface if i want to? I got a message on first startup that i would need to type username:ubuntu with a password I forgot, but have just been using the original ubuntu desktop.

---

### Post by MattPurland on 2011-02-09
> **Randy Winchester said:**
> Matt,

Which version of Nvidia driver is this?  Is it in the Ubuntu repository, or was it downloaded from Nvidia?

Cheers,
Randy

I can't remember off the top of my head (I'm at work) - I'm pretty sure it's the latest version. You'll need to allow the nvidia-config tool to create your xorg.conf

---

### Post by MattPurland on 2011-02-09
> **jasonofx said:**
> I installed Netbook Remix 10.10 on a TC1100 tonight, and I still haven't seen the Unity interface. Got the wireless working, have been updating, etc. How do i switch to the Unity interface if i want to? I got a message on first startup that i would need to type username:ubuntu with a password I forgot, but have just been using the original ubuntu desktop.

Unity doesn't work at the moment as it doesn't use Compiz (even though it should still work, there's a bug when using on the TC1100) but will work in the next version of Ubuntu (I found this out the hard way too :()

---

### Post by DannyBiker on 2011-03-03
Anyone tested the latest 11.04 to see if it's working ?

---

### Post by DannyBiker on 2011-03-10
OR : does someone have a fix to make the pen work on JoliCloud OS ?

---

### Post by jasonofx on 2011-03-19
Anybody know if the wireless card in the TC1100 works with WPA in linux? I have a TC1100 and a TC1000, and the wireless works with WPA in Windows on both. However, the wireless on the TC1000 doesn't seem to work with WPA in linux, a driver issue. I'm asking because I'm keeping the TC1100 with Windows installed on it, but I'm putting Ubuntu 9.10 Netbook on the TC1000, and if the WPA works with the different model wireless card that's in the TC1100, I'll order one for the TC1000. (Confusing enough?) :)

Edit: Guess I could just USB boot the TC1100 and see if the WPA works. Answers are still very welcome, though.

---

### Post by MyR on 2011-03-20
> **jasonofx said:**
> Anybody know if the wireless card in the TC1100 works with WPA in linux? I have a TC1100 and a TC1000, and the wireless works with WPA in Windows on both. However, the wireless on the TC1000 doesn't seem to work with WPA in linux, a driver issue. I'm asking because I'm keeping the TC1100 with Windows installed on it, but I'm putting Ubuntu 9.10 Netbook on the TC1000, and if the WPA works with the different model wireless card that's in the TC1100, I'll order one for the TC1000. (Confusing enough?) :)

Edit: Guess I could just USB boot the TC1100 and see if the WPA works. Answers are still very welcome, though.

I'm not sure all have the same wireless card.  However the one I have (Intel Pro Wireless 2200 if I recall correctly) works fine with WPA.

---

### Post by Aearenda on 2011-03-20
The wireless card that came with my TC1000 would not do WPA with Windows XP either! My TC1100 has an Atheros card which does work with WPA.

---

### Post by internetauto on 2011-03-21
Ok a little help please.
I just installed 10.04 yesterday.  Originally it was working ok, but no wireless network.  Now it has no network at all!  only changes I did were to install GOK, Device manager, and KPackageKit.

can someone help please.
I also want to get rid of the password on wake up feature. hard to use when you don't have a keyboard attached :-/

---

### Post by Randy Winchester on 2011-03-21
> **internetauto said:**
> Ok a little help please.
I just installed 10.04 yesterday.  Originally it was working ok, but no wireless network.  Now it has no network at all!  only changes I did were to install GOK, Device manager, and KPackageKit.

can someone help please.
I also want to get rid of the password on wake up feature. hard to use when you don't have a keyboard attached :-/

See this [http://ubuntuforums.org/showpost.php?p=10059913&postcount=453](http://ubuntuforums.org/showpost.php?p=10059913&postcount=453)  and maybe a few messages in the thread before it.

To get rid of the password, uncheck "Lock screen when screensaver is active" in screensaver preferences.

---

### Post by internetauto on 2011-03-21
> **Randy Winchester said:**
> See this [http://ubuntuforums.org/showpost.php?p=10059913&postcount=453](http://ubuntuforums.org/showpost.php?p=10059913&postcount=453)  and maybe a few messages in the thread before it.

To get rid of the password, uncheck "Lock screen when screensaver is active" in screensaver preferences.

tried that and got an error of no such file or directory :-{ 
I have the intelpro wireless from the factory (AFAIK).

I'm still baffled as to why I lost my hardwire connection.  Though wireless is the one I really need.

Looks like the screen saver lock worked.
Thank you

---

### Post by internetauto on 2011-03-21
ok, dug a little deeper and found 2 settings for wifi in the bios.  1 to show that the card exists and the 2nd to activate the transceiver part.  the transceiver was turned off on mine.  turned it back on and we were good.

---

### Post by internetauto on 2011-03-22
next "problem", I can't figure out how to get the screen to rotate.  I tried the steps from [here ]("http://linuxdeal.com/how-to-ubuntu-10.04-hp-tc1100")on how to do it, but it isn't working as far as I can tell.

---

### Post by MyR on 2011-03-22
> **internetauto said:**
> next "problem", I can't figure out how to get the screen to rotate.  I tried the steps from [here ]("http://linuxdeal.com/how-to-ubuntu-10.04-hp-tc1100")on how to do it, but it isn't working as far as I can tell.

I did post an updated rotate script for maverick: [http://linuxdeal.com/how-to-ubuntu-10.10-hp-tc1100](http://linuxdeal.com/how-to-ubuntu-10.10-hp-tc1100) 

BTW If anyone wants to help me out you can submit your [linux printer review]("http://linuxdeal.com/add-printer.php").  (Please please please!!) I want to make an all-Linux-compatible printer store.

---

### Post by internetauto on 2011-03-23
> **MyR said:**
> I did post an updated rotate script for maverick: [http://linuxdeal.com/how-to-ubuntu-10.10-hp-tc1100](http://linuxdeal.com/how-to-ubuntu-10.10-hp-tc1100) 

BTW If anyone wants to help me out you can submit your [linux printer review]("http://linuxdeal.com/add-printer.php").  (Please please please!!) I want to make an all-Linux-compatible printer store.

actually I was trying to use the tablet rotate button on the face, not the physical button on the side.  that was what I did wrong](*,) 

I'm not much help on the linux printer deal as I use HP printers exclusively through IP so not a good test.

---

### Post by Graham1 on 2011-04-19
> **jasonofx said:**
> Anybody know if the wireless card in the TC1100 works with WPA in linux? I have a TC1100 and a TC1000, and the wireless works with WPA in Windows on both. However, the wireless on the TC1000 doesn't seem to work with WPA in linux, a driver issue. I'm asking because I'm keeping the TC1100 with Windows installed on it, but I'm putting Ubuntu 9.10 Netbook on the TC1000, and if the WPA works with the different model wireless card that's in the TC1100, I'll order one for the TC1000. (Confusing enough?) :)

Edit: Guess I could just USB boot the TC1100 and see if the WPA works. Answers are still very welcome, though.

Wireless works fine with WPA/WPA2 on 10.10 and 11.04 (beta 2) on my TC1100.

:)

---

### Post by Randy Winchester on 2011-05-01
> **Graham1 said:**
> Wireless works fine with WPA/WPA2 on 10.10 and 11.04 (beta 2) on my TC1100.

:)

Hi Graham,

Were you able to get Unity working with your TC1100?  Is there a trick?  I saw a window on first boot that claimed that video hardware was insufficient to run it, so it started up in classic mode.  I can't get Compiz to start anymore and the upgrade removed Avant Window Manager.  Also discovered there's a known bug with bluetooth not working correctly in 11.04.  If you have any pointers on getting Unity going, I'd like to give it a try.

Thanks,
R

---

### Post by Graham1 on 2011-05-01
> **Randy Winchester said:**
> Hi Graham,
Were you able to get Unity working with your TC1100?  Is there a trick?  I saw a window on first boot that claimed that video hardware was insufficient to run it, so it started up in classic mode.  I can't get Compiz to start anymore and the upgrade removed Avant Window Manager.  Also discovered there's a known bug with bluetooth not working correctly in 11.04.  If you have any pointers on getting Unity going, I'd like to give it a try.

Thanks,
R

Hi Randy

Unfortunately, not Unity 3D (TC1100's use openGL 1.2 and not the required 1.4). However, Unity 2D is working fine (as it did in 10.10 also) having added the PPA manually. I haven't noticed any problems with Unity 2D yet but I guess it's still early days. Thanks for the info about bluetooth, I have tried this yet.

If your interested in Gnome 3, I've tried both openSUSE and Fedora live CD's on the TC1100's but had problems with both. openSUSE's display and graphics were messed up and Fedora wouldn't load to the desktop.

I guess the TC1100's are showing there age (graphically) now. 

:)

---

### Post by Blasphemist on 2011-05-01
> **Graham1 said:**
> Hi Randy

Unfortunately, not Unity 3D (TC1100's use openGL 1.2 and not the required 1.4). However, Unity 2D is working fine (as it did in 10.10 also) having added the PPA manually. I haven't noticed any problems with Unity 2D yet but I guess it's still early days. Thanks for the info about bluetooth, I have tried this yet.

If your interested in Gnome 3, I've tried both openSUSE and Fedora live CD's on the TC1100's but had problems with both. openSUSE's display and graphics were messed up and Fedora wouldn't load to the desktop.

I guess the TC1100's are showing there age (graphically) now. 

:)

Running this might give you some more information.


```
jim@jim-Satellite-L505:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20100330 DEVELOPMENT x86/MMX/SSE2
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes
```

---

### Post by Graham1 on 2011-05-01
> **Blasphemist said:**
> Running this might give you some more information.

Hi Jim

My TC1100 displays the following:-

graham@tablet:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Nouveau
OpenGL renderer string: Mesa DRI nv17 20091015 x86/MMX/SSE2
OpenGL version string:  1.2 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        no
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity supported:          no

:)

---

### Post by Blasphemist on 2011-05-01
From this document

[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

The Open GL version needs to be 1.4 or higher and the proprietary nvidia drivers are recommended for you.

> What drivers do you recommend?
AMD GPUs:

Fglrx driver: We have had some issues with the fglrx driver but we have been able to resolve them. With the fglrx driver, you will be missing features such as Kernel Mode Setting (KMS).
Open Source Radeon driver: can exhibit rendering artifacts on some systems. In the "System 3" configuration, Unity is not usable due to serious rendering issues.
NVidia GPUs: Nvidia propietary drivers.
Intel GPUs: Intel open source drivers.

---

### Post by Randy Winchester on 2011-05-01
> **Blasphemist said:**
> Running this might give you some more information.

The Nvidia 96 driver that we had to wait for to be able to run Compiz in 10.10 can not be installed in 11.04.  Because of this, it doesn't appear that we can run Compiz in 11.04.

---

### Post by Blasphemist on 2011-05-02
> **Randy Winchester said:**
> The Nvidia 96 driver that we had to wait for to be able to run Compiz in 10.10 can not be installed in 11.04.  Because of this, it doesn't appear that we can run Compiz in 11.04.

Is this what you are referring to?
[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/96.43.19-0ubuntu8](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/96.43.19-0ubuntu8)

This may well be above my pay grade but, can this be installed?

---

### Post by MyR on 2011-05-02
> **Blasphemist said:**
> Is this what you are referring to?
[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/96.43.19-0ubuntu8](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/96.43.19-0ubuntu8)

This may well be above my pay grade but, can this be installed?

you get paid for this? sign me up!

---

### Post by Graham1 on 2011-05-03
> **Blasphemist said:**
> Is this what you are referring to?
[https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/96.43.19-0ubuntu8](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/96.43.19-0ubuntu8)

This may well be above my pay grade but, can this be installed?

I tried installing these drivers yesterday but the installation fails :(. Noticed that you have a different graphics chipset in your TC1100. Is this 32MB or more? From the link you provided (other post), it seems Unity 3D requires 128MB so 3D is out of the question for me.

:)

---

### Post by MyR on 2011-05-03
I installed the nvidia-96 package two different ways (one where I installed enough dependicies so it would install, and another where I forced it) but then Ubuntu no longer boots.

Looks like 3D is hopeless on 11.04 for now.

Here's what I have so far: [http://linuxdeal.com/how-to-ubuntu-11.04-hp-tc1100](http://linuxdeal.com/how-to-ubuntu-11.04-hp-tc1100)

---

### Post by DannyBiker on 2011-05-04
Pointless post only to say that there are still people wanting to get Unity to run nicely on the HP TC1100 as well as all the features of the device.
So thanks to you all trying. I would help if I could understand anything...:/

---

### Post by Randy Winchester on 2011-05-05
> **MyR said:**
> I installed the nvidia-96 package two different ways (one where I installed enough dependicies so it would install, and another where I forced it) but then Ubuntu no longer boots.

Looks like 3D is hopeless on 11.04 for now.

Here's what I have so far: [http://linuxdeal.com/how-to-ubuntu-11.04-hp-tc1100](http://linuxdeal.com/how-to-ubuntu-11.04-hp-tc1100)

Thanks!

I tried installing the NVidia 96 a few different ways, and it just plain won't work.  After trying just about everything it appears to be by design, as if the driver is blacklisted.

Also, I noticed on your web guide that you say suspend is working correctly.   Actually, suspend is one of the features that no longer works on my machine following the upgrade.  Bluetooth is also broken.  I can live without 3d and Bluetooth, but I really miss suspend.  Any ideas about how to troubleshoot this?

Cheers,
Randy

---

### Post by wilfried1 on 2011-05-05
Thanks for all tips and viewpoints here. Very useful to me. Thanks

---

### Post by MyR on 2011-05-07
> **Randy Winchester said:**
> Also, I noticed on your web guide that you say suspend is working correctly.   Actually, suspend is one of the features that no longer works on my machine following the upgrade.  Bluetooth is also broken.  I can live without 3d and Bluetooth, but I really miss suspend.  Any ideas about how to troubleshoot this?

I installed fresh (no upgrade) and suspend just worked.  In previous versions we installed some scripts that ran before/after suspend to fix the stylus or turn wireless back on.  It is possible that these scripts are causing trouble now; see if you can remove them.  Beyond that there may be some specific log files you can look at, but I'm not really sure which ones.  This is why I do a fresh install for each new version.

Bluetooth is on and looks all right but I haven't tested it.

If all else fails and you need suspend, just reinstall.

------------

Developers have confirmed that there is no working nvidia-96 driver for 11.04.  They are working on it, so it should be released at some point.  About one to two months if I had to guess.  Let's hope unity will work after that.

I re-submitted a patch for the stylus buttons (see the launchpad link at the bottom of my [guide]("http://linuxdeal.com/how-to-ubuntu-11.04-hp-tc1100")).  It doesn't quite work now but it's a good start.  Please try to get it working if you have that C programming skill ;]

peace

---

### Post by josemasaga on 2011-06-02
Hi!
Thank you all for this thread. I've been using tc1100s for some years now and I keep coming back to this thread for advise. :)
Yesterday I installed ubuntu 11.04 on my latest tc1100 (I'm a kind of an addict), I followed all the tutorials I could find and dug in the forums, but unfortunately I can't activate the wifi card (I've tried from the BIOS, it says that it is ON) and when I rotate the screen, it all becomes blurry and I have to go back to landscape...
Any ideas...?
Thank you very much!!!

---

### Post by MyR on 2011-06-02
> **josemasaga said:**
> I followed all the tutorials I could find
I assume you looked at my [11.04 guide]("http://linuxdeal.com/how-to-ubuntu-11.04-hp-tc1100") then?
> **josemasaga said:**
> and dug in the forums, but unfortunately I can't activate the wifi card (I've tried from the BIOS, it says that it is ON)
I just added a command to the guide. See if that works for you.

> **josemasaga said:**
> and when I rotate the screen, it all becomes blurry and I have to go back to landscape...
Any ideas...?
Thank you very much!!!
Did you set the desktop session as Ubuntu classic (no effects)?

---

### Post by Blasphemist on 2011-06-02
> **MyR said:**
> I assume you looked at my [11.04 guide]("http://linuxdeal.com/how-to-ubuntu-11.04-hp-tc1100") then?

I just added a command to the guide. See if that works for you.


Did you set the desktop session as Ubuntu classic (no effects)?

I like your site and can see it getting better and better! Good work! I am curious though about why your guide doesn't mention using unity 2D?

---

### Post by josemasaga on 2011-06-02
Thank you very much for the super-fast reply!!!

> **MyR said:**
> I assume you looked at my [11.04 guide]("http://linuxdeal.com/how-to-ubuntu-11.04-hp-tc1100") then?

Yes! It's like the bible for me. ;)

> **MyR said:**
> I just added a command to the guide. See if that works for you.

The BIOS shows the wireless as activated. I'm afraid that the command didn't activate it... :(


> **MyR said:**
> Did you set the desktop session as Ubuntu classic (no effects)?

Yep, and it did wonders!! Thank you!!

What could I do with the wireless? Should I reinstall Ubuntu?

---

### Post by MyR on 2011-06-02
> **Blasphemist said:**
> I like your site and can see it getting better and better! Good work! I am curious though about why your guide doesn't mention using unity 2D?

Thanks! I've been developing it from scratch since November; still not getting much traffic though (1300/month).
The truth is I rarely use my TC1100 and I run 10.04 on my primary system, so I've never used Unity. What would I mention about it?  Screen rotation and cellwriter were both having problems before I switched to Ubuntu classic no effects.
> **josemasaga said:**
> The BIOS shows the wireless as activated. I'm afraid that the command didn't activate it... :(
OK I fired up my TC1100 to test the command.  You need to enter the command as root (and not sudo).  I updated my guide to reflect this. "sudo su" will switch to root. I presume su stands for switch user. If this command doesn't work then I don't know what's wrong with it.  Paste the terminal output from the echo command.

Random tip: "sudo !!" will add sudo to the last command you entered.

---

### Post by Blasphemist on 2011-06-03
> **MyR said:**
> Thanks! I've been developing it from scratch since November; still not getting much traffic though (1300/month).
The truth is I rarely use my TC1100 and I run 10.04 on my primary system, so I've never used Unity. What would I mention about it?  Screen rotation and cellwriter were both having problems before I switched to Ubuntu classic no effects.

OK I fired up my TC1100 to test the command.  You need to enter the command as root (and not sudo).  I updated my guide to reflect this. "sudo su" will switch to root. I presume su stands for switch user. If this command doesn't work then I don't know what's wrong with it.  Paste the terminal output from the echo command.

Random tip: "sudo !!" will add sudo to the last command you entered.

This is a link to an explanation of the purpose of unity 2D, how to install it and a demo video.
[http://www.ubuntugeek.com/install-ubuntu-unity-2d-using-ppa-in-ubuntu-11-0410-10.html](http://www.ubuntugeek.com/install-ubuntu-unity-2d-using-ppa-in-ubuntu-11-0410-10.html)

I run unity 3D but I've seen quite a few posts from users quite happy with unity 2D.

---

### Post by MyR on 2011-06-03
> **Blasphemist said:**
> This is a link to an explanation of the purpose of unity 2D, how to install it and a demo video.
[http://www.ubuntugeek.com/install-ubuntu-unity-2d-using-ppa-in-ubuntu-11-0410-10.html](http://www.ubuntugeek.com/install-ubuntu-unity-2d-using-ppa-in-ubuntu-11-0410-10.html)

I run unity 3D but I've seen quite a few posts from users quite happy with unity 2D.

All righty. I added the installation instructions. Thanks

---

### Post by josemasaga on 2011-06-05
> **MyR said:**
> If this command doesn't work then I don't know what's wrong with it.  Paste the terminal output from the echo command.

Thank you for everything!

I've tried nearly everything; I've installed other versions of ubuntu to no avail. I even went back to windows xp just to be sure that the wireless card worked. It does work on windows xp.

The terminal, by the way, doesn't give any output after entering the command, but when I try to close, it says that that there's a process running...

---

### Post by MyR on 2011-06-05
> **josemasaga said:**
> I've tried nearly everything; I've installed other versions of ubuntu to no avail....

The terminal, by the way, doesn't give any output after entering the command, but when I try to close, it says that that there's a process running...The "process" running was the root user being logged in.

These commands might give some hints to what's amiss:
lspci - should see if Linux is detecting your wireless card and what model it is)
ifconfig - lists all network interfaces
iwconfig - lists all wireless network interfaces

---

### Post by Blasphemist on 2011-06-05
> **josemasaga said:**
> Thank you for everything!

I've tried nearly everything; I've installed other versions of ubuntu to no avail. I even went back to windows xp just to be sure that the wireless card worked. It does work on windows xp.

The terminal, by the way, doesn't give any output after entering the command, but when I try to close, it says that that there's a process running...
I'm no wireless expert but I have had issues of my own on an old thinkpad with an ancient atheros wireless card. I found these good resources for wireless troubleshooting.
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)
This is quite comprehensive but if you need help at some point in this troubleshooting, don't hesitate to ask and use what you've found to provide detail.

---

### Post by josemasaga on 2011-06-05
> **MyR said:**
> lspci - should see if Linux is detecting your wireless card and what model it is

Yep, it is a "Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)"

> **MyR said:**
> iwconfig - lists all wireless network interfaces

This is what I got...

"lo         no wireless extensions.

eth0     no wireless extensions.

wlan0   IEEE 802.bg   ESSID: off/any
           Mode:Managed   Access Point: Not-Associated    TX-Power=0 dBm
           Retry   long limit:7     RTS  thr: off      Fragment thr: off
           Encryption key: off
           Power Mangament: off"

????

---

### Post by Randy Winchester on 2011-07-26
Hi Jose,

Please see message 453 on page 46 of this thread.  That will probably fix your wireless problem.

Cheers,
Randy

---

### Post by evilflame2 on 2011-10-07
Does 3d still not work? 
can someone translate the bug tracker for me
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/741930](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/741930)

---

### Post by MyR on 2011-10-07
> **evilflame2 said:**
> Does 3d still not work? 
can someone translate the bug tracker for me
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/741930](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/+bug/741930)

No, 3d doesn't work with the lastest ubuntu. They're still working on a nvidia driver. Older versions of ubuntu work fine though.

This is the problem with proprietary computer hardware -- support goes away.

---

### Post by EvilKeg on 2011-12-04
I've followed the instructions on Linux Deal but I'm having issues with the screen rotate commands. It doesnt appear to work and I cant work out why. I tried calling it from the command line and got this:

HP-Tablet-PC-Tx1100:~$ xrandr -o left
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  153 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  14
  Current serial number in output stream:  14

I've also tried to do the rotate command from the control panel but it's not got an option to rotate there.

Have I not installed something correctly on my TC1100?

---

### Post by Favux on 2011-12-04
Hi EvilKeg,

If it is a Nvidia video chipset:
```
lspci | grep VGA
```
and you are using the proprietary driver, you need rotation enabled in the xorg.conf with:
```
Option "RandRRotation" "on"
```
See appendix 1 in the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1").

---

### Post by EvilKeg on 2011-12-04
100% working now!

i love ubuntu!

---

### Post by MyR on 2011-12-04
> **EvilKeg said:**
> 100% working now!

i love ubuntu!

What version of Ubuntu did you install?

---

### Post by Musashi328 on 2011-12-20
UPDATE:::Fixed found I had to update the xf86-input-wacom driver per the launchpad instructions and it didn't take the first time. Had to use the autogen.sh method. So it now works properly.

Hello all from sunny Florida!!! Had a quick question I have everything working with the rotate script found earlier in this post. It is bound to a key and rotates but the stylus doesn't move. I can type the xsetwacom command after I rotate the screen (the same command that is in the script) and it rotates the stylus but it will not do it with the script. I know it has to be something easy I am missing but can't quite figure it out. The script is:

```
#!/bin/sh
if [ -n "$(xrandr | grep 768x1024)" ]; then
        xrandr -o normal
        xsetwacom set "Serial Wacom Tablet stylus" rotate NONE
else
        xrandr -o left
        xsetwacom set "Serial Wacom Tablet stylus" rotate cw
fi

```

TIA
Jason

---

### Post by chrisoffice on 2012-01-30
MyR,

Can you please post an instruction on how to fix issues when installing Ubuntu 11.10 on TC1100?  I installed it, but the tablet had problem waking up from suspension (blank screen), and I don't know how to assign keys under this version of Ubuntu to rotate, and control brightness, etc.

Thanks!

---

### Post by MyR on 2012-01-31
> **chrisoffice said:**
> MyR,

Can you please post an instruction on how to fix issues when installing Ubuntu 11.10 on TC1100?  I installed it, but the tablet had problem waking up from suspension (blank screen), and I don't know how to assign keys under this version of Ubuntu to rotate, and control brightness, etc.

Thanks!

I loaned my tablet to someone, so I don't have it available right now. Sorry...

---

### Post by kayarevii on 2012-02-05
Ok I got Xubuntu Oneiric successfully installed on my TC1100 (1 ghz Pentium M) runs nice and cool, I got rotate to work using the script at the beginning of this page. Note that the proprietary Nvidia drivers (Nvidia 96) are already installed and work out of the box in (X)ubuntu 11.10 so you have to edit your xorg.conf to use XRandR for the rotate script to work.

```

Section "Screen"
	Identifier	"Default Screen"
	Option	"AddARGBGLXVisuals"	"True"
EndSection

Section "Device"
	Identifier	"Default Device"
	    Option      "RandRRotation"    "True"
EndSection

```

I also got the screen brightness adjustable using this script

```

#!/usr/bin/env bash

if [[ ! -f /sys/devices/platform/tc1100-wmi/jogdial ]]; then
   zenity --info --text="This kernel does not have TC1100 WMI support."
   exit 1
fi

echo 0 > /sys/devices/platform/tc1100-wmi/jogdial
zenity --info --text="Use the jog dial to adjust the brightness. Press OK when done."
echo 1 > /sys/devices/platform/tc1100-wmi/jogdial

exit 0

```

then ```

sudo chmod +x /usr/bin/bright

```

The only problem with this is that you have to use sudo or gksu to make the script work :confused:

also suspend and hibernate are broken (blank screen), and I can't get an on screen keyboard on the startup screen:confused:

---

### Post by jjaythomas on 2012-04-30
What is the simplest way to get the plymouth splash back in 12.04?

Use to use startup-manager to change display size few versions back, but now package depreciated:mad: 

Tried both Lubuntu and Xubuntu 12.04 (I would think bad in Ubuntu also) get no splash (only words)

J.Jay

---

### Post by jjaythomas on 2012-06-09
P.S. Their a brightness script (post #385 here) that worked a 11.04 (11.10 I think also)
   not sure if 12.04.

J.Jay

---

