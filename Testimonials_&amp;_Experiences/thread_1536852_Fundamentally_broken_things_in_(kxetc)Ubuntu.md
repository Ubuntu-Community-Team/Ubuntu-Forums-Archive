---
title: "Fundamentally broken things in (k/x/etc)Ubuntu"
date: 2010-07-22
forum: Testimonials &amp; Experiences
---

### Post by SergeiFranco on 2010-07-22
I have decided to compile a list of fundamentally broken things in Ubuntu (that have been broken in long term, and have a depressing outlook of never being fixed).
This is a semi-rant as it is based on personal experience that caused long frustrating hours of trying to get basic functionality out of the bloody thing.

My biggest gripe with ubuntu (and all other variants) is the state of Audio.

Something as basic as audio, that just works in Windows is completely broken in many cases under ubuntu.

Here are the examples (drawn from my personal experience):

No Mic Boost "tick box" anywhere (not in alsamix or gnome volume control or kde volume control, not even in the pavucontrol) on many laptops and desktops that I dealt with. Without Mic Boost most of headsets are useless. There are a lot of forum posts and bugs logged regarding this issue but no solution. While in Windows "it just works". Seriously how difficult it is to make simple feature like this to work???

No software/hardware mixing for Digital outputs by default. No volume control for digital out (IEC958). Since Jaunty my custom asound.conf stopped working. In my case Phonon took over and completely discarded all my softvol and dmix. I am forced to use pulseaudio, but that also has its drawbacks -> kmix (default KDE mixer) does not work with it, so I have to use pavucontrol (but it does not integrate with my desktop). This issue is with kUbuntu. Ubuntu is slightly better in terms of it using pulseaudio by default, but there is a reason why I use KDE and that is irrelevant story.

Another major issue is the monitor resolution:

Do we edit xorg.conf or we don't? There is a lot of confusion about it. It seems that there are no advanced options in gui to override the EDID, and it seems that xorg.conf is not being respected by xorg.

Another issue is dual/triple monitor setup.
In many cases the gui app to change resolution does not recognise the monitor setup properly, in other cases you need to edit xorg.conf to increase virtual size. In some cases you have to do xranrd manually to setup monitors purely because gui app is buggy. Refresh rates (if you have a special monitor, or you want to have both monitors at same rate so there is no tearing) are also pain to setup, as gui apps seem to be confused at what refresh rates are supported by monitor, and xorg.conf is being ignored by xorg (modelines).

