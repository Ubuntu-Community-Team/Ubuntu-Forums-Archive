---
title: "New unity default hide mode"
date: 2012-02-07
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mc4man on 2012-02-07
The new default for unity is now hide mode - never. The non ccsm/gconf options for hide-mode are now 'never & autohide' as now seen in System Settings > Appearance > behavior
Atm dodge* can only be set thru ccsm or gconf, soon to be gone

An upgrade will switch hide-mode to never & may cause windows to open under the launcher. If so switch to another mode & back if never is your preferred

The possible 'window under launcher' was likely fixed with the latest unity-5.2 update.

As of the next upgrade only never & autohide will be available - if one doesn't like it then modify the code, hope someone does so for you or that dodge is officially returned which is unlikely

---

### Post by LADmaticCA on 2012-02-07
Thanks. I was just coming to see if anyone else was experiencing this. Changing modes then resetting worked for me.

---

### Post by Baldrick_NZ on 2012-02-07
> **LADmaticCA said:**
> Thanks. I was just coming to see if anyone else was experiencing this. Chaning modes then resetting worked for me.

Can be changed back with MyUnity from USC too.

---

### Post by exploder on 2012-02-07
Thanks for the tip! Un-hiding the launcher is pretty rough with my touch-pad but when I set things back it resized the windows to accommodate the launcher. I'm happy!

---

### Post by williejones on 2012-02-07
> The new default for unity is now hide mode - never. The non ccsm/gconf  options for hide-mode are now 'never & autohide' as now seen in  System Settings > Appearance > behavior
I turned Auto-hide the Launcher off and it works for me.

---

### Post by williejones on 2012-02-07
> **williejones said:**
> I turned Auto-hide the Launcher off and it works for me.


Oops, replied too soon.  Now things are going under instead of auto-hiding.

---

### Post by williejones on 2012-02-07
Still playing around with auto-hide.  Clicking restore defaults behaviors  under System settings-appearance-behavior allows autohide to work temporially.  I am not sure what
corrupts the autohide after some time opening-moving different things.

---

### Post by williejones on 2012-02-07
I booted into a second install which was last updated yesterday.  The appearance was previously under user interface.  See screenshot.

---

### Post by rburkartjo on 2012-02-08
i used ubuntu tweak and under tweaks set the launcher to intellihide

---

### Post by exploder on 2012-02-08
Todays updates seen to have fixed up the launcher, it retains the setting when set to display now.

---

### Post by MacUntu on 2012-02-08
So, 'auto-hide by default' failed once again.

---

### Post by kansasnoob on 2012-02-08
I rather like the new behavior, but regardless Mark Shuttleworth himself got into the discussion on Ayatana:

> On 08/02/12 02:23, Evan Huus wrote:

> Previously the default was for it to dodge windows - now, it is
> automatically set to never hide. The Appearance->Behaviour settings
> allow configuring always-hide and never-hide, but do not allow
> configuring the old 'dodge windows' method.
>
> On the assumption that his is intentional (and not a brown-paper-bag
> bug), why? The non-techies who I've set up with Oneiric haven't had
> any trouble grasping the dodge-windows concept,

In fact, the dodge-windows approach tested very poorly. We thought it would work well, tried it, tested it, and have had to evolve from there based on evidence.

If users encounter the dodge by moving windows against the launcher, then it is fine. They see that the dodge happens *when* they push the launcher away, they discover they can move the window back and the launcher will reappear. So far so good.

Here's the problem. Most users don't discover the dodging by moving a window till it touches the launcher. They first encounter it when they maximise a window. So, they login to the desktop. Good. They start an app. Good. Then they maximise a window, and the launcher "disappears". To these users, the behaviour is deeply uncomfortable, random. And these are in fact the majority of users.

It also turns out that users who can work with dodging launchers can also work perfectly well with launchers which always hide when not used.

So, based on that, we made the following design choices:

    To start with the launcher always visible. This is the least surprising starting position. Nothing happens unless the user commands it.
    To expose an option of having the launcher hide, or be fixed.
    Not to offer a dodge option, because users who don't want it always there are perfectly capable of using it in plain hiding mode, and users who don't know what 'dodge' means don't have to spend time trying to parse it.

>  and it's really the
> only usable option on smaller screens such as netbooks (always-hide is
> too confusing when first logging in, and never-hide takes too much
> space).

We agree on both the facts, just not your conclusion :). Yes, always-hide is a poor starting point for new users. And yes, never-hide wastes space on small devices. But the current approach is clear at the start and accommodates efficient use of space for those who need it or prefer it.

> I haven't heard any discussion on this list about the issue, so I'm
> curious as to the reasoning. Would someone more familiar with the
> change please comment?

There you go :)

> P.S. For those with a technical bent, CCSM can be used to restore the
> old 'dodge windows' behaviour for now.

**[COLOR="Red"]That codepath will disappear[/COLOR]**, we'd prefer to keep the code lean. In this case we've experimented, learned, and concluded a better approach is available, there's no argument for maintaining code we don't expose to users further.

Mark


---

