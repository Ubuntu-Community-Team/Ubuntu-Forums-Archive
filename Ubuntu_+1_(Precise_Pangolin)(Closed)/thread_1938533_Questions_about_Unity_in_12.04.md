---
title: "Questions about Unity in 12.04"
date: 2012-03-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by MountainX on 2012-03-09
Will the ability to turn off the appmenu (global menu) be a GUI setting in 12.04? 

Can I turn off the appmenu and keep the HUD? 

Is there any loss of other Unity functionality when the appmenu is turned off? 

Are Java applications supported for the HUD? 

How long will it be (if ever) before Unity gets the same broad and deep degree of customization that KDE provides? (I'm simply requesting educated guesses.)

---

### Post by AlmightyMokona on 2012-03-09
Also stability and gnome options would be good questions to ask...

---

### Post by Elfy on 2012-03-10
> **pavi_elex said:**
> ...

In the development forum - looking at threads in there - which is where this should have been posted.

It's not people in dev forum who close threads either.

---

### Post by MountainX on 2012-03-10
> **forestpiskie said:**
> In the development forum - looking at threads in there - which is where this should have been posted.


OK, I'll post it over there.

---

### Post by Elfy on 2012-03-10
It is there now :)

---

### Post by grahammechanical on 2012-03-10
Read what the owner of Ubuntu says

