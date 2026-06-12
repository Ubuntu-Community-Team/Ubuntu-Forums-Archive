---
title: "Ubuntu 12.10- is it really this bad?"
date: 2012-11-17
forum: The Cafe
---

### Post by Ms. Daisy on 2012-11-17
[http://www.dedoimedo.com/computers/ubuntu-quetzal-high-end.html](http://www.dedoimedo.com/computers/ubuntu-quetzal-high-end.html)

I found this pretty terrible review of 12.10. Is everyone with nvidia graphics cards doomed to the same fate?

---

### Post by dino99 on 2012-11-17
not all nvidia users having trouble, but i'm one of them sadly, so using "nouveau" at time. :(

---

### Post by offgridguy on 2012-11-17
Thank you for this, very interesting article.

---

### Post by Carlos Araujo on 2012-11-17
the question is: is this a priority for canonical? for us, users yes.

---

### Post by Carlos Araujo on 2012-11-17
You "forgot" the AMD Dilemma and hybrid graphics are a hell for us, users.An analysis of its drivers amd would also welcome

---

### Post by Frogs Hair on 2012-11-17
12.10 has been my favorite release since 10.10. My mother board is Nvidia based and uses Nvidia graphics as well. I have the XFCE Session and Gnome shell running in addition to Unity.

I discovered additional drivers right away only because I modify my update settings after installation. When help is opened is not clearly stated how to install proprietary drives unless I'm missing something. I hope 13.04 runs as well 12,10.

---

### Post by Swagman on 2012-11-17
Seems he didn't do enough exploring.

Additional drivers are in the end tab of software sources now.

I'm running a GTX460 which was a reasonably high end card when I bought it. No probs here.

I did have the horrible low resolution "Ubuntu splash screen" bug but the Lucid fix is still valid.

I'm glad I upgraded to 12:10 now.

---

### Post by vasa1 on 2012-11-17
Came across this: How to Install Nvidia / AMD Graphics Drivers in Ubuntu 12.10 ([http://www.youtube.com/watch?v=ioMeSCoyYng](http://www.youtube.com/watch?v=ioMeSCoyYng)).

---

### Post by Paqman on 2012-11-17
> **Swagman said:**
> Seems he didn't do enough exploring.

Additional drivers are in the end tab of software sources now.


This.

I was also a bit stumped by this when I installed Quantal, there was nothing to tell you to head to Software Sources to find Jockey.

Anyway, I have Nvidia graphics and had no trouble getting the drivers installed, so the problem sounds like it's an isolated one. Hopefully the author of that article has filed a bug.

---

### Post by szymon_g on 2012-11-17
i have gf 560 ti, big problems under 64 bit ubuntu 12.10. 
to add an insult to the injury, myunity doesn't work on new unity.
so no, ubuntu 12.10 doesn't stay long on my computer.

---

### Post by cariboo on 2012-11-17
> **szymon_g said:**
> i have gf 560 ti, big problems under 64 bit ubuntu 12.10. 
to add an insult to the injury, myunity doesn't work on new unity.
so no, ubuntu 12.10 doesn't stay long on my computer.

If you actually wanted to use 12.10, there are 4 different nvidia drivers available, have you tried them all?

Myunity is no longer available, because the developer hasn't updated it to work with dconf, and hopefully when and if there is an updated version, it doesn't need gambas to be installed too.

---

### Post by weasel fierce on 2012-11-17
I'm on Kubuntu rather than Ubuntu but it's been okay here.

---

### Post by Jakin on 2012-11-17
> **weasel fierce said:**
> I'm on Kubuntu rather than Ubuntu but it's been okay here.

Same. Only downside of some ppa's that i had used in Precise aren't working for Quantal yet-- but thats the same on any Ubuntu, i'll have to wait for those repos to be made available.

---

### Post by Erik1984 on 2012-11-18
> **weasel fierce said:**
> I'm on Kubuntu rather than Ubuntu but it's been okay here.

Yep, driver version 304.51 and I don't notice any difference in performance compared to 12.04.

---

### Post by TenPlus1 on 2012-11-18
Added xorg-edgers ppa and using nvidia 310.19 driver, very fast and stable so far...

---

### Post by Esokra on 2012-11-18
I can confirm the title in terms of nvidia drivers. That is a big regression compared to 12.04, where the driver was easy and fast to install. I have the knowledge and ability to install the drivers manually, but still the behaviour sucks. Even an advanced user does not want to spend so much time on installing drivers.
What I experienced was the following: I went to software sources and installed the driver. At the next boot compiz did not even start, so I did not even get noveau (which is logical), only a low graphics mode. The reason was, that it missed depencies I had to add manually (see [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341))! That should definitely not be the case! I hope 13.04 will correct this.
As I am on 12.04 again, I did not fix everything, for example the spalsh screen was at low resolution, despite I got the drivers installed.

---

### Post by Erik1984 on 2012-11-18
> **Esokra said:**
> I can confirm the title in terms of nvidia drivers. That is a big regression compared to 12.04, where the driver was easy and fast to install. I have the knowledge and ability to install the drivers manually, but still the behaviour sucks. Even an advanced user does not want to spend so much time on installing drivers.
What I experienced was the following: I went to software sources and installed the driver. At the next boot compiz did not even start, so I did not even get noveau (which is logical), only a low graphics mode. The reason was, that it missed depencies I had to add manually (see [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-updates/+bug/1068341))! That should definitely not be the case! I hope 13.04 will correct this.
As I am on 12.04 again, I did not fix everything, for example the spalsh screen was at low resolution, despite I got the drivers installed.

The splash screen is beyond my understanding ;) When on 12.04 it magically fixed itself to display in high resolution but with 12.10 it's ugly as before. Well the splash screen isn't very important to me anyway but it doesn't look 'professional'.

---

### Post by Swagman on 2012-11-18
Follow the steps in this guide (I did). It sorts out the big ugly low resolution screen


[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

---

### Post by Docaltmed on 2012-11-18
I couldn't even get the 12.10 install USB to give me anything but hash on the display, so I pretty much dropped any idea of upgrading right there. I'll wait until the next time.

I'll tell you one thing for free, though. I will never, ever, in this lifetime or any other subsequent lifetimes, either freely or on point of death, buy any computer that has, contains, uses or was stored next to anything resembling an nVidia card.

---

### Post by Aaron Christianson on 2012-11-18
I can tell you in one word why this will be fixed:

Steam

---

### Post by alphacrucis2 on 2012-11-18
12.10 working great here with nvidia "experimental" driver.

---

### Post by gnusci on 2012-11-18
> **Ms. Daisy said:**
> [http://www.dedoimedo.com/computers/ubuntu-quetzal-high-end.html](http://www.dedoimedo.com/computers/ubuntu-quetzal-high-end.html)

I found this pretty terrible review of 12.10. Is everyone with nvidia graphics cards doomed to the same fate?

If you pay for the power of a NVidia card you may want to use their drivers:

[https://developer.nvidia.com/cuda-downloads](https://developer.nvidia.com/cuda-downloads)

---

### Post by neu5eeCh on 2012-11-18
> **Aaron Christianson said:**
> I can tell you in one word why this will be fixed:

Steam

  	 	 	 	 	 	   Touch[FONT=Times New Roman, serif]é.[/FONT]

---

### Post by Statia on 2012-11-19
> **Swagman said:**
> Seems he didn't do enough exploring.

Additional drivers are in the end tab of software sources now.



He shouldn't have to do exploring, there should be a straight-forward, easy to find, easy to use way to install those drivers, preferably during initial installation.

Secondly, the fact that jockey completely botches his install (fails to install nvidia driver without reverting to Nouveau)  is inexcusable.

It proofs once more that Canonical's QA is abysmal.

---

### Post by Statia on 2012-11-19
> **Statia said:**
> 
It proofs once more that Canonical's QA is abysmal.

And to prove my point further, from the same review:

> Second, I did get some updates, including the nvidia-common package. I let the system run these upgrades and         whatnot, and lo and behold, after the upgrade was complete, and following the next reboot, the desktop was         unusable. I was forced to remove the driver by hand, download the sources and         kernel headers AGAIN, install the nvidia driver, and then the Nvidia module only loaded with the count         reference of 40 rather than 44, as you would normally expect, and guess what, the top panel, the Dash and the         Launcher were not available, making the desktop completely and utterly borked. I do not know what went wrong,         but this is pure ****.

---

### Post by cariboo on 2012-11-19
> **Statia said:**
> He shouldn't have to do exploring, there should be a straight-forward, easy to find, easy to use way to install those drivers, preferably during initial installation.

Secondly, the fact that jockey completely botches his install (fails to install nvidia driver without reverting to Nouveau)  is inexcusable.

It proofs once more that Canonical's QA is abysmal.

So why not join the QA team and help with testing?

---

### Post by QIII on 2012-11-19
Much easier to throw stones at the guys trying to make the arrows sometimes.

---

### Post by pqwoerituytrueiwoq on 2012-11-19
i am using a 550 TI, i don't consider a 100-130 USD GPU low end
works just fine on 12.10
kernel 3.6.3;Nvidia 310.19;xubuntu 64bit;Unity stagging ppa;Xorg edgers ppa
been running 12.10 since beta 2

---

### Post by Statia on 2012-11-20
> **cariboo907 said:**
> So why not join the QA team and help with testing?

1) I am not a programmer
2) When an application crashes and I try to send in a report, apport-kde does not work:

[http://ubuntuforums.org/showthread.php?t=2038774](http://ubuntuforums.org/showthread.php?t=2038774)

(0 answers)

Pretty ironic in terms of QA, that a tool to report bugs has a bug that prevents it from working.

---

### Post by Statia on 2012-11-20
> **QIII said:**
> Much easier to throw stones at the guys trying to make the arrows sometimes.

If no one throws stones at them they won't notice their arrows are blunt and bent.

---

### Post by cariboo on 2012-11-20
@Statia, I'm not sure how kubuntu bug reporting works, but I'd suggest you might get more help if you post your problem on the [Kubuntu forums]("http://www.kubuntuforums.net").

Also as a tester, you don't need to be a programmer, any one can be a tester from new users to experienced users, and those in between.

---

### Post by QIII on 2012-11-20
Some testers are often deliberately NOT programmers, so they don't fall prey to the expectations programmers might.  

For a programmer, as for all humans, it is easy to feel like everything is working just fine because it works just as we expect it to -- we wrote it after all!

Testing occurs on many levels.

Pick up and nock arrow.  Bend the bow and loose it.  If the arrow doesn't fly true, take it back to the guy making the arrows and tell him what it ***is*** doing.

Don't just throw down the arrows, furrow your brow, bad mouth the arrow maker and throw rocks at him (from a distance.)

---

### Post by obxhdx on 2012-11-20
Once I got sick of this problem and bought an Intel on-board powered computer. Now I'm happy.

---

### Post by Favux on 2012-11-21
Actually this is a not too surprising outcome.

Since I don't follow testing closely I can only give you a casual observer's point of view.  We'd need some of the testers I'll mention below to fill things in.

There had been a dedicated group of testers for Ubuntu.  Unfortunately small in number but robust.  However coinciding about with Unity and Plymouth some disruption occurred.  Basically some testers felt they were being persecuted for what they felt were objective appraisals.  Their perception was that what were felt to be "negative" comments and those making them were being attacked by those who didn't appreciate any criticism, real or perceived, of Ubuntu.

I gather more got upset when they perceived an unfair attack on a gal from Britain and her two cents on Plymouth.  Apparently thought she had demonstrated expertise and should have been listened to not attacked and driven away.

Anyway a number of long time testers got alienated and left.  A fair amount of the collective tester community's expertise and collective memory was no longer available.  I think Quantal may have had the smallest testing community ever.  Since a common complaint has always been that Ubuntu dev.s didn't pay enough attention to the testers I honestly don't know how much an impact that had.  Maybe more than some thought given Quantal?

Ubuntu has a new community relations person and part of their job is interfacing with testers.  And maybe some folks have learned to be a little more judicious.  So hopefully the tester pool will increase and Quantal will be an aberrant blip.

---

### Post by Statia on 2012-11-21
Sounds familiar. I concede with a critical review and get accused of throwing stones and badmouthing.

---

### Post by Statia on 2012-11-21
> **cariboo907 said:**
> @Statia, I'm not sure how kubuntu bug reporting works, but I'd suggest you might get more help if you post your problem on the [Kubuntu forums]("http://www.kubuntuforums.net").



It seems the Kubuntu bug reporting is mostly the same as in Ubuntu, only with a KDE version of apport: apport-kde. The bug also does not seem to be Kubuntu specific, as someone on the forum here reports the same bug with Xubuntu.
The bug has been filed in Launchpad in August, but has not been assigned yet. Now I would would think that a bug that prevents receiving of bug reports should be high priority, but apparently not.

Thanks for the suggestion to post on Kubuntu forums, I posted there and will see what happens.

---

### Post by QIII on 2012-11-21
> **Statia said:**
> Sounds familiar. I concede with a critical review and get accused of throwing stones and badmouthing.

I'm not trying to be nasty.  I'm trying to make a point about when criticism is most effective.  Easy to point fingers after the fact.  More effective to actively affect change before release.

There is nothing wrong with a critical review.  In fact, such criticisms are absolutely necessary.  There was no question raised about the validity of your observation. A user should ***not ***have to go hunting for something as common as installing a driver.  (But remember that some of the questions about the effectiveness of installation fall to the OEM.)  Nobody said that was an unfair observation.  The question was about timing.

We who make arrows (no, I'm not an Ubuntu dev, but I am a software developer), testers and QA departments appreciate criticisms before release, not criticisms about our motivations and abilities after we've passed a faulty batch of arrows out.  Do you think we like passing out faulty arrows?  Your observations up front in testing during the development cycle would  be constructive.  That's the point of suggesting you become a tester. 

The former criticisms are constructive.  The latter are not.

If you don't want to volunteer to do it for Canonical directly, join the U+1 Team. It looks like I have less time to devote to testing RR than I did QQ.  You can pick up my slack.  Give Canonical both barrels during the development cycle.  Consider it continuous UAT prior to release.  We can have an effect on the final product.

By the way, don't assume I am deluded into believing Ubuntu is above criticism or  that I am an Ubuntu cultist or apologist. I use Fedora every bit as much  as I use Ubuntu.  Ubuntu is far from perfect.

---

### Post by dodjob on 2013-01-06
Hi there,
I don't want to be a disrespectful bad guy but I have used ubuntu for about 5 years now and I must be honest I never had so much problems with it since my upgrade to 12.10.
really, I mean the impossibility to run unity in failsafe graphics is quite a problem for a n00b like me. 
I have it running on two machines equipped with nvidia card gt220 and gt330m both fail to start x at any kernel update and yes I know it's missing some packets in order to install the nvidia drivers correctly .. but it's the case for month now!
Second my system freezed. this didn't happend for years O_o'
It's honestly the first time I hesitate to install it around me... a complete noob couldn't install the missing linux headers, update Grub with adding "text" to the command line and reinstall the drivers from the terminal.
another thing bothered me was the amazon adds. altough I understand the need to add such things I don't understand why they didn'tadd the possibility to directly search in the "software center" from there... 
Finally the overall system is really slower than the lts. I really regret my upgrade and again I'm a complete ubuntu fan and trully loved their direction until now.
This post may remain completly unreaded but it did help me to feel better :)
Hope to haven't hurt anyone with it though ^^
Gruß,
H.

---

### Post by Gremlinzzz on 2013-01-06
:popcorn:Ubuntu 12.10 gives you all the latest features, while Ubuntu 12.04.1 LTS comes with extended support.I would recommend Ubuntu 12.04.1 LTS.

That's between the 2 choices.
I prefer Xubuntu

---

### Post by Dr. C on 2013-01-06
I installed it on an older computer AMD Athlon 64 X2, 2GB RAM, Nvidia 7800 GS (the high end AGP Nvidia Graphics card) and it works great with the Nouveau driver and Unity.

---

### Post by cariboo on 2013-01-07
@dodjob, I have the same graphics adapter, GeForce 220, and I found that the only closed source graphics driver that worked for me was the nvidia-current-updates. The Nvidia drivers are a mess on 12.10, there are at least four different ones, that I know of.

---

### Post by dodjob on 2013-01-07
Yeah I did try them all. 
The only one which were allowing me to get the unity back (I see otherwise only my wallpaper or a black screen) are the "official" Nvidia's one in nvidia 310.19. I'm in X64, it could explain some things...
The nouveau drivers are way too slow/lagg like hell on my machine.
My thought were originally that until now I was able to confidently  recommand ubuntu to anyone (_all_ my familly is since 3 years using it)
For a noob point of view to be unable to run X is no more an inconvenience but a "broken" computer. That makes me really re-think about the direction cannonical wants to take.
Such things really intrigate me and i cannot think of any reason for it. I believed that any action of updating (not upgrading) shouldn't be able to harm your computer... specially since the pswrd query for it has been removed.
I may be already old school but I don't like the fact that a complete end-user can "break" his machine without entering a root password... just say'in ^^
Again, I don't want to be the bad guy and I will find solutions to all my problems here or after googling it.. that's just in this case really surprising me from a "ship-direction" point of view :)
Gruß,
H.

---

### Post by llanitedave on 2013-01-07
Trying to upgrade to Unity 12.10 from 12.04 borked my AMD/Nvidia computer pretty badly. It might have worked better with a clean install.

I'll give it another try with 13.04, but in the meantime, I've been enjoying the 12.10 versions of both Xubuntu and Kubuntu so much, I may not have the incentive to go back to Unity.

(But who am I kidding, of course I will!)

---

### Post by MrColdbird on 2013-01-07
I must say that 12.10 isn't as bad as people say it is...
However a bunch of components got pretty instable, why that is so - I don't know.

Also... the Nvidia Driver bundled with the OS is somewhat... sucky.
Which is why - especially for Optimus Hardware - one should really add the PPA for the updated nvidia-current package and install that via Recovery Mode (Root Terminal) first.

After doing that everything is golden... it auto uninstalls / blacklists the glitchy noveau driver and replaces it with the right one from Nvidia - uing bumblebee the GPU Power Management and Hotswap works great too.

Really got nothing to complain about other than the simple fact that on some Optimus Devices the graphical Installer is glitched, forcing me to use Lubuntu 12.10 Alternate Text Installer to get the OS onto my Harddrive.

While it may seem like a big deal if you don't know it, its actually pretty easy if you do know it...

Just avoid the graphical installer - install the right drivers / add the right ppa via Recovery Root Terminal and then install your Desktop System of choice (gnome-shell for me, aka. gnome3).

---

### Post by cariboo on 2013-01-07
> **dodjob said:**
> Yeah I did try them all. 
The only one which were allowing me to get the unity back (I see otherwise only my wallpaper or a black screen) are the "official" Nvidia's one in nvidia 310.19. I'm in X64, it could explain some things...
The nouveau drivers are way too slow/lagg like hell on my machine.
My thought were originally that until now I was able to confidently  recommand ubuntu to anyone (_all_ my familly is since 3 years using it)
For a noob point of view to be unable to run X is no more an inconvenience but a "broken" computer. That makes me really re-think about the direction cannonical wants to take.
Such things really intrigate me and i cannot think of any reason for it. I believed that any action of updating (not upgrading) shouldn't be able to harm your computer... specially since the pswrd query for it has been removed.
I may be already old school but I don't like the fact that a complete end-user can "break" his machine without entering a root password... just say'in ^^
Again, I don't want to be the bad guy and I will find solutions to all my problems here or after googling it.. that's just in this case really surprising me from a "ship-direction" point of view :)
Gruß,
H.

Not having to enter a password for updates only happens when you are updating already installed packages, if anything new needs to be installed, you will be asked for a password. If you really feel the need to enter a password before updating or installing, use synaptic, it still asks for a password when starting up. :)

I do agree that updates shouldn't break a system, but you have to put part of the blame on the user, for not reviewing what is to be updated, before clicking the continue button.

---

### Post by HansKisaragi on 2013-01-07
the only thing bad about 12.10,, even 12.04.. is nouveau

after install i always purge and blacklist it.. then update to 310 proprietary drivers

---

### Post by dodjob on 2013-01-09
> **cariboo907 said:**
> Not having to enter a password for updates only happens when you are updating already installed packages, if anything new needs to be installed, you will be asked for a password. If you really feel the need to enter a password before updating or installing, use synaptic, it still asks for a password when starting up. :)

