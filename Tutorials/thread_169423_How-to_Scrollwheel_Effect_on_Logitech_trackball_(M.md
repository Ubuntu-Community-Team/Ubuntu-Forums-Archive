---
title: "How-to Scrollwheel Effect on Logitech trackball (Marble Mouse)"
date: 2006-03-13
forum: Tutorials
---

### Post by Buffalo Soldier on 2006-03-13
_**End Result**_
Using trackball to emulate wheel button scroll (horizontal & vertical) in web browser (Epiphany 2.14.0 and Firefox 1.5.0.1).

_**Method**_

[list=1]
[*] Open *xorg.conf* file using a text editor (gedit). Go to Applications -> Accessories -> Terminal and enter command:```
sudo gedit /etc/X11/xorg.conf
```

[*] Look for a section that contains the entry for your mouse, it looks kind of like this.
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```

[*] Edit that section into this:
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"Buttons"		"9"
	Option		"EmulateWheel"		"1"
	Option		"EmulateWheelButton"	"8"	# for right-handed people
	Option		"YAxisMapping"		"4 5" 
	Option		"XAxisMapping"		"6 7" 
EndSection 
```

[*] For left-handed people. Use this:
```
Option		"EmulateWheelButton"	"**9**"	# for left-handed people
```

[*] Go to Epiphany / Firefox address bar and type:```
about:config
```

[*] Filter for the word *scroll* and look for these lines:```

mousewheel.horizscroll.withnokey.action		default		integer	**[color=red]2**[/color]
mousewheel.horizscroll.withnokey.sysnumlines	default		boelean	**[color=red]false**[/color]

```

[*] Change the **[color=red]default value[/color]** into **[color=blue]new value[/color]**:```

mousewheel.horizscroll.withnokey.action		user set	integer	**[color=blue]0**[/color]
mousewheel.horizscroll.withnokey.sysnumlines	user set	boelean	**[color=blue]true**[/color]
```
[/list]

Step 

_**References:**_

a. [Xorg user documentation](http://ftp.x.org/pub/X11R7.0/doc/html/mouse.4.html)
> 
**Option** "**Buttons**" "*integer*"
Specifies the number of mouse buttons. In cases where the number of buttons cannot be auto-detected, the default value is 3. The maximum number is 24.

**Option** "**Emulate3Buttons**" "*boolean*"
Enable/disable the emulation of the third (middle) mouse button for mice which only have two physical buttons. The third button is emulated by pressing both buttons simultaneously. Default: off

**Option** "**EmulateWheel**" "*boolean*"
Enable/disable "wheel" emulation. Wheel emulation means emulating button press/release events when the mouse is moved while a specific real button is pressed. Wheel button events (typically buttons 4 and 5) are usually used for scrolling. Wheel emulation is useful for getting wheel-like behaviour with trackballs. It can also be useful for mice with 4 or more buttons but no wheel. See the description of the EmulateWheelButton, EmulateWheelInertia, XAxisMapping, and YAxisMapping options below. Default: off.

**Option** "**EmulateWheelButton**" "*integer*"
Specifies which button must be held down to enable wheel emulation mode. While this button is down, X and/or Y pointer movement will generate button press/release events as specified for the XAxisMapping and YAxisMapping settings. Default: 4.

**Option** "**XAxisMapping**" "*N1 N2*"
Specifies which buttons are mapped to motion in the X direction in wheel emulation mode. Button number N1 is mapped to the negative X axis motion and button number N2 is mapped to the positive X axis motion. Default: no mapping.
 
**Option **"**YAxisMapping**" "*N1 N2*"
Specifies which buttons are mapped to motion in the Y direction in wheel emulation mode. Button number N1 is mapped to the negative Y axis motion and button number N2 is mapped to the positive Y axis motion. Default: "4 5".

b. [mozillaZine](http://kb.mozillazine.org/About:config_entries#Mousewheel..2A)
> 
_Mousewheel.*_

These fall into two groups, vertical and horizontal scroll. The general form is:[list]
[*] mousewheel.(modifier key).(type)
[*] mousewheel.horizscroll.(modifier key).(type)[/list]

Type is then one of:
**action**
integer value that determines the type of action:[list]
[*] 0 - Scroll document by a number of lines (given by the numlines property)
[*] 1 - Scroll document by one page
[*] 2 - Move back/forward in history
[*] 3 - Make text larger/smaller[/list]

**numlines **
number of lines to scroll by (if relevant) 

**sysnumlines**
use system preferences to determine how many lines to scroll by 


---

### Post by mstlyevil on 2006-05-02
I moved this here since I keep getting request how to set up the scroll wheel effect. Hope you do not mind BuffaloSoldier. This is a great how to btw. :mrgreen:

---

### Post by jonthysell on 2006-05-17
Finally, now I can use my favorite mouse!

Although I changed the order of the YAxis mapping, made more sense to me (matches the arrows).

---

### Post by wh0rd on 2006-07-20
Hey, how's it going guys. Well I've got the same exact trackball, but scrollers aren't working under Kubuntu Dapper Drake. I've got the mouse connected to my laptop with the USB interface. **xev** shows the **Up(left small)** button as **8** and **Down(right small)** button as **9**. The **left-click(left large)** button as **1** and the **right-click(right large)** button as **3**.

---

### Post by asplode on 2006-07-22
This worked for me, although not like I expected it to.  Instead of the down button scrolling down, and the up button scrolling up, neither do the original intended action. 

Instead, I must press the down button and then scroll the trackball up or down to scroll.  But still... this is much better than having to move over the the scroll bar.

---

### Post by ace2005 on 2006-07-22
This kind of mouse?

[http://pc.itek.cz/k_464-Multimedia-Mysi/img-shop/full/610206.jpg](http://pc.itek.cz/k_464-Multimedia-Mysi/img-shop/full/610206.jpg)

This is what i use and what is the scrolling effect?

I'm confused

---

### Post by Buffalo Soldier on 2006-07-22
This is the [Marble Mouse](http://www.logitech.com/index.cfm/products/details/US/EN,CRID=2150,CONTENTID=5003) that I used. I just attached a picture to the howto.

---

### Post by asplode on 2006-07-22
How it works on mine is you hold the left scroll button down, and then move the trackball around.  It actually turns out to be extremely handy for sidescrolling in documents.  Much easier than any other way I know of.

---

### Post by incubus on 2006-07-24
I always wanted to try a trackball and since my microsoft mouse broke (evil smile), I replaced it for this Logitech Marble.

Thank you for setting up this How-to, I got it working wonderfully and with this scroll thing, now I feel reading documents is much better.

Just to share my tweak, I set the wheel scroll button to number 3, yes the same as the right click, instead of number 8. It feels more natural to me. So far I didn't notice anything bad with that, since I don't drag and drop anything with the right button.

Also, I set the middle button to be number 8, the small one on the left. Now I can open/close tabs and paste texts as in a traditional mouse. I did that through an xmodmap file:

pointer = 1 8 3 4 5 6 7 2 9 10 11 12 13

Good job, folks.

incubus

---

### Post by wh0rd on 2006-07-26
Okay I fixed it. Apparently the Howto was for **PS/2 **interface mice only. What I had to do was comment out the PS/2 configs and use **USB Mouse** as the **InputDevice**:
This is for those of us who use USB and not PS/2 for [Logitech Marble Mouse]("http://www.logitech.com/index.cfm/products/details/US/EN,CRID=2150,CONTENTID=5003")

Add this to the top of you **xorg.conf** file:

```
InputDevice "USB Mouse" "CorePointer"
```

Then add this section (it's exactly the same as Buffalo Soldier's Howto, except for the **Identifier** which is **"USB Mouse"** and **CorePointer** is defined above):

```
Section "InputDevice"
  Identifier "USB Mouse"
  Driver "mouse"
  Option "Device" 		"/dev/input/mice"
  Option "Protocol" 		"ExplorerPS/2"
  Option "Emulate3Buttons"	"true"
  Option "Buttons"		"9"
  Option "EmulateWheel"		"1"
  Option "EmulateWheelButton"	"8"
  Option "YAxisMapping"		"4 5" 
  Option "XAxisMapping"		"6 7" 
EndSection

```

If your trackball was detected as PS/2, make sure you comment it out. Then just restart X (CTRL+ALT+BACKSPACE)

A big THANK YOU to :KSBuffalo Soldier:KS !!!

---

### Post by Buffalo Soldier on 2006-07-28
Glad you find the howto usefull. Anyway, way trackball is connected using the USB port too and not PS/2. Perhaps I should include my whole xorg.conf file as reference.

---

### Post by wh0rd on 2006-07-28
Oh really. In that case posting your xorg.conf will be really helpful.

---

### Post by latuss on 2006-10-02
And how is the xorg.conf if the the trackball is in a laptop with touchpad?
thks

---

### Post by wh0rd on 2006-12-02
Hi I was wondering how can I go about making the following configuration:
- 2 (which is the larger two buttons held together) for scrolling
- 8 and 9 Back/Forward (Firefox Browser)

---

### Post by jonboy99 on 2007-01-02
Good howto.  The only problem is, if I carry out the about:config tweaks for firefox, then the two buttons on my microsoft trackball which had previously moved forward or back a page in the browsing history, have stopped working.

Anyway to have the ball to scroll but keep other buttons for forward and back?


Hmm, well, just changed the about:config settings back to default, and left the changes in xorg.conf as per the instructions, and forward, back and mousewheel emulation all work.  Good good..



:D  Just had to edit again - this is sweet..

---

### Post by PowerlessRacing on 2007-03-01
Great howto.  I also use a USB Marble Mouse but I didn't have to change anything from Buffalo Soldier's original post.  

I appreciate the howto, but now I'm left with a question.  I mapped 8 for my scrolling but 9 is still sitting there not doing anything.  How do I map 9 to perform the browser's 'back' function?

---

### Post by TheRingmaster on 2007-03-22
> **Buffalo Soldier said:**
> _**End Result**_
Using trackball to emulate wheel button scroll (horizontal & vertical) in web browser (Epiphany 2.14.0 and Firefox 1.5.0.1).

_**Method**_

Open *xorg.conf* file using a text editor (gedit). Go to Applications -> Accessories -> Terminal and enter command:```
sudo gedit /etc/X11/xorg.conf
```

Edit the section that contains the entry for your mouse.
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"Buttons"		"9"
	Option		"EmulateWheel"		"1"
	Option		"EmulateWheelButton"	"8"
	Option		"YAxisMapping"		"4 5" 
	Option		"XAxisMapping"		"6 7" 
EndSection

```
* For left-handed people. Use this:
```
Option		"EmulateWheelButton"	"**9**"
```

Go to Epiphany / Firefox address bar and type:```
about:config
```

Filter for the word *scroll* and look for these lines:```

mousewheel.horizscroll.withnokey.action		default		integer	**[color=red]2**[/color]
mousewheel.horizscroll.withnokey.sysnumlines	default		boelean	**[color=red]false**[/color]

```
Change the default [color=red]value[/color] into new [color=blue]values[/color]:```

mousewheel.horizscroll.withnokey.action		user set	integer	**[color=blue]0**[/color]
mousewheel.horizscroll.withnokey.sysnumlines	user set	boelean	**[color=blue]true**[/color]
```

_**References:**_

a. [Xorg user documentation](http://ftp.x.org/pub/X11R7.0/doc/html/mouse.4.html)


b. [mozillaZine](http://kb.mozillazine.org/About:config_entries#Mousewheel..2A)
Works Great

thanks!!

---

### Post by TheRingmaster on 2007-03-22
> **PowerlessRacing said:**
> Great howto.  I also use a USB Marble Mouse but I didn't have to change anything from Buffalo Soldier's original post.  

I appreciate the howto, but now I'm left with a question.  I mapped 8 for my scrolling but 9 is still sitting there not doing anything.  How do I map 9 to perform the browser's 'back' function?
well that button would "autoscroll", but you have it disabled in firefox.

---

### Post by Phrawm48 on 2007-05-04
Thanks to all who contributed to this thread.  I was able to use this information to *finally *get my Logitech Marble Mouse working in something other than "most basic" mode.  Having so done, I'll add the following brief observations.

Per *asplode*'s comment, below, scrolling works a bit differently than I'd expected.  For a right-handed user, pressing and holding the small left-side button allows one to pan (scroll on both the x and y axes).

I discovered I didn't need to reconfigure Firefox 2.0.0.2 to use this new panning behavior.    Moreover, I also discovered that when running Firefox 2, simultaneously clicking both the left and right-side large buttons displays a universal scrolling icon which I can then use to pan within the Firefox window.  Clicking any button returns Firefox to normal operation.

Finally, I'll mention in passing that scrolling or panning in Firefox wasn't (isn't) my biggest problem insofar as I've become quite fond of the *Grab and Drag* add-on (nee extension) available for both Firefox and Thunderbird.  See [https://addons.mozilla.org/en-US/firefox/addon/1250](https://addons.mozilla.org/en-US/firefox/addon/1250)

Cheers and thanks again to all,
Ric
SFO

---

### Post by TheRingmaster on 2007-05-05
> **Phrawm48 said:**
> Thanks to all who contributed to this thread.  I was able to use this information to *finally *get my Logitech Marble Mouse working in something other than "most basic" mode.  Having so done, I'll add the following brief observations.

Per *asplode*'s comment, below, scrolling works a bit differently than I'd expected.  For a right-handed user, pressing and holding the small left-side button allows one to pan (scroll on both the x and y axes).

I discovered I didn't need to reconfigure Firefox 2.0.0.2 to use this new panning behavior.    Moreover, I also discovered that when running Firefox 2, simultaneously clicking both the left and right-side large buttons displays a universal scrolling icon which I can then use to pan within the Firefox window.  Clicking any button returns Firefox to normal operation.

Finally, I'll mention in passing that scrolling or panning in Firefox wasn't (isn't) my biggest problem insofar as I've become quite fond of the *Grab and Drag* add-on (nee extension) available for both Firefox and Thunderbird.  See [https://addons.mozilla.org/en-US/firefox/addon/1250](https://addons.mozilla.org/en-US/firefox/addon/1250)

Cheers and thanks again to all,
Ric
SFO
that is a wonderful addon!

---

### Post by imjustabill on 2007-08-03
I just thought I'd share my xorg.conf. I've set it up so that the big left and right buttons work normally (click, right click) and pressing them at the same time acts as a middle click. Holding the small left button will let you scroll up and down with the trackball. Clicking small left and right buttons will let you go back/forward in firefox.

```

Section "InputDevice"
    Identifier "MarbleMouse"
    Driver     "mouse"
    Option     "Protocol" "auto"
    Option     "Device" "/dev/input/mice"
    Option     "Buttons" "5"
    Option     "ButtonMapping" "1 8 3 6 7"
    Option     "EmulateWheel"  "true"
    Option     "EmulateWheelTimeout" "300"  # msec
    Option     "EmulateWheelButton"  "6"
    Option     "YAxisMapping"        "4 5"
EndSection

```

Make sure that you have "MarbleMouse" under the server layout section as well. Hope someone finds this usefull!

---

### Post by ironblade on 2007-08-22
My config, set up to use right-handed, with buttons working as follows:
Big Left: normal left button
Small Left: "Button 3", ie does Pasting from clipboard
Small Right: Hold it and scroll the trackball (vertically only)
Big Right: normal right button

xorg.conf:
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "9"
        Option          "ZAxisMapping"          "4 5"
        Option          "EmulateWheel"          "1"
        Option          "EmulateWheelButton"    "9"
        Option          "Emulate3Buttons"       "true"
EndSection
```

In my ~/.kde/Autostart directory, I have a tiny shell script (trackball.sh) which runs this command:
```

/usr/bin/xmodmap -e "pointer = 1 8 3 4 5 6 7 2 9 10 11 12 13"
```

It's a bit odd to refer to 13 buttons when we just define 9, but hey, it works a treat!

---

### Post by orengolan on 2007-11-05
I use this configuration to scroll with the trackball + small left button:
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"Buttons"		"9"
	Option		"EmulateWheel"		"1"
	Option		"EmulateWheelButton"	"8"
	Option		"YAxisMapping"		"4 5" 
EndSection

```

I would like the small right button to behave the same (so I can scroll with trackball + small right button).
I tried this:
Option		"EmulateWheelButton"	"8 9"
and this:
Option		"EmulateWheelButton"	"8,9"
but it didn't work.

any ideas?

---

### Post by Lelek on 2007-11-10
> **imjustabill said:**
> I just thought I'd share my xorg.conf. I've set it up so that the big left and right buttons work normally (click, right click) and pressing them at the same time acts as a middle click. Holding the small left button will let you scroll up and down with the trackball. Clicking small left and right buttons will let you go back/forward in firefox.

```

Section "InputDevice"
    Identifier "MarbleMouse"
    Driver     "mouse"
    Option     "Protocol" "auto"
    Option     "Device" "/dev/input/mice"
    Option     "Buttons" "5"
    Option     "ButtonMapping" "1 8 3 6 7"
    Option     "EmulateWheel"  "true"
    Option     "EmulateWheelTimeout" "300"  # msec
    Option     "EmulateWheelButton"  "6"
    Option     "YAxisMapping"        "4 5"
EndSection

```

Make sure that you have "MarbleMouse" under the server layout section as well. Hope someone finds this usefull!


Report: 
Under ubuntu 7.10  this config works like a charm. Thx .

---

### Post by battlesound on 2007-11-14
> **imjustabill said:**
> I just thought I'd share my xorg.conf. I've set it up so that the big left and right buttons work normally (click, right click) and pressing them at the same time acts as a middle click. Holding the small left button will let you scroll up and down with the trackball. Clicking small left and right buttons will let you go back/forward in firefox.

```

Section "InputDevice"
    Identifier "MarbleMouse"
    Driver     "mouse"
    Option     "Protocol" "auto"
    Option     "Device" "/dev/input/mice"
    Option     "Buttons" "5"
    Option     "ButtonMapping" "1 8 3 6 7"
    Option     "EmulateWheel"  "true"
    Option     "EmulateWheelTimeout" "300"  # msec
    Option     "EmulateWheelButton"  "6"
    Option     "YAxisMapping"        "4 5"
EndSection

```

Make sure that you have "MarbleMouse" under the server layout section as well. Hope someone finds this usefull!


Nice job.  I found this useful.  Works perfectly in Gutsy.  

I think this is the best way to set up the mouse.  I wonder if we could still get the mouse to scroll ANY direction, though.  Also, can we set it up to go back/forward in nautilus?  I'm so happy with the Marble"mouse".  Thanks.

---

### Post by irish_flu on 2007-11-20
Just needed to rebuild a workstation from scratch, and forgot to save my xorg.conf file.  Oops!

Fortunately, I could still find this thread.  I'm even a lefty, so Buffalo Soldier's original post works great for me!

I haven't needed to worry about saving my mouse config since Dapper; thanks again Buffalo!

---

### Post by orengolan on 2007-11-23
I set my xorg so button 3 (big right) is my scroll effect.
I want to make the small left (and if possible also the mall right) the paste button.
I try to change the ButtonMapping to 1 8 3 4 5 6 7 2 9  but it didn't help.

any ideas?

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"Buttons"		"9"
	Option     	"ButtonMapping" 	"1 8 3 4 5 6 7 2 9"
	Option		"EmulateWheel"		"1"
	Option		"EmulateWheelButton"	"3"
	Option		"YAxisMapping"		"4 5" 
EndSection

---

### Post by Riccisayer@tiscali.fr on 2008-01-12
Hi guys, I missed something here, where does one put these magic codes. I don't do enough of this sort of thing, so I just don't know?

---

### Post by bthessel on 2008-01-12
> **imjustabill said:**
> I just thought I'd share my xorg.conf. I've set it up so that the big left and right buttons work normally (click, right click) and pressing them at the same time acts as a middle click. Holding the small left button will let you scroll up and down with the trackball. Clicking small left and right buttons will let you go back/forward in firefox.

```

Section "InputDevice"
    Identifier "MarbleMouse"
    Driver     "mouse"
    Option     "Protocol" "auto"
    Option     "Device" "/dev/input/mice"
    Option     "Buttons" "5"
    Option     "ButtonMapping" "1 8 3 6 7"
    Option     "EmulateWheel"  "true"
    Option     "EmulateWheelTimeout" "300"  # msec
    Option     "EmulateWheelButton"  "6"
    Option     "YAxisMapping"        "4 5"
EndSection

```

Make sure that you have "MarbleMouse" under the server layout section as well. Hope someone finds this usefull!

Just tried this and nothing seems to be happening. Attached is my xorg.conf any help is appreciated.

---

### Post by Phrawm48 on 2008-01-13
**bthessel** said, *Make sure that you have "MarbleMouse" under the server layout section as well.*

**b**: Any chance you could include exactly what's needed for that section, too?

Cheers & thanks,
Ric
SFO

---

### Post by Buffalo Soldier on 2008-01-24
> **Riccisayer@tiscali.fr said:**
> Hi guys, I missed something here, where does one put these magic codes. I don't do enough of this sort of thing, so I just don't know?

Hi Riccisayer,

Try reading my starter post in this thread. I will try to re-edit it to make it clearer.

> **Phrawm48 said:**
> **bthessel** said, *Make sure that you have "MarbleMouse" under the server layout section as well.*

**b**: Any chance you could include exactly what's needed for that section, too?

Cheers & thanks,
Ric
SFO

Hi Phrawm48, 

What bthessel mean is, if your config for your marblemouse look like this:

```

Section "InputDevice"
    Identifier "**[COLOR="Red"]MarbleMouse[/COLOR]**"
    Driver     "mouse"
    Option     "Protocol" "auto"
    Option     "Device" "/dev/input/mice"
    Option     "Buttons" "5"
    Option     "ButtonMapping" "1 8 3 6 7"
    Option     "EmulateWheel"  "true"
    Option     "EmulateWheelTimeout" "300"  # msec
    Option     "EmulateWheelButton"  "6"
    Option     "YAxisMapping"        "4 5"
EndSection

```

Then at the end of the xorg.conf file you should also have something like this:
```

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"**[COLOR="Red"]MarbleMouse[/COLOR]**"
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by D351 on 2008-03-20
Much thanks... It took me forever to find a track-ball, and now it works too.

---

### Post by Phrawm48 on 2008-03-21
[COLOR=#000000]Somewhat to the side, but along the way I discovered the *btnx* utility.[/COLOR]

I described it in this addition to the **[Cool applications you use that others might not know of]("http://ubuntuforums.org/showpost.php?p=4345706&postcount=836")** thread...

Cheers & hope this helps,
Ric
SFO

---

### Post by raif on 2008-03-31
I have followed the how-to and cannot get the trackball to work properly on my desktop or laptop, both of which are running Kubuntu 07.10.  While the big buttons work as normal right and left, the small buttons do not work at all and I cannot get the scrolling working.

With xev I get the buttons as follows:
big left - 1
small left - 8
big l & r together - 2
small right - 9
big right - 3

I have searched a bit and can't find any clear explanation of how to map buttons.  Some config files for the MarbleMouse suggest having 9 buttons but I can't find out why this how-to says 5 buttons.  I have found that button events 4 & 5 and 6 & 7 are for scrolling but don't really understand the x, y and z axis, other than that the Z axis is supposed to be for virtual scrolling or something.  

Or indeed how to get the left and right buttons to go forward and backwards in konqueror (or similarly with messages in Kontact), which would be incredibly useful.

Excerpts from my xorg.conf files are below:

```

Section "InputDevice"
    Identifier "MarbleMouse"
    Driver     "mouse"
    Option     "Protocol" "auto"
    Option     "Device" "/dev/input/mice"
    Option     "Buttons" "5"
    Option     "ButtonMapping" "1 8 3 6 7"
    Option     "EmulateWheel"  "true"
    Option     "EmulateWheelTimeout" "300"  # msec
    Option     "EmulateWheelButton"  "6"
    Option     "YAxisMapping"        "4 5"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection


```

```

Section "ServerLayout"
        Option          "AIGLX"         "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
#       InputDevice     "Configured Mouse"
        InputDevice     "MarbleMouse"
#       InputDevice     "stylus" "SendCoreEvents"
#       InputDevice     "cursor" "SendCoreEvents"
#       InputDevice     "eraser" "SendCoreEvents"
EndSection

```
NB I've only just commented out the Configured Mouse to see if it was defaulting to that.

I've been using ubuntu for almost three years and am stumped by this one so would appreciate any help or ideas as I could really do with having a scroll function on my marble mouse.  Hope I haven't missed something simple...

thanks

---

### Post by YAOMTC on 2008-04-25
This doesn't seem to work anymore in Hardy. I have my Marble Mouse connected through the PS/2, and I edited xorg.conf and about:config (currently using Firefox 2 rather than 3.0b5 for a few reasons)... but it doesn't effect anything.

I take it something's changed in Ubuntu to make this no longer work?

**EDIT:** Never mind! Seems it works now that I've restarted the computer. I don't remember having to restart the computer last time, but maybe I did! Well, it doesn't matter, disregard this post. >_>

---

### Post by battlesound on 2008-06-03
I'm noticing a big problem with my mouse setup now in Hardy 8.04.  I get two clicks for each single click on buttons 1 and 3.  The other two buttons aren't configured for use in firefox or nautilus so I don't know about them doing the same thing, but I can only assume they do the same thing.

my xorg.conf info:
```
Section "InputDevice"
    Identifier "MarbleMouse"
    Driver     "mouse"
    Option     "Protocol" "auto"
    Option     "Device" "/dev/input/mice"
    Option     "Buttons" "5"
    Option     "ButtonMapping" "1 8 3 6 7"
    Option     "EmulateWheel"  "true"
    Option     "EmulateWheelTimeout" "300"  # msec
    Option     "EmulateWheelButton"  "6"
    Option     "YAxisMapping"        "4 5"
EndSection
```

and, the "MarbleMouse" part, too:
```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	**InputDevice	"MarbleMouse"**
	InputDevice	"Synaptics Touchpad"
EndSection
```

When I run **xev**, I have confirmation of two clicks for one click.  I see a difference in both sets of clicks, though:  "state 0x0" and "state 0x100".

Any thoughts, solutions, help?  Thanks.

This is very confusing.

update:

I added **"CorePointer"** to the ServerLayout section and it works just fine.
It looks something like this:

```
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	**InputDevice	"MarbleMouse"       "CorePointer"**
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by Polish Rifle on 2008-07-29
I'm using Opera 9.5 and would like the big L/R buttons pressed together to trigger the scroll command.  How would I do that?  Right now I have the small left button set to scroll when I press it and move the marble.  

Do I need to change anything in Opera?

---

### Post by boldexplorer on 2008-11-07
A very big thank you Buffalo Soldier! This thread is awesome and have been a huge life saver!!

Keep on rocking!

---

### Post by phalbert on 2008-11-10
This seems to have changed in Ubuntu 8.10

# commented out by update-manager, HAL is now used


This is what is says now in my xorg.conf in Intrepid just before the
Section "InputDevice" line

---

### Post by RiazM on 2008-11-25
Hey, I'm thinking of getting one of these trackballs, is the lowdown that they don't work with 8.04 upwards? (Presumably because of the change in xorg?)

---

### Post by cascaranuez on 2008-12-06
Everything is different now in Ubuntu 8.10. See [https://wiki.ubuntu.com/X/Config]("https://wiki.ubuntu.com/X/Config") and *configure your input device* with a fdi file like this:

```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" string="Logitech USB Trackball">
      <merge key="input.x11_options.ButtonMapping" type="string">1 8 3 9 2</merge>
      <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
      <merge key="input.x11_options.EmulateWheelButton" type="string">9</merge>
      <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
      <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
      <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
    </match>
  </device>
</deviceinfo>
```

---

### Post by DetroitLibertyPenguin on 2008-12-20
What is an fdi file? How do I make it? How come nobody at Ubuntu can ever figure out "if it ain't broke don't fix it?" Ideally I'd like the small buttons to actually scroll as soon as I tap them, instead of having to hold and then scroll with the "marble" any ideas on that in this new fdi too?

How do you actually figure any of this stuff out without simply copying what other folks are doing? This is one of my top reasons for using Linux is to actually figure out why my comptuer does things

---

### Post by Locutuslaser on 2008-12-20
Yes, found that out too it works different in 8.10 In the xorg file is something commented about a new HAL config file.

---

### Post by DetroitLibertyPenguin on 2008-12-20
my xorg.conf doesn't mention anything about HAL, is that because I have Xubuntu not Ubuntu 8.10, can the orginal post still work edited in my xorg.conf

How do you actually figure this stuff out so I can come up with my own solution instead of always just copying work someone else does?

---

### Post by Hachiroku on 2008-12-27
WOW! Just when I got it to work in 8.04 after 7 months, they change it!
Time to go back to Windows? 
I'm afraid I don't understand (all over again). They used this .fdi thing before and it was a PITA then. Since I'm not a programmer, what do I name the file? I've tried "mouse", "Logitec Trackball", "Configured Mouse", etc and nothing works. Any further ideas greatly appreciated...:confused:

---

### Post by Hachiroku on 2008-12-27
Hmmm...using the xinput watch-props command, I discovered the scroll wheel button is set to 9. No matter what script you edit, it won't set the scroll button to 8. If anyone has figured this one out, let me know.

xorg.conf was soooo easy...[-o<

---

### Post by Hachiroku on 2008-12-27
Here's the script that works:

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" string="Logitech USB Trackball">
      <merge key="input.x11_options.ButtonMapping" type="string">1 8 3 9 2</merge>
      <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
      <merge key="input.x11_options.EmulateWheelButton" type="string">8</merge>
      <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
      <merge key="input.x11_options.Emulate3Buttons" type="string">false</merge>
    </match>
  </device>
</deviceinfo>

Perserverence and not allowing a machine to beat me pays off...hours later.

Now, the question is, where to put it. I have a .fdi file called "mouse", one called "Configured Mouse", one called "Logitech USB Trackball", and another one that was already there called 'preferences'. I added the script to all of them, unplugged the mouse and reattached it.

Good Luck...:)

---

### Post by AKADAP on 2009-01-04
> **Hachiroku said:**
> Here's the script that works:

<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" string="Logitech USB Trackball">
      <merge key="input.x11_options.ButtonMapping" type="string">1 8 3 9 2</merge>
      <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
      <merge key="input.x11_options.EmulateWheelButton" type="string">8</merge>
      <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
      <merge key="input.x11_options.Emulate3Buttons" type="string">false</merge>
    </match>
  </device>
</deviceinfo>

Perserverence and not allowing a machine to beat me pays off...hours later.

Now, the question is, where to put it. I have a .fdi file called "mouse", one called "Configured Mouse", one called "Logitech USB Trackball", and another one that was already there called 'preferences'. I added the script to all of them, unplugged the mouse and reattached it.

Good Luck...:)

I have just wasted several hours attempting to enable horizontal scrolling on a mouse with a scroll ball. I have decided there are some fundamental things missing from all of the how-to and documentation I have looked at.

1) What does the file name need to be? My guess is that in can be anything with the .fdi extension in the /etc/hal/fdi/policy directory, but since I have been unable to get anything to change on the mouse settings using any file I have tried, I could be very wrong.
2) Where does one find the list of "input.x11_options.blah" keys that are appropriate for a particular device? I find lots of how-to documents that use some of these keys, but I have not found a way to get a list of the possible keys to use. My attempts to guess the appropriate keys have gone nowhere.
3) What actually needs to be specified in this file? Obviously, the file needs at least a key to match so the option goes in the correct section, and the option you are trying to change must be specified, but I have read documents that claim you must also specify the driver, and others that include examples that don't specify the driver.
4) If one does need to specify the driver, how does one figure out the name of said driver?

If I look at the Xorg log, it shows it getting some of the scroll wheel properties from a config file (**) at the beginning of the line, but I have not been able to find the configuration file it is using.

These are the lines:
(**) Acrox USB & PS/2 Mouse: YAxisMapping: buttons 4 and 5
(**) Acrox USB & PS/2 Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200

My level of frustration is rather high at the moment.

---

### Post by RiazM on 2009-01-05
I used the information here: [https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB)

To configure my Marblemouse. Horizontal scrolling doesn't work, but vertical does by holding the left small button. (I edited the file so that it worked with the right small button)

---

### Post by AKADAP on 2009-01-06
> **RiazM said:**
> I used the information here: [https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB)

To configure my Marblemouse. Horizontal scrolling doesn't work, but vertical does by holding the left small button. (I edited the file so that it worked with the right small button)

The link you gave did not answer any of my questions. However it linked to other discussions which linked to other discussions so many times that I lost track of how I got to any of the sites.

Anyway one of the sites mentioned that keys of the type "input.x11_option.blah" are options that used to be placed in the xorg.conf file where "blah" was replaced by the option name.
From there I read the man page for xorg.conf, and found that the actual options were defined in the man page for the driver used.
So of to the Xorg.0.log to see if I can find what driver is being used. I come up with "evdev_drv.so" There is no man page for this.
There is also no man page for evdev_drv.
Apparantly, in spite of the file name, the driver name is evdev. There is a man page for "evdev". This confirms that the option whose name I had guessed as "XAxisMapping" exists and is actually the one I want to get horizontal scrolling.

So it looks like I have an answer to question 2.

I think my problem is down to finding a key to match so my changes get added to the right section. Currently "Acrox USB & PS/2 Mouse" is not working.

---

### Post by AKADAP on 2009-01-06
From lshal I get:

udi = '/org/freedesktop/Hal/devices/usb_device_f62_1001_noserial_if0_logicaldev_input'
  info.capabilities = {'input', 'input.mouse'} (string list)
  info.category = 'input'  (string)
  info.parent = '/org/freedesktop/Hal/devices/usb_device_f62_1001_noserial_if0'  (string)
  info.product = 'Acrox USB & PS/2 Mouse'  (string)
  info.subsystem = 'input'  (string)
  info.udi = '/org/freedesktop/Hal/devices/usb_device_f62_1001_noserial_if0_logicaldev_input'  (string)
  input.device = '/dev/input/event3'  (string)
  input.originating_device = '/org/freedesktop/Hal/devices/usb_device_f62_1001_noserial_if0'  (string)
  input.product = 'Acrox USB & PS/2 Mouse'  (string)
  input.x11_driver = 'evdev'  (string)
  linux.device_file = '/dev/input/event3'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'input'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1d.2/usb6/6-2/6-2:1.0/input/input3/event3'  (string)

So, I could have found the driver being used from the "input.xll_drive = 'evdev' (string) line.

I have created a file in the /etc/hal/fdi/policy directory called CompaqMouse.fdi that contains the following:

<?xml version="1.0" encoding="ISO-8859-1"?>

<deviceinfo version="0.2">

  <device>
    <match key="info.product" string="Acrox USB & PS/2 Mouse">
      <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
    </match>
  </device>

</deviceinfo>

As far as I can tell, this is correct, but it does not do anything.
xinput list-props "Acrox USB & PS/2 Mouse" still gets me this:

Device 'Acrox USB & PS/2 Mouse':
	Device Enabled:		1
	Middle Button Emulation:		2
	Middle Button Timeout:		50
	Wheel Emulation Inertia:		10
	Wheel Emulation:		0
	Wheel Emulation X Axis:		0, 0
	Wheel Emulation Y Axis:		4, 5
	Wheel Emulation Timeout:		200
	Wheel Emulation Button:		4
	Drag Lock Buttons:		0

Note the Wheel Emulation X Axis that I am trying to change to 6, 7 is still 0, 0.

---

### Post by jamesclish on 2009-04-04
REVOLUTIONARY!!! Well done!

This is exactly the feature I needed in my windows install...

---

### Post by Duktoonz on 2009-04-13
Thanks to all who've posted in this thread.  It helped me a great deal.  I'm easily an Ubuntu newbie having just installed this afternoon.  I'm still getting used to the command line interface of the terminal, but I think I'm catching on.  I'll admit it took some time to figure out that the code mentioned in previous posts needed to be saved in a file called mouse-wheel.fdi in the /etc/hal/fdi/policy folder, but I eventually got it.  Of course not without some minor head thumping before I finally *also* realised I need a reboot to make it go. *bonk*

Anyhoo, all is well now, and my trackball is scrolling vertically in Firefox just as god intended.  I thank you all for that.  Cheers! ;)

---

### Post by themusicwave on 2009-05-11
Hi everyone,  

I just got a Logitech Marble mouce and am trying to get the scrolling to work with the small buttons.

I have done the following to no avail.

Created a file at /etc/hal/fdi/policy/mouse-wheel.fdi with these contents
[PHP]
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" string="Logitech USB Trackball">
      <merge key="input.x11_options.ButtonMapping" type="string">1 8 3 9 2</merge>
      <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
      <merge key="input.x11_options.EmulateWheelButton" type="string">9</merge>
      <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
      <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
      <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
    </match>
  </device>
</deviceinfo>
[/PHP]

I then rebooted the machine.  Still doesn't work.  The buttons are still mapped to forward and back in firefox and don't scroll.

---

### Post by dyn0myt3 on 2009-05-15
Hi, I'm very new to Linux.
I have the same mouse, but instead of scroll effect, 
I just want the buttons to be buttons.
Is this possible.

Thanks

mysys:
Kubuntu 9.04
MSI K8T Neo2
2x160gb WD
Asus Geforce 6200
Logitech  Marble Mouse (4 button)

---

### Post by themusicwave on 2009-05-15
Hey Everyone I got in working in Ubuntu 9.04

The first thing I discovered is that it is showing up as a 32 button mouse, which is wrong.  To see this I used:

[PHP]xinput list[/PHP]

Which showed:
[PHP]"Logitech USB Trackball"	id=5	[XExtensionPointer]
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
[/PHP]

From here I copied the file I found here: [https://help.ubuntu.com/community/Logitech_Marblemouse_USB]("https://help.ubuntu.com/community/Logitech_Marblemouse_USB") to /etc/hal/fdi/policy/mouse-wheel.fdi

After this, I ran the following command to remap the keys for just this mouse.  If your mouse is showing up as something else change that string in the command.

[php] xinput set-button-map "Logitech USB Trackball" 1 8 3 4 5 6 7 2 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32[php]

This gave me the left big button as left click, the right big button as right click, the left small button as srcoll(vertical) and I think the right small button as middle click(can't figure out how to test this).

Plying with the numbering will change the mapping using this you should be able to swap any keys and make it lefty or change which is scroll and middle click.

I hope this helps someone.

---

### Post by themusicwave on 2009-05-15
It seems my changes weren't permanent.  I have to re run the command

[PHP]xinput set-button-map "Logitech USB Trackball" 1 8 3 4 5 6 7 2 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32[/PHP]

everytime I start x which includes login.  Anyone know how to make this permanent?

Thanks.

---

### Post by bbrg548 on 2009-07-26
> **themusicwave said:**
> It seems my changes weren't permanent.  I have to re run the command

[PHP]xinput set-button-map "Logitech USB Trackball" 1 8 3 4 5 6 7 2 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 26 27 28 29 30 31 32[/PHP]

everytime I start x which includes login.  Anyone know how to make this permanent?

Thanks.

In the gnome menus, go to "System -> Preferences -> Startup Applications" and select "Add".

For "Name" enter "mouse scrolling" (or whatever you want, really) and under "Command" paste your xinput command. The system will run it when it starts, and it should scroll without you having to do anything.

---

### Post by themusicwave on 2009-07-26
The only problem with adding it as a startup script is that it only works if the trackball is plugged in when you start X or ubuntu.

If the trackball isn't plugged in, then you still have to run the command.  I just put it in a shell script on my desktop so I can click it when I plug in the mouse.

Still not a perfect solution though.

---

### Post by bbrg548 on 2009-07-26
> **themusicwave said:**
> The only problem with adding it as a startup script is that it only works if the trackball is plugged in when you start X or ubuntu.

If the trackball isn't plugged in, then you still have to run the command.  I just put it in a shell script on my desktop so I can click it when I plug in the mouse.

Still not a perfect solution though.

I agree. I also seem to have lost another function - before, when I would click a link in firefox with that same button, it would open the link in a new tab. Now it doesn't.  :-x

FYI, if you don't want to clutter up your desktop with the script icon, you can put it in your ~/.gnome2/nautilus-scripts folder and (if you've marked it as executable) it will show up in the scripts submenu if you right-click on the desktop or in a nautilus window.

---

### Post by themusicwave on 2009-07-26
> **bbrg548 said:**
> I agree. I also seem to have lost another function - before, when I would click a link in firefox with that same button, it would open the link in a new tab. Now it doesn't.  :-x

FYI, if you don't want to clutter up your desktop with the script icon, you can put it in your ~/.gnome2/nautilus-scripts folder and (if you've marked it as executable) it will show up in the scripts submenu if you right-click on the desktop or in a nautilus window.

Thanks, that is much nicer than keeping it on the desktop.  My firefox links still work, if I use the left scroll button to click a link it opens in a new tab.  I am not sure what is different.  I can post anything you need for comparison.

---

### Post by bbrg548 on 2009-07-26
> **themusicwave said:**
> Thanks, that is much nicer than keeping it on the desktop.  My firefox links still work, if I use the left scroll button to click a link it opens in a new tab.  I am not sure what is different.  I can post anything you need for comparison.

Thanks, but I've found I can open a link in a new tab if I "chord" the big left and right buttons. It'll take a little getting used to, but I think it may work better (I would sometimes accidentally open a link in a new tab when I intended to scroll, the way it was before).

---

### Post by RiazM on 2009-11-09
So... anyone had any luck with getting this to work on 9.10?

---

### Post by themusicwave on 2009-11-09
No I can;t get it to scroll anymore.

---

### Post by dcipjr on 2009-11-18
I got the scrolling working on the Marble Mouse under 9.10 by running these two commands:

```

xinput set-int-prop "Logitech USB Trackball" "Evdev Wheel Emulation" 8 1
xinput set-int-prop "Logitech USB Trackball" "Evdev Wheel Emulation Button" 8 8

```

Mine is the USB version, so it'll probably be slightly different for the PS/2. xinput list will give you a list of devices, so pick yours out and try these two commands.

---

### Post by themusicwave on 2009-11-19
Do you have to run them every time you start up X?  Or is there a way to get it to always work?

---

### Post by Takis_Rempetis on 2009-12-04
The code you posted in the beggining helped me make my microsoft mouse work, cause i had no drivers. I find it really exciting what you can do with the xorg.conf file :D

Thanks for the help :D

---

### Post by kelvin spratt on 2009-12-04
if you wan't to scroll in firefox just enable autoscroll  preferences advanced in firefox.

---

### Post by zansatsu0 on 2010-01-30
After a ton of fiddling in 9.10, this is what finally worked for me:

Create and edit a new policy for your Marble Mouse.
```
sudo pico /etc/hal/fdi/policy/marble-mouse.fdi
```

Copy and paste this into your editor and save it (ctrl+x, yes, enter).
```
<?xml version="1.0" encoding="UTF-8"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.product" string="Logitech USB Trackball">
      <merge key="input.x11_driver" type="string">evdev</merge>
      <merge key="input.x11_options.ButtonMapping" type="string">1 2 3 4 5 6 7 8 9</merge>
      <merge key="input.x11_options.EmulateWheel" type="string">true</merge>
      <merge key="input.x11_options.EmulateWheelButton" type="string">8</merge>
      <merge key="input.x11_options.ZAxisMapping" type="string">4 5</merge>
      <merge key="input.x11_options.Emulate3Buttons" type="string">true</merge>
      <merge key="input.x11_options.Emulate3Timeout" type="string">75</merge>
      <merge key="input.x11_options.GrabDevice" type="string">false</merge>
    </match>
  </device>
</deviceinfo>
```

Restart hal or reboot. Try it out.

I think the GrabDevice=false option and driver=evdev clauses is what fixed it for me. Let me know if this helps anyone. Thanks and good luck.

---

### Post by ironblade on 2010-05-04
My config, working for Ubuntu 10.04 Lucid Lynx.
This setup is for right-handed folks, with buttons working as follows:
Big Left: normal left button
Small Left: "Button 3", ie does Pasting from clipboard
Small Right: Hold it and scroll the trackball (vertically only)
Big Right: normal right button

Add this to your /etc/X11/xorg.conf:
```
Section "InputClass"
        Identifier  "Marble Mouse"
        MatchProduct "Logitech USB Trackball"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "ButtonMapping" "1 8 3 4 5 6 7 2 9"
        Option "EmulateWheel" "true"
        Option "EmulateWheelButton" "9"
        Option "ZAxisMapping" "4 5"
        Option "XAxisMapping" "6 7"
        Option "Emulate3Buttons" "false"
EndSection

```

Good luck, and keep an eye on [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/567068](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/567068)

---

### Post by dklearhos on 2010-05-15
thanks a lot ironblade. my marble finally works!!
just one thing how to change the two big buttons as i am left handed? which numbers should i change?

---

### Post by rulet on 2010-05-18
I am righthanded but for me is much more easier to do scrolling with left small button pressed. How to do that in Ubuntu 10.04?

---

### Post by dklearhos on 2010-05-18
> **rulet said:**
> I am righthanded but for me 
is much more easier to do scrolling with left small button pressed. How 
to do that in Ubuntu 10.04?

change this line  
> 
Option "EmulateWheelButton" "9"


to this

> 
Option "EmulateWheelButton" "8"


---

### Post by RiazM on 2010-06-01
Is there any way we could do this using HAL instead of messing with xorg? That seems to be the "new" way to do things "properly"

---

### Post by rulet on 2010-06-10
> **dklearhos said:**
> 
Quote:
Originally Posted by rulet View Post
I am righthanded but for me
is much more easier to do scrolling with left small button pressed. How
to do that in Ubuntu 10.04?



change this line
Quote:
Option "EmulateWheelButton" "9"
to this

Quote:
Option "EmulateWheelButton" "8" 

 Thank's much, it works!

---

### Post by jonthysell on 2010-06-12
There's more info here: [https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB)

---

### Post by onclejean on 2011-08-16
Hi 
With the 6.3 + drivers for set point it is easy to scroll with the "Marble Mouse" trackball. Using the default settings click on the righ hand side mini button ant ball then scrolls the page. Click again to turn scrolling off an the ball returns to running the pointer.
A tiny icon appears mid screen to show when the scroll mode is on
I recommend it
onclejean

---

### Post by rulet on 2011-11-24
Hello again. There is a problem when using this device([I meen this]("http://www.logitech.com/ru-ru/mice-pointers/trackballs/devices/4786")) when using firefox in gnome-shell or unity on ubuntu 11.10. The selection of a text with scrolling down doesn't work in firefox, selection of a text with scrolling up works as normal. There is no such bug in chrome browser.
 Any ideas?

---

### Post by dklearhos on 2011-11-24
It looks like a firefox bug. It does not work with other mouse either.

[https://bugs.launchpad.net/firefox/+bug/744580]("https://bugs.launchpad.net/firefox/+bug/744580")

---

### Post by rulet on 2011-11-24
I see...
 I confirmed a bug there for ubuntu 11.10

---

