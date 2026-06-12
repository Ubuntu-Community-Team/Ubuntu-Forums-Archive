---
title: "Linux 3.3.1 on Precise | Copy trick not required now?"
date: 2012-04-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by VinDSL on 2012-04-04
I just installed the Linux 3.3.1 mainline kernel.  Working great!

It might be a fluke, but this is the first time that I haven't had to muck around with the "cp trick", to get the nVidia module to build (on Linux 3.3).  I even did a cold boot, to make sure I wasn't seeing things.

Also, I should mention, prior to installing Linux 3.3.1, I performed 331 upgrades (believe it or not) via Synaptic.  LoL!  :D

So, I don't know if they patched the kernel, or addressed it with one or more of the upgrades -- or I just got lucky -- but, my fingers are crossed, hoping that we're past that dismal period.

Anyone else install Linux 3.3.1 yet?

Did you have to use the copy trick?!?!?

---

### Post by bmbaker on 2012-04-05
I built the kernel from source without having to use any cp tricks :-)

---

### Post by Harry33 on 2012-04-05
Well at least Nvidia proprietary drivers in xorg-edgers (for xserver 1.12) have been rebuilt with a patch to to cope with linux 3.4 rc1 too.

---

### Post by dino99 on 2012-04-05
no need to tweak if you have the latest nvidia-current from edgers ppa, even kernel 3.4 install smootly.

---

### Post by VinDSL on 2012-04-05
> **dino99 said:**
> no need to tweak if you have the latest nvidia-current from edgers ppa, even kernel 3.4 install smootly.
Aha!  I'm running 295.33-0ubuntu1, from the Ubu restricted PPA.  It's survived several boots, and no fiddling required.  

I'll switch to the edgers PPA version later today.

I would love to get Linux 3.4 running but, no joy, so far (kernel panic).

Thanks!

---

### Post by dino99 on 2012-04-05
kernel 3.4  works nicely here with i386 & gnome-classic & nv current from edgers

---

### Post by VinDSL on 2012-04-05
> **dino99 said:**
> kernel 3.4  works nicely here with i386 & gnome-classic & nv current from edgers
Which xserver are you running?

I'm using 1.11.3 currently...

---

### Post by dino99 on 2012-04-05
> **VinDSL said:**
> Which xserver are you running?

I'm using 1.11.3 currently...

its xserver 1.12.0 from ricotz

---

### Post by VinDSL on 2012-04-05
Well, well...

I haven't *tried* to install xserver 1.12 since December.

Heh!  It worked this time!  :D

So, I'm halfway there; edgers nvidia-current & xserver 1.12.0

I'll give Linux 3.4rc1 another whirl now...

---

### Post by VinDSL on 2012-04-06
Everything compiled, just fine, without a single error, but...

I'm still getting a kernel panic when booting into Linux 3.4rc1

Oh, well, that's okay!  Maybe rc2 will work a treat.

Getting xserver 1.12.0 installed (finally) was a major accomplishment, IMO. :)

Anyway, back on topic, evidently the copy trick is no longer required.  Yeah, team!

---

### Post by VinDSL on 2012-04-07
w00t!  Just realized it's the weekend.

I judge Linux 3.4rc2 will be available soon, if things go according to form.

If not, I'll try the current daily...  ;)

---

### Post by xebian on 2012-04-07
> **VinDSL said:**
> w00t!  Just realized it's the weekend.

I judge Linux 3.4rc2 will be available soon, if things go according to form.

If not, I'll try the current daily...  ;)

3.4 rc2 is just out.  compiling now.

---

### Post by VinDSL on 2012-04-08
> **xebian said:**
> 3.4 rc2 is just out.  compiling now.
Sweet!  I'll try it, when I get home, in a few hours.

I got tired of waiting, and upgraded my Liquorix kernel instead of the daily...  :D

---

### Post by VinDSL on 2012-04-08
w00t!  Worked that time!


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-8-apr-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-8-apr-2012-1.png")[/INDENT]


I went the PAE route with 3.4rc2, even though I don't need it...  ;)

---

### Post by compuguy1088 on 2012-04-08
Lucky for you that the nvidia drivers work. For both 3.3.1 and 3.4.0 RC2 (amd64), I've gotten Kernel panics/oops with the proprietary drivers. I've posted logs here in reference to another bug...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/944772/comments/96](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/944772/comments/96)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/944772/comments/97](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/944772/comments/97)

---

### Post by VinDSL on 2012-04-09
> **compuguy1088 said:**
> Lucky for you that the nvidia drivers work.[...]
Yeah, I'm "lucky" that way.  :D

However, apport is driving me crazy, so I disabled it (for now).

```
_Disable Apport_

Temporarily:

sudo service apport stop

Permanently:

sudo gedit /etc/default/apport

(Change enabled=1 to enabled=0)
```

AFAIK, 3.4rc2 hasn't been patched for apport, and I *think* the error dialogs are bogus...

---

