---
title: "Why is Lubuntu faster than Ubuntu?"
date: 2014-12-12
forum: Ubuntu, Linux and OS Chat
---

### Post by kccv42 on 2014-12-12
Why is Lubuntu faster than Ubuntu? I seem better performance with lubuntu.

---

### Post by grahammechanical on 2014-12-12
Lubuntu is built on Ubuntu so it must share a lot of the Ubuntu code base, especially the Linux kernel and the Xserver. The difference is in the desktop environment. Ubuntu uses Gnome 3 DE and the Unity user interface. Lubuntu uses the Lightweight X11 Desktop Environment (LXDE). And that is what makes the difference.

LXDE uses less CPU and Memory resources than Gnome DE but that of itself would not explain why Lubuntu seems faster than Ubuntu. It must be to do with the need for, or the lack of the need for, 3D accelerated video rendering of the desktop environment.

> **Recommended configuration**


[LIST]
[*]The hardware requirements of LXDE are similiar to Windows 98 (Maybe a little bit higher). An old Pentium II CPU is enough.
[*]After X11 and LXDE are started, the total memory usage is about 45 MB on i386 machines. (This value may be higher or lower according to different system configurations.)
[*]Though LXDE itself doesn't require better hardware, other applications under X do need it. For example, Firefox and OpenOffice.org 2 are quite memory-hungry. So it's recommended that you have a RAM of more than 128 MB.
[/LIST]


