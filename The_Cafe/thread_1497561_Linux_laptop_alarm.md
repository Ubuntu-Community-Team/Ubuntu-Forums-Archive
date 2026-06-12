---
title: "Linux laptop alarm?"
date: 2010-05-30
forum: The Cafe
---

### Post by Vostrocity on 2010-05-30
I just saw [this]("http://www.syfer.nl/") really cool non-free app for Windows that > ..emits a loud alarm when:

The power cable is unplugged
The mouse is removed
The laptop is shut down
Unfornately, it's a Windows app so I'm wondering if anyone has coded something similar for Linux. It seems like a remarkably simple concept, and I'm not a programmer but it doesn't seem like it would be all that difficult to create. Thanks in advance.

---

### Post by Xbehave on 2010-05-30
You need a script that does something like
```
While screen locked: #something like $(pgrep screensaver) should work for the condition
    set volumes to 100% #amixer is probably the tool you want
    play sound file #aplay will work for wav, mplayer/vlc for others

```

In kde you can run a script when the power cable is unplugged or the computer is shutdown, if you find out how to do this in gnome then trigger the script it should work.

I have no idea how you would trigger the script for mouse insertion/removal but i guess you'd be reading about hal and/or dbus

---

### Post by mikewhatever on 2010-05-30
Looks like an extremely annoying program. Why would one want so many alarms?

---

### Post by andamaru on 2010-05-30
> **mikewhatever said:**
> Looks like an extremely annoying program. Why would one want so many alarms?

to **annoy** the people around them, and I assume it's so he can track people trying to steal his laptop

---

### Post by Vostrocity on 2010-05-30
> **mikewhatever said:**
> Looks like an extremely annoying program. Why would one want so many alarms?

If you're in a coffee shop or library, and someone wants to snatch your laptop, they'll have do at least one of the three: Unplug the power, unplug the mouse, or try to turn it off. It just makes it more failproof.

---

### Post by marshmallow1304 on 2010-05-31
As with car alarms, a shrieking sound will no doubt cause all passerby to rush to apprehend the thief.  /sarcasm

Waste of $10.  It seems that the only people foolish enough to buy the software are the same people who would consider leaving a $1000+ piece of equipment in an airport while they go to the bathroom.

Oh well.  I guess it was good for a chuckle:
> Laptop alarm is just great when I’m sitting at Starbucks or an airport and you got to go to the bathroom. I really can’t live without it. - Marc

---

### Post by boterbram on 2011-04-07
[LIST=1]
[*]Install mpg123
[*]Backup /etc/acpi/power.sh
[*]Add this line to power.sh: /usr/bin/mpg123 /path/to/soundfile
[*]Save and try out, should work instantly
[/LIST]

---

### Post by youbuntu on 2011-04-07
Wonderful. And what are you going to do when the thief HOLDS DOWN the power button? No software in the world is going to protect you if it cannot run! :roll:

They could pull the battery, if the machine was running from it. Double fail.

---

### Post by undecim on 2011-04-07
> **glossywhite said:**
> Wonderful. And what are you going to do when the thief HOLDS DOWN the power button? No software in the world is going to protect you if it cannot run! :roll:

They could pull the battery, if the machine was running from it. Double fail.

But by then, the alarm has already gone off and everyone around him has heard it. Almost any thief would get scared and leave it at that point.

Why is there so much negativity in this thread? It's a great idea. It won't stop the CIA from taking your laptop, nor anyone who knows that it's active and is smart enough to hold the power button (though you could also make it alarm during those 4 seconds that the power button is being held), but it will deter your average thief. Very few will have the presence of mind to quickly find and hold the power button or figure out how to remove the battery. (If the laptop has an accelerometer this can be stopped, too.) 

It shouldn't be difficult to program. A small bash script would do it. Main thing I see is that you need to keep the computer from going to sleep while it's active. Other than that, it's just a matter of engaging the alarm with a keystroke.

I'd like to see one that can work on battery power, too. A simple USB device (i.e. one that does nothing more than say to the computer "I'm here!") with a loop at the end of a cable could be used to attach your computer to a piece of furniture such that it can only be removed by removing the USB plug. Though at that point, you might as well just buy a lock cable.

---

### Post by youbuntu on 2011-04-07
> **undecim said:**
> But by then, the alarm has already gone off and everyone around him has heard it. Almost any thief would get scared and leave it at that point.

Why is there so much negativity in this thread? It's a great idea. It won't stop the CIA from taking your laptop, nor anyone who knows that it's active and is smart enough to hold the power button (though you could also make it alarm during those 4 seconds that the power button is being held), but it will deter your average thief. Very few will have the presence of mind to quickly find and hold the power button or figure out how to remove the battery. (If the laptop has an accelerometer this can be stopped, too.) 

It shouldn't be difficult to program. A small bash script would do it. Main thing I see is that you need to keep the computer from going to sleep while it's active. Other than that, it's just a matter of engaging the alarm with a keystroke.

I'd like to see one that can work on battery power, too. A simple USB device (i.e. one that does nothing more than say to the computer "I'm here!") with a loop at the end of a cable could be used to attach your computer to a piece of furniture such that it can only be removed by removing the USB plug. Though at that point, you might as well just buy a lock cable.

It is not "negativity", it is called being *realistic*. If the OP wants me to stroke their ego (ergo, that of the developer, too) I refuse, as I am telling you that this has quite a few flaws - they're obvious, if you're not willing to be blinded by the "brilliance" of the software

This is the biggest problem with inventors - I see it on the Dragon's Den ALL THE TIME. The inventor is so incredibly blinded by his/her pet idea, they stubbornly refuse to admit that it has the flaws that are duly pointed out by neutral parties. The IDEA is good enough, but I can see a few ways to bypass it. How about turning down the system volume? That'd kill it.

With SO many *hardware* solutions for anti-theft, I think you are walking uphill through cold treacle, trying to convince people this is viable. In this society where noone cares about anyone else in their direct vicinity, even if the alarm goes off, who do you think is going to risk jumping in to stop the thief and save the day? :roll:

If you've paid $1,000 for something, LOOK AFTER IT. If my mobile phone is not in my pocket, *with my hand around it, and the screen side facing my leg (to prevent it smashing)*, it is in my hand _outside_ my pocket, being used. Noone ain't stealing it from me, without a fight.

---

### Post by Elfy on 2011-04-07
closing necro'd thread

---

