---
title: "All Logitech MX Mouse Buttons (MX610) - The Quick &amp; Easy Guide"
date: 2007-01-05
forum: Tutorials
---

### Post by kogber on 2007-01-05
[COLOR="DarkRed"][B]This guide works well for the MX610 Mouse - if you own another mouse, I suggest you find a howto for that exact mouse.
[/B][/COLOR]
**Preface**
Well, everything except horizontal scrolling works - I have done some research and attempted to get horizontal scrolling to work with no luck so for.  This is as quick and easy as I could manage.

**If you are just looking for back/forward buttons in firefox, I wrote [this guide]("http://ubuntuforums.org/showthread.php?t=327131&highlight=logitech+mouse"). ** Also check out [this howto]("http://ubuntuforums.org/showthread.php?t=219894&highlight=logitech+mouse"), which has info about cruise control, as well as a different approach for evdev. 

This guide uses the evdev driver, which should work for any usb-attached mouse.  

There is a section at the end of this guide specifically for getting MX610 email and IM indicator lights working.

This has been tested with Kubuntu 6.10 Edgy and a logitech mx610 mouse.  The mx600 and mx700 mice don't work well under this setup.

I realize there are other similar guides on this forum.  I am trying to improve upon them, with a focus on simplicity and clarity for new linux/ubuntu users.

