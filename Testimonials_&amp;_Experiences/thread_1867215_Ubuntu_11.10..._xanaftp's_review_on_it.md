---
title: "Ubuntu 11.10... xanaftp's review on it"
date: 2011-10-22
forum: Testimonials &amp; Experiences
---

### Post by xanaftp on 2011-10-22
Well pretty much if I could describe Ubuntu 11.10 as one word my word would be:
**DISAPPOINTING**

I was long waiting for this new release of Ubuntu because of all the "cool new features" that people have been talking about, especially in Unity.

Well... here's my review on it:

The upgrade process went pretty well... there were no errors except with postfix which I don't even use, so I removed it.

The new Ubuntu 11.10 worked perfectly on the first boot, then after that it never worked the same again. :( Of course I only had the first boot running for about 10 minutes before I rebooted.

First about Unity... the claims it runs better and smoother. Yes it runs 10% smoother than in 11.04 but that's barely even anything. However the BIG problem with Unity is it's so freaking glitchy and bugged. Menus for windows sometimes do not appear when I move my cursor at the top. Sometimes when I click the X button it closes the wrong window. And it's quite hard to find what I'm looking for, especially in the search feature (which is crap... doesn't help me 75% of the time).

Now about speed. Yes Ubuntu 11.10 does what it claims it does by booting faster... however at what cost? The system itself and the applications run SLOWER now. It takes longer to open programs than in 11.04.

Resources? This is probably the only GOOD thing I have to say about Ubuntu 11.10. It uses less memory than previous versions of Ubuntu. Before, with my radio station running, memory ran from 1.5GB up to 2.6GB. With Ubuntu 11.10, average memory use is between 800MB and 1.2GB.

Stability? HORRID!!! Ubuntu wasn't ready to be released when it was... REALLY was not ready. There are so many problems with Ubuntu 11.10 it's far from funny. First off, a LOT of the programs I used in 11.04 quite well NO LONGER WORK correctly in Ubuntu 11.10 (and these programs are necessities since I run an internet radio station). These applications include (but DEFINITELY NOT limited to) Skype (crashes just after login), QjackCTL (buttons don't work), KMyMoney (crashes every minute), PulseAudio (does not appear in JACK connections anymore when it did in 11.04), VirtualBox (well it doesn't work because of PulseAudio not connecting correctly to JACK), and I'm sure to find plenty more applications that do not work in 11.10.

Looks of Ubuntu? Unity is "eye candy" in my opinion, and nothing more than "eye candy". It's very hard to figure out how to use. What's worse is 11.10 got rid of the old GNOME interface I used up to 11.04 (classic Ubuntu)... and even GNOME shell is not the interface I was used to and liked so much because it ran well.

Multiple Monitor support? Not good. Yes I can still use multiple monitors like I have been using in 10.10 and 11.04... but the session does not operate well on the second monitor. I sometimes don't have anything other than a white screen with an X cursor.

So can I use another session to workaround a lot of problems of Ubuntu? Absolutely not! I tried KDE and the same problems with applications not working exists. KDE by the way also runs slower in 11.10 than in all other versions of Ubuntu since 10.04. Xce I can never use because it's too basic. GNOME shell again is too basic now since they screwed with it just to force their users to use Unity.

OVERALL: Ubuntu 11.10 is a piece of crap in my opinion because it contains so many problems and bugs, and many of the applications I need to use do not work in Ubuntu 11.10. DO NOT UPGRADE if you haven't already, because you'll regret it!

As far as recommending Ubuntu 11.10, obviously, I WOULD **NOT** recommend it at all!

FINAL RATING: :KS:KS (2 out of 5 stars). The reason why it's 2 stars and not 1 is because of the resource improvement. That's the only reason. Everything else went downhill in this version.

**NOW A MESSAGE TO UBUNTU:** I'm expecting a much better 12.04 LTS version in 2012. MAKE IT GOOD AND VERY STABLE! ...or I might switch to Debian or OpenSUSE.

Thank you for reading my review.

---

### Post by rexrino on 2011-10-22
I'm still using Ubuntu 10.04.3 LTS with no problems so far.

---

### Post by xanaftp on 2011-10-22
> **rexrino said:**
> I'm still using Ubuntu 10.04.3 LTS with no problems so far.

Haha you're lucky! 10.04 LTS was probably the best version of Ubuntu I ever used as well. 12.04 better top that since it will be LTS!

...and I think from now on I'll never upgrade to a new version of Ubuntu unless:
*It is a LTS release
*I have to in order to get important updates for programs that I need.

...10.10 was crap as well but not as bad... 11.04 worked pretty well (not as good as 10.04), and then this 11.10 is the worst yet that I've ever used.

---

### Post by ajgreeny on 2011-10-22
So you quite like it then!!  (END OF IRONY).

Have you looked at the gnome 3 version of the classic gnome desktop, which can be set up to mimic the old classic gnome fairly closely.

Here's how to do it, courtesy of **bob-linux-user** in another thread.  [http://ubuntuforums.org/showthread.php?t=1865912](http://ubuntuforums.org/showthread.php?t=1865912)
> 
The Gnome that is available on Ubuntu 11.10 is I find a good alternative to Unity and as far as I can see it looks and feels like classic gnome. The instructions below let you use a panel, get rid of the diabolical overlay scrollbars and put the window controls back at top right.This is what I did:

Install ubuntu 11.10 in normal way
In a terminal type
sudo apt-get install synaptic
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar-0.2-0
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar3-0.2-0
sudo apt-get install gnome-session-fallback
sudo apt-get install gconf-editor
sudo apt-get install gnome-tweak-tool
log out and log back in gnome classic
In a terminal type
gksudo gconf-editor
Browse to apps/metacity/general. Double click on button_layout and gconf-editor and set value to
:minimize,maximize,close
Alt right click on panel at top.
-Set orientation to bottom and size to 36
Alt right click on time and move to extreme right
Alt right click on panel and add
-Main Menu
-Window List
Alt right click on "Applications Places" menu and remove
Alt right click on the "speech bubble" at bottom right and remove
Remove the slim top panel by alt right clicking and deleting
Alt right click on panel and add
-Show desktop icon
On a general area of desktop right click and change the background to what you want ( I chose Jardin Polar)
in a terminal type
sudo apt-get install ubuntustudio-theme
sudo apt-get install ubuntustudio-icon-theme
sudo apt-get install human-theme
sudo gnome-tweak-tool
Set Theme:Icon theme to Ubuntu Studio
Set GTK+ theme to Raleigh
Set window theme to human

---

### Post by xanaftp on 2011-10-22
> **ajgreeny said:**
> So you quite like it then!!  (END OF IRONY).

I liked Ubuntu 10.04 and 11.04. I did/do not like 10.10 and especially this new version 11.10.

I appreciate you trying to give me steps for mimicking the old GNOME... but I'm not going to waste my time because the interface is not my biggest problem. The biggest problem is a lot of my applications that worked on 11.04 no longer work on 11.10. If I can get the applications to work then I can tolerate Unity... or KDE which is what I'm using now since I don't like Unity that much. But again as mentioned with KDE even, the same applications that don't work on Unity also do not work on KDE and all of those used to work on 11.04 and before.

---

### Post by kurt18947 on 2011-10-22
I wonder if part of your problem is that your GTK2 programs don't work well on GTK3? If so, Ubuntu has little control over that, I think. Isn't Linux Mint going to stick with Gnome 2 for a while yet?

---

### Post by xanaftp on 2011-10-22
> **kurt18947 said:**
> I wonder if part of your problem is that your GTK2 programs don't work well on GTK3? If so, Ubuntu has little control over that, I think. Isn't Linux Mint going to stick with Gnome 2 for a while yet?

That's what I heard... that Linux Mint will. Maybe that's the problem... with regards of the old version of GNOME. Thing is though I thought qjackctl was not a GNOME application but a QT application? And that's one program that no longer works in 11.10.

---

### Post by xanaftp on 2011-10-22
Okay I have fixed a couple of the programs from the list of programs listed above I reported as not working.

Skype - Works now. I think simply changing from Unity to KDE fixed this.

PulseAudio - I forgot to load the correct modules for it to connect to JACK. It now does that.

VirtualBox - Since Pulseaudio now works, Virtualbox does as well.

All other programs mentioned above in my first post still do not work.

If I can continue fixing things and just using KDE instead of Unity, I should be able to adapt to 11.10 without too much trouble.

---

### Post by craig10x on 2011-10-23
> **kurt18947 said:**
> I wonder if part of your problem is that your GTK2 programs don't work well on GTK3? If so, Ubuntu has little control over that, I think. Isn't Linux Mint going to stick with Gnome 2 for a while yet?

From the last response from Clem (the head of mint) to a poster in one of his blog announcements at their site, it appears that Clem is working on applying extensions that are now available in Gnome 3.2 that allow a developer to customize the desktop environment...

If it works out well, Mint 12 should have Gnome 3.2 underneath with the classic linux mint desktop on top if it...which is the best of both worlds...and will give a lot of you who are disenchanted with unity and gnome shell a great alternative :)

---

### Post by 3rdalbum on 2011-10-23
> **xanaftp said:**
> 
**NOW A MESSAGE TO UBUNTU:** I'm expecting a much better 12.04 LTS version in 2012. MAKE IT GOOD AND VERY STABLE!

This is partly up to you, you know.

Developers and beta-testers do what they can to ensure that things are reasonably free of bugs, but there are some bugs that they simply don't run into. You've obviously run into several. If you'd reported them and given instructions on how to reproduce the bugs before release, they may well have been fixed before the release date.

A couple of my bugs were fixed, now I'm having a pretty good time on Unity. By the way, Unity is not hard to use, although I'd agree that the search doesn't always find what you're looking for. Even your reported 75% failure rate is still better than any Linux search engine that came before, sadly, although I have more success with Unity than you do.

So yeah, when 12.04 hits Alpha 3, you should definitely download it and test it to its fullest. Everyone should, if they can.

---

### Post by nethero on 2011-10-24
> **3rdalbum said:**
> So yeah, when 12.04 hits Alpha 3, you should definitely download it and test it to its fullest. Everyone should, if they can.

I've been using Ubuntu for a while and I'm ashamed to say I've never tested an alpha build.  Where can I download this?

---

### Post by FormatSeize on 2011-10-24
> **xanaftp said:**
> Stability? HORRID!!! Ubuntu wasn't ready to be released when it was... REALLY was not ready.
The developers are well aware of this, and they knowingly release things that they know are not finished products to meet deadlines.

---

### Post by PaulInBHC on 2011-10-25
> **nethero said:**
> I've been using Ubuntu for a while and I'm ashamed to say I've never tested an alpha build.  Where can I download this?

December 1st is the scheduled date. Browse this forum

[http://ubuntuforums.org/forumdisplay.php?f=412](http://ubuntuforums.org/forumdisplay.php?f=412)

---

### Post by kurt18947 on 2011-10-26
> **3rdalbum said:**
> 
<snip>
So yeah, when 12.04 hits Alpha 3, you should definitely download it and test it to its fullest. Everyone should, if they can.

+1.  Needless to say don't make alpha or beta releases your "this has got to work" O.S. Apport worked pretty well in 11.10 and launchpad.net and I were quite familiar :)  I see this as partial payment for a no-$$ quite good operating system. Installing an Ubuntu operating system only requires about 8-10GB of disk space if you don't store a lot of data in the partition -- which would be a bad idea because you may reinstall a few times.

---

