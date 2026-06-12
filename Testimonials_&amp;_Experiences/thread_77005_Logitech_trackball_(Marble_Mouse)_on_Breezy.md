---
title: "Logitech trackball (Marble Mouse) on Breezy"
date: 2005-10-16
forum: Testimonials &amp; Experiences
---

### Post by Buffalo Soldier on 2005-10-16
Just bought a Logitech trackball. The model name is Marble Mouse. Not sure why it's still being called a 'mouse' though. 

I unplugged my old Logitech optical mouse and plugged in the trackball. The only thing that's not working is the two small buttons at the side with an up and down arrow. I guess its supposed to be use for scrolling.

Everything else is working smoothly. I guess I have some xorg.conf editing to do. Ubuntu ROCKS :)

EDIT:

Here's my new entry in xorg.conf:
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"Buttons"		"7"
	Option		"ChordMiddle"
	Option		"EmulateWheel"		"1"
	Option		"EmulateWheelButton"	"5"
EndSection
```

p/s: using the trackball with left hand.

---

### Post by majikstreet on 2005-10-16
Congrats!

---

### Post by timseal on 2006-02-24
Did you ever find out how to get the other two buttons working?

---

### Post by mstlyevil on 2006-02-24
I am also using a Logitech Marble Mouse. If you get the scroll wheel effect working please post it. I would love to get that working myself. :) 

[IMG]http://www.logitech.com/lang/images/0/127.gif[/IMG]

---

### Post by byen on 2006-02-25
I have the same one too... I need to get the scroll wheel and the two small buttons to work. If someone has any info... we are all ears!!! :-)

---

### Post by Buffalo Soldier on 2006-03-11
Currently using Dapper Drake Flight 5. Using **xev** in the command line, I manage to know the numbers for the buttons. (see attached picture):
1 = big right button
3 = big left button
8 = small left button
9 = small right button

So here's the entry for xorg.conf:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"		"9"
	Option		"ZAxisMapping"		"4 5"
	Option		"EmulateWheel"		"1"
	Option		"EmulateWheelButton"	"9"
EndSection
```

I'm using this on the left hand... so I guess for people using it on the right hand it's: 
```

	Option		"EmulateWheelButton"	"[color=red]**8[/color]**"
EndSection
```

Dear moderators.. is this the right section to post this? or should i repost it in the howto section?

---

### Post by mstlyevil on 2006-03-11
There is a procedure for post to be added to the How To section. If you want to post this information as a new how to make sure you give details to help new users. Like how to edit their xorg file by using gedit and give the command to open it. It would probally help to go ahead and write it for right hand users and then add a note for left hand users since the majority of people are right handed.

Just read the message at the top of the Customization Tips and Tricks section for more instructions on how to post the how to. Thanks for the information, I am going to put it to good use today.

---

### Post by majikstreet on 2006-03-13
cool.. are trackballs easy to use? 

OT: Is your name Buffalo Soldier from Bob Marley's song Buffalo Soldier?

---

### Post by mstlyevil on 2006-03-13
[QUOTE=majikstreet]cool.. are trackballs easy to use? 

OT: Is your name Buffalo Soldier from Bob Marley's song Buffalo Soldier?[/QUOTE]

This particular model is.

---

### Post by mstlyevil on 2006-03-13
Buffalo Soldier, This is excellent. The scroll option works great with the wheel. I am forever indebted to you.

---

### Post by Buffalo Soldier on 2006-03-14
[QUOTE=majikstreet]cool.. are trackballs easy to use? 

OT: Is your name Buffalo Soldier from Bob Marley's song Buffalo Soldier?[/QUOTE]I used to use mouse with my right hand. Then a few months back I started to feel pain and ache in my fingers, wrist and elbow. So after doing a few readings on ergonomics, RSI, carpel tunnel syndrome and etc etc... I decided to give the trackball a try.

I started to use the trackball with my left hand because I want to give my right hand a rest... now it seems I'm more comfortable using the trackball :) The only drawback I can feel is when I want to draw or do very small movement... in that case.. the normal mouse is better.

Yes, the nickname is inspired by the song by Bob Marley.

Anyway, after reading mstlyevil advice... I've tried my best to make this guide as easy as possible... did i missed anything? Any suggestions before I post this at the how-to section? Kinda nervous... i dont think i've ever posted any howtos before.

---

