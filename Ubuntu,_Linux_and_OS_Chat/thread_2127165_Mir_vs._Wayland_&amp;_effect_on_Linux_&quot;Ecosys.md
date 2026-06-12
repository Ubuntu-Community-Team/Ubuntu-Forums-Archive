---
title: "Mir vs. Wayland &amp; effect on Linux &quot;Ecosystem&quot;?"
date: 2013-03-19
forum: Ubuntu, Linux and OS Chat
---

### Post by neu5eeCh on 2013-03-19
So, a question for those more knowledgeable. If Ubuntu develops MIR for its display server and the rest of the Linux ecosystem goes with Wayland (as apparently Mint, [KDE]("http://www.phoronix.com/scan.php?page=article&item=wayland_kde_2012&num=1") and [Gnome]("http://news.softpedia.com/news/GNOME-3-10-Might-Be-Ported-to-Wayland-337725.shtml") intend to do) isn't that a fairly serious split? Am I right in thinking that this could seriously marginalize every distribution that uses Wayland? -- or is the choice of display server fairly seamless (meaning, for instance, that game developers wouldn't have to develop two separate versions of a game). With this make twice as much work for developers considering Linux? -- or not?

---

### Post by mr john on 2013-03-19
Shouldn't make much difference if there is a compatibility layer. The developers who are going to have to do more work will probably be the Mir developers. I don't really take the opinions of Mint or Gnome seriously. It's been known for a quite some time that some people in those groups don't like Ubuntu. Gnome Shell sucks and it's highly likely that UI will drive them into obscurity over the next few years. Linux Mint just like to say things to try and show that they aren't Ubuntu. They have a bit of an identity issue.

---

### Post by grahammechanical on 2013-03-19
"Splits" as you call it are part of the genetic make up of Free and Open Source Software. Richard Stallman had a serious difference of opinion about how softeware should be developed and distributed and now we have FOSS. From the beginning there have been divisions. If someone does not like the way things are being done or they have a disagreement with another developer then they split and "fork the code" as the saying goes. Why is Wayland being developed when we have Xserver? Why is KDE being developed when we have Gnome? Why have Linux Mint (based upon Debian and Ubuntu) when we have Ubuntu?

Apparently, anybody can do what they like but let Ubuntu go a different way and it is cursed into the outer darkness. The only way to avoid this apparent "twice as much work" is for developers to be employed by one massive corporation. In FOSS developers are free to work on whatever projects that interest them. If this were not true then we would not have a Linux kernel not even a Gnu/Linux kernel. We would still be waiting for a GNU kernel.

This is life in the Free and Open Source ecosystem.

---

### Post by neu5eeCh on 2013-03-19
Thanks Grahammechenical, can't say as I disagree with anything you've written. My question was more practical than political. I'm wondering how, if at all, two different display servers will affect development. 

Ubuntu is the 800 pound gorilla. Take Steam for instance. Steam has already chosen sides. From what I can tell, they picked Ubuntu. Steam will now run on Fedora (and Arch I think), but it's not as if Steam devs developed Steam *for* Fedora. When Ubuntu switches to MIR, will this increasingly exacerbate the marginalization of non-Ubuntu distros (*there's Ubuntu and then there's the rest of them*)? Or is the difference between MIR and Wayland negligible?

---

### Post by 3rdalbum on 2013-03-19
The effect:

1. Wayland development will speed up to a furious pace to compete with Mir, which will benefit all distros that may ship Wayland in the future.

2. Mir has on-paper support from GPU makers such as AMD and Nvidia. Wayland has none. Wayland will become the geeky choice for the Ubuntu-haters, and Mir will become the choice for regular users who would prefer good 3D performance over "freedom".

3. You'll see other distros either adopt Mir as an option, or sink further into irrelevance. Either way, Mir will be THE display server for hip young Linux users :-)

*all this is assuming that Mir doesn't become abandonware, or that it doesn't end off being a total schmozzle.

---

### Post by montag dp on 2013-03-19
Lots of assumptions going on in this thread. No one really knows yet. Hopefully one will win out and become adopted by the whole community. I'm sick of this "us vs them" mentality that seems to be increasing lately (judging completely by forum posts).

---

### Post by lykwydchykyn on 2013-03-19
> **montag dp said:**
> Lots of assumptions going on in this thread. No one really knows yet. Hopefully one will win out and become adopted by the whole community. I'm sick of this "us vs them" mentality that seems to be increasing lately (judging completely by forum posts).

I agree; why is every project who supports wayland suddenly an "Ubuntu hater" motivated purely by anti-Canonical sentiment just because they don't drop 3+ years of development work the day Canonical announces a new display server that they've been developing in secret for six months?

.

---

### Post by llanitedave on 2013-03-19
> **3rdalbum said:**
> The effect:

1. Wayland development will speed up to a furious pace to compete with Mir, which will benefit all distros that may ship Wayland in the future.

2. Mir has on-paper support from GPU makers such as AMD and Nvidia. Wayland has none. Wayland will become the geeky choice for the Ubuntu-haters, and Mir will become the choice for regular users who would prefer good 3D performance over "freedom".

3. You'll see other distros either adopt Mir as an option, or sink further into irrelevance. Either way, Mir will be THE display server for hip young Linux users :-)

*all this is assuming that Mir doesn't become abandonware, or that it doesn't end off being a total schmozzle.

2.  If Mir is open source, wouldn't its supporting code for AMD and Nvidia be free for the Wayland developers to use or adapt?  Seems like there might be a door for compatibility between the two.

---

### Post by Gyokuro on 2013-03-19
Wayland/Weston is already a working system whereas MIR is far away from a working system. In my opinion some people have the impression that Canonical is leading the further development of Linux (in this case desktop) but it is not (it is louder as the rest) and if you compare the posted specification of MIR/UnityNext you will see it is somehow only a clone of Google's Chrome OS and much more developers are working for wayland and bring in support for wayland in various toolkits. If you can not attract developers outside of Ubuntu's universe how long can Canonical maintain all patches for various toolkits  outside of their upstream projects? Either you work with the community or against and fail.

---

### Post by neu5eeCh on 2013-03-19
> **lykwydchykyn said:**
> I agree; why is every project who supports wayland suddenly an "Ubuntu hater" motivated purely by anti-Canonical sentiment just because they don't drop 3+ years of development work the day Canonical announces a new display server that they've been developing in secret for six months? 

Okay, I honestly don't know what's motivating your comment or **montag dp's**. Just to be clear, I didn't say anything about "Ubuntu hating" or even suggest the same. If I'm being too sensitive (and you're not suggesting that I did) then we're all happy. ;)

Moving on...

I still don't get a sense for whether, practically speaking, MIR and Wayland will lead to two different development environments (which really *would* divide the Linux ecosystem *from a software developer's perspective*). If Ubuntu is the Llinux distro of choice, then am I mistaken in thinking that any future third party software makers (such as another Steam) would exclude other distros simply by virtue of being "coded for MIR"?

---

### Post by montag dp on 2013-03-19
> **VTPoet said:**
> Okay, I honestly don't know what's motivating your comment or **montag dp's**. Just to be clear, I didn't say anything about "Ubuntu hating" or even suggest the same. If I'm being too sensitive (and you're not suggesting that I did) then we're all happy. ;)
It wasn't your post, it was the one right above mine, plus similar sentiments that have been present in other threads lately.

---

### Post by neu5eeCh on 2013-03-19
> **Gyokuro said:**
> In my opinion some people have the impression that Canonical is leading the further development of Linux (in this case desktop) but it is not...

I'm not so sure. While Linux is in no way dependent on Canonical, Canonical's Ubuntu is unquestionably the distro (with the possible exception of Chrome OS) that has the best chance of becoming a competitor with Apple and MS. Ubuntu is the distro that is encouraging third party software developers to take the Linux platform seriously.

---

### Post by tartalo on 2013-03-19
The scenario you paint is certainly possible, but there are others.

Ubuntu is trying to become a viable alternative in the mobile market, but there are more contenders, besides the already existing and well established ones you have:

1) Tizen: backed by Samsung -the most important mobile manufacturer-, Intel -the most important CPU manufacturer- and the Linux Foundation itself. 
2) Firefox OS, Backed by Mozilla and an increasing number of phone carriers.
3) Plasma Active, backed by KDE and BasysKom, for now.

All these are going to enter the market this year, and Ubuntu is not there yet. Ubuntu has good plans but no palpable product, and Ubuntu's offer will need to be really really good to compensate the fact that they might enter a market when the contenders could have already taken positions, and the growth rate might have stabilized. (By the way Tizen and KDE bet for Wayland)

On the other hand, Ubuntu is already losing users in the PC market, and the most drastic changes are yet to come. It could be that Ubuntu's offer in two or three years is so attractive that the tendency gets reversed, why not. It's even possible that the PC as we know it disappears.

So, will Mir be so important in the whole picture as you paint it? It's early to say.

---

### Post by hainen on 2013-03-19
Or the wayland vs Mir fight result in every third part vendor write x11 apps instead as both wayland  and mir has x11  comparability with xwayland and xmir. ;)

---

### Post by neu5eeCh on 2013-03-19
> **tartalo said:**
> Ubuntu is already losing users in the PC market

I would have to question that assertion. If ubuntu is synonymous with Unity, then there [were some graphs]("http://nexus404.com/2011/11/25/ubuntu-linux-losing-popularity-among-users-ubuntu-losing-market-share-users-blame-new-unity-interface-for-decline/") that indicated as much. However, the vast majority of that market share seems to have been lost to other Ubuntu derivatives, such as Mint, Xubuntu, Kubuntu, etc... If Ubuntu switches to MIR, I would be surprised if the derivatives didn't follow sooner or later.


> **tartalo said:**
> All these are going to enter the market this year, and Ubuntu is not there yet.

All true. I guess I was limiting my speculation to desktop linux. Ubuntu's only competition, by what I can tell, would be Chrome OS. If Google decides to make Chrome OS a fully functional (as in **not** cloud dependent) OS, I think Ubuntu would quickly be relegated to *has been* or *also ran* status (and MIR *with *it). It's not that Chrome OS would be better (though that's possible) it's just that Google has huge, deep pockets.

---

### Post by lykwydchykyn on 2013-03-19
> **VTPoet said:**
> I would have to question that assertion. If ubuntu is synonymous with Unity, then there [were some graphs]("http://nexus404.com/2011/11/25/ubuntu-linux-losing-popularity-among-users-ubuntu-losing-market-share-users-blame-new-unity-interface-for-decline/") that indicated as much. However, the vast majority of that market share seems to have been lost to other Ubuntu derivatives, such as Mint, Xubuntu, Kubuntu, etc... If Ubuntu switches to MIR, I would be surprised if the derivatives didn't follow sooner or later.


Therein lies the problem, as I see it:

- KDE has no plans to support Mir.  
- GNOME neither
- Nor Enlightnment
- LXDE and XFCE are both still based on GTK2.  Don't know if a port to 3 is in the works, but last time I checked they were both sticking with 2.
- I sincerely doubt anyone is going to port GTK2 to a new display server.

The upshot is that the derivatives are either going to have to run in X11 or xmir; or else wayland will have to be brought to Ubuntu for these desktops.   If the marketshare is really all going to derivatives, then Mir on the desktop is going to be a lonely place.

---

### Post by neu5eeCh on 2013-03-20
So let me see if I understand this: Even if Ubuntu/Unity switches to MIR, the derivatives will still be able to offer an Ubuntu based system using Wayland or X11? Is it only Unity that relies on MIR? What is it that makes a derivative an "Ubuntu Derivative" if it's not, for example, using MIR?

---

### Post by lykwydchykyn on 2013-03-20
> **VTPoet said:**
> So let me see if I understand this: Even if Ubuntu/Unity switches to MIR, the derivatives will still be able to offer an Ubuntu based system using Wayland or X11? Is it only Unity that relies on MIR? What is it that makes a derivative an "Ubuntu Derivative" if it's not, for example, using MIR?

It's a derivative if it uses the same repositories; just like "Ubuntu server" is an ubuntu derivative but installs without X11.

It's no different than supporting a different desktop environment.  Kubuntu and Ubuntu use the same core OS, same repositories, are on the same release cycle, same build system, etc.  The difference is one installs KDE and the other Unity.  A wayland-based ubuntu derivative is just moving that difference one more layer down the stack.

---

### Post by graabein on 2013-03-20
I think it's a big split and I'm not too happy about it. Surely there's other places where effort is needed in Linux land. Canonical is a company though, yeay capitalism. I'd rather have them support Xfce or KDE.

I figure I'll try Ubuntu server install and add X and xmonad since I don't use Unity anyway. Finally dropped GNOME 3 also, phew. Or maybe try Debian, Arch, or something.

---

### Post by neu5eeCh on 2013-03-20
> **lykwydchykyn said:**
> It's a derivative if it uses the same repositories; just like "Ubuntu server" is an ubuntu derivative but installs without X11.

It's no different than supporting a different desktop environment.  Kubuntu and Ubuntu use the same core OS, same repositories, are on the same release cycle, same build system, etc.  The difference is one installs KDE and the other Unity.  A wayland-based ubuntu derivative is just moving that difference one more layer down the stack.

Cool. And then what's the difference between an official and unofficial derivative?

---

### Post by iamkuriouspurpleoranj on 2013-03-20
Linux is full of companies/capitalism:
- Novell(Attachmate, a company in which Microsoft has representation) : (indirectly)openSUSE
- Red Hat : RHEL/(indirectly)Fedora
- HP (as a partner of Debian)
- Opera/DuckDuckGo/Yahoo as sponsors of Mint
- Sun (historically)
- IBM

If you're using Google stuff (including Youtube) or Virtualbox/MySQL etc. (Oracle), that's all "capitalism". Personally I think Canonical are just the whipping boys of the moment. That's not to say I agree with everything it does - far from it. But stuff like RMS's call to bullying ("We need to teach Canonical a lesson") doesn't sit well with me. Also when people bandy about terms like "lock-in" and apply it to Canonical for situations that are nothing like true vendor lock-in, I smell a rat. Really if people don't want to use Ubuntu, there are plenty of other distributions. Say what you like and don't worry about what you don't like.

---

### Post by lykwydchykyn on 2013-03-20
> **VTPoet said:**
> Cool. And then what's the difference between an official and unofficial derivative?

AFAICT it has to do with official support from Canonical and the Ubuntu community. I don't have a bullet-point list of what it involves, there's probably something in a FAQ somewhere.

---

### Post by neu5eeCh on 2013-03-20
> **lykwydchykyn said:**
> AFAICT it has to do with official support from Canonical and the Ubuntu community. I don't have a bullet-point list of what it involves, there's probably something in a FAQ somewhere.

I tried to google the guidelines but couldn't find what I was looking for. It doesn't matter. I was just curious as to whether MIR would fall under the rubric of official or unofficial.

---

### Post by tartalo on 2013-03-20
One characteristic of Ubuntu derivatives is that they use only official Ubuntu repositories. Wayland and Xorg are already there and if Ubuntu continues being Debian based they will stay. So I don't foresee a problem in this sense.

But what really makes a derivative official is the blessing from Canonical, that comes when they consider that it contributes significantly to Ubuntu, whatever that means. Since this is quite subjective they could start forcing Mir, but they didn't do that with Ubuntu One or the Software Center, and these are revenue sources for Canonical, so why would they start now with Mir?

---

### Post by lykwydchykyn on 2013-03-20
> **VTPoet said:**
> I tried to google the guidelines but couldn't find what I was looking for. It doesn't matter. I was just curious as to whether MIR would fall under the rubric of official or unofficial.

I'm sure Mir will be officially supported software, since it's (a) developed by Canonical and (b) critical to the main product.

> 
Since this is quite subjective they could start forcing Mir, but they didn't do that with Ubuntu One or the Software Center, and these are revenue sources for Canonical, so why would they start now with Mir? 


I don't think they could ever *force* Mir (especially to the exclusion of X), since that would mean either dumping every other desktop environment, or coding support for Mir into all the other desktop environments.  But I don't think *Canonical* is going to be devoting resources to packaging Wayland in Ubuntu, it's going to be up to the wider community.  I could be wrong, it probably depends on how important Wayland becomes in the big picture.

---

### Post by koenn on 2013-03-20
> **lykwydchykyn said:**
>  I don't think they could ever *force* Mir (especially to the exclusion of X), since that would mean either dumping every other desktop environment, or coding support for Mir into all the other desktop environments.  .
Mir is a replacement for X, and Canonical is apparently planning to patch the most used widget toolkits so DE *can* work with Mir. Their roadmap also includes an X emulation/compatibility layer for "legacy" apps.

This goes quite deep, and apparently Canonical is betting on betting on Ubuntu getting enough desktop, tablet and phone market share to make Mir the new defacto standard. 
Not that this is necessarily bad. There's quite some agreement that X is getting old, so looking for innovation is a good idea. Remains to be seen what will be come the "next X". 

(there's a roadmap/spec for Mir at [https://wiki.ubuntu.com/Mir/Spec?action=show&redirect=MirSpec](https://wiki.ubuntu.com/Mir/Spec?action=show&redirect=MirSpec) )

---

### Post by JDShu on 2013-03-20
> **VTPoet said:**
> So, a question for those more knowledgeable. If Ubuntu develops MIR for its display server and the rest of the Linux ecosystem goes with Wayland (as apparently Mint, [KDE]("http://www.phoronix.com/scan.php?page=article&item=wayland_kde_2012&num=1") and [Gnome]("http://news.softpedia.com/news/GNOME-3-10-Might-Be-Ported-to-Wayland-337725.shtml") intend to do) isn't that a fairly serious split? Am I right in thinking that this could seriously marginalize every distribution that uses Wayland? -- or is the choice of display server fairly seamless (meaning, for instance, that game developers wouldn't have to develop two separate versions of a game). With this make twice as much work for developers considering Linux? -- or not?

In your example, it would marginalize Ubuntu, not Wayland. The result would be Ubuntu being used with X and other distributions using Wayland competing for mindshare. After all, what would be the point of Mir, if you couldn't use any applications with it?

Game developers tend to develop using various toolkits and libraries, so it would depend on whether those get ported to Wayland, Mir, or stick with X. On the other hand, applications that don't use any toolkits do exist - Blender comes to mind - and these would need to choose to support Wayland or Mir if X actually gets phased out.

That said, X will be around for a very long time.

---

### Post by lykwydchykyn on 2013-03-20
> **koenn said:**
> Mir is a replacement for X, and Canonical is apparently planning to patch the most used widget toolkits so DE *can* work with Mir. )
You have to patch more than toolkits for a whole DE to work; there's also the window manager, display manager, configuration tools for the monitor & graphics hardware, etc.  

