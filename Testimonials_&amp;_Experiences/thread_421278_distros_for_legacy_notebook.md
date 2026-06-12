---
title: "distros for legacy notebook"
date: 2007-04-24
forum: Testimonials &amp; Experiences
---

### Post by jarviw on 2007-04-24
So I distro-upgraded my old Sony Vaio P3 notebook to Feisty yesterday.  It works.

But again, the issue with display I had since the upgrade to Edgy is still there... and perhaps the most annoying, ever since Edgy, it has only been running slower and slower.
It's really annoying!  Dapper was the last ubuntu that runs fast on this P3-1000/512MB machine.  and I have no idea what's going on.  I did all these tricks I can find over here to make it run faster, but I think I am giving up ubuntu on this machine.

Does anyone have good recommendations as which distro to use on such a legacy notebook?

I want to use GNOME or KDE... (Xfce just doesn't fulfill my needs... and running Xubuntu ended up running GNOME anyways)  we use this computer primarily for web browsing and sometimes movies... and also as the print server  (75 Watt server, that's why I like notebooks).

any ideas are appreciated!

---

### Post by dannyboy79 on 2007-04-24
Gnome or KDE is whats killing the performance so when you say you want a distro for old hardware you can't say that you want to use Gnome and KDE. I myself love Xubuntu otherwise my second small distro is Puppy Linux and then Damn Small Linux. Gnome and KDE have so many libraries and dependcies, that's what's slowing your machine to a crawl. 

What don't you like about Xubuntu and I can maybe point out some solutions. If you only use your laptop for browsing and whatnot, than how can Xubuntu not be good enough?

---

### Post by jarviw on 2007-04-24
I know... It's the fancy desktop environment that's slowing everything down.

The reason I have it running GNOME is because of its usability. While I rather like Xfce, other people in the house don't... it's the interface.  
And the truth is, there's still xubuntu installed on this machine, but it doesn't really run much faster.

Puppy and DSL come with too little packages... we do occasionally need to run OpenOffice and other big things.

.......

I think I read it somewhere (over DistroWatch?) once that there's this distro running KDE with excellent performance on legacy hardware... but I can't seem to remember what it was.  something Slackware based perhaps?

---

### Post by dannyboy79 on 2007-04-24
that would probably be kanotix or knoppix. what's wrong with installing openoffice in xubuntu? if they don't like the interface, than change it so they do, everything is just as modifiable in xfce as gnome. it's just not as easy!

---

### Post by Sunflower1970 on 2007-04-24
What might work is just installing a lighter windows manager over Gnome like IceWM, or E17? It'll keep all the same programs as Ubuntu, but just make things a bit faster. IceWM is highly configurable. I was able to configure the taskbar and menu similar to how it's set up under Gnome (although it only has one taskbar not two)

---

