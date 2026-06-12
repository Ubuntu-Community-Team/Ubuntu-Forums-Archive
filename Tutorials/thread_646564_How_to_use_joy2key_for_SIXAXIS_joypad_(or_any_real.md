---
title: "How to use joy2key for SIXAXIS joypad (or any really!)"
date: 2007-12-21
forum: Tutorials
---

### Post by naivri on 2007-12-21
HI there

I´ve recently entered the ubuntu world with my PS3.  This is a post I stuck on the PSubuntu forums, but thought I would mirror it here are people are having problems figuring out how to use joy2key

If like me, you hate the way some emulators allow/don´t allow joystick control then this is the post for you !

This is especially relevant if you use a sixaxis joypad.  With the sixaxis, the d-pad is recognised as buttons and button0 = the select key !  This is no good for programs that will look at the first 2 axis in you dev/input/js0 and use them for up/down/left/right.  Besides, with the amiga, the platformers tended to have up as jump, no good with the sixaxis stick.

eg VICE - c64 emulator, is quite good, left stick for movement, any button (0 through to 19) it will accept as the fire button.  UAE however, will only accept button0 as fire, so you have to use left stick and select button as fire button.   Unacceptable !

```
sudo apt-get install joy2key
```

then
```
joy2key -dev /dev/input/js0 -terminal
```
It will prompt you
```

Calibrating axis 0
Please center the axis and press a button.
?

```
So just push any button on the pad without touching the stick.  It will change to 
```
Locked at 0
Please move the axis to its lowest position and press a button.
?
```
Hold the left stick to the left, it will change to 
```
value: -32767
```
now hit any button.  It will then change to 
```
Please move the axis to its highest position and press a button.
value: 0
```
do what it says....it will change to 
```
value: 32767
```

It will then tell you
```
Using deadzone of 50%
Calibrations set at:
Axis 0 low threshold set at -16383
Axis 0 high threshold set at 16383
(you can put these in your .joy2keyrc to avoid calibrating in the future)

```

So repeat for axis 1 (up/down on left stick) if you please, but it will tell you the same thing as me so you can do it or just hammer the X button until you reach axis 26 and it give you the ctrl-c to exit prompt.  

We are going to keep this info in a config file so u dont have to do it every time.

```
nano ~/.joy2keyrc
```
will open a blank file, paste the following in
```

COMMON
-X
-dev /dev/input/js0
-thresh -16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383
-16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383
16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383
-16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383
16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383
-16383 16383

```
ctrl-X to exit, then Y for yes to save.

Thats the basic config file sorted !  Now for the fun bit.  Getting joy2key to map a keystroke to the joypad movements.

there are 2 options 
-buttons
-axis

now say for instance i had
```
-buttons a b c d e f g h i
```
This would tell joy2key that when i push button0 - send a signal saying **a** has just been pressed.  When i push button1 - send a signal saying **b** has just been pressed etc
also
```
-axis a d w s
```
would tell it that if axis0 minimum (ie left) is pushed, send the **a** keystroke and if axis0 maximum (ie right) is pushed, send the **d** keystroke.  If axis 1 minimum (ie up) is pushed then send the **w** keystroke etc etc

for keys like left control right shift etc, you need the key mappings that X11 uses.  there is an app that will tell you that !  ie for UAE, i want the fire button to be right control so i need to know what right control is as a keymap in Xwindows

```
xev
```
will open the even viewer and will display a lot of junk
```
PropertyNotify event, serial 18, synthetic NO, window 0x3400001,
    atom 0x107 (XKLAVIER_STATE), time 4250290198, state PropertyNewValue

PropertyNotify event, serial 26, synthetic NO, window 0x3400001,
    atom 0x12b (_NET_WM_ICON_GEOMETRY), time 4250290327, state PropertyNewValue

FocusOut event, serial 27, synthetic NO, window 0x3400001,
    mode NotifyNormal, detail NotifyNonlinear

```
just press the key u want to know the keymap for ie right control and it shows 
```

KeyRelease event, serial 30, synthetic NO, window 0x3400001,
    root 0x3f, subw 0x0, time 4250341503, (805,386), root:(810,435),
    state 0x4, keycode 109 (keysym 0xffe4, Control_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
and there is our keymap in the middle **Control_R**.  Use this to find out what any key maps to for use in the config file.

Now, I want to map up/down/left/right on the keyboard to d-pad up/down/left/right.  I also want to map right control to the X button.  Using the event viewer as described above I find that they are conveniently called  Up Down Left Right and Control_R

Last piece in the puzzle is knowing what the buttons all are.  If you have jscalibrator, it will show you what the buttons are by trial and error pressing and seeing what button depresses in the window.

Or you could just look at the list below! (for the SIXAXIS pad)
button0         Select
button1 	L3
button2 	R3
button3 	Start
button4 	Dpad Up
button5 	Dpad Right
button6 	Dpad Down
button7 	Dpad Left
button8 	L2
button9 	R2
button10 	L1
button11 	R1
button12 	Triangle
button13 	Circle
button14 	Cross
button15 	Square
button16 	PS Button

pain in the neck thing is, you cant tell joy2key to map buttons 4, 5, 6, 7 and 14.  Since it runs from the command line it needs something for all the buttons up to the last one you are using.

so our code is 
```

-buttons r r r r Up Right Down Left r r r r r r Control_R

```
as you can see, i just mapped **r** to every button from 0 upwards apart from the one i wanted,  starting from button0 !

so from that button 4 is **Up** on the keyboard (from the arrow keys), button5 is Right, button6 is down & button 7 is left - all from the arrow keys.  Lastly button 14 is right control.

So we have now mapped up/down/left/right on the D-pad to the arrow keys and the X button to right control!

as a last measure, we will map the left stick to up down left right as well
```
-axis Left Right Up Down
```
remember the order is -axis axis0min axis0max axis1min axis1max

So lets throw all that in the config file (~/.joy2keyrc).  We will put it in a section called uae (as the config lets you have lots of configs for different apps)

```

COMMON
-X
-dev /dev/input/js0
-thresh -16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383
-16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383
16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383
-16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383
16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383
-16383 16383

START uae
-X
-buttons r r r r Up Right Down Left r r r r r r Control_R
-axis Left Right Up Down

```

you get the format dont you?

i could equally put in more configs for different apps by just starting them ```
START appname
```

save you .joy2keyrc file and you are ready to start

open 2 terminal windows
in one start your app (eg VICE or UAE).  So we now have our emu running.

in the 2nd window type
```
joy2keyrc -config uae
```
and it will say
```

naivri@localhost:~$ joy2key -config uae
joy2key - reads joystick status and dispatches keyboard events
By Peter Amstutz (tetron@interreality.org)
This is free software under the GNU General Public License (GPL v2)
              (see COPYING in the joy2key archive)
You are welcome to use/modify this code, and please e-mail me
if anything cool comes of it!
Version: 1.6.1   Binary built on Jan 26 2007 at 17:31:47

Please select a window to send events to

```
your mouse pointer will change to a cross and just click the window that has your emulator running.  It will then change to 
```
Initialization complete, entering main loop, ^C to exit...
```

Play away till your heart is content !

Its quite clever, when you close the window of the app/emu you are playing, joy2key will detect it and kill its self!

Any questions, let me know

---

### Post by Nazty_Nayt on 2008-07-04
Ok, I'm just lost.  I've been trying for a week now to get my PS3 controller (wired) to work with my computer/epsxe emulator, but to know luck at all.  I've tried following this guide but this is way over my head.

I got here 
```
COMMON
-X
-dev /dev/input/js0
-thresh -16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383
-16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383
16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383
-16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383
16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383
-16383 16383
```

And went to do the a b c d e f , etc.. buttons thing, and when I did that it says command not found.  When I do XEV, this little white box pops up with a white box inside that, and it doesn't do anything, I can wave my mouse over it, and a bunch of stuff gets entered into the terminal.  

It says push the key you want the map of Ie Right control, so I push the > arrow key, I'm guessing that's what we're going for here, and it gives me the key release log, but I have no idea what I'm supposed to do with it, do I copy it or something?  So anyways I guess I'm done so I move on, and do the following code
```
-buttons r r r r Up Right Down Left r r r r r r Control_R
```

In which case like earlier I get the same thing

```
bash: -buttons: command not found
```

I just don't see what I'm missing here, I've read this thing over, and over again, I am thankful though that someone has something on this, cause I've been trying to get this working for weeks now :x  Please help me out here, thanks.

---

### Post by crazyfuturamanoob on 2008-11-02
I installed joy2key with synaptic, and I have tested it.
But it doesn't work.
> arho@ohra-laptop:~$ joy2keyrc -config test
bash: joy2keyrc: command not found
arho@ohra-laptop:~$ 

What to do?

Edit: The command is joy2key, not joy2keyrc, edit your post. You probably misspelled it.

---

### Post by lernatix on 2009-02-08
I really want to use on my Yellow Dog PS3 install,
no I don't expect you to figure that out for me. ;)

However, the idea of having the right control key 
for a fire button irritates me almost as much as 
having a select button for one.

So,  my question.  Can a button be re-mapped to 
another button?   

```
ie: -buttons r r r r Up Right Down Left r r r r r r button 1
```

joy2joy anyone?

---

### Post by kidYojimbo on 2009-07-11
hey i've been looking into this as i've wanted to get epsxe going again after leaving windows behind . solution for ubuntu 8.10 and the version of joy2key 1.6.1 some of the commands may have changed , so after i set my sixaxis to just have letters as buttons , the command to run it was 

joy2key -rcfile .joy2keyrc 

-N

---

### Post by Sonic132 on 2010-11-04
Sorry for digging through the graveyard. But I'm having some severe issues with calibrating joy2key. I get it set up as a mouse. One stick set to move the pointer and one set to scroll wheel. But I can't seem to set the buttons to do anything.
Anyone have a successful configuration file? If so I could probably just copy and paste it into mine.
If not, anyone know of a working guide?
I really, really appreciate it!

Thanks for taking time to read this.

---

### Post by starscalling on 2010-12-02
> **Sonic132 said:**
> Sorry for digging through the graveyard. But I'm having some severe issues with calibrating joy2key. I get it set up as a mouse. One stick set to move the pointer and one set to scroll wheel. But I can't seem to set the buttons to do anything.
Anyone have a successful configuration file? If so I could probably just copy and paste it into mine.
If not, anyone know of a working guide?
I really, really appreciate it!

Thanks for taking time to read this.

post that config man

---

### Post by briggsosaurus on 2011-03-25
So my ps3 controller use to work directly plugged in, with no problems (on games that supported joysticks) since I've tried to install joy2key and follow these directions, not only did the joy2key fail to recongize my controller, its made it so my controller won't work at all on my computer, but it still works on my ps3. Any clues to why joy2key would whipe out my joypad drivers (I belive)

---

### Post by magnetic651 on 2011-03-31
I have a problem with this part:

"Last piece in the puzzle is knowing what the buttons all are.  If you  have jscalibrator, it will show you what the buttons are by trial and  error pressing and seeing what button depresses in the window.

Or you could just look at the list below! (for the SIXAXIS pad)
button0         Select
button1     L3
button2     R3
button3     Start
button4     Dpad Up
button5     Dpad Right
button6     Dpad Down
button7     Dpad Left
button8     L2
button9     R2
button10     L1
button11     R1
button12     Triangle
button13     Circle
button14     Cross
button15     Square
button16     PS Button"

How do I figure out the order of my buttons (I have a Logitech F310)??  jscalibrator does not work

---

### Post by magnetic651 on 2011-03-31
Okay, I got it working, though I still don't know the layout of my buttons!

I have a second controller, what would it show up as in /dev/input ??  It isn't js1

---

### Post by magnetic651 on 2011-03-31
My second joystick must be mouse0, as plugging and unplugging the second mouse makes mouse0 appear and disappear in dev/input

However when I try:

joy2key -dev /dev/input/mouse0 -terminal

I get:

joy2key - reads joystick status and dispatches keyboard events
By Peter Amstutz (tetron@interreality.org)
This is free software under the GNU General Public License (GPL v2)
              (see COPYING in the joy2key archive)
You are welcome to use/modify this code, and please e-mail me
if anything cool comes of it!
Version: 1.6.3   Binary built on Dec 22 2009 at 13:45:44

Error opening /dev/input/mouse0!
Are you sure you have joystick support in your kernel?
ryan@ryan-CM5570:~$ 

Any ideas on what to do here??

---

### Post by magnetic651 on 2011-03-31
I got it all working, one of the emulators gave me the button layout.

---

### Post by minj on 2011-04-14
Thanks for this. I got my generic acme gamepad working on lucid with wine. It shows up in lsusb as

```
Bus 005 Device 004: ID 0079:0011 DragonRise Inc.
```
Here is my .joy2keyrc:
```
COMMON
-X
-dev /dev/input/js0
-thresh 0 0 0 0 0 0 -16383 16383 -16383 16383 0 0

START tomb
-X
-buttons Control_L q e space h v Shift_L g Escape Tab
-axis 0 0 1 1 2 2 a d w s 5 5
```
As you can see this device has 10 buttons and 6 axis (4 of which are rubbish?). 
Once wine is started you attach joy2key with
```
joy2key -config tomb "Tomb Raider: Underworld"
```
The last one is the window name. For full-screen you may see it with alt+tab or something.

---

### Post by chive on 2013-02-05
Hey everybody
I have this all set up in ubuntu, I have two terminal windows open. One running mupen64plus and the other is running joy2key. the one running joy2key is telling me it's sending the correct keys. 
iscap is now 0  sendkey: button_upper: 0 keycode  0x000036  54   sendkey: keysym c
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000034  52   sendkey: keysym z
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000034  52   sendkey: keysym z
state hex 10

i wanted to push c and z on the keyboard, and it recognized that. 
The problem is that it won't communicate with mupen64plus. 
I used the same controller on project64 for windows for the same game. (zelda)
I have tried clicking on the emulator window, the terminal window it's running from, and don't know what else I could try. 
Thanks for all the help!

Also, I should point out that I can type on my computer with my controller now. I can type c,x,z, and move back and forth through text with the joystick. It is working, just won't send the info to mupen64plus.

---

