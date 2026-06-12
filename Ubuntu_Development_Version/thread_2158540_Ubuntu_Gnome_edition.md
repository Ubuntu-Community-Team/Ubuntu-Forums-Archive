---
title: "Ubuntu Gnome edition"
date: 2013-06-29
forum: Ubuntu Development Version
---

### Post by Chanath on 2013-06-29
Have you guys checked up the Gnome edition alpha? I find it working quite well in the GS session, but is quite weird in the "new" Gnome-Classic mode. The top panel is a mixture of Gnome shell panel and the Classic panel. You cannot right click it with Super+Alt pressed together to change or add anything. The bottom panel has the same problems.

I installed Gnome-shell in Ubuntu, and the GS version is better--quite responsive--than in the Ubuntu Gnome edition. But, there too is a problem in the Installed Gnome Classic panel. You can right click, but nothing can be added. Anyway, these are maybe teething problems.:)

---

### Post by Cavsfan on 2013-06-30
I installed it yesterday. At first I thought my monitor was going out with the new colors of the login screen. 
Then after installing the xswat-edgers Nvidia driver, compiz and cairo dock things changed. When compiz started, both top and bottom panels disappeared.
I even set compiz on a 10 second delay with a script and same thing happens. None of the minimize, restore or close buttons work on any windows at present.
This is the same logging into Gnome and Gnome Classic.

If it weren't for Cairo Dock I would have no access to anything. Then when I tried to customize the grub menu; at bootup grub completely disappeared and booted directly into windows.
I had to mount a live cd and do a grub recovery on another install. I do not recommaned any grub menu customization at this point with Saucy.

Perhaps some more tweaking will help. :)

---

### Post by Chanath on 2013-06-30
It was much better to install Gnome shell to the stock Ubuntu, than downloading the Ubuntu Gnome-Edition. Even the Gnome-panel (Gnome Flashback) installation works quite well than to strange Gnome-Classic already installed in that. As far as Ubuntu repos are offering Gnome shell, I'd install it the future and won't bother to download the Gnome-Edition. To experience the Gnome shell, you just don't need an Ubuntu Gnome edition at all.

---

### Post by Cavsfan on 2013-06-30
Taking compiz out by disabling startup fixed the min, restore, close buttons and brought the top and bottom panels back. But now no cube or cool stuff and Cairo Dock appears to hide behind the bottom panel. :(

---

### Post by xeizo on 2013-06-30
> **Chanath said:**
> It was much better to install Gnome shell to the stock Ubuntu, than downloading the Ubuntu Gnome-Edition. Even the Gnome-panel (Gnome Flashback) installation works quite well than to strange Gnome-Classic already installed in that. As far as Ubuntu repos are offering Gnome shell, I'd install it the future and won't bother to download the Gnome-Edition. To experience the Gnome shell, you just don't need an Ubuntu Gnome edition at all.

Yes, I did the same, tried Ubuntu Gnome-Edition first which barely worked for anything and then installed plain Ubuntu from the same daily-day and installed gnome-shell in it which worked excellent. Still running it fully updated with daily-kernel and with gnome3, gnome3-staging, gnome3-testing, xorg-edgers, pulseaudio-testing and alsa-testing - everything is smooth and works just fine  :-)

---

### Post by Cavsfan on 2013-06-30
> **Chanath said:**
> It was much better to install Gnome shell to the stock Ubuntu, than downloading the Ubuntu Gnome-Edition. Even the Gnome-panel (Gnome Flashback) installation works quite well than to strange Gnome-Classic already installed in that. As far as Ubuntu repos are offering Gnome shell, I'd install it the future and won't bother to download the Gnome-Edition. To experience the Gnome shell, you just don't need an Ubuntu Gnome edition at all.

I think I will do that myself. Did you get a working startup sound? It aggravates me unless I hear something when I login and I have spent too much time getting that to work without any success.

---

### Post by mc4man on 2013-06-30
> **Cavsfan said:**
> I think I will do that myself. Did you get a working startup sound? It aggravates me unless I hear something when I login and I have spent too much time getting that to work without any success.