### Post by mstlyevil on 2006-03-14
[QUOTE=Buffalo Soldier]I used to use mouse with my right hand. Then a few months back I started to feel pain and ache in my fingers, wrist and elbow. So after doing a few readings on ergonomics, RSI, carpel tunnel syndrome and etc etc... I decided to give the trackball a try.

I started to use the trackball with my left hand because I want to give my right hand a rest... now it seems I'm more comfortable using the trackball :) The only drawback I can feel is when I want to draw or do very small movement... in that case.. the normal mouse is better.

Yes, the nickname is inspired by the song by Bob Marley.

Anyway, after reading mstlyevil advice... I've tried my best to make this guide as easy as possible... did i missed anything? Any suggestions before I post this at the how-to section? Kinda nervous... i dont think i've ever posted any howtos before.[/QUOTE]

I think you did an excellent job. It worked perfectly on my mouse so I have nothing else to add to it.

---

### Post by Buffalo Soldier on 2006-03-14
I forgot one thing. This has not been tested on Breezy. Can anyone using Breezy & Logitech Marble please give some feedback whether this works or not?

---

### Post by mstlyevil on 2006-04-08
bump

---

### Post by mstlyevil on 2006-04-25
bump again

---

### Post by mstlyevil on 2006-05-02
I moved the how to post to the how to section. you can find it here.

[http://www.ubuntuforums.org/showthread.php?t=169423]("http://www.ubuntuforums.org/showthread.php?t=169423")

---

### Post by Drakx on 2006-06-30
[QUOTE=Buffalo Soldier]Currently using Dapper Drake Flight 5. Using **xev** in the command line, I manage to know the numbers for the buttons. (see attached picture):
1 = big right button
3 = big left button
8 = small left button
9 = small right button

So here's the entry for xorg.conf:

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"Buttons"		"9"
	Option		"ZAxisMapping"		"4 5"
	Option		"EmulateWheel"		"1"
	Option		"EmulateWheelButton"	"9"
EndSection
```

I'm using this on the left hand... so I guess for people using it on the right hand it's: 
```

	Option		"EmulateWheelButton"	"[color=red]**8[/color]**"
EndSection
```

Dear moderators.. is this the right section to post this? or should i repost it in the howto section?[/QUOTE]

Hi

I know this is an old post but the info im gonna give may help others with the same mouse :).
I've done some testing with this and Xgl and i got it working! correct for the transparcy Its simple todo all you need todo is edit your xorg.conf and use gconf-editor, so xorg.conf first:

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    #Option         "ZAxisMapping" "4 5"
    #Option         "Emulate3Buttons" "true"
# added below
    Option	  "Buttons"		"9"
    Option	  "ZAxisMapping"	"4 5"
    Option	  "EmulateWheel"	"1"
    Option	  "EmulateWheelButton"	"8 9"
EndSection

```

this section here:
```

Option	  "EmulateWheelButton"	"8 9"

```
Will allow for up and down using your two small buttons

now for compiz configurtion to have it working correctly for the transparncy
open a termial type 
```

gconf-editor

```

Now with that open browse to:

apps >> compiz >> general >> options

and scroll down till you see **opacity_decrese** and **opacity_increase**
change the values to

```

<Alt>Button9
for decrease

```

and 
```

<Alt>Button8
for increase

```

any way thats it hope this helps some one else :)

---

### Post by smittyhead on 2006-09-15
Hi, I been using this mouse for years on windows but i had button 8 as a middle mouse button and 9 as a back button, is there anyway I can make it work like this?

---

### Post by ttoine on 2007-01-23
Hum...

It seems that it doesn't work for Edgy.

I tried several tips of internet but nothing's working.

Can you try to see if there is a way to get it in Edgy ?

Toine

---

### Post by powdercarrot on 2007-02-03
The scroll works with the above edit by holding down the small left button and scrolling with the wheel.  I would like to get the small left button to work for going back in a web browser.  Any ideas?

---

