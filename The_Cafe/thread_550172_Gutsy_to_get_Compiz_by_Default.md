---
title: "Gutsy to get Compiz by Default"
date: 2007-09-13
forum: The Cafe
---

### Post by bonzodog on 2007-09-13
[http://arstechnica.com/journals/linux.ars/2007/09/12/ubuntu-technical-board-votes-on-compiz-for-ubuntu-7-10](http://arstechnica.com/journals/linux.ars/2007/09/12/ubuntu-technical-board-votes-on-compiz-for-ubuntu-7-10)

It looks like the Technical Board yesterday voted to install compiz by default on Gutsy.

Thoughts anyone?

---

### Post by wickstopher on 2007-09-13
So long as it isn't *turned on* in the default settings, I think it's great.  If they've managed to work out all the kinks and get it working properly (it's a little hairy in 7.04, in my experience, but I don't have the most up-to-date hardware), I definitely think they should include it in the base install.  I think that they should, however, keep Metacity/Kwin/XFCE as the default window managers in the various distributions.  I like having compiz on my machine to show off to friends, but for normal operation it's just a hair too much of a resource hog for my liking.

---

### Post by smartboyathome on 2007-09-13
Right now, they have it set to detect if your hardware can handle Compiz, and if so, it will start it.

---

### Post by 23meg on 2007-09-13
[QUOTE=wickstopher]So long as it isn't *turned on* in the default settings, I think it's great.[/QUOTE]

The decision was to turn it on as default on supported hardware.

---

### Post by wickstopher on 2007-09-13
I'd prefer an installation dialogue akin to this:

"Your hardware is able to run compiz fusion.  Would you like to enable it now, or try it out later?"

but that's just me.  i'm really curious to see how well-implemented it is with this release.  the whole "desktop-effects" in feisty was a bit shoddy, imo.  but, like i said before, maybe my machine just isn't meant to run compiz, so maybe it's just shoddy on my machine. ;)

---

### Post by devilmyarse on 2007-09-13
I definately hope it's not switched on by default! 

Have they thought about the certain incompatibilities with Sun's Java and Compiz? My system runs at 100% cpu with compiz and java. I don't know whether it's a problem with java or compiz. 

(FYI i installed both compiz and java from source as i know that java is sometimes lagging behind in synaptic a few versions and nothing has changed with the latest version of both software.)

---

### Post by 23meg on 2007-09-13
[QUOTE=wickstopher]I'd prefer an installation dialogue akin to this:

"Your hardware is able to run compiz fusion. Would you like to enable it now, or try it out later?"[/QUOTE]

That's not very Ubuntu'ish, since it assumes previous knowledge of the software, and adds a "Yes / No" question (and therefore clutters the installation process) against which a considerable portion of the intended audience won't find themselves in an assured position.

[QUOTE=bonzodog]Thoughts anyone?[/QUOTE]

The decision surprised me. I don't have a strong preference either way, but predicted that the TB would vote against inclusion.

---

### Post by FuturePilot on 2007-09-13
I don't care either way either. It's very easy to turn off anyway.

---

### Post by Swarms on 2007-09-13
It shouldn't prompt you if you want it or not, Ubuntu is about keeping it simple, and turning it on by default for pc's that can support me I like.

---

### Post by mips on 2007-09-13
> **23meg said:**
> The decision was to turn it on as default on supported hardware.

Well on my current Gutsy install you have to go to the system menu and enable it.

---

### Post by 23meg on 2007-09-13
The decision concerns the final release. Of course I'm not sure how current your current install is, and whether the decision has been applied to the recent daily builds.

---

### Post by LowSky on 2007-09-13
So is Compiz going to called a stable release?

---

### Post by Wiebelhaus on 2007-09-13
can't wait for this one! good job folks out there making decisions about our beloved OS.

---

### Post by bobbybobington on 2007-09-13
Flippin sweet. :guitar:

---

### Post by happysmileman on 2007-09-13
> **devilmyarse said:**
> 
(FYI i installed both compiz and java from source as i know that java is sometimes lagging behind in synaptic a few versions and nothing has changed with the latest version of both software.)

You can install Java from source now? I didn't know it was fully OSS yet

---

### Post by mech7 on 2007-09-13
will it come also with latest ATI drivers? so you dont have to run under XGL ?

---

### Post by prizrak on 2007-09-13
Somewhat a bad idea, I have Gutsy and the first install was really flaky with nVidia drivers. Restricted manager installed nvidia-glx as opposed to nvidia-glx-new which really didn't agree with my card at all. Also it defaults to direct rendering which gives me black windows and to turn it off is not nearly as easy as it used to be with Beryl. Now you have to go to the config file and edit it. I think it would be better if it asked on first boot whether you want it or not.

---

### Post by urukrama on 2007-09-13
> **bonzodog said:**
> It looks like the Technical Board yesterday voted to install compiz by default on Gutsy.

Thoughts anyone?

If that means it is installed (but not turned on) on hardware that doesn't work very well with Compiz, such as my computer, this will become one more reason for me to keep doing server installs and building up from there.

---

### Post by mips on 2007-09-13
> **mech7 said:**
> will it come also with latest ATI drivers? so you dont have to run under XGL ?

NO. Gutsy is already in feature freeze and the latest ATI drivers will not make it into gutsy. Read this somewhere today, just dont ask me where.

---

### Post by CyberAngel on 2007-09-13
Will it also be the default window manager for kubuntu?
Or only for ubuntu?

---

### Post by ThinkBuntu on 2007-09-13
Mac OS X has 3D effects enabled by default. I don't see the harm in making it default for Ubuntu, and as a matter of fact, I feel that it's about time. This will put some pressure on the Compiz developers to produce quality, efficient, stable software.

