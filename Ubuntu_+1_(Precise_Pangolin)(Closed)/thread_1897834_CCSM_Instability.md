---
title: "CCSM Instability"
date: 2011-12-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-12-20
CCSM was pretty stable for me until some days ago: I could activate/deactivate plugins normally. Now Compiz crashes practically all the times I try to do it, like it was in OO. 

Attempting to restart Compiz/Unity at a VT gives me the old "Unknown format " error. The alternative is to use the VT to load DISPLAY=:0.0 metacity --replace&, go back to the session and call unity --replace& using a terminal.

The Bailer plugin, which was working to load Metacity automatically when Unity/Compiz crashed is also not working anymore.

Is someone else seeing this behaviour?

---

### Post by mc4man on 2011-12-20
With the exception of quicklists from X-Ayatana-Desktop-Shortcuts=  compiz/ccsm is working ok here.
(2nd use of any of those quicklists causes a compiz crash or no response

Though it can at times still not recover fully  from some actions like enabling text & scale addons, though after a log out/in all is fine or as fine as compiz is currently capable of.

---

### Post by VinDSL on 2011-12-20
Working okay here, e.g. haven't noticed any change(s), but...

I'll have to admit, CCSM is like playing with dynamite, these days, so I don't get too experimental.  ;)

---

### Post by ventrical on 2011-12-20
I just enabled <watereffect> to check. It does crash but recovers really quick. Other than that it is running fairly well.

---

### Post by effenberg0x0 on 2011-12-20
> **ventrical said:**
> I just enabled <watereffect> to check. It does crash but recovers really quick. Other than that it is running fairly well.

@ventrical Does it always recovers for you? I estimate it only recovers here about 50% of the time.

I am probably running a buggy plugin: Situation seems worse here than for you guys.

---

### Post by ventrical on 2011-12-20
> **effenberg0x0 said:**
> @ventrical Does it always recovers for you? I estimate it only recovers here about 50% of the time.

I am probably running a buggy plugin: Situation seems worse here than for you guys.


Give me a few ideas to try.... so I can emulate what you  are doing. I mean CCSM works different  on may of my systems.  On my Dell inspiron with a fresh raw alpha install it has a quick recovery from crash... give me some scripts and I'll vid them.

---

### Post by ventrical on 2011-12-20
Ok.. you got to be patient .. it takes about 10 seconds for it to crash after a plugin is enabled.

 This is on a Dell Inspiron B130.

