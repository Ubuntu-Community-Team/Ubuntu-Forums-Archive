---
title: "Unity 2D To Go Away In Ubuntu 12.10"
date: 2012-05-10
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ergo-proxy on 2012-05-10
At least that's what Phoronix says.... any official comments on that? IMO lot's of people will leave Ubuntu if it comes true...

---

### Post by Shadius on 2012-05-10
I read an article stating this too. :( Not cool.

---

### Post by fluteflute on 2012-05-10
Older hardware will now be supported by the main Unity implementation. This is good news!

See: [http://askubuntu.com/q/134346/866](http://askubuntu.com/q/134346/866)

---

### Post by ergo-proxy on 2012-05-10
> **fluteflute said:**
> Older hardware will now be supported by the main Unity implementation. This is good news!
 
See: [http://askubuntu.com/q/134346/866](http://askubuntu.com/q/134346/866)
 
Good news only if it's gonna work better than Unity 2d thoughI'm a bit pesimistic but who knows... :roll:

---

### Post by kansasnoob on 2012-05-10
Doesn't this have something to do with changing to Clutter/Mutter?

I'd personally love to see us distance ourselves from Compiz as much as possible :)

It'll be fun to watch.

---

### Post by grahammechanical on 2012-05-10
Ubuntu Devloper Summit (UDS) is still going on. Here is a link to the sessions

[http://summit.ubuntu.com/uds-q/]("http://summit.ubuntu.com/uds-q/")

See if you can find a session discussing about using Clutter. It is my understanding that the blueprints that come out of UDS are the plans to be worked to during the development cycle.

Regards.

---

### Post by pressureman on 2012-05-10
> **kansasnoob said:**
> Doesn't this have something to do with changing to Clutter/Mutter?

I thought it was more to do with LLVMpipe. Phoronix reported last year about how Fedora 17 already uses LLVMpipe to allow GNOME Shell to run on non-OpenGL hardware, instead of using the GNOME fallback session.

I'm guessing that the same principle could be applied in the case of Unity 3D.

[http://www.phoronix.com/scan.php?page=news_item&px=MTAxMjI](http://www.phoronix.com/scan.php?page=news_item&px=MTAxMjI)

---

### Post by philinux on 2012-05-10
> **ergo-proxy said:**
> At least that's what Phoronix says.... any official comments on that? IMO lot's of people will leave Ubuntu if it comes true...

Only Might just now. We'll see how this pans out in a few days.

[http://ubuntuforums.org/showpost.php?p=11921051&postcount=5](http://ubuntuforums.org/showpost.php?p=11921051&postcount=5)

---

### Post by ronacc on 2012-05-10
it would be great if unity 3d went away too .

---

### Post by pressureman on 2012-05-10
> **ronacc said:**
> it would be great if unity 3d went away too .

My thoughts too, but I didn't want to start a desktop environment holy war.

Seriously though, it's disheartening to see how much resource goes into developing Unity, when there are outstanding general bugs, some of them years old, and some of them relatively easy to fix... but they take a back seat to adding more bling to Unity lenses or HUD or whatever else the latest gimmick is.

Some people actually don't faff about on Youtube or Twitter all day.

---

### Post by ronacc on 2012-05-10
I don't want to start a holy war either but I just can't resist getting a shot in from time to time . I agree about the bugs , my pet peeve is that disaster they call ubiquity .

---

### Post by grahammechanical on 2012-05-10
Might I add a link here by way of getting us back on track?

[http://www.markshuttleworth.com/archives/date/2011/08]("http://www.markshuttleworth.com/archives/date/2011/08")

Look at the heading Under the Hood

> There&#8217;s something of a competition under way between proponents of the QML based Unity-2D, who believe that the GL support here is good enough to compete both at the high end and on the low end, and the GL-heads in Unity-3D, who think that the enhanced experiences possible with raw GL access justify the additional complexity of working in C++ and GL on the metal. Time will tell! Since a lot of the design inspiration for Unity came from game interfaces, I lean to the &#8220;let&#8217;s harness all the GL we can for the full 3D experience&#8221; side of the spectrum, but I&#8217;m intrigued with what the QML team are doing.

Has that view changed in less than a year? I see a difference between session notes for a UDS session and work items of a UDS session.

The work items are what are to be worked on during the development period. The session notes are just topics for discussion.

Remember. Ubuntu is not a democracy. Who makes the important decisions?

Regards.

---

### Post by ronacc on 2012-05-10
> **grahammechanical said:**
> Might I add a link here by way of getting us back on track?

[http://www.markshuttleworth.com/archives/date/2011/08]("http://www.markshuttleworth.com/archives/date/2011/08")

Look at the heading Under the Hood



Has that view changed in less than a year? I see a difference between session notes for a UDS session and work items of a UDS session.

The work items are what are to be worked on during the development period. The session notes are just topics for discussion.

Remember. Ubuntu is not a democracy. Who makes the important decisions?

Regards.

it seems sometimes like a cross between a benevolent dictatorship and total anarchy . but to answer your question , ultimately the users make the important decision , to use or to not use Ubuntu .

---

### Post by kansasnoob on 2012-05-10
> **ronacc said:**
> I don't want to start a holy war either but I just can't resist getting a shot in from time to time . I agree about the bugs , my pet peeve is that disaster they call ubiquity .

Well ubiquity has nothing to do with Unity, but Colin Watson did indicate that he seriously wanted to do another intense rebuild of ubiquity and bring back "use largest continuous free space" as a separate option.

Of course a lot of that depends on cooperation from the design team and the proper allocation of dev time by Canonical. We can keep our fingers crossed ;)

Regarding Unity I just find it working OK now, once in a while a little bit of hide-n-seek until I google an answer but it seems pretty solid to me.

---

### Post by 3Miro on 2012-05-10
My understanding was that Unity 2D was just something quickly put together for people with weak hardware or driver issues. I don't think the devs meant for Unity 2D to be full time environment and if it happens to work well for some people, then it is more by accident as opposed to design.

In 12.04, you can run Unity 3D with Noveau, which means that you can run Unity 3D with default drivers on any decent graphics card (AMD, Nvidia or Intel). Combine this with the extended 5 year support for 12.04, then Canonical can easily just ditch Unity 2D for 12.10. If you have old hardware or just like Unity 2D, stay with 12.04 LTS. Newer machines will just run Unity 3D right out of the box.

A question to the people using Unity 2D as a full time environment: 

Unity 2D is faster (due to lack of 3D effects) and perhaps more stable (sometimes). Other than that, what does Unity 2D have that isn't included in Unity 3D?

---

### Post by ronacc on 2012-05-10
> **kansasnoob said:**
> Well ubiquity has nothing to do with Unity, but Colin Watson did indicate that he seriously wanted to do another intense rebuild of ubiquity and bring back "use largest continuous free space" as a separate option.

Of course a lot of that depends on cooperation from the design team and the proper allocation of dev time by Canonical. We can keep our fingers crossed ;)

Regarding Unity I just find it working OK now, once in a while a little bit of hide-n-seek until I google an answer but it seems pretty solid to me.

the thing about bugs was in response to pressureman's comment on the previous page .

I have no problem with unity working it is the hideous interface I cannot stand , I only use unity on first boot long enough to install gnome shell and reboot before I puke ( would be hard on the keyboard) :lolflag:

---

### Post by jbicha on 2012-05-10
There are no plans to convert Unity to Clutter/Mutter.

If there are bugs that are easy to fix, have you submitted merge proposals or patches for them?

---

### Post by rg4w on 2012-05-10
I had a brief chat with Ted Gould about this at UDS on Tuesday, and while nothing is set is stone right now he did suggest there would be many advantages to merging resources for the two projects, having them fork only at the rendering stage but in all other respects having one Unity that maintains feature parity for everyone regardless of graphics capabilities.

---

### Post by ronacc on 2012-05-10
I saw the logic many cycles back when I suggested that the .iso be moved to a dvd to avoid having to leave out packages to keep it at cd size and was told in no uncertain terms that that would prevent people especially in 3rd world countries whith older hardware from obtaining Ubuntu and that Ubuntu would not do that . I see no logic in abandoning them now for the sake of eyecandy .

---

### Post by rg4w on 2012-05-10
> **ronacc said:**
> I saw the logic many cycles back when I suggested that the .iso be moved to a dvd to avoid having to leave out packages to keep it at cd size and was told in no uncertain terms that that would prevent people especially in 3rd world countries whith older hardware from obtaining Ubuntu and that Ubuntu would not do that . I see no logic in abandoning them now for the sake of eyecandy .
Thankfully it seems no one intends to do that.

From what I hear, all that's being planned is for the end of 2D Unity as a separate package, moving the support it provides for older graphics subsystems into the main development branch.

---

### Post by jerrylamos on 2012-05-10
> **fluteflute said:**
> Older hardware will now be supported by the main Unity implementation. This is good news!

See: [http://askubuntu.com/q/134346/866](http://askubuntu.com/q/134346/866)

S-l-o-w-l-y with lots and lots of C-o-m-p-i-z wasted cycles

fuzzy, foggy, indistinct, h-u-g-e dash icons, shadow borders, dash program titles spaced way out over the screen so someone's big fat finges can touch them, pictures for those that can't read.

Choices.  I'm doing Unity-2D on my fast tower.  I try -3D on install and logout/login unity-2D. I run lubuntu on the notebooks cracking fast, for the things I usually do.

Usual Microsoft Mantra, buy a new bigger faster more expensive pc with Windoze 8.  Ubuntu is now down the same path and catching up.

So far I've been able to find something on ubuntu I run, -3D is not one of them.  Choices.

Jerry

---

### Post by jerrylamos on 2012-05-10
> **3Miro said:**
> Unity 2D is faster (due to lack of 3D effects) and perhaps more stable (sometimes). Other than that, what does Unity 2D have that isn't included in Unity 3D?

-2D doesn't have Compiz overhead.  Compiz has absolutely nothing to do with my applications but is happy to chew up processor cycles in the background even when I'm running full screen applications.

-2D doesn't have Compiz launchpad bugs either.

Jerry

---

### Post by jerrylamos on 2012-05-10
> **rg4w said:**
> From what I hear, all that's being planned is for the end of 2D Unity as a separate package, moving the support it provides for older graphics subsystems into the main development branch.

The "main development branch" is dedicated to "compiz eye candy" that doesn't have anything to do with running internet, office, mail, video, ... except "compiz eye candy" chews up lots of processor cycles taking them away from the applications I want to run.

So far I've had choices.

Jerry

---

### Post by buzzmandt on 2012-05-10
(best Seinfeld voice)... "That's a shame"

Well, any of you that know me know I'm a kde fan.  There are things i like about unity, though, and one of those things is unity 2d.

On my laptop (64bit 2.2, 2 Gigs ram, Intel mobile 4 gm45 graphics card) unity 3d is very sluggish and quite slow to respond. kde with tons of effects on is much faster (not flaming just saying).  

Unity 2d is actually quite responsive and snappy.  I think it even looks better too.  

Anyway, I'm kinda an outsider now looking in.  Unity isn't for me but I  still love the *buntu base for my kubuntu system.

---

### Post by 3Miro on 2012-05-10
> **jerrylamos said:**
> -2D doesn't have Compiz overhead.  Compiz has absolutely nothing to do with my applications but is happy to chew up processor cycles in the background even when I'm running full screen applications.

Not in my experience. You can turn off most of the compiz effects and then it is no more or less hungry than the rest of the Windows Managers, in fact it does the exact same amount of work, just using the GPU as opposed to CPU. I have tested this on pretty low end machines (integrated Intel GMA with Pentium Dual Core), compiz is about as resource demanding as Metacity or Xfwm4. Furthermore, it is considerably smoother.

> 

-2D doesn't have Compiz launchpad bugs either.

Jerry

I said other than hitting a bug. A bug is a perfectly good reason to use Unity 2D, but with more people working on Unity 3D, those would be resolved faster.

---

### Post by pressureman on 2012-05-11
> **jbicha said:**
> If there are bugs that are easy to fix, have you submitted merge proposals or patches for them?

Yup. Here's an example. [https://bugs.launchpad.net/ubuntu/+source/gnutls26/+bug/937537](https://bugs.launchpad.net/ubuntu/+source/gnutls26/+bug/937537)

Bug opened four months before 12.04 was released. All it needed was an updated package to be synced from Debian. But 12.04 was released without the bug even ever being assigned to anybody (and still isn't).

Easy pickings like that, which get overlooked in favour of a new Unity lens, make me sad.

---

### Post by kansasnoob on 2012-05-11
> **jbicha said:**
> There are no plans to convert Unity to Clutter/Mutter.

If there are bugs that are easy to fix, have you submitted merge proposals or patches for them?

I got the idea about clutter here:

[http://www.webupd8.org/2012/05/uds-q-news-unity-2d-might-go-away-more.html#more](http://www.webupd8.org/2012/05/uds-q-news-unity-2d-might-go-away-more.html#more)

I may misunderstand the relationship between Clutter and Mutter though.

---

### Post by mswift on 2012-05-12
I'd be glad, if people stopped talking about compiz as eye-candy only.
This is simply not true. There are many useful plugins which are not available in Unity-2d. There's no Windows spread (Super +W), and I really don't know how people can cope without compiz' grid plugin.

FWIW, on my 4 year old laptop, Unity-2d is neither faster nor easier on my CPU.

---

### Post by philinux on 2012-05-12
Closed now. Please see [http://ubuntuforums.org/showthread.php?t=1978803](http://ubuntuforums.org/showthread.php?t=1978803)

---

