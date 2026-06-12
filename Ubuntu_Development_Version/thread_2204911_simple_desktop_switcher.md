---
title: "simple desktop switcher"
date: 2014-02-11
forum: Ubuntu Development Version
---

### Post by felgro on 2014-02-11
Hi,

Due to the circumstance of a new laptop with a very difficult Radeon card, the only way I have been able to get a functional Ubuntu install happening is with the Trusty alpha - which means I have to use Unity for the first time. Testing in a VM, all of the alternate desktops I like cause complete, unusable video implosion. So I am resigned to learning to love Unity. And this could be entirely possible, **IF** I can find a simple widget to switch workspaces. i don't want much, just a simple display sitting in the top tool bar, like the ones that are standard in cinnamon and gnome -

[IMG]http://oi60.tinypic.com/efh47b.jpg[/IMG]

That's all - just 4 boxes to switch between windows. Does such a basic thing exist? I can't find anything and I hate the one that is in the main unity ribbon. If I can find such a beast, I am willing to at least try and like unity.

---

### Post by grahammechanical on 2014-02-11
Ok, so you have installed Trusty Tahr. In Unity we open System Settings>Appearance utility and in the Bahaviour tab we tick Enable Workspaces. That will put an icon of a 2 x 2 grid of workspaces in the Unity Launcher. Try clicking on that to see what happens. Or use Ctrl+Alt+arrow ket to move from workspace to work space.

But that is not what you want is it? So, install gnome-session-flashback. That will put 2 new session options on the login screen. Gnome Flashback (with Compiz) and Gnome Flashback (with Metacity). Choose the Metacity option then you will get a desktop that does not look like Unity or Gnome 3 shell.

On the bottom panel at the right side will be an icon of a workspace. Right click it and open Properties. That will give you options to add more workspaces along with the little boxes that you like.

If you choose the with Compiz option then you will need to use CCSM (CompizConfiguration Settings Manager) to get the same effect. Do not use the properties option that will mess things up.

Edit. One more thing. There is at least one bug with using Gnome Flashback in Trusty Tahr. We get to a desktop all right and the Appearance and Places menus are there on the top panel to the left but on the right side the Network, Sound and Power/cog menu indicators will be missing. It takes about two minutes for them to appear. Just a small inconvenience. But, hey, it is all free.

Regards.

---

### Post by oldos2er on 2014-02-11
Why do you have to use Unity? I'm running 14.04, no Unity.

---

### Post by felgro on 2014-02-12
[                                                      ]("http://ubuntuforums.org/member.php?u=1087323")@grahammechanical - that is what I am using, unity workspaces. I just don't like them. Sure, pretty and whizzbang - but it's not what I want. Just 4 clickable boxes on static toolbar - thats all I want.

@Ann - what alternatives are there that don't destroy the windowing system? Basic Gnome desktop is fatal on my machine, too scared to even try and install KDE or Cinnamon (I just spent a week beating my vid card into submission to launch a graphic environment at all - in no mood to rebuild again). Xfce does seem to work, but is just plain ugly and limited. What are you using?

---

### Post by oldos2er on 2014-02-12
Not sure what you mean by "windowing system." I use i3-wm, I also have Lubuntu 14.04 installed on an older computer; LXDE is similar to xfce, but even lighter on resources.

---

### Post by felgro on 2014-02-14
> **oldos2er said:**
> Not sure what you mean by "windowing system." 

Desktop. GUI. Non-terminal. Pretty stuff.

> I use i3-wm, I also have Lubuntu 14.04 installed on an older computer; LXDE is similar to xfce, but even lighter on resources.

Is there a resource anywhere for what does not make Trusty/Unity explode? I achieved a workable system - don't want to start from scratch.

---

### Post by oldos2er on 2014-02-14
Trusty is still alpha, so it may or may not "explode" of its own accord.  :)
I really have no experience with Unity other than to say I just don't care for it much. If you look through the Ubuntu +1 subforum you'll see people running various desktop environments on Trusty.

---

### Post by QIII on 2014-02-14
Moved to Ubuntu +1

---

### Post by oldos2er on 2014-02-14
Thanks QIII.

---

### Post by mc4man on 2014-02-14
There is an indicator-workspace that sorta does as you wanted - 
shows which ws on
switches workspaces *though* only thru the dropdown - see screen (so 1 extra click

It hasn't been developed in some time (2 yrs.) but can still be used in 14.04 with a few minutes work.
So won't bother to lay out how unless interested ...

---

### Post by Hazzabin on 2014-02-14
> **mc4man said:**
> There is an indicator-workspace that sorta does as you wanted - 
shows which ws on
switches workspaces *though* only thru the dropdown - see screen (so 1 extra click

It hasn't been developed in some time (2 yrs.) but can still be used in 14.04 with a few minutes work.
So won't bother to lay out how unless interested ...

I for one would be interested on a "How To" to get that 'widget' to work on 14.04 and I assume with 'Unity'

---

### Post by mc4man on 2014-02-14
Go here, choose the bottom all.deb, (0.6.4)  download & install with Software-center, gdebi or dpkg 
[http://ppa.launchpad.net/geod/ppa-geod/ubuntu/pool/main/i/indicator-workspaces/](http://ppa.launchpad.net/geod/ppa-geod/ubuntu/pool/main/i/indicator-workspaces/)

After install but before running (by default will be autostarted on login) you need to do 2 things - 
```
sudo apt-get install python-appindicator python-wnck
```

The installed autostart .desktop is flawed, so open it in a root text editor,  for ex. nano - 

```
sudo nano /etc/xdg/autostart/indicator-workspaces.desktop
```
using arrow & backspace  keys remove the 3rd & 2nd to last lines & the space they occupy - 
Then ctrl+o, enter, ctrl+x  on keyboard to save edits

(if desired use gksudo gedit instead of nano, gksu isn't default installed so install if need be

 These are the 2 lines to be removed (really only the latter but startup notify isn't needed so may as well remove - 
```
StartupNotify=true
AutostartCondition=GNOME /apps/indicator-workspaces/autostart
```

After that just log out/in, the indicator will show 6 sec. after login

Note that if using something like 1x4  for rotate/cube then right click on indicator > preferences & adjust to 4 x 1 as it will be set to 4 x 2 & not work properly...
Also note there is an upward limit to amount of workspaces it works on ...

---

### Post by Hazzabin on 2014-02-14
mc4man, 

many thanks for that will give it a try asap :D :guitar:

---