[http://www.youtube.com/watch?v=ZqMrqdrYoWw](http://www.youtube.com/watch?v=ZqMrqdrYoWw)


btw .. that is from a fresh alpha Precise install fully updated.

---

### Post by ventrical on 2011-12-20
And this one here with GForce Nvidia 218 on an Intel Tower 2.6 GHz

[http://www.youtube.com/watch?v=pz7SpN7KfxM](http://www.youtube.com/watch?v=pz7SpN7KfxM)

 on this one I chose the <water effect>... 

It recovers  lot faster than Oneiric did.

This is a Precise fully updated transition.

---

### Post by ventrical on 2011-12-20
> **effenberg0x0 said:**
> CCSM was pretty stable for me until some days ago: I could activate/deactivate plugins normally. Now Compiz crashes practically all the times I try to do it, like it was in OO. 

Attempting to restart Compiz/Unity at a VT gives me the old "Unknown format " error. The alternative is to use the VT to load DISPLAY=:0.0 metacity --replace&, go back to the session and call unity --replace& using a terminal.

The Bailer plugin, which was working to load Metacity automatically when Unity/Compiz crashed is also not working anymore.

Is someone else seeing this behaviour?

  I had the Bailer Plugin enabled on a system that was an Oneiric transition to Precise using an ATi Radeon... It took a little longer to recover but no probs otherwise.

---

### Post by effenberg0x0 on 2011-12-20
For example: 
Plugin "Opacity, brightness, Saturation" is enabled. If I disable it, compiz crashes almost 100% of times, meaning no matter how much I wait, the system won't became usable again.

Plugin Desktop Wall: If I deactivate it, the system restores quickly. But then if I activate it,  crash again, no restore this time.

---

### Post by ventrical on 2011-12-20
> **effenberg0x0 said:**
> For example: 
Plugin "Opacity, brightness, Saturation" is enabled. If I disable it, compiz crashes almost 100% of times, meaning no matter how much I wait, the system won't became usable again.

Plugin Desktop Wall: If I deactivate it, the system restores quickly. But then if I activate it,  crash again, no restore this time.

 Ok .. I'll give it a whirl :)

hehehe

edit*  yes ..as for Desktop wall .. there is  a conflict with Unity Plugin and 3dCube rotate so it will definitely foobar the system.

  I currently have cube and rotate enabled with Unity. I'll enable Desktop Wall and see what happens 

Oy!!!!

---

### Post by ventrical on 2011-12-20
I enabled desktop wall and it crashed and I could not open CCSM correctly .. the min/max/x border was gone and it overlayed some of my screenshots when I logged back on.

*edit*

Desktop wall will not enable but I have all my CCSM settings working and system is up and running. Definitely some serious bug here.

---

### Post by mc4man on 2011-12-20
> **effenberg0x0 said:**
> For example: 

Plugin Desktop Wall: If I deactivate it, the system restores quickly. But then if I activate it,  crash again, no restore this time.

Well if you were using unity that would disable the unity plugin - at least here then re-enabling both does work, though also produces a crash report - 
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/868868](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/868868)

There are numerous possible compiz 'crashes' - a number are supposedly fixed in the upcoming unity upgrade, ect
[https://launchpad.net/unity/4.0/4.26.0](https://launchpad.net/unity/4.0/4.26.0)

Some additional whenever nux does a bug fix upgrade & probably some more when compiz upgrades, though it's likely ccsm will never be completely trouble free

Edit: - so if I disable bailer & detection it crashes with this report - but does restore, ie. the crash doesn't mean much
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/833729](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/833729)

There's probably a compiz crash for every day of the year, most of which don't matter

---

### Post by effenberg0x0 on 2011-12-20
Guys, I don't think it's wise to ship compiz/ccsm the way it is now for the LTS. OK, we had some days in which it seemed to be more stable (less crashes). But, in the end, the thing is unstable and has been like this since OO Alpha at least. 

Although it looks like ccsm won't be a default in PP, it's fairly obvious that users will download it and also that helpers will have users download it as a way to activate Unity Plugin when it mysteriously deactivates for good.

Unity, loaded as a plugin, relies heavily on Compiz stability. It's not just some eye-candy alternative: It's basic/primary so we can use Unity.

Compiz/CCSM should receive some increased attention. Rapidly browsing Launchpad I saw some unmerged reports that seem to refer to the same issues. Not many things are to be fixed or fixed anyway. Reports, as usual, aren't always that useful.

Maybe if we do some triaging to merge everything that relates to it, try to put as much of it in the same report and do some noise in it, we can devs attention to give it some focus? 

What do you say if we designate a compiz-week, in which each of us will voluntarily:

[LIST]
[*]Extensively test compiz/ccsm to find out exactly what the bugs are, the error messages, with each plugins, etc. We can divide the work load.
[*]Browse the forum collecting threads that describe users experiences with broken compiz/ccsm that appear to be similar to what we detected.
[*]Browse Launchpad, to collect the reports that are likely about compiz/ccsm
[*]Triage-merge and add links to forum threads, plus our comments into the (then) huge Launchpad report.
[*]Use our brains collectively in a thread here, using the material we collected, to try to get to the bottom of it (where the problems are, which are them, etc).
[/LIST]
Nothing is mandatory, each one's performance will not be measured/judged, etc. It will be just a group of guys trying to get to the bottom of a problem and get devs attention to it.


If you prefer, we can define to do it after Christmas / New Years, so more people can participate on it. There's no rush, we still have time until PP release, of course.



Opinions? How do you feel about having "thematic" bug track/test weeks every now and then like this one I'm proposing?

---

### Post by ventrical on 2011-12-21
Hi Ya effenberg,

  I am all for this but I just want to point out that some of us <enthusiastically>  spent a lot of time doing the exact same thing during Oneiric alpha/beta testing and those persistent crash bugs are still there !! I think it is a no brainer that - compiz NOT working =s completely unstable UNITY! So I can certainly face the fact that  the success of Precise Pangolin DEPENDS on COMPIZ! Not having CCSM as a side bar that is functioning properly  really defeats the whole concept of having compiz as a major depend in the first place.

  In earlier versions of Ubuntu (ie; Lucid) there are many features that  function well like having different wallpapers on different desktops - not so with Natty/Oneiric/Precise. But then these features mentioned  have to be tweaked with the gconf? editior so that Nautalis <show desktop> can be disabled so the effect will work !

 Getting compiz to work properly , even in older versions, demands a wider inoperability from several different depends. In a nutshell, it's a quagmire.

 I'm in !+  :)

---

### Post by ventrical on 2011-12-21
> **effenberg0x0 said:**
> Guys, I don't think it's wise to ship compiz/ccsm the way it is now for the LTS. 

What do you say if we designate a compiz-week, in which each of us will voluntarily:

If you prefer, we can define to do it after Christmas / New Years, so more people can participate on it. There's no rush, we still have time until PP release, of course.

   Unless Canonical, the Unity devs and the Compiz devs really address this issue then it is apparent that Precise will inherit all the bugs that are currently running or new bugs that will emerge as older bugs are isolated and worked around.

  As we say in Canada , these problems were suppossed to be fixed yesterday !  I think the solutions are simple but for some reason it appears that  the devs would rather sweep  these depend problems under the carpet.

  I would suggest - as I did some months ago - act now on these problems.

** edit** Just a side note .. I do not think that CCSM is supported by Canonical - so if a user downloads it they are basically on their own.

---

### Post by effenberg0x0 on 2011-12-21
> **ventrical said:**
> Hi Ya effenberg,

  I am all for this but I just want to point out that some of us <enthusiastically>  spent a lot of time doing the exact same thing during Oneiric alpha/beta testing and those persistent crash bugs are still there 

This is exactly what is frustrating to me. I mean, are we really gonna go through general help saying the same things over and over again? "Switch to a VT and run DISPLAY=:0.0 unity --reset", "reset your profile", "your Unity plugin is deactivated", etc?

But what plays in our favour now is that they recently created the concept of alpha users, associated with a goal of making even the alpha releases usable and stable. During OO we couldn't do much, as we would always think that they would focus on those bugs until OO release day. Now we can ask them to make the alpha better for users now, by focusing on these glitches.

> **ventrical said:**
> ** edit** Just a side note .. I do not think that CCSM is supported by  Canonical - so if a user downloads it they are basically on their  own.
Users didn't play a part in choosing compiz as the base for Unity. And ubuntu devs haven't added a way in gnome-control-center for us to configure unity, so ccsm is needed, no matter if it is supported or not, it's needed as of now. When  they did chose compiz as the base, I believe they probably got in touch with Compiz/ccsm people  and, probably, studied and got to know Compiz/ccsm source from inside  out. So if they want to have stable alphas, they should upgrade the household  stuff like Unity, nux, etc either by keeping it compatible to current  compiz/ccsm code or get in touch with compiz/ccsm guys so they quickly update  their code. That can't be happening, otherwise we wouldn't be seeing the same bugs since OO.

---

### Post by ventrical on 2011-12-21
One simple solution would be to cut 'n drop certain effects that , while working well with earlier Ubuntu versions, are known to break Unity in later versions! This would not take a complete re-write. It appears that the current CCSM template 'n concept is just being rolled over and on up from previous versions. This would make for some really weird kernel work-a-rounds to keep this thing running . I can tell that they are doing this by the way the Windows Decorations <borders> are working. It just a really horrible and sloppy patch.  

  I can say , however, that Precise alpha is working really well here. I shouldn't complain , really, but thinking ahead, I think it is important to get on these bugs which may come back on release day and make for a really sad debut.

---

### Post by ventrical on 2011-12-21
> **effenberg0x0 said:**
> This is exactly what is frustrating to me. I mean, are we really gonna go through general help saying the same things over and over again? "Switch to a VT and run DISPLAY=:0.0 unity --reset", "reset your profile", "your Unity plugin is deactivated", etc?

But what plays in our favour now is that they recently created the concept of alpha users, associated with a goal of making even the alpha releases usable and stable. During OO we couldn't do much, as we would always think that they would focus on those bugs until OO release day. Now we can ask them to make the alpha better for users now, by focusing on these glitches.


Users didn't play a part in choosing compiz as the base for Unity. And ubuntu devs haven't added a way in gnome-control-center for us to configure unity, so ccsm is needed, no matter if it is supported or not, it's needed as of now. When  they did chose compiz as the base, I believe they probably got in touch with Compiz/ccsm people  and, probably, studied and got to know Compiz/ccsm source from inside  out. So if they want to have stable alphas, they should upgrade the household  stuff like Unity, nux, etc either by keeping it compatible to current  compiz/ccsm code or get in touch with compiz/ccsm guys so they quickly update  their code. That can't be happening, otherwise we wouldn't be seeing the same bugs since OO.

I recall during OO testing that georgjo dropped in with the experimental CCSM PPA...  I'll see if I can find it ... and I agree ... CCSM is needed and Canonical should embrace that if Unity is going to remain their flagship DE.

---

### Post by ventrical on 2011-12-22
I haven't found that link yet but a lot of other interesting stuff.

---

### Post by ventrical on 2011-12-22
Here is a small list of some of the compiz discussions from the most recent release of Ubuntu. Perhaps  beta testers here can use the data posted there as reference data for Precise.

[http://ubuntuforums.org/showthread.php?t=1852105](http://ubuntuforums.org/showthread.php?t=1852105)

[http://ubuntuforums.org/showthread.php?t=1856104](http://ubuntuforums.org/showthread.php?t=1856104)

[http://ubuntuforums.org/showthread.php?t=1854910](http://ubuntuforums.org/showthread.php?t=1854910)

[http://ubuntuforums.org/showthread.php?t=1855350](http://ubuntuforums.org/showthread.php?t=1855350)

[http://ubuntuforums.org/showthread.php?t=1854586](http://ubuntuforums.org/showthread.php?t=1854586)

[http://ubuntuforums.org/showthread.php?t=1849694](http://ubuntuforums.org/showthread.php?t=1849694)

---

