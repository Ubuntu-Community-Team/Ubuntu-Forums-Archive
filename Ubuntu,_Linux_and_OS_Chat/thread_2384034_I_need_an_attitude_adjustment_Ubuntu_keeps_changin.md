---
title: "I need an attitude adjustment: Ubuntu keeps changing versions."
date: 2018-02-01
forum: Ubuntu, Linux and OS Chat
---

### Post by seekertom on 2018-02-01
I've used winstuff for many years, understand upgrades, new versions etc. Have been using Ubuntu since ver 14, then used 16, then 17.01, now up to 17.10.1 (?). I understand we need updates for bugs, security issues, new features etc, but I'm stumbling over changes to what I see on my screen, changes to where I click to do things, and having to run the learning curve all over again. Not to mention the pretty wallpapers that I lose with each change.

I was really hoping Linux would not follow in the footsteps of MS and others, who seemingly make change to the os for no reason other than just because some programmer wants to show off with massive changes.

I learned a bit on 14, and liked its appearance. Same with 16, and 17.01. Now 17.10.1 is again different in how I do things, but whats worse, I'm told I Have to upgrade.

I know I'm being naieve or maybe even whiney, or whatever. I know there are different desktops, but have not yet discovered how to get things looking one way, and keeping it like that even tho versions change.

So, my friends and Ubie-lovers, please pat me on the haid, tell me everythings gonna be ok in the morning, and maybe toss in some usable advice to keep me happy while dealing with the changing color of the leaves. sotospeak.
thanks, seekertom  :( :popcorn:

Double thanks to all repliers. Some very interesting and usable info imparted here. Again, I thank y'all.

---

### Post by dragonfly41 on 2018-02-01
> [COLOR=#000000]but have not yet discovered how to get things looking one way, and keeping it like that even tho versions change.
[/COLOR]
Since 12.04 I have been using gnome-flashback to maintain consistency of Desktop look and feel.
I have it on 16.04 and I understand that it can be used in 17.10.

[https://ubuntuforums.org/showthread.php?t=2378472](https://ubuntuforums.org/showthread.php?t=2378472)

---

### Post by wildmanne39 on 2018-02-01
*Thread moved to **Ubuntu, Linux and OS Chat, a more appropriate forum**.*

---

### Post by cruzer001 on 2018-02-01
If you dislike all  the changes, maybe you should stick with LTS releases (14.04; 16.04; in April 18.04).  An LTS release comes out every two years, but is supported for 5 years.  So if you want, you can upgrade every two years or keep it for the next after release (that would be 4 years away) with a maximum life of 5 years total.  

All other releases are supported for 9 months only and should be changed when the next release comes out (every 6 months).

So I would suggest to get accustom with 17.10 and wait for the next LTS release in April.  It will be built like 17.10 and will be powered by Xorg which you can/should switch to now.  In your boot (grub) menu>advance options.

And your good to go :)

---

### Post by mörgæs on 2018-02-01
New releases are mostly important for people with new hardware. If your gear is old or semi-old it will be enough to do a fresh install with four years in between:

[https://en.wikipedia.org/wiki/Ubuntu_version_history#Version_timeline](https://en.wikipedia.org/wiki/Ubuntu_version_history#Version_timeline)

That way you don't have to adapt to a new look and feel so often.


(I consider myself ninja'ed)

---

### Post by kansasnoob on 2018-02-01
> **cruzer001 said:**
> If you dislike all  the changes, maybe you should stick with LTS releases (14.04; 16.04; in April 18.04).  An LTS release comes out every two years, but is supported for 5 years.  So if you want, you can upgrade every two years or keep it for the next after release (that would be 4 years away) with a maximum life of 5 years total.  

All other releases are supported for 9 months only and should be changed when the next release comes out (every 6 months).

So I would suggest to get accustom with 17.10 and wait for the next LTS release in April.  It will be built like 17.10 and will be powered by Xorg which you can/should switch to now.  In your boot (grub) menu>advance options.

And your good to go :)

+1! Stick with the LTS releases for production machines.

I maintain over 60 computers and I've only recently begun upgrading some of them from 14.04 (Trusty) to 16.04 (Xenial). I probably would have waited even longer but I was "upgrading" hardware anyway so it just made sense. In my case "upgrading" involved resurrecting 7 to 9 year old hardware - the higher end stuff I couldn't afford when it was new. 

Furthermore it's wise to stick with the first point release (eg; 14.04.1, 16.04.1, 18.04.1, etc) of each LTS to avoid HWE EOL. The only exception is newer hardware that requires the absolute latest versions of software to operate. I do enjoy testing the interim releases but with only a 9 month support cycle it just doesn't make sense to run them on production machines.

Of course new "exceptions" crop up from time to time. With Ubuntu's change from Unity to GNOME Shell I'd likely install 17.10 if I were planning to keep running the default GNOME desktop but recent changes in upstream GNOME are pushing me towards alternatives. The tough part is deciding on an alternative because there are so many great ones to choose from.

---

### Post by mastablasta on 2018-02-02
> **seekertom said:**
> 
I was really hoping Linux would not follow in the footsteps of MS and others, who seemingly make change to the os for no reason other than just because some programmer wants to show off with massive changes.


it is connected with OS strategy, not programmer showing off.

with 12.04 the Unity interface (you got to know in 14.04) was meant as a unified interface that works as well on PC, TV or small screen such as mobile phone. The idea was there would be a Ubuntu phone which you could plug into a dock and then use as a PC (convergence). the phone project failed. then it no longer made sense to develop specific desktop for Ubuntu. The cutbacks were made, so the Ubuntu only desktop (Unity) got axed and replaced by default Gnome 3. So now just like in th eold days Gnome developers are the ones developing the default desktop.

if you used KDE (Kubuntu) over these same years you would see smaller changes. If you chose LXDE (Lubuntu), XFCE (Xubuntu) or Mate (old Gnome2 interface) the changes are even less radical.

> [COLOR=#000000]Not to mention the pretty wallpapers that I lose with each change.[/COLOR]
wallpapers are not really connected with OS. they are just pictures.

wallpapers from old versions are still available on internet in various packages and places.

i use same wallpapers on Linux and windows machines.

---

