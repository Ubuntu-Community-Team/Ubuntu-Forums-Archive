---
title: "Any Other ATI Users Having a Hard TIme?"
date: 2009-04-30
forum: The Cafe
---

### Post by jimi_hendrix on 2009-04-30
so 8.10 comes out and i download it.  fglrx wont even activate, so its back to 8.04 for me because i like being able to scroll down screens without lag!  Then i decide to give 9.04 a whirl, and it took a seconds worht of lag to minimize anything...getting better i guess?

i have also had a hard time with a lot of other distros and my gfx (ATI mobility hd 3470) card...anyone else having the same trouble?

---

### Post by garythegoth on 2009-04-30
ATis Linux drivers are notorious for there unreliability and general suckiness....

---

### Post by jimi_hendrix on 2009-04-30
> **garythegoth said:**
> ATis Linux drivers are notorious for there reliability and general suckiness....

i am aware of that but they went from flawless in 8.04 to terrible!

---

### Post by garythegoth on 2009-04-30
How do you mean "from flawless"?

I like how easy to install the drivers are, but there performance and reliability have always been bad.

---

### Post by forrestcupp on 2009-04-30
Were you using Compiz in 8.04?  If not, maybe that's why it was flawless.  Fglrx isn't bad if you're not using compositing.

---

### Post by Falcon1002 on 2009-04-30
I had trouble on 8.10 with my radeon 1270 (it would not resume from stand by). The problem went away after I downloaded the driver for my card from amd's web site.

---

### Post by jimi_hendrix on 2009-04-30
> **garythegoth said:**
> How do you mean "from flawless"?

compiz with no lag, same with any 3d game i played

---

### Post by jimi_hendrix on 2009-04-30
> **forrestcupp said:**
> Were you using Compiz in 8.04?  If not, maybe that's why it was flawless.  Fglrx isn't bad if you're not using compositing.

see above

---

### Post by CharmyBee on 2009-04-30
Did you try using it without compiz enabled? It's not like it's essential now is it?

---

### Post by garythegoth on 2009-04-30
> **jimi_hendrix said:**
> see above

Hmmm. Maybe the drivers work better for HD2000+ cards or something. My x1250 in my laptop is not a pleasant experience with FGLRX.

---

### Post by jimi_hendrix on 2009-04-30
> **CharmyBee said:**
> Did you try using it without compiz enabled? It's not like it's essential now is it?

yes

---

### Post by Saint Angeles on 2009-04-30
with feisty and gutsy, i had to use a long, complicated, custom xorg.conf file to get FGLRX to run nicely. with hardy and intrepid, FGLRX was activated by default and I had no problems. 

but with jaunty, it loaded the open source driver for me and i got full compositing even with the live CD! it was crazy. even my videos play with no choppiness and everything is better... except for one small thing.

sometimes, while resizing a video while running compiz, it will log me off. its really annoying so now i run metacity with compositing and only load up compiz when i want to show off for people.

---

### Post by kk0sse54 on 2009-04-30
I have been using the fglrx drivers for a while now without any problems at all.

---

### Post by garythegoth on 2009-04-30
> **C!oud said:**
> I have been using the fglrx drivers for a while now without any problems at all.

Can I buy your magical ATi card please?

---

### Post by lavinog on 2009-04-30
The fglrx driver is generally pretty good.
The problem is that the support for 8.10 and 9.04 came a month after they were released, and ubuntu had to use a beta driver.
Both intrepid and Jaunty use newer Xserver versions that require changes to the fglrx drivers.

I think part of the problem had to do with changes in the dri2 spec right after ATI already implemented it.

---

### Post by Enicko on 2009-05-01
8.04 works fine for me on one machine, Jaunty was poohoriffic through beta though.  Both run on ATI cards.

Jaunty works now, but I needed professional help to get it running. And the fact that xinerama doesn't work, yea that's a buzzkill.  The catalyst interface needs an update, looks like it belongs on a 10 year old windows machine.

ATI needs to get it together.

---

### Post by garythegoth on 2009-05-01
Well, their supposedly concentrating all the resources they have into the Linux driver, but I dont exactly hold out much hope.....

---

### Post by pbpersson on 2009-05-01
I have been using Jaunty with an ATI Radeon card, no problems - I am using wobbly windows and Gnome-Do Docky

---

### Post by garythegoth on 2009-05-01
> **pbpersson said:**
> I have been using Jaunty with an ATI Radeon card, no problems - I am using wobbly windows and Gnome-Do Docky

Using the open source driver?

---

### Post by misfitpierce on 2009-05-01
I'm on 9.04 with an ATI card in laptop and its working fine... 3D effects got smoother for me... Works great.

---

### Post by jimi_hendrix on 2009-05-01
> **pbpersson said:**
> I have been using Jaunty with an ATI Radeon card, no problems - I am using wobbly windows and Gnome-Do Docky

and why am i not able to even minimize windows on normal settings without lag? (the none setting seems to get rid of the minimize button on my decoration)

