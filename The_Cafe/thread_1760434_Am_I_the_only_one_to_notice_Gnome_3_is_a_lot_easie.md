---
title: "Am I the only one to notice Gnome 3 is a lot easier on resources than Gnome 2?"
date: 2011-05-16
forum: The Cafe
---

### Post by murderslastcrow on 2011-05-16
For me, Gnome 3 has performed exceptionally well. Aside from Gnome Shell being responsive in general, I don't seem to peak at 400-500 MB like I used to in Gnome 2 with Compiz. I'm not sure if this is normal for Gnome 2 without compositing, but I think it's great that Gnome is following a tradition of using less resources and optimizing more as time goes on. I hope to see these resources drop even lower as more applications take advantage of GTK 3 and they refine the GNOME libraries over the next couple years.

Anyone else noticed how light Gnome 3 is on resources? The picture below shows my desktop in Activities view with a few other desktops populated with programs.

---

### Post by wojox on 2011-05-16
I don't measure RAM that much but Mutter is suppose to be a little less intensive.

---

### Post by user1397 on 2011-05-16
wow all of that and only 300mb?  i've got to give gnome 3 and gnome shell another shot now...

---

### Post by screaminj3sus on 2011-05-16
Resource usage seems pretty unchanged to me, but responsiveness wise gnome shell seems much more responsive than gnome 2 with compiz and unity. I am impressed so far, gnome 3 is very slick.

---

### Post by NightwishFan on 2011-05-16
Debian Sid with Gnome 3 fallback mode uses 60-80mb for me.

---

### Post by murderslastcrow on 2011-05-17
> Debian Sid with Gnome 3 fallback mode uses 60-80mb for me.

I noticed similarly low memory use. If I remember correctly, I was using Xfce just before switching to Gnome 3 on a computer that couldn't support the Shell the first time I tried it, and I noticed a marked increase in speed. They really have fixed a lot of issues in GTK 3, and it shows beautifully there. I think the Fallback is a pretty good step up from WMs, although e17 is kind of the kind of being light and looking good without compositing.

Still, it just makes KDE 4 (although I love it to pieces, and despite the efficiency improvements lately) much more obviously not-as-light. Then again, KDE 4 is lighter than OS X's latest Aqua releases, so I guess it's not such a bad thing.

---

### Post by Hydrael on 2011-05-17
Strange...I was just scanning through the web to find out if anyone else has problems with gnome-shell eating up memory like crazy -- currently 2.3GB on my system.

Then I've seen this thread and wonder where I could've messed up?

I'm running Ubuntu 11.04 and installed gnome3  following these steps:
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get install gnome-shell[COLOR=Black][COLOR=#008080][/COLOR][COLOR=#008080][/COLOR][/COLOR]

---

### Post by uRock on 2011-05-17
Unity uses all of 50-60MB RAM on my 64bit machine.

---

### Post by murderslastcrow on 2011-05-17
The shell, by itself, only uses about 30 MB tops, unless you're using the integrated messaging, in which case it goes up a bit. The single process for any single element of the GUI doesn't really tell you much, since Clutter/Mutter is part of the mix, and so it compiz for Unity. So I'm not sure if that's generally an issue.

Also, I'm using Arch, but I got similar results on Fedora. Even with the PPAs, there are some packages and services for Ubuntu and default configurations that don't mesh very well with Gnome-Shell. **Also, if you've installed Orca, but no voice files, it may react poorly** (I had Orca installed and it ended up chomping up a bit more RAM, but a lot more CPU, so uninstalling Orca is probably a good first thing to try if you don't need it).

But yeah, I top out at 300 MB. If I'm just running a browser, music player, and chat I usually only hit about 220 max. Depends on which types of software you use, though- Firefox will usually get you over 300 MB of RAM, regardless (although it's by no means a 'heavy' browser, like say Opera or IE).

---

### Post by RoflHaxBbq on 2011-05-17
Gnome 2 only uses 90MB RAM on my dinosaur of a computer.

Gnome 3 does look nice an slick though, I would like to try it.

---

