---
title: "How to install Kubuntu?"
date: 2005-03-09
forum: The Cafe
---

### Post by CowPie on 2005-03-09
I've heard a lot of news about this release, but the wiki doesn't have info on installing...has anyone done it?

---

### Post by neom on 2005-03-09
[http://wiki.ubuntu.com/InstallingKDE](http://wiki.ubuntu.com/InstallingKDE) is the best place for information on install. 

Instead of going though any hassle though, personally I just found kubuntu in the package manager and installed it from there. Worked well and seems very stable.

You can get the updated live & install ISOs at [http://cdimage.ubuntu.com/kubuntu/](http://cdimage.ubuntu.com/kubuntu/)

---

### Post by CowPie on 2005-03-14
Hi neon, I tried doing "apt-get install kubuntu" but nothing happens...

---

### Post by CowPie on 2005-03-14
[QUOTE=CowPie]Hi neon, I tried doing "apt-get install kubuntu" but nothing happens...[/QUOTE]
 Oh I see, it's apt-get install kubuntu-desktop.  Thank you for the link as welL!!

---

### Post by wbeck85 on 2005-03-16
Oh my goodness, Alright, so, i tried to install kubuntu-desktop via synaptic. It just finished, after waiting 2 hours. It only took about 3 minutes to dl everything (University ethernet -Ahhh....) but then i sat there and sat there.

**Note to synaptic users**

Make sure you are viewing the terminal in the Installation progress window(just click the tiny little arrow next to "terminal" so you can see waht goes on.

THERE ARE PROMPTS. if you do not answer them, you will stare a at progress bar going from left to right to left to right to left to right to left to right for HOURS :)

So, just fyi :)

if you apt-get kubuntu-desktop, naturally you will already be looking at a terminal and shouldnt have any problems :)

---

### Post by tamills on 2005-03-17
So does anyone know the difference between installing the KDE packages, kde-desktop, and kubuntu?

I did a search in synaptic for KDE and installed every result.  It seems to work just fine.  Is this the same as kubuntu?

Thanks

---

### Post by apokryphos on 2005-03-17
The kubuntu wiki has been updated:
[https://www.ubuntulinux.org/wiki/Kubuntu](https://www.ubuntulinux.org/wiki/Kubuntu)

In response to the above question: installing kde on ubuntu practically gives you Ubuntu. Apt-get kubuntu-desktop is a good bet; if you're not looking for all those things, install kde-core, which will get you all the necessary stuff; you'll also likely want kdm. 

For the kubuntu tweaks, get the kubuntu-default-settings package from the repositories, too.

---

### Post by CowPie on 2005-03-17
[QUOTE=apokryphos]The kubuntu wiki has been updated:
[https://www.ubuntulinux.org/wiki/Kubuntu](https://www.ubuntulinux.org/wiki/Kubuntu)

In response to the above question: installing kde on ubuntu practically gives you Ubuntu. Apt-get kubuntu-desktop is a good bet; if you're not looking for all those things, install kde-core, which will get you all the necessary stuff; you'll also likely want kdm. 

For the kubuntu tweaks, get the kubuntu-default-settings package from the repositories, too.[/QUOTE]
 You know what sucks. Uninstalling kubuntu-desktop with apt-get doesn't remove all the other stuff it installed!  And thanks for the link

---

### Post by CowPie on 2005-03-17
[QUOTE=wbeck85]Oh my goodness, Alright, so, i tried to install kubuntu-desktop via synaptic. It just finished, after waiting 2 hours. It only took about 3 minutes to dl everything (University ethernet -Ahhh....) but then i sat there and sat there.

**Note to synaptic users**

Make sure you are viewing the terminal in the Installation progress window(just click the tiny little arrow next to "terminal" so you can see waht goes on.

THERE ARE PROMPTS. if you do not answer them, you will stare a at progress bar going from left to right to left to right to left to right to left to right for HOURS :)

So, just fyi :)

if you apt-get kubuntu-desktop, naturally you will already be looking at a terminal and shouldnt have any problems :)[/QUOTE]
 Maybe it would be a good idea to file a bug with gnome to tell them to implement that windows xp notification thingy, where the taskbar blinks.

---

### Post by jdong on 2005-03-17
Both GNOME And KDE support the Urgent notifier (i.e. taskbar blink). GAIM actually can be configured to use it, through an included extension.