State of printing is also pathetic.
CUPS is broken by default, at least network printing is. The biggest issue is the timeout problem on RAW printing. Every printer must be installed as LPD, otherwise it would not print. It has been broken since 8.04.
GUI apps to configure cups are somewhat lacking. They seem to hang and miss certain settings that require me to go through [http://localhost:631](http://localhost:631) page.


Please add your issues that have been persistent.
I am fairly certain there are issues with network manager being dumb, webcam setup etc (things I don't use and have no experience with).

BTW, for those who are willing to criticise me for not trying hard enough, I am Linux sysadmin by profession and I have been using Ubuntu since 6.06, I certainly was happy to have a custom xorg.conf and asound.conf that worked, but now that power is taken away and is replaced by gui tools that do not work.

---

### Post by bodhi.zazen on 2010-07-22
I took the liberty of moving your thread to T&E.

Sounds as if you are frustrated, I suggest you take a break. I skimmed your thread and with the experience I have, I could fix most if not all of your list within a few minutes on Ubuntu. If I had the same problem on Windows I could not, it is not as if the nvidia drivers (or printers or anything else) are flawless on Windows.

IMO it all comes down to what OS are you familiar with.

---

### Post by RJARRRPCGP on 2010-07-22
The monitor thing is pathetic! I cannot set my CRT higher than 85 Hz, because X thinks my monitor isn't better than a cheap CRT! 

I currently cannot use higher than 85 Hz with my Trinitron! 

WTF X.Org!

---

### Post by SergeiFranco on 2010-07-22
> **bodhi.zazen said:**
> I took the liberty of moving your thread to T&E.

Sounds as if you are frustrated, I suggest you take a break. I skimmed your thread and with the experience I have, I could fix most if not all of your list within a few minutes on Ubuntu. If I had the same problem on Windows I could not, it is not as if the nvidia drivers (or printers or anything else) are flawless on Windows.

IMO it all comes down to what OS are you familiar with.

How would you fix no Mic Boost option, if it is lacking from alsa entirely? Certainly you could dig through alsa source code and add it, compile and use your own alsa but it is not supposed to be Ubuntu way. Right now all laptops in our company that run Ubuntu are useless for skype. The mic is too quiet. Boot them in windows and it has Mic boost option that makes it loud and clear.

Certainly I also can fix many of those issues by various scripts and trawling through forums and bug reports. 

For example the only way I could make my dual screen setup work on my laptop is to have a script launch on x startup that invokes xranrd. The laptop buttons for dual screen control do not work.

I am not suggesting that windows is better platform. In my opinion in terms of flexibilty windows is worse. But they do get certain things right. While Ubuntu tends to ignore the most basic functionality of the hardware.

---

### Post by bodhi.zazen on 2010-07-23
> **SergeiFranco said:**
> How would you fix no Mic Boost option, if it is lacking from alsa entirely? Certainly you could dig through alsa source code and add it, compile and use your own alsa but it is not supposed to be Ubuntu way. Right now all laptops in our company that run Ubuntu are useless for skype. The mic is too quiet. Boot them in windows and it has Mic boost option that makes it loud and clear.

Certainly I also can fix many of those issues by various scripts and trawling through forums and bug reports. 

For example the only way I could make my dual screen setup work on my laptop is to have a script launch on x startup that invokes xranrd. The laptop buttons for dual screen control do not work.

I am not suggesting that windows is better platform. In my opinion in terms of flexibilty windows is worse. But they do get certain things right. While Ubuntu tends to ignore the most basic functionality of the hardware.

I would suggest you start a support thread or post a bug report on LP.

You are unlikely to get support on a thread titled "Fundamentally broken things in (k/x/etc)Ubuntu" with a wall to text.

As I said, I did not fully read your post as I lost interest.

With that said, I can configure and problem solve in Linux much easier then Windows.

Although it is rare that a program needs to be re-compiled in Linux to solve issues , at least it is possible as the source code is available. Can't do that with most Windows applications.

Operating systems are tools and if Windows is the best tool for the task at hand, use Windows. Nothing wrong with that decision.

No need to make a square peg fit through a round hole or bash one or another OS.

Best of luck to you.

---

### Post by rollin on 2010-07-23
> **bodhi.zazen said:**
> 

With that said, I can configure and problem solve in Linux much easier then Windows.


Amen to that! I feel like a passenger running Windows, it's an expensive journey with a drunk driver. You just know it's going to...

---

### Post by SergeiFranco on 2010-07-26
> **bodhi.zazen said:**
> I would suggest you start a support thread or post a bug report on LP.

You are unlikely to get support on a thread titled "Fundamentally broken things in (k/x/etc)Ubuntu" with a wall to text.



Hey I was making constructive criticism. I like Linux as much as you do. I use it every day. It does not mean I am blind to the flaws like linux zealots are.
I can't stand using windows to be honest.

As for filing bug report... here are the bug reports regarding specific issue I am facing:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220787](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220787)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/534384](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/534384)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/319233](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/319233)

Or just google search for "mic boost ubuntu". This issue is a show-stopper for some one who wants to skype for example. I don't really see a 5 min work around.

Anyway treat this thread as user experience feedback and not as "linux sux windows rules", because even if I would be given a windows copy for free I will not be using it.

---

### Post by Riffer on 2010-07-27
Go to Drop Down Menu >System>Preference>Sound, under the tab marked "Input" you can adjust your mic volume.

[http://ubuntuforums.org/showthread.php?t=1516071](http://ubuntuforums.org/showthread.php?t=1516071)
[http://kubuntuforums.net/forums/index.php?topic=3086138.0](http://kubuntuforums.net/forums/index.php?topic=3086138.0)

The second thread describes how to use "alsamixer" to change your sound.

There's tons of other stuff using "mic volume lucid" instead of "mic boost".  I would suggest "mic boost" is a Windows centric way of saying "mic volume".

---

### Post by Version Dependency on 2010-07-28
I've installed 10.04 on five or six computers now.  And on one of them, I had the "mic boost" problem.  The computer owner used Skype alot so it was something that had to be fixed.  I searched high and low on these forums for possible fixes trying dozen of different things over several days.  Finally, I just changed the sound card in that computer to a card that I knew worked well with 10.04. 

So I have to agree with the original poster that the audio support could be better.

---

