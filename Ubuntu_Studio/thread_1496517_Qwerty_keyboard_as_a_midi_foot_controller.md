---
title: "Qwerty keyboard as a midi foot controller"
date: 2010-05-29
forum: Ubuntu Studio
---

### Post by decomp on 2010-05-29
I would like to plug a usb qwerty keyboard into my laptop, fire up a virtual midi controller (like virtual midi keyboard) with certain keys mapped to it and press keys with my feet to do things like start and stop effects in rakarrack or start and stop super looper. :guitar:

I know that I can map qwerty keys to notes in virtual midi keyboard, but it doesn't seem to have a lot of virtual 'buttons' for me to press. can regular 'notes' be mapped like switches in midi? 

Basically I saw what this guy did and it looks great, but obviously the software in ubuntu studio doesn't allow qwert key mapping.

[http://createdigitalmusic.com/2007/08/02/get-loopy-with-the-diy-10-ableton-footcontroller-no-soldering-required/](http://createdigitalmusic.com/2007/08/02/get-loopy-with-the-diy-10-ableton-footcontroller-no-soldering-required/)

---

### Post by transmogrifox on 2010-05-29
rakarrack has keyboard shortcuts.  You can learn them by reading help.

In short, on/off fx is 1 through 10 corresponding to each position.  I can't remember whether we added keyboard shortcuts for Looper record/stop/play...but there's an idea.

There must be a Linux program that can convert the keys also to MIDI control messages... but I don't know off hand :(

In Rakarrack, we are currently developing an "ACI", which stands for Analog Control Interface.  You can send control voltages or signals into your sound card to control things.  Right now is more of a peak/envelope detector so you could use a real analog expression pedal or wahwah to control Rakarrack parameters.

Once we implement more level control & expand its function, then you could have an array of switches that sends a different signal level for each switch into Rakarrack through the sound card, and then you could do more flexible control with it.

---

### Post by trulan on 2010-05-29
VMPK is the most customizable of the MIDI keyboards I'm familiar with.  I think it would meet your needs better than Virtual Midi Keyboard.
[http://vmpk.sourceforge.net/](http://vmpk.sourceforge.net/)

---

### Post by decomp on 2010-05-29
transmogrifox - thanks for your/everyones work on rakarrack - it's great! I saw the keyboard shortcuts on the help page. Very handy. I intend to cannibalize a qwerty keyboard & put it at my feet though, so I need to be able to customize the shortcuts.

trulan - thanks for the tip on vmpk. I installed it and it's definitely got more options, like 'extra controllers' - including on/off switches, which is exactly what I was looking for.

The spot where I'm stuck is this: if I activate midi learn in rakarrack, it will recognize me hitting an on/off button or an expression knob in vmpk (or vmk for that matter) and I can assign it to a value (like distortion drive.) This is great, except that on vmpk I can't find how to map those 'extra controllers' or expression kobs to physical keys on the keyboard. I read the faq & looked through all the options.. am I missing something?

Also, if I activate midi learn in rakarrack, it :won't: recognize me pressing just a 'regular' midi keyboard note - only switches or knobs. If I could get it to recognize regular keys, the other questions (of keymapping knobs in vmpk) would be moot (& vice versa.)

p.s. I just tried midi mapping on super looper & hydrogen, and both would accept input from anything, be it button or knob or piano key. 
 
anyway questions remains: in vmpk, how to map extra knobs or - in rakarrack, how to get it to recognize regular piano keys. any ideas?

---

### Post by decomp on 2010-06-17
Shameless Bump. 

I'm still trying to figure this out. just dl'ed the updates version of rakarrack from falktx ppa.. \m/

but I still can't map my qwerty keys to vmpk 'extra controller' buttons in order to controll rakarrack. and rakarrack still doesn't recognize 'normal' midi keypresses from vmpk or vmk.

any ideas?

---

### Post by EliasKesh on 2010-06-23
I am looking for the exact same thing. I have a USB presentation remote I attach to my guitar and would like it to control patch changes in Rakarrack and Fluidsynth. Both accept midi input for patch changes so if I could map Page Up, Page Down to a midi program change up or down I would have it. 

Still looking....

---

### Post by AutoStatic on 2010-06-23
Gee, I did find this one:

[xphat]("http://www.equalarea.com/paul/xphat/")

And guess who's the author? Paul Davis!
Guess this one doesn't compile anymore since it depends on an obsolete library (XForms) :p
And it's from like 1998 or something ;)

---

### Post by AutoStatic on 2010-06-25
Found this one too: [http://lsmi-all.sourceforge.net/](http://lsmi-all.sourceforge.net/)

From the same author as the Non apps (Non-sequencer, Non-daw, Non-mixer). I've uploaded it to my PPA. The package contains 4 little apps of which one, lsmi-keyhack, turns your qwerty keyboard into a MIDI event generator.

[http://ppa.launchpad.net/autostatic/ppa/ubuntu/pool/main/l/lsmi/](http://ppa.launchpad.net/autostatic/ppa/ubuntu/pool/main/l/lsmi/)

Please let me know if this stuff is useful, I intend to use it myself for a DIY MIDI foot controller.

---

### Post by decomp on 2010-06-28
autostatic: I just downloaded the utility you mentioned, but I can't seem to find any documentation on how to use it, and when i run it i get this:

$ lsmi-keyhack
lsmi-keyhack v0.6
Registering MIDI port...
Initializing keyboard...
Error opening event interface! (Permission denied)


The route I've been tinkering with is:

install qmidiroute

open jack control
open vmpk or vmk
open rakarrack: go to settings -> preferences -> midi -> midi implementation -> select default
open qmidiroute: go back to vmpk/vmk. press a key. go back to qmidiroute. look in the log and see what key you pressed. create a new map. set the note you pressed in vmpk/vmk, and tell qmidiroute to output a controller change at chanel 1, controller 116, and then value 1-20 toggle first 10 effects. (value of 2-3 toggles 2nd effect for example. )

Works great! Only catch: the note-off data that vmpk/vmk sends when you release the button just turns the effect right back on/off again, so you have to leave your foot on the button. Doh! anyone else figure this out?

VMPK has 'extra controllers' which rakarrack will recognize but I can't seem to map to the keyboard. I emailed the vmpk creator but he gave a kde specific solution involving d-bus which I didn't understand/know how to use independent of kde :/

So close!

---

### Post by AutoStatic on 2010-06-28
decomp, you have to run it as root (so with sudo) and with the -d switch you can select the input device. You can find your input devices in */dev/input* and with **cat /proc/bus/input/devices** you can check out which device holds which event ID.

---

### Post by decomp on 2010-06-28
thanks autostatic! So: lsmi-keyhack works great - the awesome thing about it is that it recognizes a specific keyboard (the input event you specify) and always grabs it's input regardless of window focus - so it's perfect for footpedal use! the downside is that you can't configure what type of midi note it sends and of what value - so it provides pretty much the same functionality of vmpk/vmk. Unless I'm missing something?

Also autostatic, do you know how to reset the keymap for lsmi-keyhack? I set up a dumb keymap the first time :D i tried dpkg-reconfigure but that didn't work. I can't find where it's storing config files.

So at least in the case of rakarrack (because rakarrack doesn't recognize regular midi 'note' events, only controller events) the problem still remains converting the 'note' events sent by lsmi-keyhack/vmpk/vmk to controller events (with the specific value of controller 116 and  value 1-20 )

Anyone know of an alternative to qmidiroute, or know how to stop qmidiroute from responding to the note-off events?

---

### Post by AutoStatic on 2010-06-28
> **decomp said:**
> Also autostatic, do you know how to reset the keymap for lsmi-keyhack? I set up a dumb keymap the first time :D i tried dpkg-reconfigure but that didn't work. I can't find where it's storing config files.I think it's the ~/.keydb file

> Anyone know of an alternative to qmidiroute, or know how to stop qmidiroute from responding to the note-off events?Maybe the mididings Python script is worth a try: [http://das.nasophon.de/mididings/](http://das.nasophon.de/mididings/)

It's also in falkTX's PPA: [http://ppa.launchpad.net/falk-t-j/lucid/ubuntu/pool/main/m/mididings/](http://ppa.launchpad.net/falk-t-j/lucid/ubuntu/pool/main/m/mididings/)

---

### Post by decomp on 2010-08-01
Thanks autostatic! mididings is just the trick. It took me awhile to get around to it but I finally read the documentation. A simple command line instance started with the command:

mididings "Filter(NOTEON)"

removes everything but noteon events perfectly. This can then be passed to qmidiroute (which has convenient gtk interface + save files), or qmidiroute can be skipped and more complex script can be written. I'm too lazy to write a script but I am using mididings command line instance to start and stop multiple effects with a single button in the new git version of rakarrack.

A command line instance that uses one keypress (of key 60) to start and stop rakarrack effects number 3,4 and 9 simultaneously is:

mididings "Filter(NOTEON) >> KeyFilter(60) >> [ Ctrl(116, 6), Ctrl(116, 4), Ctrl(116,16)]" 

I hope to make a demo and upload it somewhere but it might be awhile.

Thanks for your help!

---

### Post by decomp on 2010-08-01
Almost forgot - 

something wierd with lsmi, although it's workable - if I close it I have to restart the computer to use it again or I get an error stating something like "process or resource in use." Also lsmi doesn't seem to save the key database so I have to redefine keys every time.. but it's not so bad.

---

### Post by AutoStatic on 2010-08-01
And what if you stop lsmi, unplug your mouse and plug it in again? You could save the key database yourself and create a little wrapper script that copies the key database in place before starting lsmi.

---

### Post by decomp on 2010-08-01
doh just had to look at sudo processes in system manager.. it was just still running :P

---

### Post by yammy370 on 2011-07-16
I am trying to do something similar as stated above, using an old keyboard with only 15 or so keys as a foot controller (ie. effects on/off) for rakarrack. The above method seems to be working but I have come across some problems.

First of all, the ALSA connection in qjackctrl is VMPK > (mididings) > qmidiroute > rakarrack. The mididings solution works great, but i took it out for simplicity in problem solving...

So when I make a new connection in qmidiroute i can see the incoming midi note and set that as the input. I then set the controller output as being channel 1, controller 116, value 0, for example, taken from the midi implementation list of rakarrack. This then makes the desired change in rakarrack. Good. But when I repeat this for the 10 FX on/off, plus a master on/off, plus a next/previous, the signals seem to become confused, and I end up with two or three keys operating the same FX pedal and a couple being redundant. Also, if I save the qmidiroute settings, it often changes the controller from fixed (which seems to work) to offset (which doesn't), or even worse, after loading the file it has no effect on rakarrack whatsoever despite the settings looking correct.

Any ideas what the problem might be? Is it likely to be a problem in qmidiroute or in rakarrack?

As a second approach, I decided to try to use the keyboard shortcuts inside of rakarrack. The problem here, of course, is that the keys are very close together so not ideal for foot controller use. So I created a new keyboard layout "fx" (in /usr/share/X11/xkb/symbols which can be activated from the keyboards menu and from a shortcut in the icon bar) and removed redundant keys with the remaining being equally spaced. The problem I have here is that some of the keys retain their old value inside rakarrack. For example I have the "N" key now operating as "8" and using the keyboard in firefox, for example, it types an 8. But inside rakarrack it functions as an "N" and creates a new preset. Now I can try to work around this and use only keys that don't have shortcuts assigned to them, but this really works against the ideal layout and key spacing. There are some areas of the keyboard with 3 or 4 consecutive shortcut keys where this is really not practical. Any ideas on key mapping, or how the shortcuts operate inside of rakarrack?

---

### Post by youWho on 2012-01-27
It looks like this thread is a little old but if anybody is still looking for this sort of thing it seems to me that you could implement quite a variety of such MIDI transformations in Pd (PureData). I remember that Max used to have (I'm sure it still does, just that I haven't used it in a while) objects that output values when keys (I mean qwerty keys here) were pressed and I think Pd has some object(s) for that too. In any case you should definitely be able to transform MIDI events by inputting them, which essentially means receiviing them in your patch as numbers via some MIDI input oject of which there are a few, then doing something with the numbers, then packing them back into lists if necessary (for example if you're transforming note and velocity pairs) and outputting them with one of the MIDI out objects.

I'm about to try this in fact, which is why I happened upon this thread; I'll report back...

I'm editing this because I see now that I might have misunderstood you---that you (all???) are looking for drivers or other lower level ways to convert non-MIDI events into MIDI. I doubt Pd would be so useful for that unless there happens to be an object that receives input from something you want to use. I do believe that you can at least translate qwerty keys, though as far as I know that would essentially mean the keys on the main keyboard you use.

Cheers

---