you can get the old login music easily (thought they picked a new one, have never heard...

open up startup applications > add
for command use 
```
/usr/bin/canberra-gtk-play --id="desktop-login"
```

Name it as you please

---

### Post by Cavsfan on 2013-06-30
> **mc4man said:**
> you can get the old login music easily (thought they picked a new one, have never heard...

open up startup applications > add
for command use 
```
/usr/bin/canberra-gtk-play --id="desktop-login"
```

Name it as you please

Thanks mc4man for that! I tried that a bunch of times on the new gnome edition and nothing would work. The desktop-login file did not exist so I copied it from Raring and it still did not work.
I just installed the daily iso and have the sound back to working. But, that white on the middle of the top and bottom panels is back. I have gnome classic and gnome fallback.
Gnome classic doesn't appear to work as the panels do not appear and cairo dock does not appear either, so I am using fallback. It works except for the white middle panels.

---

### Post by Chanath on 2013-07-03
Here is the screenshot of the Gnome-classic-session.

 [ATTACH=CONFIG]244352[/ATTACH] 

Notice the top panel is the same Gnome shell panel with additional Applications & Places. The bottom panel cannot be right clicked and autohidden.

---

### Post by sgage on 2013-07-03
I installed Ubuntu Gnome from the 7/1 daily build, and it worked perfectly from the get-go. Installing regular Ubuntu and then adding GS from the repos certainly works, but then you have all sorts of Unity cruft hanging around. I only want simple Gnome Shell, not Unity, Compiz, what have you.

---

### Post by markbl on 2013-07-03
> **sgage said:**
> I installed Ubuntu Gnome from the 7/1 daily build, and it worked perfectly from the get-go. Installing regular Ubuntu and then adding GS from the repos certainly works, but then you have all sorts of Unity cruft hanging around. I only want simple Gnome Shell, not Unity, Compiz, what have you.
All you save is a bit of disk space. In this era of humongous disk sizes, who cares about that? Adding gnome 3/shell via a simple "apt-get install gnome-shell" to a regular ubuntu install gives you the option of selecting either Ubuntu (Unity) or GNOME (GNOME Shell) at the login screen. NOTE: if you log in using GNOME then you do not start any Unity or Compiz software at all, and vice-versa logging in with Unity. People seem confused about this. I personally have never seen the point of the Ubuntu GNOME ISO as all it gives you is NO option to log in and use Unity. I prefer GNOME Shell, but like trying Unity occasionally. My terabyte disk can afford the extra few megabytes to hold the Unity/Compiz files!

---

### Post by Chanath on 2013-07-03
> **sgage said:**
> I installed Ubuntu Gnome from the 7/1 daily build, and it worked perfectly from the get-go. Installing regular Ubuntu and then adding GS from the repos certainly works, but then you have all sorts of Unity cruft hanging around. I only want simple Gnome Shell, not Unity, Compiz, what have you.

The whole idea of Ubuntu is to have Unity, so it is better to have the GS experience *additionally* together with Unity. The Gnome classic session works better in Ubuntu, rather than in the Ubuntu Gnome edition. You can see what I get in the Gnome-Edition in the screenshot. We have the same repos for all Ubuntu derivatives, but the stock Ubuntu with other sessions installed works much better and give us more choice. In the Unity DE, all I want is an ability to autohide the top panel. As it cannot be hidden and I need the extra space, I move to GS or Gnome classic mode for the given application. In full screen applications, Unity is no bother.

I have installed Unity Next--I can only check it out--and awaiting its launch, then the fascination with GS would drop.:)

---

### Post by Harry33 on 2013-07-04
> **Chanath said:**
> The whole idea of Ubuntu is to have Unity, so it is better to have the GS experience *additionally* together with Unity. ...:)

This is surely a matter of an opinion, not a general truth, not at all.
I see the idea of Ubuntu to be much else.
We have had Ubuntu distro a long time before anyone had ever heard about Unity DE.
Unity is simply put only a modified Gnome DE, nothing else.

Installing Unity packages does not make Gnome-Shell work any better nor the Flashback either.
If the Flashback does not work well on some setups, something else is wrong.

---

### Post by Chanath on 2013-07-04
> **Harry33 said:**
> This is surely a matter of an opinion, not a general truth, not at all.
I see the idea of Ubuntu to be much else.
We have had Ubuntu distro a long time before anyone had ever heard about Unity DE.
Unity is simply put only a modified Gnome DE, nothing else.

Installing Unity packages does not make Gnome-Shell work any better nor the Flashback either.
If the Flashback does not work well on some setups, something else is wrong.

