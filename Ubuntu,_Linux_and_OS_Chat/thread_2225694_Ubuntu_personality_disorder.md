---
title: "Ubuntu personality disorder"
date: 2014-05-22
forum: Ubuntu, Linux and OS Chat
---

### Post by Leslie Viljoen on 2014-05-22
Hi people


In the last two years or so I've had a computer that doesn't do wifi, and then it did, and now it does wifi for the most part, but often refuses after a resume. If I put the computer to sleep and also close the lid, it stays on and locks up. I then often put my computer straight into my bag where it roasts its chips.


Also, its multi-monitor support was bad, then it got better, now its pretty good except it no longer remembers my monitor layouts. Sound has been pretty good except when it goes all scratchy in a program and I have to restart the progam. It could be the program's fault.


My mobile broadband worked probably 80% of the time - the rest of the time it told me I had incompatible firmare and driver. Now it won't work at all (says "disabled") and I've lost the ability to edit connections (there's only "add a new connection").


I should tell you that I was on Ubuntu 12.04 (Gnome) then, seeking stability I switched to Debian and now I'm on Ubuntu 14.04 (Gnome). Yes, that would cause an inconsistent experience except that 14.04 has more problems than 12.04 and Debian just traded the problems for other problems. To my surprise and disappointment, Debian proved no more reliable than Ubuntu. I'm on a Dell Inspiron 7520 laptop.


I avoid Unity because it makes switching between many open programs difficult and because it makes my windows stick at the borders of my two monitors which makes me rage.


The current lack of mobile broadband is costing me about 2 hours' worth of work a day, since I can't work on the commute.


So now I have to resolve this. I can't possibly use a Windows computer (my development stack won't run on there) but I could use a Mac, and that would be rock solid, though with the constant irritation of no package manager. Freedom-wise I'd hate to use anything but (GNU!)Linux.


My beef is not with the fact that there are problems, but that there are regressions. I know Linux can't be tested on every platform all the time but surely Canonical collects thousands of "problem reports" a day. Also, there are stable and "proposed/unsupported" package sources. Doesn't that mean Canonical could automatically detect which packages are causing regressions on "proposed/unsupported" and prevent them from getting into stable? Why is stable so unstable?


Oh, WOOHOO, my broadband just started working now for no good reason!
Oh, no it didn't, it's just pretending to be online. I feel like I'm living with someone with a personality disorder.

Leslie


ADDENDUM: my current list of annoyances

Ubuntu+Gnome_annoyances_14.04


    These are subjective things I'd like to change in Ubuntu, some bugs, some regressions, some just irritations.




1 May
    Regressions
        Monitor positioning is no longer remembered
        Gnome terminal crashed more than twice on the first day so I stopped using it
            (its windows became unresponsive and clicking them selected windows behind them)
        Suspend is broken again, after working for more than a year on this laptop - 
            Sometimes it works, sometimes it won't suspend (just goes black but doesn't sleep),
            sometimes it won't resume, sometimes it tries to wake but just goes back to sleep
                        if I hit suspend and immediately close the lid, it often stays on and freezes up
        None of the proprietary AMD drivers work - but of course I don't blame Ubuntu for that 


    Same as 13.10
        Gnome shell loads and then is unresponsive for about a minute
        Text screens are always spewing garbage and accusations
            "cdc_acm 3-3:1.0: This device cannot do calls on its own. It is not a modem."


        Unity defaults to a rage-inducing snapping of windows at monitor borders
            Rage is the number one reason I use Gnome shell instead of Unity
            I also like Gnome's dynamic virtual desktops, "Mission Control" style window chooser and hidden-by-default dock


        Gnome shell still isn't sure whether I'm connected to networks or not
        Broadband connections are listed in top right menu but not network settings    before connecting
        There's no way to delete these connections
        If they have long names there's no way to tell them apart


    Don't know if regression or not
        Firefox and Thunderbird menus have disappeared without telling anyone how to access them
        Evolution is a disaster as usual:
            Adding my 600MB Gmail account opens a million network operation tabs that are too truncated to read. They then sit there for more than a day. If I want to read my latest mail, I have to wait for more than a day.
            There's no way to get a list of network operations I can actually read
            Some of them are called "unknown background operation" which is not comforting
            Trying to remove evolution (as I hope new users will do) by default tries to remove my entire desktop


    Awesomeness
        Terminator fixed a bug so now ctrl-c can be swapped with ctrl-shift-c, YAY!
        Ctrl-c/v should copy and paste by default in the terminal like it does in every other program
        Gnome shell improved the message bar and top right menus

---

### Post by cariboo on 2014-05-22
@Leslie Viljoen, you may want to rethink your title, as I almost closed the thread, because we aren't here to advise on those types of problems. 

