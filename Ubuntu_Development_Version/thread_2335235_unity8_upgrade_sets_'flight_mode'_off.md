---
title: "unity8 upgrade sets 'flight mode' off"
date: 2016-08-26
forum: Ubuntu Development Version
---

### Post by ventrical on 2016-08-26
Unity8 upgrade sets flight mode to  off. Wired ethernet will not work. Must turn flgiht mode on.

Regards..

---

### Post by grahammechanical on 2016-08-26
I got a surprise a couple of days ago. Unity 8 session loaded! I cannot remember if it was yakkety or xenial. I did detect that WiFi was connected in Unity 7. At least there was an app indicator that said I was connected by WiFi to my router.

I could not activate my Ubuntu One account to install apps. But Browser connected to the internet. Then I made the mistake or resizing Browser and it froze the desktop. 

Regards

---

### Post by ventrical on 2016-08-26
I cannot get the apps accounts to work either but I am very happy with Xapps (libertine containers). I can run debs apps all day long . Some just do not work but others work fine. 

Also  - off topic- I found that the new Xorg in yakkety/xenial will allow us ro run standalone apps like Firefox/games/Libreoffice in a tty  So this is a plus.

Regards..

---

### Post by ventrical on 2016-08-26
> **grahammechanical said:**
> I got a surprise a couple of days ago. Unity 8 session loaded! I cannot remember if it was yakkety or xenial. I did detect that WiFi was connected in Unity 7. At least there was an app indicator that said I was connected by WiFi to my router.

I could not activate my Ubuntu One account to install apps. But Browser connected to the internet. Then I made the mistake or resizing Browser and it froze the desktop. 

Regards

btw i did send an e-mail to Ollie G about snappy_personal.img and have since not received a reply. Last word from Mark was that he is focusing attention to unity8 so I guess we all had to curb our enthusiasms to some degree.

regards..

---

### Post by grahammechanical on 2016-08-26
A few minutes ago I was able to get into Unity 8 on yakkety again. I ran Checkbox. It did not freeze the UI even when it got to the part where it does memory test. That part takes awhile to complete. The UI was still usable. I loaded System Settings and tested the swipe to the right screen edge application switcher function. It is fast even with an intensive task being performed.

Then I opened Browser and it froze the desktop. And now I cannot get back into Unity 8. Such is life. I will install Libertine in Unity 7 and see if I can get an app like Firefox showing up in Unity 8 the next time it feels in the mood to load.

I have Libertine installed on Unity 7 on xenial + Unity 8 session. For a few weeks it kept given system errors but they have now gone away. I keep hoping to get into Unity 8 on xenial to see if any of the installed snaps show up.

Regards

---

### Post by ventrical on 2016-08-26
I tried that method .. to sneak in apps through libertine in unity7 but it was a no go. It has to be done through unity8. I have a perfectly working unity8 on xenial with 1GB on nVidia card.  I am currently attempting to compile a list of x11-apps that work in libertine containers. There are lots that work. I hope you get  you system up and running at par.

Regards..

---

### Post by cariboo on 2016-08-26
I've been getting ilbertine crashes in Unity7, on yakkety, have sent a bug report.

---

### Post by grahammechanical on 2016-08-26
How did you install Libertine in Unity 8? Switch to tty1 and run the command and then switch back again?

Regards

---

### Post by cariboo on 2016-08-27
> **grahammechanical said:**
> How did you install Libertine in Unity 8? Switch to tty1 and run the command and then switch back again?

Regards

I actually installed it while running Unity7, it shows up after logging into Unity8.

---

