---
title: "Halfway through the dev cycle..."
date: 2015-07-26
forum: Ubuntu Development Version
---

### Post by sgage on 2015-07-26
Well, here we are, about halfway through the development cycle, and it seems pretty quiet here. Doesn't seem to be that much going on, breakage-wise. In my use case, everything just works, and works well. I have basically forgotten that Wily is a development version ;)

It feels like a full-on rolling release...

---

### Post by dino99 on 2015-07-26
That is the way it goes, quietly  ;) as the canonical devs team are all on the 'next' projects. So we only get some debian packages synced and Tim pushing 'quietly' the gnome 3.17.x packages. Some move are also seen about python 3.5 migration. Wonder when unity 8 will land as the default version (i'm not a unity user, so no really care)

---

### Post by ventrical on 2015-07-26
Ummm ... zzzzzzzzzzzzzz ... hehe :)

No .. it has been really quiet.   Really. Updates, bugs, bug-fixes....it's like a Brahms Lullabye :) This is good .. but I think breakage will come in late August/early Sept..

Regards..

---

### Post by sudodus on 2015-07-26
One zenity bug is fixed, but another zenity bug came with the update today or yesterday. I intend to report it, not now, but I hope later tonight.

My mkusb is affected by those bugs, so I run into them, when I test that mkusb works with wily.

The current problem is due to a bug or missing feature to render html. You can test it with the following script

```
#!/bin/bash

echo "<h1>HTML headline</h1>
Hello World" | zenity --text-info --html --filename=/dev/stdin \
--width=$(($wadd+640)) --height=$(($hadd+400)) \
--title "$btitle" \
--ok-label="Go" --cancel-label="Quit" \
--checkbox="Check this box if you are ready to go"

```

It should look something like the attached file (which is made in precise, but it worked a few days ago also in Wily).

***Edit:***

I have reported this bug at Launchpad, bug #1478386 'zenity's option to render html does not work'

Please check it, and please mark that it affects you too (if it does).

---

### Post by dino99 on 2015-07-26
> **ventrical said:**
> Ummm ... zzzzzzzzzzzzzz ... hehe :)

No .. it has been really quiet.   Really. Updates, bugs, bug-fixes....it's like a Brahms Lullabye :) This is good .. but I think breakage will come in late August/early Sept..

Regards..

no, no, that feature has been removed; no more breakage  :p:p

---

### Post by PaulW2U on 2015-07-26
> **dino99 said:**
> Some move are also seen about python 3.5 migration. Wonder when unity 8 will land as the default version (i'm not a unity user, so no really care)

I'm a Unity user now, having rejected Plasma 5 although I still have KDE 4 on two spare laptops.

All of my ISO tests have shown all flavours except Kubuntu to be in pretty good shape. I'm not criticising Kubuntu or Plasma 5 but it didn't work for me on my main machine.

Anyway, I'm now using two instances of Ubuntu 15.10 and both are rock solid as far as I am concerned. But stand-by PCs are ready and waiting for Unity8 to spoil things if indeed we see it this cycle. ;)

Anyway, apologies to sgage if he intended this to be an Ubuntu GNOME thread but all of my ISO tests proved UG to be in good shape :)

---

### Post by ajgreeny on 2015-07-26
> **dino99 said:**
> no, no, that feature has been removed; no more breakage  :p:p

:lolflag:
I do agree, however, that Wily has been pretty boring so far; nothing to put back together at all.

I've been running it in VBox since very early in its existence and can't remember any breakage so far.

---

### Post by sudodus on 2015-07-26
I agree, that there has been no major breakage (yet!) in Wily. But I find several minor bugs when isotesting Lubuntu (and as I said with zenity too).

---

### Post by sgage on 2015-07-26
> **PaulW2U said:**
> I'm a Unity user now, having rejected Plasma 5 although I still have KDE 4 on two spare laptops.

All of my ISO tests have shown all flavours except Kubuntu to be in pretty good shape. I'm not criticising Kubuntu or Plasma 5 but it didn't work for me on my main machine.

Anyway, I'm now using two instances of Ubuntu 15.10 and both are rock solid as far as I am concerned. But stand-by PCs are ready and waiting for Unity8 to spoil things if indeed we see it this cycle. ;)

Anyway, apologies to sgage if he intended this to be an Ubuntu GNOME thread but all of my ISO tests proved UG to be in good shape :)

No worries - I used the Gnome prefix just because that is what I use and know best. In fact, it's good to hear from the other flavors - probably shouldn't have bothered with the prefix... :KS

---

### Post by coffeecat on 2015-07-26
> **sgage said:**
> No worries - I used the Gnome prefix just because that is what I use and know best. In fact, it's good to hear from the other flavors - probably shouldn't have bothered with the prefix... :KS

Fixed that for you! We have a prefix for every occasion. :wink:

---

### Post by sgage on 2015-07-26
Thanks coffeecat!

Love the avatar...

---

### Post by Cavsfan on 2015-07-26
Yes, it's odd no major breakage even when the 4.0 kernel was introduced. Now already on the 4.1 kernel and still no breakage.
 I remember in Vivid a new kernel causing severe breakage that lasted for a while.

Maybe that was later on in the cycle though.

I'm testing Ubuntu 15.10 gnome FB with compiz of course and Ubuntu Mate 15.10 on 2 partitions. No major problems so far.

I installed Arch Linux on my main linux partition using Xcfe exclusively. It's a hard one to get installed but then there's no going back. :lolflag:

---

### Post by Cavsfan on 2015-07-26
> **sgage said:**
> Thanks coffeecat!

Love the avatar...

Yeah that is a coffeecat indeed LoL!

---