---

### Post by lavinog on 2009-05-01
Something to mention:
The fglrx driver as of 9-4 will only work for newer cards.
Older cards (over 2 years old) will most likely have to use the open source driver.

If you want to say your driver works great or poorly, help out the community by posting what cards you are using.

I have a laptop with a Radeon 200m that is not supported by the new fglrx, but I havent tested it with the open source driver yet. (Will be after finals)

On my desktops I have a Radeon 3680 and a onboard Radeon 3200. Both work great with the 9-4 fglrx driver (with some display corruption in firefox, but that should be fixed next month).

---

### Post by garythegoth on 2009-05-01
> **lavinog said:**
> Something to mention:
The fglrx driver as of 9-4 will only work for newer cards.
Older cards (over 2 years old) will most likely have to use the open source driver.

If you want to say your driver works great or poorly, help out the community by posting what cards you are using.

I have a laptop with a Radeon 200m that is not supported by the new fglrx, but I havent tested it with the open source driver yet. (Will be after finals)

On my desktops I have a Radeon 3680 and a onboard Radeon 3200. Both work great with the 9-4 fglrx driver (with some display corruption in firefox, but that should be fixed next month).

It really shouldnt be a case of "fixed next month". nVidia can make decent drivers, why cant ATi?

---

### Post by Pasdar on 2009-05-01
My experience with ATI 3470 on Ubuntu is not good at all. Pre 9.04 I couldn't install Ubuntu on my laptop at all, but I can install with 9.04. I had to disable compiz to get rid of the lag with everything I did.Though I tried nexius with compiz on and it worked great, but verything else sux, incleading video playback and what not. Disabling Compiz makes it a bit better... At least I don't get a lag with everything I do... I can play video's.. etc. Basically my GeForce 6200 on a slow PC outperforms my ATI 3470 on a high end laptop, lol.

---

### Post by hatten on 2009-05-01
problem-free ATI-er here =P

---

### Post by lavinog on 2009-05-01
> **garythegoth said:**
> It really shouldnt be a case of "fixed next month". nVidia can make decent drivers, why cant ATi?

The issue is a regression from the last release. ATI releases a new driver every month. nVidia releases when they determine that it is ready. ATI made a deal that they will release their drivers with/without bugs so that they can constantly be moving forward.
Currently nVidia has the better driver because they have a better history with linux, ATI only recently started treating the linux community with respect. ATI at least provided the documentation for the open sourced drivers. The open source driver for nVidia had to be reverse engineered.

Many bugs in Ubuntu have a 'fixed next release' solution.
These are things that happen when you use a release schedule.

---

### Post by days_of_ruin on 2009-05-01
Do new ati gfx cards have problems?
Would this [one]("http://www.engadget.com/2009/04/28/ati-radeon-hd-4770-gpu-review-roundup/") work out of the box?

---

### Post by jmcboots on 2009-05-06
> **days_of_ruin said:**
> Do new ati gfx cards have problems?
Would this [one]("http://www.engadget.com/2009/04/28/ati-radeon-hd-4770-gpu-review-roundup/") work out of the box?

It worked for me with a fresh install! Everything but xinerama. So my dual head set up is currently a "duplicate" head. But all the 3d effects, fades, wobblies, etc, all work at 1600x1200.

---

### Post by pandasonic on 2009-05-29
I built a new PC with an ATI Radeon HD 4770.  I'm running Jaunty (64-bit).

I installed the restricted drivers and then got the "AMD/ATI unsupported hardware" message on the bottom right corner of my screen.  Installing Catalyst 9.5 from ATI's website fixed that.  Compiz works just fine, but I cannot suspend/hibernate if it's enabled.  Not having compositing enabled is fine by me.

However, I am unable to log out at all.  Any time I try to log out, the screen will turn black and my system freezes.

Any ideas?

ATI is pissing me off.  I got this card because it's cheap and works great with Windows but I'd love to be able to use my PC for something other than just playing games (which is what Windows is for).

---

### Post by Tipped OuT on 2009-05-29
ATI Radeon 9100/9000 IGP with open source driver over here. :(

---

### Post by randyklein99 on 2009-06-10
> **pandasonic said:**
> I built a new PC with an ATI Radeon HD 4770.  I'm running Jaunty (64-bit).

I installed the restricted drivers and then got the "AMD/ATI unsupported hardware" message on the bottom right corner of my screen.  Installing Catalyst 9.5 from ATI's website fixed that.  Compiz works just fine, but I cannot suspend/hibernate if it's enabled.  Not having compositing enabled is fine by me.

However, I am unable to log out at all.  Any time I try to log out, the screen will turn black and my system freezes.

Any ideas?

ATI is pissing me off.  I got this card because it's cheap and works great with Windows but I'd love to be able to use my PC for something other than just playing games (which is what Windows is for).

I got the same problem.  I had to use the RadeonHD without Acceleration to get the 4770 stable in 2D.  No 3D yet though.

---

