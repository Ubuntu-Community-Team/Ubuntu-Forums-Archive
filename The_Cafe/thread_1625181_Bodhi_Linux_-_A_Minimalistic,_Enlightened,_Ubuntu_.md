---
title: "Bodhi Linux - A Minimalistic, Enlightened, Ubuntu Desktop Distro"
date: 2010-11-18
forum: The Cafe
---

### Post by beastrace91 on 2010-11-18
I am working with a small team on an Ubuntu spin... Looking for testers!

[Bodhi Release Announcement]("http://jeffhoogland.blogspot.com/2010/11/announcing-bodhi-linux.html") 
[Bodhi About Page]("http://bodhilinux.com/about.html")

*Constructive* criticism and feedback is appreciated :D

~Jeff

---

### Post by cpmman on 2010-11-18
Downloading now - comments tomorrow.

---

### Post by Sporkman on 2010-11-18
Congratulations on your new venture. Unfortunately the data indicates it may an uphill battle:

[IMG]http://sporkforge.com/prmimg/04ce/fgf97edacb02945ci000500004c253020.png[/IMG]

Good luck nevertheless!

---

### Post by beastrace91 on 2010-11-18
Haha, I'm aware of that data.

I'm hoping the opposite effect of the lack of Enlightenment based distros in general works in my favor :)

~Jeff

---

### Post by BandD on 2010-11-18
looks very promising.  I've been menaing to try out Enlightenment for a while now...looks like the perfect excuse.  I'll download tongiht and install this weekend.  I'll report back then.

---

### Post by ikt on 2010-11-18
You say it looks beautiful but then show this:

[http://www.bodhilinux.com/images/frontsplash/bodhi2.png](http://www.bodhilinux.com/images/frontsplash/bodhi2.png)

That isn't beautiful, not compared to this:

[http://en.wikipedia.org/wiki/File:Snow_Leopard_Desktop.png](http://en.wikipedia.org/wiki/File:Snow_Leopard_Desktop.png)

---

### Post by NightwishFan on 2010-11-18
Beauty is in the eye of the beholder. How is that even relevant? I will also say I dislike OSX from bottom to top. The attention to detail is nice however... >_<

Anyway, good job. If anyone has a use for this, the trouble is maintaining it. :)

---

### Post by ironhoof on 2010-11-19
OpenGEU used to be Ubuntu based. I however like this, I will give it a try too (being a huge enlightenment lover). The fact it also just went 2nd BETA also further pleases me. It should be 1.0 Final by the end of December. That is however the EFL, the DE/DS/WM
will then be finished some time after that. :)

With a custom distro though, you can choose when to upgrade the environment though. I use E17 from compile -> install.

I like seeing that someone else is giving this a go!

---

### Post by czr114 on 2010-11-19
> **ikt said:**
> You say it looks beautiful but then show this:

[http://www.bodhilinux.com/images/frontsplash/bodhi2.png](http://www.bodhilinux.com/images/frontsplash/bodhi2.png)

That isn't beautiful, not compared to this:

[http://en.wikipedia.org/wiki/File:Snow_Leopard_Desktop.png](http://en.wikipedia.org/wiki/File:Snow_Leopard_Desktop.png)

Beauty is in the eye of the beholder. To someone looking for a light desktop environment with a focus on productivity, the first can be beautiful. That second shot  can just as easily be described as busy, intrusive, and toyish.

---

### Post by ironhoof on 2010-11-19
TESTED

Ok, tried it, I have a few things I noticed...

Its decent, however the main thing I know people will not like is the left click context menu.

It is common, and people mention it often in E17, but most do not try to change this setting on their own, and don't know the setting even exists.

In the settings, and mouse bindings you can change the mouse buttons around. I would suggest that first.

I also say adding the system tray e-module. <-important


I see your using the taskbar e-module already, good idea! 

Other than that, it is well on its way!

---

### Post by Rasa1111 on 2010-11-19
love the name! <3 :)

will check it out over the weekend. :)
 Nice work.

---

### Post by BandD on 2010-11-20
Tried out the live environment just now.  I'm impressed with what you've put together so far.  This is my first time using an Enlightenment distro and it's pretty nice.  There are a couple of things I ran into in my short test.  

The main problem was that I was unable to connect to the internet.  On the first boot, I was able to associate with my WPA encrypted network, but couldn't get outside the local net (I was simulaneously borwsing the net on my other computers conencted to the same network).  The only thing I was able to access was the router's admin page (no servers running currently in house).  I tried rebooting and was never again able to associate with my network.  

