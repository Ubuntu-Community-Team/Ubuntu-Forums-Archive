---
title: "When you try a new distro, what exactly are you comparing?"
date: 2012-06-06
forum: The Cafe
---

### Post by yeehi on 2012-06-06
Perhaps you download a lot of distros and give them a spin in VirtualBox, or maybe you use a live CD image and try it that way or even install as a dual boot on your computer.

What are you really concerned about / influenced by when you check out the new distro?

For example, your first impression might be that you like the default wallpaper on the desk top.

Then you might notice that there is no panel to click on to launch applications.

You might somehow be able to tell whether it is Gnome or KDE being used, or some other. (How do you recognize this?)

I suppose you then go on to see whether your favourite applications have been installed or are available for download on your distro.

Maybe you notice that only ext 3 is supported, no ext4...

These are just a beginners things to notice. I wonder what are your real concerns when you check out a distro.

Of course, I hope that you are concerned whether the distro is [endorsed]("http://www.gnu.org/distros/free-distros.html") by the free software foundation!

---

### Post by philinux on 2012-06-06
Moved to Cafe.

---

### Post by scouser73 on 2012-06-06
When I stepped out of using Windows and into Linux I first started with Open Solaris, then Open Suse, then to Ubuntu.

Ease of use, I don't mean how easy it is to install an O/S but package installation.

---

### Post by deadflowr on 2012-06-06
> **scouser73 said:**
> When I stepped out of using Windows and into Linux I first started with Open Solaris, then Open Suse, then to Ubuntu.

Ease of use, I don't mean how easy it is to install an O/S but package installation.

I agree with this.
When I install and try any distro, I always check and see how well the package management system works. This includes the update management. If the update manager breaks, I ditch that distro. No need to run a system that uses a bad packaging system.

---

### Post by eyeofliberty on 2012-06-06
I'm usually looking at speed, stability, and resource consumption. And then, package management/available apps, and robustness of the community around it.

---

### Post by LiamOS on 2012-06-06
One thing I find to be telling of a distribution is the installation process. I quite like to see an extremely hands-on installation method, or at least the option to do so with an 'expert install' or whatever(Graphical installers are always nice to have if you're not in the mood).

The first thing I check with a working system is always the package management, but not in the most conventional way. I like to see how functional it is, and compare that against how many problems can result from its complexity. In that regard, APT and Portage would be my top two choice; APT due entirely to its simple use and extremely rare errors, and Portage due almost entirely to its extreme adaptability, since APT isn't particularly powerful, and Portage is often a massive pain. I also quite like Pacman, but I'm a bit biased against it since I'm not a huge fan of Arch.

Comparing distros out of the box is something I don't really do anymore, unless I'm setting somebody else up, but I compare the documentation and helpfulness of the user-base.For example, Gentoo's is fantastically detailed, but was a bit daunting when I was more of a newbie than I am now. Ubuntu's is also very detailed, but it tends to be geared towards GUI use and people new to Linux; fantastic in its own way, but it becomes a bit of a drag if you like to do things without GUIs, or have screwed around with your system a lot. 

Finally, I like how check how much breakage I tend to get when I run something like:
```
# apt-get update
# pacman -Syu
# emerge --update --deep --with-bdeps=y --newuse world 
```
A big plus for Ubuntu is that there's rarely(If ever?) any breakage from that. This is also the reason I don't like Arch as much as a lot of people.

---

### Post by Hylas de Niall on 2012-06-06
1 - functionality and stability on my particular hardware
2 - pleasing themes?
3 - how many of my 'must have' apps are on the default install?
4 - how many of my 'don't want' apps are *not* on the default install?
5 - is it Debian based?

---

### Post by neu5eeCh on 2012-06-06
Package management. Package management. Package management. In my experience, Ubuntu (along with PPA's) outstrips both Fedora and Opensuse in ease of use and stability. The last time I used Opensuse (and clicked their install from here buttons) it didn't work three quarters of the time - what with missing dependencies and the like. Maybe they've improved?

If I'm just comparing different Ubuntu distributions, then it's all about the DEs and the refinements therein. I currently use Voyager (an XFCE respin). I tried running the BETA of Pinguy OS off a liveCD, but it didn't work (assume it was BETA issues).

---

### Post by vasa1 on 2012-06-06
And there's this: [http://blog.bodhizazen.net/linux/desktop-environments-ram-use/](http://blog.bodhizazen.net/linux/desktop-environments-ram-use/)

---

### Post by vasa1 on 2012-06-06
> **VTPoet said:**
> Package management. Package management. Package management. ...
Remind me of someone who went, "Developers, developers, developers" ;)

---

### Post by vasa1 on 2012-06-06
> **yeehi said:**
> Perhaps you download a lot of distros and give them a spin in VirtualBox, or maybe you use a live CD image and try it that way or even install as a dual boot on your computer.

What are you really concerned about / influenced by when you check out the new distro?
...
I don't test much at all (just the one machine, bandwidth issues, fear of breaking). But, before installing anything I read, read, read and so I'm in a position to know most things mentioned in the OP except how exactly it will run on my machine.

It's *interesting* to come across experiences of people who install/test first and then go on to comment about pretty obvious things that they quite easily could have known about before installing/testing.

---

### Post by djsroknrol on 2012-06-07
I look for "the feel" overall...the layout, the features it has, memory management and OS stability. :popcorn:

---

### Post by MadmanRB on 2012-06-07
I look at the performance, overall experience, package repositories, default apps and how far I could go with it

---

### Post by yeehi on 2012-06-07
> **vasa1 said:**
> Remind me of someone who went, "Developers, developers, developers" ;)

