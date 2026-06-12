---
title: "KPackageKit needs to go!"
date: 2009-08-13
forum: The Cafe
---

### Post by Ranax on 2009-08-13
I am so fed up with it. Something always breaks it. The latest mistake I make was trying to install VirtualBox. It couldn't install it as Python 2.5 was not installed. So I go to KPackageKit to install, and what do you know it's broken and I have to use the CLI to remove the broken VirtualBox install, even though it said it hadn't been installed! I've lost count of the amount of times KPackageKit has broken on me, be it installing a DEB that goes wrong or a bug in KPackageKit itself. The Java install bug is still there after about 6 months of being reported! It's ridiculous and along with the lack of a decent native KDE browser means that it quickly becomes a chore to use!

---

### Post by Skripka on 2009-08-13
I had heard rumours of KPackageKit getting better...

Last I used it 6 months ago--it was even worse than the tool (Adept) it was replacing, as much as like dividing by zero that may seem.  Couldn't even find packages installed on my box.

All the *Kit tools are annoyances IMHO.  They end up making things far more complex than they need be.  There's a useful thread in the Arch forums that is frequently cited for help purposes that is entitled "I won the battle against PolicyKit/HAL!"

---

### Post by reyfer on 2009-08-13
I tried, I really tried, to use kpackagekit.....but I always go back to install packages, upgrades and uninstalling packages through Synaptic.

---

### Post by Cenotaph on 2009-08-13
I agree, Synaptic is so much better. I know they don't like to use GTK based tools in Kubuntu, but well, it is much better and it already exists.

PCLinuxOS uses it and it's KDE based.

---

### Post by Changturkey on 2009-08-13
You'd think someone would've made a carbon copy of Synaptic already, but in Qt instead of GTK.

---

### Post by Arup on 2009-08-13
One of the reasons I stick to Gnome and synaptic, its the easiest and most friendliest instalation manager.

---

### Post by Slug71 on 2009-08-13
Kpackagekit in Karmic should be much better.

---

### Post by starcraft.man on 2009-08-13
I haven't been bothered by it so far. To be honest though, I do 95% of all my installation and package management a terminal. I guess that makes me neutral on the vote so I'll abstain.

---

### Post by Ranax on 2009-08-13
> **Changturkey said:**
> You'd think someone would've made a carbon copy of Synaptic already, but in Qt instead of GTK.

I have wondered about that as well! :lolflag:

> **Slug71 said:**
> Kpackagekit in Karmic should be much better.

I hope so!

---

### Post by swoll1980 on 2009-08-13
I don't think they need to get rid of it. They just need to fix it.

---

### Post by Firestem4 on 2009-08-13
> **starcraft.man said:**
> I haven't been bothered by it so far. To be honest though, I do 95% of all my installation and package management a terminal. I guess that makes me neutral on the vote so I'll abstain.

I only ever use KPackageKit for browsing these days. Its less tedius than apt-cache show/search in the command line (for lots of packages at once)

Otherwise I do all of that through apt. While I don't have anything to really dislike about kpackagekit, i've never had the problems other people seem to.

If its that big of a problem though you can use synaptic (apt-get install synaptic) problem solved.

---

### Post by DeadSuperHero on 2009-08-14
I've really enjoyed it in the Karmic builds so far.

---

### Post by Screwdriver0815 on 2009-08-14
I also used to hate it. But with the latest updates it got better. And I don't hate it anymore, I just have a slight distrust against it.

Now it crashes less often and also the search tool got better.

Still it is not as good as Synaptic. I am sure that the developers will fix it. So it has not to go, it just has to be fixed.

---

### Post by praveesh on 2009-08-14
Start a new thread in the brainstorms

---

### Post by konqui on 2009-08-14
I'm testing Karmic and kpackagekit is quite good. However I agree that it was terrible in Jaunty. Adept 2 beta was better than it!

---

### Post by RiceMonster on 2009-08-14
I have gnome-packagekit on Fedora and it's alright. There's some areas it can improve upon, but it looks promising. I really don't know how different it is to kpackagekit though.

That said, I don't really use GUI packagemanagers. I prefer to use plain apt, yum, pacman, etc on the command line.

---

### Post by Ranax on 2009-08-14
> **konqui said:**
> I'm testing Karmic and kpackagekit is quite good. However I agree that it was terrible in Jaunty. Adept 2 beta was better than it!

That is great to hear! :D

---

### Post by Xbehave on 2009-08-14
KPackageKit is pretty nice in Fedora11, while i gave up on GUI management (yum/apt ftw) completely because adept sucked so hard, i don't mind kpackagekit occasionally popping up in my system tray and installing updates. I assume the problem with KPackageKit is the interaction with apt/dpkg isn't as mature as with yum/rpm. 

My only beef is that it is a constantly running deamon when it could just use anacronjobs!

---

### Post by madjr on 2009-08-14
new alpha 4

