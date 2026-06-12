---
title: "Ubuntu Raring 13.04: The Good, The Bad, and the Ugly"
date: 2013-04-27
forum: Ubuntu, Linux and OS Chat
---

### Post by stevedude on 2013-04-27
**The Good**: Finally, I have an Ubuntu release (64-bit Raring 13.04) where an upgrade path worked flawlessly instead of having to do a fresh install and reinstall all of my software and configurations.

The new icons and lenses.

Application swiching from the Unity menu (IE: Open several Firefox windows (not tabs) and easily switch between them.



**The Bad**: In my workflow, I was used to selecting the gear icon and choosing "About This Computer" in Ubuntu Quetzel 12.10 and the system would run a software update check and notify me that I could install the updates within the Details window that appeared. Now I have to select Dash, type "Software Updater", and select the Software Updater program. Not as elegant as the prior release and will probably go unnoticed if you never used Ubuntu that way.

Steam Games graphics are slower, not faster, with this update (IE: Serious Sam 3 and other FPS games for Linux) 


**The Ugly**: Skype does not work if you are using NVidia or AMD proprietary drivers and requires a workaround as stated here: [http://www.webupd8.org/2013/04/fix-skype-not-working-in-ubuntu-1304.html](http://www.webupd8.org/2013/04/fix-skype-not-working-in-ubuntu-1304.html)

Now that I have to use "Software Updater" to check for Ubuntu updates, why didn't developers change the name of "Software & Updates" which lists which repositories are being used? This is confusing to users; "Software Updater" and "Software & Updates" that perform differing functions.

Google Chrome can't be installed on fresh installations due to the same bug that affects Skype. See workaround here: [http://www.webupd8.org/2013/04/7-things-to-do-after-installing-ubuntu.html](http://www.webupd8.org/2013/04/7-things-to-do-after-installing-ubuntu.html)

Sound issues also can occur after upgrading to Ubuntu Raring 13.04. See the workaround here: [http://linuxg.net/how-to-fix-the-no-sound-error-after-upgrading-to-ubuntu-13-04/](http://linuxg.net/how-to-fix-the-no-sound-error-after-upgrading-to-ubuntu-13-04/)



Overall, I'm just "OK" with this update. I love Ubuntu, but upgrade time can be a chore. What's your Good/Bad/Ugly experience?

---

### Post by cariboo on 2013-04-28
This isn't a support question, moved.

---

### Post by deadflowr on 2013-04-28
Non-free packages can be, unfortunately, expected to have problems on a new release.
The chromium project is working on the chrome problem at least.
Who knows what microsoft is doing about the skype problem.

---

### Post by Mopar1973Man on 2013-04-28
Might be a option of backing up to 12.04 LTS for better stability of the common thing you using. Just my 2 cents worth.

---

### Post by VietCanada on 2013-04-29
Separate X screens option still doesn't function. Twinview allows one to have different resolutions for different monitors but twinview is not separate X screens. I had numerous issues trying to work in twinview in the same way I worked in separate X screens. Too many to enumerate. They are just not the same thing. 

I still don't appreciate Dash. Its not even ballpark as simple and intuitive as having files organized in well labelled folders. It's also slower. Is that because it is going online to look for unnecessary and unwanted 'suggestions'? I can do that myself if I'm interested. It's just a start menu button without folders organizing the files. 

Changing workstations. I used to just right click on the top bar of any window and select 'move to the workstaion right' or whatever. After some fooling around I discovered that I have to leave full screen mode to get this option.

Which leads to the whole issue of the window menu options all being on the same bar at the top. I guess having other windows just plain disappear without any explanation or help whatsoever whenever a new window is open is a consequence of moving the window menu. Definitely slower, not to mention the learning curve when compared to just clicking the name of the window along some bar at the bottom of the screen to change screens.  Many, many issues with this inexplicable, unnecessary change. The fact that the menu options aren't visible unless the mouse is nearby caused me a lot of grief. How about some tooltips? Not to mention looking for my lost windows, panic at the thought of having lost something important, apprehension of openning new windows. Wasted time looking for old windows and waiting for them to open again. It's slow and it slows me down.

Lots of niggly issues with software I've openned. Too many to list. I chose a destination folder for transmission dls yet every time I open it that folder has changed. Apparently randomly but I don't know for sure.

Libre Office presentation. When openned my mouse became sticky and clicking on things didn't seem to work. My PC is powerful enough for any OS on the market for the public.

The wallpaper selection is not as nice this time. A couple nice pics and a lot of boring, fuzzy coloured things. I like landscapes on my desktop, I don't like PC art so that's only a personal issue.

It looks nice. If they could improve the Dash to make it more user friendly, organized and stop it from going online and then repair the separate X screen functionality and finally leave the window menu options on the windows that they are meant for. it would be great. 

So for me it's close but no cigar. I need skype for work at times so that's a big (financial) problem for me if it doesn't work. Make Dash user friendly, get back separate X- screen, fix Skype. Ubuntu 13 just feels kind of amateurish. The way simple things don't work or are unfathomably unintuitive. Kind of like some kids first stab at making an OS. Of course he knows where everything is and how it works, he wrote it but little thought given to end users and what their experience might be. Especially those that just expect things to work.

I dual boot with Mint Mate 13 and all those work so Ubuntu 13 is just a plaything for me atm.

---

### Post by gerowen on 2013-04-29
I did an "in-place" upgrade from 12.10 

**Good**

- Like some of the new icons better than the old ones.
- The "files" application that replaced the home icon seems to open a bit faster, and the new look/icons on the left pane are nice.
- None of my 3rd party applications were broken and still function normally after the upgrade. (With one minor caveat, see "Ugly")
- My wife, who isn't terribly techy, didn't even notice I had upgraded the computer.

**Bad**

See "Ugly".

**Ugly**

- Google Chrome has this issue where some things (not always flash) look all garbled, like an old NES cartridge when it freezes mid-game or something.
- There seems to be some weird flash issues that did not exist for me in 12.10.  I've had some flakey issues with both peppermint flash and the Adobe flash from the Ubuntu repos.  In 12.10, the Ubuntu release of Adobe flash worked fine, and for the most part it still does, but I had a video freeze in fullscreen, and had to CTRL+ALT+F1, issue a "killall firefox", then CTRL+ALT+F7 back in order to regain control of my computer.

---

### Post by craig10x on 2013-04-29
@VietCanada:  regarding the dash going online...that is by default but they provide an easy way to turn it off...just go to privacy in system settings and turn the buttons off...no more online searches...

---

### Post by VietCanada on 2013-04-29
> **craig10x said:**
> @VietCanada:  regarding the dash going online...that is by default but they provide an easy way to turn it off...just go to privacy in system settings and turn the buttons off...no more online searches...

Thanx, I unstalled Amazon while I was at it too.

---

### Post by neu5eeCh on 2013-04-29
> **stevedude said:**
> ** ... The Ugly**: Skype does not work if you are using NVidia or AMD proprietary drivers and requires a workaround as stated here: [http://www.webupd8.org/2013/04/fix-skype-not-working-in-ubuntu-1304.html](http://www.webupd8.org/2013/04/fix-skype-not-working-in-ubuntu-1304.html)

(....)

Google Chrome can't be installed on fresh installations due to the same bug that affects Skype. See workaround here: [http://www.webupd8.org/2013/04/7-things-to-do-after-installing-ubuntu.html](http://www.webupd8.org/2013/04/7-things-to-do-after-installing-ubuntu.html)



Are these issues isolated to the Unity DE, or do they effect all respins: Xubuntu, Kubuntu, etc...?

---

### Post by stevedude on 2013-05-01
@VTPoet; I don't know off-hand, but if they are based on Ubuntu 13.04 it may impact those. Sorry I can't be more definitive.

---

### Post by monkeybrain2012 on 2013-05-01
> **VTPoet said:**
> Are these issues isolated to the Unity DE, or do they effect all respins: Xubuntu, Kubuntu, etc...?

Skype is working now after yesterday's skype update. The Chrome problem has to do with missing libraries from Raring's repo, nothing to do with DEs,Chrome/Chromium has fixed the bug but it has not filtered down to the stable channel yet, you can install stable Chrome if you grab those libraries from quantal's repo (see the webupd8 link in your quote)

---

### Post by codingman on 2013-05-01
> **VTPoet said:**
> Are these issues isolated to the Unity DE, or do they effect all respins: Xubuntu, Kubuntu, etc...?

I have issues with Skype on Arch when using proprietary NVIDIA drivers. I am using i3-wm, so not locked to DE either. Switched to nouveau and now it works.

---

### Post by boulboul on 2013-05-02
I upgraded from 12.10 to 13.04 and i was happy that everything ran smoothly expect Skype for which I had to apply the reported trick:
LD_PRELOAD=/usr/lib/i386-linux-gnu/mesa/libGL.so.1 /usr/bin/skype
Note, that Chrome from time to time freezes the session but this was already the case with 12.10 (seems like it's associated to compiz process)
so positive feedback from my side.

---

### Post by Col936 on 2013-05-04
[B]I used the Beta version, about a week and a half before it came out officially, mind you.
The Good:[/B] Runs nicer and faster, as well as a few new icon styles and what not.
[B]
The Bad:[/B] A few weird visual glitches in Unity, like the search window has a few weird image/color/quality bugs.

**The Ugly: **Came without a BUNCH of apparently important dependencies, one of which I had to download from the internet, as it wasn't available in the package registry for some reason. I couldn't install Google Chrome, Synaptic Package Manager, or ANY other packages without these.I was quite tempted to just go back to my old 12.10 and stay there until it officially came out.

But that was the first day I had it. The same day, I switched to LXDE(I'm weird. I use desktop environments that come in derivatives of Ubuntu, yet I don't just switch over...), and I ran even faster with that. Overall, after working out a few kinks, I felt like it was a big improvement over 12.10.

> **stevedude said:**
> Skype does not work if you are using NVidia or AMD proprietary drivers

A friend of mine had this same issue with 12.10. I have a netbook with integrated graphics, so I don't need drivers too badly. He, however, has a gaming laptop, with a NVidia GeForce 8600M GT or something. Upon getting the drivers and installing them, when he opened skype it dropped to a terminal-of-death screen. He got rather mad at me because I couldn't fix it. It was, however, a fresh install, so that may or may not have had something to do with it.

---

### Post by Sam Mills on 2013-05-04
> **stevedude said:**
> I love Ubuntu, but upgrade time can be a chore.
That's why I always fresh install while keeping my home folder from the previous install. From what I hear, upgrading can actually take longer than a fresh install. Reinstalling apps again is really not a big deal, as I can install all of them from one command in the terminal.

But I'm running Xubuntu 13.04, and it has been flawless, minus the hiccup I had with the internet connection. But that was because of Comcast and not Ubuntu's fault.

---

### Post by Sam Mills on 2013-05-04
> **Col936 said:**
> 
**The Ugly: **Came without a BUNCH of apparently important dependencies, one of which I had to download from the internet, as it wasn't available in the package registry for some reason. I couldn't install Google Chrome, Synaptic Package Manager, or ANY other packages without these.I was quite tempted to just go back to my old 12.10 and stay there until it officially came out.


That was probably because you didn't have all of the repos enabled which is an easy fix. Ask on the forums! The people here are wonderful about helping with problems.

---

