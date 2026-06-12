---
title: "SHMConfig defies all attempts to enable on Gazelle"
date: 2008-03-06
forum: System76 Support
---

### Post by darkknight045 on 2008-03-06
I cannot for the life of me get the SHMConfig to be recognized on my laptop.  I have not had this problem with Gutsy previously.

I get the message that SHMConfig is disabled, no matter what I set it to:

I have tried:

Option    "SHMConfig"    "on"
Option    "SHMConfig"    "True"
Option    "SHMConfig"    "1"
Option    "SHMConfig"    
I always restart X, ctrl-alt-backspace, that not working I reboot.  Nothing works.

Can someone please help me?

---

### Post by thomasaaron on 2008-03-07
What Gazelle model do you have?

Is this a new Gazelle (GazV5)?
If it is, SHMConfig will not work with it. The machine has an Elantech touchpad, which is not supported by gsynaptics.

If it is NOT a GazV5, do you have this line in the Server Layout section...
Inputdevice     "Synaptics Touchpad"

Also, what are you running? Hardy? (If so, I've heard that xorg is changing a bit in it, and you may have uncovered a bug.

---

### Post by darkknight045 on 2008-03-07
This is entirely possible, this laptop arrived about week ago.

Is there a way for me to disable the touchpad while I'm typing?

---

### Post by thomasaaron on 2008-03-07
Yes, then it is the GazV5.

sudo modprobe -r psmouse #Disable touchpad
sudo modprobe psmouse #Re-enable it.

You could put these in two desktop launchers using these commands:
gksu modprobe psmouse #Turn it on
gsks "modprobe -r psmouse" #Turn it off -- notice the quotes

---

### Post by darkknight045 on 2008-03-07
Thanks!

This isn't as convenient as the command that will auto turn off while typing, but its a good workaround.

Thank you very much for the timely replies!

---