### Post by voided3 on 2007-04-24
Try out the latest release of Puppy Linux, which I believe is 2.15CE. I tried it on a 700mhz Celeron micro ATX comp with 384mb of memory and it was blindingly fast; it took no longer than one second for just about any program to open, plus my d-link wifi card worked out of the box. The newest version even has flash and different themes pre-installed, plus if I remember correctly it does have Open Office in the repos. You said you have tried Xubuntu already, but was it 7.04 or 6.10? The latest xfce 4.4 is really nice in my opinion; in fact, I use it instead of gnome now on all of my comps. It can be configured to be very simple, or you can have fancy window transparency and shadowing. Try out Fluxbuntu and Damn Small Linux as well; they run really light thanks to their fluxbox WM, but the GUI takes some getting used to if you are used to gnome. As another poster said, Knoppix or Gnoppix also are good options. A big factor in speed also is what graphics driver you have installed. For example, I have a Radeon 9250 in one of my computers and I noticed that it's desktop performance went way down since I can't get an ATI proproetary driver for Xorg 7.2 where before it was quite swift (and could play UT2k4 on full settings at 1024x768... sigh, it's nvidia or nothing from now on). Anyway, good luck!

---

### Post by j0e_x on 2007-04-24
Hello,
 i'm using Xubuntu Edgy on a Toshiba Satellite 12057 (iirc). 512 megs of RAM, 32 meg Intel graphics and 40 gig HD. Runs great. I have the desktop setup so it looks a lot like regular Ubuntu.
 Still, that being said, I find the one distro that seems to work when others lie down and die to be PUPPY Linux. Everyone seems to love it, especially first timers. It's not my fave distro but I'd give it a shot. Seems to support lots of hardware, and pretty easy to set up. Also, what it does not come with is easily obtained. I have Puppy w/Open Office, BG2 theme and some games all on my USB stick. Good luck!

---

### Post by ThinkBuntu on 2007-04-24
Try out Zenwalk. Quick slackware-based distro that's very good for older machines. And the look isn't so shabby either, so maybe everyone else there can live with it.

---

### Post by phidia on 2007-04-24
> **ThinkBuntu said:**
> Try out Zenwalk. Quick slackware-based distro that's very good for older machines. And the look isn't so shabby either, so maybe everyone else there can live with it.

I'm going to cast my "vote" with ThinkBuntu. The latest release of zenwalk (4.4.1) is light and fast.
I believe it also has the gnome libs too-I think a livecd of zenwalk was released recently too.

[http://distrowatch.com/table.php?distribution=zenwalk](http://distrowatch.com/table.php?distribution=zenwalk)

---

### Post by tiffanyjewelry on 2008-10-21
i don't think that's a easy question,but you can get help from others.Good luck!

---

### Post by snowpine on 2008-10-21
I've spent the last few days playing around with Debian Etch (the current stable release). It is a Gnome desktop but is much lighter than Ubuntu. Might be perfect for you. Good luck!

---

### Post by armandh on 2008-10-21
I've no trouble with 8.04 [now re installed 8.10] on a 933 P-III 512 meg ram 128 meg video.

it is now being used as a media box next to the family room HD TV
fed by a DVI/HDMI adaptor plug

try a fresh install rather than upgrade

PS see next
I have puppy on a 733 P-III 256 meg ram on board vid
works well.

---

### Post by wolfen69 on 2008-10-21
Puppy Linux all the way!

---

### Post by EnergyRecruit on 2008-11-16
Hi Bernard,

I've looked into the Ubuntu / AMD 64 issue a bit more closely, and discovered
the cause of the problem and a workaround. I have updated the bug here:
[http://bugs.activestate.com/show_bug.cgi?id=38886](http://bugs.activestate.com/show_bug.cgi?id=38886)
Basically, try symlinking pango-basic-fc.so to where pango is looking for it:
sudo ln -sf /usr/lib32/pango/1.4.0/modules/pango-basic-fc.so
/usr/lib/pango/1.4.0/modules/pango-basic-fc.so
Let me know if you have any further questions or comments.**[B][SIZE="3"][/SIZE]**[/B]
best regards,

---

### Post by fluxlizard on 2008-11-17
I'm running pclinuxos gnome edition on my old thinkpad (p3 700mhz with 256 mb ram and 4mb(!) video card).

It runs just fine.

Before I upgraded my ram I only had 192 mb and I ran pcfluxboxos and stuck a menu bar (wbar I think it was) and a mac style icon launch bar on it and it ran all the latest softwares (like firefox, gimp, open office) really quickly. With the extra memory (256 now) I decided I like the feel of gnome, and performance has been hit only a little.

---

### Post by mikjp on 2008-12-15
At the moment my favourite distro for my P1000 / 256 Mb is Vector Linux. Now that Slackware 12.2 is just released I might change the distribution soon...

mikko

---

### Post by fluxlizard on 2008-12-15
pclinuxos gnome edition will run great on there.
You won't have to sacrifice gnome interface, thousands of apps in synaptic, etc. It runs fine on my p3 700 mhz laptop with 256 mb ram and 4mb video card (yep it's really only 4mb).

---