---

### Post by 23meg on 2007-09-13
[QUOTE=ThinkBuntu]Mac OS X has 3D effects enabled by default.[/QUOTE]

And hardware that's guaranteed to handle it. Not a good point of reference, at least technically.

---

### Post by p_quarles on 2007-09-13
I've only looked at Gutsy via the live CD, but from what I can tell, the default Compiz effects are very light. No desktop cube, no water effects or wobbly windows or anything. If it's able to correctly determine hardware compatibility, then it shouldn't cause many problems for people.

---

### Post by Spike-X on 2007-09-13
> **ThinkBuntu said:**
> This will put some pressure on the Compiz developers to produce quality, efficient, stable software.

From what I've read, this was the argument for including it in Gutsy.

---

### Post by p_quarles on 2007-09-13
I think the other part of the argument, too, is putting pressure on Xorg developers and graphics adapter vendors.

---

### Post by RAV TUX on 2007-09-13
> **bonzodog said:**
> [http://arstechnica.com/journals/linux.ars/2007/09/12/ubuntu-technical-board-votes-on-compiz-for-ubuntu-7-10](http://arstechnica.com/journals/linux.ars/2007/09/12/ubuntu-technical-board-votes-on-compiz-for-ubuntu-7-10)

It looks like the Technical Board yesterday voted to install compiz by default on Gutsy.

Thoughts anyone?
You can only spin the cube so many times or have your windows go down in flames until the novelty wears off.

This was a hit last year, now it's just old hat.

I'll stick with the 3d effects in Elive Gem with e17.

---

### Post by Stan_1936 on 2007-09-13
> **p_quarles said:**
> ...default Compiz effects are very light. No desktop cube, no water effects or wobbly windows or anything. ....

Oh dear word...no way is it that diluted!!!!  Ouch.:confused:

---

### Post by p_quarles on 2007-09-13
> **Stan_1936 said:**
> Oh dear word...no way is it that diluted!!!!  Ouch.:confused:
Well, you can still *enable* all those things, they're just not turned on automatically.

---

### Post by Stan_1936 on 2007-09-13
ok, that helps.  I like the idea of having it turned on automatically.  That way I'm not dissapointed over the course of a month or so...it's just going to happen in one go and done...decision made....yes or no, I will know right off the bat.

---

### Post by luca.b on 2007-09-14
What a bad idea, IMO. Although OSS and FOSS is always about scratching an itch, the compiz/beryl guys are essentially reinventing the wheel with regards to window management (not for 3D effects). 
Personally I think the project should cooperate into including compositing support in mature and stable window managers, like metacity or KWin.

---

### Post by misfitpierce on 2007-09-14
Yes it should auto see if you have hardware to support instant on. If not it wont run but once you set up for it to run you can turn it off/on as done so. Thats how it should end up.

---

### Post by tomplast on 2007-09-14
This makes me angry, after I had installed Ubuntu and enabled the 3D-drivers I had Compiz activated, I don't remember getting asked about it?

Freedom comes with a choice, Compiz doesn't :/. And I couldn't find anywhere to deactivate it afterwards either, I may have missed it, if so then please tell me.

---

### Post by frodon on 2007-09-14
For those who tested it on gutsy, does it play nice with game like enemy territory or counter strike source with wine ?
I mean if it decreases game performances, gamers will surely prefer metacity.

---

### Post by gotonpo on 2007-09-14
glad to be an xubuntu user.  I'm sure we'll still get compiz disabled by default.  xfce's native compositing works easier and better for me anyway, even on new hardware.. and it works fine w/ games!  I forget to turn it off when I play WoW all the time, and I never notice a performance hit (although I'm sure there is a slight one).

---

### Post by graabein on 2007-09-14
I for one am glad to see Compiz by default. I'm sure it's easy to turn off. Desktop effects are the talk of the town so I think it's a smart way to attract new users.

What I want to know are what effects/plugins are default? I love the cube and absolutely think it should be default. Multiple desktops are one of the first things Windows and smack users notice with GNU/Linux to my knowledge.

I haven't run Compiz in ages, since before the Beryl branch really. I heard Compiz runs fine on dual monitors now. That's cool. Hope it handles full screen programs (games) also even though I don't play em.

:popcorn:

---

### Post by CyberAngel on 2007-09-14
Does anyone know the following?

> **CyberAngel said:**
> Will it also be the default window manager for kubuntu?
Or only for ubuntu?

Thanks.

---

### Post by forrestcupp on 2007-09-14
You don't ever hear about people being mad that MacOSX has a lot of eye candy by default.  That would be silly.

For gaming, I have a couple of shortcuts in my panel to scripts that switches to Metacity or Compiz.

---

### Post by triptoe on 2007-09-14
I am glad it is being included by default for two reasons... bug testing.. the more people that use it the better it will progress... and because this release is called Gutsy. There had to be a reason ;) . It would simply be lame if it was gutsy and they didn't do anything gutsy technologically speaking.

---

### Post by Anthem on 2007-09-14
> **tomplast said:**
> This makes me angry, after I had installed Ubuntu and enabled the 3D-drivers I had Compiz activated, I don't remember getting asked about it?

**Freedom comes with a choice, Compiz doesn't** :/. And I couldn't find anywhere to deactivate it afterwards either, I may have missed it, if so then please tell me.
What a bizarre statement.  I think you're either misunderstanding the meaning of "freedom" or the meaning of "choice."  Regardless, you can easily disable or uninstall compiz.

By your logic, Ubuntu doesn't give you a choice of word processors, graphics programs, desktop environments, consoles, or browsers.  Sure, you can install or remove whatever you want later, but they're restricting your "choice" by choosing for you!  The horror!

Obviously, Ubuntu hates freedom.

---