It should also drop open the terminal window in the event of a prompt.

This bug, instead, should be filed to the Synaptic guys.

---

### Post by bored2k on 2005-03-17
[QUOTE=CowPie]Maybe it would be a good idea to file a bug with gnome to tell them to implement that windows xp notification thingy, where the taskbar blinks.[/QUOTE]
 A bug ? What you want is to ask apt-get developers [debian] to make it produce a sound when a question gets asked, right ?

:-\

---

### Post by CowPie on 2005-03-17
[QUOTE=bored2k]A bug ? What you want is to ask apt-get developers [debian] to make it produce a sound when a question gets asked, right ?

:-\[/QUOTE]
 oops, I didn't know it was their problem!

---

### Post by apokryphos on 2005-03-18
[QUOTE=CowPie]You know what sucks. Uninstalling kubuntu-desktop with apt-get doesn't remove all the other stuff it installed!  And thanks for the link[/QUOTE]
Yeah, it's only a meta-package; it depends on other packages, but the reverse is not true. You can find out which ones it installs by checking the dependencies it has.

---

### Post by poofyhairguy on 2005-03-21
[QUOTE=bored2k]A bug ? What you want is to ask apt-get developers [debian] to make it produce a sound when a question gets asked, right ?

:-\[/QUOTE]


Nope. You want them to jump!

---

### Post by JaspSoft on 2005-03-23
newbie question:

I have kubuntu on cd, how to i install the kunbuntu-desktop onto a machine already running gnome ubuntu?

I have hoary.

---

### Post by J. S. Jackson on 2005-03-31
[QUOTE=JaspSoft]newbie question:

I have kubuntu on cd, how to i install the kunbuntu-desktop onto a machine already running gnome ubuntu?

I have hoary.[/QUOTE]

Fairly simple really.  Have a look here:
[http://kubuntu.org/documentation.php](http://kubuntu.org/documentation.php)

That's the method I used.

---

### Post by lao_V on 2005-03-31
[QUOTE=wbeck85]
**Note to synaptic users**

Make sure you are viewing the terminal in the Installation progress window(just click the tiny little arrow next to "terminal" so you can see waht goes on.

THERE ARE PROMPTS. if you do not answer them, you will stare a at progress bar going from left to right to left to right to left to right to left to right for HOURS :)

So, just fyi :)

if you apt-get kubuntu-desktop, naturally you will already be looking at a terminal and shouldnt have any problems :)[/QUOTE]

This has now been fixed/modified so that if there is a prompt in the terminal window a dialog box will appear which will ask you if you want to replace your configuration file or not.

It seems to be that Ubuntu dev's have been making a considerable number of changes (tweaks) in the way the standard kernel/software works. I'm just wondering if these are upstreamed at all? It would be pretty sad if they weren't.

---

### Post by J-Doe on 2005-04-03
Just wondering... I'm currently using Ubuntu Hoary and I installed KDE a while ago (haven't actually been using linux at all for a couple of months). I just installed KDE via apt-get and my KDE 3.3.2 is working somewhat well...
Should I install kubuntu-desktop ? cause now I guess I'm not using the real Kubuntu?
I won't do a clean install cause I had to work a little to get this system to work with my hardware...
So to be clear my question is: Should I install Kubuntu and if I should, how should I update my system to Kubuntu? :)

Again, thanks in advance for antbody kind enough to answer my questions...  ;-)

---

### Post by benjamonk on 2009-12-08
I'm thinking of trying Kubuntu 9.10 as I am having display issues with Ubuntu.

I get that I need to select the Kubuntu-Desktop package but do I need to remove everything Gnome related too? How do I do that, to make sure I've got everything removed? Do a search on 'Gnome' and remove everything completely?

---

### Post by alphaniner on 2009-12-08
Four and a half years dead.  That's quite a necro-bump.  You should start a new thread in the [Desktop Environments Forum]("http://ubuntuforums.org/forumdisplay.php?f=329").

---

### Post by benjamonk on 2009-12-08
Oh yes. Whoops!

---

### Post by NormanFLinux on 2009-12-08
Keep Synaptic and get rid of Kpackagekit. Its poorly implemented and I prefer Synaptic for installing software in Kubuntu.

---

### Post by cariboo on 2009-12-08
This thread is way to old, things have changed quite a bit in almost 5 years. IF you have installation questions, ask them in General Help. Closed.

---

