---
title: "Is Ubuntu still the distro for me in the future"
date: 2009-07-11
forum: The Cafe
---

### Post by Wim Sturkenboom on 2009-07-11
I started playing with Warty Warthog in the early days of Ubuntu. I felt very comfortable with it (my previous Red Hat skills could still be applied).

When I bought a new PC, it became a dual boot (WinXP / Dapper Drake, now WinXP / Hardy Heron). Somewhere along the line I noticed that changing runlevels (init 3 or so) no longer took me to a text only interface. I also noticed something like upstart (an approach that I can understand).

Just reading in a thread here that the <ctrl><alt><backspace> functionality has been disabled in Jaunty Jackalope. Doing some research about the why revealed the biggest crap reason that I can imagine (users can press it by accident). Yeah, they can also push the reset button by accident.

I'm not against changes although I might have some difficulty to adapt, but I have two problems with all these changes:
1)
I will have difficulty to fix problems on my system as my knowledge no longer applies.
2)
I'm becoming very reluctant to help people here when it comes to setup and configuration as whatever I know might no longer apply so I put users on the wrong foot.

I'm still a very happy Ubuntu desktop user (spending about 98% of my time on my system in Ubuntu) as it has always worked on my hardware but I wonder if the next LTS is still for me?

Does anybody have similar sentiments? Or is it just me?

WimS

---

### Post by hansdown on 2009-07-11
Hi Wim Sturkenboom.

You can enable ctrl+alt+backspace in 9.04.