If they're patching toolkits, it's so that applications can work on Mir; I don't see them doing the work to bring Gnome or KDE to Mir, especially since the whole point is to have Unity running across all devices.

---

### Post by solarghost on 2013-03-21
I think the effect on the "Ecosystem" will be positive.

Canonical have decided that X does not meet it's future needs/requirements, they probably had a look at Wayland and decided the same thing, in the end they decided to build their own tool. Now they are getting attacked for building an Open Source tool? They are giving Open Source developers a new tool to work with, I don't understand the hate.

I give a slight chuckle when I hear the argument that they are fragmenting the Open Source community. They are doing what all Open Source developers should be doing, building tools that they want to use because the current tools are not good enough.

Mir being a huge success will have only good consequences for the Wayland team, they will be able to look at what Canonical have done and take out the good and emulate it. If Mir is a big failure the Wayland team can instead see where the pitfalls are and try their best to avoid them.

---

### Post by JDShu on 2013-03-21
> **solarghost said:**
> 

Canonical have decided that X does not meet it's future needs/requirements, they probably had a look at Wayland and decided the same thing, in the end they decided to build their own tool. Now they are getting attacked for building an Open Source tool? They are giving Open Source developers a new tool to work with, I don't understand the hate.


No, they didn't have an honest look at Wayland, but that has been discussed in other threads on this forum.

> 
I give a slight chuckle when I hear the argument that they are fragmenting the Open Source community. They are doing what all Open Source developers should be doing, building tools that they want to use because the current tools are not good enough.

Mir being a huge success will have only good consequences for the Wayland team, they will be able to look at what Canonical have done and take out the good and emulate it. If Mir is a big failure the Wayland team can instead see where the pitfalls are and try their best to avoid them.

I don't think you understand what people mean by fragmentation being a problem. This isn't about Linux users wanting a One True Way. This is about toolkit developers needing to bear the burden of an additional display server. It's also about driver developers needing to support another display server. Developers who are already stretched too thin.

---

### Post by Primefalcon on 2013-03-21
personally I have hope for this project, we'll see what happens though, canonical does however have the resources to do this...as they proved with Unity

---

### Post by neu5eeCh on 2013-03-21
> **JDShu said:**
> I don't think you understand what people mean by fragmentation being a problem. This isn't about Linux users wanting a One True Way. This is about toolkit developers needing to bear the burden of an additional display server. It's also about driver developers needing to support another display server. Developers who are already stretched too thin.

This was my own concern, more or less; though I don't know to what degree a differing display server affects programming. If Ubuntu is the Linux distro of choice for third party software developers, and if their software is developed specifically for MIR, then this would seem to complicate matters for other distros still using X or using Wayland. I could be wrong though, which is why I'm asking the question.

---

### Post by Dry Lips on 2013-03-21
> **Primefalcon said:**
> personally I have hope for this project, we'll see what happens though, canonical does however have the resources to do this...as they proved with Unity

I freely admit that I'm no expert on these things, but can Unity (at the moment a layer built upon Compiz/Gnome 3) be compared to building a display server from scratch? I'd think building a display server is vastly more complicated than making a DE. 

Correct me if I'm wrong...

---

### Post by mikodo on 2013-03-21
> **Dry Lips said:**
> I freely admit that I'm no expert on these things, but can Unity (at the moment a layer built upon Compiz/Gnome 3) be compared to building a display server from scratch? I'd think building a display server is vastly more complicated than making a DE. 

Correct me if I'm wrong...

The [Roadmap]("https://wiki.ubuntu.com/Mir/Spec?action=show&redirect=MirSpec#April_2014") they have is for it to be functional for 14.04.

;p

---

### Post by BigSilly on 2013-03-21
> **VTPoet said:**
> Take Steam for instance. **Steam has already chosen sides. From what I can tell, they picked Ubuntu**. Steam will now run on Fedora (and Arch I think), but it's not as if Steam devs developed Steam *for* Fedora. When Ubuntu switches to MIR, will this increasingly exacerbate the marginalization of non-Ubuntu distros (*there's Ubuntu and then there's the rest of them*)? Or is the difference between MIR and Wayland negligible?

Unless I'm much mistaken, this isn't the case. Steam hasn't chosen Ubuntu. It's chosen Linux. It chose Ubuntu as its first approach to Linux, as the perception is it's the most popular Linux distro, but what Ubuntu does next will have zero effect on Steam I imagine. The Steam box isn't going to be Ubuntu-based (I don't know where this idea comes from, so please enlighten me if there's solid info I missed), but Linux based, and the client is Linux based. Of course what comes after X will affect how distros work with the Steam client on the desktop, but Steam in and of itself is not solely intended for Ubuntu.

My personal take is Ubuntu and Mir will pull further away from Linux as we know it. Whether this will result in the success they want is debatable. I suspect Wayland will be what the Linux eco-system uses, and Mir will be what Ubuntu uses, much like how things are right now with Unity. I don't think this will affect drivers from Nvidia etc, as you'll see the same driver across both approaches. From what I gather, it's not like how X was and shouldn't cause a divide from a driver point of view.

---

### Post by JDShu on 2013-03-21
> **VTPoet said:**
> This was my own concern, more or less; though I don't know to what degree a differing display server affects programming. If Ubuntu is the Linux distro of choice for third party software developers, and if their software is developed specifically for MIR, then this would seem to complicate matters for other distros still using X or using Wayland. I could be wrong though, which is why I'm asking the question.

As I said in an earlier post, third party software developers are likely to use gtk, Qt or some other toolkit library which would have X/Wayland/MIR support. True, there are certain applications that do in fact draw directly to the display server such as Blender, and these applications will have to deal with the complications - but in most cases I don't think it would affect application developers directly.

The main issue is that the fragmentation is likely to result in us taking even longer to move away from X11 because the toolkit developers need to put in work to support multiple display servers. The one thing that might make everything work out is if Canonical pulls out amazing engineering chops and their Qt/Gtk/whatevertoolkit downstream patches work flawlessly.

---

### Post by JDShu on 2013-03-21
> **BigSilly said:**
> 
My personal take is Ubuntu and Mir will pull further away from Linux as we know it. Whether this will result in the success they want is debatable. I suspect Wayland will be what the Linux eco-system uses, and Mir will be what Ubuntu uses, much like how things are right now with Unity. I don't think this will affect drivers from Nvidia etc, as you'll see the same driver across both approaches. From what I gather, it's not like how X was and shouldn't cause a divide from a driver point of view.