[https://wiki.ubuntu.com/KarmicKoala/Alpha4/Kubuntu](https://wiki.ubuntu.com/KarmicKoala/Alpha4/Kubuntu)

you can try new builds and see

[IMG]https://wiki.ubuntu.com/KarmicKoala/Alpha4/Kubuntu?action=AttachFile&do=get&target=kpackagekit2.png[/IMG]

---

### Post by SuperSonic4 on 2009-08-14
> **Skripka said:**
> I had heard rumours of KPackageKit getting better...

Last I used it 6 months ago--it was even worse than the tool (Adept) it was replacing, as much as like dividing by zero that may seem.  Couldn't even find packages installed on my box.

All the *Kit tools are annoyances IMHO.  They end up making things far more complex than they need be.  There's a useful thread in the Arch forums that is frequently cited for help purposes that is entitled "I won the battle against PolicyKit/HAL!"

I had to bookmark that thread so PolicyKit.conf would play nice with mounting devices

I didn't really get used to KPackageKit before moving on but it wasn't that good to be honest, it seemed random whether or not it would work. I think something like Shaman would be excellent (but uses apt instead of pacman)

---

### Post by bailout on 2009-08-14
> **Changturkey said:**
> You'd think someone would've made a carbon copy of Synaptic already, but in Qt instead of GTK.

They started doing that some years ago. It was called kynaptic but development stopped before it fully matched synaptic. Then they put a lot of time developing adept from scratch but development seemed to stop before it was finished. They have now started all over again with kpackagekit :(

I have now switched to gnome but I can't see why people like synaptic so much tbh. I found adept before the switch to kde4 much easier to use. The search in synaptic is very poor.

---

### Post by buzzmandt on 2009-08-17
> **Slug71 said:**
> Kpackagekit in Karmic should be much better.

kpackagekit in karmic isn't better, IMHO it sucks.  if you try to install something that has dependencies that need to be removed it will tell you one of them, even if there are many.  It won't offer to remove them and install what you wanted like synaptic does.    I run synaptic and gnome-app-install from kde (kubuntu) because it works so much better.  at this point i think anything would be better than kpackagekit

---

### Post by Screwdriver0815 on 2009-08-17
> **buzzmandt said:**
> kpackagekit in karmic isn't better, IMHO it sucks.  if you try to install something that has dependencies that need to be removed it will tell you one of them, even if there are many.  It won't offer to remove them and install what you wanted like synaptic does.    I run synaptic and gnome-app-install from kde (kubuntu) because it works so much better.  at this point i think anything would be better than kpackagekit

I don't understand why people bloat their computers with different package managers...

even when KPackageKit sucks in your opinion: why don't you use the terminal and apt-get?
Is it so difficult to type some commands? :confused:

---

### Post by ssri on 2009-08-18
> **Screwdriver0815 said:**
> I don't understand why people bloat their computers with different package managers...

even when KPackageKit sucks in your opinion: why don't you use the terminal and apt-get?
Is it so difficult to type some commands? :confused:

Maybe some people like to control and manage their packages through gui?  As for myself, I think using apt and "aptitude search <packagename?> | grep <>" is all I need to manage my kubuntu install.  I can query a hell of a lot more information regarding package policies, dependencies and control which packages I want to have on my system through the terminal quickly and easily.  I guess it is different folks, different strokes.

---

### Post by shockdiode on 2009-10-02
I've given kpackage kit a fair shake for awhile now and it simply continues to suck. No big deal for me personally as I'll just stick with the command line utilities when there are updates but I really think the lack of functionality and all above issues that people have mentioned are going to turn off users. 

I think many users want a nice, easy to use gui package manager that works well and kpackagekit is not it.

---

### Post by praveesh on 2009-10-02
> **Screwdriver0815 said:**
> I don't understand why people bloat their computers with different package managers...

even when KPackageKit sucks in your opinion: why don't you use the terminal and apt-get?
Is it so difficult to type some commands? :confused:

not everyone is faster in typing. More over , the letters associated with the options need to be remembered. And some time need to be spent initially  for learning

---

### Post by Slug71 on 2009-10-02
> **shockdiode said:**
> I've given kpackage kit a fair shake for awhile now and it simply continues to suck. No big deal for me personally as I'll just stick with the command line utilities when there are updates but I really think the lack of functionality and all above issues that people have mentioned are going to turn off users. 

I think many users want a nice, easy to use gui package manager that works well and kpackagekit is not it.

The problem is debconf and conf file integration in Packagekit. This is currently being worked on. Once this is done,expect a huge improvement.
Packagekit will likely become the backend to Ubuntu Software Center too which could well mean that USC might be ported to Kubuntu too.

Please see this thread regarding debconf and PK:

[http://ubuntuforums.org/showthread.php?t=1268447](http://ubuntuforums.org/showthread.php?t=1268447)

---

### Post by gregconquest on 2010-04-01
I'm trying to use KPackageKit now under kubuntu netbook beta 1 (lucid 10.04) and I just don't understand the basic interface!

When I search, I see a list of programs sorted how I don't know and which one is basic I don't know. Then I select one and I get more info though no option to install or uninstall it. I right-mouse click on it and it just collapses. Double-click does the same thing. No mouse action appears to be able to select a package for installation. 

Then on the right in the "Acton" column I have down arrows or X's. What do they mean? I click one of the arrows and it changes from dark gray to light gray. Aha! Finally I get it! . . . . . . .  No I don't. Changing an arrow from one shade of gray to another doesn't mean anything! Why didn't someone put a f*cking legend somewhere?

I just tried to install Thunderbird, and now there is an X where there used to be a down arrow. Uh, I deleted it? This is retarded (my apologies to people with mental mental disabilities; I'm not talking about you.) I have no way of telling from this interface what I just did.

The "Help" button is grayed out, so KPackageKit itself doesn't help me to understand WTF is going on. I search online and there is no immediate page telling me the basics of how to use it. This page is one of the top pages for:
kpackagekit faq

Searching for other keywords gets me no better.

What kind of idiot designs a basic GUI application and doesn't make it apparent how to use it?

Greg

---