### Post by murderslastcrow on 2011-05-17
It'd be interesting to see matchboxwm, e17, Gnome3, or KDE Mobile on actual smartphone hardware, but the N900 is probably the only phone really friendly for Xorg in the first place. Gnome 3 could really adapt well to that kind of device, especially considering the padding on windows and the such (many mobile users might hate the idea of windows, of course).

It certainly seems Gnome 3 could run okay on a lot of the newer smartphones if it keeps it up with the lightness. Gnome and GTK have a much brighter future ahead, I think. I was really scared they might just drown under all the pressure from Qt 4 and soon 5, and all the new stuff optimized for handheld devices. Just imagine GIMP on a tablet- that's my dream. XD

---

### Post by Dustin2128 on 2011-05-17
I noted similarly low usage testing out Gnome 3 final the other day, it's quite impressive- course I usually use xfce.

---

### Post by cbowman57 on 2011-05-17
> **Hydrael said:**
> Strange...I was just scanning through the web to find out if anyone else has problems with gnome-shell eating up memory like crazy -- currently 2.3GB on my system.

Then I've seen this thread and wonder where I could've messed up?

I'm running Ubuntu 11.04 and installed gnome3  following these steps:
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get install gnome-shell[COLOR=Black][COLOR=#008080][/COLOR][COLOR=#008080][/COLOR][/COLOR]

Let me guess, 64-bit?  Mine was having problems with a huge memory leak the other day, the 32-bit seemed stable.  It may be fixed now, haven't noticed it for a couple days.  In the interim I put a launcher in favorites to run **gnome-shell --replace** when things got sluggish.

---

### Post by SynonM on 2011-05-17
> **cbowman57 said:**
> Let me guess, 64-bit?  Mine was having problems with a huge memory leak the other day, the 32-bit seemed stable.  It may be fixed now, haven't noticed it for a couple days.  In the interim I put a launcher in favorites to run **gnome-shell --replace** when things got sluggish.

speaking of 64-bit ... is it worth it cbowman57 ?

---

### Post by cbowman57 on 2011-05-18
> **SynonM said:**
> speaking of 64-bit ... is it worth it cbowman57 ?

Very good question. I've run mostly 64-bit distros for over a year but every time I would do a 32-bit installation to play with it seemed faster, lighter but I just wrote it off thinking it was just an fresh uncluttered system.  Since I moved to G3 shell I really noticed the difference and made my mind up to go with 32-bit. My motherboard can handle 8GB RAM, I only have 2 and really don't do anything that would require I have more than 4.

Other people might have had a different experience, it's not something I've seen anyone really mention in the forums.

As always, YMMV. :)

---

### Post by SynonM on 2011-05-18
> **cbowman57 said:**
> Very good question. I've run mostly 64-bit distros for over a year but every time I would do a 32-bit installation to play with it seemed faster, lighter but I just wrote it off thinking it was just an fresh uncluttered system.  Since I moved to G3 shell I really noticed the difference and made my mind up to go with 32-bit. My motherboard can handle 8GB RAM, I only have 2 and really don't do anything that would require I have more than 4.

Other people might have had a different experience, it's not something I've seen anyone really mention in the forums.

As always, YMMV. :)

thanks a million

saves me the troubles
:popcorn:
maybe 64-bit in a few years and a new computer 
(after the 64-bit turnover) 
or
maybe once people really start talking 128-bit :P

---

### Post by Hydrael on 2011-05-18
> **cbowman57 said:**
> Let me guess, 64-bit?  Mine was having problems with a huge memory leak the other day, the 32-bit seemed stable.  It may be fixed now, haven't noticed it for a couple days.  In the interim I put a launcher in favorites to run **gnome-shell --replace** when things got sluggish.

Yes, 64-bit.
But I simply forgot to do the dist upgrade.
After doing that the memory usage stabilized itself and is now also <200MB.

---

### Post by sostentado on 2011-05-18
Count me in

---

### Post by Hydrael on 2011-05-20
> **Hydrael said:**
> Yes, 64-bit.
But I simply forgot to do the dist upgrade.
After doing that the memory usage stabilized itself and is now also <200MB.

Ok, have to revert that.
Yesterday gnome-shell ate 5.4gb of ram

---

