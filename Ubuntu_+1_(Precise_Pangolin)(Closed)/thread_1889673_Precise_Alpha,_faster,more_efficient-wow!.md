---
title: "Precise Alpha, faster,more efficient-wow!"
date: 2011-12-01
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by ventrical on 2011-12-01
Precise Alpha is twice as fast as any of it's predecessors on older machines (this one Dell Inspiron B130) and it's just passing with flying colours and it uses  and manages (so far) the CPU resources correctly. Also I noticed that there seems to be some efficient memory swapping going on.

 Why can't we keep it in this state when it gets released in April 2012 ?

:)

Thanks Canonical. This is going to be an exciting testing period.

---

### Post by paul_in_london on 2011-12-01
> **ventrical said:**
> Precise Alpha is twice as fast as any of it's predecessors on older machines (this one Dell Inspiron B130) and it's just passing with flying colours and it uses  and manages (so far) the CPU resources correctly. Also I noticed that there seems to be some efficient memory swapping going on.

 Why can't we keep it in this state when it gets released in April 2012 ?

:)

Thanks Canonical. This is going to be an exciting testing period.

While I'm here, the way I like to do it, instead of installing the whole kit and kaboodle, is to use the minimal boot image to install a bare-bones system and then just install what I want (and no more) using aptitude. See this thread for example:

[http://ubuntuforums.org/showthread.php?t=1845284](http://ubuntuforums.org/showthread.php?t=1845284)

Doesn't mean I'm immune to breakage obviously, but it has its benefits.

---

### Post by ventrical on 2011-12-01
Honestly .. I kid you not.. I am testing Precise Alpha (full default) on this little 10GB hdd that only has a max 20MB burst and it is just flying.!!!! Everything is just falling into place. Pop here , open there.. absolutely no lag or moloases!! With Oneiric/natty/Lucid.. whatever.. I mean ..yes they were good, yes they were fast .. but this Alpha .. it is just awesome.. so awesome that I don't want to update it :)

---

### Post by deonis on 2011-12-01
sitting on it now, and it feels nice and stable. +1 to Unity and Ubuntu. Could be nice to see it customizable though

---

### Post by paul_in_london on 2011-12-01
> **ventrical said:**
> Honestly .. I kid you not.. I am testing Precise Alpha (full default) on this little 10GB hdd that only has a max 20MB burst and it is just flying.!!!! Everything is just falling into place. Pop here , open there.. absolutely no lag or moloases!! With Oneiric/natty/Lucid.. whatever.. I mean ..yes they were good, yes they were fast .. but this Alpha .. it is just awesome.. so awesome that I don't want to update it :)

That sounds pretty good for a full iso! I think I last started from scratch early in the oneiric cycle so my minimal oneiric install has metamorphosed into a minimal precise install. I wish I'd documented what I do to tweak things because I always struggle to remember. Things like:

[LIST=1]
[*]Disabling swap
[*]noatime instead of relatime in /etc/fstab if that's still beneficial
[*]Which services I disable at boot (and how I disabled them)
[*]Setting up firefox to use a RAM profile (tmpfs)
[*]Which kernel modules I blacklisted
[*]Can't think of anything else this second!
[/LIST]

EDIT: forgot about PPAs! I've cut it down to:

[LIST=1]
[*]chromium-daily
[*]ricotz-testing
[*]mozilla-daily
[*]xorg-edgers
[/LIST]

---

### Post by shuttleworthwannabe on 2011-12-02
Ok--I am curious. Firstly, did they fix the battery problem and the overheating problem on some laptops (mainly with the nvidia cards and intel graphics card).

I will try it on my oldish desktop (Core2Duo) for now.

---

### Post by ventrical on 2011-12-02
> **shuttleworthwannabe said:**
> Ok--I am curious. Firstly, did they fix the battery problem and the overheating problem on some laptops (mainly with the nvidia cards and intel graphics card).

I will try it on my oldish desktop (Core2Duo) for now.

I have this -00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) graphics on a Dell laptop and it is running cool as a cucumber and this is only a single core 1.6GHz Celeron.with ccsm running cube.

---

### Post by fjgaude on 2011-12-02
Okay, so far, 12.04 Alpha 1 is 40% faster, in video using GTKPerf, than 11.04. Of course I'm with Intel graphics. That makes it about 10% faster than 11.10 was.

---

### Post by shuttleworthwannabe on 2011-12-02
> **ventrical said:**
> I have this -00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) graphics on a Dell laptop and it is running cool as a cucumber and this is only a single core 1.6GHz Celeron.with ccsm running cube.