This really has to be the key feature of a distro - but we don't need to download the iso file to find this out; in fact, downloading the iso doesn't really tell us about the number of developers.

How can we find out how many developers are at work on a given distro? Is there a webpage somewhere that lists the number of people at work on a particular distro? By the way, I think most developers would be at work on a particular application, rather than a particular distro. Is that right? How do we know what they are doing on a particular application? It would be nice to know whether they were tweaking it for use with a particular distro.

---

### Post by black veils on 2012-06-07
in no particular order:


1.  highly configurable desktop environment (panels, plugins, themes etc)
2.  stability
3.  based on debian/ubuntu, because that is what i am familiar with, from a lot of exploration. i dont have the energy or interest to learn other package management systems.
4.  preferably thunar or nautilus file manager

i have never thought about this in a list-making way before, i am not sure if that is everything.

first impressions are not an issue for me, i am happy to setup everything the way i need/want.

Xubuntu and Bodhi Linux are the distros for me (xfce and enlightenment desktop environments).

---

### Post by zombifier25 on 2012-06-07
I'm not interested in trying out other distros anyway, since what I'm looking for is Debian/Ubuntu based, and most's core system I can replicate with my current Ubuntu.

But I do try out small, run from RAM distros though. I have a copy of Puppy Linux on my flash drive.

---

### Post by mamamia88 on 2012-06-07
How long it takes to get everything up and running the way i want.

---

### Post by Simian Man on 2012-06-07
> **yeehi said:**
> What are you really concerned about / influenced by when you check out the new distro?
Like others have said, package management is critical.  That's why I keep coming back to Fedora, no other package manager is as nice to use as yum in my opinion, though I've tried many others.

Another issue is the update and release policy.  Does the distro have set releases or is it rolling?  Does it update to new versions of programs, or does it only update for bug fixes?  The installer is also something I look for as they vary widely among distributions.

I also look for the general feel which includes the website and community.

> **yeehi said:**
> You might somehow be able to tell whether it is Gnome or KDE being used, or some other. (How do you recognize this?)
If you use both for a little bit, it is very easy to tell.  If you need to tell, open up a file browser window, and go to Help->About.  If will say Dolphin for KDE, Nautilus for Gnome, and Thunar for Xfce.

> **yeehi said:**
> Of course, I hope that you are concerned whether the distro is [hendorsed]("http://www.gnu.org/distros/free-distros.html") by the free software foundation!
Nope, I couldn't care less what they think.

---

### Post by matt_symes on 2012-06-07
IMHO, the most important thing in any distribution is the level of support available.

Forums, IRC and the help documents.

---

### Post by jonathonblake on 2012-06-07
> **yeehi said:**
> 
What are you really concerned about / influenced by when you check out the new distro?

How easy is it to install the software I use?

How many programs that I use on a daily basis, will I have to compile and install myself, if I want to stay current?  [I quit using Red Hat, when I realized that I was automatically downloading, compiling, and then installing the Linux kernel, Apache, MySQL, and Python, simply to have the most recentely released versions on my system.]

How A11Y is the distro?


jonathon

---

### Post by ads2996 on 2012-06-15
Stability, Stability!, STABILITY!

---

### Post by Mikeb85 on 2012-06-16
Speed, stability, ease of use, package management - these seem to be the most important, and what differentiate distros the most.  

For instance, right now I'm using openSUSE.  What I like most about it is YAST - an all in one tool for changing repositories, managing updates, devices, installing software, virtual machines, servers - literally any change you can make to your computer, you do through a single tool which is YAST.  It's utterly fantastic.  

Other than that SUSE uses a fairly standard KDE desktop, kind of boring, I prefer Ubuntu's Unity (might try to install it on SUSE, some people have managed to).  SUSE also seems to run programs faster than Ubuntu, seems a lot more stable, but it's also much less user friendly (getting Skype to work was a headache, although now it works flawlessly).  While I love SUSE's configurability, I occasionally miss Ubuntu's polish and ease of use.  

Here's a pic of YAST btw:

---

