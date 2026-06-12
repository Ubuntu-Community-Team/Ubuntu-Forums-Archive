---
title: "More about the demise of Unity 2D"
date: 2012-08-17
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by cariboo on 2012-08-17
I just received this:

> *Hi Everyone -

Today is the first day that 'Unity' can be used without confusion on
Ubuntu. Unity 2D has been removed as a default option in favor of Unity 3D
across the board. This is a work in progress, so bear with us as we sort
out the details in the transition.

What does this mean? First and foremost, it means we have one codebase
going forward. Secondly, it means that that there will be some regressions
in use cases where Unity 2D fit in the past. Lastly, it means you should
see a unified experience wherever Unity runs.

Ever since Unity was introduced there have been slight gaps in the
experience between Unity 2D and Unity 3D (forever forward called Unity).
With one code base for all form factors we can guarantee a unified
experience. One code base also means we should be able to move faster as we
don't have to split the effort anymore, further accelerating our pace of
innovation.

But there is a cost to this decision. Unity 2D fit a very specific use case
in very low-end and non-GPU accelerated hardware. By consolidating to Unity
using LLVMpipe for this specific use case we expect to see some regressions
in systems supported. This means that a certain class of hardware will no
longer be supported to run Unity. Unity will run on all GPUs that support
OpenGL 2.0. The earliest GPUs that meet this requirement are at least 5
years old[1]. Even so, we know some subset of cards and hardware that could
previously run Unity 2D will no longer be able to run Unity.

For these cases, we are actively working on Unity running through LLVMpipe
which is a work in progress. Unity through LLVMpipe is CPU bound which
means systems with decently modern CPU architectures and non-GPU
accelerated hardware should be able to run Unity. As I mentioned, this
approach is a work in progress as we tweak the experience and effects to
maximize the performance. We expect this to shake out over the rest of this
cycle and bleed into 13.04 as well[2][3].

Still, with all the above, there will be systems that are simply too old to
run Unity. In those cases it would be necessary to either stick with 12.04
LTS or run another desktop environment[4].

We want this transition to go as smoothly as possible and are working on
supporting as much hardware as we reasonably can. Hopefully we should have
most of the wrinkles worked out by 12.10 release with just a little
hangover for 13.04.

Thank you,
Jason
Ubuntu Desktop Manager

[1] - Unity will run on GPUs with support for OpenGL 2.0
The earliest GPUs meeting this requirement are at least 5 years old
Intel i915
NVIDIA GeForce 5200FX and up (5200, 6xxx, 9xxx, xxxGT(X/S))
ATI Radeon 9000 and up, maybe earlier (9000, X1xxx, HDxxxx)

By chip series rather than model series:
Intel: i915
ATI: R300 chip series
Nvidia: NV30 chip series

[2] - We know Unity is showing some graphical corruption inside a VM. Work
to correct this has been done but not landed yet.

[3] - We know Unity won’t work right now on ARM. A solution is being worked
on and should be ready shortly, hopefully before feature freeze.

[4] -
[http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available](http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available)
*

---

### Post by vasa1 on 2012-08-17
Very welcome clarifications!

---

### Post by ventrical on 2012-08-17
Ok .. thanks Cariboo. So  is it assumed that a fresh install is required for this to take place?

---

### Post by cariboo on 2012-08-17
> **ventrical said:**
> Ok .. thanks Cariboo. So  is it assumed that a fresh install is required for this to take place?

You shouldn't have to, I did a fresh install about 6 hours before the new version of Xorg became available in the regular repositories. On my Nvidia system, nouveau was installed, and nvidia-current-updates was disabled, automagically.

---

### Post by cariboo on 2012-08-17
A bit more of an update for those that aren't subscribed to the ubuntu-devel mailing list:

> On Fri, Aug 17, 2012 at 09:39:18AM +0300, Timo Aaltonen wrote:
>   Just a heads-up, the new xserver et al moved to quantal, but the
> nvidia binary driver doesn't work with it, instead it'll likely just
> crash on login.

> So if you're using the blob, don't upgrade to current quantal until
> there's a new driver provided by NVIDIA.

The nvidia-graphics-drivers package has been updated to correctly document
that it's not compatible with the new X server.  Thanks to Alberto for the
update!  So this addresses the biggest problem, which is that users who are
using the nvidia driver would get upgraded to a broken desktop (because the
loaded kernel driver wouldn't work with the new X).  Instead, the nvidia
driver package is now uninstallable in quantal until a version becomes
available that's compatible with the current X server.  This should help
some quantal users being accidentally upgraded to a broken combination of
packages.

Users who want to stay current with quantal in the meantime should remove
the nvidia driver package from their system and use the nouveau driver
instead.

-- Steve Langasek Give me a lever long enough and a Free OS to set it on, and I can move the world. 
Debian Developer [http://www.debian.org/](http://www.debian.org/)
Ubuntu Developer 
 [email]slangasek@ubuntu.com[/email] 

---

### Post by ventrical on 2012-08-17
> **cariboo907 said:**
> You shouldn't have to, I did a fresh install about 6 hours before the new version of Xorg became available in the regular repositories. On my Nvidia system, nouveau was installed, and nvidia-current-updates was disabled, automagically.

Thanks Cariboo907,

 I just realize that  some of my older nvidia cards do not fit the specifications but, oddly enough. Kubuntu works just great with those older cards.

 Thanks for your updates on this.

---

### Post by jerrylamos on 2012-08-17
> Jason Ubuntu Desktop Manager: But there is a cost to this decision. Unity 2D fit a very specific use case in very low-end and non-GPU accelerated hardware.  
?  I'm running 2D on a late model wide screen dual processor Acer notebook, a fast 3.3 gHz Compaq tower, and a late model netbook.

I run 2D by having main Precise and in once case Lubuntu partitions along with the 3D Quantal test partition that I'm running least.  

I'm not in for big fuzzy foggy squirrely hard to see Sponge Bob desktop - example try Alt-tab with a few applications and a few firefox windows up.

But then again I don't have a smartphone if that's the appearance goal.

Jerry

---

### Post by cariboo on 2012-08-17
Gerry what graphics adapter does your system use, as most of us have no problem with graphics, running Unity 3D? BTW, I'm typing this on a tablet, I had to change the way I type, but, I'm getting faster using the on screen keyboard. I also have a docking station/keyboard, in case I get annoyed with on screen keyboard. :-)

---

### Post by jerrylamos on 2012-08-18
> **cariboo907 said:**
> Gerry what graphics adapter does your system use, as most of us have no problem with graphics, running Unity 3D? BTW, I'm typing this on a tablet, I had to change the way I type, but, I'm getting faster using the on screen keyboard. I also have a docking station/keyboard, in case I get annoyed with on screen keyboard. :-)
Advanced Micro Devices [AMD] nee ATI RC410 [Radeon Xpress 200] and a late model netbook and a wide screen amd64 notebook.  I assume they are working just like Jason wants.  I thought the forum was for testers to give early warning on how Ubuntu would be perceived by users but apparently not.

---

### Post by cariboo on 2012-08-18
> **jerrylamos said:**
> Advanced Micro Devices [AMD] nee ATI RC410 [Radeon Xpress 200] and a late model netbook and a wide screen amd64 notebook.  I assume they are working just like Jason wants.  I thought the forum was for testers to give early warning on how Ubuntu would be perceived by users but apparently not.

This forum is for testing the next version of Ubuntu, and reporting problems, not disrespecting the developers and the design team.

If you don't like Unity, stop testing it, there's always the other 3 derivatives that need testing too.

---