This guide is based on [Dankoozy's]("http://97k.eu/blog/comments.php?y=06&m=10&entry=entry061015-170138") blog post, with several changes. 


[SIZE="3"]**The Quick & Easy Guide**[/SIZE]

[SIZE="2"]**1. Backup your xorg.conf file**[/SIZE]

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.good     #(think: Copy Source Destination)
```

now you have a good version (xorg.conf.good) of the file to fall back on if something goes wrong.   If, after rebooting, you wind up at a text prompt, type in your username and pass.  Then type: [COLOR="DarkRed"]
**Write this down!** [/COLOR]
```

sudo cp /etc/X11/xorg.conf.good /etc/X11/xorg.conf
startx  # this command will load Xorg (the GUI)

``` 

[SIZE="2"]**2. Equipment Check **[/SIZE]
We need three packages, which we can get with the following console command all at once (these might require universe or multiverse to be enabled in your package manager):

```
sudo apt-get install xvkbd xbindkeys xserver-xorg-input-evdev
```

**xserver-xorg-input-evdev** is the generic usb driver we will be using for the mouse.
**xvkbd** will allow mouse button presses to simulate keyboard buttons, such as Alt + Left/Right for forwards/backwards.
**xbindkeys** is a program that will run in the background and map the mouse buttons to the actions we will set.  Optionally, get the xbindkeys-config package - this is a GUI for editing the xbindkeys bindings text file, but this guide will simply edit the text file manually.

[SIZE="2"]**3. Create Two Text Files **[/SIZE]

**a.** create a new rule file for udev with the following command:
```
sudo gedit /etc/udev/rules.d/19-local.rules    
``` (replace gedit with kate in kubuntu)

in this text file, paste the following:

```

KERNEL=="hiddev*", NAME="%k", MODE="666"
KERNEL=="event*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/**mx610**"

```

The bold mx610 part can be replaced with whatever you want - just make a note of what you have written here, because it must correspond to what you will write in the xorg.conf file.

**b. **  now create the xbindkeys bind file:

```
gedit ~/.xbindkeysrc
```

and paste the following:  ( go to the [xbindkeys site]("http://hocwp.free.fr/xbindkeys/xbindkeys.html#configuration") for more info and example configuration files)
[I]
People with other mice and some expertise - please add your bind files.[/I]

```

# Backward and Forward buttons
"xvkbd -xsendevent -text "\[Alt_L]\[[COLOR="Black"]L[/COLOR]eft]""
m:0x0 + b:8
"xvkbd -xsendevent -text "\[Alt_L]\[[COLOR="Black"]R[/COLOR]ight]""
m:0x0 + b:9

#Email Button - put in a console command to launch your mail app, such as thunderbird or kmail
"firefox -new-tab http://mail.google.com/mail/"
m:0x0 + c:236
XF86Mail

# sad note - the IM button is not a real button - as far as I can tell

# Volume +
"amixer set PCM 1+"
m:0x0 + c:176

# Volume -
"amixer set PCM 1-"
m:0x0 + c:174

# Mute
"amixer set PCM toggle"
m:0x0 + c:160

```

[SIZE="2"]**4. Autostart xbindkeys  **[/SIZE]
Next, we need to add the xbindkeys process to the autostart. 
**In Ubuntu:**
[INDENT]System > Preferences > Sessions
select the Startup Programs tab
Add: /usr/bin/xbindkeys[/INDENT]
 
**In Kubuntu:**
[INDENT]```
kate ~/.kde/Autostart/start-xbindkeys
```
Insert this into the file:
```
#!/bin/sh xbindkeys
```
Make it executable:
```
chmod +x ~/.kde/Autostart/start-xbindkeys
```[/INDENT]

[SIZE="2"]**5. Edit The xorg.conf File **[/SIZE]
Open up your xorg.conf file in a text editor:

```
sudo gedit /etc/X11/xorg.conf
```  

find the Module Section and **add** the evdev module:

```

Section "Module"
  Load "i2c"
  Load "bitmap"
  ....
  ....
  **load "evdev"**
EndSection

```

Next, change the InputDevice section for the mouse to this:

```
Section "InputDevice"
  Identifier "**Configured Mouse**"
  Driver "evdev"
  Option "Device" "/dev/input/**mx610**"
EndSection
```

Make sure that the bold mx610 name part corresponds to the name part in the file 19-local.rules that we made before.

Make sure the Identifier name, Configured Mouse, is the same as in the ServerLayout section:

```
Section "ServerLayout"
	...
**	InputDevice	"Configured Mouse"**
	...
EndSection
```


[SIZE="2"]**6. Save and Reboot**[/SIZE]

save the xorg.conf file, and the other two text files previously created.  Then Restart the computer.  [COLOR="DarkRed"]**Remember: if the xorg.conf file is not edited properly (ie typos) you will need to revert to the backup as explained above.**[/COLOR]  

An alternate backup strategy for xorg.conf is to comment out old stuff by adding # to the start of an old line.  Then to edit xorg.conf and check for mistakes, you can say "sudo nano etc/X11/xorg.conf" right there before loading Xorg.


[SIZE="3"]**Optional: Indicator lights with the mx610hack**[/SIZE]

Get the mx610hack  [here]("http://www.cynapses.org/tmp/lomoco/mx610hack-0.3.tar.gz")

Then extract it.  

Delete the debcomp link file, and replace it with [this file]("http://www.fastcgi.com/devkit/depcomp")

Open up a console window, change to the directory where you extracted the files.  

Compile the mx610 hack:

```

./configure
make
sudo make install

```

Now you should be able to control the lights!  In the console, try "mx610hack --usage" and "mx610hack --help".  For example:

```

mx610hack --email-on /dev/hiddev0
mx610hack --email-off /dev/hiddev0

```

I use an email notifier called checkgmail, which can execute a command when there is mail, and another command when there is no new mail.  This is very cool, because the blue email LED stays on as long as I have new mail, so I don't have to have the monitor on.  I also use Kopete, and I have setup my IM light to pulse when I get an IM, and then it turns off, with this **one** command in the Notifications:

```
mx610hack -i /dev/hiddev0 && sleep 1.5 && mx610hack -O /dev/hiddev0 
```

You can use the same idea for your mail application if there is only one command you can execute on a new mail event.  The sleep value is how long the light will stay on before the second part of the command is executed to turn it back off.

---

### Post by apathos on 2007-01-13
Hope it's ok to post here...

I'm looking forward with great anticipation to having all (or at least almost all) of my mouse buttons working.  But when I get to step 2, the terminal reports that ```
Reading state information... Done
Package xvkbd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xvkbd has no installation candidate
```

Being an almost complete ubuntu newb, what should i do now?  I'd try to go download it myself, but i have no idea if it would work the same, or if i could even find it when i got it.  :oops:

---

### Post by kogber on 2007-01-13
apathos, you need to enable **universe** and **multiverse** in your package manager.  These are repositories that hold packages that are not in the main Ubuntu OSS package category.  I am going to assume that you are using Ubuntu with the default Synaptic package manager, in which case it would go like this:

in Synaptic Package Manager
goto Settings > Repositories

and um, make sure all of the check boxes are checked.   After doing so, click Reload, and try searching for xvkbd to see if that package is listed as a part of your available package list.  Then see if you can install it again.  Let me know if you have any more trouble.

---

### Post by apathos on 2007-01-14
well, ok.  Thank you for the previous help, that did take care of the problem.

Now I've followed all the remaining instructions meticulously (as best I can being Utternewb), but am willing to consider I may have made some mistakes.

But I'd first like to consider another problem.  I've been working with the understanding my mouse is an MX610.  I just discovered it's an MX600.  Quite similar, but still a different model (as best, I can tell, no pretty lights).

Might this explain why this isn't working, or is it more likely I just messed something up?

---

### Post by kogber on 2007-01-14
apathos, 

I believe I figured out the problem.  The words left and right need to be capitalized in the bind file for the xvkbd command to work in Ubuntu (The text editor uses the same bracket system for code and quote tags so this caused Left and Right to go lowercase on my initial post of the guide, this has been fixed now):

# Backward and Forward buttons
"xvkbd -xsendevent -text "\[Alt_L]\[**L**eft]""
m:0x0 + b:8
"xvkbd -xsendevent -text "\[Alt_L]\[**R**ight]""
m:0x0 + b:9

so edit the bind file with the correction, and then goto System Monitor, find xbindkeys in the Processes, click End Process with it selected, and type xbindkeys in the console to restart the process.  Then the back/forward buttons should be working.

I have also updated the Guide with the correction.  I actually have an mx600 mouse/keyboard set, so I booted up Ubuntu on my desktop and tested it out.  The back/forward works in firefox and the File Browser, but the zoom in/out buttons are not being registered (only the 100% button is being detected).  On the flipside, the horizontal scroll events are being detected by the kernel, so I should be able to get that working whenever I get some time to play around with it.

---

### Post by apathos on 2007-01-14
That did it!  Thanks!  This is really a big help.

and I look forward to the horizontal fix as well (as you have time, of course).

Thanks again!

--apathos

---

### Post by cez801 on 2007-01-19
Hi, got the main mouse buttons working without an problems. The only ones that did not go with the standard edgy install where the mouse forward and backwards, so I'm glad I have them back :)

I tried compiling the mx610 hack to get the indicator lights working but got the following error after the ./compile.

/bin/bash: /home/chrisst/missing: No such file or directory
configure: WARNING: `missing' script is too old or missing
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

The config.log did not really shed any light on the issue.

BTW - I am newbie, only installed Ubuntu 4 days ago, but used unix about 10 years ago.

---

### Post by kogber on 2007-01-19
cez801, the line about the 'missing' script is irrelevant - i have the same warning.  It's the errors you gotta watch out for.

Anyways, my guess is you are missing some c libraries needed to compile, so I would suggest you try:

```
sudo apt-get install libc6-dev

```
or, if you are running amd64:

```
sudo apt-get install libc6-dev-amd64
```

Let me know if that fixes it or not, i'll edit the guide for others.

---

### Post by cez801 on 2007-01-19
I did not notice your update. But I managed to find a solution. I was trying to get bluetooth installed and in those instructions you needed to have these packages.
[LIST]
[*]build-essential
[*]automake
[*]autoconf
[/LIST]
So I installed those packages as well, and managed to complete the mx610 hack. 
Works like a charm.

BTW - this is a pretty new Ubuntu install - so adding those three packages should sort it out for any one else. I used the Synaptic Package Manager UI to do it, but I'm sure you know a terminal command to make it easier for the guide.

Great guide, Ironically I never managed to get the lights working under windows (for Outlook or Express) using the Logitech drivers :)