### Post by Pilot6 on 2012-02-08
Does this mean that 'Dodge Windows' will not be possible to switch on even using ccsm? That is really a stupid decision. This behaviour is very convenient. It may br true that it is not obvious for new users. But to disable it completely... it is a MS way of doing things.

---

### Post by prusswan on 2012-02-08
So this is why the windows are occluded, I actually thought there was something wrong with the windows that are unable to maximize while staying out of the launcher area

for a windows user, always-hide = autohide, never-hide = always on top, launcher = cheap imitation of windows 7 taskbar, is that correct?

---

### Post by mc4man on 2012-02-08
> **Pilot6 said:**
> Does this mean that 'Dodge Windows' will not be possible to switch on even using ccsm? That is really a stupid decision. This behaviour is very convenient. It may br true that it is not obvious for new users. But to disable it completely... it is a MS way of doing things.

From what was posted above that would appear so, there is no guarantee that any option currently available will remain an option or even available.
From the same MS last year - 
> so we will remove experimental settings when the experiment is
over and we have an answer. We will not keep code paths around just
because somebody likes that option

In the context that unity seems to more about the single current workspace then this change & upcoming culling don't matter that much

---

### Post by cariboo on 2012-02-08
Further down in the discussion, Mark said that ccsm would still be available in the repositories for those that want or need it, though from what I understand, there will not be any new development done on it, at least by Canonical.

---

### Post by keithpeter on 2012-02-08
Hello All

I'm using Unity and Gnome Shell for normal tasks at home to gain insight into the 'new' interfaces, and my customary tasks are relatively straight forward so my workflow is unlikely to be altered by changes like this.

However, this all seems a little improvised, minor but significant changes occuring now and again but with no ability to change the changes. HUD appeared as an extra affordance for power users, then pivoted into a core function.

Precise is an LTS release. Can we take it that after the interface freeze date there will be no further changes to the way Unity works for the entire Precise support cycle? That there will be a fixed baseline to write tutorials from and to provide training on while Precise is used?

---

