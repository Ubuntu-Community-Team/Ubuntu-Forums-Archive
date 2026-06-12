---
title: "Ubuntu Is Heading Toward A Rolling Release"
date: 2015-05-04
forum: Ubuntu, Linux and OS Chat
---

### Post by craig10x on 2015-05-04
Looks like main edition ubuntu will have the optional rolling release style model available by 16.04 LTS (if you prefer that and i sure do) and there will be two versions (regular and snappy)...At that time, we should also have a stable release of Unity 8 and mir as well...Next year looks pretty exciting for Ubuntu :D

We should know a lot more during and after the upcoming conference, but meanwhile, here's a neat article from softpedia about it:
[http://news.softpedia.com/news/Ubuntu-Is-Slowly-Moving-Towards-the-Rolling-Release-Model-480083.shtml](http://news.softpedia.com/news/Ubuntu-Is-Slowly-Moving-Towards-the-Rolling-Release-Model-480083.shtml)

---

### Post by monkeybrain20122 on 2015-05-04
I don't think snappy is "rolling" in the sense of Arch. If I understand correctly it allows you to install the latest and greatest user end software but the core is not upgraded (so stability of the core will not be compromised like in a true rolling release) Snappy will also allow multiple versions of the same software since each instance is isolated with its own libs. My questions are  will the system become very big like Windows, and will the separation of /home and / still make sense? (or the / partition will be very small since all applications will be installed in /home without sudo since they are sandboxed) What about upgrading core components like kernel and video driver (which is possible with ppa now)?

---

### Post by craig10x on 2015-05-04
In the article, they do mention that core components can be upgraded as well (and in fact, if they cause any regressions, they can be rolled back which i believe is something you can't do with your average rolling release distro)...so, sounds to me like they are talking full rolling model...working in much the same was as you android phone gets new apps, and even the entire system can be upgraded as well...And the article says that they wouldn't really need to have the 6 month versions anymore, just updated isos periodically for snappy version of ubuntu for those who are installing "fresh" (much like the rolling releases already do)...

Logically, they would probably just have a regular LTS release every 2 years (as is already the case) and Snappy Rolling Ubuntu with new iso images every 6 months for those installing clean...and will considerable cut back on their work as they would no longer need to do the 6 month versions...They could concentrate on LTS and new features and changes for snappy...

---

### Post by grahammechanical on 2015-05-04
It is the core components that "roll" with each transactional update. And the system will detect update failures and roll back automatically. According to the graphic used by Mark the kernel will be a snap and so will the OS. They will be read only and they will get the transactional updates.

It is not "rolling" in the sense that I understand the Arch method to be a rolling release. But I do not mind. As for the apps they will be updated by the app developer and published in the app store just as it is done on the Ubuntu phone. So, it will indeed be possible to run more than one version of an app. As Mark put, a stable version and a development version.  And of course it will all take up space.

PPAs will not be necessary because that kind of software can be published as a snap app. Now, flow charts are one thing but getting it all working is something else and it remains to be seen how it will all work out. But it does make for a very interesting next 12 months.

I cannot wait to install the first Ubuntu Snappy Personal ISO image and see it roll on.

Regards.

---

### Post by mastablasta on 2015-05-05
sounds interesting. but windows has this feature for decades... more or less stable core and upgrading only apps.

---

### Post by Bucky Ball on 2015-05-05
Hear it from the horses mouth at the [pre-conference webcast]("https://plus.google.com/hangouts/onair/watch?hid=hoaevent%2Fcdpv7h8eqipl367pht8mc1oscj8&wpsrc=yta&ytl=9IfgX-k7Hag") by Mark Shuttleworth from last night. That gives a full explanation. This does not. ;)

Snappy is a completely different approach so attempting to equate the way things work now with how they work (and are projected to continue working) in Snappy is like comparing apples and oranges.

From what I can see, Snap Apps are a great idea and concept, but there's a LONG way to go yet and it is shifting sands. It's like this: you can be (or this is the idea) on the Snappy stable tree where things will not be a lot different to what they are now, on the surface, for the average user, or you can be on the Snappy dev tree, which will be, in effect, a rolling release. So, for most users, nothing much will appear to change I wouldn't think.

For devs, learning curve and switch your brain a few degrees one way or the other. That's where things are really going to change/are changing. Convergence, apparently, is where it's at.

---

### Post by craig10x on 2015-05-05
@BuckyBall: actually, i watched the video, and it is a little confusing the way Mark presented it...because i heard him say that you can download 2 kinds of snaps in your snappy (and have both as a matter of fact which you can switch in the command line) stable and developments snaps...If so, while it is true if you download only development snaps, you would essentially be on development as you guys who test have now...but if you only downloaded the stable snaps, that doesn't mean nothing much would change, because you would still get core changes, new apps, features, kernels, etc if you only downloaded the stable snaps, as they become stable, so that would still be a rolling model, it's just it would take  a bit longer to get the new stuff...but you would still get it AUTOMATICALLY and wouldn't be installing a new ubuntu every 6 months just to get them ;)

So, in essence, it sounds like what you would have is either: rolling stable or rolling development (or you could play with both if you like on the same install just by entering a terminal command to switch them)...
Stable snappy rolling would get updated like your android phone does, when the new item is READY, you get it automatically in your downloads...we don't have that now on the 6 month versions...It would still save the bother of having to upgrade every 6 months...You'd get everything development does, just not quite as soon...

---

### Post by Bucky Ball on 2015-05-05
> **craig10x said:**
> @BuckyBall: actually, i watched the video, and it is a little confusing the way Mark presented it...because i heard him say that you can download 2 kinds of snaps in your snappy (and have both as a matter of fact which you can switch in the command line) stable and developments snaps...If so, while it is true if you download only development snaps, you would essentially be on development as you guys who test have now...but if you only downloaded the stable snaps, that doesn't mean nothing much would change, because you would still get core changes, new apps, features, kernels, etc if you only downloaded the stable snaps, as they become stable, so that would still be a rolling model, it's just it would take  a bit longer to get the new stuff...but you would still get it AUTOMATICALLY and wouldn't be installing a new ubuntu every 6 months just to get them ;)

So, in essence, it sounds like what you would have is either: rolling stable or rolling development (or you could play with both if you like on the same install just by entering a terminal command to switch them)...
Stable snappy rolling would get updated like your android phone does, when the new item is READY, you get it automatically in your downloads...we don't have that now on the 6 month versions...It would still save the bother of having to upgrade every 6 months...You'd get everything development does, just not quite as soon...

That's it. Quite true. Good explanation. ;)

You can snap on what you like to what you like. Even different versions of the same program. For instance, a stable Libreoffice and a testing one. They're self-contained so you can have a stable and test the testing. Much easier for testing apps purposes than devoting an entire install or VM.

---

### Post by d-cosner on 2015-05-05
Is Snappy all that much different than Red Hat's idea of containers? It just kind of sounds like a way to expand on it.

From an announcement today for the new Red Hat test images.

> The new images for RHEL 6.7 Beta include a number of bug fixes and new  features, such as base images to facilitate moving services from  traditional environments into application containers.

---

### Post by d-cosner on 2015-05-05
Ubuntu Snappy as it is right now.

[https://www.youtube.com/watch?v=TiMsrbJoecE](https://www.youtube.com/watch?v=TiMsrbJoecE)

---

### Post by mc4man on 2015-05-08
I wouldn't be confusing snappy apps with applications commonly installed on Desktop installs now. They would seem, at least for reasonable future, to be apps like from an app store.  ( click, apple/windows/android stores, ect.

---

### Post by craig10x on 2015-05-08
Basically, based on the explanations i heard on Mark's and some of the developers videos, that there will be 2 branches of snappy personal....testing (which they also call the rolling release version) and stable...testing gets stuff first of course, and when it is deemed ready for stable it gets pushed to the stable version...So, stable actually fully rolls as well, just in a bit of a slower manner...but unlike now, you won't have to wait 6 months to get new features, new apps, new kernels, etc etc...as you do now...;)

Sounds good to me...i just hope they can have it ready for "prime time" by 16.04's release...

And the "testers" will appreciate that you can run both the testing snappy and stable versions on the same install and just switch from one to the other with a simple terminal command :)...
 
