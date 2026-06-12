---
title: "Stuck in stand-by"
date: 2009-09-09
forum: System76 Support
---

### Post by miniyak on 2009-09-09
This has happened one or twice before this week but more often recently i have got stuck in stand-by. What happens is i close the lid (set to stand-by) then walk away or pack it up into my laptop bag. Then when i come back to it and open the lid i realize that the panp5 is still on. black screen with back-light and a flashing hyphen/underscore? in the top left hand corner, sometimes no hyphen. This has happened 3 times in the past week

in order to solve this i have to hold down the power button and do a cold boot. 

programs open- 
firefox (all the time)
Open Office (more recently) - 2 or 3 windows
Miro 

other particulars
if my battery is fully charged i take it out on AC power, sometimes i put it in while it going to into stand-by but typical i put it back in before or after.

not sure how much the extra info is going to help but may be someone else is having a similar issue and they can compare?

---

### Post by gila_monster on 2009-09-09
I've not had a problem with it with my panp4, but settings can change. What happens when you push Fn-F4? (That's the key on the p4 that starts/stops suspend mode.)

---

### Post by thomasaaron on 2009-09-10
Also, what do you have it set to do when the lid is closed (System > Prefs > Power Management)?

Another thing, while it has gotten better over time, multiple consecutive suspend resume cycles without ever powering the machine off can cause problems too. There still may be some bugs to work out there.

---

### Post by gamerchick02 on 2009-09-10
> **thomasaaron said:**
> Also, what do you have it set to do when the lid is closed (System > Prefs > Power Management)?

Another thing, while it has gotten better over time, multiple consecutive suspend resume cycles without ever powering the machine off can cause problems too. There still may be some bugs to work out there.

I notice this on the Pangolian. I got around it by setting up to not suspend when it's plugged in.

*shrug* I'm just happy the machine wakes up from suspend.

Amy

---

### Post by miniyak on 2009-09-11
> What happens when you push Fn-F4? (That's the key on the p4 that starts/stops suspend mode.) 

I set sleep button to "do nothing" because it is the in worst spot ever (i was accidentally going into suspend when i wanted to mute or put the volume down) I am curious as to what would happen if it were pressed while it was stuck but im not expecting any miracles.(because hard system function like silent mode and screen switching still seem to do things while stuck). Otherwise, while properly running, the button press induces suspend just as closing the lid would do.

> Also, what do you have it set to do when the lid is closed (System > Prefs > Power Management)?


Suspend, on AC power and battery
> 
Another thing, while it has gotten better over time, multiple consecutive suspend resume cycles without ever powering the machine off can cause problems too. There still may be some bugs to work out there.

I have had a strong feeling that this is the issue. As I may have mentioned before in previous threads that I only ever do a full shut down when I need to, other wise the panp5 is in suspend when not in use. Regardless, I was starting to get the idea that something being done was causing the this to happen more frequently.

---

### Post by miniyak on 2010-01-12
Well, I hate to revive a topic from the dead but i just did a fresh full install of karmic, and this issue is occurring everytime i try to put the Panp5 into suspend

did the s76 "restore system" and "install driver" w/ driver 2.4.4.

Whats next? maybe i should start whole new thread for this one.

Karmic's boot time is good (about 40 seconds on my panp5 if i remember correctly) but its still not good enough to beat resuming from suspend.

this wasn't happening with my first install of karmic so im finding this rather curious.. i must be missing something

---

### Post by thomasaaron on 2010-01-13
miniyak, are you using 32-bit? (I thought I saw something from you about that in another thread??)

If so, part of the reason we switched to 64-bit is because its support for suspend/hibernate was much better. It can probably be made to work in 32-bit, though, but you may have to do some configuration fiddling.

---

### Post by miniyak on 2010-01-13
No, this particular issue is occurring on a clean full karmic 64-bit install

 I'm using the 32 bit install on a HDD in an external enclosure. Didn't bother installing the s76 driver on the external for compatibility reasons. I was using this other disc internally for a day or so because i borked grub on my old dualboot jaunty/karmic install.

---

### Post by thomasaaron on 2010-01-13
OK, do you have your nVidia drivers enabled? 
System > Admin > Hardware Drivers

---

### Post by miniyak on 2010-01-13
Thats exactly it, I was just about to post when you did Tom, 

... this was fixed simply by installing the graphics driver. I guess things were resuming from stand-by but the screen was staying blank.
My previous 64 bit karmic install was suspending w/out the graphics driver... but I think this was only after I installed then uninstalled the driver.

Unfortunately this has lead to another issue. When I resume from suspend now the brightness is cranked all the way down. I also noticed this after the cold starts I was doing after being stuck in suspend.

I think i remember something like this coming up on the forums... ill look in a bit

I should also note that the nvidia driver changed my appearance settings cranking the desktop effect up to normal as opposed to none. I would normally suspect this was ubuntu's doing (auto detecting capabilities). But i suspect it has something to do with the driver. In my old jaunty install w/ the driver could never keep the "none" setting under desktop effects after a restart so I would have to manually switch it to none everytime i wanted to play a game. Hopefully this is not the case now

---