### Post by mc4man on 2012-02-08
ccsm/gconf only reflect the plugins & the options within - 
this is a commit of possibly some interest 
[http://bazaar.launchpad.net/~unity-team/unity/trunk/revision/1933](http://bazaar.launchpad.net/~unity-team/unity/trunk/revision/1933)

(as in - they're getting out of dodge

---

### Post by xedi on 2012-02-08
I am confused about how the neu ubuntu launch behavior is supposed to work:

1. By default it was auto-hide off, which is terrible, since it never goes away. (will this be the default for 12.04? Strange choice IMO)
2. Reveal Left: It does not reveal when I just go to the left side, but I have to wiggle, or go really fast. Is that normal? It is better with higher sensitivites, but I still have to go in faster than I am used to even if I go all the way to the border.
3. Top Left. Isn't that the same as reveal left? No matter what I do, everything works as with reveal left, so I wonder what the difference is.

---

### Post by EgoGratis on 2012-02-08
If we where able to install CCSM and set preferred mode in previous releases then i guess now when system settings allows the user to change behavior we don't have a problem. But something else is bothering me much more.

> It also turns out that users who can work with dodging launchers can  also work perfectly well with launchers which always hide when not used.I guess i am not that user? I could never use Autohide. Autohide is like saying i can't think of a better way so i will do nothing? Who will use Autohide? Nobody? 

Dodge Windows is something it takes some time to get used to but it is the only way someone can convince me to not to use Never hide. And because Ubuntu with option Dodge Windows convinced me to try to use it i now use it all the time.

Don't cripple Unity Shell please Dodge Windows is one of the things that makes it unique and useful. Taking away Dodge Windows functionality is taking away option to use the whole screen for 99% of the users and Unity Shell would just become another Shell that does not work well if you want to use as much of the screen as possible. 

And personal note i just can't imagine i could not use Dodge Windows anymore. It's like flagship feature of Unity Shell and please keep it.

---

### Post by mc4man on 2012-02-08
> **xedi said:**
> I am confused about how the neu ubuntu launch behavior is supposed to work:

1. By default it was auto-hide off, which is terrible, since it never goes away. (will this be the default for 12.04? Strange choice IMO)
2. Reveal Left: It does not reveal when I just go to the left side, but I have to wiggle, or go really fast. Is that normal? It is better with higher sensitivites, but I still have to go in faster than I am used to even if I go all the way to the border.
3. Top Left. Isn't that the same as reveal left? No matter what I do, everything works as with reveal left, so I wonder what the difference is.

1st - the reveal is more based on go to edge, then push against than going against once with speed unless the pressure value is very low (sensitivity - high

It's also possible that any setting for 'reveal pressure' in System settings and gconf will be over-ridden by the same setting in ccsm. If so, (is here), & *you have ccsm installed *then open it > in the unity plugin > lower the value there to suit - screen

Atm there is no Top Corner **Only** > reveal that actually works

---

### Post by mc4man on 2012-02-08
> **EgoGratis said:**
> 
Don't cripple Unity Shell please Dodge Windows is one of the things that makes it unique and useful. Taking away Dodge Windows functionality is taking away option to use the whole screen for 99% of the users and Unity Shell would just become another Shell that does not work well if you want to use as much of the screen as possible. 

And personal note i just can't imagine i could not use Dodge Windows anymore. It's like flagship feature of Unity Shell and please keep it.
No one here can keep it alive & atm in the unity trunk it is gone.( at least appears so to me.
If so it actually may be fairly straightfoward to restore in source, at least for 12.04
(the next major upgrade to unity should prove informative as to it's fate in 12.04

While this bug is not about dodge being removed because **atm it hasn't been**, it might as well be, you may want to keep an eye on for a "Invalid" or "Won't Fix" in lieu of something positive

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/928719](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/928719)

---

### Post by xedi on 2012-02-08
> **mc4man said:**
> 1st - the reveal is more based on go to edge, then push against than going against once with speed unless the pressure value is very low (sensitivity - high

It's also possible that any setting for 'reveal pressure' in System settings and gconf will be over-ridden by the same setting in ccsm. If so, (is here), & *you have ccsm installed *then open it > in the unity plugin > lower the value there to suit - screen

Atm there is no Top Corner **Only** > reveal that actually works

Thanks a lot, now I get it, you need to keep pushing it. I am not sure whether that's something intuitive... it wasn't for me obviously.

---

### Post by keithpeter on 2012-02-08
> **xedi said:**
> Thanks a lot, now I get it, you need to keep pushing it. I am not sure whether that's something intuitive... it wasn't for me obviously.

I switched AutoHide ON and enabled the 'Left Side' reveal in the Appearance | Behaviour pane of the System Settings.

On my PC the default setting has too low a sensitivity, I had to push the slider well up to something like 70% to get acceptable unhiding when mousing to the left.

On the 24 inch monitor on this PC I'll probably leave Unity in the default always on mode. On a netbook, I'd want that space at the left.

I also now have three 'gestures' on the windows key if Autohide enabled;

[LIST=1]
[*]tap: invokes the Dash
[*]longer than tap but not very long press: brings up launcher
[*]long press brings up launcher with the numbers and that lovely shortcut overlay
[/LIST]

---

### Post by kyleabaker on 2012-02-08
> **xedi said:**
> Thanks a lot, now I get it, you need to keep pushing it. I am not sure whether that's something intuitive... it wasn't for me obviously.

This behavior is clearly not ready for prime-time. Mark makes the point that the Dodge option wasn't as intuitive/clear and here we are with a reveal implementation that I've seen several people clueless on and/or complain about.

The option to drop the Dodge feature doesn't bother me, but if we're losing features then I expect a more refined result with the features that remain.

As is now, Unity's side panel is no different (with the exception of poor implementation for revealing the hidden panel) from the Windows taskbar or Mac launcher, both of which also offer "always on/locked" as well as "auto-hide".

---

### Post by cryptotheslow on 2012-02-08
I liked the dodge behaviour - makes sense on a bigger or landscape screen where nothing is ever full screened. Nice to have the launcher just duck out of the way when I wanted its space. I'm lost as to what is not intuitive about that.

Anyway - given that is no more - I find myself left with auto-hide - which at the moment for me is performing (diplomatically) sub-optimally.

The hide works fine. But getting the damn thing to reappear is a lottery. 

Put an application all the way over to the left when the launcher is hiding and the fun begins. Mouse to left of screen - sometimes a grab appears to resize the application, sometimes nothing happens, sometimes the launcher pops out (even though I have reveal set to top-left corner and am in the middle of screen vertically).

When the launcher is in stubborn won't reveal mood it seems crashing the cursor at high speed into the left side works - sometimes not. Sometimes scooting up and down the left works - sometimes not.

I swear this was sent to try us :D

I proffer no solution (other than bring back dodge at least as an option). But I do feel better for venting :D

---

### Post by ELD on 2012-02-09
Anyone else seen the ports on Ubuntu for 12.04 remove the launcher hiding option?
 
Apparently we now will only get always hide or always show, for every step forward unity has a step backwards it seems. I don't want my launcher to always be invisible neither do i want it always taking up screenspace on my laptop...
 
Anyone else bugged by it?

---

### Post by sffvba[e0rt on 2012-02-09
I liked the dodge feature, but as long as the option isn't just always show (which was what I thought had happened initially) I am OK with it if the reasoning is that the dodge was too problematic (which it sounds like).


404

---

### Post by jerrylamos on 2012-02-09
I'm not a launcher fan but on this netbook on the latest 12.04 update launcher isn't there until I hover near the left margin, almost always because I'm trying to do something in the window and the launcher goes splat over what I wanted to see.  Now sometimes I do want the launcher and it shows up O.K.

Jerry

---

### Post by prusswan on 2012-02-09
This is not yet in the dist is it? I still see it on autohide now. Without dodge the only thing that makes sense is to auto-hide since otherwise it will always be blocking maximized windows, which is as annoying as I can imagine.

---

### Post by EgoGratis on 2012-02-09
1.) I could agree the default mode should be Never hide.
2.) I can't agree Dodge Windows will be removed!

Autohide can't compare to Dodge Windows in any way. How many Windows users do you see that use Autohide? None? Autohide is like saying i am not willing to do anything!

I could agree on one fact. Dodge Windows is harder to implement and maintain but compare it as the substitution to Autohide is just plain wrong.

I thought about this and for me two things are acceptable.

1.) Dodge Windows stays as the third option (stays forever).
2.) Dodge Windows gets removed but new third options is implementer IN THE SAME TIME.

The proposal is this. You have 3 options. One is Never hide, third is Always hide and the option in between is Newer hide + Hide only when one (or more) window(s) is maximized.

In this way you take all the complexity of Dodge Windows away because this mode would work just like Never hide but when you Maximize any widows the launcher hides it self. 

This is the flagship feature of Unit Shell on the Desktop isn't it? Global Menu + Dodge  Windows lets you use all the screen? 

This would not be hard to implement and maintain? "The fancy stuff that cause problems under certain condition" would be removed but Unity Shell could still be considered as the shell that manages desktop space better by default  then all the alternatives?

If Dodge Windows gets taken away and only Never hide and Autohide is left then i must say this is just plain WRONG. Then we just get another shell that any dock can beat and basically from user perspective only has one mode: Never hide.

---

### Post by EgoGratis on 2012-02-09
1.) I could agree the default mode should be Never hide.
2.) I can't agree Dodge Windows will be removed!