### Post by ronacc on 2012-08-20
It does mot mater if we like unity or not ( I don't) it still needs testing on as diverse hardware base as possible . As the "mainline" of Ubuntu development It shouldn't give end users a bad experience at release .

---

### Post by jerrylamos on 2012-08-20
> **ronacc said:**
> It does mot mater if we like unity or not ( I don't) it still needs testing on as diverse hardware base as possible . As the "mainline" of Ubuntu development It shouldn't give end users a bad experience at release .Ditto.  I did submit a bug a just the day before updated "Unity" ubuntu on my wide screen amd64 and got this response:
...processing it in order to get sufficient information for the developers failed (it does not generate a useful symbolic stack trace). This might be caused by some outdated packages which were installed on your system at the time of the report:
libnss3 version 3.13.1.with.ckbi.1.88-1ubuntu6 required, but 
3.13.1.with.ckbi.1.88-1ubuntu7 is available
libglib2.0-0 version 2.33.8-1 required, but 2.33.8-1ubuntu1 is available

So I'll try again, apparently one day behind on apt-get update is too old for Launchpad.  That's the "Unity 3D" ubuntu install on one of my processors I just run it looking for bugs.  

For general usage on my other two pc's (netbook, tower, I'm a pc buff) I run 2D or lubuntu or trying 12.10 Kubuntu amd64 at the moment fresh download yesterday so buggy it can't process bugs.  Try again soon.  

Jerry

---

### Post by ronacc on 2012-08-20
I have gotten that same message many many times this cycle , in fact most of the bugs I have tried to file failed for that or a similar reason . It seems to me that apport itself is buggy this time around . and when I got that message about " out of date packages" it was often just after an update . I have filed a few "by hand"  but the data apport gathers could not be included .and this time around has been very buggy for me .

---

### Post by ventrical on 2012-08-20
> **ronacc said:**
> I have gotten that same message many many times this cycle , in fact most of the bugs I have tried to file failed for that or a similar reason . It seems to me that apport itself is buggy this time around . and when I got that message about " out of date packages" it was often just after an update . I have filed a few "by hand"  but the data apport gathers could not be included .and this time around has been very buggy for me .

 I too have had great difficulty getting apport to work correctly. It is very  disappointing to go through that process and have the bug proceedure fail.  However, we have here (at Ubuntuforums) where we can report bug-like symptoms and glitches.  And thats a bouns for  the devs because not much can get lost in translation. Om the other hand , it's a lot of uneccessary  downtime for testers but I also think that this is part of the load as a hacker and beta tester when we take on  testing  with the spirit of trying to cause breakage so that better patches can be produced upstream.

---

### Post by kansasnoob on 2012-08-20
> **ronacc said:**
> It does mot mater if we like unity or not ( I don't) it still needs testing on as diverse hardware base as possible . As the "mainline" of Ubuntu development It shouldn't give end users a bad experience at release .

Well said!

I personally want to shift most of my focus towards Lubuntu and LXDE, but I still need to "cross-test" to see what's going on ;)

---

### Post by jerrylamos on 2012-08-20
Took my latest today's update of 12.10 Ubuntu then installed LXDE from Synaptic on top of Ubuntu 12.10.  Running that right now, choose between Ubuntu Development's desktop and LXDE at logoff/login.  There's a couple other options about Opehbox etc. that I'll try.

Lubuntu doesn't seem to get development attention, but LXDE is actively used by Debian etc. so 12.10 Ubuntu with LXDE might not be too buggy...famous last words.

Jerry

p.s. I've got a fast tower, a wide screen notebook, and a netbook so I've been trying Ubuntu development releases on all three looking for bugs.  I run "Unity" (don't know where they got that name) briefly for bugs then switch to the other desktops for my general use.

---

### Post by fjgaude on 2012-08-20
The name Unity comes from the desire to have Ubuntu work on all devices, even TVs, cells, netbooks, laptops, and tablets. We are on our way into the 21th century.

---

### Post by jerrylamos on 2012-08-20
> **fjgaude said:**
> The name Unity comes from the desire to have Ubuntu work on all devices, even TVs, cells, netbooks, laptops, and tablets. We are on our way into the 21th century.Admitedly this is still Alpha/Beta, but do take a look at this forum to see if "Unity" is in fact running on everything.  I'm enjoying different desktops on top of 12.10 Ubuntu myself.  From my experience at IBM, running on everything could mean the "least common denominator".

Have fun.  Choices.

Jerry

---

### Post by fjgaude on 2012-08-20
Well, we will have to wait and see how it turns out. With the right imagination, design, and coding we could have something better than IBM even would have dreamed. <grin>

I'm seeing all the touch, tap, pinch, sweep code already in the later version of 12.10. We will see...

---

### Post by cariboo on 2012-08-21
> **jerrylamos said:**
> Admitedly this is still Alpha/Beta, but do take a look at this forum to see if "Unity" is in fact running on everything.  I'm enjoying different desktops on top of 12.10 Ubuntu myself.  From my experience at IBM, running on everything could mean the "least common denominator".

Have fun.  Choices.

Jerry

We have to define least common denominator though. Does it mean anything that will run currently available operating systems from all manufacturers, or does it mean having the ability to run operating systems that have been available for the last 10 years?

I don't expect my Apple G4 (circa 1999) to run OSX of any version, and I'm resigned to the fact that my iMac (circa 2001) will only run OSX 10.4. I have Intel Celeron powered systems that won't run Windows 7, so why should I expect them to run the latest version of Ubuntu.

As far as I'm concerned I will run operating systems appropriate to the hardware. If that means running something other than Ubuntu, it doesn't bother me in the least. The other derivatives, need just as much testing as Ubuntu, and the more testers, the merrier.

---

### Post by ventrical on 2012-08-21
> **cariboo907 said:**
> We have to define least common denominator though. Does it mean anything that will run currently available operating systems from all manufacturers, or does it mean having the ability to run operating systems that have been available for the last 10 years?

I don't expect my Apple G4 (circa 1999) to run OSX of any version, and I'm resigned to the fact that my iMac (circa 2001) will only run OSX 10.4. I have Intel Celeron powered systems that won't run Windows 7, so why should I expect them to run the latest version of Ubuntu.

As far as I'm concerned I will run operating systems appropriate to the hardware. If that means running something other than Ubuntu, it doesn't bother me in the least. The other derivatives, need just as much testing as Ubuntu, and the more testers, the merrier.

 I like your attitude cariboo907. Ubuntu is growing and in the course of it's development it is outgrowing certain hardware. Kubunu and Lubuntu
  and other variants will run on graphics adapters  that Unity will not. There is always a fallback of some sort for older machines.

---

### Post by Stinger on 2012-08-21
> **cariboo907 said:**
> We have to define least common denominator though. Does it mean anything that will run currently available operating systems from all manufacturers, or does it mean having the ability to run operating systems that have been available for the last 10 years?

I beg to differ, I don't think we have to define anything, the kernel developers will take care of that (or the companies who make  drivers for linux), they decide witch hardware is gonna be supported and witch not.

The Problem arises when the hardware is supported but not working well, like Unity3d via the llvmpipe. As Unity is actually an extension of the Compiz Window Manager, it will be Unity and compiz running through the pipe.
Some older but still supported hardware configurations have trouble living up to Unity/compiz demands but AFAIK ran just fine with Unity2d.

The right solution to this problem would have been to slim down Unity/compiz before trying to run it through the llvmpipe (just because everyone else do) and still offer Unity2d until a slimmed down version was available.
Or better yet, make Unity one or more Gnome shell extensions using mutter and ditch compiz.

---

### Post by ronacc on 2012-08-21
one of the things that worries me about the current thrust of Ubuntu is that we seem to be adopting the attitude of the "big 2" Apple and M$ , namely "you want to run Ubuntu go buy a new box" . This I think is a mistake . Older but still perfectly good hardware represents an absolutely HUGE potential market . Not long ago Ubuntu was very concerned about not giving that market away , what changed ? We need to give those with the "latest and greatest" an experience to match their hardware and also offer those who have been abandoned by the "big 2" an opportunity to run as secure and capable OS as their hardware allows . Yes there are the derivatives but who knows about them but those who already are using linux . The area of growth for Ubuntu is those who are not yet linux users , aiming to cannibalize current users away from Suse or Fedora et all won't get us nearly as many new users.I don't know what the answer is ( Ubuntu lite ? ) but finding one could go a long way tword squashing BUG 1 . And also would be GREEN by keeping a lot of old hardware out of the trash stream .

---

### Post by pressureman on 2012-08-21
I wouldn't consider supporting older hardware a "huge potential market", since Ubuntu doesn't make any money from this. The term "market" implies that is mutually profitable for both parties. The types of organizations who cannot afford new hardware (eg. rely on hardware donations) are usually the same organizations who have no budget to buy commercial support services from Canonical - something that the company depends on to stay afloat.

I would call supporting older hardware a "philanthropic opportunity". I know that Ubuntu's roots go back to this ideal, but Mr Shuttleworth doesn't have an infinite supply of cash to keep funding the project indefinitely. As I understand it, Canonical are pretty much on the brink of breaking even, year to year.

IMHO, it is unreasonable to expect the latest versions to support older hardware forever and ever. Eventually, the older hardware just simply isn't economical to support anymore. The effort it takes to keep old drivers up to date with the (constantly evolving) kernel ABI isn't worth the numbers of that particular hardware in the field. Kernel contributions from the likes of Red Hat, SuSE etc will predominantly be aimed at supporting modern, enterprise hardware, since that's what their *paying customers* are interested in. Contributions from hobbyist kernel developers will usually revolve around the hardware that the developer personally owns, or has ready access to. As the older hardware slowly disappears off the face of the planet, so too do the possibilities for developers to test software on it.

If people expect ten year old hardware to be supported, I think they're better to stick to a slightly older release, from a time when that hardware was considered leading edge (or at least "current"). Either that, or step up to the plate and start writing code ;-)

PS: I think bug #1 is largely symbolic, and will never be closed.

---

### Post by jerrylamos on 2012-08-21
> I like your attitude cariboo907. Ubuntu is growing and in the course of it's development it is outgrowing certain hardware. Kubunu and Lubuntu
and other variants will run on graphics adapters that Unity will not. There is always a fallback of some sort for older machines.Well, I have three late model computers that will slog through Compiz, a wide screen amd64x2 notebook, a netbook also x2, a fast tower.  I'd gotten used to using 2D.  I'm a bit tired of developers talking down to me - these are mainstream not "old slow pc's".

So now what I did is a full install of Ubuntu then adding LXDE desktop on top, works fine thank you, I'm not as efficient as I was on 2D but easily usable.  

Also in another partition doing a full install of Ubuntu then adding xubuntu-desktop.  That brings in a whole lot of applications I don't use, but so be it, I'll give it a try.

Oh, yes, on the LXDE Ubuntu I can log in (briefly) to "Unity" to check for major bugs, then right back to LXDE Ubuntu for easy general use.

And I do have a Precise 2D Ubuntu still supports that - I think.

Ubuntu's been running for me, ubiquity is still a @#$%^, so using LXDE and xubuntu-desktop on top of Ubuntu is interesting and might turn up some useful bugs.  Development can test the "Unity" desktop.

---

### Post by ventrical on 2012-08-21
we will still have 5 years support for Unity 2D with 12.04 and by that time I am quite sure that something new and punchy will be available - even for older machines.

---

### Post by ventrical on 2012-08-21
> **jerrylamos said:**
> Well, I have three late model computers that will slog through Compiz, a wide screen amd64x2 notebook, a netbook also x2, a fast tower.  I'd gotten used to using 2D.  I'm a bit tired of developers talking down to me - these are mainstream not "old slow pc's".

So now what I did is a full install of Ubuntu then adding LXDE desktop on top, works fine thank you, I'm not as efficient as I was on 2D but easily usable.  

Also in another partition doing a full install of Ubuntu then adding xubuntu-desktop.  That brings in a whole lot of applications I don't use, but so be it, I'll give it a try.

Oh, yes, on the LXDE Ubuntu I can log in (briefly) to "Unity" to check for major bugs, then right back to LXDE Ubuntu for easy general use.

And I do have a Precise 2D Ubuntu still supports that - I think.

Ubuntu's been running for me, ubiquity is still a @#$%^, so using LXDE and xubuntu-desktop on top of Ubuntu is interesting and might turn up some useful bugs.  Development can test the "Unity" desktop.

 I admire your perserverence.

 Unity 2D had a certain ambiance to it. (You can still run Unity 2D with 5 years of support on the Precise Platform). It had this really neat effect with smooth scrolling of icons and I still cannot figure out why they 'the devs' were not able to replicate this effect with Untiy 3D. (so much for ambiance and effervescence)! :)

 I mean , it's not the end of the world. Most likely Lucid will be extended past it's EOL cycle and we still have Precise LTS but Unity 2D was becoming a regular desktop for beta testing on older machines (and new machines also). I have a Le Pan tablet. Honestly .. that thing is the most useless computer (if you want to call it that) that I have ever seen or used. (Thankully it was given to me for testing and I didn't spend money on it). Fo rthe most part it is a conversation executive toy play-thing  device  to take notice for a few minutes around the water cooler - and then life goes on.  All I use it for is a GPS device and it is even buggy there also. It's so hard to position .. I don't get it .. anyways .. thankfully I have towers & keyboards that I only have  to clean every 3 months and don't get these awful smudges on them. :) lol

 Lubuntu  (LDXE) and xubuntu are also very sleek, fast and effervescent. Xubuntu really does not get enough up-time or credit that it is deserving of.

---

### Post by ronacc on 2012-08-21
@pressureman
By market I meant potential new users . By increasing our user base we increase the likelyhood that companies will notice us and use Ubuntu and its comercial support services .That "older hardware slowly dissappearing " still represents 100's of millions of units.And what CFO or CPO wouldn't want to see his $ go a little further ? I have no dog in this fight , when my hdw gets old I build a new one , I just hate to see a resource get ignored . Supporting hdw that others don't is good advertising .

---

### Post by ventrical on 2012-08-21
> **ronacc said:**
> @pressureman
By market I meant potential new users . By increasing our user base we increase the likelyhood that companies will notice us and use Ubuntu and its comercial support services .That "older hardware slowly dissappearing " still represents 100's of millions of units.And what CFO or CPO wouldn't want to see his $ go a little further ? I have no dog in this fight , when my hdw gets old I build a new one , I just hate to see a resource get ignored . Supporting hdw that others don't is good advertising .

 And that lends to the whole ubuntu 'goal' of  having 200,million users (or something to that effect). It is going to be a hard goal to attain because a lot of noobs have a real hard time with busted systems and repos . etc.. and so they'll just spend the money on a commercial product. 

 But pressurman is making some realistic points I think.

---

### Post by jerrylamos on 2012-08-21
My solution is full install of Ubuntu then add LXDE desktop.  All the Ubuntu applications are available.  

I've tried XFCE4 briefly, and Kubuntu briefly - at my level of kubuntu takes me more keystrokes to do what I can do with LXDE.

Yes these are late model current full architecture netbook, amd64 wide screen notebook external monitor, 3.3 gHz tower.  I run "Unity" very briefly for major breaks then right back to LXDE on 12.10 or sometimes 2D on 12.04.

---

### Post by vexorian on 2012-08-21
The Unity-2D "use case" that optimized unity will never cover is running without compiz. Compiz seems to always slow down my system whereas things like mutter or metacity with compositing don't. I really wish unity wasn't locked to compiz, and now that Unity-2D is killed. I guess I will have to get used to something not made by canonical.

And my desktop is perfectly capable of running unity in compiz  right now. But it does not change the fact that compiz blows. At least it blows in this computer, which is 3 years old. Compiz is the one thing I have to get rid of to change my desktop from annoyingly slower to "actually incredibly decent superb fast". mutter and metacity , each using compositing and opengl and looking pretty don't have this issue. I like it when my computing power is not spent on a window manager full of features that I don't use. All I need in a window manager is it being able to run unity, allow apps to do compositing and add shadows to window decorations and menus. Mutter and metacity do this job just fine without wasting so much resources. 

Again, it is not that I cannot run compiz, it is that when I run compiz, everything else becomes much slower. Firefox loses responsitivity. Opengl games noticeably drop in FPS. Etc.

Even Windows 7 allows you to disable all of its special effects. So that when you don't really need your desktop to use GPU power, you can just disable them. Enjoy the great performance of games and multimedia apps when 99% of your computing power is spent on them . As opposed to when 30% of your power is spent on windows 7's special effects or on ubuntu's compiz.

While the devs repeat things like how this will fix their duplication of efforts. They don't really say why they chose the plugin that was locked into compiz as opposed to the stand-alone application. Since "unity-2D" can run with compiz just fine. it would have been a more logical move to scrap the compiz unity and instead make unity-2D the new unity. At this moment, my unity 2.0 is using metacity's compositing features to have transparency in dash and in its launcher and stuff. Yet since it is not locked to compiz, it can fallback to a mode that does not need compositing.

Worse, the compiz lock-in is what makes unity a lot less appealing to other distributions. Unless other distributions give unity their blessing, Canonical will have to be the only contributor to it and unity will not have a lot of future. So it baffles me that they would not be working towards making unity easier to be ported to other distros. Choosing the compiz lock-in over the standalone app is the opposite of what they could have done to improve this.

**Edit:** also, what happens when your GPU drivers stop working out of a misconfiguration or because your GPU is too recent? Until compiz has a fallback mode in which it can run without needing these drivers, making the only DE available require it is going to be very bad when your GPU drivers fail.

---

### Post by pressureman on 2012-08-21
> **ronacc said:**
> @pressureman
By market I meant potential new users . By increasing our user base we increase the likelyhood that companies will notice us and use Ubuntu and its comercial support services .That "older hardware slowly dissappearing " still represents 100's of millions of units.And what CFO or CPO wouldn't want to see his $ go a little further ? I have no dog in this fight , when my hdw gets old I build a new one , I just hate to see a resource get ignored . Supporting hdw that others don't is good advertising .

It saddens me also to see still-working hardware thrown out by companies. The cold hard reality of it though, is that their accountants will write off computers usually when they're 3-4 years old - some companies write them off even earlier than that, depending on local tax laws and rate of depreciation.

The moment that that old hardware starts costing more money to support, than what it would cost to replace it with a shiny new box, is the moment it gets ruthlessly tossed out. Schools and educational institutes usually have a higher threshold of pain when supporting old hardware. That is, they'll persevere longer than most businesses would. They often have access to a cheap or free labour pool though - students.

Now, that discarded hardware *could* end up being refurbished and redeployed in some other organization - but this requires somebody to take the initiative and do that. Often, it's cheaper to simply recycle the metals and plastics. Shredding PCBs to extract copper, gold, and other precious metals is often far more lucrative.

---

### Post by ronacc on 2012-08-21
> **ventrical said:**
> And that lends to the whole ubuntu 'goal' of  having 200,million users (or something to that effect). It is going to be a hard goal to attain because a lot of noobs have a real hard time with busted systems and repos . etc.. and so they'll just spend the money on a commercial product. 

 But pressurman is making some realistic points I think.

Yes pressurman is making some good points . What I am pointing out is that we have the opportunity to "lock in " the affection of that segment of users that do not buy new hdw every 2 or 3 years . "older machines" like those designed to run XP or cariboo907's G4 are still hugely capable machines as long as they are not asked to play the latest games or spreadsheet the entire budget of General Motors or a 3rd world country . The owners of those machines deserve some love too , they will return it .  perhaps "official" support for the alternatives or maybe just one would be a good thing . Not Kubuntu , KDE is going the allout heavyweight route too but one of the "lightweights" .

---

### Post by jerrylamos on 2012-08-21
> **ronacc said:**
> Yes pressurman is making some good points . What I am pointing out is that we have the opportunity to "lock in " the affection of that segment of users that do not buy new hdw every 2 or 3 years. I did buy widescreen notebook amd 64 with external monitor usually, 10.1" netbook with either it's own screen or right now hooked to a 15" TV 1366x768, and a 3.3 gHz tower on 1440x900.

Oh, I've got 10.1" and 7" tablets.  O.K. for output, poor (!) for input.

I'm running 12.10 Ubuntu with LXDE desktop and also 12.04 Precise with 2D.

Somebody else can test Unity and Compiz - I run briefly for any major breaks then right back to LXDE for testing the rest of 12.10, precise 2D for salvaging wreckage.  

BTW, I do a lot of installs and Ubiquity is still good for getting bugs.  It hung last night so of course Grub was clobbered and couldn't reboot - Ubiquity does that first before finding out if it can actually install O.K. so Super Grub2 to the rescue.

---

### Post by balloons on 2012-08-21
There's so many unity2d threads.. Anyways, spamming this link to all of them as I think it will help. If you want to try the new version of compiz (and help test it!) check this out. LLVMpipe is enabled, and working well for me so far. See how it fares for you. 

[http://ubuntuforums.org/showthread.php?t=2045579](http://ubuntuforums.org/showthread.php?t=2045579)

---

### Post by Stinger on 2012-08-22
> **ventrical said:**
> we will still have 5 years support for Unity 2D with 12.04 and by that time I am quite sure that something new and punchy will be available - even for older machines.

What I am hearing is: If you are having a pc with older but supported hardware, QQ 12.10, with all it's new technology, is out of reach ?
Meaning hardware demands is rising for 12.10 compared to 12.04 ?

I personally would hate to see Ubuntu to grow into a linux version of "Windows Vista"
That certainly won't give Ubuntu many new users.

---

### Post by ventrical on 2012-08-22
> **ronacc said:**
> Yes pressurman is making some good points . What I am pointing out is that we have the opportunity to "lock in " the affection of that segment of users that do not buy new hdw every 2 or 3 years . "older machines" like those designed to run XP or cariboo907's G4 are still hugely capable machines as long as they are not asked to play the latest games or spreadsheet the entire budget of General Motors or a 3rd world country . The owners of those machines deserve some love too , they will return it .  perhaps "official" support for the alternatives or maybe just one would be a good thing . Not Kubuntu , KDE is going the allout heavyweight route too but one of the "lightweights" .

ronacc,

I have been making that argument for years, decades, however, planned obsolescence has a way of catching up with time, especially in the PC hardware platform. Software and hardware in the PC business are not like automotive. Yes, you can put a hemi-supercharger into an old shell of a car and it will make it better but you can't put a souped-up software package into an old processor. Performance is not backward compatible. I think this is a hard reality that we all have to deal with , however, the art of downgrading seems to be a new phenom trend taking place and that gives everybody a lot of leeway.

---

### Post by ventrical on 2012-08-22
> **pressureman said:**
> It saddens me also to see still-working hardware thrown out by companies. The cold hard reality of it though, is that their accountants will write off computers usually when they're 3-4 years old - some companies write them off even earlier than that, depending on local tax laws and rate of depreciation.

The moment that that old hardware starts costing more money to support, than what it would cost to replace it with a shiny new box, is the moment it gets ruthlessly tossed out. Schools and educational institutes usually have a higher threshold of pain when supporting old hardware. That is, they'll persevere longer than most businesses would. They often have access to a cheap or free labour pool though - students.

Now, that discarded hardware *could* end up being refurbished and redeployed in some other organization - but this requires somebody to take the initiative and do that. Often, it's cheaper to simply recycle the metals and plastics. Shredding PCBs to extract copper, gold, and other precious metals is often far more lucrative.

Recycling is one of  my fortes'.  Lots of gold on those older 'piano-fingers'. Also I like refurbrishing older PCs. It is to my benefit when people throw out perfectly good PCs. I just adopted two new orphans. A Dell Dimension 3100 3.GHz/80GBSATA. Diagnosis- Windows XP corruption and a HPa1106n 516P4/2.9GHz/200GBSATA. Diagnosis - victim of Vista. Most of all these PCs just need the heat sync fan on the processor clean.  Thermal protection shut-down emulates malware or mobo malfunction. Ignorance is bliss ! :)& with the way commercial software behaves it's a bonus. Ubuntu has recovered a lot of PCs from the roadside.

---

### Post by ventrical on 2012-08-22
> **Stinger said:**
> What I am hearing is: If you are having a pc with older but supported hardware, QQ 12.10, with all it's new technology, is out of reach ?
Meaning hardware demands is rising for 12.10 compared to 12.04 ?

I personally would hate to see Ubuntu to grow into a linux version of "Windows Vista"
That certainly won't give Ubuntu many new users.

There are just too many good programmers out there. I predict that a new DE will be developed to ride on the QQ kernel that will facillitate older machines.( FVWM-Crystal already does this but nobody wants to spend the time to tweak it.). I cannot predict if it will or will not be in the Canonical Repos.

---

### Post by jerrylamos on 2012-08-22
My 3 pc's are not older.  They are current.  They do run Unity, just long enough to see if it works and install synaptic and then select LXDE.  I do use Firefox, Libre, Nautilus, ... nice useful stuff to me in the Ubuntu install.

BTW, some time ago I saw some statistics on Ubuntu downloads showing a trend with Unity, maybe it was in Ubuntu Planet.  I haven't seen those statistics lately. or how the number of downloads compares to other platforms such as Mint, Fedora, Debian, openSUSE.  It would be hard to get that data since it is private data from each organization.  DistroWatch.com is likely to be a skewed market to a class of linux buffs.

I try the other distro's from time to time and come right back to Ubuntu, 2D on Precise and LXDE on Quantal.  

Jerry

---

### Post by zombifier25 on 2012-08-22
I personally support the move since there are other DEs designed specificly for low-end computers. Unity was not, and never will be, built for old systems. If your computer comes from the museum, not even Unity 2D will do.

'sides, if we keep making operating systems designed for 128MB RAM computers, technology will never move on.

---

### Post by pressureman on 2012-08-22
> **zombifier25 said:**
> I personally support the move since there are other DEs designed specificly for low-end computers. Unity was not, and never will be, built for old systems. If your computer comes from the museum, not even Unity 2D will do.

'sides, if we keep making operating systems designed for 128MB RAM computers, technology will never move on.

+1.

I wholeheartedly agree.

---

### Post by Stinger on 2012-08-22
> **zombifier25 said:**
>  If your computer comes from the museum, not even Unity 2D will do.

'sides, if we keep making operating systems designed for 128MB RAM computers, technology will never move on.
> **pressureman said:**
> +1.

I wholeheartedly agree.

You are both way beside the point I was trying to make earlier, I'm NOT talking about nostalgic hardware but hardware supported in 12.04
But please, feel free to have a few laughs on my account.

---

### Post by vasa1 on 2012-08-22
> **zombifier25 said:**
> I personally support the move since there are other DEs designed specificly for low-end computers. Unity was not, and never will be, built for old systems. If your computer comes from the museum, not even Unity 2D will do.

'sides, if we keep making operating systems designed for 128MB RAM computers, technology will never move on.
The issue is _not_ limited to DEs. The latest version of many operating systems, browsers, office suites run better on "modern" machines. Many websites are also designed that way.

---

### Post by vexorian on 2012-08-22
You can congratulate the software industry for their success at nullifying all the progress of the hardware industry.

I mean really . "If we keep designing OS to use less than 128MB there will never be technological progress". Is it really progress? It is only progress if the new OS is actually doing a lot more things than the old OS. But you hand me something like windows 7 and I wonder where are is the GB of RAM getting used and how it improves the experience. If the old OS needed X in computing resources and new OS needs X*X, then I hope the new OS is X times more useful better.

I think using all of your system's resources is a wonderful thing. I just prefer when the resources are used in the actual applications I am running rather than a window manager that does a lot of things I don't really care about. And I mean, maybe transparent thingies are cool, but it is not compiz what pays my bills, it is not compiz what allows me to read stuff on the web, it is not compiz what entertains me. When considering the little value compiz adds to my computer, I feel that the resources it spends are not proportional to it.

My computer is current, and I am planning to buy an 2012 i7 with good GB of RAM and a blazing GPU by the end of the month. I still would avoid compiz. I mean, a new computer won't change my opinion that compiz really is a terrible thing to run. I will likely stick to 12.04 and run unity 2D (full with compositing from metacity or mutter). Again, not because my computer is old, but because I don't like getting locked into compiz.

And oddly enough , unity 2D in 12.04 currently has more features than "real unity" ? What's up with that? I can actually change its appearance to be a solid color. I can make it hide automatically ONLY when a window uses its space. When running in a window manager with compositing, the launcher and dash actually use transparency and effects just fine. Etc, etc, etc. All while running metacity which has this strange trait of NOT making everything feel clogged.




> **Stinger said:**
> What I am hearing is: If you are having a pc with older but supported hardware, QQ 12.10, with all it's new technology, is out of reach ?
Meaning hardware demands is rising for 12.10 compared to 12.04 ?

I personally would hate to see Ubuntu to grow into a linux version of "Windows Vista"
That certainly won't give Ubuntu many new users.
What new technology exactly? I think the most important things about 12.10 vs. 12.04 would be LibreOffice and Firefox versions, I am sure that there will be support from PPAs to update these big apps for the LTS 12.04.

---

### Post by Stinger on 2012-08-22
> **vexorian said:**
> 
I think using all of your system's resources is a wonderful thing. I just prefer when the resources are used in the actual applications I am running rather than a window manager that does a lot of things I don't really care about. And I mean, maybe transparent thingies are cool, but it is not compiz what pays my bills, it is not compiz what allows me to read stuff on the web, it is not compiz what entertains me. When considering the little value compiz adds to my computer, I feel that the resources it spends are not proportional to it.

Exactly my point, I couldn't have said it better :D
Using my systems resources in the actual applications rather than using them for running compiz/unity through the llvmpipe and draining the cpu for it's power.

> **vexorian said:**
> What new technology exactly?

New kernel, new  X.Org Server, newer Gnome apps, all that kinda stuff to mention a few.

---

### Post by jerrylamos on 2012-08-22
> **zombifier25 said:**
> I personally support the move since there are other DEs designed specificly for low-end computers. Unity was not, and never will be, built for old systems. If your computer comes from the museum, not even Unity 2D will do.

'sides, if we keep making operating systems designed for 128MB RAM computers, technology will never move on.This is an amd64 dual processor 2 GB - the fresh 12.10 A3 install yesterday. Ubiquity slideshow highlighted customizing so since there's no 2D I'm running LXDE desktop just fine.  My 1.66 gHz netbook with 1 GB is running the same, as well as my 3.3 gHz tower.  

Some people are jumping to the conclusion that "old hardware" is the only reason everyone isn't using Unity/Compiz.  Not so.  

I get chewed out on these forums if I comment on Unity so let the marketplace do that.

---

### Post by ventrical on 2012-08-22
This is an Intel 516 Pentium 4 64bit processor, 2.9GHz, 1GBddr2 with Intel graphics. Unity 3D running fine in 64bit mode.  It don't matter to me. Unity, GNOME. KDE, Xubuntu. They are all working good here. Not on Unity on Nvidia.  Can't be helped right now .. so run something else. Keep updating .. it gets better :)

---

### Post by philinux on 2012-08-22
Here's what it says.

[https://help.ubuntu.com/community/Installation/SystemRequirements/](https://help.ubuntu.com/community/Installation/SystemRequirements/)

And interesting. I'd not seen this before.

[https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements](https://wiki.ubuntu.com/DemystifyingUnityGraphicsHardwareRequirements)

At the end of the day just use what works for you on new or old machInes

. ):P

---

### Post by ronacc on 2012-08-22
I wonder what some of the devs are thinking , not just ubuntu's , they seem to be coding to waste as much resources as they can , as I type this the clock applet is using 2% of my cpu ,  google chrome 12% for one window  and this is not a legacy machine what ever happened to the idea of tight efficient coding ? I don't think current OS's are all that much better than my circa 1985 A500 had for all that they require 100 times the cpu and gpu to even boot .

---

### Post by effenberg0x0 on 2012-08-22
I like the idea of FOSS freedom and being able to use what works, as it was mentioned. What I don't like is having to change every few months. Once I customize my DE to be exactly the way I want it, exactly the way it's comfortable, fits my needs and enhances my work productivity, I'd like to rest assured I won't have to change DE and do it all again soon.

When I think of Ubuntu in the corporate, government, education segments - and I like to think Ubuntu is mature enough and will continue to grow in share in these markets, I can't imagine CIOs trusting to invest their IT budget and staff time to deploy a OS that may or may not work tomorrow or next week with some DE or even considering the risk of having to reinvest in deployment, employees training, application customization, etc to adapt to another DE every time someone decide to change something or when anything bad happens with the current DE.

Regards,
Effenberg

---

### Post by ronacc on 2012-08-22
boy did you say a mouthfull , every 6 months I have to search long and hard to find where they hid all the settings this time.

---

### Post by pressureman on 2012-08-22
What some people seem to forget is that we now have computers with much higher display resolution and higher colour depth than 10 years ago. What do you think happens to the contents of windows when they're in the background? Well... they're still in memory... and the more windows (or browser tabs) you have open, the more memory is used, just to save the window contents for when you bring that window to focus again.

If you double the horizontal and vertical resolution, you *quadruple* the memory required to buffer the contents of that window. And going from legacy 8-bit (256 colour) graphics to a 24-bit RGB display *triples* the memory requirements. All that has to be stored somewhere.

People gladly accept higher resolutions, richer colours, faster frame rates, sharper fonts, and prettier icons... but give little thought to how the system requirements to drive that can balloon rather rapidly.

Watching a 1080p video on your computer? That's approximately 150 MB *per second* that has to be decoded by the CPU and copied to video memory. Could your computer from 10 years ago do that? How about 5 years ago?

Software developers will always try to maximise the capacity of current hardware. If they didn't, there would be no incentive for hardware designers to keep building bigger, faster machines. Occasionally things get out of sync a little, but the latest software is always more or less suited to the latest hardware.

I agree that some of the "bling" on desktops is unnecessary and does nothing to improve usability (wobbly windows anyone?). An option to turn that off is always nice, for those of us who don't just use our machines for dicking around.

One thing remains true regardless: your 5-year old computer still runs a 5-year old OS **just as well as it ever did**. Simply installing the latest software on it does not automagically make the hardware more powerful too.

---

### Post by vexorian on 2012-08-22
Compiz' resource hogginess  is unrelated to the increase of resolutions. It has always been pretty awful at that. Other window managers can run the same amount of applications WITH compositing in the same resolution without using as many resources.
> **ronacc said:**
> boy did you say a mouthfull , every 6 months I have to search long and hard to find where they hid all the settings this time.
You don't *have* to upgrade every 6 months, you know.

A normal ubuntu release is supposed to last 1.5 years. 12.04 will be supported for 5 years. After a while of using ubuntu you get tired of all that giberish of upgrading, that's how I kept feisty for 2 years and then 10.10 for 1.5 years.

---

### Post by vexorian on 2012-08-22
Edit: Sorry, betrayed by ISP.

---

### Post by jerrylamos on 2012-08-22
> **pressureman said:**
> What some people seem to forget is that we now have computers with much higher display resolution and higher colour depth than 10 years ago.
Sir, not sure what you're talking about.  This is a 1G netbook Atom N455 happily runnung 1366x768 on today's Quantal daily build i386.  Ubiquity slide show today says I can customize Ubuntu so I'm running LXDE desktop.  This afternoon I was running my amd64 2G notebook 1280x1024 external monitor with yesterday's Quantal amd64 customized with LXDE desktop.  Tonight I'll likely be in the living room running my 3.3 gHz tower 1440x900 monitor with a couple days old Quantal updated, again with LXDE desktop.  I've also got backup (Alpha can crash) partitions with Precise 2D on each of them.

---

### Post by pressureman on 2012-08-22
> **jerrylamos said:**
> Sir, not sure what you're talking about.  This is a 1G netbook Atom N455 happily runnung 1366x768 on today's Quantal daily build i386.  Ubiquity slide show today says I can customize Ubuntu so I'm running LXDE desktop.  This afternoon I was running my amd64 2G notebook 1280x1024 external monitor with yesterday's Quantal amd64 customized with LXDE desktop.  Tonight I'll likely be in the living room running my 3.3 gHz tower 1440x900 monitor with a couple days old Quantal updated, again with LXDE desktop.  I've also got backup (Alpha can crash) partitions with Precise 2D on each of them.

Yep, you've described in considerable detail a few times before how varied your setup is and how often you reinstall Ubuntu. I don't know anyone with as much free time as you, to dedicate to testing the install media. We appreciate your effort. I spend most of my day writing software, and if I had to set up my development environment each day from scratch, I wouldn't have any time left to do any actual work.

I seem to have missed the point of your argument though. I don't run Unity (or LXDE), so I don't have first hand experience with some of the gripes that seem to be arising with lower spec hardware. I run Gnome Shell on a **3 year old** Thinkpad T500 (Core2 Duo 2.66 GHz, 4GB) and I'm completely satisfied with the performance. I may replace the 7200 RPM HDD with an SSD, or I might just wait a bit and replace the whole thing with a new T530.

If people buy bargain bin computers, they honestly can't expect them to survive perhaps one major OS update, before they're obsolete. That's why I spent a reasonable amount on this notebook, but also knew that it would provide adequate performance for at least 4 years (probably more like 5 or 6). Of course, not everybody can afford a top of the line machine (even if purchased wisely, and only every 4-5 years or so). But I really can't understand how a person thinks that a given piece of computer hardware is infinitely upgradeable. There are limits to how far you can go, before the software, which runs adequately on current models, is just simply too demanding for older machines.

What should developers do? Write new software for old hardware? Support an ever decreasing population of 32-bit notebooks? Or write software that is targeted to fully utilise the capabilities of modern hardware? As a developer with about 20 years experience, writing software for all kinds of platforms from Sinclair ZX81 (8-bit, 3 MHz (not GHz!), 2 KB memory), through 80286 and right up to modern multi-core Xeons, I know the difference between writing efficient code, and simply throwing more hardware at the problem. However, the harsh reality of today's software development industry is that writing efficient code *takes longer*. Writing software is expensive. Sure, this stuff is open source, but somebody has either had to write it in their spare time, or maybe they're lucky enough to work for a company that pays them to hack on open source code. But writing software for a customer is expensive. Real expensive. And the developer can either spend longer optimising the code, or, as is often cheaper, may write the code in a different language which is faster to develop with, but requires beefier hardware. If using a different language isn't an option, the developer may simply just be forced to write code as quickly as they can, and forego some of the testing, benchmarking, optimising, and rewriting that go into writing code for Mars Science Laboratory space probes.

It's time for Ubuntu to grow up. There are distros out there (or even just Ubuntu spinoffs) that specifically aim to support lower spec hardware. I don't think it's right to hold back Canonical's flagship OS when there are obvious alternatives available.

---

### Post by ronacc on 2012-08-22
> **vexorian said:**
> 
You don't *have* to upgrade every 6 months, you know.

A normal ubuntu release is supposed to last 1.5 years. 12.04 will be supported for 5 years. After a while of using ubuntu you get tired of all that giberish of upgrading, that's how I kept feisty for 2 years and then 10.10 for 1.5 years.

I know I don't have to and in fact I don't , I'm still running 10.10 on my 2 work boxes , but I DO test continuously , I haven't missed a session since Dapper Drake and a little more consistency in configuration would sure be nice .And as someone mentioned above that would impress comercial CTO's more than 2 boatloads of eyecandy.

---

### Post by cariboo on 2012-08-23
> **ronacc said:**
> I know I don't have to and in fact I don't , I'm still running 10.10 on my 2 work boxes , but I DO test continuously , I haven't missed a session since Dapper Drake and a little more consistency in configuration would sure be nice .And as someone mentioned above that would impress comercial CTO's more than 2 boatloads of eyecandy.

What Canonical offers businesses is a different product from what us regular consumers get. See [here]("http://www.ubuntu.com/business/desktop/remix")

**Note:** You'll have to register in order to download the iso.

---

### Post by effenberg0x0 on 2012-08-23
> **cariboo907 said:**
> What Canonical offers businesses is a different product from what us regular consumers get. See [here]("http://www.ubuntu.com/business/desktop/remix")

**Note:** You'll have to register in order to download the iso.

Thanks for the info Cariboo. By the way, sorry for the lame and OT question but what is this? It's in the page you linked.

[ATTACH]223053[/ATTACH]

I see a bowling Ball and a hand.

Regards,
Effenberg

---

### Post by cariboo on 2012-08-23
> **effenberg0x0 said:**
> Thanks for the info Cariboo. By the way, sorry for the lame and OT question but what is this? It's in the page you linked.

[ATTACH]223053[/ATTACH]

I see a bowling Ball and a hand.

Regards,
Effenberg

You got me, that's what I see too. :-D

---

### Post by effenberg0x0 on 2012-08-23
> **cariboo907 said:**
> You got me, that's what I see too. :-D

I found the meaning, but there's obviously something wrong with my brain because I can't understand it.

[ATTACH]223056[/ATTACH]

**Source:** [http://design.ubuntu.com/downloads?metadata=element-pictogram](http://design.ubuntu.com/downloads?metadata=element-pictogram)

I think I need some sleep... I'll look at it again tomorrow lol

Regards,
Effenberg

PS: And why would he keep playing even with his hand hurt? :( That's a harsh way to cut costs.

---

### Post by Hreinsi on 2012-08-23
A fork and three beans on a plate

---

### Post by Hreinsi on 2012-08-23
I installed 12.10 on my Toshiba A-100 from 2005 or 6, Radeon Xpress 200M Now I have 3d working Can enable cube rotate and more not installed any drivers my self, dont have desktop menus on top bar like edit go and so on. My question is are ther a big bug in Software sources does not open anyone know how to fix that thx

---

### Post by Hreinsi on 2012-08-23
:) Could it be wrong aptdaemon running 045+bzr852

---

### Post by jerrylamos on 2012-08-23
> **pressureman said:**
> Yep, you've described in considerable detail a few times before how varied your setup is and how often you reinstall Ubuntu. I don't know anyone with as much free time as you, to dedicate to testing the install media. We appreciate your effort. I'm a retired main frame computer engineer doing fitness, helping political campaigns, and a pc buff since 1982 and an ubuntu tester sincd Dapper Drake Beta.> I seem to have missed the point of your argument though. I don't run Unity (or LXDE), so I don't have first hand experience with some of the gripes that seem to be arising with lower spec hardware.My point is I'm running very reasonably spec'd hardware with no gripes using LXDE on 12.10 and 2D on 12.04.  My opinion lots of people with good spec hardware run xubuntu, kubuntu, mint, ... instead of Ubuntu's default desktop.  Out of curiosity I'm somewhat following the Gnome Ubuntu efforts.

I do get some juicy bugs with install, look at Phillinux's comment on Daily Build.

---

### Post by ventrical on 2012-08-23
> **pressureman said:**
> Yep, you've described in considerable detail a few times before how varied your setup is and how often you reinstall Ubuntu. I don't know anyone with as much free time as you, to dedicate to testing the install media. We appreciate your effort. I spend most of my day writing software, and if I had to set up my development environment each day from scratch, I wouldn't have any time left to do any actual work.

I seem to have missed the point of your argument though. I don't run Unity (or LXDE), so I don't have first hand experience with some of the gripes that seem to be arising with lower spec hardware. I run Gnome Shell on a **3 year old** Thinkpad T500 (Core2 Duo 2.66 GHz, 4GB) and I'm completely satisfied with the performance. I may replace the 7200 RPM HDD with an SSD, or I might just wait a bit and replace the whole thing with a new T530.

If people buy bargain bin computers, they honestly can't expect them to survive perhaps one major OS update, before they're obsolete. That's why I spent a reasonable amount on this notebook, but also knew that it would provide adequate performance for at least 4 years (probably more like 5 or 6). Of course, not everybody can afford a top of the line machine (even if purchased wisely, and only every 4-5 years or so). But I really can't understand how a person thinks that a given piece of computer hardware is infinitely upgradeable. There are limits to how far you can go, before the software, which runs adequately on current models, is just simply too demanding for older machines.

What should developers do? Write new software for old hardware? Support an ever decreasing population of 32-bit notebooks? Or write software that is targeted to fully utilise the capabilities of modern hardware? As a developer with about 20 years experience, writing software for all kinds of platforms from Sinclair ZX81 (8-bit, 3 MHz (not GHz!), 2 KB memory), through 80286 and right up to modern multi-core Xeons, I know the difference between writing efficient code, and simply throwing more hardware at the problem. However, the harsh reality of today's software development industry is that writing efficient code *takes longer*. Writing software is expensive. Sure, this stuff is open source, but somebody has either had to write it in their spare time, or maybe they're lucky enough to work for a company that pays them to hack on open source code. But writing software for a customer is expensive. Real expensive. And the developer can either spend longer optimising the code, or, as is often cheaper, may write the code in a different language which is faster to develop with, but requires beefier hardware. If using a different language isn't an option, the developer may simply just be forced to write code as quickly as they can, and forego some of the testing, benchmarking, optimising, and rewriting that go into writing code for Mars Science Laboratory space probes.

It's time for Ubuntu to grow up. There are distros out there (or even just Ubuntu spinoffs) that specifically aim to support lower spec hardware. I don't think it's right to hold back Canonical's flagship OS when there are obvious alternatives available.

 I am a certified Pinball Machine/Video game  Repair technician - circa 1975. From 1975 to 1980 the Vector Analog Generators always seemed to handle high speed graphics with the older 8080as. I mean the whole game was actually burned on to the entire mobo.  So one would wonder why those old popular games were so fast at rendering and what the excuses are today with the processors we have now.

---

### Post by pressureman on 2012-08-23
> **jerrylamos said:**
> My point is I'm running very reasonably spec'd hardware with no gripes using LXDE on 12.10 and 2D on 12.04.  My opinion lots of people with good spec hardware run xubuntu, kubuntu, mint, ... instead of Ubuntu's default desktop.

IMHO, anything with less than 2GB these days is "low spec", especially when about 95% of new machines ship with *at least* 4GB, and the trend seems to be moving towards 6 or 8GB. Heck, even my Android phone has a gigabyte of RAM.

Slightly OT: Try selling some old hardware on eBay if you want a reality check. I'm a firm believer that something is only worth what the market will pay for it. Last year I tried selling some perfectly working 10/100 3Com NICs, a PCI SATA controller, and some early PCIe video cards. Advertised them for $1 starting bid, no reserve. *Some* items sold... for $1. Some had no bids at all.

> **ventrical said:**
> I am a certified Pinball Machine/Video game  Repair technician - circa 1975. From 1975 to 1980 the Vector Analog Generators always seemed to handle high speed graphics with the older 8080as. I mean the whole game was actually burned on to the entire mobo.  So one would wonder why those old popular games were so fast at rendering and what the excuses are today with the processors we have now.

Because back then, large chunks of high speed code (particularly in games) were programmed in assembler. Also the graphics back then were much lower resolution and lower colour bit-depth than today, so there were simply a lot fewer bytes to shuffle around. I dabbled with low-level VGA register programming as a teenager, back when the "demo scene" was in full swing. Sure, you could write some nice 320x200 intros with smooth animation at about 25 FPS, as long as you wrote fairly concise x86 asm. There was a hack that made the overscan area of the screen a different colour, and how far down the screen that colour bar reached, indicated how much of the vertical retrace time you were using. As long as you updated the screen within the V-retrace time, you avoided any "tearing".

Comparing that to a modern gaming rig from today, with 1080p and 32-bit colour, is like comparing chalk and cheese. The "excuse" today is that a single game texture is larger than the *entire video RAM* of a machine from 1980. People are no longer content with 25 FPS - they want 60, 120 or even higher. It's all simple math. You can easily work out how many gigabits per second have to be pushed along that PCIe bus.

Also the majority of gaming code these days is C, not assembler. Some highly optimised routines may still have sprinklings of inline asm, but if software houses wrote the entire thing in asm, their competitors would beat them to the market every time.

Software: high performance, rapid development, low resource requirements. Choose any two ;)

---

### Post by effenberg0x0 on 2012-08-23
Hi, 

As we went OT and I still am puzzled about the pictogram (see [the post above]("http://ubuntuforums.org/showpost.php?p=12189928&postcount=62")), I have decided to improve that thing to a more reasonable one.

Original:
[ATTACH]223086[/ATTACH]

Updated:
[ATTACH]223089[/ATTACH]

Regards,
Effenberg

---

### Post by pressureman on 2012-08-23
> **effenberg0x0 said:**
> Hi, 

As we went OT and I still am puzzled about the pictogram (see [the post above]("http://ubuntuforums.org/showpost.php?p=12189928&postcount=62")), I have decided to improve that thing to a more reasonable one.

Aha... so it wasn't a leper's hand with a gangrenous thumb, losing the tips of the fingers.

Good to know.

---

### Post by ronacc on 2012-08-23
looks like its throwing the coins away not saving them !

---

### Post by effenberg0x0 on 2012-08-23
I think that as expensive as bowling can be nowadays (if you pay it "per-hour"), one should stop playing once your hand is clearly cut through. There's a limit to cutting costs - go to a hospital.

A colleague mentioned that "if you caught bowling ball worms, you should take 3 white pills".

Regards,
Effenberg

---

### Post by vexorian on 2012-08-25
Sorry for drifting off the off-topic thread. But, if something will allow unity-3D to have a fallback mode that does not need so many GPU resources, will it at least be possible to opt-in when you have good GPU drivers? 

When I try to give "unity-3D" a chance, I find myself learning that even simple wine apps like Zuma or Bejeweled Twist suffer a noticeable performance hit in comparison with how well they run when compiz is not working.

---

### Post by ventrical on 2012-08-25
I installed a daily alternate today and it loaded Unity 3D by default on a machine that would have nothing to do with it before. (of course using llvmpipe). It was like a Pink Floyd song.. Hello.., Hello .. is there anybody in there... just nod ... etc..  Like a real slow echo .. but then GNOME fall back worked just great.:) lol

 I really liked Unity 2D and the way the icons had this super smooth scrolling. I can't figure out why they could not do that with Unity 3D

---

### Post by jerrylamos on 2012-08-25
> **ventrical said:**
> I really liked Unity 2D and the way the icons had this super smooth scrolling. I can't figure out why they could not do that with Unity 3DTry running top in a terminal maybe 2 windows side by side to see the %CPU that Compiz is using when you do scrolling etc.

My workaround is to do a full 12.10 install then install LXDE on top of it.  Choose Ubuntu (Unity) desktop or LXDE by logging out & in.  LXDE doesn't use Compiz.  Scrolling on this Intel Atom netbook is just fine.

---

### Post by cariboo on 2012-08-25
On my 2 year old self built system, cpu usage goes up by 3 - 4 % when scrolling in chromium. Chromium itself uses more resources when scrolling. Unless compiz uses 100% of your cpu's resources, I don't see what you are complaining about, isn't the cpu there to be used, instead of sitting idle all the time?

---

### Post by fjgaude on 2012-08-25
Hey, neither Chromium or compiz use much CPU percentage while scrolling on my Intel HD4000 box. That box is 19 months old.

---

### Post by VinDSL on 2012-08-25
Hrm...

I just ran Synaptic and noticed several Unity 2D updates.

SUP with that?!?!?

---

### Post by cariboo on 2012-08-25
If you read the package descriptions, you'll see they are just place holders, I'm sure they'll disappear over time.

---

### Post by lolpenguin on 2012-08-26
i.e. Transitional packages so your system doesn't die. They are empty and will get remove.

---

### Post by vexorian on 2012-08-26
> **cariboo907 said:**
> On my 2 year old self built system, cpu usage goes up by 3 - 4 % when scrolling in chromium. Chromium itself uses more resources when scrolling. Unless compiz uses 100% of your cpu's resources, I don't see what you are complaining about, isn't the cpu there to be used, instead of sitting idle all the time?
It is meant to be used by useful things.

---

### Post by VinDSL on 2012-08-26
Seems odd, to me -- Unity 2D transitional packages.

"Transition"  to what?

Transitional packages can usually be removed, since they are no longer needed.

Maybe they're hedging their bet, like Gnome did with Nautilus 3.6

I don't get it...

---

### Post by jerrylamos on 2012-08-26
> **vexorian said:**
> It is meant to be used by useful things.
Agree.  My view, some people are fascinated by a big fancy eye candy cover of a book.  Fancy covers could sell books to some people.  I'm interested in the contents myself, and once open the cover should stay out of the way.  Personal opinion.  Precise 2D and Quetzal LXDE do get out of the way so I have solutions for me.  Hope I'm not treading on the Ubuntu COC.  Ubuntu is all about choices according to the Quantal Quetzal Ubiquity slide show.

---

### Post by VinDSL on 2012-08-26
> **pressureman said:**
> [...] I really can't understand how a person thinks that a given piece of computer hardware is infinitely upgradeable.[...]
Heh!  Maybe it's the "stickers" & "badges", OEMs plaster all over the case.  :D

A co-worker gave me this pristine eMachine etower 667ix, a while back. "NEVER OBSOLETE"


[INDENT][IMG]http://vindsl.com/images/doorstop-snappie-small.png[/IMG][/INDENT]


And, guess what?!?!?

It still runs fine on Puppy Linux 4.3  LoL!

Only thing I had to upgrade was the NIC...

---

### Post by VinDSL on 2012-08-26
> **jerrylamos said:**
> Agree.  My view, some people are fascinated by a big fancy eye candy cover of a book.  Fancy covers could sell books to some people.  I'm interested in the contents myself, and once open the cover should stay out of the way.
True!  And, it works both ways.

The machine I'm typing this on is going on 7 years old.  The CPU was $1000+, the case over $400, blah, blah, blah.

The reason I continue to use it is because of its fancy eye candy looks.

I'm in a GS session right now, but Unity works fine too.  Dittos for LXDE/Openbox.  Every flavor of Ubuntu I've tried works great on this machine.

LXDE looks just as good as Unity and GS, once you apply the same tweaks.

Anyway, I'm in no hurry to upgrade my hardware either.  ;)

---

### Post by kansasnoob on 2012-08-26
> **VinDSL said:**
> True!  And, it works both ways.

The machine I'm typing this on is going on 7 years old.  The CPU was $1000+, the case over $400, blah, blah, blah.

The reason I continue to use it is because of its fancy eye candy looks.

I'm in a GS session right now, but Unity works fine too.  Dittos for LXDE/Openbox.  Every flavor of Ubuntu I've tried works great on this machine.

LXDE looks just as good as Unity and GS, once you apply the same tweaks.

Anyway, I'm in no hurry to upgrade my hardware either.  ;)

The puter price reminds me of an old Micron that's currently collecting dust in my closet. I think it cost me nearly a thousand smackeroos in the late 90's.

Surprisingly it still works, but sooooooooo slow ;)

---

### Post by xeizo on 2012-08-26
I've trashed all old computer equipment, I don't have place for it, must have had close to a hundred PC:s over the years including Amigas ...

Now the oldest running is a C2Q, this Linux-box, which I downgraded graphics on to save power(changed from GTX470 which is now collecting dust to a GT430 biosmodded to GT440 - consumes 3W in desktop use - almost ideal for Linux-use!). Sysdrive is a Crucial M4 SSD and 8GB of old DDR2-RAM, very fast for Linux-stuff :) 
Windows is running on a Sandy Bridge i7/GTX680.