I was also able to crash the live environment a few times.  Probably a graphics error as it shot me to tty1.  

Other minor things were that when I was browsing the system settings menu it became VERY difficult to read the sub menus with the current theme.  The sub menus pop-up on top of the main menu and the lines between the two become blurred...

I'm going to go ahead and install it on a small partition now and see if I have better luck with a true install.


=====UPDATE=====

Installed.  It certainly boots FAST!  But now it doesn't even recognize my wireless adapter.  No wireless networks found. It's still a good piece of work and I look forward to seeing where this project goes.  I haven't gotten it to crash yet either, so it seems relatively stable.

---

### Post by cpmman on 2010-11-20
Live cd OK but install can't find internet connect?

---

### Post by kamon8124 on 2010-11-20
I'm a hard core gnome user, but of all the alternatives, E17 has always been most intriguing to me. 
The few times I decided to take the plunge and install the E17 WM/DM in Ubuntu, I ran into such massive problems that in each instance I gave up and rolled back to my "comfort zone". 
This is why I'm so excited to give this distro a try. The same, comfortable Ubuntu base, rolled together with E17 by someone who actually knows what they're doing :D
I'm going to install this in virtual box as soon as I get home and report back.

---

### Post by TiBaal89 on 2010-11-20
I have zero knowledge/experience with Enlightenment... the desktop or otherwise, I'm sure.  I'll have to try it out. :D

---

### Post by beastrace91 on 2010-11-20
The Enlightenment network manager has been giving *lots* of people headaches. It will be traded out for the gnome network manager in the 0.1.1 disc - it is pre-installed on the 0.1.0 disc. To load it run the following in terminal -

```
ck-launch-session
nm-applet
```

And see if that can connect to your wireless network. Also I am aware that the audio is massively foobared at the moment - working on correcting that for the next release next week.

Find any other issues please let me know in this thread or via email (fastest) JeffHoogland at Linux dot com

Cheers,
~Jeff

---

### Post by cpmman on 2010-11-20
Brill - thanks mate - online and happy! :)

---

### Post by andymorton on 2010-11-20
> **beastrace91 said:**
> I am working with a small team on an Ubuntu spin... Looking for testers!

[Bodhi Release Announcement]("http://jeffhoogland.blogspot.com/2010/11/announcing-bodhi-linux.html") 
[Bodhi About Page]("http://bodhilinux.com/about.html")

*Constructive* criticism and feedback is appreciated :D

~Jeff


I'm downloading it now. I'll install and give it a testing tomorrow when I get home. :)

---

### Post by cpmman on 2010-11-20
Like the desktop switch. Where's the compose key set?

---

### Post by matt_symes on 2010-11-20
Hi

I have just downloaded it an have tried it in virtual box. 

First attempt did not go well and it  kept crashing everytime i tried to select something on the menu or open of the three applications at the bottom.

Second attempt much better. Connected to my wireless network with no problems and i could get on the internet. It did not crash, loads quickly and has a nice look and feel.

I really do not like the left click for menu and i would default to right click.

I will have a longer play when i get the time and give you some real feedback.

Kind regards.

---

### Post by BandD on 2010-11-20
I just came across something else.  Being totally new to Elightenment, I was messing with the different profiles and clicked on defualt.  I went through the process of slecting the new defuat settings only to realize that I couldn't get back to the very pretty defualt that Bodhi comes with.  I don't know if there's a way to make the defualt Bodhi theme it's own choice in the Enlightenment profile, but it would be nice to be able to easily get back to it if you want to.

The nm-applet thingy did the trick!  Thanks.

---

### Post by beastrace91 on 2010-11-20
Right clicking on the desktop by default brings up the "favorites" menu, which is empty by default.

By compose keyset do you mean key bindings? If so it is under *input* in the settings.

~Jeff

---

### Post by beastrace91 on 2010-11-20
> **BandD said:**
> I went through the process of slecting the new defuat settings only to realize that I couldn't get back to the very pretty defualt that Bodhi comes with.

Ahh! That is a fantastic idea. I am half done uploading 0.1.1 now, 0.1.2 will include a "bodhi" profile by default.

~Jeff

---

### Post by cpmman on 2010-11-20
> **beastrace91 said:**
> Right clicking on the desktop by default brings up the "favorites" menu, which is empty by default.

By compose keyset do you mean key bindings? If so it is under *input* in the settings.

~Jeff

I  normally set the menu key to be the compose key for things like euro symbol (C + =) and Spanish (n + ~) and have not worked out how to do it in Bodhi.

---