Autohide can't compare to Dodge Windows in any way. How many Windows  users do you see that use Autohide? None? Autohide is like saying i am  not willing to do anything!

I could agree on one fact. Dodge Windows is harder to implement and  maintain but compare it as the substitution to Autohide is just plain  wrong.

I thought about this and for me two things are acceptable.

1.) Dodge Windows stays as the third option (stays forever).
2.) Dodge Windows gets removed but new third options is implementer IN THE SAME TIME.

The proposal is this. You have 3 options. One is Never hide, third is  Always hide and the option in between is Newer hide + Hide only when one  (or more) window(s) is maximized.

In this way you take all the complexity of Dodge Windows away because  this mode would work just like Never hide but when you Maximize any  widows the launcher hides it self. 

This is the flagship feature of Unit Shell on the Desktop isn't it? Global Menu + Dodge Windows lets you use all the screen? 

This would not be hard to implement and maintain? "The fancy stuff that  cause problems under certain condition" would be removed but Unity Shell  could still be considered as the shell that manages desktop space  better by default  then all the alternatives?

If Dodge Windows gets taken away and only Never hide and Autohide is  left then i must say this is just plain WRONG. Then we just get another  shell that any dock can beat and basically from user perspective only  has one mode: Never hide.

---

### Post by dagroves on 2012-02-09
I think it is fine, but for those of us who still use crappy old square CRT monitors rather than the widescreen monitors, that will leave us practically no room on our screen.

---

### Post by EgoGratis on 2012-02-09
I don't care too much about things like when i move the window with my mouse if  launcher reacts to it and stuff like that. You can remove this at any  time and it wont make much difference to me and it can work like Never hide but there should be one options included then to Hide the launcher when application is Maximized!

I use Dodge Windows on all may screens. Small/Big/Wide... it does not make any difference. When i Maximize application(s) i want to be able to use the whole screen as i am now but when i don't work with Maximized application(s) i want to be able to use and see unity launcher as i am now. Why? Because it makes sense and because it works better this way than on any OS i have tried. Autohide could never work this way!

---

### Post by BigSilly on 2012-02-09
I'm a bit confused by this announcement. I was reading it earlier on OMG! Ubuntu!, and I must have read it three times and it still makes no sense to me.

So, the dodge windows thing is going, but the auto hide behaviour will still be intact. It's been removed because new users didn't like the bar disappearing without a clue of how to get it back. With this in mind, what difference will it make removing dodge windows? The auto hide behaviour still causes the bar to disappear when maximising an application. Dodge windows at least had a visual representation of what was happening (i.e the bar "bounced" out of the way of the window), whereas with auto hide the bar disappears completely with a whoosh.

Please, if I've got the wrong end of the stick let me know. :confused:

---

### Post by VMC on 2012-02-09
> **BigSilly said:**
> I'm a bit confused by this announcement. I was reading it earlier on OMG! Ubuntu!, and I must have read it three times and it still makes no sense to me.

So, the dodge windows thing is going, but the auto hide behaviour will still be intact. It's been removed because new users didn't like the bar disappearing without a clue of how to get it back. With this in mind, what difference will it make removing dodge windows? The auto hide behaviour still causes the bar to disappear when maximising an application. Dodge windows at least had a visual representation of what was happening (i.e the bar "bounced" out of the way of the window), whereas with auto hide the bar disappears completely with a whoosh.

Please, if I've got the wrong end of the stick let me know. :confused:

If you play around with "Appearance > Behavior > Reveal sensitivity", that may answer your questions.

Also Left side, Top left corner play a part.

---

### Post by mc4man on 2012-02-09
> **BigSilly said:**
> I'm a bit confused by this announcement. I was reading it earlier on OMG! Ubuntu!, and I must have read it three times and it still makes no sense to me.