Ubuntu was there with all the DEs, and one day Ubuntu introduced Unity, and it had come to stay with Ubuntu, the default distro of Ubuntu. *All others are derivatives.* The next Unity probably would be Unity Next. The idea of Ubuntu is to give a distro to millions, and they had succeeded in introducing the Unity DE. The people, who actually use Unity don't even complain. Anyway, I was better off in installing Gnome shell and Gnome panel from the repos in Ubuntu, than having an installed version of Ubuntu Gnome edition. Gnome 3 and Compiz is under Ubuntu, and the DE is Unity. When you apt-get install gnome-shell, you get a dual distro. When you apt-get install gnome-panel, you get a triple distro. And, no hitches at all.:)

---

### Post by Stinger on 2013-07-04
The Ubuntu brainwash campaign seems to work. the more times You keep repeating terms like Unity, the more people think that's the universal truth and what Ubuntu is all about.
Ps.
I don't know what Unity exactly is but I know for sure it's not a DE, Unity is just another shell on top of the GNOME app's, like Gnome-shell and Cinnamon, .
Just try to remove all the GNOME applications and see what's left. Just another empty shell ( maybe that's exactly what Unity is ).

---

### Post by sgage on 2013-07-04
> **Chanath said:**
> Ubuntu was there with all the DEs, and one day Ubuntu introduced Unity, and it had come to stay with Ubuntu, the default distro of Ubuntu. *All others are derivatives.* The next Unity probably would be Unity Next. The idea of Ubuntu is to give a distro to millions, and they had succeeded in introducing the Unity DE. The people, who actually use Unity don't even complain. Anyway, I was better off in installing Gnome shell and Gnome panel from the repos in Ubuntu, than having an installed version of Ubuntu Gnome edition. Gnome 3 and Compiz is under Ubuntu, and the DE is Unity. When you apt-get install gnome-shell, you get a dual distro. When you apt-get install gnome-panel, you get a triple distro. And, no hitches at all.:)

I simply do not like Unity, Compiz, the whole paradigm of Unity. I like Gnome Shell. I use Ubuntu because of the ease of installation and the up-to-date and comprehensive repos. Ubuntu Gnome is the perfect solution for creating the system that I want.

As far as adding GS to stock Ubuntu and having it run better than GS in Ubuntu Gnome, I simply don't buy it. Something else was going on there...

---

### Post by pulpo69 on 2013-07-04
i like the gnome-shell. it's fullfilling all my needs on the desktop and gives me a good workflow. i tried unity, but i didn't like it. maybe unity is fine on a tablet, but on a "traditional" pc gs is perfect for me.

---

### Post by xeizo on 2013-07-04
> **sgage said:**
> I simply do not like Unity, Compiz, the whole paradigm of Unity. I like Gnome Shell. I use Ubuntu because of the ease of installation and the up-to-date and comprehensive repos. Ubuntu Gnome is the perfect solution for creating the system that I want.

As far as adding GS to stock Ubuntu and having it run better than GS in Ubuntu Gnome, I simply don't buy it. Something else was going on there...

Well, vanilla Ubuntu probably has much more QA than Ubuntu Gnome which may explain why it is a more stable base even for installing gnome-shell on it. That is as of now, the quality of Ubuntu Gnome will much likely improve upon time .... I've tried gnome-shell in current Debian, it was very buggy I think Saucy + gnome-shell is much more polished even if it is alpha-software

---

### Post by sgage on 2013-07-04
> **xeizo said:**
> Well, vanilla Ubuntu probably has much more QA than Ubuntu Gnome which may explain why it is a more stable base even for installing gnome-shell on it. That is as of now, the quality of Ubuntu Gnome will much likely improve upon time .... I've tried gnome-shell in current Debian, it was very buggy I think Saucy + gnome-shell is much more polished even if it is alpha-software

Not sure how QA has anything to do with it, since Ubuntu Gnome is basically a metapackage using nothing but the same exact packages as Ubuntu uses.

As far as current Debian, I am running GS in it right now, and it works beautifully. Debian stable is like that. No surprises, no bugs, no conflicts, no problems. Just slightly older software if that sort of thing is critical to you.

To say that Saucy+GS is much more polished strikes me as absurd.

---

### Post by Cavsfan on 2013-07-04
For the half day I had that Gnome edition installed. I noticed it was like no Ubuntu I have ever seen before. Everything about it was different.

I tried to customize the grub menu and lost grub altogether. It booted straight into WIndows 7. Had to mount a live cd and recovery that way.

---

