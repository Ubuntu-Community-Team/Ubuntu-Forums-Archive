---
title: "Budgie desktop - how to replace dock (plank) with panel?"
date: 2016-11-11
forum: Ubuntu/Debian BASED
---

### Post by spectatorx on 2016-11-11
After reading news at phoronix about budgie remix becoming official flavor i decided to give it a go and so far i'm impressed with how eye-candy this DE is and how lightweight at the same time. Usually eye-candy DEs are resource hogs and unstable giving some odd visual glitches.

I'm not fan of docks overall and this idea to me is not the most ergonomic thing in the world so at this moment plank is to me the only downside of budgie desktop. How to replace dock with classic panel like it is available in let's say, xfce or lxde?

---

### Post by Frogs Hair on 2016-11-11
I use Budgie on from the 16.10 repository which is different from the PPA , but you can remove plank or simply exclude in startup applications. The PPA upgrades the file manager which will affect the unity desktop if you happen to login.  

 It is possible add a panel in the Budgie settings and move the panel applets to either top or bottom . In the settings while the panel is in the top position select the add/+ indicator and this will create a bottom panel and then you can add or move applets for each panel.

Note: I used the PPA on 16.04 as well.

---

### Post by Bucky Ball on 2016-11-11
You mean you installed [Ubuntu Budgie from here]("https://budgie-remix.org/downloads/")? In other words, you have installed the OS and not just the desktop environment? It is not clear from your post.

> ... budgie remix becoming official flavor i decided to give it a go  

This would indicate you have installed Ubuntu Budgie (Budgie Remix OS), the OS, not just the desktop environment. Not sure where it's an official flavour but Ubuntu Budgie is not an official Canonical flavour and therefore not supported in the Ubuntu Official Flavours Support areas here. :)

Official support areas for Ubuntu, Kubuntu, Xubuntu, Edubuntu, Lubuntu, UbuntuGnome, Ubuntu Studio, Mythbuntu, Ubuntu Mate, and Ubuntu Kylin.

*Thread moved to **Ubuntu/Debian based**.*

---

