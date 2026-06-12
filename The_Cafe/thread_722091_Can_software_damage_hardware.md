---
title: "Can software damage hardware?"
date: 2008-03-12
forum: The Cafe
---

### Post by rajeev1204 on 2008-03-12
hi

Iam using the development version of hardy and i was wondering if there is any danger to the hardware like the CPU or graphics card etc.

For example, like different driver versions of graphics driver seem to show different temperatures for the GPU,so do these critical components have in built checks to ensure that faulty code doesnt ruin it.



thanks and regards
rajeev

---

### Post by amingv on 2008-03-12
Yes and no.

Yes because software controls hardware, and it can make it perform a damaging operation. (i.e.  if the hardware moves)

No because software is nothing but a flow of electricity, and it cannot damage hardware by itself.

Now, software _can_ damage other software in the hardware that makes it work, but this doesn't essentially break the hardware. Finally, as unstable as Hardy may be, I doubt you should worry about these matters..

---

### Post by WalmartSniperLX on 2008-03-12
Also if the software gains low level control of the hardware, it can sometimes do fatal damage to the hardware. This is rare but it can happen. Think about overclocking. All you're doing is changing settings in the BIOS by being allowed access to low level settings. Mess with the wrong things and you can kiss your hardware goodbye. There are viruses that go about this method.

Basically, all hardware is driven by software. So technically, it is possible to destroy your hardware (or at least make it unable to operate) by messing with software.

In your case though, I don't think this is of any concern :P But it is something worth knowing.

---

### Post by wormser on 2008-03-12
The upgrade to Gusty blew my eternal amplifier for sound.  :cry:
[http://ubuntuforums.org/showthread.php?t=620618](http://ubuntuforums.org/showthread.php?t=620618)

---

### Post by quanumphaze on 2008-03-12
I remember reading somewhere that a bad xorg.conf file cad blow up an old CRT monitor by using unsupported frequencies/resolutions. Newer monitors don't though and can detect it. So software can damage hardware. And this is nothing to worry about for LCD screens.

There is also some problem with laptop HDD spindowns that can shorten it's life for some people. It's a real problem today if you set the spin down time too short. It will park the HDD heads only to start up again.

Back on track. The mentioned overclocking can melt your hardware, but I seriously doubt that Hardy dev will decide to access low level BIOS features and overclock it (even if you tried).

Chances are that Hardy will be less a risk than Gutsy or any other stable or unstable OS.

---

### Post by bobbocanfly on 2008-03-12
Yes it can. Bad, low-level code can do a lot of damage. Fortunately though, you are unlikely to get any hardware damage using Hardy (especially now FeatureFreeze has passed) as everything is tested multiple times upstream and then before it is uploaded into the repositories downstream.

---

### Post by hhhhhx on 2008-03-12
technically yes, but mostly no :)

---

### Post by kdm on 2008-12-04
I didn't think it was possible, until the Ibex Alpha Intel network card fiasco !

---

### Post by x0as on 2008-12-04
Yes, the release version of Mandrake 9.2 bricked some LG cd/dvd drives.

---

### Post by p_quarles on 2008-12-04
A famous instance was older versions of X causing CRTs to explode. You had to have settings outside what was supported by the screen, of course, but it did happen. 

Hardware design usually involves safeguards against allowing software to do things that would damage it. For instance, CPUs have a lot of safeguards built in against overheating. That's only as good as the hardware designer, though, and only protects against things they thought of in advance.

---

### Post by Daveski on 2008-12-04
> **WalmartSniperLX said:**
> Mess with the wrong things and you can kiss your hardware goodbye. There are viruses that go about this method.


I seem to remember that there was an Amiga virus that played a tune on the internal floppy drive by spinning the main drive motor at different speeds. This usually did not damage the drive, but the bashing the read heads against the stops for percussion usually did :-)

---