### Post by sgage on 2013-07-04
> **Cavsfan said:**
> For the half day I had that Gnome edition installed. I noticed it was like no Ubuntu I have ever seen before. Everything about it was different.

I tried to customize the grub menu and lost grub altogether. It booted straight into WIndows 7. Had to mount a live cd and recovery that way.

That's odd, because it's exactly the same grub, handled exactly the same way. There is nothing about U-G that has anything to do with grub.

I've never experienced anything like what some of you are reporting, and I install a new build of U-G once a week. The only material difference (besides no Unity) is that it uses GDM instead of lightdm. It's never caused me any problem.

---

### Post by markbl on 2013-07-04
> **sgage said:**
> 
As far as current Debian, I am running GS in it right now, and it works beautifully. Debian stable is like that. No surprises, no bugs, no conflicts, no problems. Just slightly older software if that sort of thing is critical to you.
Slightly older? I just checked now and the current version of GNOME Shell in debian stable, testing, and unstable is 3.4. That's the problem trying to use GNOME on Debian, the packages are ancient.

I see a strong opportunity for a debian based distro based on current GNOME 3 packages. I think Ubuntu GNOME is good work, but ultimately it will become too hard to develop and maintain against the Ubuntu base, particularly with the friction and deviation occurring between GNOME/Ubuntu (i.e. between Red Hat and Canonical realistically). Trying to merge GNOME stuff against changes due to Mir/Wayland, compiz/mutter, upstart/systemd, etc. It's just TFH.

---

### Post by Stinger on 2013-07-04
> **markbl said:**
> 
I see a strong opportunity for a debian based distro based on with current GNOME 3 packages. I think Ubuntu GNOME is good work, but ultimately it will become to hard to develop and maintain against the Ubuntu base, particularly with the friction and deviation occurring between GNOME/Ubuntu (i.e. between Red Hat and Canonical). Try to merge GNOME stuff against changes due to Mir/Wayland, compiz/mutter, upstart/systemd, etc. It's just TFH.

You have some quite valid points there, Ubuntu-GNOME must be allowed to have it's own upstream Gnome version, must be allowed to use different low level components like upstart and Wayland etc. 
But I'm afraid that's not gonna happen in near future, there is just to many trade off's being tied to the Ubuntu base and the Gnome components in it.
A Debian based distro with the Upstream Gnome version could be a better approach, I agree :D 

Have any of you tried Fedora 19 ? 
It's IMHO the best implementation of the Gnome 3.8 DE, and I'm really really sorry that Ubuntu can't deliver anything that even comes close to this.

Of course Ubuntu has it's large software base ( thanks to Debian ) and other 'nice to have' thingies but that doesn't make up for all the other trade off's.

---

### Post by jbicha on 2013-07-04
> **Stinger said:**
> 
Have any of you tried Fedora 19 ? 
It's IMHO the best implementation of the Gnome 3.8 DE, and I'm really really sorry that Ubuntu can't deliver anything that even comes close to this.

Could you give some specifics about how Fedora 19 is a better implementation of GNOME 3.8 than Ubuntu GNOME 13.10? I think Fedora and Ubuntu GNOME are very similar. Ubuntu GNOME even includes a few things that Fedora 19 doesn't (Tweak Tool, dconf Editor, and the new GNOME Classic).

---

### Post by Stinger on 2013-07-04
@jbicha
Well so far it's just an opinion but one thing that springs to mind is GNOME PackageKit. 
I've tried Gnome 3.8 from Ubuntu-GNOME, OpenSuse with Gnome 3.8 and Fedora 19.
On my list Fedora tops, Ubuntu-GNOME comes second and OpenSuse third.
I could dig a little deeper if you think Ubuntu-GNOME could benefit from it, else I see no point in doing so.

---

### Post by mc4man on 2013-07-04
> **Stinger said:**
> 
Have any of you tried Fedora 19 ? 
It's IMHO the best implementation of the Gnome 3.8 DE, and I'm really really sorry that **Ubuntu can't deliver anything that even comes close to this.**
.
Fairly strong, definitive statement

> **Stinger said:**
> @jbicha
Well so far it's just an opinion but one thing that springs to mind is GNOME PackageKit. 
I could dig a little deeper if you think Ubuntu-GNOME could benefit from it, else I see no point in doing so.
Pretty weak response, would of thought you could do better without any 'digging deep'

---