---

### Post by kogber on 2007-01-19
Yeah, I find it funny that I get far more functionality out of this logitech mouse in linux without the windows Logitech drivers.  This is all thanks to the [kde developer]("http://www.kdedevelopers.org/blog/102") who made the mx610hack.  The led's would only theoretically work with Outlook and MSN in windows - both of which are disgusting programs I never touched.  Glad to hear the guide was useful.

---

### Post by TigerCR1200 on 2007-01-23
I am having problems getting this setup. I started the setup with a mx600 that turned out to be bad so I took it back and got the mx610. I cant seem to get it to function quite right. I have it working now but no scroll wheel which is driving me nuts. I also cant seem to get it setup with evdev, my old mouse worked fine with it but this one just gives me no core pointer found. 

cat /proc/bus/input/devices
> I: Bus=0003 Vendor=046d Product=c518 Version=4200
N: Name="Logitech USB Receiver"
P: Phys=usb-0000:00:02.2-1.3/input1
S: Sysfs=/class/input/input2
H: Handlers=kbd event2 
B: EV=f
B: KEY=c0002 400 0 0 1 f80 78000 6639fa d84157ad 8e0000 0 0 0
B: REL=40
B: ABS=1 0

> tiger@tiger-edgy:~$ cat /etc/udev/rules.d/19-local.rules
KERNEL=="hiddev*", NAME="%k", MODE="666"
KERNEL=="event[0-9]*", SYSFS{../name}=="Logitech USB Receiver", NAME="input/mx600"


> tiger@tiger-edgy:~$ ls /dev/input
by-id  by-path  event0  event3  mice  mouse0  mx600  ts0


xorg.conf:
> Section "ServerLayout"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection
> Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
	Load  "evdev"