I do agree that updates shouldn't break a system, but you have to put part of the blame on the user, for not reviewing what is to be updated, before clicking the continue button.
:D ah ah I will let you explain this to my 70 years old mother ^^
I like ubuntu to be rock solid and stupid proof for a everyday use. I mean I personally will succeed to get a solution to nearly all my problems or at least a workaroud. Real n00b end-users can't with 12.10. 
But I really don't want to argue :) I mean I am and will remain a little Ubuntu fan. just I liked the "easy-way" until now :)
Gruß,
H.

---

### Post by kurt18947 on 2013-01-09
> **dodjob said:**
> :D ah ah I will let you explain this to my 70 years old mother ^^
I like ubuntu to be rock solid and stupid proof for a everyday use. I mean I personally will succeed to get a solution to nearly all my problems or at least a workaroud. Real n00b end-users can't with 12.10. 
But I really don't want to argue :) I mean I am and will remain a little Ubuntu fan. just I liked the "easy-way" until now :)
Gruß,
H.

I agree with you.  12.10 isn't 'bullet-proof' by any means.  12.04 however is - at least for me.  12.10 isn't getting anywhere near SWMBO s machine.  It seems that the release after an LTS can be flaky.  10.04 was solid, 10.10 had its 'issues' at least for a while after being released.  There's nothing that mandates 'the latest and greatest'.