### Post by Chanath on 2013-07-05
@Jbicha & others 

You might notice the screenshot I've posted in #9. The Gnome-classic in Ubuntu Gnome Edition is somewhat strange, with the top panel acting like the GS top panel, and the bottom panel cannot be right-clicked at all. I have stock Ubuntu saucy and I've installed GS and G-classic (called flashback). There is ano problem in using GS & the G-flashback, they work as they should be in their own sessions. But, in Ubuntu Gnome Edition, the gnome-classic session in muddled up. I know it is Ubuntu+1 here ans we have to accept hitches of all kinds, *but* both the stock Ubuntu and the Ubuntu Gnome have the same repos. If th eGS works just as well in stock Ubuntu, I have no idea, why I need a Gnome edition at all. I thought about this for the past Ubuntu Gnome editions, and installed them all to test. I just don't know why I should download the Ubuntu Gnome edition in the future. Maybe it'd have a value, if GS won't work with Mir in the future and has to use X to exist. 

Anyway, the G-classic session in Ubuntu Gnome is very strange. Updating & dist-upgrading doesn't change that problem yet. I am keeping it in a separate partition to test further.

---

### Post by jbicha on 2013-07-05
> **Chanath said:**
> 
You might notice the screenshot I've posted in #9. The Gnome-classic in Ubuntu Gnome Edition is somewhat strange, with the top panel acting like the GS top panel, and the bottom panel cannot be right-clicked at all. I have stock Ubuntu saucy and I've installed GS and G-classic (called flashback).

It sounds to me like you are confusing two different things. The gnome-panel session is now called GNOME Flashback (in 13.04 it was called GNOME Fallback and between 11.04 and 12.10 Ubuntu called it GNOME Classic).

The GNOME developers now have a new mode for GNOME Shell called GNOME Classic because it uses a similar style (although not all of the features) to the gnome-panel experience. Ubuntu GNOME 13.10 includes the new GNOME Classic by default but not GNOME Flashback. In 13.10 GNOME Classic and GNOME Flashback are not the same thing.

---

### Post by Chanath on 2013-07-05
> **jbicha said:**
> It sounds to me like you are confusing two different things. The gnome-panel session is now called GNOME Flashback (in 13.04 it was called GNOME Fallback and between 11.04 and 12.10 Ubuntu called it GNOME Classic).

The GNOME developers now have a new mode for GNOME Shell called GNOME Classic because it uses a similar style (although not all of the features) to the gnome-panel experience. Ubuntu GNOME 13.10 includes the new GNOME Classic by default but not GNOME Flashback. In 13.10 GNOME Classic and GNOME Flashback are not the same thing.

No, I am not confusing these things at all. *We are talking about Saucy here.*
In my stock Ubuntu, once I installed the Gnome panel, I get a session called Gnome Flashback, which looks like older Gnome2, with the right-clicking ability of the panels using Super+Alt, whereas in the Ubuntu Gnome Edition, its called Gnome Classic session. The screenshot I posted is from the Gnome Classic session, and as you notice, the top panel is messed up. There is no right-click ability for the bottom panel, autohide or get rid of it. Usually, I get rid of one panel. Okay, we are still in Alpha+ level in both Ubuntu and Ubuntu Gnome, but the repos are the same for both. How come, the stock Ubuntu with installed Gnome panel works normal, while the Ubuntu Gnome Edition's classic session doesn't?

Anyway, let's wait and see how it develops. I am keeping the Ubuntu Gnome edition, upgrading it every few days.

---

### Post by jbicha on 2013-07-05
> **Chanath said:**
> No, I am not confusing these things at all. *We are talking about Saucy here.*
In my stock Ubuntu, once I installed the Gnome panel, I get a session called Gnome Flashback, which looks like older Gnome2, with the right-clicking ability of the panels using Super+Alt, whereas in the Ubuntu Gnome Edition, its called Gnome Classic session. The screenshot I posted is from the Gnome Classic session, and as you notice, the top panel is messed up. There is no right-click ability for the bottom panel, autohide or get rid of it. Usually, I get rid of one panel. Okay, we are still in Alpha+ level in both Ubuntu and Ubuntu Gnome, but the repos are the same for both. How come, the stock Ubuntu with installed Gnome panel works normal, while the Ubuntu Gnome Edition's classic session doesn't?

Anyway, let's wait and see how it develops. I am keeping the Ubuntu Gnome edition, upgrading it every few days.

