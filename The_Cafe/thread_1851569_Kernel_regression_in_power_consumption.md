---
title: "Kernel regression in power consumption"
date: 2011-09-28
forum: The Cafe
---

### Post by MonolithImmortal on 2011-09-28
Ubuntu 11.10 Power consumption up ~50% according to Phoronix.
[http://www.phoronix.com/scan.php?page=news_item&px=OTg5Mg](http://www.phoronix.com/scan.php?page=news_item&px=OTg5Mg)

Read. Comprehend. Discus.

---

### Post by el_koraco on 2011-09-28
What's to discuss? This has been on and off since .34, .35 or something, with variations to the theme. It's probably gonna get worse before it gets better.

---

### Post by KiwiNZ on 2011-09-28
> **el_koraco said:**
> What's to discuss? This has been on and off since .34, .35 or something, with variations to the theme. It's probably gonna get worse before it gets better.

Maybe not for you, but others especially heavy Laptop users will be interested.

---

### Post by el_koraco on 2011-09-28
> **KiwiNZ said:**
> Maybe not for you, but others especially heavy Laptop users will be interested.

I do have a laptop. The news is interesting, there's just not too much to discuss. Unless you count peepz saying that Canonical should put everything on hold until it settles stuff with the drivers (lol) as a discussion.

---

### Post by MonolithImmortal on 2011-09-28
Discussion point: Carry your power cord with you everywhere. Laptop users with newer Intel cpu's can count on getting maybe 3 hour battery life on a good day.

---

### Post by KiwiNZ on 2011-09-28
With the expanding sales of Laptops globally power consumption is an important factor for a large number of users. 

Power consumption up by 50% + is an important factor in OS selection and may well be a deal breaker.

---

### Post by MonolithImmortal on 2011-09-28
> **KiwiNZ said:**
> With the expanding sales of Laptops globally power consumption is an important factor for a large number of users. 

Power consumption up by 50% + is an important factor in OS selection and may well be a deal breaker.
^ This.

---

### Post by el_koraco on 2011-09-28
> **MonolithImmortal said:**
> Discussion point: Carry your power cord with you everywhere. Laptop users with newer Intel cpu's can count on getting maybe 3 hour battery life on a good day.

Do you think somebody will contradict this stuff or what? I mean, none of this comes a surprise, given that the kernel development has never really focused on power consumption. The only efforts have been made by the Zen/Liquorix kernel team and fewt with Jupiter, way off the main line. fewt especially has shown that you can do wonders with some lines of code, but it will probably take another six months, a year, maybe even too, until the main line kernel starts dealing with this. You don't need battery life on servers, do you.

---

### Post by MonolithImmortal on 2011-09-28
No I don't think someone will contradict that, but it may be news to quite a few people here. Anyway, it's relevant to Ubuntu, and just about everyone here for that matter. 

Speaking of Fewt and Jupiter, is Jupiter even available for Ubuntu?

---

### Post by KiwiNZ on 2011-09-28
> **el_koraco said:**
> Do you think somebody will contradict this stuff or what? I mean, none of this comes a surprise, given that the kernel development has never really focused on power consumption. The only efforts have been made by the Zen/Liquorix kernel team and fewt with Jupiter, way off the main line. fewt especially has shown that you can do wonders with some lines of code, but it will probably take another six months, a year, maybe even too, until the main line kernel starts dealing with this. You don't need battery life on servers, do you.

With Unity, it is arguable that Canonical see the future for it's "desktop" Distribution as being largely up taken by the mobile user. Therefore it is also arguable that Canonical should put some effort into resolving power consumption issues.

---

### Post by el_koraco on 2011-09-28
> **MonolithImmortal said:**
> 
Speaking of Fewt and Jupiter, is Jupiter even available for Ubuntu?

Yes, the webup8 guys have a ppa.

---

### Post by el_koraco on 2011-09-28
> **KiwiNZ said:**
> Therefore it is also arguable that Canonical should put some effort into resolving power consumption issues.

They should put a lot more work into the kernel and graphics drivers in general. "Desktop Linux" obviously needs a company to finance development on desktop (laptop, netbook, tablet, whateva) related issues like power consumption, heat and so on.

---

### Post by 3Miro on 2011-09-28
> **KiwiNZ said:**
> With Unity, it is arguable that Canonical see the future for it's "desktop" Distribution as being largely up taken by the mobile user. Therefore it is also arguable that Canonical should put some effort into resolving power consumption issues.

How much does Canonical work on the kernel? AFIK all of their efforts are in the graphical realm. Red Hat makes a lot of drivers, I don't think Canonical really has people to contribute to the kernel.

While I would like to see issue resolved, I am not sure if Canonical has the manpower to solve this particular issue.

---

### Post by ninjaaron on 2011-09-28
> **KiwiNZ said:**
> With Unity, it is arguable that Canonical see the future for it's "desktop" Distribution as being largely up taken by the mobile user[...]

Despite numerous and repeated claims to the contrary by anyone who actually works for the company.

But the point still stands, of course, that someone should do something about ******* power consumption issues in the kernel if they want Linux to be a viable OS for anything that isn't constanly plugged in.

---

### Post by Paqman on 2011-09-28
Power consumption is a big deal for data centres. I'm sure Intel, Red Hat, Google, etc are whipping their Linux kernel hackers into a frenzy over this. Unless the bug doesn't present on server hardware, I suppose...

---

### Post by cariboo on 2011-09-28
> **Paqman said:**
> Power consumption is a big deal for data centres. I'm sure Intel, Red Hat, Google, etc are whipping their Linux kernel hackers into a frenzy over this. Unless the bug doesn't present on server hardware, I suppose...

This problem only affects laptops/battery powered devices, a data center wouldn't worry about laptop battery usage.

---

### Post by Paqman on 2011-09-28
> **cariboo907 said:**
> This problem only affects laptops/battery powered devices

Ah. Well, I suspect we're stuffed then.

---

### Post by fuduntu on 2011-09-28
There is no such thing as a power "regression" in the kernel.  There was a patch to a bug found by RedHat related to how the kernel enables ASPM.  The bug caused a group of computers effected to crash when the BIOS reported that ASPM wasn't supported, but ASPM was enabled in hardware ([RHEL-681017]("https://bugzilla.redhat.com/show_bug.cgi?id=681017")).  The fix was too instruct ASPM to go to an off state if the BIOS reported it wasn't supported rather than leaving it default.  This fixed the instability issue causing systems to crash.

More information on the subject:

[http://lwn.net/Articles/449648/](http://lwn.net/Articles/449648/)
[http://lwn.net/Articles/449448/](http://lwn.net/Articles/449448/)

HOWEVER, forcing ASPM to turn off on systems that report that it us unsupported caused a slight loss in power savings.  It was a sacrifice necessary to prevent systems from crashing.

**IT WAS THE RIGHT THING TO DO.**

also

**IT IS NOT A REGRESSION.**

The reason that is is not a regression is that the kernel's exposed tuneable parameters for power management are not dynamic.  This means that when you boot up either with a power cord connected or on battery your kernel boots into the same state.

It is optimized for performance, and not power savings.

An example of this would be dirty_writeback_centisecs. This parameter specifies the time in 100ths of a second where pdflush wakes up and writes cached data out to disk.  By default it is set to 500 which is optimal for performance but sub optimal for battery life.  A much more sane value when on battery is 1500.  Unfortunately, the parameter does not change "automatically" when you unplug.

Other examples would be parameters like nmi_watchdog, sched_smt_power_savings, and snd_hda_intel/parameters/power_save.

This is why a tool like [Jupiter]("http://www.jupiterapplet.org") or [tuned]("https://fedorahosted.org/tuned/") comes in, these tools are designed to alter the state of the kernel to optimize the system for performance when plugged in, and battery life when unplugged.  In the case of Jupiter, not only do I change multiple kernel parameters, but I also change the power state of (supported) devices to shift them to power savings mode.

***snip***

I tried to explain to him why he was wrong, but **he ignores reason choosing instead to continue to poison Linux users into believing the sky is falling** when it isn't.

For those that do see a small loss in battery life and are willing to risk stability for a few extra minutes unplugged, there is a workaround.

Set 'pcie_aspm=force' on the kernel command line of grub.conf, reboot, and move on with life.

To see if you have a bad BIOS, look at /sys/module/pcie_aspm/parameters/policy.  If it says 'default', you probably unfortunately have a computer that is reporting that ASPM is unsupported.

If you have a laptop or netbook, and you want optimal battery life, install [Jupiter]("http://www.jupiterapplet.org") or [tuned]("https://fedorahosted.org/tuned/") and get on with your life.

The remaining complaints Michael blindly points at the kernel are most likely configuration problems in the Ubuntu distribution itself (Unity or other application maybe), in the Xorg video driver stack shipping with Ubuntu, or operator error.

No offense to Ubuntu intended, it just honestly isn't well optimized for portable computers.  Even the older netbook remixes were just a different GUI bolted onto a default install.  I should know, I spent a lot of my personal time [optimizing  it for Eee PCs](https://sourceforge.net/projects/eeepc-acpi-util/) which eventually led to my being invited to join the Eeebuntu project (now called [Aurora](http://www.auroraos.org)).

If you are looking at powertop and you are seeing crazy wakeups, look at what you have running and what you are doing.

**If you see things like applications (Chromium, Firefox, Thunderbird, Terminals, shell scripts, etc), congrats - you are doing it wrong.**

Every process, keystroke, mouse movement, etc causes a wakeup, some cause tens or hundreds of wakeups per second.  **If you want to test for wakeups, you need to close EVERYTHING** except the base desktop (**clean boot recommended**), open a terminal, unplug, and start powertop as root.

**Now .. walk away for ~15 minutes.**

Still seeing crazy wakeups?  Probably not.

**Michael would be far more helpful to the community if he would learn how to properly identify and test for these sorts of problems and report them through the proper channels.  He is more interested though in driving clicks to his website, and the best way to do that is through fear, uncertainty, and doubt**.

---

### Post by fuduntu on 2011-09-28
> **el_koraco said:**
> Yes, the webup8 guys have a ppa.

+ when they run into issues they can't resolve themselves, they contact me directly and I help if I can.  Since I don't use Ubuntu, I can't help with some issues, but I can and do help them with core Jupiter problems.

---

### Post by ninjaaron on 2011-09-28
Congratulations sir.  These posts have just won you the internet.

---

### Post by castrojo on 2011-09-28
Not 100% sure but I think it's this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)

---

### Post by fuduntu on 2011-09-28
> **castrojo said:**
> Not 100% sure but I think it's this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131)

Case in point.

```
  25.7% (155.8)   [i915] <interrupt>
  13.3% ( 80.3)D  chromium-browse
   5.7% ( 34.7)   [iwlagn] <interrupt>
   5.1% ( 31.2)   PS/2 keyboard/mouse/touchpad interrupt
   3.2% ( 19.6)   desktopcouch-se
   0.1% (  0.7)D  ntop
   1.2% (  7.3)D  thunderbird-bin
   1.7% ( 10.0)   gwibber-service
   1.6% (  9.9)   ubuntuone-syncd

```

- [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131/comments/1](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131/comments/1)

Not an idle system - 347 process and device interrupts per second.  That is not a bug, that is a system that is busy being used.

---

### Post by JDShu on 2011-09-28
> **fuduntu said:**
> There is no such thing as a power "regression" in the kernel.  There was a patch to a bug found by RedHat related to how the kernel enables ASPM.  The bug caused a group of computers effected to crash when the BIOS reported that ASPM wasn't supported, but ASPM was enabled in hardware ([RHEL-681017]("https://bugzilla.redhat.com/show_bug.cgi?id=681017")).  The fix was too instruct ASPM to go to an off state if the BIOS reported it wasn't supported rather than leaving it default.  This fixed the instability issue causing systems to crash.

More information on the subject:

[http://lwn.net/Articles/449648/](http://lwn.net/Articles/449648/)
[http://lwn.net/Articles/449448/](http://lwn.net/Articles/449448/)



+1

This is the most informative post on this board in months. Read it. Really.

---

### Post by fuduntu on 2011-09-28
> *snip*

Excuse me .. Who snipped my post, and WHY?

I'd appreciate it if you kept your fingers off of my posts.

---

### Post by KiwiNZ on 2011-09-28
> **fuduntu said:**
> Excuse me .. Who snipped my post, and WHY?

I'd appreciate it if you kept your fingers off of my posts.

This is a Moderated Forum.

From the Code of conduct.....

"you agree that forum staff have the right to remove, edit, move or close  any post, topic or thread at any time they see fit following the  guidelines outlined below.

[LIST]
[*]Attacks and derogatory terms of any kind are not welcome. This  includes references to other operating systems and the companies that  produce them.
[*]Flames are messages that personally attack or call any people  names or otherwise harass. These, along with any generally condescending  posts will be edited or removed at the moderators discretion."
[/LIST]

---

### Post by fuduntu on 2011-09-28
> **KiwiNZ said:**
> This is a Moderated Forum.

From the Code of conduct.....

"you agree that forum staff have the right to remove, edit, move or close  any post, topic or thread at any time they see fit following the  guidelines outlined below.

[LIST]
[*]Attacks and derogatory terms of any kind are not welcome. This  includes references to other operating systems and the companies that  produce them.
[*]Flames are messages that personally attack or call any people  names or otherwise harass. These, along with any generally condescending  posts will be edited or removed at the moderators discretion."
[/LIST]

ok, fair enough.

---

### Post by MonolithImmortal on 2011-09-29
> **fuduntu said:**
> There is no such thing as a power "regression" in the kernel.  There was a patch to a bug found by RedHat related to how the kernel enables ASPM.  The bug caused a group of computers effected to crash when the BIOS reported that ASPM wasn't supported, but ASPM was enabled in hardware ([RHEL-681017]("https://bugzilla.redhat.com/show_bug.cgi?id=681017")).  The fix was too instruct ASPM to go to an off state if the BIOS reported it wasn't supported rather than leaving it default.  This fixed the instability issue causing systems to crash.

More information on the subject:

[http://lwn.net/Articles/449648/](http://lwn.net/Articles/449648/)
[http://lwn.net/Articles/449448/](http://lwn.net/Articles/449448/)

HOWEVER, forcing ASPM to turn off on systems that report that it us unsupported caused a slight loss in power savings.  It was a sacrifice necessary to prevent systems from crashing.

**IT WAS THE RIGHT THING TO DO.**

also

**IT IS NOT A REGRESSION.**

The reason that is is not a regression is that the kernel's exposed tuneable parameters for power management are not dynamic.  This means that when you boot up either with a power cord connected or on battery your kernel boots into the same state.

It is optimized for performance, and not power savings.

An example of this would be dirty_writeback_centisecs. This parameter specifies the time in 100ths of a second where pdflush wakes up and writes cached data out to disk.  By default it is set to 500 which is optimal for performance but sub optimal for battery life.  A much more sane value when on battery is 1500.  Unfortunately, the parameter does not change "automatically" when you unplug.

Other examples would be parameters like nmi_watchdog, sched_smt_power_savings, and snd_hda_intel/parameters/power_save.

This is why a tool like [Jupiter]("http://www.jupiterapplet.org") or [tuned]("https://fedorahosted.org/tuned/") comes in, these tools are designed to alter the state of the kernel to optimize the system for performance when plugged in, and battery life when unplugged.  In the case of Jupiter, not only do I change multiple kernel parameters, but I also change the power state of (supported) devices to shift them to power savings mode.

***snip***

I tried to explain to him why he was wrong, but **he ignores reason choosing instead to continue to poison Linux users into believing the sky is falling** when it isn't.

For those that do see a small loss in battery life and are willing to risk stability for a few extra minutes unplugged, there is a workaround.

Set 'pcie_aspm=force' on the kernel command line of grub.conf, reboot, and move on with life.

To see if you have a bad BIOS, look at /sys/module/pcie_aspm/parameters/policy.  If it says 'default', you probably unfortunately have a computer that is reporting that ASPM is unsupported.

If you have a laptop or netbook, and you want optimal battery life, install [Jupiter]("http://www.jupiterapplet.org") or [tuned]("https://fedorahosted.org/tuned/") and get on with your life.

The remaining complaints Michael blindly points at the kernel are most likely configuration problems in the Ubuntu distribution itself (Unity or other application maybe), in the Xorg video driver stack shipping with Ubuntu, or operator error.

No offense to Ubuntu intended, it just honestly isn't well optimized for portable computers.  Even the older netbook remixes were just a different GUI bolted onto a default install.  I should know, I spent a lot of my personal time [optimizing  it for Eee PCs]("https://sourceforge.net/projects/eeepc-acpi-util/") which eventually led to my being invited to join the Eeebuntu project (now called [Aurora]("http://www.auroraos.org")).

If you are looking at powertop and you are seeing crazy wakeups, look at what you have running and what you are doing.

**If you see things like applications (Chromium, Firefox, Thunderbird, Terminals, shell scripts, etc), congrats - you are doing it wrong.**

Every process, keystroke, mouse movement, etc causes a wakeup, some cause tens or hundreds of wakeups per second.  **If you want to test for wakeups, you need to close EVERYTHING** except the base desktop (**clean boot recommended**), open a terminal, unplug, and start powertop as root.

**Now .. walk away for ~15 minutes.**

Still seeing crazy wakeups?  Probably not.

**Michael would be far more helpful to the community if he would learn how to properly identify and test for these sorts of problems and report them through the proper channels.  He is more interested though in driving clicks to his website, and the best way to do that is through fear, uncertainty, and doubt**.
Read. Comprehend. Repeat.

---

### Post by Thewhistlingwind on 2011-09-29
> **fuduntu said:**
> [Pure win.]

You sir, win this thread, the cafe, the board, the forum, the server, and the internet.

That was quite possibly one of the best posts I have ever read.

---

### Post by sffvba[e0rt on 2011-09-29
As a laptop user this is worrying: "Ubuntu 11.10 is using the Linux 3.0 kernel and not the Linux 3.1 kernel, which is drawing even more power."

Bad news and more to follow...


404

---

### Post by BrokenKingpin on 2011-09-29
This is disappointing to see. I found when I wen't from Xubuntu 10.04 to 11.04 on my laptop the battery life was worse... now it is going to be even worse than that? It is pretty bad when Windows 7 has better battery life than a relatively light Linux distro.

This is a pretty big deal. Hopefully the kernel team is working on the issue (and a fix to my touchpad driver lol).

---

### Post by fuduntu on 2011-09-29
> **BrokenKingpin said:**
> This is a pretty big deal. Hopefully the kernel team is working on the issue (and a fix to my touchpad driver lol).

WOW, are you serious?

---

### Post by KiwiNZ on 2011-09-29
I think I will buy a test Laptop to test this. It will be interesting to try different Distros and see if there is really anything to get ones under garments in a reef knot.

---

### Post by jerenept on 2011-09-29
> **KiwiNZ said:**
> I think I will buy a test Laptop to test this. It will be interesting to try different Distros and see if there is really anything to get ones under garments in a reef knot.

Huh, a reef knot? Takes me a couple tries to get one of those right.

---

### Post by makitso on 2011-10-02
> This problem only affects laptops/battery powered devices, a data center wouldn't worry about laptop battery usage.So, my thinking is that Canonical really is not interested in mobile devices.  And, perhaps the kernel folks aren't either.  Power, wifi, suspend, issues have been dogging Ubuntu/Kernel for several years now -- since I started using Linux in 2008.   

So, until these issues are addressed by SOMEONE forget tablets and the like.

Fuduntu,  very impressive post.  However, while all the things you say are true, are we expecting all laptop owners to do all these things to get a system that is usable -- and then "get on with their life"?  Yes, for those of us who like fixing things this work well.  But, Canonical is trying to drive Ubuntu toward mainstream.  To me, this means it should work out of the box.

> nstall [Jupiter]("http://www.jupiterapplet.org/") or [tuned]("https://fedorahosted.org/tuned/") and get on with your life. Jupiter looks promising from what I can see.  However, it does not appear to work on Ubuntu 11.10 and tuned is only a fedora tool.

---

### Post by thatguruguy on 2011-10-02
[Make Jupiter work on 11.10]("http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html")

---

### Post by del_diablo on 2011-10-02
> **thatguruguy said:**
> [Make Jupiter work on 11.10]("http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html")

I see a solution requirering a PPA, and I raise the question: Why is it not working out of the box, and why has Ubuntu not been patched to make sure it works?

---

### Post by michaelcarey95 on 2011-10-02
I'm probably frying my laptop battery by doing this, but I only use it for very short periods of time where it's impossible to use my power cord.  Otherwise, I keep it plugged in (with the battery hooked up).  The point of a portable computer wasn't meant to work 100% without wires, it was meant to move from place to place.  I can move from place to place, I just require an outlet.  :p

---

### Post by thatguruguy on 2011-10-02
> **del_diablo said:**
> I see a solution requirering a PPA, and I raise the question: Why is it not working out of the box, and why has Ubuntu not been patched to make sure it works?

Because it's not a project controlled by Canonical, maybe?

---

### Post by sffvba[e0rt on 2011-10-02
> **thatguruguy said:**
> Because it's not a project controlled by Canonical, maybe?

Good point.

I installed Jupiter on my laptop running Natty.  Seems a pretty decent application, will see in time if it makes a difference however.


404

---

### Post by AloofObserver on 2011-10-02
So my AMD powered laptop isn't likely to see worse power consumption? I currently get approximately 7 hours with 11.04 but around 8 hours with Windows 7. Anything worse than 7 hours and I will have to carry around a second battery... I'd rather not do that.

I wish that the kernel developers put more effort into optimizing the kernel power consumption. Unfortunately that is not where the funders want their money spent :(

---

### Post by del_diablo on 2011-10-02
> **thatguruguy said:**
> Because it's not a project controlled by Canonical, maybe?

Thought it was just another upstreamed project endorsed by the official repos of Ubuntu, which was left behinnd due the repos freezing over.
So if that is not the case, then well, its not that bad.

---

### Post by del_diablo on 2011-10-02
AloofObserver: The regression only affects "some" Intel models. Which is a lot of em and all new ones.
For AMD its only faulty BIOS from the producers side, and nothing more.
Be glad its not a Turion64 chip, because the majority of those chips did not come with power managment support due OEMs not caring.

---

### Post by makitso on 2011-10-02
thanks so much for the link to Jupiter install for 11.10.   By switching to power saving mode, my Thinkpad t60 is now much better behaved and uses about 14 watts (powertop).  I have  been running on battery for 1/2 hour and it still shows 3.23 hours 94%.

---