### Post by Frogs Hair on 2016-11-11
Budgie won't be an official flavor until 17.04 though 16.10 offers the desktop and there is 16.04 PPA also.

 [https://budgie-remix.org/2016/11/08/its-official/](https://budgie-remix.org/2016/11/08/its-official/)

---

### Post by spectatorx on 2016-11-11
Thanks for help.
Yes, next release of budgie remix is going to be official flavor but i already decided to try it and i'm happy with it. Budgie desktop, imo, is the best DE i've tried - lightweight and highly configurable. I'm amazed with options of configuration of look of it while it is really lightweight and pls do not even start to me with kde which is horrible resource hog and is totally not suitable for laptops :P

In short: i've configured it the way i wanted it and now it's perfect for me, no plank, taskbar on top.

P.S.
OMG, it is so cute and laptop doesn't sweat like it used to with horrible mateDE.

---

### Post by spectatorx on 2016-11-11
One more question about budgie desktop... On task list every task has fixed length and i can't find options to change it. It is getting hilarious when more programs are opened and they get out of task list. Of course switching between tasks out of space can be workarounded by using multiple workspaces and switching between them or just pressing alt+tab but still would be nice to see some setting to auto-adjust length of task or to change fixed length to something smaller as default is pretty lengthy.

---

### Post by Frogs Hair on 2016-11-11
I use the icon task list so there only icons representing open applications. I also don't pin applications so I know whats open by the icons in the panel.

---

### Post by spectatorx on 2016-11-11
Sounds like nice workaround, but it only shows 4 icons pinned by default and when i unpin them my opened applications do not show in there, how to change this behavior to this what i want to achieve? Icon task list doesn't have any additional settings to tweak it.

I also do not pin applications, that's useless waste of space, for something like this dock is much better solution.

---

### Post by Frogs Hair on 2016-11-11
Here is my Budgie 16.10 top panel settings and they work as I wrote though I could move the icon task list to a bottom panel to give more space for open application icons.

---

### Post by spectatorx on 2016-11-11
Seems like i have some different version of budgie desktop, icon of that feature is different from yours and it works different way as i explained it in previous post.

---

### Post by Frogs Hair on 2016-11-11
I'm running 10.2.7-3 from the 16.10 repository. I used the PPA from the link with 16.04. 

  [http://www.webupd8.org/2016/03/how-to-install-budgie-desktop-in-ubuntu-ppa.html](http://www.webupd8.org/2016/03/how-to-install-budgie-desktop-in-ubuntu-ppa.html)

---

### Post by spectatorx on 2016-11-11
Ok, i will try it, thx for link.
According to info from terminal i have installed:
budgie-desktop 10.2.8
Copyright © 2014-2016 Ikey Doherty, Solus Project

Seems like this is exactly the same version as at ppa mentioned in article, i'm wondering why there are such differences in how works and in functionality.

---

### Post by Frogs Hair on 2016-11-11
Your picture looks different because it's a different screen. I was in the panel menu and you displayed the applets menu. You may very well have 2.8 if using the same PPA because it's an older post from webupd8. I have the same applets.

---

### Post by spectatorx on 2016-11-11
Are you sure? If i am wrong please correct me. I think differences may originate in DE being set up under two different distros (yours is ubuntu as i assume and mine is ubuntu budgie remix).

---

### Post by spectatorx on 2016-11-11
Are you sure? If i am wrong please correct me. I think differences may originate in DE being set up under two different distros (yours is ubuntu as i assume and mine is ubuntu budgie remix).

---

### Post by Frogs Hair on 2016-11-11
We have the same applets and the settings appear to be the same , but I rearranged  my panel applets and added spacers after installation. In your bottom panel you should be able to replace the tasklist with the icon tasklist to eliminate the text. I'm not using the ark theme at the moment either.

---

### Post by spectatorx on 2016-11-11
Ok, i figured it out now and it works exactly as you said, almost. There is a little bug with activating of this list: when you activate icon task list it doesn't show icons of which are already opened and it is needed to reopen them to make them visible on this list.

So yes, icon task list works perfectly excepts its first launch.

Thank you for help and your patience.

---

### Post by Frogs Hair on 2016-11-11
You're welcome, there was a bit of learning curve for me too.

---

### Post by spectatorx on 2016-11-11
To conclude this thread here is how looks final result of my first deeper contact with budgie desktop. I've tried it few days ago on ubuntu-mate by installing from ppa but for some reason half of interface wasn't rendered so DE was unusable and to be honest it always ends up to me in similar fashion if i want to test some DE by installing it on installed os. and then i have to use distro with pre-installed DE of my choice.

---

### Post by Bucky Ball on 2016-11-11
> **spectatorx said:**
> ... to be honest it always ends up to me in similar fashion if i want to test some DE by installing it on installed os. and then i have to use distro with pre-installed DE of my choice.

Thought of using Virtualbox and running the OSs you want to try as a virtual machine? Save yourself a whole lot of time and hassle rather than installing every OS you want to try.

Just download the ISO, launch Virtualbox, create a virtual machine and boot directly from the ISO. No need to install. Installing every OS you want to try sounds boring! :)

---

### Post by spectatorx on 2016-11-11
I do not like virtual machines as they are not the same thing as installing on physical machine and this way they will not show problems which you may face after installing on physical machine. I'm not testing new OSes all that often, before ubuntu-mate (this year) i've tried xubuntu.... 2-3 years ago, lubuntu even more years ago so... yes, that's how often i try some new distro ;-) Before installing any linux distro first i launch its live session if available.

P.S.
Installing new OS, as this thread clearly shows it, is never boring :-)

---

### Post by Bucky Ball on 2016-11-11
> **spectatorx said:**
> Installing new OS, as this thread clearly shows it, is never boring :-)

'Not boring' when you do it as often as you are and as a learning thing, which seems to be the case. 'Is boring' when you are checking out four or five in a few days or a week just because you're curious. :)

I checked out about ten in four or five days about two years ago. No way would I want to be doing all that installing. 

Anyhow, have fun. :)

---

### Post by happykillmore on 2016-12-18
I'm using budgie ubuntu or budgie remix 16.10 on virtualbox and i'm having the same problem. I hate the plank(dock) I figured how to move it to the top or bottom but when it is over the panel which is where i want it it disappears when you mouse over it.So there is no way to add it to the panel like it is in solus. I can't find a way to add apps to the panel or launcher like you can in ubuntu or i would just do that and disable the eyesore. I'm sticking with ubuntu mate for now but i really want to like this distro. Whoever said this was highly customizable must have been referring to something else other than the gui. I saw where one version of budgie had a tweak tool but 16.10 does not. This one is basically as is with very limited tweaking like arranging the deck chairs on the Titanic. I hope they correct this so i can send them a tip for a job very well done but for now it will stay in virtualbox. Maybe solus will grow on me but i am much more at home with ubuntu.

---