Sorry but you **are** confused. In Ubuntu GNOME, please install gnome-panel (or gnome-session-flashback). Log out and you'll see that there are two different and separate sessions: GNOME Classic and GNOME Flashback.

---

### Post by Chanath on 2013-07-05
> **jbicha said:**
> Sorry but you **are** confused. In Ubuntu GNOME, please install gnome-panel (or gnome-session-flashback). Log out and you'll see that there are two different and separate sessions: GNOME Classic and GNOME Flashback.

Okay, but does the Gnome-Classic look like Gnome-Classic in that screenshot in #9? There is a mixture of menus there, and if you click on the "Applications", you get typical Gnome shell Applications view, but with fixed 4 workspaces. The Dash is there too, so what's the difference between the Gnome (Shell) session & the Gnome-Classic session in it? What is the use of the unresponsive bottom panel, if I can get a task bar as a gnome extension in the top panel, just as its in the Gnome (Shell) session? 

*Gnome Flashback looks very much like the old Gnome 2, whereas the Gnome-Classic doesn't.*

---

### Post by OGpmpdog on 2013-07-05
> **Chanath said:**
> Okay, but does the Gnome-Classic look like Gnome-Classic in that screenshot in #9? There is a mixture of menus there, and if you click on the "Applications", you get typical Gnome shell Applications view, but with fixed 4 workspaces. The Dash is there too, so what's the difference between the Gnome (Shell) session & the Gnome-Classic session in it? What is the use of the unresponsive bottom panel, if I can get a task bar as a gnome extension in the top panel, just as its in the Gnome (Shell) session? 

*Gnome Flashback looks very much like the old Gnome 2, whereas the Gnome-Classic doesn't.*

Hi, I hope all is well.

I will make 2 suggestions:

1) Please do not argue tech stuff with the former lead developer of UG.:D

2) Please do me a favor and listen whenever he takes the time to comment here.  Thank you.

Now, I upgraded to UG Saucy back in April (havent done any fresh installs yet).  Beyond the keyboard searches being fragmented, GS runs buttery smooth.

---

### Post by Stinger on 2013-07-06
> **OGpmpdog said:**
> 

1) Please do not argue tech stuff with the former lead developer of UG.:D
Why not ? tech stuff should indeed be discussed with a developer. I like very much what Jeremy has done to make the impossible happen, putting the Gnome DE back (where it belongs) on top of Ubuntu.
That doesn't mean I agree in every move or the general direction Ubuntu-GNOME has taken since the project started ( as you probably have noticed :biggrin: ).  

> Now, I upgraded to UG Saucy back in April (havent done any fresh installs yet).  Beyond the keyboard searches being fragmented, GS runs buttery smooth.
Well good for you, you got all the butter. I got all the chrashes ;)

Suggestion: Ubuntu-GNOME 13.10 should be aligned with the [Gnome releases]("https://wiki.gnome.org/ThreePointNine") and released with GNOME 3.10.1 sometime after october the 16.
Ubuntu-GNOME should NOT have to respect the old "stable" Gnome version in Ubuntu.

---

### Post by sgage on 2013-07-06
> **Stinger said:**
> Ubuntu-GNOME should NOT have to respect the old "stable" Gnome version in Ubuntu.
I believe it has to use whatever is in the Ubuntu repositories, which I think it has to do to remain an "official" flavor, etc. If you want 3.10, well, that's why they invented the gnome3-team ppa's :KS

---

### Post by Chanath on 2013-07-06
> **OGpmpdog said:**
> Hi, I hope all is well.

1) Please do not argue tech stuff with the former lead developer of UG.:D

Oh, I thought he was still the lead developer. If he is not, that must be the problem with Ubuntu Gnome edition. :) I hope he is doing something with it, though. 
I'm not going to uninstall the Gnome editon, not until the 14.04 comes out as daily cdimage in October.

---

### Post by Stinger on 2013-07-06
> **sgage said:**
> I believe it has to use whatever is in the Ubuntu repositories, which I think it has to do to remain an "official" flavor, etc. If you want 3.10, well, that's why they invented the gnome3-team ppa's :KS
Yeah I know, being an official flavor comes with a price tag as long as Ubuntu can't handle the changes in Gnome because of the Unity-shell they use.
The developers call it stability and polish but it's nothing more than bending and tweaking the Gnome components to fit the needs of the Unity-shell.
This has nothing to do with actual development or progress. most development in Ubuntu lies in the Unity-shell and all it's fancy ( commercial ) lenses.
I personally think this adaption process is a waste of good developer resources. But that's the price Ubuntu has to pay to be in control. I don't think it's fair to pass this price tag to Ubuntu-GNOME too.