[http://www.markshuttleworth.com/archives/1027](http://www.markshuttleworth.com/archives/1027)

What would be your educated guess? That Ubuntu is going to go backwards? Ubuntu employs one person to work full time on Kubuntu. That person will be reassigned after 12.04 is released. Does that suggest to you that Ubuntu is going to follow the KDE path?

The best thing about Linux is user customization. The worse thing about Linux is user customization. People break the OS and then blame the OS and then expect a simple fix.

It is my educated guess that in the future when people are buying Ubuntu PCs and laptops and netbooks and tablets and Android+Ubuntu phones - that all the user customization will be severely restricted. Either that or people will buy these things on condition that any modification of this sort will invalidate the guarantee. 

Regards.

---

### Post by MountainX on 2012-03-10
I just found out about the "HUD for KDE" project (properly called [AppMenu Runner]("http://www.afiestas.org/appmenu-runner-meet-the-kde-hud/comment-page-1/#comment-17657")) by Alex Fiestas.

[http://www.afiestas.org/appmenu-runner-meet-the-kde-hud/comment-page-1/#comment-17657](http://www.afiestas.org/appmenu-runner-meet-the-kde-hud/comment-page-1/#comment-17657)

Unity has some good ideas, but they are being implemented in un-ergonomic ways for users of large screens or multiple monitors. 

And the problem is the Unity lacks the customization features to allow the user of a large screen to fix this. I'm guessing that Unity will continue the Gnome trend of limited customization. 

But with things like HUD coming to KDE, I hope I'll have the best of these new features in KDE together with the customization options I love.

---

### Post by keithpeter on 2012-03-10
Hello All

HUD seems to use the text contained within the global menu app as the basis for the searches, so I imagine no global menu means no HUD at present. I'd love to be proved wrong.

> **grahammechanical said:**
> It is my educated guess that in the future when people are buying Ubuntu PCs and laptops and netbooks and tablets and Android+Ubuntu phones - that all the user customization will be severely restricted. 

Yup, I think that is what might happen if Canonical find a hardware partner.

I'll bet there will by a 'cyanogen' for Ubuntu pretty soon though :twisted:

@MountainX

> Desktop: can't get a working Linux install...

Why on Earth not? Desktops are usually *easier* than laptops. Is it some strange hardware?

---

### Post by MountainX on 2012-03-10
> **keithpeter said:**
> 
@MountainX


Why on Earth not? Desktops are usually *easier* than laptops. Is it some strange hardware?

I'm not sure yet. If you think you can help, here is the hardware:

[http://forums.opensuse.org/english/get-technical-help-here/applications/471417-dolphin-menu-become-unresponsive-dolphin-terminates-reboot-required-2.html#post2446024](http://forums.opensuse.org/english/get-technical-help-here/applications/471417-dolphin-menu-become-unresponsive-dolphin-terminates-reboot-required-2.html#post2446024)

[http://hardforum.com/showthread.php?p=1038349791#post1038349791](http://hardforum.com/showthread.php?p=1038349791#post1038349791)

My satisfaction with Linux has taken a big downward dive in the last year. All the desktop changes have introduced more limited/incomplete functionality together with more bugs. I feel like 2011 was the "Vista" year of Linux desktops. Hopefully 2012 will be better. I'm committed to Linux, but struggling to find a distro/desktop that can be my new long term home.

---

### Post by jbicha on 2012-03-10
> **MountainX said:**
> Will the ability to turn off the appmenu (global menu) be a GUI setting in 12.04? 

No, that would require a feature freeze exception and a user interface freeze exception. And it would require someone to write the code. It's still a goal for 12.10 though, and it's not very difficult to do even without a switch in System Settings.

> **MountainX said:**
> 
How long will it be (if ever) before Unity gets the same broad and deep  degree of customization that KDE provides? (I'm simply requesting  educated guesses.)

No, the design goals for GNOME & Ubuntu are to limit customization because too many configuration choices won't be as well tested and make the interface too confusing for most computer users. I believe this has been the case since Ubuntu started in 2004.

---

### Post by MountainX on 2012-03-10
> **jbicha said:**
> No, that would require a feature freeze exception and a user interface freeze exception. And it would require someone to write the code. It's still a goal for 12.10 though, and it's not very difficult to do even without a switch in System Settings.

@[jbicha]("http://ubuntuforums.org/member.php?u=898421") - thanks for the replies. Are you a developer?

Regarding the feature freeze for 12.04, the question I asked about is actually in the UI spec before the freeze. It just hasn't shown up in the product yet, as of 12.04 beta 1. See this link for the UI spec that contains a setting for making menus either global or window-local.

[https://docs.google.com/document/d/1ILTJDiDCd25Npt2AmgzF8aOnZZECxTfM0hvsbWT2BxA/edit?hl=en_GB&amp;pli=1](https://docs.google.com/document/d/1ILTJDiDCd25Npt2AmgzF8aOnZZECxTfM0hvsbWT2BxA/edit?hl=en_GB&amp;pli=1)

> **jbicha said:**
> 

No, the design goals for GNOME & Ubuntu are to limit customization because too many configuration choices won't be as well tested and make the interface too confusing for most computer users. I believe this has been the case since Ubuntu started in 2004.

I'm coming to realize that KDE suits me better for this reason. However, it is also nice to see that KDE is taking inspiration from the work Ubuntu has done on Unity. I especially like HUD, so seeing HUD coming to KDE is exciting.

---

### Post by jbicha on 2012-03-10
Yes, I'm a developer but there's quite a bit I don't know how to do (like adding that feature).

Yes, there are a lot of thing in that spec that won't make it into Ubuntu 12.04. The UI freeze means that the UI currently in Ubuntu can't be changed without approval (from the Release Team, Docs Team, & Translators), regardless of whether it's in a spec or not.

---

### Post by MountainX on 2012-03-10
@[jbicha]("http://ubuntuforums.org/member.php?u=898421") - thank you!!! I appreciate you taking the time to answer. I hope to learn enough to make some contributions in the future. I'm going to start by seeing if I can learn to compile the Linux kernel. (I'm going to do this for an Android kernel first.)

---

### Post by grahammechanical on 2012-03-10
There is this comment:

> Still rough edges to be sure, even in this 12.04 release (we are not  going to be able to land locally-integrated menus in time, given the  freeze dates and need for focus on bug fixes) but we will SRU key items  and of course continue to polish it in 12.10 onwards.

From here:

[http://www.markshuttleworth.com/archives/1027](http://www.markshuttleworth.com/archives/1027)

I am of the opinion that stuff like this is just a bit bolted on to stop the rush away from Ubuntu. After all, if others can take Ubuntu and add and take away to give back this and put back that, then Canonical can also do it. But I am not sure if this kind of stuff is not an off branch away from the main trunk.

Regards.

---

### Post by MountainX on 2012-03-10
> **grahammechanical said:**
> There is this comment:

From here:

[http://www.markshuttleworth.com/archives/1027](http://www.markshuttleworth.com/archives/1027)

I am of the opinion that stuff like this is just a bit bolted on to stop the rush away from Ubuntu. After all, if others can take Ubuntu and add and take away to give back this and put back that, then Canonical can also do it. But I am not sure if this kind of stuff is not an off branch away from the main trunk.

Regards.

Yeah, interesting. What does "we will SRU key items" mean? 

And, since Mark obviously recognizes the importance of "locally-integrated menus" for an LTS release, why couldn't a couple of the "500 amazing people at Canonical" have been assigned this task starting a few months ago? (I've seen seemingly less important projects receiving more attention over these last few months.)

Unity definitely started pushing me away from Ubuntu (so far just a slight push over to Kubuntu, but it got me looking around widely). But, as a user, I am seeing some good ideas coming out of Unity. As I said above, it is too bad that these good ideas are not implemented in an ergonomical and well-designed manner (according to UI design experts). 

One the one hand, I think it would not have been that much harder to just design it better from the start. However, it seems like Unity was initially designed for small screens and those compromises go very deep. I don't know if Unity will ever be as good on the large desktop as it could have been if the initial design had been committed to "first, doing no harm" to the core desktop experience.

Earlier today, when I saw Oxygen AppMenu and the KDE AppMenu Runner, it stuck me that this is a very nice implementation of the same ideas that works better on large screens and may work just as well on smaller screens. (I haven't used those products yet, so I don't know how well they actually work.)

I like the innovation Canonical is doing with Unity. I think it is good for Linux on the desktop (and phone, tablet, TV, etc.). I would like to have all that plus better ergonomics, better usability on large or multi-monitor setups, and the philosophy of customization that KDE offers. 

Since I can't have all that (it seems), the next best thing is seeing all this innovation inspire the rest of the Linux community. (I assume some of the foundational code is also available to other DE's as a framework or libs, etc.) Eventually, all the Linux desktop environments will benefit from this work, one way or another. Oxygen AppMenu and the KDE AppMenu Runner give me hope that the time lag will be minimal.

---

### Post by keithpeter on 2012-03-10
> **MountainX said:**
> I'm not sure yet. If you think you can help, here is the hardware:

[http://forums.opensuse.org/english/get-technical-help-here/applications/471417-dolphin-menu-become-unresponsive-dolphin-terminates-reboot-required-2.html#post2446024](http://forums.opensuse.org/english/get-technical-help-here/applications/471417-dolphin-menu-become-unresponsive-dolphin-terminates-reboot-required-2.html#post2446024)

Hello MountainX

Your implied definition of 'working' in that last thread is much more demanding than mine! 

It might be worth your time posting in the hardware sub-forum on Ubuntuforums with a **specific issue or list of issues** that you encountered when booting from (say) 11.10. Posting a hardware list might not elicit many replies because the chances of someone having exactly the same hardware are small.

I've learned in this thread that the UI freeze is a *definite* freeze, which means I can update my Unity 2d guides based on what we have in Precise now.

I'd love to know what Shuttleworth meant by 'we will SRU key items' as well. I thought it might mean pop a modified Unity into a later point release of 12.04, but apparently not from jbicha's replies.

---

### Post by larrypg on 2012-03-10
stable release update?

---

### Post by arpanaut on 2012-03-10
> **larrypg said:**
> stable release update?

April 26, 2012?

---

### Post by jbicha on 2012-03-10
The 500+ employees at Canonical don't all work on gnome-control-center. To get an idea of Canonical's major divisions, check out their [website]("http://www.canonical.com/about-canonical/overview") (& [upper management]("http://www.canonical.com/about-canonical/overview/management-team")). Some of the things worked on are OEM services (this is a huge piece since the community can't contribute much here, nor will it really be blogged about much), Bazaar, Launchpad, Ubuntu One, Landscape, Unity and support services for paying consumers and enterprises. And of course, not everyone at Canonical is a developer.

SRUs generally are for high-priority fixes, not user interface changes. (Of course, Firefox & Chromium get a pass since their releases are also security releases so it's important to have the latest stable versions.)

There will still be some limited UI changes the next few weeks, but they need to get approval first.

---

### Post by MountainX on 2012-03-11
> **jbicha said:**
> 
SRUs generally are for high-priority fixes, not user interface changes. (Of course, Firefox & Chromium get a pass since their releases are also security releases so it's important to have the latest stable versions.)

There will still be some limited UI changes the next few weeks, but they need to get approval first.

Thanks for the explanations. Now it makes sense.

---