Nevertheless, there is lots of situations where it is nice to be able to run a desktop on not so powerful hardware. And more to come, ARM desktop boards may be an interesting future. Extremely low power in smaller than mini-ITX cases :guitar:

---

### Post by VinDSL on 2012-08-26
> **kansasnoob said:**
> The puter price reminds me of an old Micron [...]

Surprisingly it still works, but sooooooooo slow ;)
That's a true concern, with older hardware.  Time is money.

The most resource-intensive action I perform is video encoding.

Creating a video on this machine is quick enough, but when I do the final encoding, I move if off to my laptop, which is considerably faster, e.g. less time consuming.

> **xeizo said:**
> I downgraded graphics to save power [...] consumes 3W in desktop use [...]
Yes, that's another concern. for me.

I didn't realize how much electricity this thing uses, until I hooked it up to a "Kill-A-Watt" amp/watt meter -- 200 watts, sitting idle at the desktop -- regardless of the "power saving" state.  By comparison, my monstrous side-by-side refrigerator only uses 260-watts, when the compressor is running.  

Beauty comes at a cost.  LoL!

Truthfully, I probably won't upgrade my desktop hardware until the mobo fails, but the thought of needlessly wasting all that money on electricity is eating away at my psyche.

---

### Post by pressureman on 2012-08-26
> **VinDSL said:**
> Yes, that's another concern. for me.

