---
title: "Question about Desktop Enviroments"
date: 2015-11-22
forum: Ubuntu, Linux and OS Chat
---

### Post by Buster_Ball on 2015-11-22
Hello everyone!  I have recently discovered Linux and have been trying out various Distros and i have a quick question.

Whats the core differences between the Desktop Enviroments ? for example i had always been under the assumption that GNOME would always have a top level menu and them after downloading Debian GNOME it looked more like UNITY with the Menu/Iocons on the side. apparently i had the wrong idea. what i would like to know is how can you tell one from the other just by a quick look and how are they different as far as function ? im not asking for a complete run down of all the different DE's i have no problem learning that on my own but a quick comparison between a few like GNOME,KDE,UNITY or whichever you prefer would be great so i can get a better idea of what im looking for when selecting. Thanks!

---

### Post by Bucky Ball on 2015-11-22
Welcome. One way to answer your questions is to install Virtualbox (it's in the Software Centre), download some ISOs and run them as virtual machines in VBox. You can also create bootable install media, USB or DVD, of the various flavours and spins, boot from them and 'Try *buntu' without installing to hard drive or changing your setup in any way.

lxde and xfce4 are lightweight, Unity and KDE are heftier. But as you've discovered, there are lots to choose from, each with their own traits. 

I do a [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD") and add xfce4 and whatever else I want so up to you the hybrid you create to suit your tastes. Only way to really know if a DE is going to work for you is to try it. Good luck and have fun. :)

---

### Post by buzzingrobot on 2015-11-22
> **Buster_Ball said:**
> ... i had always been under the assumption that GNOME would always have a top level menu and them after downloading Debian GNOME it looked more like UNITY with the Menu/Iocons on the side. Thanks!

Gnome changed in 2011 when it stopped development and maintenance of the old Gnome 2 environment.  Unity on Ubuntu is Canonical's response to that, and the Gnome team moved on to Gnome 3 and the Gnome Shell you see today.

---

### Post by grahammechanical on 2015-11-22
A picture speaks a thousand words.

Do a web search. Gnome 3; Ubuntu Unity: LXDE; Xfce; KDE; Mate desktop; KDE fusion; LXQT desktop and so on.

Do that and you will be offered a selection of images relative to what you searched for. That way this thread does not become yet another attempt to cause disagreements among the Ubuntu forum community. And this is the give-away for me:

> whichever you prefer would be great

It invites disagreements.

---

### Post by neu5eeCh on 2015-11-22
> **Buster_Ball said:**
> Hello everyone!  I have recently discovered Linux and have been trying out various Distros and i have a quick question.

Whats the core differences between the Desktop Enviroments ? for example i had always been under the assumption that GNOME would always have a top level menu and them after downloading Debian GNOME it looked more like UNITY with the Menu/Iocons on the side. apparently i had the wrong idea. what i would like to know is how can you tell one from the other just by a quick look and how are they different as far as function ? im not asking for a complete run down of all the different DE's i have no problem learning that on my own but a quick comparison between a few like GNOME,KDE,UNITY or whichever you prefer would be great so i can get a better idea of what im looking for when selecting. Thanks!

XFCE4 --> Drop Down Menu/Minimal Eye Candy/ Low Memory Usage/_Extremely_ Configurable
Unity  --> Icon Launcher/Minimal Eye Candy/Highest Memory Usage/Least Configurable DE
Gnome Shell --> Icon Launcher/Minimal Eye Candy/High Memory Usage/Minimally Configurable (Limited Configurability with Extensions)
KDE  --> Drop Down Menu/Oodles of Eye Candy/High Memory Usage/_Extremely_ Configurable
Cinnamon --> Drop Down Menu/Moderate Eye Candy/Moderate Memory Usage/Moderately Configurable
Pantheon --> Drop Down Menu/Minimal Eye Candy/Moderate Memory Usage/Minimally Configurable
LXDE --> Drop Down Menu/Minimal Eye Candy/Low Memory Usage/Very Configurable
[Budgie]("http://www.omgubuntu.co.uk/2014/07/install-budgie-evolve-os-desktop-ubuntu-14-04") --> Drop Down Menu/Minimal Eye Candy/Low Memory Usage/Minimally Configurable (New & Beta-ish)
Enlightenment --> Drop Down Menu/Lots of Eye Candy/Low Memory Usage/_Extremely_ Configurable (Bodhi Linux now uses a fork of Enlightenment)

This is, of course, subjective, but:

Like Windows 2000 --> LXDE
Like Windows XP --> XFCE (Commonly used to mock-up XP) & Cinnamon (no transparency)
Like Windows 7 or 10 --> KDE
Like Chrome OS --> Budgie, XFCE or Pantheon
Like OS X --> Pantheon
Commonly Compared to Mobile OS's like Android or iOS because of their Icon Launchers --> Unity and Gnome Shell

Hope that helps. :-)

---

### Post by Buster_Ball on 2015-11-23
Bucky, ive already gathered up a nice little stack of live distro's in the past week but i guess it wouldnt hurt to use VBox and give my burning rom a rest..

[COLOR=#000000]buzz, my first cpl years with linux was spent with Kali and BT5 and the first install i selected was with GNOME for whatever reason and others after that i just stuck with it from there.  after i did a live boot from Debian 8 and soon as i logged in the first thing that went through my head was "wtf, i thought i downloaded GNOME".[/COLOR][COLOR=#000000]

graham, i did that already and i think it just left me more confused.

VTPoet, thats pretty much what i was wanting to know and thank you for taking X amount of time from ur life to type all that out for me. 
[/COLOR]

---

### Post by Bucky Ball on 2015-11-23
Thing is, though, as extensive as VT's list is, with enough tweaking you can make one look very similar to another if you're determined enough. :)

If I add this window manager and that dock to xfce it starts to look like something else, so ... hybridise! One of the things I like about Linux/Ubuntu is that I can make it look like what works best for me and am not forced to be stuck with a default desktop environment and that's that. Have fun!

---

### Post by monkeybrain20122 on 2015-11-23
In both Unity and gnome shell you can add a classical drop down menu though why one would want to do it I don't know, menu sucks in finding things. In Unity it is called classicmenu-indicator in the repo. In gnome shell I think there is an extension for it. 

They look similar, but Unity is a lot more stable and  configurable with compiz config setting manger (actually I disagree that unity is not configurable, other than the position of the dock and the buttons on the left it is very configurable with the ccsm functionwise) It can be configured to produce a very smooth work flow; gnome shell is a lot more constricting. Extensions help a bit or it will be almost unusable IMO because of all kinds of minor inflexibilities and aggravations, but extensions are frequently abandoned and what works in one gnome shell release may not be installable in the next. 

Unity 7 is in maintenance and bug fix mode so it is quite stable whereas gnome changes erratically from one release to the next, features and functions you rely on in one release will be removed out of the blue in the next because of some bizarre "design decisions". I don't know how  well Ubuntu gnome works, my experience with gnome shell is with Fedora, which is more up to date and closer to upstream, it is getting to be a pain to use.

---

### Post by neu5eeCh on 2015-11-23
> **monkeybrain20122 said:**
> (actually I disagree that unity is not configurable, other than the position of the dock and the buttons on the left it is very configurable with the ccsm functionwise)

Yes, it's subjective. I personally count the ability to move the panel and the/(or any) launcher *_as configurability_* (more so than any other feature). Unity doesn't allow it. You can't move the panel. The most you can do is make it transparent. I don't know if it's still possible to move the launcher (could do it with CCSM but it was messy). It *can* be hidden. Gnome Shell is slightly more configurable. You can't move the panel but it's possible, _if_ the extensions are working on any given Tuesday, to alter other features. My two favorite desktops are Plasma 5 (Kubuntu) (if I have the power) and XFCE if I don't. My favorite XFCE distro is Voyager. It's overkill but I actually use all the extras. All that said, I'm really looking forward to Unity 8.

Speaking of which, I forgot a desktop (I kept feeling like a forgot one):

Deepin, it's the most Windows 10-like in certain respects -- very polished.

[Deepin]("http://www.deepin.org/system.html?language=en") --> Icon Launcher/Minimal Eye Candy/High Memory Usage/Minimally Configurable

---