### Post by NormanFLinux on 2010-11-20
The best Enlightenment - e17 implementation is currently PCLOS, which uses the Synaptic package manager for all the software. Its as beautiful an OS as you could have in Linux.

There is no "official" e17 version in the Ubuntu universe yet.

---

### Post by beastrace91 on 2010-11-21
> **NormanFLinux said:**
> The best Enlightenment - e17 implementation is currently PCLOS, which uses the Synaptic package manager for all the software. Its as beautiful an OS as you could have in Linux.

You see this -

[img]http://www.pclinuxonline.com/wp-content/uploads/2010/10/blackwood-theme6.png[/img]

Feels cluttered and does not look nice to me in the slightest - to each their own though I guess.

> **NormanFLinux said:**
> There is no "official" e17 version in the Ubuntu universe yet.

That is one of the many reasons I am working on Bodhi - I feel Ubuntu has *much* better support and usability than PCLinuxOS ever has/will. But again this is purely subjective.

~Jeff Hoogland

---

### Post by Rasa1111 on 2010-11-21
I agree that screenshot does not look very nice, Jeff. 

But this one looks decent~ [except for the yucky icons]. lol
Same OS. 
[IMG]http://i54.tinypic.com/2vnpeo6.png[/IMG]

Never heard of it until now.
 I like the "Linux for extraterrestrials" thing. lol :)

 I just finished the Bodhi download,
 soon as I get some tea on, 
it's time for some enlightenment. lol 

:)

---

### Post by unknownPoster on 2010-11-21
> **NormanFLinux said:**
> The best Enlightenment - e17 implementation is currently PCLOS, which uses the Synaptic package manager for all the software. Its as beautiful an OS as you could have in Linux.



That's subjective and shouldn't be a reason to try to discourage someone from starting a project.

---

### Post by matt_symes on 2010-11-21
Hi 

I seem to be getting this alot, not all the time though (see screenshot). It happens when i try to start any application or select any context menu option. I am still running through virtual box. When it happens i cannot shutdown and have to kill it. At next reboot it is telling me there is no bootable media, a consequence of the forced shutdown i suspect.

Kind regards

---

### Post by beastrace91 on 2010-11-21
@Matt Go grab the 0.1.1 disc I just uploaded, it is compiled with a newer version of Enlightenment (among other things). From that point on you can just update enlightenment via apt-get.

I will be compiling E updates and pushing them to the bodhi repo a few times a month.

Cheers,
~Jeff

---

### Post by Sean Moran on 2010-11-22
Thanks very much mate.  I even started a thread two days ago looking for a nice little version of Ubuntu that would pay more attention to the time it takes to download 336 MB than the capacity of a 700Mb CD-ROM, and you've already done it.

I swapped out Enlightenment for the standard GNOME desktop. and have increased the size of the ,iso from 336 to 389, but can probably take out some of the extra stuff over the week to bring it back down to around 350, which is the ultimate goal.

Thanks for Bodhi.

---

### Post by beastrace91 on 2010-11-22
If you are installing gnome, I know the packages you can tear out of the system right off the bat are -

ecore, edbus, edje, eet, efreet, eina, eio, elementary, embryo, enlightenment, evas, places, shellementary, taskbar, tclock, and lxdm.

Odds are there are a few others as well, but those are the ones I know off the top of my head.

Cheers,
~Jeff

---

### Post by The Real Dave on 2010-11-22
Looks nice :) Grabbing it now, torrent is downloading at a crazy speed :)

---

### Post by beastrace91 on 2010-11-22
> **The Real Dave said:**
> torrent is downloading at a crazy speed :)

Yep - one of my buddies has a seed box hosting it that uploads at like 2megs/second :D

~Jeff

---

### Post by cpmman on 2010-11-22
> **beastrace91 said:**
> 
By compose keyset do you mean key bindings? If so it is under *input* in the settings.

~Jeff

I might be thick but I still cannot find how to set the menu key as the "compose" key.

---

### Post by beastrace91 on 2010-11-22
Should be able to press "add binding" and then press the menu key.

~Jeff

---

### Post by cpmman on 2010-11-23
> **beastrace91 said:**
> Should be able to press "add binding" and then press the menu key.

~Jeff

Three times done that but there is nothing to assign the "compose" function to the key. On each occasion (three separate boots) I gave up looking and went back to Firefox to see if there is any alternative method of key assignment.  I do not know if it was coincidence that after about five more minutes the desktop crashed and threw me out to a tty1 login screen.

Compaq CQ61 4 Gb
Radeon 4200
sda10 (several os installs)

---