EndSection
> Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
        Option 	    "Buttons" "10"
	Option	    "ZAxisMapping" "6 7 4 5"
	Option	    "Emulate3Buttons" "no"
EndSection

Again evdev doesnt want to work when I set it as the driver and mx600 and event1. I have commented out all the Option's that have to do with the buttons. The only thing I can see that I haven't tried yet is "Option "CorePointer"". I guess I can try that one next just to see if it works.

Thanks for any help,
TigerCR1200

**The CorePointer was the problem. I always thought that was a requirement for xorg to know which pointer to use.**

---

### Post by kogber on 2007-01-23
TigerCR1200,

Like I wrote in the guide,
> Make sure that the bold mx610 name part corresponds to the name part in the file 19-local.rules that we made before.

In your case, your InputDevice section in xorg.conf would be:

```
Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "evdev"
  Option "Device" "/dev/input/**mx600**"
EndSection
```

You should get rid of all of the other stuff in the InputDevice section since you are using evdev, ie the CorePointer, ZAxisMapping and Emulate3Buttons lines.

btw, when you do cat /proc/bus/input/devices you are going to get 2 instances of the Logitech USB Receiver device, because it uses two usb logical interfaces, one for the standard mouse events, and one for the extra buttons.  The one for the actual mouse events contains the line "Handlers=mouse0...".  The one you pasted here is for the other mouse events that are simulated keyboard events, "Handlers=kbd event2" (kbd stands for keyboard).

---

### Post by taximorph on 2007-01-28
Excuse my noobishness, but I have to precede the commands with sudo to make the LEDs work. Is there some way round this, other than logging in as root?

---

### Post by kogber on 2007-01-28
taximorph, you can change permissions on the compiled mx610hack so that it is executable by all users.  Open up a console and launch nautilus/konqueror as a superuser:

```
sudo nautilus /usr/local/bin
```

mx610hack should be here.  Right click, select Properties.  Find the permissions options, and make sure it is executable by group and others.

---

### Post by taximorph on 2007-01-29
> **kogber said:**
> taximorph, you can change permissions on the compiled mx610hack so that it is executable by all users.  Open up a console and launch nautilus/konqueror as a superuser:

```
sudo nautilus /usr/local/bin
```

mx610hack should be here.  Right click, select Properties.  Find the permissions options, and make sure it is executable by group and others.

Thanks kogber, that's brilliant :D

---

### Post by Dankoozy on 2007-01-29
Tis good to see that blog post going to so much good use :)

---

