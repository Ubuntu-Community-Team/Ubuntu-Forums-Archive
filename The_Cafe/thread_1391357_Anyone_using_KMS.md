---
title: "Anyone using KMS?"
date: 2010-01-26
forum: The Cafe
---

### Post by Sashin on 2010-01-26
Has anyone here used systems with KMS before?
Is it supposed to affect the boot only, or also the actual desktop?
I have two computers and one has KMS enabled (it has an intel graphics card).

I've noticed that all the graphics on it look significantly crisper and sharper, to the point in which I get annoyed when looking at the other computer. I thought it was because of KMS but then after closer inspection, realised that it has a HD screen.

Is anyone able to confirm whether KMS is what is making things radically different or is it merely the screen?

---

### Post by Techsnap on 2010-01-26
Used it on Fedora, worked great, especially when you upgrade mesa it makes the FOSS ATi driver impressive.

---

### Post by Sashin on 2010-01-26
Yeah, I'm thinking of either installing fedora on my nvidia comp or upgrading the kernel.

---

### Post by Icehuck on 2010-01-26
It's nice, but it annoys me to no end when udev loads and it changes screen resolution mid boot.

---

### Post by handy on 2010-01-26
The next kernel or two should have KMS pretty well mainstream with any luck.

---

### Post by Sashin on 2010-01-26
The new one .33 has it. And even though lucid is getting .32, its being backported so that lucid will have nouveau.

---

### Post by RiceMonster on 2010-01-26
Works great on Fedora with an intel card

---

### Post by Sashin on 2010-01-26
Is the difference significant?

---

### Post by RiceMonster on 2010-01-26
> **Sashin said:**
> Is the difference significant?

For the bootscreen, yes.

---

### Post by Xbehave on 2010-01-26
I found (on ATI* atleast) it offers performance at the cost of stability, I had to disable it completely^ for fedora and am having a love/hate relationship atm, everything was fine for a while, but then an update introduced a crash that happens at a random point after boot (usually 10s of minutes).

*I have an RS482 chip though which is particularly ugly to code for

^The nice thing is that it is really easy to disable so while I currently don't have any compositing it doesn't make my machine unusable.

> **Sashin said:**
> Is the difference significant?
For open drivers (intel, radeon, nouvea) yes, KMS is required for DRI2, on my machine this means:
[LIST]
[*]1.5-2 times the fps in glxgears 
[*]support for more opengl features
[*]kwin compositing will work
[/LIST]

If you use closed drivers (flgrx or nvidia) then probably not

---

### Post by falconindy on 2010-01-26
KMS is what allows my laptop to load into X. Without, it's a hard crash every time.

I got a good laugh at the people who say that the "forced" switch to native mode resolution annoys them when the overriding majority of Ubuntu users rarely even see a VC or boot text. KMS is highly desireable if it causes no adverse effects.

---

### Post by MaxIBoy on 2010-01-26
Been using it for months, and it's great (Intel i915.) Basically, you can switch between VTs instantly. (But it won't cure cancer and fix your air conditioning, either.)

---

### Post by Sashin on 2010-01-26
VTs? what do you mean?

---

### Post by Icehuck on 2010-01-26
> **Sashin said:**
> VTs? what do you mean?

Virtual Terminal/Virtual Console. If you're in Ubuntu, hit ctrl alt F1 and you'll see one. Also hit alt-f7 to go back.

---

### Post by Sashin on 2010-01-27
oh, I've used those before, but I never knew what they were called.

---