I didn't realize how much electricity this thing uses, until I hooked it up to a "Kill-A-Watt" amp/watt meter -- 200 watts, sitting idle at the desktop -- regardless of the "power saving" state.  By comparison, my monstrous side-by-side refrigerator only uses 260-watts, when the compressor is running.

Modern hardware (especially newer Intel chips) have made great strides in energy efficiency. If you're willing to tolerate "middle of the road" performance, it's not uncommon to see idle power consumption drop to between 20-30 W.

Last year I discovered these little embedded PCs - [http://www.pokini.de/cms/pokini/index.php?id=modell-uebersicht&L=1](http://www.pokini.de/cms/pokini/index.php?id=modell-uebersicht&L=1)

They're Intel Atom-based (unfortunately 32-bit, but up to 2 GHz), have up to 2GB RAM, and happily run Windows 7 (or Linux of course) - and all that is powered by an 18 W external power brick. The best part of all is that they have no fan and are thus completely silent - ideal for a home micro-server.

---

### Post by kansasnoob on 2012-08-26
> **pressureman said:**
> Modern hardware (especially newer Intel chips) have made great strides in energy efficiency. If you're willing to tolerate "middle of the road" performance, it's not uncommon to see idle power consumption drop to between 20-30 W.

Last year I discovered these little embedded PCs - [http://www.pokini.de/cms/pokini/index.php?id=modell-uebersicht&L=1](http://www.pokini.de/cms/pokini/index.php?id=modell-uebersicht&L=1)

They're Intel Atom-based (unfortunately 32-bit, but up to 2 GHz), have up to 2GB RAM, and happily run Windows 7 (or Linux of course) - and all that is powered by an 18 W external power brick. The best part of all is that they have no fan and are thus completely silent - ideal for a home micro-server.

It's great to mention energy usage :guitar:

I use a "kill-a-watt" device to see what kind of bang I'm actually getting for the buck. With this low-end set of hardware I get very acceptable VGA graphics watching flash video for about the price of running a 40 watt light bulb:

> AMD Sempron Processor LE-1250 @ 2.2 GHz
nVidia C61 [GeForce 7025 / nForce 630a] (rev a2)
nVidia MCP61 High Definition Audio (rev a2)
nVidia MCP61 Ethernet (rev a2)
2GB DDR2 RAM

Idle it uses about 2 to 4 watts. And watching an actual DVD using either Totem or VLC uses about 24 to 28 watts. To me that's pretty darn energy efficient.

This Intel set is even more energy efficient:

> Intel Atom CPU  230 @ 1.60GHz
Intel 82945G/GZ Integrated Graphics Controller (rev 02)
Intel N10/ICH 7 Family High Definition Audio Controller (rev 01)
Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
2GB DDR2 RAM

But Flash Video is a bit gorfy :(

And don't even get me started on the 18 boxes I maintain with VIA P4M800 graphics - seemed like a good buy 6 or 7 years ago ](*,)

---