So, the dodge windows thing is going, but the auto hide behaviour will still be intact. It's been removed because new users didn't like the bar disappearing without a clue of how to get it back. With this in mind, what difference will it make removing dodge windows? The auto hide behaviour ....

Because the default will be "never" so as far as Ubuntu's target audience there will be nothing to stress their apparently  disinterested brains about.

---

### Post by philinux on 2012-02-09
Mark Shuttleworth explains.

 [http://www.omgubuntu.co.uk/2012/02/mark-shuttleworth-explains-dodge-ditch-decision-in-precise/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/02/mark-shuttleworth-explains-dodge-ditch-decision-in-precise/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

And global menus might be optional.

 [http://www.techdrivein.com/2012/02/no-more-dodge-windows-in-unity-global.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+techdrivein+%28Tech+Drive-in%29](http://www.techdrivein.com/2012/02/no-more-dodge-windows-in-unity-global.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+techdrivein+%28Tech+Drive-in%29)

---

### Post by BigSilly on 2012-02-09
> **philinux said:**
> Mark Shuttleworth explains.

 [http://www.omgubuntu.co.uk/2012/02/mark-shuttleworth-explains-dodge-ditch-decision-in-precise/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/02/mark-shuttleworth-explains-dodge-ditch-decision-in-precise/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

As I say in my post, I'd read that but couldn't make sense of it! I need to have a play with Unity and the CCSM settings to understand what Mark is getting at. But as I see it, the launcher behaviour he wants to make better for new users is still there even when removing the dodge windows option.

---

### Post by philinux on 2012-02-09
> **BigSilly said:**
> As I say in my post, I'd read that but couldn't make sense of it! I need to have a play with Unity and the CCSM settings to understand what Mark is getting at. But as I see it, the launcher behaviour he wants to make better for new users is still there even when removing the dodge windows option.

Did you follow the blue link? [https://lists.launchpad.net/unity-design/msg07665.html](https://lists.launchpad.net/unity-design/msg07665.html)

---

### Post by EgoGratis on 2012-02-09
When i maximize window launcher should hide. When i don't have any window maximized then launcher should not be hidden.

Autohide and Never hide can't replace this and this option should be available and it does not have to be complex as current Dodge Windows solution it can only respect or be managed by simple fact: is at least one windows maximized or not and how hard would be to implement this option and maintain it?

---

### Post by philinux on 2012-02-09
> **EgoGratis said:**
> When i maximize window launcher should hide. When i don't have any window maximized then launcher should not be hidden.

Autohide and Never hide can't replace this and this option should be available and it does not have to be complex as current solution it can only respect or be managed by simple fact that one or more maximized windows exist and nothing else!

Quote from my previously posted link.

 Here's the problem. Most users don't discover the dodging by moving a window till it touches the launcher. They first encounter it when they maximise a window. So, they login to the desktop. Good. They start an app. Good. Then they maximise a window, and the launcher "disappears". To these users, the behaviour is deeply uncomfortable, random. And these are in fact the majority of users.

---

### Post by kaldor on 2012-02-09
Will anything be done about the appearance of the launcher merging with the panel? It looks awkward when something is maximized.

---

### Post by EgoGratis on 2012-02-09
Yes and this was forced upon all users for several releases? Why didn't nobody held our hands then? But what happened is some of the users got used to this and don't want to use anything else. Why? Because it works great and not Auto not Never hide can replace this!

And to say you must remove Dodge Windows now when default mode will be Never hide? What does this have to do with the users experiencing the first encounter then? Nothing!

The real reason Dodging Windows will be removed is there are bugs that would have to be fixed or are to hard to fix and it is easier to just remove it.

Because of that i proposed solution when Dodge Windows would be removed and replaced with simplified approach.

Launcher would only hide if at least one windows is maximized. In all other situations it would act exactly as Never hide does.

And Never hide would be default so first users would never have to think where the Launcher had went?

---

### Post by BigSilly on 2012-02-09
> **philinux said:**
> Did you follow the blue link? [https://lists.launchpad.net/unity-design/msg07665.html](https://lists.launchpad.net/unity-design/msg07665.html)

Yes I read that too. Thank you for the link though. :)

> **EgoGratis said:**
> When i maximize window launcher should hide. When i don't have any window maximized then launcher should not be hidden.

Autohide and Never hide can't replace this and this option should be available and it does not have to be complex as current Dodge Windows solution it can only respect or be managed by simple fact: is at least one windows maximized or not and how hard would be to implement this option and maintain it?

I have to agree. I understand what Mark is saying and the audience he is aiming for, but really, lopping out a useful and practical option is such a shame. It adds a great deal to Unity's tactile feel imho.

> **philinux said:**
> Quote from my previously posted link.

 Here's the problem. Most users don't discover the dodging by moving a window till it touches the launcher. They first encounter it when they maximise a window. So, they login to the desktop. Good. They start an app. Good. Then they maximise a window, and the launcher "disappears". To these users, the behaviour is deeply uncomfortable, random. And these are in fact the majority of users.

Again, I understand this now, but still feel its a shame to cut this out altogether. Since there's little I can do about it, I won't complain or moan about it. I imagine I'll be setting my 12.04 bar to auto hide, but it's not as useful overall an option for me personally.

---

### Post by EgoGratis on 2012-02-09
How much work would it take to create and maintain this third option. Launcher would only hide if at least one window is maximized and to have this third option in system settings?

If the answer is not a lot then please do it and leave this flagship feature of Unity Shell available for use and because Never hide will be default no new user with get confused just because third option in system settings exist.

---

### Post by philinux on 2012-02-09
> **EgoGratis said:**
> How much work would it take to create and maintain this third option. Launcher would only hide if at least one window is maximized and to have this third option in system settings?

If the answer is not a lot then please do it and leave this flagship feature of Unity Shell available for use and because Never hide will be default no new user with get confused just because third option in system settings exist.

You would need to talk to the unity team on freenode irc. Or the design team mailing list.

---

### Post by EgoGratis on 2012-02-09
I respect what is being said. I do see some problems with Dodge Windows and i do know that it would be hard to fix all of them. I do see problems for first time users with Dodge Windows by default. I understand everything is being said and i respect it and find these claims valid.

BUT there is another tiny bit that is important too and could be lost. The ability to have launcher visible when no window is maximized and to use the whole screen when at least one is maximized is something that Unity Shell provides by default and it's great and i will say it again flagship feature of Unity Shell!

All the complexity of current implementation can be taken away and nobody has to fix the bugs it has. I am more or less fine with that.

Simple launcher on/off switch that could be enabled in system settings and would act like Never hide + Hide launcher if at least one window on the screen is maximized. In all other situations it would act exactly the same as Never hide and i don't care too much if this in my opinion better mode or Never hide would be the default mode. I could try to pass these proposal to somebody that makes the decision but i think that at least somebody that reads this thread knows where to copy/paste this discussion way better then me? Thanks!

---

### Post by prusswan on 2012-02-09
> **philinux said:**
> Mark Shuttleworth explains.

 [http://www.omgubuntu.co.uk/2012/02/mark-shuttleworth-explains-dodge-ditch-decision-in-precise/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29](http://www.omgubuntu.co.uk/2012/02/mark-shuttleworth-explains-dodge-ditch-decision-in-precise/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28OMG%21+Ubuntu%21%29)

And global menus might be optional.

 [http://www.techdrivein.com/2012/02/no-more-dodge-windows-in-unity-global.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+techdrivein+%28Tech+Drive-in%29](http://www.techdrivein.com/2012/02/no-more-dodge-windows-in-unity-global.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+techdrivein+%28Tech+Drive-in%29)

he might be the first person in history who gets shot for a interface design decision..

---

### Post by SemiExpert on 2012-02-09
News:  [http://www.omgubuntu.co.uk/2012/02/mark-shuttleworth-explains-dodge-ditch-decision-in-precise/](http://www.omgubuntu.co.uk/2012/02/mark-shuttleworth-explains-dodge-ditch-decision-in-precise/)  Background explanation:  [http://askubuntu.com/questions/29553/how-can-i-configure-unity](http://askubuntu.com/questions/29553/how-can-i-configure-unity)  In recent months, I've actually come to accept Unity with 11.10, mostly because of how well the Dodge Windows effect manages screen real estate in the upper left hand corner of the screen.  I was surprised by this announcement.  Shocked.  Just when Unity seemed to be approaching a level of maturity, here's another about face, killing a feature that actually made the left handed Unity dock less intrusive.  Dodge Windows effect worked for me.  It represented an optimal solution.  It's gone.  At this rate, I don't think that Unity is the solution to Linux desktop fragmentation.

---

### Post by prusswan on 2012-02-09
there's always gnome classic and maybe gnome session, not too late to join the light side :D

---

### Post by cariboo on 2012-02-09
Merged three threads on the same subject.

---

### Post by cariboo on 2012-02-09
Personally the only thing I want to clutter up my desktop is open windows, I find having the launcher show all the time, or having dodge windows set distracting. I like the fact that the launcher only shows when I want it to, I feel the same way about global menus. Let me control when I want to see them.

---

### Post by SemiExpert on 2012-02-09
> **philinux said:**
>  
And global menus might be optional.

 [http://www.techdrivein.com/2012/02/no-more-dodge-windows-in-unity-global.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+techdrivein+%28Tech+Drive-in%29](http://www.techdrivein.com/2012/02/no-more-dodge-windows-in-unity-global.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+techdrivein+%28Tech+Drive-in%29)

 What was the primary objective of Unity to begin with?  In the current implementation, Unity maximizes screen real estate with the Dodge Windows Effect and Global Menus.  With one going away and the other falling from favor, I really question what remaining rationale there is for Unity?

---

### Post by cariboo on 2012-02-09
> **SemiExpert said:**
> What was the primary objective of Unity to begin with?  In the current implementation, Unity maximizes screen real estate with the Dodge Windows Effect and Global Menus.  With one going away and the other falling from favor, I really question what remaining rationale there is for Unity?

Unity came about, because the old 2 panel was no longer available in Gnome 3, and gnome-shell wasn't ready early enough to be included in 11.04

---

### Post by prusswan on 2012-02-09
> **cariboo907 said:**
> Unity came about, because the old 2 panel was no longer available in Gnome 3, and gnome-shell wasn't ready early enough to be included in 11.04

That's not what I heard, some were saying that Unity is a pet project to really define the character of Ubuntu as its very own interface. Gnome is just collateral damage

---

### Post by cariboo on 2012-02-09
> **prusswan said:**
> That's not what I heard, some were saying that Unity is a pet project to really define the character of Ubuntu as its very own interface. Gnome is just collateral damage

Citation please. Who are you going to beleive, some random web site, or someone who has actually used Unity since it was released pre-alpha in 10.10?

---

### Post by larrypg on 2012-02-09
Hello,

It took a while (of upgrading)  but I think the auto-hide feature is pretty much working like it used to.  I do not have a little 10 inch pad but I am using a 24 inch screen.  

I do not want the launcher to be visable at all times...if I move my mouse over to the left side of the screen I would like the launcher to appear.  With the latest it seems to do all that.  I can think of no reason with my screen size to want the launcher to sit there and not be able to hide. I can think of even less with a smaller screen.

Now if only my Unity desktop would not go crazy I would be most happy.

---

### Post by prusswan on 2012-02-10
> **cariboo907 said:**
> Citation please. Who are you going to beleive, some random web site, or someone who has actually used Unity since it was released pre-alpha in 10.10?

I believe what I see since the time Gnome2 is thrown under the bus and Unity is propped as the one and only choice no matter how ill executed it will turn out to be.

---

### Post by cariboo on 2012-02-10
> **prusswan said:**
> I believe what I see since the time Gnome2 is thrown under the bus and Unity is propped as the one and only choice no matter how ill executed it will turn out to be.

You may want to do some research, as gnome 2 is no longer developed, and there at least 4 other choices of desktop environments available. Unity is installed by default, but you don't have to stick with it, you can install the Lubuntu-desktop, Xubuntu-desktop, Kubuntu-desktop and Edubuntu desktop without having to do a re-install. Using a Linux distro is all about choice, the first choice you have to make is if you want to learn how to use a Linux distribution. It is entirely possible to us Ubuntu without having to learn anything, but you'll never get the full benefit by doing that.

My suggestion is to install it on real hardware, and spend at least a couple of months learning your way around, before making any decisions about what desktop environment is the best for you. Try as many different distributions as you have time for  as Ubuntu may not suit the way you do things.

If you do decide to stick with Ubuntu, get involved, report bugs, take part in IRC or the mailing lists, contribute back to the community by helping others solve their problems, or if you can write code, consider become a part of the bug squashing team.

Ubuntu is a meritocracy, you get recognized for want you do, not for what you say.

One last thing before I step off my soapbox, grow a thick skin if you intend on posting regularly in this sub-forum, you will be questioned on what you say here. This sub-forum isn't moderated as heavily as some of the others.

---

### Post by prusswan on 2012-02-10
> **cariboo907 said:**
> You may want to do some research, as gnome 2 is no longer developed, and there at least 4 other choices of desktop environments available. Unity is installed by default, but you don't have to stick with it, you can install the Lubuntu-desktop, Xubuntu-desktop, Kubuntu-desktop and Edubuntu desktop without having to do a re-install. Using a Linux distro is all about choice, the first choice you have to make is if you want to learn how to use a Linux distribution. It is entirely possible to us Ubuntu without having to learn anything, but you'll never get the full benefit by doing that.

My suggestion is to install it on real hardware, and spend at least a couple of months learning your way around, before making any decisions about what desktop environment is the best for you. Try as many different distributions as you have time for  as Ubuntu may not suit the way you do things.

If you do decide to stick with Ubuntu, get involved, report bugs, take part in IRC or the mailing lists, contribute back to the community by helping others solve their problems, or if you can write code, consider become a part of the bug squashing team.

Ubuntu is a meritocracy, you get recognized for want you do, not for what you say.

Isn't this proving my point about the purpose of Unity and having it installed by default? Trying to cast pre-Unity users as ignorant and unconstructive, and disguising unpaid testing of something they should never have to use as learning, is disingenuous. Try telling Windows users to "learn" Mac by designing Windows 8 to look exactly like a Mac. Why should they be forced to become guinea pigs to realize the narcissistic vision of one?

---

### Post by cariboo on 2012-02-10
> **prusswan said:**
> Isn't this proving my point about the purpose of Unity and having it installed by default? Trying to cast pre-Unity users as ignorant and unconstructive, and disguising unpaid testing of something they should never have to use as learning, is disingenuous. Try telling Windows users to "learn" Mac by designing Windows 8 to look exactly like a Mac. Why should they be forced to become guinea pigs to realize the narcissistic vision of one?

If that's the way you feel, why are you here?

---

### Post by prusswan on 2012-02-10
> **cariboo907 said:**
> If that's the way you feel, why are you here?

To witness as Unity fail badly enough for them to realize they should return to their roots. I don't actually have a problem with Ubuntu as long as Unity stays out of my way.

---

### Post by ventrical on 2012-02-10
> **cariboo907 said:**
> Citation please. Who are you going to beleive, some random web site, or someone who has actually used Unity since it was released pre-alpha in 10.10?


 Actually  it was Mark Shuttleworth who said .. "Unity is the driving force behind Ubuntu".

regards,,

---

### Post by keithpeter on 2012-02-10
> **prusswan said:**
> To witness as Unity fail badly enough for them to realize they should return to their roots. I don't actually have a problem with Ubuntu as long as Unity stays out of my way.

Hello prusswan and all

Linux is about choice, and other platforms don't offer that. The point being made above as I read it was that by choosing a GNU/Linux based OS you can try out many different GUIs and see which one fits you rather than take a one size fits all approach.

Canonical, the company behind Ubuntu, are developing a highly spiced and strongly flavoured dish. You may prefer to choose from a different menu and you can!

Canonical need to find an income stream, they can't burn through Mark Shuttleworth's capital forever, and the markets they are looking at appear to include devices such as TVs, possibly tablets and mobile appliances. There are lots of desktop solutions available, and, I personally think Unity is ok for my simple needs.

I don't think we really want Unity to fail as that will impact on Canonical's profitability.

---

### Post by exploder on 2012-02-10
With any panel you usually do give up a small amount of screen real estate and it does not bother me to keep the Unity panel displayed.  


Canonical does not want to miss the boat, like what happened with netbooks and I like how they are trying to come up with something original. I find Unity to be much more convenient to use on my notebook than that other OS that it came with. Unity is different and many people do not like change but change is what it takes to get into the mainstream.

With this release cycle I see a great deal of information right out in the open and much easier ways to express quality concerns. Every bit of information pertaining to this release is available right here in the development forum, there is a solid foundation for this release to be successful.

---

### Post by varunpr97 on 2012-02-10
guys if you already dont know the dodge feature will also be removed from ccsm.... i have already changed to xfce, xubuntu is absolutely fantastic. Alright unity and gnome 3 are still beng developed and i feel they will soon be gud in the future. Remember this is a LTS release and the ubuntu developers hav just 6 months to conme up with something new..... i  *personally* feel the gnome  developers and canonical devs are a bit crazy. There was absolutely no reason for changing something that was developed for 2 decades... I share the same view as Torvalds and gnome 3 n unity is nothing more than unholy mess. What gnome developers should have done was maintain gnome 2 for anothere 3 years unill thy get gnome 3 sorted out... xubuntu is awesomn... i advie people who  frustrated with gnome to give it a try. Unity and gnome needs time to develop Just wait for 5 years and you will soon be in love with it. Guys sorry for my spelling and grammer.... it does no help when you are texting from a cellphone

---

### Post by rg4w on 2012-02-10
> **philinux said:**
> And global menus might be optional.

 [http://www.techdrivein.com/2012/02/no-more-dodge-windows-in-unity-global.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+techdrivein+%28Tech+Drive-in%29](http://www.techdrivein.com/2012/02/no-more-dodge-windows-in-unity-global.html?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+techdrivein+%28Tech+Drive-in%29)
Global menus are less of a problem than concealing them until the user figures out that hovering over the top panel reveals them.

Will the menu concealment become optional in 12.04?  Or (with prayers and hopes!) set to false by default?

---

### Post by SemiExpert on 2012-02-10
> **cariboo907 said:**
> You may want to do some research, as gnome 2 is no longer developed.....

 Yes, I think that we all can accept that Gnome 2.x is dead.  To be honest, I was still using Gnome 2.32 in Ubuntu 11.04 and only switched to Unity in 11.10.  Why?  Gnome 2.32 had a few issues, while Unity had finally become unproblematic and impressively reliable in 11.10.  On older hardware that defaults to Unity 2D, the experience is very poor, which goes to show how much Dodge Windows Effect and other Compiz features improve the experience with Unity.    As previously stated, Unity seemed to finally be reaching a level of maturity and stability as a desktop.  It was working.  With this latest revelation, I've lost a lot of confidence in Unity.  I honestly can't see where it's headed.  Without Dodge Windows Effect and default Global Menus, what's the point of Unity?    At this point, will Unity ever have the same level of acceptance as the former Gnome 2.x desktop?  Before this latest abandonment, I actually was starting to feel there was hope for Unity.  Now I don't.  As much as I hate to admit it, I think that Ubuntu's developers would be well advised to abandon Unity in favor of......Cinnamon.  I hate to say it.  I don't especially like Mint, and I've found that Mint 12 is far buggier than Ubuntu 11.10.  But the lack of stability, flexibility and vision with Unity has become a major issue for the entire Linux community.  Desktop fragmentation is a major issue and while we can all argue whether Gnome 3.0 or Unity initiated the current round of fragmentation and controversy, neither has offered up a satisfactory solution.  I've finally lost confidence in Unity with the death of Dodge Windows Effect and the shift away from Global Windows.  I doubt that I'm alone.  Cinnamon.  Cinnamon.  [http://cinnamon.linuxmint.com/](http://cinnamon.linuxmint.com/)

---

### Post by Elfy on 2012-02-10
I think this has run it's course. Closed.

---