### Post by ttoine on 2007-02-09
Ok, with the tips in the howto section of the forum it works. (I didn't noticed about this one, sorry)

Actually, in Firefox, horizontal scroll with the ball do "back / next", I like it and so I will not tweak Firefox conf.

Thanks a lot, guys.

Toine

---

### Post by Phrawm48 on 2007-02-15
I've tried the quoted mods a couple of different ways but Kubuntu freezes during boot rather than display the "wristwatch" symbol.  In other words, my computer can't read the modified xorg.conf file.

I then use recovery mode to restore my backup xorg.conf file so the computer can boot normally.

Now I'm stuck.  So my question is, are the InputDevice sections given in this thread a *replacement* for the existing mouse section, or a *supplement* to it?  In other words, do I delete the existing mouse section in xorg.conf and use only the modified one, or do I add the modification but leave the existing section in?

Cuz' I'm not making any progress getting my Marble Mouse to work...

Cheers & thanks,
Ric

---

### Post by powdercarrot on 2007-03-10
I would like to set my small left button to browse back, the small right button to browse forward and the combination (large left+large right+wheel) to scroll.

Any ideas on how I can get this working?

---

### Post by dustrho on 2007-04-15
> **powdercarrot said:**
> I would like to set my small left button to browse back, the small right button to browse forward and the combination (large left+large right+wheel) to scroll.

Any ideas on how I can get this working?

I would also like to know how to accomplish this task, as the Marble Mouse is by far the best mouse I've ever used. I have three of these in my possession... one for this laptop I'm currently using, my powerhouse desktop computer and my work computer. Hope there's a solution to this.

---

### Post by Pollywoggy on 2007-08-01
> **dustrho said:**
> I would also like to know how to accomplish this task, as the Marble Mouse is by far the best mouse I've ever used. I have three of these in my possession... one for this laptop I'm currently using, my powerhouse desktop computer and my work computer. Hope there's a solution to this.

I ordered a trackball like this one and should have it in the next couple of days.
I found this which might help get the mouse working:

[http://www.linuxquestions.org/hcl/showproduct.php/product/670](http://www.linuxquestions.org/hcl/showproduct.php/product/670)

The advice there is to use the USB to PS/2 adapter which is included with the mouse and to set it up like this:

Section "InputDevice"
 Identifier "mouse0"
 Driver "mouse"
 Option "Name" "AutoDetected"
 Option "Buttons" "5"
 Option "Protocol" "MouseManPlusPS/2"
 Option "Device" "/dev/psaux"
 Option "Emulate3Buttons"
 Option "Emulate3Timeout" "50"
 EndSection

---

### Post by tropicflite on 2007-09-17
I'm on Tribe5, but this has been working for me since Dapper:

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Emulate3Buttons" "true"
    Option         "Buttons" "9"
    Option         "EmulateWheel" "1"
    Option         "EmulateWheelButton" "8"
    Option         "YAxisMapping" "4 5"
    Option         "ZAxisMapping" "6 7"
EndSection
```

And I also use firefox's [[COLOR="blue"]mouse gestures extension[/COLOR]]("https://addons.mozilla.org/en-US/firefox/addon/39") for forward and back.

---

### Post by Pollywoggy on 2007-09-18
> **tropicflite said:**
> I'm on Tribe5, but this has been working for me since Dapper:

```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Emulate3Buttons" "true"
    Option         "Buttons" "9"
    Option         "EmulateWheel" "1"
    Option         "EmulateWheelButton" "8"
    Option         "YAxisMapping" "4 5"
    Option         "ZAxisMapping" "6 7"
EndSection
```

And I also use firefox's [[COLOR="blue"]mouse gestures extension[/COLOR]]("https://addons.mozilla.org/en-US/firefox/addon/39") for forward and back.

I am trying this out in my xorg.conf
The Marble Mouse is not very good for games, I spin around uncontrollably but in Linux it works great.

---

### Post by Locutuslaser on 2007-11-03
Just configured one too and it's great. For games i will plug another usb mouse in then.

---

### Post by geokker on 2008-10-07
I have a default installation of Hardy 64-bit. I have two mice plugged in - a bog-standard dell optical (PS/2) and a Logitech Marble Mouse (USB). Using xev, I discovered the button numbers and added 2 lines to my xorg.conf:

> Section "InputDevice"
     Identifier  "Configured Mouse"
     Driver      "mouse"
     Option      "CorePointer"
[B]     Option "EmulateWheel" "1"
     Option "EmulateWheelButton" "9"[/B]
EndSection

The left small button (I'm a lefty) now emulates scrolling when depressed and using the ball.

Love the mouse - so comfortable.

---

### Post by Bionic_Beefpile on 2008-11-02
Just FYI, the button configuration stopped working for me after upgrading to Intrepid.  I found the fix here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/261995](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/261995)

You have to add this code to /etc/X11/xorg.conf:
```
Section "ServerFlags"
    Option "AutoAddDevices" "false"
EndSection
```

I did this just before the "ServerLayout" section and restarted X, and the scroll started working again just as in Hardy.

---

### Post by oldschoolgentoo on 2010-11-04
Bump

Anyone using this on lucide 10.04?

---