---

### Post by stinkeye on 2013-01-09
> **Viiral said:**
> the only thing bad about 12.10,, even 12.04.. is nouveau

after install i always purge and blacklist it.. then update to 310 proprietary drivers
Experiences vary.
The nouveau drivers work excellently with my nvidia GeForce GTX 550Ti in Quantal.

---

### Post by cariboo on 2013-01-09
I installed the 12.10 [Gnome-remix]("https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10") on my netbook a couple of days ago, and I'm quite surprised at the graphics performance. It doesn't seem any faster than Unity in day to day usage, but I can get acceptable performance when watching youtube videos at 720p, running Unity, videos at 720p, the audio and video stutters, or the video freezes, while audio continues, and generally it is just a pain, I set the default to 480p just to avoid any problems in Unity.

---

### Post by charlie99 on 2013-01-14
ref the excellent 'QA team history' posted earlier:

- I have been using various Ubuntii on several machines for a while..

- recently decided to resurrect an old HP / Compaq nx9010, went for Lubuntu 12.10 due to it being on LXF166 DVD along with some other useful stuff, and Lubuntu NOT having the Unity stuff...

- All distros (Ubuntu, Kubuntu, Xubuntu, Lubutu) would LiveBoot OK; but first install attempts for Lubuntu (from the live boot desktop icon) were crashing with a kernel oops; fairly specific error message about NULL POINTER reference.. call stack indicated issue was related to the specific Broadcom WiFi card in the machine (earlier version live boots on other machines with BCOM WiFi had always found / proposed the correct proprietary driver..).

- figured a work-around to that..got the instal to complete and downloaded the appropriate Broadcom card drivers.. added a couple of apps like Thunderbird & Firefox.. but now see that various 'Ubuntu internal errors' are occurring; including within apport....

- is it worth posting a bug over at Launchpad .. ??

---

