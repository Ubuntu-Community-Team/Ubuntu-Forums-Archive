---
title: "Why don't 5 button mice work out of the box in Linux/Ubuntu"
date: 2007-10-05
forum: The Cafe
---

### Post by treis on 2007-10-05
I'm looking for an explanation here, not trying to rip on anyone.  

I don't know the first thing about programming or drivers, but it seems to me that the mouse is the simplest device to drive.  Gutsy is able to detect and properly configure every piece of hardware on my laptop (with the restricted driver manager of course).  Even the touch button play/pause, forward, back, volume, and mute buttons work, yet a simple 5 button mouse is beyond it.  I don't think it's a driver issue because, well, it's a wireless mouse and it works.  Heck, it even identifies the model.  Yet the back/forward buttons just don't work out of the box, and there isn't any easy way to get it working.  What gives?

---

### Post by kidders on 2007-10-06
Hi there,

I've always assumed the reason for Linux's flakiness with mice that have lots and lots of buttons is that the time & effort that would have to go into accounting for every type of mouse in existence outweighs the benefit users would gain, especially given that (a) configuring mice manually is, by and large, trivial, and (b) any default behaviour assigned to buttons 6, 7, 8... probably wouldn't be what many user want, so they'd have to reconfigure their mouse themselves anyway.

I'm not sure if I think that's a reasonable excuse ... it's just the only decent explanation I can come up with hehe. In general, I find Xorg's management of all input devices quite unsatisfactory, but people tend to sort of get used to it, I suppose.

Having said that, even though a 10-button mouse might be problematic, most 5-button mice should work perfectly well out of the box. Linux users have always liked their "middle" mouse button -- Xorg can even emulate it for users that don't have one -- and virtually all modern mice have a scroll wheel these days, so you really shouldn't be having problems imo.

I'm curious...

[LIST]
[*]What mouse do you have?
[*]Which buttons are giving trouble?
[*]Is it that they don't work, or do they do the wrong thing? (Eg your scroll wheel is inverted for no reason.)
[*]Does xev recognise the problematic buttons?
[/LIST]

I have a Logitech MX Revolution ... one of the most difficult mice to configure in Linux, for a number of reasons:
[LIST]
[*]At the driver level, it is a mouse & keyboard combined.
[*]It falls victim to some weirdness in the current evdev.
[*]It essentially has no "second" mouse button.
[/LIST]
Your problems could be caused by these (or other) pitfalls, but I'd be happy to help you sort it out.

---

### Post by Spike-X on 2007-10-06
Do they work out of the box under Windows, or do you have to install special software?

---

### Post by ssam on 2007-10-06
i think the poster is saying is that the mouse and main buttons work fine, but the extra buttons are not configured to do anything. (this is my experience with logitech mice).

currently to make the buttons useful one has to edit the xorg.conf to get X to recognise the events. and then use extra software to map them to something useful.

there is a bug report

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/42678](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/42678)

in which it says.

> 
In Hardy we will upgrade to xorg-server which has input hotplug capabilities. With that feature, we may be better able to address input features such as this one, or perhaps add better GUI config tools or something. Currently, there's not a clear way of getting this to work out of the box.


---

### Post by stimpack on 2007-10-06
They work out-of-the-box in Windows, MS Intellimouse and Logitech MX. Drivers can provide extra things like changing DPI, but all the buttons work.

Usually its Linux that is better out-of-the-box, has to be, we don't have drivers :). But Windows wins this one.

I'd say Logitech MX and MS Intellimouse, should fully work, can't think of a reasonable excuse. Maybe others too, but these 2 are the 'big guns'.

---

