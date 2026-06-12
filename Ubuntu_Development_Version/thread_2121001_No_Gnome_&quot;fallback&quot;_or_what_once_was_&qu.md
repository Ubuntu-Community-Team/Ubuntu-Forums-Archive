---
title: "No Gnome &quot;fallback&quot; or what once was &quot;classic&quot;"
date: 2013-02-28
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2013-02-28
Just wondering if anyone is experiencing this. When I booted up into Raring today I was looking at Unity even though I had Gnome fallback selected.
I logged out and back in: same thing. Installed all of the updates along with the 3.8.0-8 kernel and it's still the same.

It will not go into anything except Unity no matter what I select before logging in. :-s

---

### Post by kurt18947 on 2013-02-28
If you check the repositories, you should find "gnome-session-fallback".  It used to install when I installed gnome-shell but it didn't this go-round.  I believe in the future 'gnome-classic' is going to be a gnome shell extension.  The good news here is that there are a bunch of choices if you find Unity not to your taste.  You're aware of MATE?  Or Cinnamon, Xfce, LXDE all of which install with/on top of Ubuntu?

---

### Post by Cavsfan on 2013-02-28
> **kurt18947 said:**
> If you check the repositories, you should find "gnome-session-fallback".  It used to install when I installed gnome-shell but it didn't this go-round.  I believe in the future 'gnome-classic' is going to be a gnome shell extension.  The good news here is that there are a bunch of choices if you find Unity not to your taste.  You're aware of MATE?  Or Cinnamon, Xfce, LXDE all of which install with/on top of Ubuntu?

Ironically I have that installed. I even selected it when I logged in. I was just trying to float through this testing cycle, but it is going crazy as of today and I may have to just do a clean install.
I have LXDE installed but, not real fond of it and I have tried MATE or Cinnamon I forget.

Yesterday it booted up into Gnome fallback just fine and today it went into Unity for no good reason. I think it's just borked. I have logged out and rebooted and nothing changes.

I just put that in the title of the thread because I didn't know they were changing Classic to Fallback.
Thanks for the reply!

---

### Post by kurt18947 on 2013-02-28
There have been a LOT of updates the past few days.  So far 13.04, even though it's early in the development cycles has been much better behaved than 12.10 gnome remix.  I'm not a Unity fan either but gnome-shell with a few extensions and add-ons has worked out pretty well for me.  I installed Xfce on 12.10 and though it certainly won't win any graphic design awards, it was better behaved.  My biggest complaint with 12.10 was power management.  It'd go into suspend fine, it wouldn't come out in a usable state due to a firmware bug. None of this on 13.04 so far.

---

### Post by Cavsfan on 2013-03-01
> **kurt18947 said:**
> There have been a LOT of updates the past few days.  So far 13.04, even though it's early in the development cycles has been much better behaved than 12.10 gnome remix.  I'm not a Unity fan either but gnome-shell with a few extensions and add-ons has worked out pretty well for me.  I installed Xfce on 12.10 and though it certainly won't win any graphic design awards, it was better behaved.  My biggest complaint with 12.10 was power management.  It'd go into suspend fine, it wouldn't come out in a usable state due to a firmware bug. None of this on 13.04 so far.

It is pretty early in the development process but, right now when I select Gnome Fallback I get Unity. I am currently backing stuff up and going to try another clean install from the daily iso.
I don't have any real problems with Quantal 12.10; mine suspends and awakes just fine.

I just got a bunch of updates and rebooted. It's still the same. I can tolerate Unity but, when Classic or fallback is available, it should work. Time to do a fresh install.

---

### Post by kurt18947 on 2013-03-01
> **Cavsfan said:**
> It is pretty early in the development process but, right now when I select Gnome Fallback I get Unity. I am currently backing stuff up and going to try another clean install from the daily iso.
I don't have any real problems with Quantal 12.10; mine suspends and awakes just fine.

I just got a bunch of updates and rebooted. It's still the same. I can tolerate Unity but, when Classic or fallback is available, it should work. Time to do a fresh install.

No question about that, it should indeed work.  As far as my power problem, I didn't get too excited.  I have what may be kind of an oddball mother board.  The USB ports are weird, the BIOS is weird.  12.10 was fine on a 'real' USB flash drive install running on a Thinkpad.  Have you tried MATE yet?  I'd be curious how closely it sticks to the gnome 2 design.

---

### Post by fantab on 2013-03-01
I have installed Cinnamon. And it is working quite well with 13.04. On my desktop though Cinnamon consumes a little more resources (Memory) than Unity. I had earlier tried MATE and it consumes more resources than Cinnamon. IMO between Cinnamon and MATE, Cinnamon is the choice to make.

---

### Post by Cavsfan on 2013-03-02
Currently still trying to get back to where it was... I re-installed Raring over a Lucid install. :-D Which was no big deal as I am just keeping it around until April anyway.
I didn't have a whole lot invested in it. I sure will miss Lucid though - the last of the pure Gnome Ubuntus that you could pretty much do anything with.
Now we have Unity and pursue things like getting gnome back hence gnome classic or now gnome fallback.

My Raring install should still be in the state it was as it is still on sda7. As soon as I get the fstab record(s) cleaned up I should be ready to try again. I have a daily iso from March 1st.

---

### Post by zika on 2013-03-03
I might overlooked sometning but I did not see that anyone mentioned here fallback session from gnome-shell that is all that &#8222;classic&#8220; was and works like a charm... With/without compiz...

---

### Post by Cavsfan on 2013-03-03
Almost have it all back to where it was before the Unity panel started appearing in my Gnome Fallback session.
I downloaded a fresh daily iso today and installed that. It still would not let me install 13.04 with my USB drive connected. It also would not reboot when finished.
I had to press the reset button to get it to reboot.

No matter what I tried I could not get Emerald window decorator installed via these instructions, which have always worked flawlessly in the past on Raring and other installs:
[COLOR=blue]_[http://www.upubuntu.com/2012/06/how-to-install-emerald-from-source-on.html](http://www.upubuntu.com/2012/06/how-to-install-emerald-from-source-on.html)_[/COLOR]

When attempting ```
emerald --replace
``` 
it just says error emerald not found.

However I know this is still early in development and breakage will occur so I am ok with it.
I will mark this thread resolved as the unity panel is gone now after doing a clean install.

Just have to customize the grub menu, which I have done a "couple" of times. :)

---

### Post by Cavsfan on 2013-03-03
Has the way to resolve a thread been changed? In thread tools at the top, mark this thread as resolved is not an option. :shock:

---

### Post by sgage on 2013-03-03
Edit your post, and go to "Advanced". Then look under 'prefixes' and you'll see 'solved' there for you to pick.

---

### Post by Cavsfan on 2013-03-03
> **sgage said:**
> Edit your post, and go to "Advanced". Then look under 'prefixes' and you'll see 'solved' there for you to pick.

Thanks for that info. :) I'll try that.

---

### Post by Cavsfan on 2013-03-03
> **sgage said:**
> Edit your post, and go to "Advanced". Then look under 'prefixes' and you'll see 'solved' there for you to pick.

I finally got it. I had to edit the initial post and mark it there as resolved. I wonder what happens when the first post is so old that you can no longer edit it.
IMO it should be under thread tools where it used to be.

---

### Post by cariboo on 2013-03-03
We've upped the edit limit to 60 days, so for most threads, that shouldn't be a problem.

---

### Post by Cavsfan on 2013-03-03
> **cariboo907 said:**
> We've upped the edit limit to 60 days, so for most threads, that shouldn't be a problem.

Sounds good! Thanks for the update.

---

