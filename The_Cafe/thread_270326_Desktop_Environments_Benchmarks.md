---
title: "Desktop Environments Benchmarks"
date: 2006-10-03
forum: The Cafe
---

### Post by aysiu on 2006-10-03
As a continuation of [sbergman27's experiments in How to make kubuntu faster like xp](http://ubuntuforums.org/showthread.php?p=1565403#post1565403) that had these results on 96 MB of RAM using Edgy Beta 1: ```
XFCE Desktop Only: 7
XFCE Firefox     : 31
XFCE Epiphany    : 29

Gnome-Core Desktop Only: 19
Gnome-Core Firefox     : 44
Gnome-Core Epiphany    : 43

KDE-Core Desktop Only  : 9
KDE-Core Konqueror     : 15
KDE-Core Firefox       : 32
``` I thought I'd try a few tests on my 766 MHz 128 MB RAM old eMachines with Dapper. Here are the results: ```
**xfce4**
*Login: 19*
Firefox: 20
Konqueror: 34

**xubuntu-desktop**
Login: 21
*Firefox: 16*
Konqueror: 26

**gnome-core**
Login: 30
Firefox: 24
Konqueror: 41

**ubuntu-desktop**
Login: 34
Firefox: 19
Konqueror: 35

**kde-core**
Login: 50
Firefox: 29
*Konqueror: 11*

**kubuntu-desktop**
Login: 83
Firefox: 38
Konqueror: 13
``` To be honest, I'm not quite sure what to make of the results. Clearly XFCE and Xubuntu are faster than both Gnome and KDE... but everybody knew that already, and it's no surprise that Konqueror would load up more quickly in KDE than in Gnome or XFCE.

By the way, "login" was from the moment I hit **Enter** after typing in my password until the computer stopped making noise (which was usually a second or two after the wallpaper on the desktop had loaded).

"Firefox" was from the moment I clicked the Firefox icon to the moment the homepage had fully loaded.

"Konqueror" was also from the moment I clicked the icon to the moment the homepage had fully loaded.

The margin of error is plus or minus one second (I just used a regular clock with seconds--no fractions of a second).

---

### Post by Engnome on 2006-10-03
> **aysiu said:**
> 

By the way, "login" was from the moment I hit **Enter** after typing in my password until the computer stopped making noise (which was usually a second or two after the wallpaper on the desktop had loaded).


Maybe not the best indicator that the desktop is ready, just bc the hdd has stopped working doesn't mean the DE is ready.

But thx alot anyway, good test. Now I know that GNOME is faster than KDE even though there was a test sometime ago that said GNOME used more memory. (the tester was a KDE dev so I didn't really trust him)

---

### Post by ComplexNumber on 2006-10-03
> Now I know that GNOME is faster than KDEthats always been the case for me whatever distro i used. kde's area of worst performance must be in the login times. it just takes soooooooo long. kde in suse was the worst. with kde on suse, i used to go and make a coffee, because i knew that by the time i returned it would still be trying to login.

---

### Post by Kateikyoushi on 2006-10-03
I didn't try suse for 7 years but did it really become that bad ?
I will try to test ratposion vs gnome and xfce if get it to install in ubuntu, maybe ion3.

---

### Post by ComplexNumber on 2006-10-03
> I didn't try suse for 7 years but did it really become that bad ?
yes. i ws using suse 10.

---

### Post by maniacmusician on 2006-10-03
> **ComplexNumber said:**
> thats always been the case for me whatever distro i used. kde's area of worst performance must be in the login times. it just takes soooooooo long. kde in suse was the worst. with kde on suse, i used to go and make a coffee, because i knew that by the time i returned it would still be trying to login.
really? logging in takes less than 10 seconds for me with kubuntu. and thats because i have the composite manager enabled, but not composite itself so the composite manager spends 3 or 4 seconds crashing.

---

### Post by ComplexNumber on 2006-10-03
> **maniacmusician said:**
> really? logging in takes less than 10 seconds for me with kubuntu. and thats because i have the composite manager enabled, but not composite itself so the composite manager spends 3 or 4 seconds crashing.
quite a bit different from what aysiu and others get. that means, on your system, that gnome takes about 5/6 second to log in, and xfce takes even less.

---

### Post by aysiu on 2006-10-03
> **Engnome said:**
> Maybe not the best indicator that the desktop is ready, just bc the hdd has stopped working doesn't mean the DE is ready. So what is the best indication of desktop readiness for a desktop environment? All the icons and panels have loaded and the background has loaded and the hard drive stops buzzing around... is there something else to wait for? I'm not trying to be cheeky. I genuinely want to know, in case I ever do one of these for my faster computer.

By the way, to those excited about what this proves about Gnome v. KDE, this is one study. I happen to think this study is a good one (as I did it myself, and I'm relatively unbiased when it comes to these kinds of discussions), but it is **one** study. In fact, sbergman27's numbers seem to go straight against mine (that from 96 MB of RAM).

To those offended about how long it takes to log into KDE--yes, on my faster computer, it doesn't take nearly as long, but all of these numbers are for a five-year-old computer with a 766 MHz processor and 128 MB of RAM.

On my newer 2.1 GHz processor with 512 MB of RAM, the differences (if any) between Gnome and KDE are negligible, and both seem deathly slow in comparison to IceWM (what I'm using now).

---

### Post by Kateikyoushi on 2006-10-03
So if I assume Xfce and IceWm performs very close to each other on your faster pc I am not mistaken, am I ?

---

### Post by aysiu on 2006-10-03
I haven't done time studies on it yet, but my *feeling* is that IceWM is faster, yes.

---

### Post by maniacmusician on 2006-10-03
> **ComplexNumber said:**
> quite a bit different from what aysiu and others get. that means, on your system, that gnome takes about 5/6 second to log in, and xfce takes even less.
no, that's totally different. he's testing it on a computer with low specs. With a faster computer, the login time ratio does not stay proportionate, because there's no set conversion factor. What i mean is that if my computer's specs are x times as good, that doesnt mean that it's speed will increase by a factor of x. as aysiu said, the differences between kde and gnome on an upper level PC are barely noticable. XFCE is naturally faster. But not by too much once you start installing lots of programs which result in more services to initiate.

---

### Post by aysiu on 2006-10-03
I think people should recognize home-tested benchmarks for what they are--home-tested benchmarks. They're interesting and truthful, but they are not scientific studies to be extrapolated as global generalizations to all hardware.

The few things I did conclude from this study are:

1. On a low-spec computer, installing and uninstalling various desktop environments takes a *long* time.

2. If an application takes longer than 15 seconds to launch, you might as well just get up and get something to drink... unless you're stuck waiting by the computer timing how long it takes to load!

3. There are tweaks to get Gnome and KDE faster on low-spec computers, but I think you're probably just better off with XFCE... or a window manager like Fluxbox or IceWM.

4. If you are going to stick with KDE on a low-spec computer, use native KDE applications only.

---

### Post by bastiegast on 2006-10-03
About konqeror starting fast on KDE, from what i know its being preloaded. Can't gnome preload some apps that i use frequently? Would be nice i think. (Yes I know apt-get preload, but i mean automtically preloading).

Hmm, thinking of it, it might be a bit too windows like preloading apps that you didnt ask for ;)

---

### Post by awakatanka on 2006-10-03
Is the test done with a clean install on every setup? Thats the only good setup to test else it can contain things from other DE's that can load to.

---

### Post by aysiu on 2006-10-03
> **awakatanka said:**
> Is the test done with a clean install on every setup? Thats the only good setup to test else it can contain things from other DE's that can load to. I did a server install, installed one desktop environment, uninstalled it, installed another, uninstalled it, etc. So I did not do a clean reinstallation of the entire Ubuntu every time, but I did do a clean installation of the desktop environment. Does that make sense?

> **bastiegast said:**
> About konqeror starting fast on KDE, from what i know its being preloaded. Can't gnome preload some apps that i use frequently? Would be nice i think. (Yes I know apt-get preload, but i mean automtically preloading).

Hmm, thinking of it, it might be a bit too windows like preloading apps that you didnt ask for ;) Actually, if you do a fresh Kubuntu installation, I think you'll see that the preload option is unchecked in KControl. Can someone correct me if I'm wrong on this?

---

### Post by awakatanka on 2006-10-03
> **aysiu said:**
> I did a server install, installed one desktop environment, uninstalled it, installed another, uninstalled it, etc. So I did not do a clean reinstallation of the entire Ubuntu every time, but I did do a clean installation of the desktop environment. Does that make sense?

 
Could it be possible that there still be things left that will load with a other DE ?

If i uninstall something it mostly doesn't do a clean unstall there will always be leftovers.

So if there is a leftover from a KDE that can load with a GNOME (our other way around )the test can show wrong results.

To be sure and have clean test results you need to do a clean install i think.

The results of both tests contradict eachother. So its important that test are done the same way.

But maybe i'm seeing it wrong.

---

### Post by maagimies on 2006-10-03
> **aysiu said:**
> I did a server install, installed one desktop environment, uninstalled it, installed another, uninstalled it, etc. So I did not do a clean reinstallation of the entire Ubuntu every time, but I did do a clean installation of the desktop environment. Does that make sense?So, when you benchmarked kde, the .kde directory was not already created? I find that once it is, kde loads much faster than gnome, while gnome loads about the same speed as it did with the first run.

---

### Post by aysiu on 2006-10-03
No, you're not seeing it wrong--you're being scientific.

My study was not a scientific study. And I don't know everything about sbergman27's methodology.

The two are not controlled studies at all. For example, my memory limitation was physical (I had only 128 MB of RAM), but sbergman27's memory limitation was artificially imposed (there was actually more than 96 MB of RAM available).

It is possible that there could have been lingering applications, but I highly doubt it, and I don't see why one desktop environment would load applications from another desktop environment unless you changed the startup settings.

---

### Post by aysiu on 2006-10-03
> **maagimies said:**
> So, when you benchmarked kde, the .kde directory was not already created? I find that once it is, kde loads much faster than gnome, while gnome loads about the same speed as it did with the first run.
Well, I did them in this order:
xfce
xubuntu-desktop
gnome-core
ubuntu-desktop
kde-core
kubuntu-desktop

So if you're saying that the applications or desktop environment will load more quickly after the profile folder is created, that would indicate that Ubuntu and Kubuntu are even slower than my results indicated.

---

### Post by kripkenstein on 2006-10-03
> **aysiu said:**
>  I thought I'd try a few tests on my 766 MHz 128 MB RAM old eMachines with Dapper. Here are the results: ```
**xfce4**
*Login: 19*
Firefox: 20
Konqueror: 34

**xubuntu-desktop**
Login: 21
*Firefox: 16*
Konqueror: 26

**gnome-core**
Login: 30
Firefox: 24
Konqueror: 41

**ubuntu-desktop**
Login: 34
Firefox: 19
Konqueror: 35

**kde-core**
Login: 50
Firefox: 29
*Konqueror: 11*

**kubuntu-desktop**
Login: 83
Firefox: 38
Konqueror: 13
```

This is an interesting issue. I'm not sure I'm reading the results correctly, though. It seems that gnome-core **saved** 6MB by loading Firefox. Perhaps what happened is that a big chunk of memory was swapped out? If so, then the correct measure should be RAM usage+swap file usage, and not just RAM.

Also, Firefox seems to take **less** on ubuntu-desktop than gnome-core, which is odd. This may be the swapfile issue again.

---

### Post by maagimies on 2006-10-03
> **aysiu said:**
> Well, I did them in this order:
So if you're saying that the applications or desktop environment will load more quickly after the profile folder is created, that would indicate that Ubuntu and Kubuntu are even slower than my results indicated.Well, I guess they are, I have neither installed atm to test if I remembered correctly. I could be wrong of course.

---

### Post by aysiu on 2006-10-03
> **maagimies said:**
> Well, I guess they are, I have neither installed atm to test if I remembered correctly. I could be wrong of course.
Well, that would be an interesting follow-up study if someone wants to do it: does a desktop environment or its applications load faster if the profile folder already exists?

---

### Post by aysiu on 2006-10-03
Follow-up results...

**Part 1... The profile**
Well, I reran it with the profile and then with the profile deleted.

Original results for Kubuntu:
Login - 83
Firefox - 38
Konqueror - 13

Results when run again (same profile as last time):
Login - 70 (-13)
Firefox - 33 (-5)
Konqueror - 20 (+7)

Results after deleting the profile:
Login - 99 (+16)
Firefox - 41 (+3)
Konqueror - 18 (+5)

Honestly, I don't think it makes that much of a difference, especially since Konqueror seemed to load up slightly more quickly without the profile.

**Part 2... IceWM**
Login - 9
Firefox - 19
Konqueror - 23

So it seems IceWM has comparable speeds to Xubuntu and XFCE when launching applications, but its login time is significantly speedier.

**Part 3... Preload**
I checked the Kubuntu default settings for preloading Konqueror. The default is that the maximum number of preloaded instances is 1, but the box for preloading at startup is *un*checked.

I'm not sure what the point of specifying the maximum number of preloads is if you also default to not preloading...

---

### Post by aysiu on 2006-10-03
The first post was sort of an artificial experiment for the sake of *consistency*, but the truth is that you can get even KDE useful on a low-spec machine.

I tried my best to tweak *kde-core* to be useful:

1. Ran the **kpersonalizer** wizard and chose *fewer effects* with only the background wallpaper and image previews checked.

2. Went to **Settings > Configure Konqueror > Performance.** For *Minimize Memory Usage*, I selected *Never*. I also checked the box next to *Preload an instance after KDE startup*.

3. For **Fonts**, I unchecked *Use anti-aliasing for fonts*.

4. For **Launch Feedback**, I selected *No Busy Cursor* and unchecked *Enable taskbar notification*.

5. For **Splash Screen**, I selected *None*.

6. Under **Style** > **Toolbar**, I unchecked *Highlight buttons under mouse*.

7. For **Window Decorations**, I unchecked *Use shadowed text*, *Animate buttons*, and *Colored window border*.

8. I removed the pager from the panel (I never use it anyway) and under **Multiple Desktops**, I changed the *Number of desktops* to 1.

9. **Panels** > **Hiding**, unchecked *Show right panel-hiding button*

10. **Taskbar**, chose *Classic* for *Appearance* and unchecked *Sort alphabetically by application name*.

11. Under **Storage Media** > **Advanced**, I unchecked *Enable medium application autostart after mount*

What's the improvement for *kde-core* with optimization tweaks? Well, I uninstalled Firefox, so...

Login - 35 (-15)
Konqueror - 7 (-4)

The login is still longer than *gnome-core* and *ubuntu-desktop* and *xfce4* and *xubuntu-desktop*, but it's significantly shorter than *kde-core* without tweaks and *kubuntu-desktop*.

Also, even though we had to preload an instance of Konqueror, 7 seconds to start any application on my old clunker is pretty damn good.

It is possible to get KDE (and probably Gnome) usable on an old system.

Still, I would highly recommend XFCE or IceWM for older systems (128 MB of RAM or less).

---

### Post by Polygon on 2006-10-04
please label the numbers i am confused on what they mean. what are they, MB of ram? seconds? something else?

---

### Post by aysiu on 2006-10-04
Sorry, they're seconds.

The ones in parentheses are the difference between that and the previous trial.

So *Login - 35 (-15)* means the login took 35 seconds, and that was 15 seconds less than before (which was 50 seconds).

---

### Post by Elim on 2006-10-04
aysiu, what is the difference between ubuntu-desktop and gnome-core and kubuntu-desktop and kde-core?  Thanks.

---

### Post by Engnome on 2006-10-04
> **Elim said:**
> aysiu, what is the difference between ubuntu-desktop and gnome-core and kubuntu-desktop and kde-core?  Thanks.

Ubuntu desktop means all the stuff (read bloat) you get when you install normally. Gnome core means... pick a wild guess;)  no bloat whatsoever!

Have a look at: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) for instructions.

---

### Post by shining on 2006-11-13
> **Engnome said:**
> Ubuntu desktop means all the stuff (read bloat) you get when you install normally. Gnome core means... pick a wild guess;)  no bloat whatsoever!

Have a look at: [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems) for instructions.

Though, I would think the majority of dependencies are applications which are not automatically run, so that shouldn't make a difference, should it?
If only the services make a difference, isn't it possible to disable them in gnome and kde?

---

### Post by shining on 2006-11-13
> **aysiu said:**
> 
**Part 3... Preload**
I checked the Kubuntu default settings for preloading Konqueror. The default is that the maximum number of preloaded instances is 1, but the box for preloading at startup is *un*checked.

I'm not sure what the point of specifying the maximum number of preloads is if you also default to not preloading...

It doesn't preload them at startup, but say you launch konqueror a first time (it'll take several second), then when you close it, everything will stay in memory, so that next time you open konqueror, it'll come up faster.

Though, this should also be done on the kernel level, but maybe in a smaller extent, and so it isn't as efficient. I'm not sure. But it should still make a noticeable difference. Did you reboot between every test?

---

