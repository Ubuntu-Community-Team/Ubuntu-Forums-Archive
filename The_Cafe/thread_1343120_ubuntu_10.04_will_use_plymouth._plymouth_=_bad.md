---
title: "ubuntu 10.04 will use plymouth. plymouth = bad?"
date: 2009-12-01
forum: The Cafe
---

### Post by sudoer541 on 2009-12-01
ubuntu 10.04 will use [Plymouth]("http://www.omgubuntu.co.uk/2009/12/lucid-to-use-plymouth-non-intel-users.html") however this is a problem.

---

### Post by earthpigg on 2009-12-01
wow, that website is horribly cluttered.

---

### Post by sudoer541 on 2009-12-01
> **earthpigg said:**
> wow, that website is horribly cluttered.
+1

---

### Post by RiceMonster on 2009-12-01
Why didn't they just go with plymouth in the first place? I mean, they created Xsplash, even though plymouth was already there, and now they're going to dump it? Then again, the article doesn't offer any real source to show the decision was made.

Furthermore, plymouth is not bad. It just makes use of KMS, which is not available from proprietary drivers.

---

### Post by cariboo on 2009-12-01
+1, I find it pretty annoying with all the extra clutter. I've stopped clicking on links to the site.

---

### Post by PryGuy on 2009-12-01
Hmmm, well, that's strange if it's true, 'cause Canonical rejected Plymouth in Karmic for some reason. Plymouth is truly incredible, but why they aborted it for Karmic I wonder?

---

### Post by gnomeuser on 2009-12-01
Plymouth has a vesa fallback, it won't give you the flickerfree experience in full but any card can use it. 

Plymouth is full of awesome.

Regardless, out of the box you should get KMS on intel, ati and nvidia (nouveau works great for this - no 3d acceleration though but that is coming along).

---

### Post by NoaHall on 2009-12-01
I've never trusted any news report from that site since he went a little crazy and posted the wrong information about chrome os(it was just the browser.)

Anyway, any problems - you know what the fix it. ```
 sudo apt-get remove plymouth && sudo apt-get install xsplash
```

---

### Post by FuturePilot on 2009-12-01
That doesn't make any sense. They put a heck of a lot of work into creating Xsplash and making it work nicely only to dump it on the next release!? :-s

---

### Post by sudoer541 on 2009-12-01
dont know if I understood, but the article stated that plymouth will affect compiz.

---

### Post by NoaHall on 2009-12-01
> **sudoer541 said:**
> dont know if I understood, but the article stated that plymouth will affect compiz.

Compiz doesn't run until you log in. And normally not straight away, either.

---

### Post by RiceMonster on 2009-12-01
> **sudoer541 said:**
> dont know if I understood, but the article stated that plymouth will affect compiz.

It doesn't; it's just a bootscreen. Iif you want to use compiz with ATI or nVidia, you'll have to use the proprietary drivers, which don't have KMS support, and thus, you won't be getting a flicker-free experience from plymouth.

---

### Post by vishzilla on 2009-12-01
1. No reliable source
2. Plymouth is awesome
3. Its great if you have Intel card although there are workarounds for the other cards
4. I am currently using Plymouth in Arch

---

### Post by PryGuy on 2009-12-01
> **futurepilot said:**
> that doesn't make any sense. They put a heck of a lot of work into creating xsplash and making it work nicely only to dump it on the next release!? :-s+1

---

### Post by sudoer541 on 2009-12-01
> **RiceMonster said:**
> It doesn't; it's just a bootscreen. Iif you want to use compiz with ATI or nVidia, you'll have to use the proprietary drivers, which don't have KMS support, and thus, you won't be getting a flicker-free experience from plymouth.

so 
compiz = no flicker free startup
and 
flicker free startup= no compiz 
? I am very confused!

---

### Post by NoaHall on 2009-12-01
> **sudoer541 said:**
> so 
compiz = no flicker free startup
and 
flicker free startup= no compiz 
? I am very confused!

Yep, that just about sums it up.

---

### Post by RiceMonster on 2009-12-01
> **sudoer541 said:**
> so 
compiz = no flicker free startup
and 
flicker free startup= no compiz 
? I am very confused!

To get a flicker free startup with plymouth, the graphics driver needs to be able to use KMS (kernel mode setting), which means the screen resolution and depth mode are set by the kernel. This is not possible with the proprietary drivers from ATI and nVidia, because of licensing issues, and the fact that it's just not implemented (and won't be). However, you can use KMS with the open source drivers, but they don't not have 3D support, which is required to use compiz. Therefore, you can't use compiz with the drivers plymouth is designed to work with. So what you said is more or less right.

Make sense?

---

