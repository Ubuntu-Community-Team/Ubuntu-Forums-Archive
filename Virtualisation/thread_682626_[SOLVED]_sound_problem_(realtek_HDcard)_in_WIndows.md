---
title: "[SOLVED] sound problem (realtek HDcard) in WIndows XP running in VIrtualbox under Ubu"
date: 2008-01-30
forum: Virtualisation
---

### Post by cyneuron on 2008-01-30
hi there

just installed latest virtualbox on ubuntu gutsy. everything worked fine, except the sound.

in virtual windows xp, it doesn't show any driver in device manager.

when i tried to update driver :

1. automatically, no result.

2. gave it the location of original realtek high definitin sound driver files, no result..

have tried all four option, namelu, Null, ALSA, OSS, PulseAudio in Virtualbox Sound Setting.

is there any way to configure sound in Windows XP under Virtualbox under Ubuntu ?

(have searched on google, lot of posts with same problem with no result)

please help...

---

### Post by kyphi on 2008-02-01
There are no drivers to be installed in your VirtualBox installation of XP.  Sound comes from your Ubuntu installation.

You MUST install your guest additions.

I assume that you have sound in Gutsy.

I have my sound option set to OSS.

---

### Post by cyneuron on 2008-02-02
problem is solved. i was using modified version of xp (with nlite, in which i had removed all the drivers from windows installation disc).

now working fine. thanks.

---

### Post by Loffe_ on 2008-06-01
> **cyneuron said:**
> problem is solved. i was using modified version of xp (with nlite, in which i had removed all the drivers from windows installation disc).

now working fine. thanks.

I am also using an nLited xp version. Did you do a full xp reinstall? If not, where can I find the missing sound driver?

I don't want to install a full xp if all a need is a sound driver...

Thanks

---

### Post by pizpot on 2008-06-01
While running the XP virtual machine, click Device->Install Guest Additions. Then Shut Down the XP virtual machine, and turn on the Audio for that machine. ie) select it on the left, and then on the right, click Audio->Enable Audio.

---

### Post by Jarige on 2009-08-07
Now how did you solve it? I've got exactly the same problem :)

---

### Post by Jose Catre-Vandis on 2009-08-07
For me, using nlited XP installs I used an old set of Realtek drivers. They are hard to find now on the realtek site, but I got them off an old driver install CD i had lying around. You can download them here:

[http://rapidshare.com/files/218676901/Realtek2004.rar](http://rapidshare.com/files/218676901/Realtek2004.rar)

---

### Post by Jarige on 2009-08-08
Damn, I hate RapidShare. It won't work 50% of the time for me, and this is such a time.
Can you upload it somewhere else plz? Or ad it as attachment in your next message if its not too big.

---

### Post by Jose Catre-Vandis on 2009-08-08
It's 11 mb so can't attach here. Keep trying with RS, it works fine here. 217 other people needed this and got it too!

---

### Post by Jarige on 2009-08-08
Thanks, after a reboot RapidShare allowed me. 
It doesn't want to install still. I've tried some drivers before, those gave me a blue screen. These drivers just crash when installing. Giving Windows error report, then telling me that install was succesful. Reboot; nothing. :(

---

### Post by Jarige on 2009-08-08
After reboot it says found new hardware (as every boot does).

---

### Post by Jose Catre-Vandis on 2009-08-08
Oh dear, the reason for using the old set of drivers from 2004 was because the current drivers do just as you said and crash out on install or crash Windows, whereas the old ones do work. Have you cleared out all the old drivers completely?

---

### Post by Jose Catre-Vandis on 2009-08-08
> **Jarige said:**
> After reboot it says found new hardware (as every boot does).

So have you got sound?

---

### Post by Jarige on 2009-08-09
It still doesn't work, and I don't know whether I cleared the drivers, so I guess not :)
I don't exactly know how to do that either...

---

### Post by Jarige on 2009-08-09
BTW, it will find my hardware correctly (at first it didn't) but it asks for a driver file: 'ALCXWDM.SYS'. I found this in this map: C:\Program Files\Realtek AC97\ and it probably got extracted by previous drivers I tried. When I select that one, it will continue, but crash when its almost done.
The drivers I got from you crashed on the same time. I just executed setup.exe, and after a while it crashed. No extraction of 'ALCXWDM.SYS' as far as I know.

---

### Post by Jose Catre-Vandis on 2009-08-09
Hmmm, not sure what else to suggest, don't think you can extract the setup.exe and install manually. I'll have a look for something else to help.

This might help for cleaning out.

[http://www.tomshardware.co.uk/forum/page-245488_10_0.html](http://www.tomshardware.co.uk/forum/page-245488_10_0.html)

---

### Post by Jarige on 2009-08-09
Thanks for the help so far, I'll just hope to hear from you again.
I'll use Windows 7 then, although it boots very slow, the sound works there.

---

### Post by kopcicle on 2010-04-09
Jose Catre-Vandis 
I know this is an older thread but ...
Worked for me . Realtek 2.11.15.0 installer, Win XP Sp3 guest ,Ubuntu 9.10 host, VBox 3.1.6 . OSS is checked in audio settings in virtualbox menu . 

~kop

---

### Post by Jarige on 2010-04-09
Could you give a link to the driver installer?
My installer keeps giving a bsod :S Even in a VM Windows sucks -.-'

---

