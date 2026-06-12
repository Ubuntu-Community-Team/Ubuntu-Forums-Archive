---
title: "Possible to prevent shutdown by holding power button"
date: 2008-03-08
forum: Security Discussions
---

### Post by Sukarn on 2008-03-08
On all computer systems I have worked with so far, there has been a way to force the system to halt without a safe shutdown by pressing and holding the power button for a few seconds.

Now, I know that this is a feature built into the hardware, and its not something that Ubuntu or any other OS can overcome, but is there anything that can be done to prevent a shutdown by this method?

I locked my x-session and left the computer for a few minutes. Upon coming back I found it switched off. A guy who happened to be nearby at that moment told me that someone had just come and held the power button till the computer turned off.

Needless to say, I lost only about a couple of minutes of my unsaved work, but this issue concerns me now. This seems kind of like a security issue to me now.

Is there any method to stop this from happening again?

Also, I would like to know if there's a method to stop the computer from restarting when Ctrl+Alt+Del is pressed in a terminal window when no one is logged in, and from shutting down under the same conditions when the power button is pressed.

---

### Post by tgalati4 on 2008-03-08
Disconnect the power button inside the machine.  Use the powerstrip to turn on and a crontab entry to shutoff at night or direct shutdown command.  

If that sounds drastic, there's a way to assign the power button to do a shutdown command.  Unfortunately, it takes more than 4 seconds to shutdown a system.  7 seconds is the fastest I've seen.  So disks may get sync'ed in that time, but any open applications will probably lose data.

Put a big label on the front--"Processing Important Company Batch Jobs--Do Not Shut Down."

---

### Post by Dr Small on 2008-03-08
> **tgalati4 said:**
> Disconnect the power button inside the machine.  Use the powerstrip to turn on and a crontab entry to shutoff at night or direct shutdown command.  

If that sounds drastic, there's a way to assign the power button to do a shutdown command.  Unfortunately, it takes more than 4 seconds to shutdown a system.  7 seconds is the fastest I've seen.  So disks may get sync'ed in that time, but any open applications will probably lose data.

Put a big label on the front--"Processing Important Company Batch Jobs--Do Not Shut Down."
Umm, how would you use the powerstrip to turn it on?

---

### Post by Sukarn on 2008-03-08
> **Dr Small said:**
> Umm, how would you use the powerstrip to turn it on?

I would like to know that too.

---

### Post by srt4play on 2008-03-08
> **Dr Small said:**
> Umm, how would you use the powerstrip to turn it on?

Jumper the pins together on the motherboard that the power button is connected to and leave the power supply switched on.

---

### Post by Sukarn on 2008-03-08
> **srt4play said:**
> Jumper the pins together on the motherboard that the power button is connected to and leave the power supply switched on.

Cool... That sounds kind of like what I'm looking at doing here.
Thanks

---

### Post by Dr Small on 2008-03-08
> **srt4play said:**
> Jumper the pins together on the motherboard that the power button is connected to and leave the power supply switched on.
Awesome. I'll have to try it sometime :)

---

### Post by Dr Small on 2008-03-08
I just tried this on my old Compaq, and it really didn't work. But I think it is more of a BIOS issue rather than wireing issue.

I found an old jumper on an old motherboard, stuck it on the Power SW jumper, plugged in the system, and it powered on for about 1.5 seconds, and powered back off.

I tried this with the power switch too, held in the power button, and it did exactly the same thing. So I think that the BIOS is reading the connection to power it on, and then reading the rest of the constant connection as a signal to shutdown, and that is exactly what it is doing.

This may not be so with other systems, but it was for the one that I tested this on. So, next time I shutdown my desktop or server, I'll test it out on them to see if it will work, and report back.

Dr Small

---

### Post by Sukarn on 2008-03-09
A similar thing happened with me. The system powers on for a bit and then switches off.

---

### Post by Dr Small on 2008-03-09
Try looking around in your BIOS setup for any options on what the power does. I looked around and didn't find any on mine, but it seems to me I have seen that option before on one of the many BIOSes I have been in.

---

### Post by Sukarn on 2008-03-09
Power button can be changed between "On/Off" and "Suspend", although changing it to suspend makes no difference in how the button functions and what it does.

There are other options in there for various ways to turn on the computer like "Wake up by LAN", "Wake up by KBC" "Wake up by PS/2 mouse", "Wake up by Ring" and "Wake up by Alarm". I've tried the options for mouse and keyboard, and they do not work. The wake up by alarm works, but is irrelevant to what I'm trying to do here.

The only other option in there is about what to do in case of a Power failure when the power comes back on. The options are "Last State", "Off" and "On". I know what this does, but again, this option is irrelevant here.

---

### Post by Dr Small on 2008-03-09
Hmm... Well that's a real bummer, because it sounded like a good idea :|

---

### Post by tgalati4 on 2008-03-10
You may have to hot-wire the power supply.  Run a small jumper from the back of the ATX power connector from the green wire to any black wire.  That will provide power to the power supply so that the computer can boot completely from a power strip.  This is needed on newer power supplies that don't have an on/off button on the back near the EIC power cord.

---