### Post by FuturePilot on 2009-12-01
Haha, more things that don't make sense. They've been working so hard to make a flicker free boot experience on all graphics cards which is why they didn't go with Plymouth since KMS won't work with proprietary graphics drivers. So now they're going to screw over everyone but Intel graphics users? I doubt they put all that work into the boot experience for Karmic only to start from scratch again with Lucid.

The article mentions [this]("http://www.nvnews.net/vbulletin/showpost.php?p=1841465&postcount=4") post but obviously they haven't seen [this]("http://www.nvnews.net/vbulletin/showpost.php?p=1946400&postcount=5") post.

Also, that article is lacking a source for the info. In my eyes the credibility of that site is fading fast.

---

### Post by LowSky on 2009-12-01
So if you want to use Proprietary drivers just set the PC to boot showing text. I doubt most people care about the flickering or the splash screen in question.

---

### Post by forrestcupp on 2009-12-01
> **RiceMonster said:**
> This is not possible with the proprietary drivers from ATI and nVidia, because of licensing issues, and the fact that it's just not implemented (and won't be).

Why can't they use some kind of shim to get around the licensing issues?  They pretty much already do that for other issues, don't they?

---

### Post by sudoer541 on 2009-12-01
> **forrestcupp said:**
> why can't they use some kind of shim to get around the licensing issues?  They pretty much already do that for other issues, don't they?

+1

---

### Post by NoaHall on 2009-12-01
> **forrestcupp said:**
> Why can't they use some kind of shim to get around the licensing issues?  They pretty much already do that for other issues, don't they?

Because they don't care about how Ubuntu wants to do things - Ubuntu doesn't earn them the money from Linux.

---

### Post by Keyper7 on 2009-12-01
It seems that the idea is to replace usplash by Plymouth, not xsplash.

However, this makes even less sense. So there will be Plymouth AND xsplash?

---

### Post by Paqman on 2009-12-01
> **LowSky said:**
> So if you want to use Proprietary drivers just set the PC to boot showing text. I doubt most people care about the flickering or the splash screen in question.

Text? Bleugh! 

Xsplash is lovely, i'd hate to see it go. There's no way in hell i'd turn off Compiz to get a nicer splash screen though.

---

### Post by whoop on 2009-12-01
I haven't looked at the technical side of this at all, so I'll probably make no sense all, but:

Wouldn't it possible to (for instance) boot plymouth with the 2D nvidia driver and load the proprietary driver once boot is (nearly) completed (for machines with nvidia cards)? If this is possible it will probably result in at least one flicker, but still, you get a nice boot and 3D for your desktop.

I doesn't really bother me, in any case.. Plymouth woohoo :D

---

### Post by Simian Man on 2009-12-01
> **Paqman said:**
> Text? Bleugh! 

Xsplash is lovely, i'd hate to see it go. There's no way in hell i'd turn off Compiz to get a nicer splash screen though.

Plymouth has a vesa fall back which means you will still get a nice graphical boot no matter what graphics card and drivers you use.  It just isn't quite as crisp and clear as it is with KMS.

---

### Post by Paqman on 2009-12-01
> **Simian Man said:**
> Plymouth has a vesa fall back which means you will still get a nice graphical boot no matter what graphics card and drivers you use.  It just isn't quite as crisp and clear as it is with KMS.

So this is all a storm in a teacup? Business as usual round here then...

---

### Post by forrestcupp on 2009-12-01
> **NoaHall said:**
> Because they don't care about how Ubuntu wants to do things - Ubuntu doesn't earn them the money from Linux.

No, but if Fedora and many other large distros are using Plymouth, and they are, wouldn't that give them reason to hack something together?  I guarantee that there is a way around licensing issues, and I think there are enough Linux users that will eventually be using Plymouth to make it justifiable.

It's another hurdle that will be jumped in time.

---

### Post by K.Mandla on 2009-12-01
> **FuturePilot said:**
> In my eyes the credibility of that site is fading fast.
+1
> **Paqman said:**
> So this is all a storm in a teacup? Business as usual round here then...
Same here.

---

### Post by gnomeuser on 2009-12-01
> **Paqman said:**
> So this is all a storm in a teacup? Business as usual round here then...

Well the vesa fallback isn't flawless and finding a way to enable it reliably on setups that do not do kms is probably going to take some work. I suspect we could do some magic in jockey to set this when installing a proprietary driver to set the right parameters.

Even at that should vesa fail we fall back on an acsii backend - not as pretty but it will give you a progress bar.

Out of the box though it should work on the 3 major cards (intel, ati and nvidia).

---