Tried the live USB on my Dell Latitude E5520 laptop with the Intel HD 3000 integrated graphics--I can confirm that while it is fast and agile, it's tempt runs is higher than native Windows 7 (area under the right side of the touchpad gets really hot!) and CPU fan keeps blowing relentlessly--this does not happen in Windows I am afraid. Also noticed, battery life to be lower (but could be because of the heating and CPU fan blowing all the time).

Anyway I thought I would feedback.

---

### Post by jmate24 on 2011-12-03
> **shuttleworthwannabe said:**
> Tried the live USB on my Dell Latitude E5520 laptop with the Intel HD 3000 integrated graphics--I can confirm that while it is fast and agile, it's tempt runs is higher than native Windows 7 (area under the right side of the touchpad gets really hot!) and CPU fan keeps blowing relentlessly--this does not happen in Windows I am afraid. Also noticed, battery life to be lower (but could be because of the heating and CPU fan blowing all the time).

Anyway I thought I would feedback.

yes battery life decreases on laptops if:

1. processor governor is set to performance all the time and there by increasing the fan speed and getting hot.
2. the screens brightness is set to maximum 100%
3. whether you are using wireless or a LAN cable (or not {no networking})
4. how many devices are connected to your laptop. (i.e. external USB 2.5" drive, printer, tv tuner, cameras, USB flash/pen/thumb drives, monitors, earphones/speakers, etc., etc., etc.)
5. the programs you are running from watching a movie to playing the latest mmorpg.
6. the age of the laptop (date of manufacture; older laptops generate more heat because they do not have the latest technology to keep things cool.)
7. your GPU.
8. how dusty it is inside your house and laptop. (i recommend blowing out your fan with a good vacuum with the bottom covers still on just aim for the vents and the CPU and gpu fan.
9. the ambient temperature inside your home/office/work-space.
10. whether you use a laptop cooler (using a sturdy metal one with more than one fan is the best.)

good luck.

---

### Post by alphacrucis2 on 2011-12-03
I thought the kernel 2.6.38 "feature" that caused these laptop power issues (known as the ASPM problem) was to be fixed finally in 3.2.?

Edit:

Phoronix tested a patch which is supposed to fix this problem:

[http://www.phoronix.com/scan.php?page=article&item=linux_aspm_solution&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_aspm_solution&num=1)

---

### Post by Jordanwb on 2011-12-03
Awesome. I'm not sure if my laptop is affected by this but it's still good news.

---

### Post by shuttleworthwannabe on 2011-12-03
> **jmate24 said:**
> yes battery life decreases on laptops if:

1. processor governor is set to performance all the time and there by increasing the fan speed and getting hot.
2. the screens brightness is set to maximum 100%
3. whether you are using wireless or a LAN cable (or not {no networking})
4. how many devices are connected to your laptop. (i.e. external USB 2.5" drive, printer, tv tuner, cameras, USB flash/pen/thumb drives, monitors, earphones/speakers, etc., etc., etc.)
5. the programs you are running from watching a movie to playing the latest mmorpg.
6. the age of the laptop (date of manufacture; older laptops generate more heat because they do not have the latest technology to keep things cool.)
7. your GPU.
8. how dusty it is inside your house and laptop. (i recommend blowing out your fan with a good vacuum with the bottom covers still on just aim for the vents and the CPU and gpu fan.
9. the ambient temperature inside your home/office/work-space.
10. whether you use a laptop cooler (using a sturdy metal one with more than one fan is the best.)

good luck.
These are good laptop etiquettes --irrespective of what OS ur using.

I follow all these and yet, in Ubuntu fan and battery life suck big time.

I am saying this is not fixed, yet.

---

### Post by thatguruguy on 2011-12-03
There's still [some talk]("http://www.webupd8.org/2011/11/rhythmbox-confirmed-as-default-music.html") about making Jupiter part of the default installation, or at least including it in the regular repositories.

I haven't tried installing Jupiter on my Precise test machine, but it works well in Oneiric.

---

### Post by sammiev on 2011-12-03
Running 12.04 here with Jupiter and haven't noticed any problems to date.

---

### Post by rtalcott on 2011-12-11
I have 2 real installs...one on a 3 GHz P4 and one on a Phenom 9600 and both machines seem to be very fast...faster than any of the previous versions of Ubuntu...it's not subtle at all...

---

### Post by ventrical on 2011-12-11
My Dell Inspiron B130 is not exactly a high-end performance machine - but I found it noteworthy to document how Precise alpha-1 seems to make a perfect fit with the hardware.  I do not think this is one of those phantom hybrid stories either although I cannot , at this point, really explain why it works so well on the Dell.

  I am assuming that  during the install process that all the hardware was recognized and the correct drivers were installed and that there is  no bottle-neck between the hdd and the other bus components.

---