Well maybe this dilemma will resolve itself when the Unity-shell is ported to QT and Mir ? I can only hope :)

---

### Post by sgage on 2013-07-06
> **Stinger said:**
> Yeah I know, being an official flavor comes with a price tag as long as Ubuntu can't handle the changes in Gnome because of the Unity-shell they use.
The developers call it stability and polish but it's nothing more than bending and tweaking the Gnome components to fit the needs of the Unity-shell.
This has nothing to do with actual development or progress. most development in Ubuntu lies in the Unity-shell and all it's fancy ( commercial ) lenses.
I personally think this adaption process is a waste of good developer resources. But that's the price Ubuntu has to pay to be in control, but I don't think it's fair to pass this price tag to Ubuntu-GNOME too.

Well maybe this dilemma will resolve itself when the Unity-shell is ported to QT and Mir ? I can only hope :)

I agree with you for the most part. Ever since Ubuntu went on their Unity kick, I've felt like the writing was on the wall. I'm not interested in Unity, and 'lenses' and commercial tie-ins and whatnot. I have been sort of waffling around since that began. I have found Debian to be a solid home-base, but if it's the latest and greatest that you're after, well, it might not be your cup of tea. Me, I don't care - I just want to do the stuff I need to do, and I want stability. Boy, does Debian deliver on that score.

Fedora might track upstream Gnome a little better, I don't know. F 19 just came out with GS3.8. I've tried just about everything out there, and nothing has really impressed me. The fact is that Ubuntu maintains fairly awesome repositories, and that is why I have stuck with Ubuntu as long as I have - IMO the repos are their primary value-add. But it's been a long time since I felt they were going my way - hence my experimentation with other distros, primarily Debian. Talk about 'upstream' - it is the headwaters, really.

Just home from my 40th HS reunion... I guess I'm old enough now to where I value the stability over cutting edge.  8-)

---

### Post by Stinger on 2013-07-06
> **sgage said:**
> I agree with you for the most part. Ever since Ubuntu went on their Unity kick, I've felt like the writing was on the wall. I'm not interested in Unity, and 'lenses' and commercial tie-ins and whatnot. I have been sort of waffling around since that began.
I have been waffling a bit myself too ;) First I thought "Ubuntu and  Unity must be the way", Gnome 3 was only half baked and not an option then. I tried Fedora 17 and thought this has got some potential afterall, wonder if Ubuntu has somthing similar ? I fell in love with the [Ubuntu GNOME Shell Remix ]("http://ubuntu-gs-remix.sourceforge.net/p/home/") , still use it on my netbook.
For stability I use Mint Mate, else I use Ubuntu-Gnome and Fedora. ( been experimenting with [Netrunner]("http://www.netrunner-os.com/") too, writing from it now, but thats another story ;) ) 

Hope the HS reunion went well.
Cheers !

---

### Post by Chanath on 2013-07-06
I think the all-rounder of the Ubuntu family is Kubuntu. Maybe, Kubuntu might not be a fully supported derivative, but I've been experimenting with Kubuntu for sometime. I tried Mageia, Calculate, Sabayon KDE distros, but keep coming back to Kubuntu. This is a fully fledged distro, as KDE is fully fledged--you don't need to look for extensions etc, everything is there. Muon Discover, Muon Package Manager are highly responsive apps, Kwin gives the eye candy. Dolphin is a super file manager, and it has Libre-Office installed. I am using Kubuntu Saucy, and I have no hitches yet. Once, I thought KDE is childish, but not any more.:) Kubuntu's netbook DE is quite interesting too.   You have to install it.

GS has lot of extensions, giving a massive choice to the user. There are even Gnomenu, Unity Dash and new Slingshot extensions too, which gives you a chance to stay away from GS's Dashboard. I have installed the old Slingshot launcher (not the extension) in GS, which works much better than the GS's default Dashboard. That, someone could make an extension to use these launchers, Gnomenu, New Slingshot etc, and if the user can install a qute old Slingshot and use that very easily, blocking away the GS's Dashboard, then I have a queston to the GS developers (I know, this is not the place for that), why do we need this Dashboard at all? I think everyone (developers) had gone nuts about touch screens, as in mobile phones. The desktop/laptop would live some more years--not everyone wants to lean forward and touch the screen with their fingers.