### Post by Pekkalainen on 2007-10-06
I have myself posted requests regarding this issue for the last 4 releases of Ubuntu, no one seems to care about it so Im stuck with 3 out of 5 buttons working on my MX510 :(

I have tried the guides posted here on the forum but no matter what I do I end up crashing Xorg. I was able to get it working in Hoary the last time and it was after about 3 hours of head ache. Dont call it trivial please :mad:

---

### Post by kidders on 2007-10-06
> **Pekkalainen said:**
> Dont call it trivial please :mad:Hehe sorry ... things are only easy if you know how.

Since both you and treis seem to be having problems, we might as well go from the beginning. Basically, the first thing to do is to see whether Xorg can see you push all your mouse buttons or not, with xev. If not...[LIST]
[*]You may be using the wrong input driver. Other than the one called "mouse", you could try one called "evdev".
[*]You might need to spoon-feed Xorg a little. Normally, it tries to detect how many buttons you have, and so on, but it sometimes makes mistakes, much as it can do on occasion with things like video RAM.
[/LIST]
If you can arrive at a point where xev recognises all your buttons, you're half way there. The next jobs are...[LIST]
[*]Make sure your buttons are in the right order.
[*]Assign some functionality to them.
[/LIST]

---

### Post by Teh Dust on 2007-10-06
I remember back when I tried using Fedora Core 6 and the only thing that impressed me was the default cursor and that the 5 button logitech mouse I had at the time worked out of the box. If Fedora can do it, why not Ubuntu?

---

### Post by Pekkalainen on 2007-10-06
> **kidders said:**
> Hehe sorry ... things are only easy if you know how.

Since both you and treis seem to be having problems, we might as well go from the beginning. Basically, the first thing to do is to see whether Xorg can see you push all your mouse buttons or not, with xev. If not...[LIST]
[*]You may be using the wrong input driver. Other than the one called "mouse", you could try one called "evdev".
[*]You might need to spoon-feed Xorg a little. Normally, it tries to detect how many buttons you have, and so on, but it sometimes makes mistakes, much as it can do on occasion with things like video RAM.
[/LIST]
If you can arrive at a point where xev recognises all your buttons, you're half way there. The next jobs are...[LIST]
[*]Make sure your buttons are in the right order.
[*]Assign some functionality to them.
[/LIST]

Xev sees all the buttons. I tried using Evdev as driver but Xorg refuses to use it and crashes when I restart X. Thats the point I got to so far in Feisty. By the way I have the mouse connected to USB and used the guide intended for that. 

I did however, as I wrote this bitter reply find a guide that seems to work: [http://ubuntuforums.org/showthread.php?t=485175&highlight=logitech+mice](http://ubuntuforums.org/showthread.php?t=485175&highlight=logitech+mice)

Nevermind I guess :lolflag:

---

### Post by -grubby on 2007-10-06
> **Spike-X said:**
> Do they work out of the box under Windows, or do you have to install special software?

exactly! I had to do that for my Microsoft Intellimouse. even though the other 2 side buttons don't work, I've never used them anyway.

---

### Post by treis on 2007-10-06
> **kidders said:**
> 
[LIST]
[*]What mouse do you have?
[*]Which buttons are giving trouble?
[*]Is it that they don't work, or do they do the wrong thing? (Eg your scroll wheel is inverted for no reason.)
[*]Does xev recognise the problematic buttons?
[/LIST]


I had an Intellimouse and currently have a logitech MX1000

The back/forward buttons don't do anything.  IIRC with my Intellimouse the scroll button was originally back/forward, and the back/forward buttons didn't do anything.

I've had both of them working but after a disastrous attempt to set up dual monitors my xorg.conf got fuxxored, and I ended up using the opportunity to upgrade to Gutsy.  I just don't feel like mucking around in xorg.conf because of the potential to break my system.  

I guess I just don't understand.  I see two very simple and easy ways to fix the problem.

(1)  The thing is that my system recognizes the mouse.  It gives me options to change the sensor resolution, shows me the battery life, and allows me to change the RF channel.  Assuming this is true for other mice, have a database of proper xorg.conf settings.  A user plugs in a mouse, the system recognizes it and updates xorg.conf.  Even if it doesn't do all that automatically have a little program that has a drop down menu.  The user runs the program, selects his/her mouse, and it updates it for them.

(2) Have a program like the old joy stick configuration programs.  Have it prompt "left click", and record what the user clicks for left click.  Do so for every button and it will be configured.  


I don't remember having to install a driver for a mouse ever.  I'm only 21, but I've been using computers since I was 6, and I was the computer guy in the house so I would have remembered.  Every thing was just plug and play.  I will admit that I used a standard 3 button mouse until XP.  However, I have no doubt that if I plug in my logitech mouse into a computer running XP that it would work immediately.

---

### Post by RAV TUX on 2007-10-06
> **treis said:**
> I'm looking for an explanation here, not trying to rip on anyone.  

I don't know the first thing about programming or drivers, but it seems to me that the mouse is the simplest device to drive.  Gutsy is able to detect and properly configure every piece of hardware on my laptop (with the restricted driver manager of course).  Even the touch button play/pause, forward, back, volume, and mute buttons work, yet a simple 5 button mouse is beyond it.  I don't think it's a driver issue because, well, it's a wireless mouse and it works.  Heck, it even identifies the model.  Yet the back/forward buttons just don't work out of the box, and there isn't any easy way to get it working.  What gives?I have a 7 button mouse that works by default in Xubuntu.

I use Xubuntu 7.10 just for reference but it worked in Xubuntu 7.04 also.

I use a Razer Copperhead, which btw I originally bought for my wife to use on her Convertible(notebook/tablet) computer that uses Windows XP Tablet Edition 2005 and even with the special software from Razer the mouse would not work on Windows!!!...imagine that a mouse designed for Windows and it simply did not work!...but it works by default in Linux!

---

### Post by southernman on 2007-10-06
> **treis said:**
> I had an Intellimouse and currently have a logitech MX1000

The back/forward buttons don't do anything.  IIRC with my Intellimouse the scroll button was originally back/forward, and the back/forward buttons didn't do anything.

I've had both of them working but after a disastrous attempt to set up dual monitors my xorg.conf got fuxxored, and I ended up using the opportunity to upgrade to Gutsy.  I just don't feel like mucking around in xorg.conf because of the potential to break my system.  

I guess I just don't understand.  I see two very simple and easy ways to fix the problem.

(1)  The thing is that my system recognizes the mouse.  It gives me options to change the sensor resolution, shows me the battery life, and allows me to change the RF channel.  Assuming this is true for other mice, have a database of proper xorg.conf settings.  A user plugs in a mouse, the system recognizes it and updates xorg.conf.  Even if it doesn't do all that automatically have a little program that has a drop down menu.  The user runs the program, selects his/her mouse, and it updates it for them.

(2) Have a program like the old joy stick configuration programs.  Have it prompt "left click", and record what the user clicks for left click.  Do so for every button and it will be configured.  


I don't remember having to install a driver for a mouse ever.  I'm only 21, but I've been using computers since I was 6, and I was the computer guy in the house so I would have remembered.  Every thing was just plug and play.  I will admit that I used a standard 3 button mouse until XP.  However, I have no doubt that if I plug in my logitech mouse into a computer running XP that it would work immediately.

I feel ya! I use/have used the MS Intellimouse (5-button) for a few years now. IIRC, it works plug and play on xp, but not for ubuntu. While it is just a simple matter of editing the xorg.conf file to make the forward/back buttons work as they are supposed to, you'd think it could be made to work in *nix also... plug and play

Honestly, to me it is a trivial issue, but it is an issue none-the-less!

---

### Post by victor_c26 on 2007-10-07
What about the new G9 from Logitech?

---

### Post by LowSky on 2007-10-08
this is what your xorg.conf file should have as your mouse options if you want to use logitech 510 or higher mouse

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option          "Buttons"               "7"
	Option          "ButtonMapping"         "1 2 3 6 7"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection

```

---

### Post by sp0onman on 2007-10-08
i used this guide to get all my buttons on mx1000 working :
[https://help.ubuntu.com/community/MX1000Mouse]("https://help.ubuntu.com/community/MX1000Mouse")
best mouse ever, the shape is perfect for me, and have been using it since it came out, probably 2 or 3 years ago now?

---

### Post by macogw on 2007-10-08
My 5-button Logitech mouse worked out-of-the-box with Feisty....until it died when it crossed the border into Washington, DC.  I've lost 2 mice (the other was a wireless 5-button Microsoft mouse which also worked out of the box), 2 keyboards, and 1 mp3 player to crossing that border.  I've also had an AC power adapter and a short in my motherboard develop within 2 weeks of crossing that border.

---

### Post by RageOfOrder on 2007-10-08
I use a logitech G5 myself. By letting Evdev pick up the buttons I don't have to manually assign anything. Have a look:

This is my mouse entry in /etc/X11/xorg.conf

```

Section "InputDevice"
     Identifier            "Mouse0"
     Driver                  "evdev"
     Option                 "evBits" "+1-2"
     Option                 "keyBits" "~272-287"
     Option                 "relBits" "~0-2 ~6 ~8"
EndSection

```

You have to make sure that evdev is loaded (modprobe evdev) before X loads or it won't work. For gentoo that's as easy as entering 

```

# echo "evdev" >> /etc/modules.autoload.d/kernel-2.6

```

I'm not sure how that holds up with *buntu

---

### Post by spoilerhead on 2007-10-08
Thats my mouse driver block on my notebook. just ignore the touchpad part
the mouse part has no problems handling mutliple mice (mx512, old logitech optical).

the important thing to get all mice working with hotplug on the fly is to remove every "corepointer" section

yes, all buttons work without problem in all applications that support multiple mouse buttons (i.e. FF)
```

#mice
Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "evdev"
        Option      "SendCoreEvents" "true"
        Option      "Name" "Logitech USB-PS/2 Optical Mouse"
        Option      "Emulate3Buttons" "true"
        Option      "ZAxisMapping" "4 5 6 7"
        Option      "Buttons"   "12"
        Option      "Resolution"    "400"
        Option "AllowMouseOpenFail" "true"

EndSection

#touchpad
Section "InputDevice"
        Identifier  "Synaptics Touchpad"
        Driver      "synaptics"
        Option          "SendCoreEvents" "true"
        Option      "SendCoreEvents" "true"
        Option      "Device" "/dev/psaux"
        Option      "Protocol" "auto-dev"
        Option      "HorizScrollDelta" "0"
        Option      "LeftEdge" "1700"
        Option      "RightEdge" "5300"
        Option      "TopEdge" "1700"
        Option      "BottomEdge" "4200"
        Option      "FingerLow" "25"
        Option      "FingerHigh" "30"
        Option      "MaxTapTime" "180"
        Option      "MaxTapMove" "220"
        Option      "VertScrollDelta" "100"
        Option      "MinSpeed" "0.10"
        Option      "MaxSpeed" "0.12"
        Option      "AccelFactor" "0.0015"
        Option      "ZAxisMapping" "4 5"
        Option      "YAxisMapping" "6 7"
EndSection


```

---

### Post by Griffongob on 2007-12-12
Sorry to rez an old thread like this but has anyone gotten a Razor Death Adder working with all 5 buttons?

---

### Post by SunnyRabbiera on 2007-12-12
well these multimedia mice are bound to cause issues, but maybe its possible to configure the system to use at least most of the buttons.
I know my multimedia keyboards dont work 100% in linux but really I dont give a crap if I can press a button and my internet comes up, I can do without it.

---

### Post by boast on 2007-12-22
> **Spike-X said:**
> Do they work out of the box under Windows, or do you have to install special software?

my mx510 buttons worked in a fresh install of windows.

---

### Post by hanzomon4 on 2007-12-22
Why would you even need 5 buttons?

---

### Post by Lostincyberspace on 2007-12-22
Pause and play amarok, Next , Previous , backward forward in firefox.

---

### Post by Lostincyberspace on 2007-12-22
Does any one know how this works with Linux?
Logitech MX Revolution
I have been looking at it a long time and I think I want to get it.

---

### Post by kidders on 2007-12-22
> **Lostincyberspace said:**
> Does any one know how this works with Linux?
Logitech MX Revolution
I have been looking at it a long time and I think I want to get it.

It works just fine, once you tell Xorg about the button/wheel configuration. Strangely, I've found that the buttons aren't all sequentially numbered (which is odd!), and one of them has a keycode, rather than a button number. I was a bit perplexed by that one at first, but it's actually kinda handy. :-)

---

### Post by yatt on 2007-12-22
> **Spike-X said:**
> Do they work out of the box under Windows, or do you have to install special software?
They work out of the box on Windows. Left, Right, Middle, Forward, and Back all work out of the box on Windows. (Logitech MX518)
On Linux I had only Left, Right, and middle.

---

### Post by prizrak on 2007-12-23
A 5 button mouse works for me w/o a problem. Well it's really more like a 4 button mouse because it's a laptop and doesn't have a real clicable scroller. It would be a 5 button mouse had it been on a desktop. 
It breaks down like this:
1 - Touchpad, moves the pointer around
2 - Tap to click/left button, left click
3 - Right button, right click
4 - Side of the touchpad/down/up scroller, scrolls the text
5 - Left/right scroller goes forward/back through webpages
6 - Left + Right button, emulates middle click.
goes forward/back through webpages
Normal desktop 5 button mouse breakdown
1 - Mouse, obviously
2 - Left button, left click functionality
3 - Right button, right click functionality
4 - Scrolling wheel, vertical(possibly also horizontal) scroll
5 - Side button 1/2 goes forward/back through webpages
6 - Clicking the wheel, middle click functionality

This setup has worked for me since Dapper without any issues so it would appear as if Ubuntu is able to recognize and setup 5 button mice. It seems as if it is incapable of doing it to all the mice. Also it seems that with some tuning software for touchpads you can have many more buttons.

---

