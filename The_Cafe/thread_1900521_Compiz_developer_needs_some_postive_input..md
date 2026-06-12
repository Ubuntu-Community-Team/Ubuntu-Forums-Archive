---
title: "Compiz developer needs some postive input."
date: 2011-12-26
forum: The Cafe
---

### Post by Linuxratty on 2011-12-26
Would you good folk pop over and chat him up a bit?

[http://smspillaz.wordpress.com/2011/12/25/apology-2/#comment-6076](http://smspillaz.wordpress.com/2011/12/25/apology-2/#comment-6076)

---

### Post by Paddy Landau on 2011-12-26
Done!

---

### Post by BigSilly on 2011-12-26
Sounds like he needs help rather than well wishing... :(

---

### Post by grahammechanical on 2011-12-26
Coincidently, I looked up the Compiz web site just the other day. I was looking for some information on what each of the Compiz settings actually did because I have no idea. I was thinking of trying out a few of the effects on 12.04 to see what worked and what broke the desktop.

The only effect I use is wobbly windows. That worked in 10.10 but not in 11.04 but it now works in 11.10 and 12.04. So, I was wondering what else worked and what did not work. But actually I do not know what all the settings are supposed to do.

That blog shows what effect negative comments can have on someone who is obviously working hard and doing his best.

Some Linux users are not shy about making negative comments. It can have a serious effect on some people. It must surely be against the Ubuntu code of conduct.

Do not moan - get involved.

Regards.

---

### Post by Paddy Landau on 2011-12-27
> **grahammechanical said:**
> ... wobbly windows ... worked in 10.10 but not in 11.04 but it now works in 11.10 and 12.04.
Funny; I'm using 11.04 and my Wobbly Windows works perfectly. You might have had a conflicting setting.

---

### Post by keithpeter on 2011-12-27
> **BigSilly said:**
> Sounds like he needs help rather than well wishing... :(

Hello BigSilly and all

That is what I tried to say when I left a comment on his blog. Speaking from personal experience (outside computing), it can be hard to recognise when you need help. But sometimes you do, and you need to accept that, and identify the bits of the project that are in most urgent need of attention. This process is not one of personal failiure but of professional growth.

Ubuntu Unity depends on compiz as the default window manager I understand, so perhaps Canonical will be putting some extra resources and time on this project.

Has the version of the Compiz package that Unity will depend on for 12.04 already been decided? Or is there a 'push' or 'sprint' for a package deadline for 12.04 coming up? 

Crunch points in projects make you realise where you are and how far you have to go (again from personal experience outside computing)!

---

### Post by Carterclan on 2011-12-27
> **grahammechanical said:**
> 

The only effect I use is wobbly windows. That worked in 10.10 but not in 11.04 but it now works in 11.10 and 12.04. So, I was wondering what else worked and what did not work. But actually I do not know what all the settings are supposed to do.



How are you doing that, I can't get any effects to work in 11.10. I did find a workaround in 11.04 that pretty much enabled everything but have been unable to do so in 11.10 :(

---

### Post by ergo-proxy on 2011-12-27
It's hard to disagree that Compiz project needs more developers or a kind of project manager...

---

### Post by grahammechanical on 2011-12-27
@carterclan

did you upgrade or fresh install? I saw all the problems people where having going from 11.04 to 11.10 and I fresh installed. I also had 11.04 as a fresh install on another partition and I converted it to 12.04. I have just not had the nerve to test any of the other Compiz effects.

I have decided that when 12.04 is officially released I shall fresh install it on my working partition. I shall also reformat my /home partition as I agree with Paddy Laundau that settings conflicts are often the cause of some problems.

Regards.

---

### Post by Paddy Landau on 2011-12-27
> **grahammechanical said:**
> I shall also reformat my /home partition as I agree with Paddy Laundau that settings conflicts are often the cause of some problems.
All you need to with regard to Compiz is reset the settings. I think (but I'm not sure) that *Preferences > Reset to defaults* will do the trick. Alternatively, delete the relevant folders, which, as far as I can tell, are:
```
~/.gconf/apps/compiz-1
~/.gconf/apps/compizconfig-1
~/.compiz
~/.config/compiz-1
```Then log out and in again.

---

### Post by Carterclan on 2011-12-27
My 11.10 install was a fresh one not an upgrade. Admittedly I never tried that hard, just installed CCSM and tried turning on wobbly windows with no joy. After posting here today I thought I would give it another go still with no luck. However I have managed to turn them on using Ubuntu tweak!! makes no sense to me.

 I don't want to restore default settings in CCSM as I am using Ubuntu Unity Plugin Rotated which I much prefer to the standard Unity.

Hopefully we will be able to play with CCSM to our hearts content in 12.04 without the fear of breaking Unity

---

### Post by BrokenKingpin on 2011-12-28
I personally do not see the need for Compiz anymore. The big DEs already have compositing built in now with the same effects (kwin), and the lighter DEs do not need something as heavy as compiz.

If people still see the need for it then I hope the project continues though.

---

### Post by Pogeymanz on 2011-12-28
Kwin is the only one even close to Compiz's capabilities so far, and it is very lacking and performs way worse than Compiz. Every time I use KDE, I replace Kwin with Compiz.

---

### Post by BigSilly on 2011-12-28
> **BrokenKingpin said:**
> I personally do not see the need for Compiz anymore. **The big DEs already have compositing built in now with the same effects (kwin), and the lighter DEs do not need something as heavy as compiz**.

If people still see the need for it then I hope the project continues though.

Ubuntu still relies on it though. ;)

I like Kwin a lot, but Compiz is obviously more fully featured. I don't replace Kwin with Compiz on KDE personally, but I could understand why someone would.

I'm a bit confused though, as I thought Compiz development was now in house at Canonical for Ubuntu...:confused: Is the dev not really getting the support there?

---