By the way, I installed the old Slingshot launcher in stock Ubuntu too. It is just a few hundred kbs. If I can autohide the top panel, I'd use it there, but as I can't autohide it, I had to install Gnome-panel and get to the clear screen. Not everyone has widescreen monitors.

---

### Post by VinDSL on 2013-07-07
> **Chanath said:**
> GS has lot of extensions, giving a massive choice to the user. There are even Gnomenu, Unity Dash and new Slingshot extensions too, which gives you a chance to stay away from GS's Dashboard.
I like the GS Dashboard.  You can move it to the desktop, where it belongs, using 'Dash to Dock'.

Here it is, in GS 3.9.3 Staging (extension compiled from source)...


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-7-jul-2013-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-7-jul-2013-1.png")[/INDENT]


The only "problem" is, it remains on the left-side, Unity-style.

If I want to place a dock elsewhere, I use Plank.

---

### Post by Chanath on 2013-07-09
VinDSL,

Your desktop looks very nice!
I haven't upgraded to GS 3.9.3 yet. Does it have many extensions? How do you find it, better than GS 3.8.2?

---

### Post by VinDSL on 2013-07-09
> **Chanath said:**
> VinDSL,

Your desktop looks very nice!
I haven't upgraded to GS 3.9.3 yet. Does it have many extensions? How do you find it, better than GS 3.8.2?
Thanks!

There are usually quite a few extensions, included in the GS Staging package.  Going to the official GNOME Shell Extensions web site will be of little help to you, unless you know how to hack json files and/or the author offers the source code, which you can compile yourself.

Personally, I don't run that many extensions.  Matter of fact, I usually disable or remove them.

The only shell extensions I'm currently running are:
[LIST]
[*]Dash to Dock
[*]Icon Hider
[*]User Themes
[*]Workspace Indicator
[/LIST]

Truthfully, I cannot remember how 3.8.2 performed.  If you're happy with it, I'd stick with it.

GS3 Staging has/will break.  It's in heavy development.  Plus, it renders Unity unusable (at least, on this machine).

Having said that, GS 3.9.x just keeps getting better n' better, even though I can't quantify the differences...  ;)

---

### Post by Chanath on 2013-07-09
VinDSL,

Thanks for the reply. I installed GS 3.9.3, but didn't find any extensions, so I purged the ppas and got GS 3.8.2 back. The extensions I need are;
1) Hide top bar,
2) Task bar (not the one like Windows, but the one that works as a window list),
3) Weather,
4) Shutdown button,
5) User Themes 

Actually, more I use the GS, more I like it. Additionally, I can have either the Cairo Dock or the standalone DockbarX, but not a necessity. I don't know how to hack the json file. If you can, show me how to. Its quite interesting to have the Dash on the screen. How did you do that? I sometimes use the dock, which comes on the right side, but not a necessity, if I have the Task Bar on the top panel.  I also used the idea from OMG Ubuntu to group the applications. [http://www.omgubuntu.co.uk/2013/05/add-categories-to-gnome-shell-dashboard](http://www.omgubuntu.co.uk/2013/05/add-categories-to-gnome-shell-dashboard)  

Regards!
Chanath

---

### Post by Chanath on 2013-07-09
VinDSL,

Thanks for the reply. I installed GS 3.9.3, but didn't find any extensions, so I purged the ppas and got GS 3.8.2 back. The extensions I need are;
1) Hide top bar,
2) Task bar (not the one like Windows, but the one that works as a window list),
3) Weather,
4) Shutdown button,
5) User Themes 

Actually, more I use the GS, more I like it. Additionally, I can have either the Cairo Dock or the standalone DockbarX, but not a necessity. I don't know how to hack the json file. If you can, show me how to. Its quite interesting to have the Dash on the screen. How did you do that? I sometimes use the dock, which comes on the right side, but not a necessity, if I have the Task Bar on the top panel.  I also used the idea from OMG Ubuntu to group the applications. [http://www.omgubuntu.co.uk/2013/05/add-categories-to-gnome-shell-dashboard](http://www.omgubuntu.co.uk/2013/05/add-categories-to-gnome-shell-dashboard)  

Regards!
Chanath

Ps: This has got posted twice. How do I delete it?

---