Drivers do in fact need an interface to X. In mesa, that's the DDX. (check out: [http://yangman.ca/blog/2009/10/linux-graphics-driver-stack-explained/](http://yangman.ca/blog/2009/10/linux-graphics-driver-stack-explained/)) The NVidia driver and AMD's Catalyst also install their own X drivers ([http://wiki.debian.org/NvidiaGraphicsDrivers#Installation-1](http://wiki.debian.org/NvidiaGraphicsDrivers#Installation-1)). While I'm not intimately familiar with Wayland/Mir architecture, it is likely that these drivers would need something written to interface with Wayland/Mir.

---

### Post by neu5eeCh on 2013-03-21
> **BigSilly said:**
> Unless I'm much mistaken, this isn't the case. Steam hasn't chosen Ubuntu. It's chosen Linux. It chose Ubuntu as its first approach to Linux, as the perception is it's the most popular Linux distro...

But isn't that, in effect, "choosing" Ubuntu? Ubuntu users could quickly download Stream via the download manager. For a short time the first official release of Steam "on Linux" wasn't initially available to other distros unless you were knowledgeable enough to manually install it. If what JDShu writes is correct, then even with MIR it will be business as usual.

---

### Post by neu5eeCh on 2013-03-21
> **JDShu said:**
> Drivers do in fact need an interface to X. In mesa, that's the DDX. (check out: [http://yangman.ca/blog/2009/10/linux-graphics-driver-stack-explained/](http://yangman.ca/blog/2009/10/linux-graphics-driver-stack-explained/)) The NVidia driver and AMD's Catalyst also install their own X drivers ([http://wiki.debian.org/NvidiaGraphicsDrivers#Installation-1](http://wiki.debian.org/NvidiaGraphicsDrivers#Installation-1)). While I'm not intimately familiar with Wayland/Mir architecture, it is likely that these drivers would need something written to interface with Wayland/Mir.

Interesting. So, the question becomes: Are these companies going to write drivers for X, Wayland and MIR (if a choice has to be made). They only just barely cobble together Linux drivers. Am I wrong in thinking this could turn into a Blu-ray versus HD DVD style "battle"? If so, I would expect Canonical's MIR to become the defacto standard. The other distros, even if they were to all go with Wayland, are utterly irrelevant outside the Linux-verse -- including RedHat.

---

### Post by JDShu on 2013-03-21
> **VTPoet said:**
> Interesting. So, the question becomes: Are these companies going to write drivers for X, Wayland and MIR (if a choice has to be made). They only just barely cobble together Linux drivers. Am I wrong in thinking this could turn into a Blu-ray versus HD DVD style "battle"? If so, I would expect Canonical's MIR to become the defacto standard. The other distros, even if they were to all go with Wayland, are utterly irrelevant outside the Linux-verse -- including RedHat.

Anything can happen, but prominent developers from within AMD and Red Hat claim that the majority of their customers that use Linux and propietary drivers are corporate workstations, implying that the desktop market - ie. us - are not targetted at all. This is the justification for keeping Catalyst around despite it being a buggy POS. The fact that it even works for us is basically luck. Ubuntu is only really a powerhouse on consumer desktop Linux, so if I was to bet money I would bet on whatever Red Hat and Novell (the main corporate Linux providers) choose.

Btw, I am unfamiliar with exactly how difficult a DDX or Wayland equivalent is to write. If it's not hard then maybe it doesn't matter on the driver side.

---

### Post by c2tarun on 2013-03-22
Hi friends, I read [this]("http://www.wired.com/wiredenterprise/2013/03/ubuntu-mir/") article and my feelings are the title of the thread. Please share what do you think about the article?

---

### Post by Elfy on 2013-03-22
merged thread

---

### Post by Nemesis2012 on 2013-03-22
Wayland is the new Xserver mir is a google based Unity Only Ubuntu Server so who knows whats going to be the new standard

---

### Post by Paqman on 2013-03-22
> **Gyokuro said:**
> if you compare the posted specification of MIR/UnityNext you will see it is somehow only a clone of Google's Chrome OS 

If that's true it's not that surprising, given that Canonical have said they've been providing Google with "engineering support" on a contractor basis. It's a bit vague what that support is, but it's not unreasonable that Google might have turned to the biggest desktop Linux distro when putting a bit of shine onto their own desktop Linux effort (especially since Chrome OS doesn't use X either).

---

### Post by hainen on 2013-03-22
> **Paqman said:**
> If that's true it's not that surprising, given that Canonical have said they've been providing Google with "engineering support" on a contractor basis. It's a bit vague what that support is, but it's not unreasonable that Google might have turned to the biggest desktop Linux distro when putting a bit of shine onto their own desktop Linux effort (especially since Chrome OS doesn't use X either).

In the future Google probably plan to use surfaceflinger but today I'm pretty sure google use X11 in chrome.

---

### Post by hainen on 2013-03-22
> **VTPoet said:**
> But isn't that, in effect, "choosing" Ubuntu? Ubuntu users could quickly download Stream via the download manager. For a short time the first official release of Steam "on Linux" wasn't initially available to other distros unless you were knowledgeable enough to manually install it. If what JDShu writes is correct, then even with MIR it will be business as usual.

They selected Ubuntu as their first supported linux platform. We really don't now what that mean in long term. Especially after they release their expected "steambox". Games don't need a advanced windows management. They are probably fine with Xorg in short and middle term. And if they switch display server they need to get the game developer on the train. If we wait maybe two years before the new display servers has stabilized, they has released their steam <whatever it is>, they has a bunch of game developer in steam. I suspect it can take time before they support either wayland or MIR.

---

### Post by Paqman on 2013-03-22
> **hainen said:**
> In the future Google probably plan to use surfaceflinger but today I'm pretty sure google use X11 in chrome.

I may well be mistaken then. I thought they'd rolled their own.

---

### Post by BrokenKingpin on 2013-03-22
I don't even see the point about arguing about this. To be honest, I don't see X11 being replaced by either in the near future anyways. Both Wayland and Mir are no where near prime time (especially Mir). Don't get me wrong, we do need a new display server, but we are years away from anything being ready. So lets revisit this conversation two years from now when they are both still probably will not be ready, where X11 will still be going along and still doing the job.

I also do not see what the big deal about Canonical wanting to create their on display server... if they want to create there own display server, let them. If it is better than what is out there people will use it, if not then they won't... simple.

---

### Post by Gyokuro on 2013-03-22
> **BrokenKingpin said:**
> I don't even see the point about arguing about this. To be honest, I don't see X11 being replaced by either in the near future anyways. Both Wayland and Mir are no where near prime time (especially Mir). Don't get me wrong, we do need a new display server, but we are years away from anything being ready. So lets revisit this conversation two years from now when they are both still probably will not be ready, where X11 will still be going along and still doing the job.

I also do not see what the big deal about Canonical wanting to create their on display server... if they want to create there own display server, let them. If it is better than what is out there people will use it, if not then they won't... simple.

+1 to your post which express in a very good way why at the moment there is no real need for a replacement in such a short time. The requirements for the mobile space is different and I think the driving forces are here Google with Android and Tizen (which will boom in Asia like crazy) and we should not forget there is also another force which do not jump at MIR/Wayland in the next time - commerical Unices (Solaris, AIX, HP-UX,..) the clocks there tick different. NVidia ported their drivers to Linux not for people who like to play games, they have done it as HPC people wanted to use the technology (CUDA) for their expensive hardware to run their various simulations with GPU support - that's were the money is - the coporations, governments and other big institutions and RedHat has a good reputation to deliver technology and have developers who are active in delivering software technolgies and supporting upstream projects with their various developers. That should not be an advertisement for RedHat but this company is doing for opensource and it's spirit much more as Canonical. MIR is only Canonicals requirement to bring on their idea to the mobile space.

---

### Post by lykwydchykyn on 2013-03-23
Wanted to post this link since it's a pretty good picture of where some of the other major communities out there stand with regard to Mir, and how it may affect other DE's and so forth:

[http://www.markshuttleworth.com/archives/1235#comment-400682](http://www.markshuttleworth.com/archives/1235#comment-400682)

That's a comment from Aaron Seigo (lead developer for KDE/plasma desktop) on one of Mark's blog posts about Canonical's new directions and how it affects the community.  Interesting reading, since this is a perspective from actual developers, not just users, journalist, or blogger cranks.

---

### Post by neu5eeCh on 2013-03-23
> **lykwydchykyn said:**
> Wanted to post this link since it's a pretty good picture of where some of the other major communities out there stand with regard to Mir, and how it may affect other DE's and so forth:

[http://www.markshuttleworth.com/archives/1235#comment-400682](http://www.markshuttleworth.com/archives/1235#comment-400682)

That's a comment from Aaron Seigo (lead developer for KDE/plasma desktop) on one of Mark's blog posts about Canonical's new directions and how it affects the community.  Interesting reading, since this is a perspective from actual developers, not just users, journalist, or blogger cranks.

Thanks for the link. That's fascinating stuff and goes some way toward answering my question. Especially this:

"So that means our software won’t run on Mir. Since our software is not shipped with Ubuntu anyways, that’s a non-issue." ~ Aaron Seigo

As I thought, there will be software that simply won't run on MIR (without some cost in time and effort). Will be interesting to see how this all sugars off. I'm not worried about it from a user's perspective. However, if I had to make a prediction, I expect that Ubuntu's move (if Ubuntu defaults to MIR) will marginalize the rest of the linux ecosystem (if the rest stubbornly refuse to follow suit). Then again, they're all largely irrelevant **anyway **(sorry Arch, Debian, Fedora, PCLOS, Redhat, etc...) Ubuntu is the only distro (and Canonical is the only company) that has a chance in the larger scheme of things. All the other distros just don't matter (and they're not in it for that reason anyway) so an extra layer of irrelevance shouldn't bother them (until and unless certain video drivers only work with certain display servers). That's when all the little wheels will start squeaking very loudly.

---

### Post by neu5eeCh on 2013-03-25
Jesse Smith nailed the issues I've been wondering about in the latest Distrowatch Weekly (500th issue). [He writes]("http://distrowatch.com/weekly.php?issue=20130325#feature"):

"...Wayland was receiving a lukewarm welcome from the community as a whole.

         At least it was until Canonical announced the launch of Mir, a potential competitor to Wayland. A week after the [announcement went public]("http://www.omgubuntu.co.uk/2013/03/canonical-announce-custom-display-server-mir-not-wayland-not-x"), [this post]("https://mail.gnome.org/archives/release-team/2013-March/msg00087.html") was made to the GNOME mailing list stating: "The  recent Mir announcement makes it a bit more urgent that we put our  weight behind Wayland and help it reach its full potential." The  post suggests GNOME should support Wayland before the end of 2013 and  it's probably not a coincidence this is the same time-line proposed by  Canonical for getting Unity working with Mir. I personally think it is  also interesting to note the proposed push to get GNOME working with  Wayland comes from Matthias Clasen, a Fedora contributor with an  @redhat.com [e-mail address]("https://fedoraproject.org/wiki/User:Mclasen").  I suspect in the final quarter of 2013 we will see an interesting and  problematic fork in the road where GNOME runs on top of Wayland on  Fedora, Unity runs on top of Mir on Ubuntu and other distributions not  based on either of these projects will be running their desktop  environments on top of standard X.

         Why might this be problematic? Well, aside from the likelihood  of new bugs being introduced with the arrival of fresh software there is  also the question of video drivers. Linux distributions already suffer  from poor video driver support and dividing that limited support three  ways isn't going to help. While it should be relatively easy to make  existing open source drivers work across X, Wayland and Mir, closed  source drivers (those needed for 3-D support and gaming) do not yet work  with Wayland or Mir. It's already hard enough to get companies like AMD  and NVIDIA to support Linux when they are asked to support the X  graphic stack, are these companies going to volunteer to support three  different display systems in the small desktop Linux market? Might they  only support one or two of the display options and, if so, which ones?

         Increasingly we are seeing the Linux community divided into  camps, not just the classic RPM vs DEB and GNOME vs KDE camps of the  past. The chasms are growing wider, dividing the community into separate  groups using different init processes, display systems and access  controls. It is my concern as both a developer and a user that we are  seeing a division of the Linux community into multiple separate  communities. We appear to have the Fedora/Red Hat camp on one side, the  Ubuntu/Canonical camp on the other and we have many other distributions  stuck in the middle..."

---

### Post by tartalo on 2013-03-25
> **VTPoet said:**
> The  post suggests GNOME should support Wayland before the end of 2013 and  it's probably not a coincidence this is the same time-line proposed by  Canonical for getting Unity working with Mir.

Perhaps not, but it's not like the effort around Wayland started the day after Mir was announced, it's been a years long way, and a quite transparent one.

> I suspect in the final quarter of 2013 we will see an interesting and  problematic fork in the road where GNOME runs on top of Wayland on  Fedora, Unity runs on top of Mir on Ubuntu and other distributions not  based on either of these projects will be running their desktop  environments on top of standard X.

Most probably everyone will still be using X, with Ubuntu making a slow transition to Mir and everyone else to Wayland. By the way, my impression is that KDE will be ready for Wayland before Gnome.

> are these companies going to volunteer to support three  different display systems in the small desktop Linux market? Might they  only support one or two of the display options and, if so, which ones?

And that's why everyone is unhappy with Canonical announcing first that Ubuntu would be an early supporter of Wayland, then not contributing to it, and then developing in secret an alternative. It hasn't helped either the lot of questionable things that Canonical employees have said about Wayland, KDE, Red Hat, Intel... or almost anyone that has actually contributed with code.

> We appear to have the Fedora/Red Hat camp on one side, the  Ubuntu/Canonical camp on the other and we have many other distributions  stuck in the middle..."

I don't see anyone stuck in the middle. Only Ubuntu has announced plans to use Mir.

---

### Post by Nemesis2012 on 2013-03-25
> **tartalo said:**
> Perhaps not, but it's not like the effort around Wayland started the day after Mir was announced, it's been a years long way, and a quite transparent one.



Most probably everyone will still be using X, with Ubuntu making a slow transition to Mir and everyone else to Wayland. By the way, my impression is that KDE will be ready for Wayland before Gnome.



And that's why everyone is unhappy with Canonical announcing first that Ubuntu would be an early supporter of Wayland, then not contributing to it, and then developing in secret an alternative. It hasn't helped either the lot of questionable things that Canonical employees have said about Wayland, KDE, Red Hat, Intel... or almost anyone that has actually contributed with code.



I don't see anyone stuck in the middle. Only Ubuntu has announced plans to use Mir.

you do have some really good points MIR is going to be Ubuntu only Wayland is going to be the New Xserver so now getting AAA Developers to develop for Linux is going to be five times harder Canonical Sunk the Ship before it sailed for a lot of Linux Users gamers etc [IMG]http://ubuntuforums.org/images/icons/icon9.png[/IMG]
and how many tool kits are we going to have how many bugs will Mir and Wayland have will we have Nvidia and AMD Drivers for Mir and Wayland
whos going to Develop the OpenSource Drivers For Mir? we have OpenSource Drivers for Wayland
most Developers are working on Wayland so if Mir is not going to use Wayland Code tool kits etc
is the little team of developers at Canonical going to write all code a huge team of developers been working on for 2+ years? or is Canonical going to hire more developers to keep? only time will tell

---

### Post by neu5eeCh on 2013-03-25
I found the following curious:

"The recent Mir announcement makes it a bit more  urgent that we put our weight behind Wayland and help it reach its full  potential."

What does he mean by this? Why is it more urgent for Gnome to get behind Wayland? Tell me I'm wrong but I read (between the lines) something like spite, resentment and contrarianism? What difference does it make to Gnome's schedule that Ubuntu uses MIR? The way I read between the lines is as follows: Gnome now feels that they are in direct competition with Canonical. They want to be the  defacto Linux desktop (and probably blame Unity for their current problems). The [writer of the post]("https://mail.gnome.org/archives/release-team/2013-March/msg00087.html") probably thinks that if Gnome can establish Wayland before Canonical establishes MIR, then third party video driver support (for example) will flock to Wayland rather than MIR. Gnome's boat will be lifted, Canonical's will sink.

For those who think competition in the Linux ecosystem is a good thing, I think we've got it -- a major competitive split between two big names. My feeling though is that Canonical will win. They've got the money and they're already years ahead of Gnome when it comes to expanding beyond the desktop. If Canonical says, once and for all, that it's going with MIR, and if Ubuntu is where the eyes are, Red Hat and Gnome can either cling to an irrelevant Wayland or swallow their pride. That's kinda' the way I read the tea leaves.

---

### Post by zer010 on 2013-03-25
Absolutely agree with BrokenKingpin.  Build it, if it's good, they will come.  X has been around and been voted for replacement a while now.  So far, I'm still a happy *nix user.

---

### Post by neu5eeCh on 2013-03-25
> **zer010 said:**
>  So far, I'm still a happy *nix user.

Me too. : ) I'm thinking this can only be good from *our *perspective. Still, it will be interesting to see how it all sugars off.

---

### Post by montag dp on 2013-03-25
> **VTPoet said:**
> I found the following curious:

"The recent Mir announcement makes it a bit more  urgent that we put our weight behind Wayland and help it reach its full  potential."

What does he mean by this? Why is it more urgent for Gnome to get behind Wayland? Tell me I'm wrong but I read (between the lines) something like spite, resentment and contrarianism? What difference does it make to Gnome's schedule that Ubuntu uses MIR? The way I read between the lines is as follows: Gnome now feels that they are in direct competition with Canonical. They want to be the  defacto Linux desktop (and probably blame Unity for their current problems). The [writer of the post]("https://mail.gnome.org/archives/release-team/2013-March/msg00087.html") probably thinks that if Gnome can establish Wayland before Canonical establishes MIR, then third party video driver support (for example) will flock to Wayland rather than MIR. Gnome's boat will be lifted, Canonical's will sink.

That might be so, but I can't say I fault the Gnome developers for feeling that after after what Canonical just pulled on everybody.

---

### Post by lykwydchykyn on 2013-03-26
> **VTPoet said:**
> 
What does he mean by this? Why is it more urgent for Gnome to get behind Wayland? Tell me I'm wrong but I read (between the lines) something like spite, resentment and contrarianism? 

I think that's a very presumptive and negative way to interpret his statement.   Earlier he says:

> 
So far, we've silently assumed that Wayland is the future display
system on Linux, and that we will get to using it eventually.


In other words, it's more likely that (based on Canonical's announcement a few years back that they were getting behind Wayland) they just assumed the distros would make Wayland happen and they'd get around to supporting it when it was happening.  Now they realize it's not, and that Wayland is a community effort now.

I think you greatly underestimate RH and Suse if you think they are irrelevant compared to Canonical.  They've both been profitable companies for longer than Canonical has existed.

---

### Post by forrestcupp on 2013-03-26
I haven't read the entire thread, but if Ubuntu goes to Mir and Gnome goes to Wayland, what will happen if you want to install Gnome Shell in Ubuntu?

---

### Post by tartalo on 2013-03-26
> **forrestcupp said:**
> I haven't read the entire thread, but if Ubuntu goes to Mir and Gnome goes to Wayland, what will happen if you want to install Gnome Shell in Ubuntu?

If Ubuntu continues being Debian based all dependencies should be available, but at this point I don't know if that can be taken for granted.

---

### Post by neu5eeCh on 2013-03-26
> **lykwydchykyn said:**
> I think you greatly underestimate RH and Suse if you think they are irrelevant compared to Canonical.  They've both been profitable companies for longer than Canonical has existed.

I don't think I do. They have zero presence in the larger general market. They are irrelevant. Sorry.

---

### Post by lykwydchykyn on 2013-03-26
> **VTPoet said:**
> I don't think I do. They have zero presence in the larger general market. They are irrelevant. Sorry.

No need to apologize; I'm not offended, I just think you're wrong :D.

---

### Post by llanitedave on 2013-03-26
> **VTPoet said:**
> I found the following curious:

"The recent Mir announcement makes it a bit more  urgent that we put our weight behind Wayland and help it reach its full  potential."

What does he mean by this? Why is it more urgent for Gnome to get behind Wayland? Tell me I'm wrong but I read (between the lines) something like spite, resentment and contrarianism? What difference does it make to Gnome's schedule that Ubuntu uses MIR? The way I read between the lines is as follows: Gnome now feels that they are in direct competition with Canonical. They want to be the  defacto Linux desktop (and probably blame Unity for their current problems). The [writer of the post]("https://mail.gnome.org/archives/release-team/2013-March/msg00087.html") probably thinks that if Gnome can establish Wayland before Canonical establishes MIR, then third party video driver support (for example) will flock to Wayland rather than MIR. Gnome's boat will be lifted, Canonical's will sink.

For those who think competition in the Linux ecosystem is a good thing, I think we've got it -- a major competitive split between two big names. My feeling though is that Canonical will win. They've got the money and they're already years ahead of Gnome when it comes to expanding beyond the desktop. If Canonical says, once and for all, that it's going with MIR, and if Ubuntu is where the eyes are, Red Hat and Gnome can either cling to an irrelevant Wayland or swallow their pride. That's kinda' the way I read the tea leaves.

I see it as a tacit admission that efforts on Wayland had been lagging, and they got caught with their pants down.  If this event re-energizes them, and suddenly we have two well-built alternatives to X, I think it will ultimately be good for everyone.

---

### Post by JDShu on 2013-03-26
> **forrestcupp said:**
> I haven't read the entire thread, but if Ubuntu goes to Mir and Gnome goes to Wayland, what will happen if you want to install Gnome Shell in Ubuntu?

The possibilities I can think of are:

- Canonical/Ubuntu has patches porting Shell to Mir, so you can just it.
- Just fall back to X
- Either Mir or Wayland is irrelevant so Shell will just work with Mir or Ubuntu will have Wayland.

---

### Post by mikodo on 2013-03-26
OK, well some things are going to be different in the immediate future. Like Mir by 14.04, possibly. With Gnome/RH fast tracking Wayland, maybe soon.

What ever happens, I am confident linux will prevail and will continue to improve. Too many people are involved in developing it, to let anything catastrophic happen that can't be sorted out. Generally options are a good thing. Sometimes competition too.

;p

---

### Post by coutts99 on 2013-03-27
> **lykwydchykyn said:**
> No need to apologize; I'm not offended, I just think you're wrong :D.

I agree with this bloke

---

### Post by Nemesis2012 on 2013-03-27
> **VTPoet said:**
> I don't think I do. They have zero presence in the larger general market. They are irrelevant. Sorry.

RedHat makes some of the most used Linux's around seeing how redhat had a Revenue of $1.13 billion 2012 vs canonica's Revenue around $30 million a year + RedHat is a major Developer of Linux Kernel Drivers Packages etc
Redhat Also Gives the most to Linux Community as well [http://community.redhat.com/](http://community.redhat.com/) if it was not for them Linux may have been a dead fish in the water a long time ago

---

### Post by tartalo on 2013-03-27
Red Hat might have done more for Ubuntu than Canonical themselves.

Canonical is nowhere to be seen in the Kernel development:
[http://go.linuxfoundation.org/who-writes-linux-2012](http://go.linuxfoundation.org/who-writes-linux-2012)

Canonical made a contribution to X.org/Wayland, and it was deemed newsworthy:
[http://www.phoronix.com/scan.php?page=news_item&px=MTEwNTc](http://www.phoronix.com/scan.php?page=news_item&px=MTEwNTc)

Canonical contributed very little to Gnome:
[http://www.neary-consulting.com/docs/GNOME_Census.pdf](http://www.neary-consulting.com/docs/GNOME_Census.pdf)

And these have been three key elements of Ubuntu always.

Now look at this: [http://community.redhat.com/contributions/](http://community.redhat.com/contributions/)

I think we should be thankful to Red Hat, Suse, etc for making Ubuntu great.

---

### Post by forrestcupp on 2013-03-27
> **tartalo said:**
> If Ubuntu continues being Debian based all dependencies should be available, but at this point I don't know if that can be taken for granted.

> **JDShu said:**
> The possibilities I can think of are:

- Canonical/Ubuntu has patches porting Shell to Mir, so you can just it.
- Just fall back to X
- Either Mir or Wayland is irrelevant so Shell will just work with Mir or Ubuntu will have Wayland.

Thanks, guys. I believe the dependencies for both will probably be satisfied in the repos. But I'm just wondering how it will work practically. Both Mir and Wayland are going to completely take the place of X, right? And right now, X is started *before* LightDM, GDM, KDM, or whatever, right? So if you install Ubuntu, it's going to start Mir before it loads up LightDM, where you choose your Desktop Environment. So then Mir is already started, and what happens if you choose Gnome Shell?

They're going to have to think these things through, or it's going to be a major mess. Having choices is only good when it's not detrimental to the overall experience.

---

### Post by Gyokuro on 2013-03-27
> **forrestcupp said:**
> Thanks, guys. I believe the dependencies for both will probably be satisfied in the repos. But I'm just wondering how it will work practically. Both Mir and Wayland are going to completely take the place of X, right? And right now, X is started *before* LightDM, GDM, KDM, or whatever, right? So if you install Ubuntu, it's going to start Mir before it loads up LightDM, where you choose your Desktop Environment. So then Mir is already started, and what happens if you choose Gnome Shell?

They're going to have to think these things through, or it's going to be a major mess. Having choices is only good when it's not detrimental to the overall experience.

They will replace X when they are ready and distributions use them not sooner - X will stay for a very long time and I will repeat what I have already wrote in the forums - MIR is only Canonicals requirment to bring on their vision of unity everywhere. Now to your question - yes in case of X11 but you forgot the kernel modules (nvidia, intel, amd driver). In case of MIR: you need XMIR do rune GNOME which is not there or Canonical have to send MIR patches to Gnome devs and they have to accept them - also not there and I think very unlikeley that this will happen in the next time as Gnome devs already have wayland patches in and the roadmap is public that they go the wayland road. Nothing secret here, nothing new and I'm not aware that somebody is working on a MIR/wayland backend server (checked the released MIR code) and Mir/Spec Wiki ([https://wiki.ubuntu.com/Mir/Spec?action=show&redirect=MirSpec](https://wiki.ubuntu.com/Mir/Spec?action=show&redirect=MirSpec)). In my opinion the rest of projects could work relaxed and make sane technical decisions and if MIR fails there are other routes to go and they are already available.

---

### Post by tartalo on 2013-03-27
I don't have a clue about how that could be done, but I love to speculate:

KDE is considering replacing the Display Manager, KDM probably won't make it in the transition to Wayland. The alternatives they are considering are LightDM and SDDM: [http://aseigo.blogspot.com.es/2013/03/logging-into-plasma-workspaces-2.html](http://aseigo.blogspot.com.es/2013/03/logging-into-plasma-workspaces-2.html)

LightDM is Canonical's work and it's integration with KDE was going quite well until the Mir announcement, this is what the KDE front-end maintainer said: [http://www.sharpley.org.uk/blog/lightdm-mir-wayland](http://www.sharpley.org.uk/blog/lightdm-mir-wayland) 

It's now clear that Canonical won't add Wayland support to LightDM themselves but, according to Aaron Seigo, LightDM developers are open for a collaboration, the reticence comes from some KDE developers and downstreams: the trust in Canonical has suffered, there are some license issues...

On the other hand, SDDM is written in QML and it's very promising but it needs a lot of work, so the decision is not easy. 

***If*** KDE decided to use LightDM and join efforts with Canonical, there might be a little hope for a sane solution for Wayland/Mir coexistence in the same installation. However this is only interesting for Ubuntu users that use Unity plus another DE, and this collective is probably not a priority for anyone involved in the decision.

---

### Post by JDShu on 2013-03-27
> **forrestcupp said:**
> Thanks, guys. I believe the dependencies for both will probably be satisfied in the repos. But I'm just wondering how it will work practically. Both Mir and Wayland are going to completely take the place of X, right? And right now, X is started *before* LightDM, GDM, KDM, or whatever, right? So if you install Ubuntu, it's going to start Mir before it loads up LightDM, where you choose your Desktop Environment. So then Mir is already started, and what happens if you choose Gnome Shell?

They're going to have to think these things through, or it's going to be a major mess. Having choices is only good when it's not detrimental to the overall experience.

Hats off to you for illustrating the problem so clearly, I was having trouble explaining that  "choice is not always better".

I think worst case scenario, you can run Shell in X mode, and then run that on XMir. Ridiculous, but it would work.

---

### Post by forrestcupp on 2013-03-27
> **tartalo said:**
> 
***If*** KDE decided to use LightDM and join efforts with Canonical, there might be a little hope for a sane solution for Wayland/Mir coexistence in the same installation. However this is only interesting for Ubuntu users that use Unity plus another DE, and this collective is probably not a priority for anyone involved in the decision.I'll bet there are a lot of people who install Ubuntu and then use a different DE. I know there are a lot of people who like to be able to choose from several different DEs, and Ubuntu is the obvious starting point. If it doesn't get worked out, then Ubuntu will no longer be the obvious starting point, and I think they'll suffer for it. But I'm sure it will be a while before they just switch over, and I'm sure they'll figure all of this out before making such a drastic move in a release.

In my opinion, going rogue with a replacement for X is about as ridiculous as switching to the HURD kernel.

> **JDShu said:**
> Hats off to you for illustrating the problem so clearly, I was having trouble explaining that  "choice is not always better".

I think worst case scenario, you can run Shell in X mode, and then run that on XMir. Ridiculous, but it would work.I just wonder about this because I'm currently using Gnome Shell, and for various reasons, I like installing it from Ubuntu rather than installing one of the vanilla Gnome variants. Hopefully if it ends up being your worst case scenario, they'll come up with a way to automate all of that so that the average user doesn't have to mess with that kind of headache.

---

### Post by lykwydchykyn on 2013-03-27
Of course it may be perfectly possible to run X, Wayland, and Mir simultaneously on the same box in different VT's.  I'm not saying it will be, but considering that most of the code involved hasn't even been written yet, who knows?

---

### Post by neu5eeCh on 2013-03-27
> **Nemesis2012 said:**
> RedHat makes some of the most used Linux's around seeing how redhat had a Revenue of $1.13 billion 2012 vs canonica's Revenue around $30 million a year + RedHat is a major Developer of Linux Kernel Drivers Packages etc
Redhat Also Gives the most to Linux Community as well [http://community.redhat.com/](http://community.redhat.com/) if it was not for them Linux may have been a dead fish in the water a long time ago

Ya'll confuse revenue with relevance. When anybody without tape on their glasses knows who RedHat is, when we see a Redhat or Suse Tablet or smart phone, then I might start thinking you're even remotely correct. 

They're just not relevant to anyone outside of the Linuxverse. Steam didn't didn't come to "linux" because they were all het up about Redhat's popularity on the desktop. And SUSE who? They almost went down the drain not too long ago. 

When Ubuntu says they're going with MIR, folks sit up and take notice. If Redhat decided they were going to use [insert acronym], so what? What's important here is where third party software developers (whose revenue is based on the eyes of the general public) see a return on investment. They couldn't give a rat's butt about Suse or Redhat.

---

### Post by kaldor on 2013-03-27
> **VTPoet said:**
> Ya'll confuse revenue with relevance. When anybody without tape on their glasses knows who RedHat is, when we see a Redhat or Suse Tablet or smart phone, then I might start thinking you're even remotely correct. 

They're just not relevant to anyone outside of the Linuxverse. Steam didn't didn't come to "linux" because they were all het up about Redhat's popularity on the desktop. And SUSE who? They almost went down the drain not too long ago. 

When Ubuntu says they're going with MIR, folks sit up and take notice. If Redhat decided they were going to use [insert acronym], so what? What's important here is where third party software developers (whose revenue is based on the eyes of the general public) see a return on investment. They couldn't give a rat's butt about Suse or Redhat.

Because obviously the desktop is the only relevant platform.

---

### Post by cariboo on 2013-03-27
RedHat and Canonical have different target audiences, RedHat is the Linux desktop in enterprise, and as we all know most enterprise want a locked down desktop, hence the direction that Gnome, backed by Redhat is going. Canonical wants to have Ubuntu on every desktop, as well as on as many other devices as possible

---

### Post by montag dp on 2013-03-27
> **cariboo907 said:**
> RedHat and Canonical have different target audiences, RedHat is the Linux desktop in enterprise, and as we all know most enterprise want a locked down desktop, hence the direction that Gnome, backed by Redhat is going. Canonical wants to have Ubuntu on every desktop, as well as on as many other devices as possibleHence the increasingly locked-down nature of Unity, err, wait...

---

### Post by neu5eeCh on 2013-03-28
> **kaldor said:**
> Because obviously the desktop is the only relevant platform.

Right. You're making my point.

> **cariboo907 said:**
> RedHat and Canonical have different target  audiences, RedHat is the Linux desktop in enterprise, and as we all know  most enterprise want a locked down desktop, hence the direction that  Gnome, backed by Redhat is going. Canonical wants to have Ubuntu on  every desktop, as well as on as many other devices as possible

Exactly. And that's the reason companies like Suse and RedHat are irrelevant when it comes to anything like wider adoption. If Ubuntu's MIR is successful, then that's what 3rd party software developers, interested in the broader market, are going to develop for.

---

### Post by lykwydchykyn on 2013-03-28
> **VTPoet said:**
> Ya'll confuse revenue with relevance. When anybody without tape on their glasses knows who RedHat is, when we see a Redhat or Suse Tablet or smart phone, then I might start thinking you're even remotely correct. 


'cause relevance makes the world go 'round.  And pays developers to work on stuff (like display servers).  Or that could be revenue, not sure since I'm confused. ;)

More to the point:  it doesn't matter at all how many users a distro has when it comes to developing software.  What matters is how well it inspires the developer community to follow its lead, and how much money it has to hire developers when they don't.  From what I read, Canonical is doing a poor job of the former, and they're on at best equal footing with Suse and RedHat when it comes to the latter.  This isn't a clincher that "Mir will fail", but your remark that the rest of the Linux universe is "irrelevant" is a little short-sighted.

---

### Post by Gyokuro on 2013-03-28
> **lykwydchykyn said:**
> 'cause relevance makes the world go 'round.  And pays developers to work on stuff (like display servers).  Or that could be revenue, not sure since I'm confused. ;)

More to the point:  it doesn't matter at all how many users a distro has when it comes to developing software.  What matters is how well it inspires the developer community to follow its lead, and how much money it has to hire developers when they don't.  From what I read, Canonical is doing a poor job of the former, and they're on at best equal footing with Suse and RedHat when it comes to the latter.  This isn't a clincher that "Mir will fail", but your remark that the rest of the Linux universe is "irrelevant" is a little short-sighted.

+1 to your post - I have already wrote that you have to attract the developers and they have to trust you in your decisision making. That trust is something which Canonical to not have at the moment and you earn this over years and if you look at their past decisions which way application developers should go (quickly,...) and now QML/QT someone could get the impression that this is not professional at all and that they do not work together only take parts, polish the surface and write what great they have achieved - for me thats only a lot of marketing talk. And to write that RH/SuSE is irrelevant shows me that some users only care for their Ubuntu universe. However if you work with and for big companies you will see that they are using mainly RH/SuSE/Debian due to various certifications and the same for developers (CentOS in case you want to test stuff but do not need  a certified distribution for testing or development work ) and they are very active in major upstream projects (kernel, compiler, window system and toolkits,..). That should not mean that I think it is a bad company (it's a young and maybe have to learn)  but they should really work more with upstream, work on a better comunication and should be active also in key parts of the community and not only polish the surface.

---

### Post by tartalo on 2013-03-28
The funny thing is that when Ubuntu was concentrated in polishing and Marketing they did a fantastic job, who can deny that? If you wanted to hand a Linux CD to friend who knew nothing about Linux, there was nothing better than Ubuntu, it almost always worked and even the CD itself gave an excellent impression.

But the recent publicity stunts have left me a sweet-sour taste, first it was really exciting learning about the phone plan, but discovering that there wasn't almost anything palpable behind the videos was disappointing (CyannogenMod and placeholder images... really?), and then learning that the plan included departing from the Ubuntu I knew and liked and more importantly from the common effort around Linux was a really cold shower.

It can be argued that everyone asked Canonical to code more and they are finally doing it.

I hope than all this plan doesn't end in a complete failure, because Ubuntu has done a lot for Linux users in it's own way.

---

### Post by Gyokuro on 2013-03-28
> **tartalo said:**
> The funny thing is that when Ubuntu was concentrated in polishing and Marketing they did a fantastic job, who can deny that? If you wanted to hand a Linux CD to friend who knew nothing about Linux, there was nothing better than Ubuntu, it almost always worked and even the CD itself gave an excellent impression.

But the recent publicity stunts have left me a sweet-sour taste, first it was really exciting learning about the phone plan, but discovering that there wasn't almost anything palpable behind the videos was disappointing (CyannogenMod and placeholder images... really?), and then learning that the plan included departing from the Ubuntu I knew and liked and more importantly from the common effort around Linux was a really cold shower.

It can be argued that everyone asked Canonical to code more and they are finally doing it.

I hope than all this plan doesn't end in a complete failure, because Ubuntu has done a lot for Linux users in it's own way.

That's correct and nobody denies it but you have take care that people do not think over time you are only a marketing driven company after they realize that below the shown marketing stuff there is no real engineering (only taken parts from various upstream projects) but the other way round do not work too - engineers are not good at marketing their work and here I think have Canonical an advantage over the competitors which are at their engineering work superb but miss the flair to sell the product to the users. In the end we will only advance if we bring OSS in general to the minds of people instead to show a community which fight against each other. The key is transparent communication and keep down our egos together and work together otherwise we fail as community.

---

### Post by neu5eeCh on 2013-03-28
> **lykwydchykyn said:**
> More to the point:  it doesn't matter at all how many users a distro has when it comes to developing software.  What matters is how well it inspires the developer community to follow its lead...

Yes. And? How many third party developers do you see rushing to develop apps for Suse, or PCLos, or Fedora, or Slack, or Arch? I'm just not seeing any evidence to support your contention. Show me the evidence and that will convince me. How are Suse, Arch or RedHat relevant to a Steam (for example)?

---

### Post by montag dp on 2013-03-28
> **VTPoet said:**
> Yes. And? How many third party developers do you see rushing to develop apps for Suse, or PCLos, or Fedora, or Slack, or Arch? I'm just not seeing any evidence to support your contention. Show me the evidence and that will convince me. How are Suse, Arch or RedHat relevant to a Steam (for example)?What third-party developer is producing software specifically for Ubuntu?  Steam is producing software for Linux and happens to promote Ubuntu because it is considered to be the best/most popular distro for new Linux users.

---

### Post by mikodo on 2013-03-28
> **Gyokuro said:**
> That's correct and nobody denies it but you have take care that people do not think over time you are only a marketing driven company after they realize that below the shown marketing stuff there is no real engineering (only taken parts from various upstream projects) but the other way round do not work too - engineers are not good at marketing their work and here I think have Canonical an advantage over the competitors which are at their engineering work superb but miss the flair to sell the product to the users. In the end we will only advance if we bring OSS in general to the minds of people instead to show a community which fight against each other. The key is transparent communication and keep down our egos together and work together otherwise we fail as community.
Nice paragraph.

 Is this possible? An ideal possibly. "Keep down our egos together". Well we are fragmented, with fractured egos, it's the nature of the beast of OSS/FLOSS/FOSS/Linux/GnuLinux/this license/that license/these special interest groups/those special interest groups/. It is what makes "linux". It's what empoweres "linux". If our volunteer devs, testers, bug triagers all had to work on the same project goals and road maps, "linux" would fail as it is today. We all do this to be different for as many reasons as there are people using "linux",  for reasons not available in closed source propriety operating systems. Differsity is the nature and strength of our community.

Discussions like these are important for multiple levels of understanding. I am not dismissing it, but embrace the information the discussion brings.


The only thing constant about change is that it is constant. Should we fear this? Not if we expect that change is inevitable. Then it is rational and exiciting.

Where the heck is the spell-check?

;p

---

### Post by CarpKing on 2013-03-28
> **forrestcupp said:**
> In my opinion, going rogue with a replacement for X is about as ridiculous as switching to the HURD kernel.

It doesn't seem fair to compare a venerable, mature, nearly-functional project like HURD with an upstart like Mir :V.

---

### Post by neu5eeCh on 2013-03-29
> **montag dp said:**
> ...happens to promote Ubuntu because it is considered to be the best/most popular distro for new Linux users.

Bingo. :guitar:

And not just for new Linux users. Now what's going to happen if Ubuntu switches to MIR? That's the question I was initially asking.

---

### Post by montag dp on 2013-03-29
> **VTPoet said:**
> Bingo. :guitar:

And not just for new Linux users. Now what's going to happen if Ubuntu switches to MIR? That's the question I was initially asking.Ok, well that's not what you said.  You implied that Steam is producing apps specifically for Ubuntu, which is not the case.

As for your question, I think it illustrates why people are upset about what Canonical is doing.  They are introducing fragmentation at a very fundamental level, to the detriment of the community at large.  At the same time, if Ubuntu becomes the only distro to use Mir, which I think is likely if it ends up actually succeeding, I don't see third-party developers rushing to write software for it.  They wouldn't want their software tied to a single, fallible distribution.

---

### Post by thatguruguy on 2013-03-29
> **montag dp said:**
> Ok, well that's not what you said.  You implied that Steam is producing apps specifically for Ubuntu, which is not the case.

As for your question, I think it illustrates why people are upset about what Canonical is doing.  They are introducing fragmentation at a very fundamental level, to the detriment of the community at large.  At the same time, if Ubuntu becomes the only distro to use Mir, which I think is likely if it ends up actually succeeding, I don't see third-party developers rushing to write software for it.  They wouldn't want their software tied to a single, fallible distribution.

As a first guess, I'd think that most people who would want to write an app that works with both Ubuntu Touch and desktop Ubuntu would create it with Qt Creator, rather than directly writing a bunch of code that directly manipulates the display server, whether that would be X11, Wayland or Mir. Or they'd write it using some other IDE that deals with the display server-specific code for them.  But again, that's just a guess on my part.

---

### Post by montag dp on 2013-03-29
> **thatguruguy said:**
> As a first guess, I'd think that most people who would want to write an app that works with both Ubuntu Touch and desktop Ubuntu would create it with Qt Creator, rather than directly writing a bunch of code that directly manipulates the display server, whether that would be X11, Wayland or Mir. Or they'd write it using some other IDE that deals with the display server-specific code for them.  But again, that's just a guess on my part.That's probably true.  Hopefully most software will run on both display servers without issue, so developers can just develop for Linux without having to worry about it.  I'm not a developer so I don't know how realistic that is.  Seems like at the very least, Canonical would have to provide support for the major toolkits when writing Mir. (Or do the toolkits have to support the display server? Like I said, I'm not exactly sure how it works.)

---

### Post by thatguruguy on 2013-03-29
> **montag dp said:**
> That's probably true.  Hopefully most software will run on both display servers without issue, so developers can just develop for Linux without having to worry about it.  I'm not a developer so I don't know how realistic that is.  Seems like at the very least, Canonical would have to provide support for the major toolkits when writing Mir. (Or do the toolkits have to support the display server? Like I said, I'm not exactly sure how it works.)

One of the design goals for Mir (and this is also true for Wayland) is to ensure that legacy apps which rely on X11 still run. 

More importantly, I think your earlier statement that "I don't see third-party developers rushing to write software for it.   They wouldn't want their software tied to a single, fallible  distribution" is fundamentally flawed. Generally speaking, I'd think that if you wanted to reach the largest possible audience of desktop Linux users, you're going to write for the distribution that is used by the largest number of people.  Which right now is Ubuntu, by a significant margin (according to all sources that aren't Distrowatch).

---

### Post by montag dp on 2013-03-29
> **thatguruguy said:**
> One of the design goals for Mir (and this is also true for Wayland) is to ensure that legacy apps which rely on X11 still run. 

More importantly, I think your earlier statement that "I don't see third-party developers rushing to write software for it.   They wouldn't want their software tied to a single, fallible  distribution" is fundamentally flawed. Generally speaking, I'd think that if you wanted to reach the largest possible audience of desktop Linux users, you're going to write for the distribution that is used by the largest number of people.  Which right now is Ubuntu, by a significant margin (according to all sources that aren't Distrowatch).While that's true, I don't think that Ubuntu deviating significantly from the rest of the Linux world at a fundamental level really inspires confidence from a developer point of view, especially considering Canonical is a relatively small company without a huge force of programmers.  Linux distributions come and go, and Ubuntu is still fairly new in the grand scheme of things.

---

### Post by neu5eeCh on 2013-03-29
> **montag dp said:**
> Ok, well that's not what you said.  You implied that Steam is producing apps specifically for Ubuntu, which is not the case.


No, I never wrote that. I just looked through all my posts to confirm that. Maybe you were confusing me with BigSilly, who wrote: "[Steam] chose Ubuntu as its first approach to Linux, as the perception is it's the most popular Linux distro..." I agreed with that and added that this is, in effect, "choosing" Ubuntu.

> **montag dp said:**
> As for your question, I think it illustrates why people are upset about what Canonical is doing.  They are introducing fragmentation at a very fundamental level, to the detriment of the community at large.  At the same time, if Ubuntu becomes the only distro to use Mir, which I think is likely if it ends up actually succeeding, I don't see third-party developers rushing to write software for it.  They wouldn't want their software tied to a single, fallible distribution.

I disagree with this last part. If it weren't for Ubuntu, I doubt any signigicant third party developers would be tying their software to linux *at all *(let alone any distros). At the risk of offending, I *do* get the sense that some of you are suffering delusions of grandeur when it comes to desktop linux. If the broader market comes to the linux desktop, it's going to be on Ubuntu and the evidence already supports that. If Ubuntu switches to MIR, and if 3rd party software must rely on a specific display server, then Ubuntu will be favored. That's my prediction. We'll see if I'm right or wrong...

---

### Post by thatguruguy on 2013-03-29
> **montag dp said:**
> While that's true, I don't think that Ubuntu deviating significantly from the rest of the Linux world at a fundamental level really inspires confidence from a developer point of view, especially considering Canonical is a relatively small company without a huge force of programmers.  Linux distributions come and go, and Ubuntu is still fairly new in the grand scheme of things.

I guess it depends on whether you define what Canonical is doing is "deviating" or "leading".  For years, there hasn't been a significant increase in adoption of desktop Linux. Canonical in particular, and the Ubuntu community as a whole, id trying to change that. As I've argued before, following the way the rest of the Linux community has been heading for all these years hasn't worked; why should anyone expect that following "the rest of the Linux world" is the way to attain greater market penetration, if it hasn't worked yet?

For most 3d party developers, the display server doesn't really matter, because they don't interact directly with the display server. The display server does matter for developers working on lower-level stuff, like desktop environments (KDE, Gnome, etc.).  KDE developers have already stated they aren't ggoing to support Mir, because it is only going to be used by Ubuntu. Essentially, they'd rather support Wayland (which isn't being used by *anyone* right now) than support Mir, which at least *one* distro is going to use. I'm no mathematician, but my understanding is 1>0.

I'm not sure if it really matter that KDE devs won't support Mir, since the flagship Ubuntu product uses Unity as its DE. But the sour grapes that seems to be the go-to response of people to anything that Canonical does gets kinda old.

---

### Post by thatguruguy on 2013-03-29
Incidentally, I think the primary reason for Canonical stearing Ubuntu away from Wayland and towards Mir is a commercial one that will ultimately benefit users. NVIDIA has stated it won't support Wayland, because the Wayland devs insisted that NVIDIA must expose its codebase to ensure compliance with the Wayland server. Neither NVIDIA nor ATI wants to expose all of their driver code, because they don't want to give any commercial advantage to the other. Canonical has stated that they are working directly with NVIDIA and ATi on Mir, which I'm going to assume to be a true statement. In fact, I'm going to assume that Canonical has promised that they'll allow the development of proprietary drivers without any requirement that said code be open. That may be a loss to those who want all code to be open source, but it'll be a win for those companies and, ultimately, a win for users.

---

### Post by mikodo on 2013-03-30
> **thatguruguy said:**
> 
For most 3d party developers, the display server doesn't really matter, because they don't interact directly with the display server. The display server does matter for developers working on lower-level stuff, like desktop environments (KDE, Gnome, etc.).  KDE developers have already stated they aren't ggoing to support Mir, because it is only going to be used by Ubuntu. Essentially, they'd rather support Wayland (which isn't being used by *anyone* right now) than support Mir, which at least *one* distro is going to use. I'm no mathematician, but my understanding is 1>0.

I'm not sure if it really matter that KDE devs won't support Mir, since the flagship Ubuntu product uses Unity as its DE..
I concerned what this will mean for my beloved Xubuntu. I cut my linux teeth on Ubuntu. I want to be able to continue to enjoy all that Xubuntu has now.

If I have to, I'll go to another distro with Xfce with sadness, as I fear the experience may be diminished for me.

;p

---

### Post by tartalo on 2013-03-30
> **thatguruguy said:**
> KDE developers have already stated they aren't ggoing to support Mir, because it is only going to be used by Ubuntu. Essentially, they'd rather support Wayland (which isn't being used by *anyone* right now) than support Mir, which at least *one* distro is going to use. I'm no mathematician, but my understanding is 1>0.

KDE (and Gnome, and Enlightenment and and and) will continue with the years long work on Wayland, and won't change their plans unless they see Canonical deliver. Seems very reasonable to me.

Mir is being used in 0 distros now, I know at least 2 experimental distros that are using Wayland right now (Maui and Rebeca Black OS), if we are talking about the future, all the major distros, even Ubuntu, include Wayland in the repositories.

---

### Post by BigSilly on 2013-03-30
I think if Ubuntu delivers on Mir and its other plans, then no doubt nVidia and ATI etc will develop their drivers for the devices, just as they have for Android. I don't think however, that this will mean that suddenly they'll cease their output for Linux support though. As has been previously stated, Ubuntu is not Linux (and I agree with previous posters that it isn't bigger than Linux either), and this is becoming more and more apparent as they pull away. Nvidia did state they wouldn't support Wayland, but this was a long time ago now. I've no doubt that graphics drivers will still be created for whatever happens to Linux (ie. not Ubuntu) in the future. My honest feeling is that whatever Ubuntu gets up to, this isn't really going to have a massive impact on the rest of the Linux world insofar as driver support. As Clem from Linux Mint stated recently, [Mir is irrelevant]("http://www.muktware.com/5356/clement-lefebvre-mir-irrelevant-linux-mint"). In the future, there'll be Ubuntu, and Linux. This makes me sad ultimately, but it's what Mark wants.

---

### Post by iamkuriouspurpleoranj on 2013-03-30
Not sure how Linux Mint going its own way in a way that only benefits the Mint project and not the "upstream distribution" (Ubuntu) is ethically/morally different to Canonical developing its own display server. All this will work itself out in the end, anyway. Either AMD will support both or one of the two. If it's the latter, the others will come into line (Wayland or Mir). But reduplication of effort? That's just a Linux/FOSS thing. Ubuntu did not start that. Everything is a fork of something else.

Clement Lefèbvre's answer was characteristically measured. As far as he's concerned, Mir doesn't exist yet and so there's no need to factor it into his plans for Mint. It's business as usual.

---

### Post by Mi*6d@# on 2013-03-30
> **BigSilly said:**
> I think if Ubuntu delivers on Mir and its other plans, then no doubt nVidia and ATI etc will develop their drivers for the devices, just as they have for Android. I don't think however, that this will mean that suddenly they'll cease their output for Linux support though. As has been previously stated, Ubuntu is not Linux (and I agree with previous posters that it isn't bigger than Linux either), and this is becoming more and more apparent as they pull away. Nvidia did state they wouldn't support Wayland, but this was a long time ago now. I've no doubt that graphics drivers will still be created for whatever happens to Linux (ie. not Ubuntu) in the future. My honest feeling is that whatever Ubuntu gets up to, this isn't really going to have a massive impact on the rest of the Linux world insofar as driver support. As Clem from Linux Mint stated recently, [Mir is irrelevant]("http://www.muktware.com/5356/clement-lefebvre-mir-irrelevant-linux-mint"). In the future, there'll be Ubuntu, and Linux. This makes me sad ultimately, but it's what Mark wants.
Define "Linux" then please. Last I checked Linux is merely the name of kernel which is used by Ubuntu.

Yes, Mark is trying to pull away from Linux **branding** and rightfully so. You won't gain desktop acceptance if you associate your brand with geeks and coders. But from the technical POV **Ubuntu is a Linux-based OS.**

---

### Post by neu5eeCh on 2013-03-30
> **BigSilly said:**
> My honest feeling is that whatever Ubuntu gets up to, this isn't really going to have a massive impact on the rest of the Linux world insofar as driver support. As Clem from Linux Mint stated recently, [Mir is irrelevant]("http://www.muktware.com/5356/clement-lefebvre-mir-irrelevant-linux-mint"). In the future, there'll be Ubuntu, and Linux. This makes me sad ultimately, but it's what Mark wants.

Here's the full quote from Clem:

"Lefebvre: Mir is irrelevant. Nobody ever heard of it a week ago and  plans don't change based on wild speculations. If Ubuntu isn't clear on  what they want Ubuntu to be, that's their problem. It has nothing to do  with Linux Mint."

This is a very weird reply. It seems (at least to me) that Ubuntu is being very clear as to what they want to be -- a "unified" desktop that will work across multiple platforms. I smell a strong whiff of politics throughout Clem's response. The idea that there's going to be "Ubuntu, and Linux" is silly. Like Skybon said, last I checked, Ubuntu was a Linux-based OS. 

All that said, what Clem *didn*'t say spoke volumes. As I read it, Clem will have no problem switching to MIR when and if Canonical establishes it as a viable display server.

Clem's history with Debian-based MINT has always struck me as half-hearted. My prediction (I make a lot) will be that he's going to keep riding "Mark's" coattails wherever they carry him.

---

### Post by montag dp on 2013-03-30
> **VTPoet said:**
> Here's the full quote from Clem:

"Lefebvre: Mir is irrelevant. Nobody ever heard of it a week ago and  plans don't change based on wild speculations. If Ubuntu isn't clear on  what they want Ubuntu to be, that's their problem. It has nothing to do  with Linux Mint."

This is a very weird reply. It seems (at least to me) that Ubuntu has being very clear as to what they want to be -- a "unified" desktop that will work across multiple platforms. I smell a strong whiff of politics throughout Clem's response. The idea that there's going to be "Ubuntu, and Linux" is silly. Like Skybon said, last I checked, Ubuntu was a Linux-based OS. I didn't really see the response as political, but prudent with his choice of words.  Many of us on the forum like to speculate a lot, but as the lead developer of a popular distro, that's not a very wise thing to do.  I thought his response was quite appropriate with regard to Mir.

---

### Post by BigSilly on 2013-03-30
I absolutely think Clem's approach was measured, and that was why I linked to it. Let's wait and see, is the message.

I guess what I'm saying is, with Android as an example, the fact that it has proprietary drivers and modules, this hasn't had an effect on the Linux "ecosystem" as per the thread title. I don't think Ubuntu and Mir will prove any more disruptive either. That's what I'm getting at in a roundabout way. There's Android, and there's the Linux ecosystem. There'll be Ubuntu, and the Linux ecosystem, and they don't necessarily have to have an impact on each other. I think drivers will come forward for Ubuntu if it's successful with Mir, and also Wayland when the time comes.

I'm sorry if I've got the discussion wrong, but I thought the train of thought here was that Mir would come along and take away any efforts from proprietary driver creators from the wider Linux desktop, being probably Wayland based. I'm just saying I don't imagine this will prove the case at all. Oh, and sorry for my obviously offensive use of sabdfl's first name.

---

### Post by iamkuriouspurpleoranj on 2013-03-30
Yes - it was only political in the sense that many politicians are careful with their words. Think how inadvertently inflammatory Mark's remark about having root proved to be. He was only speaking of the trust any user of a distro places in the maintainers of that distro. It pays to be careful.

---

### Post by neu5eeCh on 2013-03-30
Guess I don't see phrases like "wild speculation", in reference to MIR, as either "measured" or "politic" (or referring to their decision as "their problem"). Not seeing it, but maybe that's just me.

---

### Post by montag dp on 2013-03-30
> **VTPoet said:**
> Guess I don't see phrases like "wild speculation", in reference to MIR, as either "measured" or "politic" (or referring to their decision as "their problem"). Not seeing it, but maybe that's just me.You may well be biased.  ;)  (It's okay, we all are in some ways.)

---

### Post by Nemesis2012 on 2013-04-01
> **tartalo said:**
> KDE (and Gnome, and Enlightenment and and and) will continue with the years long work on Wayland, and won't change their plans unless they see Canonical deliver. Seems very reasonable to me.

Mir is being used in 0 distros now, I know at least 2 experimental distros that are using Wayland right now (Maui and Rebeca Black OS), if we are talking about the future, all the major distros, even Ubuntu, include Wayland in the repositories.

Arch Linux has Wayland in the repo's too

---

### Post by Stonecold1995 on 2013-04-14
> **SkyBon said:**
> Yes, Mark is trying to pull away from Linux **branding** and rightfully so. You won't gain desktop acceptance if you associate your brand with geeks and coders. But from the technical POV **Ubuntu is a Linux-based OS.**
So if you can call Ubuntu (or the future of Ubuntu) Linux, why do we not call OSX BSD?  After all, it IS based on the Mach kernel, but no one in their right mind would use anything with "Apple" and "BSD" in the same sentence!  Just because it's *technically* Linux doesn't mean it will carry any of the same philosophy as Linux.

---

### Post by monkeybrain2012 on 2013-04-14
> **Stonecold1995 said:**
> So if you can call Ubuntu (or the future of Ubuntu) Linux, why do we not call OSX BSD?  After all, it IS based on the Mach kernel, but no one in their right mind would use anything with "Apple" and "BSD" in the same sentence!  Just because it's *technically* Linux doesn't mean it will carry any of the same philosophy as Linux.

Well I for one would not want to see Ubuntu becomes to Linux as OSX to BSD. For one thing, except for the UI, most of Ubuntu is still Debian (which is not ashamed of calling itself Linux) and all software that run on Linux would run on Ubuntu and vice versa (at least in principle), that I think is good. BTW, I like the Linux philosophy and I am sure many of us who currently use Ubuntu do too.

Edited: Not following much about the saga of Wayland and Mir, but as long as it is FOSS I don't have a philosophical problem with it. But if Canonical decides to close sourced it in the future a la Apple I am leaving.

---

### Post by mJayk on 2013-04-16
> **Stonecold1995 said:**
> So if you can call Ubuntu (or the future of Ubuntu) Linux, why do we not call OSX BSD?  After all, it IS based on the Mach kernel, but no one in their right mind would use anything with "Apple" and "BSD" in the same sentence!  Just because it's *technically* Linux doesn't mean it will carry any of the same philosophy as Linux.


Its where it started and the fact that it is still open source

---

### Post by Roasted on 2013-04-17
> **monkeybrain2012 said:**
> Well I for one would not want to see Ubuntu becomes to Linux as OSX to BSD. For one thing, except for the UI, most of Ubuntu is still Debian (which is not ashamed of calling itself Linux) and all software that run on Linux would run on Ubuntu and vice versa (at least in principle), that I think is good. BTW, I like the Linux philosophy and I am sure many of us who currently use Ubuntu do too.

Edited: Not following much about the saga of Wayland and Mir, but as long as it is FOSS I don't have a philosophical problem with it. But if Canonical decides to close sourced it in the future a la Apple I am leaving.

I agree with your edit considerably. While I love many aspects of different Linux distros, I also like using a distro that does what I need. I've tried others but Ubuntu really hits the nail on the head for my uses. I personally don't think Ubuntu will ever close their source. I think their reliance on the Linux kernel will make that exponentially more difficult (well, somewhat impossible) to do as opposed to what OSX did with BSD. I was reading the About Ubuntu page the other day where they indicate open source is at the heart and soul of Ubuntu. That is really powerful, and I hope (and expect) that their dedication to retaining the open source model will continue on indefinitely, despite whatever closed source proprietary drivers and other bits they may package out of the box.

Come the day where Ubuntu decides to close off code and lock everything down Apple style, I will absolutely hit the road as well. That said, I would feel that same way with any other OS. Mint, Fedora, Debian. If I'm on any one of them and they lock the gates, they'll be written off as an OS I would no longer support or use. I just don't ever see that happening by any stretch of the imagination, so it's a crossroads I don't ever anticipate hitting.

---

### Post by neu5eeCh on 2013-04-23
Some fairly new information. Interesting and confirms what I thought might happen. NVIDIA has apparently (and strongly) [indicated that they have zero interest in developing drivers for Wayland]("http://ostatic.com/blog/kdes-future-will-be-wayland"). That means that, as far as NVIDIA is concerned, a DE like KDE will be at a disadvantage in certain situations.

On the other hand, [NVIDIA appears to be cooperating with Canonical]("http://www.golem.de/news/displayserver-mir-nvidia-kooperiert-mit-canonical-bei-der-treiberentwicklung-1303-98071.html") on the development of MIR.

Seems to me that KDE is at a turning point. I can't see how KDEs insistence on using Wayland (if the current trend holds) will result in anything other than their future marginalization. If they want to reach beyond linux enthusiasts (in the future) this doesn't seem the way to do it, but maybe they don't care.

---

### Post by lykwydchykyn on 2013-04-23
VTPoet, I think you've been victimized by some sloppy journalism at Ostatic.  The "developer" who said NVidia couldn't care less about wayland support is just a member of the Nvidia forums, there's no indication that he/she/it is a developer or NVidia employee.  In fact, looking at some of this person's other posts on the forum, it's clear they are not.

Read a few of the comments (especially the first one by a KDE developer) as it dismisses a lot of the errors and FUD in that article.

---

### Post by hainen on 2013-04-23
Besides that he speaks about egl  backend. Both Mir and Wayland use that. I suspect if Nvidia support either Mir or Wayland  they support both in the end. If not, they support  neither. They have probably not decided what they do yet. It's probably not very important for Nvidia at the moment.

also the other part of article about KDE was apperently wrong. Greasslin wrote a long article about it
[http://blog.martin-graesslin.com/blog/2013/04/the-history-on-wayland-support-inside-kwin/](http://blog.martin-graesslin.com/blog/2013/04/the-history-on-wayland-support-inside-kwin/)

---

### Post by neu5eeCh on 2013-04-23
> **lykwydchykyn said:**
> VTPoet, I think you've been victimized by some sloppy journalism at Ostatic.

Well then... caveat emptor. Glad to know KDE won't be left in the cold.

---

### Post by Gyokuro on 2013-04-24
> **VTPoet said:**
> Well then... caveat emptor. Glad to know KDE won't be left in the cold.

Here is more information where KDE is heading: [http://dot.kde.org/2013/04/24/plasma-pow-wow-produces-detailed-plans-workspace-convergence](http://dot.kde.org/2013/04/24/plasma-pow-wow-produces-detailed-plans-workspace-convergence)

---

### Post by Bill Tetzeli on 2013-05-14
> **VTPoet said:**
>  However, if I had to make a prediction, I expect that Ubuntu's move (if Ubuntu defaults to MIR) will marginalize the rest of the linux ecosystem (if the rest stubbornly refuse to follow suit). Then again, they're all largely irrelevant **anyway **(sorry Arch, Debian, Fedora, PCLOS, Redhat, etc...) Ubuntu is the only distro (and Canonical is the only company) that has a chance in the larger scheme of things. All the other distros just don't matter (and they're not in it for that reason anyway) so an extra layer of irrelevance shouldn't bother them (until and unless certain video drivers only work with certain display servers). That's when all the little wheels will start squeaking very loudly.

I strongly disagree.  These other distros carry a significance that vastly outweighs their adoption numbers, in that they can (theoretically) act as a curb on Ubuntu's darker impulses (if any).  Keep in mind that moving from Ubuntu to Debian or Mageia or Fedora isn't like moving from Windows to Linux.  Linux users are notorious distro-hoppers; just because they've settled on one distro doesn't mean they haven't tried a few others (most have).  I suspect that whichever distro is the EASIEST is the one that's going to be the top dog.  That's Ubuntu's strength right now (although with Unity some of that has passed off to Mint - I recently switched from Raring Ringtail to Mint 14 XFCE and Pear 6 on my netbook).  If Canonical gets too big for its britches, eventually it'll make a Windows 8-like, boneheaded, arrogant move that will turn everyone off.  The last thing hundreds of thousands, if not millions, of users will do with their Ubuntu volume is download a competing distro's ISO image and burn it to DVD before using it to whisk Ubuntu off to Never-Never Land.  Canonical has to be aware of this, especially with MS's woes right now.  They know that it's much easier to switch to a different distro than it is from Windows to Linux.  These "irrelevant" distros you mention are the reason why.  So while they may never have significant user share, they will continue to have significant effect.

Personally, though, I like by and large what Canonical's been doing.  The Linux success stories (server systems, Android, Roku, etc.) have all come from systems that know and are appropriate for the target user.  The reason Linux has failed in the desktop up till now is that it didn't address the target user, but the developer.  Canonical changed that.  Ubuntu and its derivatives are incredibly easy to install, set up, navigate, use (including program installation) and maintain.  That is what desktop users want - the minimum number of steps, the minimum (preferably zero) commands typed for the maximum effect and utility.  (It's funny how all the difficulties in Win 8 are pure bull, but all the difficulties in Linux have very good reasons, oh yes, yes they do.)  The computer was the province of geeks (in the worst sense of the word) till Apple popularized Mac's GUI.  That should have registered with Linux developers.  Instead, we got happy horse**** about philosophy and open-source purity, none of which meant a damn because the optical drive still won't work and the screen melts like film stuck in a projector every time I boot up.  Canonical changed that.  They made usability and ease their goal and have been the most successful at it.  If their success leads them away from that in the future, the alternative distros are chomping at their heels.  If it doesn't, I don't care how it gets accomplished.  Like 99% of all computer users, I just want the damn thing to work.  As far as Ubuntu becoming an open-source Windows - if by that one means a set standard with a large user base that software developers can target and get PAID for developing professional standard programs (and Linux multimedia ain't that - the pros all use Windows or Mac), then I'm all for it.  Like I said, as long as the OS is open source I don't care if the programs on it are open source or proprietary.  I just want them to work and live up to their billing.

---

### Post by hainen on 2013-05-14
> **Bill Tetzeli said:**
> I strongly disagree.  These other distros carry a significance that vastly outweighs their adoption numbers, in that they can (theoretically) act as a curb on Ubuntu's darker impulses (if any).  Keep in mind that moving from Ubuntu to Debian or Mageia or Fedora isn't like moving from Windows to Linux.  Linux users are notorious distro-hoppers; just because they've settled on one distro doesn't mean they haven't tried a few others (most have).  I suspect that whichever distro is the EASIEST is the one that's going to be the top dog.  That's Ubuntu's strength right now (although with Unity some of that has passed off to Mint - I recently switched from Raring Ringtail to Mint 14 XFCE and Pear 6 on my netbook).  If Canonical gets too big for its britches, eventually it'll make a Windows 8-like, boneheaded, arrogant move that will turn everyone off.  The last thing hundreds of thousands, if not millions, of users will do with their Ubuntu volume is download a competing distro's ISO image and burn it to DVD before using it to whisk Ubuntu off to Never-Never Land.  Canonical has to be aware of this, especially with MS's woes right now.  They know that it's much easier to switch to a different distro than it is from Windows to Linux.  These "irrelevant" distros you mention are the reason why.  So while they may never have significant user share, they will continue to have significant effect.

Personally, though, I like by and large what Canonical's been doing.  The Linux success stories (server systems, Android, Roku, etc.) have all come from systems that know and are appropriate for the target user.  The reason Linux has failed in the desktop up till now is that it didn't address the target user, but the developer.  Canonical changed that.  Ubuntu and its derivatives are incredibly easy to install, set up, navigate, use (including program installation) and maintain.  That is what desktop users want - the minimum number of steps, the minimum (preferably zero) commands typed for the maximum effect and utility.  (It's funny how all the difficulties in Win 8 are pure bull, but all the difficulties in Linux have very good reasons, oh yes, yes they do.)  The computer was the province of geeks (in the worst sense of the word) till Apple popularized Mac's GUI.  That should have registered with Linux developers.  Instead, we got happy horse**** about philosophy and open-source purity, none of which meant a damn because the optical drive still won't work and the screen melts like film stuck in a projector every time I boot up.  Canonical changed that.  They made usability and ease their goal and have been the most successful at it.  If their success leads them away from that in the future, the alternative distros are chomping at their heels.  If it doesn't, I don't care how it gets accomplished.  Like 99% of all computer users, I just want the damn thing to work.  As far as Ubuntu becoming an open-source Windows - if by that one means a set standard with a large user base that software developers can target and get PAID for developing professional standard programs (and Linux multimedia ain't that - the pros all use Windows or Mac), then I'm all for it.  Like I said, as long as the OS is open source I don't care if the programs on it are open source or proprietary.  I just want them to work and live up to their billing.

Why can you not use a closed source os if it do what it is supposed to do. What is the point with using ubuntu over osx if osx work at least as good and has better support for the closed source program you say you need?

---

### Post by Jack Harper on 2013-05-15
Honestly I dont know why some people are hating Mir so much,if Canonical pulls it off great,another alternative to the aging X.org,it was about time Linux community make an alternative for it,Wayland,Mir,more alternatives is more competition and better features.If Wayland cant compete and ultimately loses so be it,some people in the Linux community believe that every single open source project must survive indefinitely,that is not always good,I always wondered as to why Linux community didnt start working on X.org replacement earlier.Linux must evolve and that means some things are meant to be changed.Whether other distributions will adopt Mir it remains to be seen,I am sure some will be stubborn enough to refuse to adopt it even if it turns out to be a brilliant piece of software.I like innovations and Mir and Unity on QT/QML,along with mobile/tablet/desktop compatible OS is very interesting to me,but haters are going to hate,and being a Linux user for about 12 years now I have seen my share of dinosaur attitudes of some people in the Linux community,they simply refuse to go along with innovations,still clinging to their very old ways.They are afraid of losing their precious toy because it will no longer be cool to use Linux if many people use it,you can see that happening even now as such people switch to Gentoo,Arch and similar distributions because they are for "advanced users" and Ubuntu and other "user friendly" distributions are for "beginners".It is not likely that Ubuntu will ever become a completely closed source project,that would make no sense,what Ubuntu will hopefully become is an integrated multipurpose OS that grows and is available for all devices,for personal and business use.I hope Canonical will succeed with Mir,Unity on QT/QML and multipurpose OS because that is where the future is.Dinosaurs that refuse to change will end up like Nokia that refused to adopt Android and is now on a steady decline.There is nothing wrong with an OS that can run on mobile phones,tablets,desktops and servers,in fact it is brilliant and I hope they succeed :)

---

### Post by zemega on 2013-05-15
The fact that Wayland is slow before Mir was announced shows that lack of competetion and option makes 'one' slow/dependant/not motivated/etc. 
Its important for the display server to be able to adapt to many things 'physically' in the future. When can I put displays on my refrigerator so that I can keep tracks of th things inside the fridge? I don't need a full size motherboard inside the fridge, I just need something like raspberry pi, and some advanced monitor on the fridge (OLED, transparent, plasma or whatever works). In fact getting a stock phone just to do that is great, but it will need stock OS that can do lots of things, and Ubuntu is headed that way. 

The future for me is that, almost everything will have display on it, from tables, fridge, walls, even simple electrical (light, fan, stuff) switch will use a display system (assuming that a small 5x5 cm display can control all the lights, fans, ventilation, aircond, valves, in the house/office). Can Wayland do that? Can X do that? Can Mir do that? Can it do it beautifully and smooth? There might not be anymore physical keys in keyboards, its all a display sytem with touch input, you just touch them instead of hitting them. It might sound to scifi, but thats one of the possible feature. I dont see or hear Wayland going to do something about this, Wayland probably will just be a desktop display server, instead of an all-around you can put anywhere.

It seems Mir is going that way, seemless intergration between display output and touch input (well its not just Mir, but the OS as well). Ubuntu and Mir is going to break the touch input barrier, not counting Android of course they did a great job in that, but they just have different phylosophy compared to desktop Linux. 

I can see that I can just put one Ubuntu device in the kitchen and be able to have multiple touch display on the fridge, table top, cabinets and stuff. One Ubuntu device in my office, have multiple displays to it, have multiple inputs to it, and many other functions. Instead of an OS for a tablet, server, phone and desktop, it can be an OS that can run the house or office environments. Assuming people will not put in an overzealous A.I. into it and give birth to SkyNet.

---

### Post by lykwydchykyn on 2013-05-15
Nobody I know of is "hating Mir", unless "hate" means "everyone isn't dropping their plans and years of work to move to a display server project which was just announced out of nowhere".    If you don't understand the reasons why non-Ubuntu projects aren't jumping up and down to support it, here is a breakdown of the reasons from a KDE developer:

[http://blog.martin-graesslin.com/blog/2013/05/mir-in-kubuntu/](http://blog.martin-graesslin.com/blog/2013/05/mir-in-kubuntu/)

I invite you to read and contemplate some of these reasons and point of view rather than just conclude that all non-ubuntu free software developers are small-minded haters.

---

### Post by Jack Harper on 2013-05-15
> **lykwydchykyn said:**
> Nobody I know of is "hating Mir", unless "hate" means "everyone isn't dropping their plans and years of work to move to a display server project which was just announced out of nowhere".    If you don't understand the reasons why non-Ubuntu projects aren't jumping up and down to support it, here is a breakdown of the reasons from a KDE developer:

[http://blog.martin-graesslin.com/blog/2013/05/mir-in-kubuntu/](http://blog.martin-graesslin.com/blog/2013/05/mir-in-kubuntu/)

I invite you to read and contemplate some of these reasons and point of view rather than just conclude that all non-ubuntu free software developers are small-minded haters.

I didnt mean people with objective concerns like the author of the blog post you mention,I meant a portion of Linux users,try reading comments on various articles on Mir around the Internet,plenty of hate,from Phoronix to other Linux related websites.Not that I am saying they dont have a right to voice their own opinion,they do but some are hating Mir because they apparently have a need to bash Canonical and Ubuntu just for the sake of it,they dont even bother to wait until the Mir is published to see how the whole situation will play out,and then make comments with some arguments.

---

### Post by Stonecold1995 on 2013-05-15
> **Jack Harper said:**
> I didnt mean people with objective concerns like the author of the blog post you mention,I meant a portion of Linux users,try reading comments on various articles on Mir around the Internet,plenty of hate,from Phoronix to other Linux related websites.Not that I am saying they dont have a right to voice their own opinion,they do but some are hating Mir because they apparently have a need to bash Canonical and Ubuntu just for the sake of it,they dont even bother to wait until the Mir is published to see how the whole situation will play out,and then make comments with some arguments.
People don't bash Canonical "just for the sake of it".  They/we bash them because they pulled out a dirty trick that one would expect only something like Microsoft or Apple to do.  I mean, developing a display driver is fine, and developing a competing display driver is fine, but the way the presented it, after lying publically to everyone, is just wrong.  Especially considering Mir's purpose and limitations.

---

### Post by smellyman on 2013-05-16
lying?

---

### Post by Stonecold1995 on 2013-05-16
> **smellyman said:**
> lying?
Announcing that they'll work on Wayland and that NVidia is willing to work with Wayland but secretly developing Mir, and then suddenly announcing "just kidding, we weren't actually planning on using Wayland at all".

---

### Post by montag dp on 2013-05-16
> **Stonecold1995 said:**
> Announcing that they'll work on Wayland and that NVidia is willing to work with Wayland but secretly developing Mir, and then suddenly announcing "just kidding, we weren't actually planning on using Wayland at all".Didn't they also publish some falsehoods about Wayland in their original post explaining why they were going to develop Mir?  From what I've read, that didn't go over well either.

I should mention that I'm also fine with it if they want to develop their own display server, but I think they owe it to the community to be a bit more up-front about they are doing, and not try to mislead people.

---

### Post by smellyman on 2013-05-17
saying you didn't eat a cookie when in fact you did is lying.

I guess I lie all the time when I change plans

---

### Post by lykwydchykyn on 2013-05-17
Changing plans wasn't lying, but spreading falsehoods about Wayland was.  They later apologized, but I'm still seeing the same memes floating around as if they were fact.

---

### Post by Stonecold1995 on 2013-05-18
> **lykwydchykyn said:**
> Changing plans wasn't lying, but spreading falsehoods about Wayland was.  They later apologized, but I'm still seeing the same memes floating around as if they were fact.
What's the point of appoligizing if they don't do anything about it?  Just because you can say sorry doesn't make it right, especially if you still go ahead and do it.

---

### Post by Perfect Storm on 2013-05-18
> **Stonecold1995 said:**
> What's the point of appoligizing if they don't do anything about it?  Just because you can say sorry doesn't make it right, especially if you still go ahead and do it.

About what? Not starting on the Mir project. Doesn't make sense. Done is done, apology is given. People need to start to move on.

---

### Post by Stonecold1995 on 2013-05-19
> **Artificial Intelligence said:**
> About what? Not starting on the Mir project. Doesn't make sense. Done is done, apology is given. People need to start to move on.
But they're continuing to work on Mir and are continuing their plans after lying about Wayland to everyone, that's the whole point.

---

### Post by Perfect Storm on 2013-05-19
> **Stonecold1995 said:**
> But they're continuing to work on Mir and are continuing their plans after lying about Wayland to everyone, that's the whole point.

and....?

It's common in the linux world if you're unhappy with something you fork or make your own stuff for whatever reasons.

---

### Post by Stonecold1995 on 2013-05-21
> **Artificial Intelligence said:**
> and....?

It's common in the linux world if you're unhappy with something you fork or make your own stuff for whatever reasons.
There's nothing wrong with forking something or creating something, it's HOW they did it, how they severely messed up plans for OTHER distros to use Wayland as well, jeopardizing distros like Kubuntu and damaging chances that Wayland will have a working Nvidia driver (which both them and Nvidia had lied about, all the while working on their OWN project behind closed doors).

And it wasn't just a "mistake" either, so appologizing and moving on is not fixing the problem.

---

### Post by llanitedave on 2013-05-22
They can't "unHow" it.  So what you prefer?  Tarring and feathering?  Public lynchings?  Honor suicides?  Burn all Mir builds and fire the developers?  Ubuntu cease to exist?  Pinin' for the fjords?

Or maybe you can actually make a positive contribution on your own account to whatefer you think the right solution is?  Otherwise, you just seem to be drinking the cup of bitterness and savoring the flavor.

---

### Post by Bazon on 2013-05-23
the effect it had on me: i love the flexibility of gnome-shell and i don't use any ubuntu specific developments at all. so my consequence was: goodbye ubuntu. i moved to arch on my main computer, it is great, my other computers will follow.

---

### Post by Leuchten on 2013-05-24
The mir stuff didn't push me from Ubuntu, but if I was still using kubuntu it would've, and not just because KDE says they won't support mir. It's ridiculous how insular ubuntu is becoming.

Oh, and by the way, steam is not ubuntu only. I have steam working perfectly fine on fedora 18.

---

### Post by dodo3773 on 2013-05-24
> **Artificial Intelligence said:**
> and....?

It's common in the linux world if you're unhappy with something you fork or make your own stuff for whatever reasons.

Why "and..?"? Does it not concern you that the upstream developers would lie or mislead the community with respects to development? Not at all? Not even with a public apology / admission of guilt? I do not understand your position clearly I don't think. Mir / Wayland / foobarbaz doesn't matter. Not the point. At least that's not how I took the comment that was responded to.   

On to the original topic: Reading the motivation behind Mir reasons on the wiki Mir/Spec it seems like Mir would be something that would help out more for mobile platforms to me. If that's it then it makes enough sense I guess. I can't imagine it making any huge difference for my use case either way though since I don't run Ubuntu or keep up with the newest commercial/closed applications and games and steam and stuff. My opinion is that a more collaborated effort would have a more beneficial "effect on Linux "Ecosystem"". As far as I can tell Mir source code is up on launchpad either way. If they do something truly great I don't see why wayland couldn't use some of the codebase if they wanted to or take a look at it at least. So, in that respect it may not be so bad for the ecosystem. But, I still think it's more bad than good at this point (I admit I still know little about the mir / wayland thing from a technical standpoint (no shortage of opinionated articles to read on the internet though I'm sure)).  Guess we'll just have to wait and see.

---

### Post by mips on 2013-05-24
> **dodo3773 said:**
> Does it not concern you that the upstream developers would lie or mislead the community with respects to development? Not at all?

I don't think people are to worried about things like lying & ethics, just the way people are.

---

### Post by hainen on 2013-05-24
> **dodo3773 said:**
> Why "and..?"? Does it not concern you that the  upstream developers would lie or mislead the community with respects to  development? Not at all? Not even with a public apology / admission of  guilt? I do not understand your position clearly I don't think. Mir /  Wayland / foobarbaz doesn't matter. Not the point. At least that's not  how I took the comment that was responded to.   

On to the original topic: Reading the motivation behind Mir reasons on  the wiki Mir/Spec it seems like Mir would be something that would help  out more for mobile platforms to me. If that's it then it makes enough  sense I guess. I can't imagine it making any huge difference for my use  case either way though since I don't run Ubuntu or keep up with the  newest commercial/closed applications and games and steam and stuff. My  opinion is that a more collaborated effort would have a more beneficial  "effect on Linux "Ecosystem"". As far as I can tell Mir source code is  up on launchpad either way. If they do something truly great I don't see  why wayland couldn't use some of the codebase if they wanted to or take  a look at it at least. So, in that respect it may not be so bad for the  ecosystem. But, I still think it's more bad than good at this point (I  admit I still know little about the mir / wayland thing from a technical  standpoint (no shortage of opinionated articles to read on the internet  though I'm sure)).  Guess we'll just have to wait and see.
Wayland has MIT licence and canonical use a gpl license. Canonical can reuse wayland stuff (as we have seen) but Wayland can not use MIR code.

---

### Post by hainen on 2013-05-24
I have a feeling it unlikely stuff like [http://www.collabora.com/videos/rpi-wayland-demo-720p.webm](http://www.collabora.com/videos/rpi-wayland-demo-720p.webm) occurs to MIR

---

### Post by Perfect Storm on 2013-05-24
> **dodo3773 said:**
> Why "and..?"? Does it not concern you that the upstream developers would lie or mislead the community with respects to development? Not at all? Not even with a public apology / admission of guilt? I do not understand your position clearly I don't think. Mir / Wayland / foobarbaz doesn't matter. Not the point. At least that's not how I took the comment that was responded to.   

On to the original topic: Reading the motivation behind Mir reasons on the wiki Mir/Spec it seems like Mir would be something that would help out more for mobile platforms to me. If that's it then it makes enough sense I guess. I can't imagine it making any huge difference for my use case either way though since I don't run Ubuntu or keep up with the newest commercial/closed applications and games and steam and stuff. My opinion is that a more collaborated effort would have a more beneficial "effect on Linux "Ecosystem"". As far as I can tell Mir source code is up on launchpad either way. If they do something truly great I don't see why wayland couldn't use some of the codebase if they wanted to or take a look at it at least. So, in that respect it may not be so bad for the ecosystem. But, I still think it's more bad than good at this point (I admit I still know little about the mir / wayland thing from a technical standpoint (no shortage of opinionated articles to read on the internet though I'm sure)).  Guess we'll just have to wait and see.

Then people needs to go out more, if they get worked up by this. There are much worse crime in the world than this. It isn't the first time misleading/misinformation have apperared in the open source community or in IT generally. There are people behind these project afterall, and where people is mistakes etc. will happen. I don't underestand the vendetta in such cases, live and let live...

But I suspect because it's Canonical made a mistake, it needs to burn down to the ground and the ashes scattered into the void.

---

### Post by dodo3773 on 2013-05-24
> **mips said:**
> I don't think people are to worried about things like lying & ethics, just the way people are.

Yeah, I suppose your right. No need to apologize then though. They should have just told the community to get bent instead since that's the truth. 

> **hainen said:**
> Wayland has MIT licence and canonical use a gpl license. Canonical can reuse wayland stuff (as we have seen) but Wayland can not use MIR code.

Then I don't see how it could be good in any realistic way at all for the rest of the ecosystem. That should sum it all up there. But could you elaborate on this a little more?

Edit: Now that I think about it a little more I really don't think it's going to have a huge effect either way on the larger community. 

> **Artificial Intelligence said:**
> Then people needs to go out more, if they get worked up by this. There are much worse crime in the world than this. It isn't the first time misleading/misinformation have apperared in the open source community or in IT generally. There are people behind these project afterall, and where people is mistakes etc. will happen. I don't underestand the vendetta in such cases, live and let live...



But I suspect because it's Canonical made a mistake, it needs to burn down to the ground and the ashes scattered into the void.


I simply meant that the whole thing is disconcerting to me as a human. Not as an end user / developer whatever. If it was a simple mistake then it wouldn't matter at all (although if it was a simple mistake surely it would have been justifiable and would have not required an apology (not that one is required anyways since apologies are a waste of time to begin with (I agree with Stonecold1995's sentiment on that absolutely))). I have no vendetta. The world will keep turning irrespective of which direction Canonical decides to take. Similar to when they started the Unity desktop thing. It does seem like Ubuntu is slowing becoming something that the community would no longer consider GNU/Linux though (in the free sense). At least that is my perceived direction that it is taking. They are becoming an island in my eyes. I do agree with you on other people in the community making mistakes or not following through on things. I have seen that a few times. The only argument I have read so far in favor of this being good to the community was by 3rdalbumn which stated "[COLOR=#8A8A8A]Wayland development will speed up to a furious pace to compete with Mir, which will benefit all distros that may ship Wayland in the future.[/COLOR]".

Edit: I think the move has a bigger impact on how other people in the community perceive Ubuntu rather than the technical advantages or disadvantages.

---

### Post by hainen on 2013-05-24
> **dodo3773 said:**
> Yeah, I suppose your right. No need to apologize then though. They should have just told the community to get bent instead since that's the truth. 



Then I don't see how it could be good in any realistic way at all for the rest of the ecosystem. That should sum it all up there. But could you elaborate on this a little more?


I'm on extremly thin ice now as I really dont versed in licenses. But as I'm understands it. GPL  require linked code is under gpl, but double licensing is fine. Mit licence allow double licensing the code as  gpl/mit. The effect is you can take mit code and double license in a gpl project. But as gpl don't allow double licensing. If you take gpl code to your mit licensed project you need re-license the project as gpl.

---

### Post by dodo3773 on 2013-05-24
> **hainen said:**
> I'm on extremly thin ice now as I really dont versed in licenses. But as I'm understands it. GPL  require linked code is under gpl, but double licensing is fine. Mit licence allow double licensing the code as  gpl/mit. The effect is you can take mit code and double license in a gpl project. But as gpl don't allow double licensing. If you take gpl code to your mit licensed project you need re-license the project as gpl.

Okay so in this respect wouldn't the fault be with wayland upstream then rather than mir? Why not just gpl?

---

### Post by Stonecold1995 on 2013-05-24
> **mips said:**
> I don't think people are to worried about things like lying & ethics, just the way people are.
Um, yes they are.  *Especially* in the open source software community.

---

### Post by JDShu on 2013-05-24
> **dodo3773 said:**
> Okay so in this respect wouldn't the fault be with wayland upstream then rather than mir? Why not just gpl?

Because it's really low down the stack - anything that uses Mir libraries may need to be GPL'd depending on the legal specifics and many important applications would need to use the display server libraries. This could make it hard for third parties to write applications using Mir. Specifically, Martin Graesslin [argues]("http://blog.martin-graesslin.com/blog/2013/05/mir-in-kubuntu/") that KWin would be unable to use Mir without switching the whole codebase to GPLv3. Whether GPLv3 only is an acceptable license is a different debate, but the point is that it limits the choices of people who want to develop using Mir.

---

### Post by dodo3773 on 2013-05-24
> **JDShu said:**
> Because it's really low down the stack - anything that uses Mir libraries may need to be GPL'd depending on the legal specifics and many important applications would need to use the display server libraries. This could make it hard for third parties to write applications using Mir. Specifically, Martin Graesslin [argues]("http://blog.martin-graesslin.com/blog/2013/05/mir-in-kubuntu/") that KWin would be unable to use Mir without switching the whole codebase to GPLv3. Whether GPLv3 only is an acceptable license is a different debate, but the point is that it limits the choices of people who want to develop using Mir.

So would you say that this move may in a way actually be self defeating (on the desktop specifically not a phone)?

---

### Post by JDShu on 2013-05-25
> **dodo3773 said:**
> So would you say that this move may in a way actually be self defeating (on the desktop specifically not a phone)?

I personally think so. I think the realistic outcome is that Mir will miss the deadlines and hobble along until it dissipates under a mountain of technical debt and hard problems. It's not going to destroy the community like some say, but it's also very unlikely to succeed within a reasonable timeframe. But hey, I could be completely wrong... let's see if Canonical can surprise me :)

---

### Post by zemega on 2013-05-25
Can we talk about software or programs in Linux and how this situation is going to impact them? Would developer stop supporting Ubuntu just because of Mir. Would mainstream favourite developer such as Skype and Steam stop supporting Ubuntu? How about obscure scientific software, such as CDO and GrADS? If Ubuntu is no longer supported just because they're using Mir, that means some user will have to leave Ubuntu and go to other distros, or worse go back to Windows. Apart from the OS itself, software distribution is an important point in this Linux ecosystem.

---

### Post by LordDelta on 2013-05-25
My two cents:

Anti-Mir is nonsense. I think Wayland and Mir is just the right number (well, maybe room for one or two more display servers) of display servers.

X11 was the truly atrocious situation. Yes, it works fine now, but how long did that take? 30 years? 40? Why? Partly, because there was little competition. Partly, because there was only one system, there was only one system, and no way to change it.

This time, yeah, Wayland will be stable and working, years ahead of Mir. But, it also won't be able to respond to change as quickly - 4 years of development aren't going to change themselves overnight.

As long as there is some common interchange standard everyone can agree on, I think we'll be fine. I don't know what that will be, but I could forsee it being OpenGL, or some XML or JSON standard.

---

### Post by neu5eeCh on 2013-05-27
Just installed Xubuntu 13.04 and noted that my AMD Catalyst Drivers wouldn't have worked if I had chosen Unity as my DE. Glad I was able to revert to the pre-patched version of X. The only thing that stops tear-out when watching vids are the proprietary drivers. If not for the FLGRX drivers, I would probably revert to Windows on this laptop (VAIO 64bit with Radeon).

And that brings me to MIR. I assume, if Ubuntu switches to MIR, all those old proprietary drivers are no longer going to work. This means that I will probably have to give up Ubuntu at some point. I'm certain I'm not the only one whose going to have these issues. Once Ubuntu switches to MIR, is it reasonable to assume that thousands of users, like myself, who rely on older ATI drivers, will have to look for a distro that still uses X?

---

### Post by dodo3773 on 2013-05-27
> **VTPoet said:**
> Just installed Xubuntu 13.04 and noted that my AMD Catalyst Drivers wouldn't have worked if I had chosen Unity as my DE. Glad I was able to revert to the pre-patched version of X. The only thing that stops tear-out when watching vids are the proprietary drivers. If not for the FLGRX drivers, I would probably revert to Windows on this laptop (VAIO 64bit with Radeon).

And that brings me to MIR. I assume, if Ubuntu switches to MIR, all those old proprietary drivers are no longer going to work. This means that I will probably have to give up Ubuntu at some point. I'm certain I'm not the only one whose going to have these issues. Once Ubuntu switches to MIR, is it reasonable to assume that thousands of users, like myself, who rely on older ATI drivers, will have to look for a distro that still uses X?

I don't think this will be the case. As far as I know wayland has some sort of X emulation (reusing dri drivers at least (doesn't that apply to amd/ati drivers?)) I would be surprised if mir didn't have something similar. They seem like they would have to at least to some extent otherwise a lot of application compatibility would be lost I would think. Doesn't seem logical.

---

### Post by neu5eeCh on 2013-05-27
> **dodo3773 said:**
> I don't think this will be the case. As far as I know wayland has some sort of X emulation (reusing dri drivers at least (doesn't that apply to amd/ati drivers?)) I would be surprised if mir didn't have something similar. They seem like they would have to at least to some extent otherwise a lot of application compatibility would be lost I would think. Doesn't seem logical.

The current FGLRX drivers won't work on MIR unless AMD modifies them. I think it *_extremely_* unlikely that AMD would spend time and money on such an undertaking. There's _nothing_, absolutely nothing, in it for them. While Wayland and MIR may have X-emulators, this is a different type of functionality.

It's particularly odd because Unity currently relies on 3D capable hardware (they've gotten rid of Unity 2D). So what the heck do they expect a million users to do when they switch to MIR and and all those proprietary 3D drivers no longer work? Am I not getting something?

---

### Post by deadflowr on 2013-05-27
> **VTPoet said:**
> The current FGLRX drivers won't work on MIR unless AMD modifies them. I think it *_extremely_* unlikely that AMD would spend time and money on such an undertaking. There's _nothing_, absolutely nothing, in it for them. While Wayland and MIR may have X-emulators, this is a different type of functionality.

It's particularly odd because Unity currently relies on 3D capable hardware (they've gotten rid of Unity 2D). So what the heck do they expect a million users to do when they switch to MIR and and all those proprietary 3D drivers no longer work? Am I not getting something?

I believe that neither mir or wayland can run closed-source drivers at this point.
At least with mir I know that it can only run open-source drivers, but I'm almost certain it's the same with wayland.

---

### Post by dodo3773 on 2013-05-27
> **deadflowr said:**
> I believe that neither mir or wayland can run closed-source drivers at this point.
At least with mir I know that it can only run open-source drivers, but I'm almost certain it's the same with wayland.

Oh I see. well that's a bummer then. There is a number of other great distros though.

---

### Post by deadflowr on 2013-05-27
> **dodo3773 said:**
> Oh I see. well that's a bummer then. There is a number of other great distros though.

I should clarify that's on the desktop.

Not sure about phones or tablets.

But we will have nice front row seats when the closed source drivers choose which side they will support, or if they shun both and we have to use X forever on the desktop.

---

### Post by neu5eeCh on 2013-05-28
> **deadflowr said:**
> I should clarify that's on the desktop.

Not sure about phones or tablets.

But we will have nice front row seats when the closed source drivers choose which side they will support, or if they shun both and we have to use X forever on the desktop.

I find it hard to believe that Canonical would seriously leave behind a major portion of its user base. Really? I'm willing to go out on a limb and assert that the vast majority of Ubuntu installs are on older hardware. Is Shuttleworth really going to give all these people the finger?  

And what about the burgeoning game market on Ubuntu? Are all these gamers going to give up their proprietary drivers for MIR? That's insanity. Well... I've got my front row seat and my popcorn. Looks like it's going to be an exciting movie. :popcorn:

---

### Post by monkeybrain2012 on 2013-05-28
> **VTPoet said:**
> I find it hard to believe that Canonical would seriously leave behind a major portion of its user base. Really? I'm willing to go out on a limb and assert that the vast majority of Ubuntu installs are on older hardware. Is Shuttleworth really going to give all these people the finger?  

And what about the burgeoning game market on Ubuntu? Are all these gamers going to give up their proprietary drivers for MIR? That's insanity. Well... I've got my front row seat and my popcorn. Looks like it's going to be an exciting movie. :popcorn:

I think this will be ironed out when Mir makes its appearance. Canonical works with Steam to bring gaming to Linux (supports Ubuntu first) I am sure they are aware of that.

---

### Post by deadflowr on 2013-05-28
I read this last night/this morning (twas late)

[http://www.omgubuntu.co.uk/2013/05/mark-shuttleworth-on-mir-unity8-future](http://www.omgubuntu.co.uk/2013/05/mark-shuttleworth-on-mir-unity8-future)

---

### Post by neu5eeCh on 2013-05-28
> **monkeybrain2012 said:**
> I think this will be ironed out when Mir makes its appearance. Canonical works with Steam to bring gaming to Linux (supports Ubuntu first) I am sure they are aware of that.

Translation: "No, really, the ship is unsinkable." ;)

---

### Post by monkeybrain2012 on 2013-05-29
> **deadflowr said:**
> I read this last night/this morning (twas late)

[http://www.omgubuntu.co.uk/2013/05/mark-shuttleworth-on-mir-unity8-future](http://www.omgubuntu.co.uk/2013/05/mark-shuttleworth-on-mir-unity8-future)

"The current plan is to stretch for Unity 8 in 14.04 LTS, but we are  confident we can have Unity 7 running there just fine. We already  support Unity 7 and it’s getting faster and cleaner as we go,.."

So does this mean that there will still be an option to use x in 14.04? If that is the case I am not too worry, it will be another 6 years before Mir becomes the only option.

---

### Post by deadflowr on 2013-05-29
> **monkeybrain2012 said:**
> "The current plan is to stretch for Unity 8 in 14.04 LTS, but we are  confident we can have Unity 7 running there just fine. We already  support Unity 7 and it&#8217;s getting faster and cleaner as we go,.."

So does this mean that there will still be an option to use x in 14.04? If that is the case I am not too worry, it will be another 6 years before Mir becomes the only option.

Being that they're pressing hard just to get something into the repos for testing on 13.10 tells me that they won't make it to a full switch by 14.04.

And if by some chance they did make it and a change happens, you can expect an even larger migration from Ubuntu to other flavors or distros.

I think moving to mir as the default display server, in less than a year, would be more disastrous then when they switched to unity for 11.04.

But adding it for 14.10 and beyond seems like a better, more rational direction.

---

### Post by monkeybrain2012 on 2013-05-29
> Being that they're pressing hard just to get something into the  repos for testing on 13.10 tells me that they won't make it to a full  switch by 14.04.

Yeah to make a full switch to Mir in the LTS without full blown testing in a productive environment (13.10 ) first is utterly insane. But I don't think Mark Shuttleworth has completely lost his marbles, so I interpret his answer to OMG to mean "We set the high (perhaps not realistically  attainable) goal of getting Unity 8 and Mir into a workable state by 14.04 but it will not be the only option, Unity 7 (hence X) will still be supported in 14.04 and we have made many improvement there as well"

---

### Post by neu5eeCh on 2013-05-29
> **deadflowr said:**
> And if by some chance they did make it and a change happens, you can expect an even larger migration from Ubuntu to other flavors or distros.

Many flavors and distros seem to be moving toward Wayland. This will also render 3rd party video drivers (designed for X), perfectly useless. It may turn out to be a tough situation for many linux users. One of the long-vaunted advantages of Linux has been the ability to use it on older hardware. This may no longer be the case and many users, on older machines, might well be driven back to windows (*if* they want to take full advantage of their video cards) or increasingly niche-y linux distributions based on Ubuntu (perhaps) but running X.

---

### Post by lykwydchykyn on 2013-05-29
> **VTPoet said:**
> One of the long-vaunted advantages of Linux has been the ability to use it on older hardware. 

I think we've already entered an era where "normal" mainstream distros don't do any better on older hardware than Windows, and only specialized "lightweight" distros are aimed at older hardware.

---

### Post by zemega on 2013-05-29
Its certainly true some harware is old now. And I do think its time to upgrade your computer/laptop for cheap now. Look at Asus future model, 2x1GHz cpu, intergrated graphic (probably ati radeon or intel), and 2gb ram (hopefully upgradeable) for less than 300USD. The price of Windows 7 is more than half of the laptop price. And if distros want to move forward, it got to keep up and use the potential of current technology while maintaining support for technology a few years before. A distro won't be popular if it can only use half of the technology or capability of the technology/spec of the user. Its also means Linux user must also let go of really old hardware, and change/upgrade to latest or slightly new/old.
Edit: Although I don't mind if Ubuntu/Canonical release a remix for old hardware, like the netbook remix before. Simple Unity (no fancy blur, depth or transparency), simple browser and other stuffs, and probably uses X. Although If they can make Mir to be lightweight, and better than X, that would be a better choice.

Isnt X can do many things, but a user don't really need that much. Would not that means Mir might just be lighter than X?

---