[http://lxde.org/lxde](http://lxde.org/lxde)

No mention of graphic requirements

[http://jeffhoogland.blogspot.co.uk/2013/02/comparison-of-linux-desktops-opengl.html](http://jeffhoogland.blogspot.co.uk/2013/02/comparison-of-linux-desktops-opengl.html)

Read the comments to that blog post. I often wonder why anyone bothers.

Regards.

---

### Post by kccv42 on 2014-12-12
Does lubuntu not have 3d accerlerated graphics?

---

### Post by vasa1 on 2014-12-13
> **grahammechanical said:**
> ... It must be to do with the need for, or the lack of the need for, 3D accelerated video rendering of the desktop environment.

...
[http://jeffhoogland.blogspot.co.uk/2013/02/comparison-of-linux-desktops-opengl.html](http://jeffhoogland.blogspot.co.uk/2013/02/comparison-of-linux-desktops-opengl.html)

Read the comments to that blog post. I often wonder why anyone bothers.

Regards.
I don't know what you meant by "I often wonder why anyone bothers.", but I remember an Ubuntu "ad" from about a couple of years ago showing how fast a Ubuntu system booted up (with an SSD).

And here's a link to how the LXQt devs are trying to make things faster: [http://sourceforge.net/p/lxde/mailman/message/33088016/](http://sourceforge.net/p/lxde/mailman/message/33088016/)

---

### Post by kccv42 on 2014-12-13
I am confused on your last post.

---

### Post by Tar_Ni on 2014-12-13
It's pretty much all about the desktop environment.

What is Lubuntu?

*''Lubuntu is a flavor of Ubuntu based on the** Lightweight X11 Desktop  Environment (LXDE)**, as its default GUI. The goal is to provide a **very** ** lightweight distribution**, with all the advantages of the Ubuntu world  (repositories, support, etc.). Lubuntu is targeted at "normal" PC and  laptop **users running on low-spec hardware**. Such users may not know how  to use command line tools, and in most cases **they just don't have enough  resources for all the bells and whistles of the "full-featured"  mainstream distributions**.*''

Link: [http://lubuntu.net/](http://lubuntu.net/)

Ubuntu on ther other hand, uses the Unity desktop environment which is heavier but also a lot more polished and with some eye candies. LXDE or even Xfce is meant for older computers that just can't handle this kind of DE because the hardware wasn't meant for it. If you want to think in terms of Windows, as for ressources (RAM, CPU, GPU) in the Linux world Lubuntu is to Windows 98/XP what Ubuntu would be to Windows 7/8.

So that's why Lubuntu is faster, it's a lightweight OS which aims to be fast and low on ressources and therefore suitable for older/cheaper hardware.

---

### Post by kccv42 on 2014-12-13
ok. That makes sense. Thanks for clarifying.

Do you like lubuntu?

---

### Post by bapoumba on 2014-12-13
> **kccv42 said:**
> Do you like lubuntu?
I do, and It is the only flavor this poor laptop will run :)

---

### Post by sudodus on 2014-12-13
> **kccv42 said:**
> Do you like lubuntu?

I like the idea to keep old working computers running with modern and light-weight operating systems. I help testing Lubuntu (iso-testing of the next version). You can read more about the Lubuntu community at this link

[https://wiki.ubuntu.com/Lubuntu#Contribute_to_Lubuntu](https://wiki.ubuntu.com/Lubuntu#Contribute_to_Lubuntu)

---

### Post by Tar_Ni on 2014-12-13
> **kccv42 said:**
> Do you like lubuntu?

Absolutely. I am running the LTS release on my aging desktop computer with 1GB RAM, Pentium 4 CPU and it works very well for my needs. Without LXDE and Lubuntu this computer will be taking the dusts in somebody's attic. And ironically this is the only computer I am using at this point for my laptop is broken and I decided to sold it and purchase another one eventually. I am growing fond of Lubuntu because it's just so straight to the point, a 'no nonsens' OS that gives decent performance on hardware that would be considered useless by Microsoft's standard.

---

### Post by kccv42 on 2014-12-14
for a newer computer should it still run good?

---

### Post by sammiev on 2014-12-14
> **kccv42 said:**
> for a newer computer should it still run good?

Works great on i5 laptops.

---

### Post by kccv42 on 2014-12-14
Good to know.

---

### Post by DuckHook on 2014-12-15
Practically any time you simplify, simplify, simplify, you get faster, faster, faster. It's not quite as absolute as Newton's or Einstein's laws, but it is pretty accurate, probably similar to Moore's law.

As a guy who loves bringing ancient HW back to life, I love Lubuntu. It is running on most of my old laptops right now, including the one I take vacationing and couldn't give two hoots about were it lost or stolen, as it's probably worth no more than ten bucks on eBay. Yet, a machine that ancient runs tickety-boo on Lubuntu, but would have a massive coronary on Ubuntu. And Lubuntu is not just restricted to old machines. I bought a new computer for a relative and installed Lubuntu on it despite the fact that it had plenty of horsepower and could have easily handled Ubuntu. The reason? Lubuntu is simpler to use and was laid out very similarly to XP which she had gotten used to seeing: "start" button on lower left, task bar where she expected to see it, etc.

If you want to see the simpler=faster law really at work, then try running a non-GUI environment. In a stripped-to-the-bones command line environment, things happen sometimes in the blink of an eye that would take anywhere from two to ten times as long in a GUI environment. You need a true CLI environment, though; not just a CLI console that is running on top of a GUI. I have tried the following experiment: two absolutely identical laptops&#8213;one running Lubuntu, the other a pure CLI&#8213;the CLI was twice as fast transferring a massive file via NFS on Ethernet. 40% faster over WIFI. Five times faster retrieving 50 e-mails (Mutt vs Thunderbird). 22% faster executing a complex find (identical parameters). About 10% faster updating/upgrading (apt-get vs Software Update). Some comparisons are unavoidably apples to oranges, but browsing the web in the CLI (yes, it is possible) using *Links* makes *Firefox* feel like swimming in molasses.

If you look at resource usage while doing a task, you start to understand why: CLI apps use up a very small fraction of the memory that GUI apps must hog. They use less CPU cycles, less swapping, less everything. They also tend to be written more leanly, which often translates into further efficiency in resource usage. I'm sure something similar is at work between a big versus lean DE like Ubuntu vs Lubuntu. I would wager good money that PCManFM is faster than Nautilus, AbiWord faster than LibreOffice, etc.

---

### Post by vasa1 on 2014-12-15
> **DuckHook said:**
> ... I have tried the following experiment: two absolutely identical laptops&#8213;one running Lubuntu, the other a pure CLI ...
@DuckHook, I suspect there may not be much of a difference but have you compared a Lubuntu session with an Openbox session?

---

### Post by DuckHook on 2014-12-15
> **vasa1 said:**
> ...have you compared a Lubuntu session with an Openbox session?Have never actually timed GUI differences like I did CLI to Lubuntu. And the only reason I did that one was because Mutt seemed so much faster than Tbird that I got out the stopwatch to compare, and then one thing led to another. However, even without quantifying, the qualitative difference between Lubuntu and Ubuntu is so obvious that I don't need to stopwatch it to tell the difference. Between, Lubuntu and Openbox? I don't know that there would be much.

Problem is that a lot of the difference depends on your HW. If you are getting close to maxing out on RAM, that's when tight code and efficiency really show their worth. If Mutt is still operating within RAM whereas launching Tbird means swapping to HD, then this would account for a lot of the difference. If this theory is correct, then others may not see as much difference on modern HW.

---

### Post by vasa1 on 2014-12-15
> **DuckHook said:**
> ...
Problem is that a lot of the difference depends on your HW. If you are getting close to maxing out on RAM, that's when tight code and efficiency really show their worth. ...
That's logical. While I'm not in a position to compare machines or distros, I got the feeling that the Openbox box session starts faster than a Lubuntu session but after that there isn't much difference in performance.

---

### Post by kccv42 on 2014-12-15
What is Openbox box session?

---

### Post by DuckHook on 2014-12-16
> **kccv42 said:**
> What is Openbox box session?The desktop that we take for granted is actually built up of a succession of layers, each more bloated and sophisticated than the last. Think of it as something like an onion.

At the very heart of Lubuntu is the kernel. Surrounding it are all the utilities, basic commands, and basic apps that yield a command line environment. Surrounding that is the graphical engine called 'X' or XServer. Around that is the Window Manager called Openbox. Around that is the final layer: the Desktop Manager that is called LXDE (the word "Lubuntu" is derived from 'L'XDE + 'ubuntu'). It's this last layer that gives you the eye candy and functionality that most users think of as "Lubuntu", but it's not really necessary to getting work done. Some power users like *vasa1* sometimes prefer to get rid of the Desktop Manager layer altogether, free up all those resources, and just work at the Window Manager level. In Lubuntu's case, this means that you choose Openbox at login, and the system will load up to the Window Manager stage but won't load LXDE.

Openbox is actually enough to get any sort of work done. All apps are available in Openbox, and you can resize windows, minimize them, etc. But it's rather rough around the edges. For a much slicker implementation of a 'buntu-based Window Manager, you can download and try Bodhi Linux. It's not based on Openbox, but rather, the Enlightenment window manager. I must say that I find Bodhi's functionality to be absolutely wonderful. It's even lighter weight than Lubuntu because it doesn't have to devote any resources at all to a Desktop Environment. It's not often mentioned by the old hounds around these forums because it is not an official flavour and therefore is not supported by Canonical. It's more of a derivative than a flavour, but it is in active development, has a very committed and engaging community and is known and loved by far more people than just me.

I suspect that I've just further confused you. If so, just ignore Bodhi and stick with Lubuntu. I definitely do not recommend that you boot into Openbox until you are familiar enough with Linux that you can do without a DE.

---

### Post by vasa1 on 2014-12-16
> **DuckHook said:**
> ... I definitely do not recommend that you boot into Openbox until you are familiar enough with Linux that you can do without a DE.
The first time I logged into an Openbox session I panicked and rebooted. It was several months later that I dared to get into the water again, but much better prepared :)

I liked Bodhi's approach of not installing most of the applications that other distros do. Instead, at least when I last looked at it, it offered a choice of two sets of applications, one heavy, the other lighter, a user could choose to install.

---

### Post by DuckHook on 2014-12-16
> **vasa1 said:**
> ...when I last looked at it, it offered a choice of two sets of applications, one heavy, the other lighter, a user could choose to install.Bodhi is actually not a good distro for beginners. I know I'm stepping on a lot of toes saying this, but it's true. Bodhi is too far different from Windows that most users will just get lost and have no idea how to "make it go". It really is more of a customizer's distro: one that really persnickety power users can populate with only the exact apps that they want *and absolutely nothing more*. While it does come with two preselected packages (Bodhi calls them "bundles"), almost no Bodhi user I'm familiar with installs them. Instead, the convention is to apt-get only precisely the apps they want, and usually with the *--no-install-recommends* flag at that.

If a user is so inclined, s/he can install not only either of the bundles, but further fine-tune his/her install from a well-considered set of packages, plugins, apps and modules. I must confess to being the lazy sort who often resorts to this method over the painstaking finessing used by the gurus.

---

### Post by /ADM on 2014-12-16
I hear sometimes the same argument for OS X, it's too different I cannot use it.  Sometimes you need to give users an incentive to use it and they will learn it.

---

### Post by vasa1 on 2014-12-16
I wonder if Lubuntu couldn't be even lighter/faster. I don't know to what extent icon-bloat can slow things down but many of the Lubuntu Box theme icons are bloated, IMO. They're svg and could be scoured (the way the Humanity icon devs did for their icons). IMO, they also contain excessive detail in terms of gradients. On my system, I've replaced quite a few of the icons with ones very similar to GNOME's symbolic icons.

---

### Post by DuckHook on 2014-12-16
> **/ADM said:**
> I hear sometimes the same argument for OS X, it's too different I cannot use it.  Sometimes you need to give users an incentive to use it and they will learn it.Though I would like to agree with you (after all, I do love the distro), the comparison doesn't work because the learning curve for Bodhi is much steeper and higher than it is for OS X. We are comparing a full-fledged desktop environment (in OS X case) with a distro that stops at the window manager stage (Bodhi). Granted, it's a slick implementation of a window manager, but it's still just a window manager and requires a user to think very differently.

Of course, if a new user is intrigued nonetheless and wants to try it, I'm happy to say: "go for it." It's free to download and runs as a LiveCD/USB, so there's nothing to lose but a little time.

---

### Post by DuckHook on 2014-12-16
> **vasa1 said:**
> I wonder if Lubuntu couldn't be even lighter/faster. I don't know to what extent icon-bloat can slow things down but many of the Lubuntu Box theme icons are bloated, IMO. They're svg and could be scoured (the way the Humanity icon devs did for their icons). IMO, they also contain excessive detail in terms of gradients. On my system, I've replaced quite a few of the icons with ones very similar to GNOME's symbolic icons.I'm sure you're right, but there's a point of diminishing return. The presence of a whole DE dwarfs whatever drawbacks might arise from icon-bloat. Going back to Bodhi, I'd rather get rid of the DE and all of *its* far larger bloat, but keep the pretty icons. But then, that's just me.

If you know of any themes that use stripped down icons, but that still look cool, please do share. I'm sure that I'm not the only one around here who can appreciate a minimalist aesthetic.

---

### Post by sudodus on 2014-12-16
Try [ToriOS]("http://torios.org/"). It's still only in the development stage (alpha approaching beta), very light (much lighter than Lubuntu), based on Ubuntu 12.04 LTS, and uses JWM. The installation is very light and fast too, using the OBI installer.

---

### Post by monkeybrain20122 on 2014-12-16
> **kccv42 said:**
> Why is Lubuntu faster than Ubuntu? I seem better performance with lubuntu.

That depends on  your hadware. If you have an old or weak machine then it is faster because it is 'lighter'.  But the differences disappear on better hardware as they become relatively negligible. On my 4 year old second hand dell Latitude E5310 (core  i5 with ironlake graphic card and 4G of ram) I see no difference in performance but Ubuntu is a lot more polished, aesthetically appealing and it supports much smoother workflow. I doubt that there is much difference if you have a relatively up to date graphic card (to support 3D desktop) and > 2Gs of ram. Anyway if I have at least 1 G of ram and less than 2G I would rather use Xubuntu, I find lubuntu too stripped down and buggy (and hideously ugly out of the box :))

---

### Post by vasa1 on 2014-12-16
I remember people having problems with Lubuntu's Software Center. Looks like the "workflow" wasn't suitable.

Re. it being too stripped down, that's what apt-get, Synaptic, or the Software Center are for.

Re. buggy, I suppose other distros and software are bug-free. I'll think about that the next time I see a thread about Compiz.

Re. ugly, I'm not sure that using a computer is a Miss World competition.

For some reason, Lubuntu's existence seems to upset some people enough to get them to take time off their valuable workflow to post what they've posted before :)

---

### Post by vasa1 on 2014-12-16
> **DuckHook said:**
> ...
If you know of any themes that use stripped down icons, but that still look cool, ... a minimalist aesthetic.
Well, the stripped down part can be defined but the other two are subjective :)

---

### Post by Bucky Ball on 2014-12-16
Try the mini.iso and just install LXDE and only the apps you want/need if you're looking for speed (on young or old computers). That's what I do, but not with lxde because I don't like it. I use xfce4 instead. This is on my i3 lappy with 4Gb RAM. It flies.

---

