---
title: "Speakers not recognized if pre-plugged"
date: 2008-08-24
forum: System76 Support
---

### Post by glacialfury on 2008-08-24
Awkward title, eh?  Wondering if this happens to anyone else, and whether there is a remedy for it.

If I turn the Serval on and there is something in the headphones jack (either headphones or a speaker plug), it ignores those devices and plays all sounds from the laptop speakers.  If I unplug the headphones/speakers and plug them in again, it appropriately recognizes them and starts using them.

This is awkward because I have the laptop volume turned all the way up (to be with the speakers), and ideally I'd turn the speakers off if I didn't want to hear the startup noises etc, but it will come blasting through the laptop speakers.

Anyone have any tidbits that I might glean?

---

### Post by jeamer on 2008-08-24
I have this problem too, and would love a remedy. Mine recognizes both the external speakers and the laptop speakers as well. Tough on the laptop speakers when it's turned up to the externals on boot.

---

### Post by thomasaaron on 2008-08-25
Well, off the top of my head, I'd say it is a jack-sensing, hardware-related feature. I believe jack-sensing waits for a change in impedance (i.e. something with a certain amount of impedance being inserted into the jack). Since it is not sensing that *event*, it defaults to the laptop speakers. 

If I'm right, there probably isn't a cure for it short of a bios update that addresses that issue (which well may not exist).

What laptop are you using? I want to do some testing on this on other laptops. It could be a bios-level bug, or it could be there is a reason for this behavior. Interesting...

---

### Post by darkknight045 on 2008-08-25
I have this on the GazP5, also if I use the mute key(the 1st key on the right where the hotkeys are) then unmute it defaults to the speakers again.  I think, in my case, it will still play out the headphones but it also plays out the speakers.

---

### Post by eldragon on 2008-08-25
ive noticed this too on every laptop i tried.

if the headphones are on during boot, it defaults to laptop speakers instead. 

i think there is something missings during the harware check in order to see if there is something plugged or not.

fixing it should be trivial (if i knew where to look)

---

### Post by jeamer on 2008-08-25
I have it on the PanV3. Note that it recognizes BOTH the laptop and external speakers after bootup. Weird.

---

### Post by thomasaaron on 2008-08-25
Guys, I think this is probably a feature that is there for a reason (though, admittedly, I'm not sure what that reason is). I'm researching it.

It happens to laptops made by msi, asus and compal. I'm betting it happens on many others as well (although I have no others to test on).

---

### Post by glacialfury on 2008-08-25
I'm on a Serval 4.

---

### Post by glacialfury on 2008-08-28
As a workaround then for the laptop, rather than leaving it muted (which I may forget to do before I shut it down), is there a way to shut off the "daDONK" that plays when the login screen first appears?  

I'm assuming that the sound settings won't touch this, because the sound settings I know how to reach are specific to my login session.  I'd be happy with a silent bootup, which is all I was going for by leaving headphones/speakers plugged in anyway.

---

### Post by unutbu on 2008-08-28
Go to System>Administration>Login Window.
Click the Accessibility tab.
Uncheck the "Login screen ready" box. The daDONK sound I believe is caused by the question.wav file (/usr/share/sounds/question.wav).

---