### Post by phrostbyte on 2009-12-01
> **RiceMonster said:**
> Why didn't they just go with plymouth in the first place? I mean, they created Xsplash, even though plymouth was already there, and now they're going to dump it? Then again, the article doesn't offer any real source to show the decision was made.

Furthermore, plymouth is not bad. It just makes use of KMS, which is not available from proprietary drivers.

XSplash takes over when X.org loads. I don't think it will be replaced. 

Plymouth = splashscreen for the kernel
XSplash = splashscreen for X

It's worth noting Plymouth requires KMS for prettiness, and only FOSS drivers currently support KMS. There are KMS drivers for all three major card vendors though.

---

### Post by phrostbyte on 2009-12-01
> **Paqman said:**
> So this is all a storm in a teacup? Business as usual round here then...

Yes. Without KMS, there will be effectively no difference between plymouth and usplash. Usplash doesn't have some magical mode setting ability, it relies on VESA. Plymouth likewise has a VESA fallback, but you are limited on what you can do in VESA mode, as you are in usplash anyway.

---

### Post by JBAlaska on 2009-12-01
I'm used to seeing Plymouth with my Mandriva 2010 box, albeit in vesa mode as the Nouveau 2D drivers sux, it's no big deal, boot time is LONGER than Karmic. But it is much nicer looking than the butt ugly monochrome usplash. 

It has a swirly thingy throbber and the text "Hit esc to see boot text" or words to that effect.

---

### Post by Exodist on 2009-12-01
What has SuSE been using for the past 8 years? SuSE and now openSUSE has always had the best and most professional looking boot screens for every release.

---

### Post by gnomeuser on 2009-12-01
> **phrostbyte said:**
> XSplash takes over when X.org loads. I don't think it will be replaced. 

Plymouth = splashscreen for the kernel
XSplash = splashscreen for X

It's worth noting Plymouth requires KMS for prettiness, and only FOSS drivers currently support KMS. There are KMS drivers for all three major card vendors though.

xsplash will very likely die. Plymouth provides a smooth transition to gdm or the desktop session (similar to what moblin does).

---

### Post by t0p on 2009-12-02
> **Paqman said:**
> Text? Bleugh! 

Xsplash is lovely, i'd hate to see it go. There's no way in hell i'd turn off Compiz to get a nicer splash screen though.

I couldn't care less about splash screens.  And anyway the Karmic splash screen is about the worst I've seen on Ubuntu since Feisty.  Text is fine.

Maybe my memory is playing tricks on me: I seem to remember Breezy had the text instead of a splash screen.  We should go back to that.  Text For The Win!!

---

### Post by benmoran on 2009-12-02
That site always has interesting news, but a lot of it is biased. 

ATI users will also be able to use Plymouth, providing they are using the open source drivers. The open drivers support 3D (that means compiz) on most cards already, minus the very new ones. The open ATI drivers also support KMS, that means Plymouth. 

Only the Nvidia guys are left out. Thats what happens when Nvidia wants to play the driver game by their own rules, not Linux's rules. 

But anyway, who cares? It's just a few second boot screen. Most people these days use LCDs that don't really "flicker" the same way CRTs do.

---

### Post by phrostbyte on 2009-12-02
> **benmoran said:**
> That site always has interesting news, but a lot of it is biased. 

ATI users will also be able to use Plymouth, providing they are using the open source drivers. The open drivers support 3D (that means compiz) on most cards already, minus the very new ones. The open ATI drivers also support KMS, that means Plymouth. 

Only the Nvidia guys are left out. Thats what happens when Nvidia wants to play the driver game by their own rules, not Linux's rules. 

But anyway, who cares? It's just a few second boot screen. Most people these days use LCDs that don't really "flicker" the same way CRTs do.

Newer open source Nvidia drivers do support KMS, although they aren't as mature as the ATI/Intel ones. Intel develops their own FOSS drivers, and AMD provides specs and support. Nvidia does neither.

---

### Post by bekind2thenoob on 2009-12-02
On the Wiki:

[https://wiki.ubuntu.com/FoundationsTeam/LucidBootExperience]("https://wiki.ubuntu.com/FoundationsTeam/LucidBootExperience")

---

### Post by sudoer541 on 2009-12-02
How about if they forget about boot screens?
when I turn on my pc I want it to boot fast so how about if they dont include a boot screen? 
how about if the pc boots directly to the log in screen without showing the boot screen?

---

### Post by Tibuda on 2009-12-02
> **sudoer541 said:**
> How about if they forget about boot screens?
when I turn on my pc I want it to boot fast so how about if they dont include a boot screen? 
how about if the pc boots directly to the log in screen without showing the boot screen?

That would be nice, but I think they should reduce the boot time before removing the boot screen.

---

