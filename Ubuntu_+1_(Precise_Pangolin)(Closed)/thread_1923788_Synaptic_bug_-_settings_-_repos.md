---
title: "Synaptic bug - settings - repos"
date: 2012-02-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Elfy on 2012-02-11
Not sure if this is the same as the reload sources bug, but it crashed while trying to access software sources.

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/930657](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/930657)

I fit is I'm sure it'll get the duplicate label.

Xubuntu :)

---

### Post by Penguin360 on 2012-02-11
Is Synaptic still included in the release? I heard it was removed and I don't see it in my 12.04 either.

---

### Post by Elfy on 2012-02-11
I use xubuntu - still installed by default and I would think a lot of people are going to install it whether it's installed in ubuntu by default.

---

### Post by dcstar on 2012-02-12
> **forestpiskie said:**
> Not sure if this is the same as the reload sources bug, but it crashed while trying to access software sources.

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/930657](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/930657)

I fit is I'm sure it'll get the duplicate label.

Xubuntu :)

I have had no problems with Synaptic in Gnome 3 - on my 64-bit 12.04 Alpha so far.

---

### Post by Harry33 on 2012-02-12
> **CodingBeaver said:**
> Is Synaptic still included in the release? I heard it was removed and I don't see it in my 12.04 either.

It is included, but it doesn't belong to the default installation.
It can be installed from Precise repos (universe) just like for example Vlc videoplayer.

---

### Post by Harry33 on 2012-02-12
> **dcstar said:**
> I have had no problems with Synaptic in Gnome 3 - on my 64-bit 12.04 Alpha so far.

If you have installed Precise, and also the latest version of Synaptic (0.75.5~exp5), you do very likely have some problems.
For example occasional crashing and inability to use the "Quick Filter".

---

### Post by ranch hand on 2012-02-12
I have not used Synaptic lately in my Xubuntu install.  Usually do my upgrades by chroot and then go visit to see if it still works.

I will not do that today.  I will go over and use Synaptic.  If there is a problem I will add my me too.

I need to figure out what to file a bug on for Xubuntu anyway.

Cups and cups related packages like the blues-cups package will not install correctly in the chroot environment.  dpkg has no problem configuring them when I get over there so it must have to do with the installation script in the deb package having some problem with chroot.

---

### Post by VinDSL on 2012-02-12
> **forestpiskie said:**
> [https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/930657](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/930657)
I added a "me too"...

Every time I open Synaptic, lately, it's like rolling dice!

For instance, it'll crash when I Reload the PPAs. I restart it, and it works fine.

Sometimes it'll never Reload the PPAs.  I have to use apt-get update from CLI.

Next session, it works on the first try...  

It never allows me to do a Quick Filter.  I have to open a separate Search window, blah, blah, blah.

Anyway, I added myself, as being affected.  ;)

**Edit**

Just thinking (while I was brewing another pot of coffee)...

Last night, I did a minor, incremental update, then restarted the computer (warm boot).

After the desktop came up, and fully loaded, I got an error message saying that Synaptic wouldn't load -- even though I hadn't touched anything -- hadn't even moved my mouse.

Weird stuff!

---

### Post by sammiev on 2012-02-12
Synaptic loads for me but it's dead.

---

### Post by Elfy on 2012-02-13
> **VinDSL said:**
> It never allows me to do a Quick Filter.  I have to open a separate Search window, blah, blah, blah.!

That's this one

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/928955](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/928955)

---

### Post by ranch hand on 2012-02-14
Forgot to report.

Did not leave a me to on the bug.  Worked fine for me.

It found some off the wall repo and changed the sources.list fine.  Then I manually choose the Calgary repo (has up to now been the US repo) and it changed that just fine.

I did add a me too to the quick search bug.  As I never use that feature I would never have known about it if someone hadn't mentioned it.  Certainly does not work to type into it.  Makes 28 on that bug.  A lot of folks must use that.

---

### Post by VinDSL on 2012-02-14
> **ranch hand said:**
> A lot of folks must use that.
Yeah, I use it every time I open Synaptic.

It's like "Google Search" for apt-get... suggestions even pop-up, as you type.  ;)

---

### Post by ranch hand on 2012-02-14
> **VinDSL said:**
> Yeah, I use it every time I open Synaptic.

It's like "Google Search" for apt-get... suggestions even pop-up, as you type.  ;)
I have used it.  Doesn't blow my skirt up.

I am one of the folks that think it is a waste of space.  If folks like it and use it I must be wrong on that.  Still am not going to be using it.

Hope they get it fixed though.  Kind of weird to click on it and nothing happens.

---

### Post by VinDSL on 2012-02-16
> **ranch hand said:**
> Hope they get it fixed though.  Kind of weird to click on it and nothing happens.
It's (quick filter) magically working tonight... LoL!

Go figure.  :D

---

### Post by mc4man on 2012-02-16
> **VinDSL said:**
> It's (quick filter) magically working tonight... LoL!

  
nothing like a little update sneaking in, .. & the 1st time i remember 'get screenshot' actually working

---

### Post by mc4man on 2012-03-04
This synaptic crash seems to have been fixed with latest upgrade to -  0.75.5
(no sign of issue here anymore

---

### Post by dino99 on 2012-03-05
Still crash here on i386 , logged as gnome-classic, and for many others ( bug #932432 )

---

### Post by Elfy on 2012-03-05
Waiting to see what happens now that synaptic has had an update - only get the issue when there are new packages available. At present there are none.

---

### Post by mc4man on 2012-03-05
This is the bug I was seeing -[ Bug#936677]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/936677")
which the bug in post 1 seemed more like than the one it was duped to - [Bug #932432]("https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/932432")
Though all seem quite similar
Any way on a new install today have tried every which way - no crashes

---

### Post by Elfy on 2012-03-05
Just done a reload and apply changes in synaptic. No crash.

---

### Post by VinDSL on 2012-03-05
> **forestpiskie said:**
> Just done a reload and apply changes in synaptic. No crash.
Just did a reload, and it crashed on me.

Second reload works fine...  ;)

---

### Post by ventrical on 2012-03-06
> **mc4man said:**
> This synaptic crash seems to have been fixed with latest upgrade to -  0.75.5
(no sign of issue here anymore

 Yes as of yesterdays updates it has reverted to it's old, rock-solid self again :)

---

### Post by VinDSL on 2012-03-06
> **ventrical said:**
> Yes as of yesterdays updates it has reverted to it's old, rock-solid self again :)
Dittos!

Working exemplary for me, now...

---

### Post by VinDSL on 2012-03-07
Hrm...

Spoke too soon...  :)

---