### Post by ventrical on 2016-08-27
Yes .. that is the method according to - [http://mhall119.com/2016/05/dogfooding-unity-8/](http://mhall119.com/2016/05/dogfooding-unity-8/)

Regards..

---

### Post by ventrical on 2016-08-27
> **grahammechanical said:**
> How did you install Libertine in Unity 8? Switch to tty1 and run the command and then switch back again?

Regards

I used both methods because I had to remove and re-install. So , from unity7 or tty  from a running unity8 session it will work. I would use xenial if you have an unstable system if you want libertine to work with some semblance of normalcy. It works on yakkety but  after you have done lots of work and tweaking it will wipe everything out randomly during an update/upgrade... I'm not complaining ... it's par for the course in development version.

@graham

I have all my systems working according to the pseudo-list method from the link that you had posted - [http://mhall119.com/2016/05/dogfooding-unity-8/](http://mhall119.com/2016/05/dogfooding-unity-8/)  and I have my nVidia adapted machines working just fine on 1GBDRAM so I don't see why  you are having probs getting libertine running.  The only extras was I kept  re--installing fresh installs until I got it right. (both yak and xenial)


edit:

and yes .. it takes lots of re-boots and 
```

sudo apt-get update
sudo apt-get dist-upgrade
sudo dpkg --configure -a
sudo apt-get install -f

```

a few times and not always in that order.
Regards..

---

### Post by ventrical on 2016-08-27
Here are some more screenshots.. from X11apps that work.
This is from the game titanion. I can also run Brutal Chess but it will not allow screenshot. A quark I guess.

---

### Post by ventrical on 2016-08-27
Oh.. it did take a screenshot of Brutal Chess.

---

### Post by ventrical on 2016-08-27
Awesome enough I can run two games concurrently, Brutal Chess and Chromium BSU.

edit:
Just keep in mind that this is done in a container. You can also run different apps from different containers concurrently.

---

### Post by ventrical on 2016-08-27
You can run terminal.click in unity8 session while also running xterm from a container concurrently. Notice htop in running clean in xterm. You have to actually install htop  seperately into each container. This displays the security benefits of running lxc containers.

---

### Post by mc4man on 2016-08-27
> **ventrical said:**
> Unity8 upgrade sets flight mode to  off. Wired ethernet will not work. Must turn flgiht mode on.

Regards..
Well that doesn't seem right, if true (ethernet doesn't work simply by being plugged in) then they should fix that

---

### Post by ventrical on 2016-08-28
+1

err .. maybe I did something ... and flicked it off myself :)

---

### Post by ventrical on 2016-08-28
> **mc4man said:**
> Well that doesn't seem right, if true (ethernet doesn't work simply by being plugged in) then they should fix that

Wrong assumption on my part. It is off by default and has nothing to do with wired network.

Regards..

---

### Post by cariboo on 2016-08-28
I assume, that unity8 is set in flight mode when you don't have a wireless connection, the screenshot is just after startup.

---

### Post by grahammechanical on 2016-08-28
In my opinion, Unity 8 has not yet transitioned from mobile to desktop UI. Unity 8 still expects either a WiFI or a mobile type connection. System Settings is certainly still presenting as a utility for a mobile device.

A fresh install of 27 August yakkety daily ISO would not allow me to set up a WiFi connection in Unity 7 until I had disconnected the wired connection to the router. This was after I installed Unity 8 session. So, standard yakkety may not have this problem. Or may be it does.

Regards.

---

### Post by ventrical on 2016-08-28
> **cariboo said:**
> I assume, that unity8 is set in flight mode when you don't have a wireless connection, the screenshot is just after startup.

I think that it mostly correct.

Regards..

---

### Post by ventrical on 2016-08-28
> **cariboo said:**
> I assume, that unity8 is set in flight mode when you don't have a wireless connection, the screenshot is just after startup.

I think now that it is merely a cosmetic bug in that the 'wired' ethernet indicator is not patched in. All my systems are wired ethernet (that I am using for unity8/yakkety testing). So there may be a .deb package that will work with this. I am experimenting with all ( as many as I can in schedule) the deb apps available at the USC. 16.04 or 16.10 will not display the deb package name but trusty will - for example  chromium-browser.

Regards..

---