### Post by iosefatu on 2009-02-17
I've changed Nvidia VGA after Ubuntu 7.10 and 8.10, also sound card working in another way than before. Now I changed back to XP. The problem was like in drivers, but i changed VGA completely. Was no possible to work, blue screens always

---

### Post by hyperdude111 on 2009-02-17
I theory yes.

eg. You use software to overclock your cpu to max then start converting videos. Your cpu will fizzle, burn then die........

---

### Post by PythonPower on 2009-02-17
Software can damage hardware. For example, improperly setting the CRTC settings can damage a monitor; refresh rates can, I have heard, damage old CRT monitors.

---

### Post by adamlau on 2009-02-17
Constantly running disk intensive tools can certainly shorten the lifespan of drives.

---

### Post by marcgh on 2009-02-17
Overburning a DVD (putting more data than the total available) does certainly ruin the DVD writer.

RIP my LACIE 40x - Lightscribe

---

### Post by tom66 on 2009-02-17
Very old memory can be damaged by attempting to address memory out of range. It can end up destroying it. For example, if you had 16 address lines (16 bits, 64K memory) but only 10 of those lines actually corresponded to memory cells (10 bits, 1K memory), then you can damage the memory by writing to the upper 4 bits.

If the software can make the speakers move between the two minimum and maximum states, then it can eventually damage them, especially if it tries to go beyond the tolerances of the device. And if it does this at a low frequency, you might not even notice. I don't know of any virus that can do this, though. 

The software can switch off the fan, and with a faulty temperature sensor the computer can be damaged if it doesn't shut down. It might even possible for software to switch off the sensor, shutoff control and other features. 

Running the HDD at full speed and moving the head backwards and forwards is likely to break it. Also stopping and starting is supposed to shorten the life of a drive. 

When you run a CRT at a higher frequency than designed, you can hear a whining. That usually indicates something is running at a very high frequency, higher than normal, and can shorten the life of the screen. 

Formatting a drive completely can damage it, as you can override factory formatting and the drive will never be recognized again. Same for BIOSes.  

And through obscure bugs, it may just be possible to overwrite the microcode in a CPU (which I doubt, but it may be possible). If you did this, then the CPU would never recognize a single instruction again. 

Flash memory can only be written about 100,000 times. If you constantly overwrite data, you will eventually render the flash useless, as nothing can be written to it again after this.  

You can corrupt the firmware in many devices, such as WiFi cards, rendering them completely useless. 

The Motorola 6800 can damage the computer's bus lines by the instruction 'HCF' (Halt, then Catch Fire). It successively toggles each of the bus lines, but it does it so fast that it can damage them. It was intended for manufacturer testing. 

Also: [http://trixter.wordpress.com/2006/02/02/computing-myth-1-software-cannot-damage-hardware/](http://trixter.wordpress.com/2006/02/02/computing-myth-1-software-cannot-damage-hardware/)

---

### Post by Pbethe on 2010-01-19
> **adamlau said:**
> Constantly running disk intensive tools can certainly shorten the lifespan of drives.

So, my question would be, can installing Ubuntu and booting from the live CD kill off a CD drive?  I had two drives go bad last year. The first was quite old, but its replacement was new.
You can read all about it on my thread:

[http://ubuntuforums.org/showthread.php?t=1180017]("http://ubuntuforums.org/showthread.php?t=1180017")

---

### Post by J V on 2010-01-19
In theory, your average windows virus could easily turn off the fan and then send the CPU into overdrive (followed by meltdown)

But open source software just won't do that...

---

### Post by Techsnap on 2010-01-19
> But open source software just won't do that.

There have been numerous ocassions where Linux has totally bricked hardware. You could even check the rest of this thread.

---

### Post by juancarlospaco on 2010-01-19
Yes, 
install Windows Vista Starter and see, it damage Hardware, itself, people, and cats

---

### Post by gnomeuser on 2010-01-19
[the Intel e1000e](http://lwn.net/Articles/304105/) displays just one recent example of this happening.

---