### Post by steffen on 2007-01-30
I just got a Microsoft Wireless Presenter 3000 ([http://www.microsoft.com/hardware/Presenter/productdetails.aspx?pid=092](http://www.microsoft.com/hardware/Presenter/productdetails.aspx?pid=092)) that wasn't auto-detected by Ubuntu (Edgy).

Here's output from dmesg:

> [17278045.248000] usb 2-2: new low speed USB device using uhci_hcd and address 11
[17278045.480000] usb 2-2: configuration #1 chosen from 1 choice
[17278045.500000] input: Device USB Device as /class/input/input17
[17278045.500000] input: USB HID v1.11 Keyboard [Device USB Device] on usb-0000:00:1d.1-2
[17278045.528000] input: Device USB Device as /class/input/input18
[17278045.528000] input: USB HID v1.11 Mouse [Device USB Device] on usb-0000:00:1d.1-2

and from "cat /proc/bus/input/devices"
> I: Bus=0003 Vendor=05fe Product=2002 Version=0210
N: Name="Device USB Device"
P: Phys=usb-0000:00:1d.1-2/input1
S: Sysfs=/class/input/input18
H: Handlers=kbd mouse3 event7 ts3 
B: EV=7
B: KEY=30000 0 20000 3878 d801d101 1e0000 0 0 0
B: REL=3

Anyone know how I can get this thing connected and working?

---

### Post by kogber on 2007-01-30
steffen, assuming this usb device doesn't use a proprietary means of communication that requires the MS driver, it probably sends out keycodes like most devices.  If this is the case, you could figure out the keycodes and map them.  Heres an example:

[http://michael-prokop.at/blog/2006/05/14/using-targus-wireless-multimedia-presenter-with-linux/](http://michael-prokop.at/blog/2006/05/14/using-targus-wireless-multimedia-presenter-with-linux/)

Since I don't have this device or a similar one, I'm not sure I can be of much help.  Please post about this issue in a new or relevant thread.

---

### Post by hellraiser_rob on 2007-02-01
Thanks for the howto, it worked well apart from with one minor problem for my mx700, the scroll wheel doesn't work properly, for some reason it also acts and a forward/backward button.

Does anyone have any suggestions for this?  Cheers.

Rob

---

### Post by benbuleong on 2007-02-02
Hi,

There seems to be so many smart guys here, so I 'll post for help,
I followed the steps closely and got my mouse working, but it'll becomes dead every time after I come back from a screen saver or even after a few minutes of use. I am not sure what triggered this problem. After rebooting, the mouse works PERFECT, but only for so much...

Any ideas please ?

---

### Post by kogber on 2007-02-02
benbuleong, that sounds terrible.  Are you sure its not a low battery issue of some sort?  Did the mouse work fine before this guide?  I think I need some more history and details about your mouse and OS to try and help.

---

### Post by benbuleong on 2007-02-02
yes, kogber.

In fact, the mouse did work before everything ( before I came to this forum). It's jsut that it's always dead halfway. Not battery problem because it's fully charged.

I am using Toshiba M55-S139 laptop with dual boot, with the other running windows. Ubuntu version 6.1 and Logitech MX 610.

I did the automatic installation of ubuntu since I am a novice in Linux. Everything works well (even my wireless network card !) after the installation completed. Indeed, everything but the mouse.

I have bought a corded USB mouse in case there is no solution -- don't wanna spend so much time doing the configuration and have to get to my programming. 

If you know anything, please let me know ! It'll be very much appreciated !

benbuleong

---

### Post by kogber on 2007-02-02
I'm not sure I understand your line, "It's just that it's always dead halfway".  Did the mouse freeze in Ubuntu before you tried this guide?  Does the mouse work fine in windows?

---

### Post by benbuleong on 2007-02-02
I think I found someone else who had the same problem. It's not the problem with the mouse. I just changed to my corded mouse and exactly the same thing happened -- again.

[http://ubuntuforums.org/showthread.php?t=311462&page=2&highlight=m55-S139](http://ubuntuforums.org/showthread.php?t=311462&page=2&highlight=m55-S139)

But, how can I edit the grub ? Can someone highlight the steps ?

---

### Post by trenog on 2007-02-09
I have a problem myself. I did exactly as the first post said, but only the Back, Forward buttons work and for some reason the left scroll is considered Back as well. 

I was looking to get the Zoom+ button to be Volume+ instead and Zoom-, Volume-. Finally, the 100% button I would like to work as a Play/Pause. I say these things because they don't work like that and have no affects after the changes. I've got a Logitech mx600 mouse.

Thanks for any help!

---

### Post by kogber on 2007-02-09
trenog, the mx600 is different from the mx610, in a hardware sense.  I have this mouse as well, and I know what you mean.  I posted earlier in this thread about the mx600,

> I actually have an mx600 mouse/keyboard set, so I booted up Ubuntu on my desktop and tested it out. The back/forward works in firefox and the File Browser, but the zoom in/out buttons are not being registered (only the 100% button is being detected). On the flipside, the horizontal scroll events are being detected by the kernel, so I should be able to get that working whenever I get some time to play around with it.

I have to admit I haven't actually tried to get the horizontal scrolling to work.  You can use the 100% button as play/pause, as long as you map the associated button in the xbindkeysrc file.  I have no idea why the zoom in/out buttons aren't being detected by Ubuntu.  If you manage that part, then you can map them in the bind file as well.

---

### Post by Rabbit_Alex on 2007-02-13
Does anyone know if the next Ubuntu release, Feisty Fawn, will include better detection and support for Logitech mice?

---

### Post by scallywag87 on 2007-02-28
As a quick solution to your horizontal scrolling problem:

1. install 'xev':   sudo apt-get install xev

2. run xev:          xev

3. press a button on your mouse while xev is open.  This should return a value for the button on the mouse.
[INDENT]Ex: "ButtonRelease event, serial 29, synthetic NO, window 0x3800001,[/INDENT]
    [INDENT]root 0x1a5, subw 0x0, time 189102494, (74,24), root:(84,121),[/INDENT]
    [INDENT]state 0x100, *button 1*, same_screen YES"[/INDENT]
"button 1" indicates the left click of my mouse (I'm actually using a VX Revolution, but the process should be the same).

4. add to .xbindkeysrc with the same key binds used earlier in this guide, but substitute your buttons for left and right tilt into the button labels.  Also, change the key bind to "\[Left]" and "\[Right]" respectively (with capital first letters).

This may not be the best method for getting horizontal scroll, but it worked well for me.

P.S. You can use this same process to bind any of the buttons on your mouse.  I was able to bind my zoom keys to "\[Control]\[plus]" and "\[Control]\[minus]" to get zoom in nautilus and firefox.

Here is what my .xbindkeysrc looked like after I finished binding all buttons on my mouse:

#Backward
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8

#Forward
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9

#Left Tilt
"/usr/bin/xvkbd -xsendevent -text "\[Left]""
  m:0x0 + b:7

#Right Tilt
"/usr/bin/xvkbd -xsendevent -text "\[Right]""
  m:0x0 + b:6
#I'm aware of the obvious confusion of the buttons being switched (left and right - 7 and 6), 
#but that is just how it worked out between 'xev' and testing

#Zoom In
"/usr/bin/xvkbd -xsendevent -text "\[Control]\[plus]""
  m:0x0 + b:13

#Zoom Out
"/usr/bin/xvkbd -xsendevent -text "\[Control]\[minus]""
  m:0x0 + b:14

---

### Post by mbvlist on 2007-03-08
All right, I've got this set up. It doesn't add any functionality: Edgy already detected 3 buttons, scrollwheel, volume and email correctly. I have this vague idea it doesn't work: scroll left/right doesn't give any output on xev :(.

So first of all: how do I check my mouse works using the rules set up in this howto? 

Now the real problem is, I bought a lefthanded MX610. It has the mouse-buttons swapped (because it's left-handed), but I am more used to the right-handed setup. How do I setup this mouse to swap button 1 and 3, without interfering the other input devices? I don't like my touchpad with the buttons reversed ;)

---

### Post by computergee on 2007-03-14
Thanks for the great advice, I got all my buttons and lights working except horizontal scrolling. I recently tried out PCLinuxOS 2007 Test Release 2, and horizontal scrolling worked out of the box! I grew accustomed to it, and now miss it dearly now that I'm back in Ubuntu. I'm curious as to why it worked out of the box in PCLinuxOS though, here are the bits of the xorg.conf file I used when horizontal scrolling worked in PCLinuxOS, which may help us getting it working here.

```
Section "ServerLayout"
    Identifier "layout1"
    InputDevice "Keyboard1" "CoreKeyboard"
    InputDevice "Mouse1" "CorePointer"
    InputDevice "Mouse2" "SendCoreEvents"
    Screen "screen1"
EndSection

Section "InputDevice"
    Identifier "Mouse1"
    Driver "mouse"
    Option "Protocol" "ExplorerPS/2"
    Option "Device" "/dev/mouse"
EndSection

Section "InputDevice"
    Identifier "Mouse2"
    Driver "evdev"
    Option "product" "0xc518"
    Option "vendor" "0x046d"
    Option "HWheelRelativeAxisButtons" "7 6"
EndSection

```

I've been messing with it hoping to get it to work, but I've had no such luck. Maybe you guys will.

---

### Post by TerrorAndHubris on 2007-05-20
I've followed the instructions in the OP, only to have no effect. Using Feisty with an MX610. I greatly wish to get not only the forward/back working, but the sidescroll as well (I'd love to use that as a desktop switching toggle).

Also, xev does not respond to either side scroll direction. What could be wrong?

---

### Post by foug on 2007-05-23
I'd also like to get my side buttons working so I can bind them to things in WoW and other programs. right now my two side buttons mimic middle click and right click. Does yours do that as well?

---

### Post by weatherman1293 on 2007-05-24
I get the following error:

```
make[1]: Entering directory `/home/mike/mx610hack'
source='mx610hack.c' object='mx610hack.o' libtool=no \
        DEPDIR=.deps depmode=none /bin/bash ./depcomp \
        gcc -DHAVE_CONFIG_H -I. -I. -I.    -Wall -W -g -O2 -c mx610hack.c
/bin/bash: ./depcomp: No such file or directory
make[1]: *** [mx610hack.o] Error 127
make[1]: Leaving directory `/home/mike/mx610hack'
make: *** [all] Error 2

```

---

### Post by Guilo on 2007-07-08
Thanks for your guide.


But it doesn't work for me :(

Here is my X log (what concerns evdev) :

(II) evdev brain: Rescanning devices (1).
(EE) PreInit returned NULL for "Mouse[1]"
(WW) <default pointer>: No Device specified, looking for one...
(II) <default pointer>: Setting Device option to "/dev/input/mice"
(--) <default pointer>: Device: "/dev/input/mice"
(==) <default pointer>: Protocol: "Auto"
(**) Option "AlwaysCore"
(**) <default pointer>: always reports core events
(==) <default pointer>: Emulate3Buttons, Emulate3Timeout: 50
(**) <default pointer>: ZAxisMapping: buttons 4 and 5
(**) <default pointer>: Buttons: 9
(WW) No core pointer registered
(II) XINPUT: Adding extended input device "<default pointer>" (type: MOUSE)
(II) XINPUT: Adding extended input device "evdev brain" (type: evdev brain)
(II) XINPUT: Adding extended input device "Keyboard[0]" (type: KEYBOARD)
(II) evdev brain: Rescanning devices (2).
(--) <default pointer>: PnP-detected protocol: "ExplorerPS/2"
(II) <default pointer>: ps2EnableDataReporting: succeeded
No core pointer

Fatal server error:
failed to initialize core devices

---

### Post by abrichr on 2007-07-20
Great guide, I've still to customize the xbindkeys config file, but the back/forward buttons are definitely useful.

The middle mouse button, however, doesn't work.  How can we enable this?

---

### Post by dasunst3r on 2007-08-25
Thanks for the guide.  Here's a little something you could add:
[http://koti.mbnet.fi/simom/pidgin/mx610-notification/](http://koti.mbnet.fi/simom/pidgin/mx610-notification/)

---

### Post by skattyadz on 2007-08-27
Hey. Bear with me I'm new to linux and stuff =]

This worked for me but I'd like to change the back and forward buttons to change desktops. I'm running compiz fusion so I'm sure theres a shortcut somewhere I guess. 

Other thing is that the  horizontal scrolling buttons come up as keyboard buttons left and right. If i try changing it it also affects my keyboard! Could there be any way to isolate those buttons from the keyboard, if possible I'd like to set that up for switching tabs in FF. 

Is there any way to map my extra keyboard buttons on my Logitech keyboard?

Thanks

Edit:

I tried this but it didnt work for changing desktops

I think I'm not calling the keys right.

```
# Flip Tabs buttons
"xvkbd -xsendevent -text "\[Alt_L]\[Control]\[Left]""
m:0x0 + b:8
"xvkbd -xsendevent -text "\[Alt_L]\[Control]\[Right]""
m:0x0 + b:9

```

---

### Post by dp_wiz on 2007-09-25
Can't manage to get buttons other than volume(x3) and email which are working OotB.
Tried every hack around. Can someone post their full xorg.conf for working stuff in gutsy(or feisty)?

---

### Post by Sturmeh on 2007-10-08
> **skattyadz said:**
> 
I tried this but it didnt work for changing desktops

I think I'm not calling the keys right.

```
# Flip Tabs buttons
"xvkbd -xsendevent -text "\[Alt_L]\[Control]\[Left]""
m:0x0 + b:8
"xvkbd -xsendevent -text "\[Alt_L]\[Control]\[Right]""
m:0x0 + b:9

```

Yeah I think it presses the keys in order, but keeps them held down, beause it doesn't seem to work for me either. ( besides it would be "Ctrl_L" wouldn't it? )


> **TerrorAndHubris said:**
> I've followed the instructions in the OP, only to have no effect. Using Feisty with an MX610. I greatly wish to get not only the forward/back working, but the sidescroll as well (I'd love to use that as a desktop switching toggle).

Also, xev does not respond to either side scroll direction. What could be wrong?

This guide allows you to map the keys as you like, the Forward/Back is the same as the side scroll, there are only 2 buttons for this function.

The Sideways scroll you mentioned is also called "horizontal scroll" which is said to be unworkable...


> **foug said:**
> I'd also like to get my side buttons working so I can bind them to things in WoW and other programs. right now my two side buttons mimic middle click and right click. Does yours do that as well?

Follow this guide and you can map them to any keyboard key you like...


> **dasunst3r said:**
> Thanks for the guide.  Here's a little something you could add:
[http://koti.mbnet.fi/simom/pidgin/mx610-notification/](http://koti.mbnet.fi/simom/pidgin/mx610-notification/)

Hey thanks, but I had a little troubles with the make file, you need to edit it so it points to /usr/lib/pidgin/ instead of ~/.pidgin/plugin/ ... heh.


> **dp_wiz said:**
> Can't manage to get buttons other than volume(x3) and email which are working OotB.
Tried every hack around. Can someone post their full xorg.conf for working stuff in gutsy(or feisty)?

Make sure you follow the guide completely, I'm on Feisty, and it works.


:popcorn: <-- munch, munch.

---

### Post by kingster80 on 2007-10-15
First of all, Thank you for this tutorial, worked like a charm (almost).

By the way im a complete noob, so bare with me...
I followed your guide meticulously, and found everything to work.

my only problem is that when i add xbindkeys to "System > Preferences > Sessions" it doesnt automatically start when i reboot. I need to go to the terminal and use su for root privileges and then type xbindkeys for things to work.

I'm just guessing here, but it seems to me that i need some root privileges to run the command.

any ideas are very appreciated. Thanks again

---

### Post by Jiawen on 2007-10-21
I'm having a weird problem in Gutsy (7.10). I've done all the instructions, and the forward and back buttons work fine, but the volume buttons (+, -, mute) do nothing. Doing "amixer set PCM 1+" in a terminal works fine, so that appears to be configured correctly. But doing the same thing from my MX610 does nothing. This all worked perfectly under 7.04, though. 

Anyone know what's going on?

---

### Post by Mazen on 2007-12-14
My xorg file doesn't have the "Module" part!
it used to work in Feisty but not anymore in Gutsy!
is there a work around?!

---

### Post by boom2k1 on 2008-02-02
thanks!

---

### Post by Sturmeh on 2008-02-28
> **Mazen said:**
> My xorg file doesn't have the "Module" part!
it used to work in Feisty but not anymore in Gutsy!
is there a work around?!

Look harder sir!

It's there, I just did a fresh Gutsy install, and it's there with only 2 modules by default, you may have more or less.

If you are ABSOLUTELY CERTAIN it's not there, you can make the section. ( Because gutsy DOES use it. )

---

### Post by momsab on 2008-03-28
better solution: btnx [http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)

---

### Post by nyarlathotep77 on 2009-11-03
Howdy all,

after a clean installation of Karmic Koala I had lost my Logitech MX610.

I realized that hacking about the xorg.conf is no more recommended, so I created a fdi file containing:
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
	<device>
		<match key="info.product" string="MX610 Laser Cordless Mouse">
		 <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
		 <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
		</match>
	</device>
</deviceinfo>

```

Now this works ok and I can use my mouse, but the only problem is that to get it working after any reboot I need to plug out and re-plug the usb dongle.

Any clue about how to have my mouse up and running after rebooting?

Cheers!

---

### Post by jw5801 on 2009-11-03
> **nyarlathotep77 said:**
> Howdy all,

after a clean installation of Karmic Koala I had lost my Logitech MX610.

I realized that hacking about the xorg.conf is no more recommended, so I created a fdi file containing:
```

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
	<device>
		<match key="info.product" string="MX610 Laser Cordless Mouse">
		 <merge key="input.x11_options.YAxisMapping" type="string">4 5</merge>
		 <merge key="input.x11_options.XAxisMapping" type="string">6 7</merge>
		</match>
	</device>
</deviceinfo>

```

Now this works ok and I can use my mouse, but the only problem is that to get it working after any reboot I need to plug out and re-plug the usb dongle.

Any clue about how to have my mouse up and running after rebooting?

Cheers!

It depends on your desktop environment. Most of them seem to want to try and configure mouse settings and all that themselves, so when the session manager starts it overwrites whatever settings hal put in, which is irritating, to say the least.

As a workaround, you can try using xinput to set the properties in a script which is run after login, however that's no simple task.

---

### Post by nyarlathotep77 on 2009-11-12
Hi,

unfortunately I don't quite exactly know how to use xinput for my purpose.

Has anybody worked out how to get the mx610 work under 9.10?
Mine works only after plug out and in. Used to be fine under 9.04.

If I logout and re-login I loose the mouse and need to plug out and in again.

Please heeelp!!! It's really hard yakka here!

Cheers!

---

### Post by nyarlathotep77 on 2009-11-14
Hi,

this problem is really driving me mad.

I tried the solution at [https://wiki.ubuntu.com/X/Config/Input#Troubleshooting]("https://wiki.ubuntu.com/X/Config/Input#Troubleshooting") which consists in changing the priority by which gdm gets executed compared to hal, but it doesn't work.

Yet, in 9.10 hal got deprecated and apparently replaced by something called device-kit.

Has anybody a clue whether this could be the problem?

In fact in order to give gdm a lower priority than hal, there should be some hal reference in some of the directories /etc/rc?.d, but I cannot find anything related to hal, so that might be the reason why the troubleshooting explained at the link above doesn't work in 9.10.

Hope somebody can find a solution about this, I'll keep investigating meanwhile.

Cheers

---

### Post by Ventil on 2009-11-15
Great guide but I have a problem now. I don't have amixer installed. I only use pulseaudio. Does anyone knows the commands for increase|decrease|mute volume for pulseaudio.
Thanks
```
# sad note - the IM button is not a real button - as far as I can tell

# Volume +
"amixer set PCM 1+"
m:0x0 + c:176

# Volume -
"amixer set PCM 1-"
m:0x0 + c:174

# Mute
"amixer set PCM toggle"
m:0x0 + c:160
```

---

### Post by Ventil on 2009-11-16
anyone?

---

### Post by NaskoD on 2011-09-07
I'm with Ubuntu 10.04 LTS and I don't have xorg.conf file in the file system at whole. Till step 5 my forward and backward buttons are working but no volume buttons.

---