### Post by beastrace91 on 2010-11-23
Did you take note of what you where doing when Enlightenment crashes out? Also just so you know - if you read the crash message it gives it says you can press "f1" to recover. This allows Enlightenment to reload while keeping all your applications loaded with 0 data loss. Only DE that can crash and not affect anything you are doing as it reloads ;)

I am not quite sure what you mean by set menu to "compose" is that a command you would normal have run when you press the menu key?

~Jeff

---

### Post by cpmman on 2010-11-23
Yes - each time I was in Firefox using a google tab to search for alternatives.
There was no crash message - simply a tty1 with login request - no error message. (not checked the logs - shall do and report back tomorrow - turned midnight here)

In all other distros I have tried the "System - Preferences - Keyboard - Layouts - Options - Compose key position" allows a choice of keys.

---

### Post by cpmman on 2010-11-24
Same result - no error message on screen and non I can attribute to this in logs.

Shall await next week's revision.

---

### Post by BandD on 2010-11-24
I went ahead and grabbed 0.1.1 last night.  Crashed the livecd twice not really doing anything.  But eventually got it installed (so now I'm back to the nice bodhi theme again!).  Seems good so far.  Haven't really pushed it at all yet.  

How can I make enlightenment use the nm-applet by defualt on startup?  I imagine I can jsut write a simple bash script or some such, but where to I stick it or how do I tell enlightenment to run a certain script on start up?

Also, one thing that seems slightly quirky to me is that when I open firefox it opens to less than full screen horizontially but full screen vertically.  So what I see is about a two inch strip of desktop (complete with upper panel) to the right side of firefox.  I think it would be better to either have firefox open full screen or constrained below the panel.

---

### Post by bressix on 2010-11-25
Jeff, it's a nice job.
I'm trying to use de drawer module, but it is unavailable in your repository.
And if i try to use the official repository, it's crash.

---

### Post by beastrace91 on 2010-11-26
Ahh, 

Yes do *not* mix and match packages from the "official" enlightenment repo and the Bodhi one. The official one is months out of date (where is Bodhi is within a few days of the SVN)

I will add compiling the drawer module to my to do list (along with weather) are there any others you would like to request I push out to the repo?

Cheers,
~Jeff

---

### Post by matt_symes on 2010-11-26
0.1.1 is alot more stable on my machine. Well done. What changes did you make?

---

### Post by beastrace91 on 2010-11-26
> **matt_symes said:**
> 0.1.1 is alot more stable on my machine. Well done. What changes did you make?

The largest change was trading out SLiM for LXDM. Enlightenment didn't play well with however SLiM was starting the window manager.

~Jeff

---

### Post by luckylucky on 2010-12-03
Jeff,

Congratulations on your venture with Bodhi.  Sure, there are plenty of spin off distros, but yours with an Ubuntu backing plus ENLIGHTENMENT is a project that I'll be watching with a keen eye.  

I've downloaded the ISO and am trying it in vbox... [COLOR="Red"]How do you install it?[/COLOR]

*** SUGGESTION ***

I've played with a number of smaller distros for netbooks (and wished for something good with enlightenment).

I think if you were to use Peppermint OS as the base to build on top of would make a great OS with enlightnment.  So far Bodhi doesn't seem to have any meat in it - of course it is just in alpha.


Anyhow, I do see a significant opportunity for a cool distro to evolve here.  I'll be keepin' an eye out on this one.



************************** 

Another question - what would it take to have this grow to become a viable distro?

---

### Post by beastrace91 on 2010-12-04
Luckylucky,

The installer is [kinda buried]("http://www.bodhilinux.com/getsupport/forum/viewtopic.php?f=12&t=5") at the moment, but it is there. For the next release I am going to put it in an easier spot to find methinks.

I thought about using Peppermint or something along those lines as a base, but minimalistic is my over all goal. So I figured going with a minimal CD as a base made the most sense over all.

I am not quite sure what it takes to be a viable distro... This is really just a pet project of mine (and some others) that I have been installing for friends so they can play with Enlightenment. If it takes off great :) if not... Then I will still be here providing updates for it to those that do use it. If you have ideas on how to make it take off, please let us know. Myself and my team are always open to input.

~Jeff

---

### Post by beastrace91 on 2010-12-16
Our forth alpha release (0.1.3) is now public. Let us know what you think!

[img]http://4.bp.blogspot.com/_1i7EX7a2ELY/TQqfjOvHmQI/AAAAAAAAAeE/6zeSUNDaAJI/s1600/bodhi.png[/img]

~Jeff

---

### Post by matt_symes on 2010-12-16
Downloading now.

Will check it out tomorrow.

---