My own personal plan, is to continue upgrading into each new 6 month version of ubuntu until the ubuntu snappy personal stable version is ready for "prime time" use since i love the idea of having a rolling ubuntu and not have to re-install every 6 months to get the latest stuff and i would imagine that the 6 month version will get phased out at that point...replaced by new "up to date" iso images (for new installers) every 6 months, instead...

---

### Post by grahammechanical on 2015-05-08
If we see the Ubuntu phone update model as the intended update method for Ubuntu Snappy Personal Desktop then perhaps we should keep in mind that Ubuntu phone has different update channels. Snappy Desktop may follow the same pattern.

[https://developer.ubuntu.com/en/start/ubuntu-for-devices/image-channels/](https://developer.ubuntu.com/en/start/ubuntu-for-devices/image-channels/)

There is often a big difference between a vision and reality. Time will tell what is achievable. And muddle through is the usual method of progress.

Regards.

---

### Post by d-cosner on 2015-05-08
The whole Snappy idea is not as new and revolutionary as the news sites would like us to believe. Red Hat has been working on basically the same thing, it just is not as highly profiled by news sites.

[http://www.zdnet.com/article/red-hat-takes-a-stand-against-container-fragmentation-with-standards/](http://www.zdnet.com/article/red-hat-takes-a-stand-against-container-fragmentation-with-standards/)

---

### Post by grahammechanical on 2015-05-08
Snappy is not container technology. Containers for Canonical is LXC and LXD,

[https://help.ubuntu.com/lts/serverguide/lxc.html](https://help.ubuntu.com/lts/serverguide/lxc.html)

[http://www.ubuntu.com/cloud/tools/lxd](http://www.ubuntu.com/cloud/tools/lxd)

[https://linuxcontainers.org/](https://linuxcontainers.org/)

Snappy is a packaging format that is evolving out of the Click package format developed by Canonical for the Ubuntu phone. 

[https://developer.ubuntu.com/en/publish/packaging-click-apps/](https://developer.ubuntu.com/en/publish/packaging-click-apps/)

[https://developer.ubuntu.com/en/snappy/guides/packaging-format-apps/](https://developer.ubuntu.com/en/snappy/guides/packaging-format-apps/)

Ubuntu Snappy Core is Ubuntu Core with Snappy packaging as the default packaging method. What we are discussing here is the intention to produce a Ubuntu Desktop version using Snappy packaging. And in particular we are discussing the benefits of transactional updates to the kernel and OS with an offshoot discussion on the benefits of Snapp apps being updated by the developer without the need to wait until the next release of Ubuntu.

> We want our apps to be secure. To achieve this, all apps run under  confinement. When producing the apps, you get to decide which security  privileges your app needs. Please only pick security permissions your  app is actually going to use. networking is the only one the  Ubuntu SDK suggests by default. If you are unsure which security  privileges to choose, read our article about [Security policy for click packages]("https://developer.ubuntu.com/en/publish/security-policy-groups/").

There is a big difference between saying that "apps run under confinement" and saying that they are run in containers. The question as to whether FOSS development will benefit from one massive corporation gaining a monopolistic control over development is another discussion entirely. And not one I want to enter into.

Regards.

---

### Post by mikodo on 2015-05-08
> **craig10x said:**
> If so, while it is true if you download only development snaps, you would essentially be on development as you guys who test have now...but if you only downloaded the stable snaps, that doesn't mean nothing much would change, because you would still get core changes, new apps, features, kernels, etc if you only downloaded the stable snaps, as they become stable, so that would still be a rolling model, it's just it would take  a bit longer to get the new stuff...but you would still get it AUTOMATICALLY and wouldn't be installing a new ubuntu every 6 months just to get them  Would all the *buntu variants, easily transition to this too?  Well, I suppose all will. I shouldn't have said "easily", though. It's a growing/change process.

---

### Post by craig10x on 2015-05-08
Main edition ubuntu will definitely have it of course (w/unity) i think it will be up to the developers of the various community distributions (like xubuntu/lubuntu, etc) if they want to have it as well...based on what i have heard on the conference videos, it would work for them, just a matter of whether they desire to do it or not, i would imagine...

---

### Post by grahammechanical on 2015-05-08
There is more to a distro than OS packages. Some of the flavours do not have many developers. Here is an opportunity for volunteers to learn how to convert debian packaged apps to snapp apps. That will help lighten the load should the developers of the flavours feel that they should make the transition.

Regards.

---