It would probably help if you posted the make and model of the laptop, as well as the wireless chipset.

---

### Post by Leslie Viljoen on 2014-05-22
As I said: Dell Inspiron 7520 laptop. Network: Intel Corporation Centrino Wireless-N 2230.
But the point of my post is not that there are specific issues with a specific piece of hardware - it's that **Canonical should use their awesome crowd sourcing powers to prevent regressions reaching stable**. There's no reason we should continually take one step forward and two steps back!

---

### Post by Old_Grey_Wolf on 2014-05-22
The first post was so long and not direct about what the point was. I gave up reading it straight away.

---

### Post by Leslie Viljoen on 2014-05-22
I found it quite entertaining but I suppose I'm biased.

---

### Post by Old_Grey_Wolf on 2014-05-22
> **Leslie Viljoen said:**
> ...**Canonical should use their awesome crowd sourcing powers to prevent regressions reaching stable**. There's no reason we should continually take one step forward and two steps back!

Have you volunteered your time to do testing of pre-release versions? Crowed sourcing only works well if people participate.

---

### Post by Leslie Viljoen on 2014-05-22
I have indeed. And I have submitted many bugs over the years. I've tried (and sometimes succeeded) in fixing some. I spoke up when Ubuntu was bricking network cards. I once wrote a tool to try and detect regressions automatically by installing programs with desktop files and making sure they would still start.

It would be interesting to discover that not enough people are running on pre-release versions for Canonical to be able to detect regressions, if that were the case I would gladly jump in and submit bug reports for pre-releases.

Would a regression hold a package out of "stable" though?

---

### Post by Old_Grey_Wolf on 2014-05-22
> **Leslie Viljoen said:**
> ...Would a regression hold a package out of "stable" though?

From my experience, Ubuntu does not have the same concept of "stable" the way that Debian does. There is no release called Ubuntu Stable. Based on using it for 8 or 9 years, I think Ubuntu may include a package that some find to be unstable depending on the feedback. I know that it has been know to include packages that were beta versions.

---

### Post by tgalati4 on 2014-05-22
You have a specific Use Case and hardware.  Unfortunately, Ubuntu in it's default form does not work for you.  You might try other distros.  I use Linux Mint Mate because it works better on older hardware.  For your specific annoyances, you need to address each one and really work hard to fix them.  They are all fixable--it's a matter of patience.

Mac might work better for you, but I agree, working inside a walled garden is no fun.  There is a package manager, it's just not what you are used to.  You will shell out a lot of money for a Mac solution.  You will be upset when Apple drops your hardware support in 5 years.

---

### Post by BadMichael on 2014-05-22
For years, Centrino's Wi-Fi on my Dell Inspiron was flaky under both Windows and later Puppy Linux. That's probably why Intel quietly buried the Centrino brand. Why blame Ubuntu?

---

### Post by rrnbtter on 2014-05-23
Greetings,
@OP I agree with the tone and substance of your post. However, I use mostly dev editions so I don't really have a focus on what normal is supposed to be like:)

---

### Post by Leslie Viljoen on 2014-05-23
As I said, it's not the specific problems, it's the fact that they are **regressions**. Things that worked are broken. As a software developer I solve this problem by having a test suite that prevents regressions creeping into my stable code. As a distro I think Ubuntu could make use of their error reporter to achieve the same thing.

@Old_Grey_Wolf: that's true about Ubuntu not having a stable release. Unfortunately even Debian was no better - though I have no base to compare to so I can't say if Debian had any regressions. I wonder if there is any distro I could really rely on for daily work purposes. @tgalati4 I have tried Mint and it didn't pass my 10-minute test. That's where I install an OS and see if I encounter a bug in the 1st 10 minutes.

I've been using Linux as my primary OS for the last 12 years or so, I would not seriously use a closed OS unless I really was completely unable to work. My strategy this far has been to buy a second hard drive and install upgrades in parallel, then only completely move if there are no major regressions. This I did not do with the last upgrade because I had a 1TB drive and a second would be quite expensive.

Anyway, it's painful and I wish I could say there was a solution.

---

### Post by ventrical on 2014-05-23
@leslie

I have done some extensive experiements (with the help of grahamechanical) with the btrfs file system. It has tools which allow an end_user to restore a system back to it's previous state. I have found it works great for regressive and deprecating updates/upgrades. It is not all fail-proof but it works extremely well. I do not know it this is the tool for you but it certainly eliminates 'downtime' which usually sends me climbing the walls :) lol  

You may be interested in these links:

[http://ubuntuforums.org/showthread.php?t=2152656&highlight=btrfs](http://ubuntuforums.org/showthread.php?t=2152656&highlight=btrfs)

[http://ubuntuforums.org/showthread.php?t=2112829&highlight=btrfs](http://ubuntuforums.org/showthread.php?t=2112829&highlight=btrfs)

[http://ubuntuforums.org/showthread.php?t=2146447&highlight=btrfs](http://ubuntuforums.org/showthread.php?t=2146447&highlight=btrfs)

Regards

---

### Post by sudodus on 2014-05-23
> **Leslie Viljoen said:**
> As I said, it's not the specific problems, it's the fact that they are **regressions**. Things that worked are broken. As a software developer I solve this problem by having a test suite that prevents regressions creeping into my stable code. As a distro I think Ubuntu could make use of their error reporter to achieve the same thing.

...

I think it works like this: The hardware drivers are developed to manage new hardware as well as to keep working with the old hardware, but unfortunately some old hardware is dropped in that process.

The developers are seldom reading the Ubuntu Forums. One way to communicate with them is to take part in iso testing and bug reporting. I think the best time to make a version compatible with your hardware is during the test periods of alpha, beta and release candidate. You are welcome to the [testing tracker]("http://iso.qa.ubuntu.com/") and you can get an account at [Launchpad]("https://launchpad.net/") for bug reports.

---

### Post by jamapii on 2014-05-23
I have just installed 14.04 and seen erratic behaviour too. Ok, so I have moved the old home directory with some setup, installed a few apps, installed a theme, tried a new kernel, tried hibernate, had crashes.

I guess some of the problems mentioned are NOT distinct, but a symptom of an underlying problem/design feature that some booting/startup things do not work reliably.

I have seen

- as far as i remember, suspend used to work with my new kernel, but stopped working
- sometimes the keyboard layout switcher indicator applet (that shows "EN"/whatever) starts up, sometimes it doesn't. When it doesn't, i can try to start it from a terminal, and it shows an error that seems to be related to dbus permissions.
- Sometimes the theme, fonts, colors are applied correctly, sometimes not. As if the theme is not read from configuration files, but from a server that starts in parallel and may or may not have started in time. This may be a Gnome/gtk feature, as i have seen the theme be applied with a delay before. In Unity, it is sometimes not applied at all, or partially applied.
- Focus follows mouse has just stopped working in this session, and the options in Tweak tool GUI (which is hard to find) have magically changed to insane values.
- Once the Ubuntu search thingy started displaying certain letters as spaces (s, u and others). This was only until the next reboot.

The bottom line is, you boot multiple times, and it acts differently each time. (exhibits different failures) This happens more often with a non-default configuration. And to be clear, I can very well adapt to different behaviour, I just prefer a computer that works and is not restrictive or just plain broken.

----

However, some the problems are related to updates. This way, a system is never stable over time, but degrades. I think I will make more use of virtual machines and chroot environments in future. So one may say qemu is my favourite OS. The worst thing for me have been, indeed, mobile broadband USB devices. They didn't work in Linux (one had a driver and software with an old kernel and no way to put it on a new kernel). They cannot possibly work reliably in Windows, because they invariably come with a clumsy adware that is required to start it, which does everything with a long delay, fails every other time and degrades over time. All those who happily told me "it works in Windows" later told me "it stopped working", some install multiple versions of such connection software and don't know anymore what to use.

So i think, a mobile broadband stick should be connected to a virtual machine with USB pass through, and this VM has the sole purpose to be a router for broadband, and its image is backed up when it works. The OS on this should be Linux, even an old version will do.

---

### Post by black veils on 2014-05-24
a filesystem or setup with some sort of restore function would definitely be useful.

but also what i would do if i were you is:
--  try a different system like linux lite or maybe LXLE as they both add drivers for old/odd hardware, you may have better results.
--  only allow security updates, either by disabling the other repositories, or by setting up the unattended-upgrades method to handle things.
prevent updates for the kernel, xserver etc
--  or even get a more compatbile computer, as you are intent on staying with linux as long as you can work.

---

### Post by tgalati4 on 2014-05-24
The OP didn't follow his own advice.  Keep a working distro.  Try a new distro as dual-boot, so if you have problems you can simply go back to the working distro and save your 2-hours per day.  

Fortunately, for Canonical, the focus on a phone operating system and phone hardware will make the mobile experience better.  For the rest of us--not so much.

---

### Post by d-cosner on 2014-05-24
I can really understand the original post in this thread. For years I seemed to always see the regressions from one release to the next. These days I avoid most issues by running on older, proven hardware. My desktop for example is a Compaq Intel based system, (well, the main board anyway.). It has on-board Intel graphics, realtec on-board sound, etc and it works with any Linux distro.

My HP 665 laptop is fairly new but it is pretty simple in design. What I mean is there is nothing really cutting edge about it. The Laptop has ATI graphics because it is only running on an E1 chip, it does have 8 GB of DDR 3 RAM though. I use the open source graphics drivers and the laptop runs just fine.

Fortunately, most of the time, (not always though...), the open source drivers will catch up to hardware that has been around for a while. Bleeding edge hardware is always going to take some work on the users part until it has been around for a while. Vendors tend to drop support on older products to force you to upgrade, I do not ever see that changing...

My boys computer has an NVidea GT220 graphics card, the system will freeze up constantly using the open source drivers. Using the oldest proprietary drivers will keep the system running but I have to manually fix Plymouth to display and it is never really displayed the way it is meant to be. Either the open source drivers will have to improve for this hardware or eventually I will have to get another graphics card to keep their system running the way they need it too.

None of us can change hardware manufacturers attitudes. We all know there are under the table deals with certain software vendors and I suspect that will continue as well. There is planned obsolescence to force you to buy new components or completely replace your perfectly good computer, that is always going to happen too. 

The best advise I have for dealing with regressions and problematic hardware is to go with a stable rolling release like PCLinux OS or a LTS release like Ubuntu 14.04. Sure, you may have to manually work your way around the regressions for a while but once you have the problems solved you should be fine for a decent length of time. 

I have felt the pain of regressions many times to the point of returning to Windows! Unfortunately, I can not run Windows with a clear conscience. Do keep in mind though that with all of the game titles, Steam Box, etc coming to Linux almost daily, hardware drivers are going in the right direction for us for a change. 

I see regressions in proprietary operating systems too, so it's not just Linux suffering from this. My wife uses a Windows computer to play World Of Warcraft, even the Windows Update supplied certified drivers would not get her ATI 5775 graphics card working properly! The system would crash constantly! It took some trial and error playing with drivers to get her graphics to work reliably. The 5775 has been around for a long time now and I thought it would have been problem free under Windows.

I hope you can work your way through the issues!

---

### Post by help_me2 on 2014-05-24
If sounds like you really love linux. So why not get another computer that was built for linux? I've had no problems using Ubuntu on my Dell Latitude E5520. System76 sells pc's with Ubuntu preinstalled and will work perfectly. Why fight it?

---

### Post by LastDino on 2014-05-24
> **help_me2 said:**
> If sounds like you really love linux. So why not get another computer that was built for linux? I've had no problems using Ubuntu on my Dell Latitude E5520. System76 sells pc's with Ubuntu preinstalled and will work perfectly. Why fight it?

+1 to this, I've never had to run an extra mile to get my current hardware working with any Linux distro I've tried so far, so I might be standing on different ground of point of view then some here. But really, it serves well to do your research on hardware compatibility before you actually buy it. Another thing is, while it is true that Linux is life line to old machines, I don't think it is primary objective of Linux, and as time passes, you're bound for some frustration with incompatibility. I'm not even going to talk about hardware design to run specific OS's that's just.....well, against the logic of mine which assumes what my computer should be.

---

### Post by Leslie Viljoen on 2014-05-25
Thank-you for the tips everyone, there are some good ideas here. Yes, I should try and support the people that do actually support Linux, like System76. Usually my computer is bought by the company I'm working for without thorough research - and I guess the company ultimately suffers lack of productivity because of that. So generally I have this difficult combination:

1. Need for fairly new packages because I'm developing against them (newer versions of Postgres/Postgis for example)
2. Usually very new laptop hardware
3. Need for rock solid stability so I don't interrupt my work

Next time I'm in the market for a machine I'm going to push hard for one purpose-built for Linux.
Btrfs is an interesting idea I've never considered.

I'm still intrigued by the possibility of automated regression testing for Linux though - some automatic system that prevents unstable packages from polluting a stable release.

---

### Post by ventrical on 2014-05-27
> **Leslie Viljoen said:**
> 

I'm still intrigued by the possibility of automated regression testing for Linux though - some automatic system that prevents unstable packages from polluting a stable release.


 I recall getting into a discussion about this very thing over 2 years ago during another dev cycle and , eventually the stable release we now know as Precise Pangolin. We discussed, specifically, about the repositories of all the depends and other programs .. etc.  In a perfect world Ubuntu stable releases would run without corruption if we approach them with a walled garden mentality - but - today this is not the case in the busy ways of the internet and to test other programs and tools we have to open up the repos to non-Canonical supported software that may not always be maintained. So , I would propose that one could parse through the database and see what is maintained and updated by Canonical and then look at what the 'partners' are doing.

  Personally speaking I still have extremely stable installs on USB flash-drives from 2010 that still work long after the Lucid repositories were closed.  Also , one of the reasons that we have an aggressive QA section is , I believe , to deal with the very question you have raised.

  I do like your idea.. I just wonder though how huge of an undertaking it would be.

Regards..

---