[http://lifehacker.com/5259425/re+enable-ctrl+alt+backspace-for-ubuntu-904](http://lifehacker.com/5259425/re+enable-ctrl+alt+backspace-for-ubuntu-904)

There have been a few changes, but most cli commands stay pretty much the same.

Skripka has a better way in the post below.

[http://reformedmusings.wordpress.com/2009/04/25/enabling-ctrl-alt-backspace-in-ubuntu-904-jaunty/](http://reformedmusings.wordpress.com/2009/04/25/enabling-ctrl-alt-backspace-in-ubuntu-904-jaunty/)

---

### Post by Skripka on 2009-07-11
FYI-

Zap was disabled by the new Xorg.  ANY distro that uses it, no longer has Zap be default.  It isn't that hard to renable anyway, you just have to add a serverflag to your xorg.conf.

---

### Post by Wharf Rat on 2009-07-11
> **hansdown said:**
> Hi Wim Sturkenboom.

You can enable ctrl+alt+backspace in 9.04.

[http://lifehacker.com/5259425/re+enable-ctrl+alt+backspace-for-ubuntu-904](http://lifehacker.com/5259425/re+enable-ctrl+alt+backspace-for-ubuntu-904)

There have been a few changes, but most cli commands stay pretty much the same.

Bless you my friend.  I need to re-engage this as from time to time my laptop will freeze and this gets me going without a powerdown.

---

### Post by nlinecomputers on 2009-07-11
How does one go about telling the powers that be that I would like in future versions of Ubuntu to have the CTRL-ALT-BACKSPACE functions enabled by default?

---

### Post by forrestcupp on 2009-07-11
Maybe they need to add an option in the installer.

But if they end up adding options for everything, you might as well install Arch.

---

### Post by _sAm_ on 2009-07-11
> **Wharf Rat said:**
> Bless you my friend.  I need to re-engage this as from time to time my laptop will freeze and this gets me going without a powerdown.

Or you could press right alt + printscreen +k to restart X.

---

### Post by koleoptero on 2009-07-11
> **_sAm_ said:**
> Or you could press right alt + printscreen +k to restart X.

Thank you! :D

---

### Post by Wim Sturkenboom on 2009-07-11
@hansdown
I'm aware that I can re-enable that but that was beside the point that I'm trying to make.

@Skripka
I was not aware that it's an xorg thing and not an Ubuntu thing; sorry Ubuntu ;)

@hansdown
CLI commands stay the same. Yes, that's true but that does not help if the functions of runlevels have changed. And yes, I know that there is some GDM stop thing.

@_sAm_
<right-alt><printscreen>k
Never knew that one. Thanks. As I'm not using Jaunty, I trust you that that still works (just tested it in Hardy and it does work there). The user can also press that by accident :D (although it must be a big accident :D )

@forrestcupp
Adding stuff to the installation menu has been mentioned a couple of times (if I remember correctly, I also suggested something like that long ago); it's usually not greeted with a warm welcome and I can accept that although I'm highly in favor of an advanced menu that let's you configure stuff and choose what you want to install (e.g. why install evolution if I want to use Thunderbird).

---

### Post by Pasdar on 2009-07-11
Let me see if I understand what you're saying... developments in Ubuntu are going too fast for you to keep up with it? You've never switched between Windows OS's have you? Maybe you should check the difference between Win98, Win 2k, WinXP, Win VISTA, and Win7 to get what I mean. In my opinion changes are coming along too slowly, I want it to go even faster.

The most important thing you need to remember is that no one is forcing you to upgrade to any version of anything. Some people, till this day, especially many offices are still using Windows 95, others Windows 98... that's an OS of more than 10 years ago...

What use is there to life if you refuse to keep up with the technology of that time?

Why do you change from Ubuntu versions anyway? Why not just stay with the version you have now for the next 20 years if you don't want change?

---

### Post by FuturePilot on 2009-07-11
Just FYI the Ctrl+Alt+Backspace was an upstream decision, not an Ubuntu one, so it will most likely find its way into every distro.

---

### Post by nlinecomputers on 2009-07-11
> **Pasdar said:**
> Let me see if I understand what you're saying... developments in Ubuntu are going too fast for you to keep up with it? You've never switched between Windows OS's have you? Maybe you should check the difference between Win98, Win 2k, WinXP, Win VISTA, and Win7 to get what I mean. In my opinion changes are coming along too slowly, I want it to go even faster.

The most important thing you need to remember is that no one is forcing you to upgrade to any version of anything. Some people, till this day, especially many offices are still using Windows 95, others Windows 98... that's an OS of more than 10 years ago...

What use is there to life if you refuse to keep up with the technology of that time?

Why do you change from Ubuntu versions anyway? Why not just stay with the version you have now for the next 20 years if you don't want change?

I think you are reading more into this post then he said.  

1. There are legit reasons not to upgrade to every version of Ubuntu.  The powers that be recognize this which is why the LTS versions are provided.  The problem with cutting edge is that sometimes you get cut.   

2.  Not all change is considered good.  Vista changed things in the GUI for no reason that I can see other then to change them.

The logic behind changing the ZAP in xorg is questionable and there is plenty of reason to not like it and to question using a distro if that function continues to be disabled.

I use to be a Suse user but after Novel took over they so messed up Yast that I changed to ubuntu.

---

### Post by Wim Sturkenboom on 2009-07-11
> **Pasdar said:**
> Let me see if I understand what you're saying... developments in Ubuntu are going too fast for you to keep up with it? You've never switched between Windows OS's have you? Maybe you should check the difference between Win98, Win 2k, WinXP, Win VISTA, and Win7 to get what I mean. In my opinion changes are coming along too slowly, I want it to go even faster.

The changes mentioned in my opening post have not given me any benefits (it's subjective, I know) and only seem to make my life more difficult.

As changes can't come fast enough for you: just curious what you want to see changed and why?

> **Pasdar said:**
> 
The most important thing you need to remember is that **no one is forcing you to upgrade** to any version of anything. Some people, till this day, especially many offices are still using Windows 95, others Windows 98... that's an OS of more than 10 years ago...

What use is there to life if you refuse to keep up with the technology of that time?

Why do you change from Ubuntu versions anyway? Why not just stay with the version you have now for the next 20 years if you don't want change?
That's not true if one is slightly security conscious. So I'm forced in 2011 to leave Hardy Heron for what it is. By that time I have to see what my next OS will be (an upgrade or something completely different).

And in my opinion this has nothing to do with technology. If you don't agree with that, please give me some examples.

---

### Post by Pasdar on 2009-07-11
> **Wim Sturkenboom said:**
> The changes mentioned in my opening post have not given me any benefits (it's subjective, I know) and only seem to make my life more difficult.
Well in my case anything before Ubuntu 8.10 simply did not work on my laptop and Ubuntu 9.04 did, so in terms of compatibility they are definitely busy. However, you wouldn't know because it simply works on your PC/Laptop. Other than that, I don't know it's definitely faster than before. Have you checked the change log?

> As changes can't come fast enough for you: just curious what you want to see changed and why?
What I want is for the OS to keep up with its time. I want the OS to become so fast that when I click on something and I do not notice difference between the time I click and the time the window is open in front of my screen. I want optimal support for everything, maximum juice taken out of hardware (background and foreground) applications to be made to make everything even simpler, etc.

I'm actually disappointed at the things they said they would focus on with Ubuntu Karmic... its an improvement, but not the kind of improvement most people are waiting for.

There are wonderful ideas to be found at brainstrom ubuntu, some have so many votes... yet they are being ignored... i'm getting the feeling that site was nothing more than a sham... why does it even exist anyway if they just want to add things they want themselves. uhhgg.

> That's not true if one is slightly security conscious. So I'm forced in 2011 to leave Hardy Heron for what it is. By that time I have to see what my next OS will be (an upgrade or something completely different).

And in my opinion this has nothing to do with technology. If you don't agree with that, please give me some examples.
Why not just install Debian then? Or is it too difficult to install? :)

---

### Post by earthpigg on 2009-07-11
> What I want is for the OS to keep up with its time. I want the OS to become so fast that when I click on something and I do not notice difference between the time I click and the time the window is open in front of my screen. I want optimal support for everything, maximum juice taken out of hardware (background and foreground) applications to be made to make everything even simpler, etc.

get 32 gigs of ram and a UPS.

have your computer copy everything from your / partition into the first 29 gigs of ram (leaving 3 free to be used as conventional ram) at boot up. to work with space constraints, only use /home for settings and whatnot.... keep music, documents, etc on a traditional hard disk partition.

at shut down, have it copy everything from ram back onto your hard disk.

possible right now.

:P

---

### Post by CJ Master on 2009-07-11
> **Pasdar said:**
> 

Why not just install Debian then? Or is it too difficult to install? :)

He doesn't like some changes so he should switch to entirely different distro. I love your logic!

---

### Post by chucky chuckaluck on 2009-07-11
*sudo pkill X* will get you out, as well.

---

### Post by Wim Sturkenboom on 2009-07-12
> **Pasdar said:**
> Well in my case anything before Ubuntu 8.10 simply did not work on my laptop and Ubuntu 9.04 did, so in terms of compatibility they are definitely busy. However, you wouldn't know because it simply works on your PC/Laptop. Other than that, **I don't know it's definitely faster than before**. Have you checked the change log?
The upgrade from 6.06 to 8.04 made it slower. Boot time feels longer and Firefox is definitely slower (best noticed when you opt to save a picture (save link as); in 6.06 you got the save_as dialog immediately (within a second), in 8.04 it takes 1 or 2 seconds. The latter might not be an actual Ubuntu issue.

> **Pasdar said:**
> 
What I want is for the OS to keep up with its time. I want the OS to become so fast that when I click on something and I do not notice difference between the time I click and the time the window is open in front of my screen. I want optimal support for everything, maximum juice taken out of hardware (background and foreground) applications to be made to make everything even simpler, etc.
I'm waiting for the quantum computer to solve the speed issue :) And you can not support something if you don't have the specifications in the first place.

> **Pasdar said:**
> 
There are wonderful ideas to be found at brainstrom ubuntu, some have so many votes... yet they are being ignored... i'm getting the feeling that site was nothing more than a sham... why does it even exist anyway if they just want to add things they want themselves. uhhgg.
I might give it a look. Isn't that the one where the mono debate started? And where somebody suggested to remove the gimp?

> **Pasdar said:**
> 
Why not just install Debian then? Or is it too difficult to install? :)I freely admit that that might indeed be too difficult. I'm used to simple things like Slackware :guitar: So maybe Zenwalk will be the next one.

---

