---
title: "Idea for a distro, tell me what you think."
date: 2009-12-18
forum: The Cafe
---

### Post by murderslastcrow on 2009-12-18
Tell me if you think I'm insane.

So, I was reading about how compiz is a window manager, so you can actually use it just like openbox or e17 (of course, it requires compositing on startup, so if your driver is proprietary, this is a problem).

Soooo. I was thinking of a distro that lets you configure your video card during set up so it can have compositing enabled by default, and include some of the sexy stuff desktop Linux has to offer but isn't installed by default in Gnome or KDE (Cairo Dock, Gnome DO, screenlets, some other stuff that adds to usability), and just focus the whole OS around some of those creative ways to get things done for hardcore fans. Also, since it wouldn't be using a DE, that would save RAM by just running compiz as the window manager.

Also, for people with computers that can't do compositing, or are very old, I was thinking of getting some utilities that are similar to these, yet lightweight (wbar, kupfer, conky, etc.) so you can run it on a PC with less than 128 MB of RAM, too, but keep the same functionality/look.

It would be nice to get people who are all about sexy interfaces in, since some people think KDE is lame. It will target GTK as a toolkit.

So do you guys think this is a good idea? One of my friends with an old G3 iMac would love the lightweight version since he only has 128 MB of RAM, and it would sate his eyecandy fetish. These are the kind of people I would be targetting, people with older Macs and people wanting a lighter compiz.

---

### Post by Extract_Here on 2009-12-18
That sounds like a pretty good idea. Are you thinking of making a team to build this OS or is it just a fantasy?

---

### Post by fabounet on 2009-12-18
sounds good because Compiz standalone is already a reality, though quite a pain to set up.
If a distro could do all the work it would be helpful !

> Also, for people with computers that can't do compositing
I'd recommend to focus on a goal, not to make the next super-distro-that-everybody-would-use.
you'll have to make choice if you want to reach your goal.

---

### Post by MooPi on 2009-12-18
I would like to hear from someone that has used this method ???

---

### Post by murderslastcrow on 2009-12-18
Well, I've already made a lot of focused respins for my buddies with some basic tools, it wouldn't be that difficult. The script for hardware configuration wouldn't be all that painful to integrate. So I could just make a pretty webpage with an overview, links to download for 32-bit, 64-bit, and PowerPC (torrents with backup mirrors, of course).

I mean, I haven't been using my server or domain for much lately.

But yeah, I've been researching how to do this, and I have plenty of test machines to practice with. I have some buddies on dA who might wanna' contribute simple art like wallpapers, too.

But yeah, maybe it would be a good idea to just focus on one version. To be honest, it might be worth it to make the lightweight one and just make it as pretty as possible to show you don't need compiz to look awesome.

---

### Post by Mike'sHardLinux on 2009-12-18
Is it really possible to do all that with the same functionality/look with 128MB of RAM???? If so, wow!

Edit: Crap!! Wait, now you're saying you don't want to use Compiz???

---

### Post by abyrne on 2009-12-18
> **murderslastcrow said:**
> you don't need compiz to look awesome.

That's Debatable...
:)

---

### Post by Mike'sHardLinux on 2009-12-18
> **abyrne said:**
> That's Debatable...
:)

This!

---

### Post by MooPi on 2009-12-18
If thats the case just use Openbox, it has native compositing and runs lightweight.
I want something different though. You made me think about it and now I want it.
Here is what I'm going to do, Minimal install, add proprietary driver, add Compiz , add file manager ,display manager, reboot and see if it works. I've got a spare computer and I'm going to do it right now.

---

### Post by abyrne on 2009-12-18
> **MooPi said:**
> If thats the case just use Openbox, it has native compositing and runs lightweight.

I'm running openbox right now and I love it. However, if ur distro's just openbox w/ compositing and some apps, its basically just a tricked-out LXDE (which i am also running)

---

### Post by MooPi on 2009-12-18
No I've got just Openbox, pcmanfm ,lxpanel and scripts for panel icons.

---

### Post by MooPi on 2009-12-19
Okay, murderslastcrow, I tried what you proposed last night and It's not feasible with Ubuntu, sorta. Here is what I did. 
1) I used the minimal install CD and loaded a command line install 
2) Apt-get , xorg, gdm, pcmanfm,    Stage 2) compiz, nvidia-glx ,reboot.
3) Config nvidia with "sudo config-nvidia" apt-get various themes
4) apt-get Cairo dock , start "cairo-dock -o" 

Everything works but there are to many dependencies pulled in from gnome for Ubuntu to just use compiz as the sole windowing manager. So I'm going to wipe the drive and and install a gnome-core set-up and add compiz and cairo dock and other eye candy. Disable what I want to make sure it's a stable desktop. Some of the steps are abbreviated truncated but I'm going to assume you understand the process. Next attemp I'll document each step as to be able to convey a complete install.
I'd like to comment that this install attempt is on a very inexpensive computer. Total of $265 dollars .The graphics chip is integrated Nvidia 6100, 1 gig ram, single core AMD Athlon. So the fancy desktop environment can be had at a relatively small cost of build.

---

### Post by MooPi on 2009-12-19
Well the idea of using gnome-core was a failure. I'm not certain what the problem was but I couldn't get compiz to start. I've abandoned that idea and focused only on the the core of what would be considered eye candy. The steps were similar but changed.
1) Command Line install
2) apt-get   gdm,  xorg, compiz  / reboot
3)apt-get  nvidia-glx-185, gnome-themes, cairo-dock. Activate nvidia driver,```
 sudo nvidia-xconfig
```  reboot
4) Enable compiz, then add cairo-dock to startup applications / reboot
From that point you should have all the eye candy with the need to add your favorite applications.
Once again this is on integrated nividia graphics, one gig of ram and a single core cpu for a total cost of build at $265.  I think this is affordable to most people.

---

### Post by murderslastcrow on 2009-12-19
There are some extra configuration settings you need to take into consideration, since compiz isn't commonly used as a stand alone window manager.

[https://help.ubuntu.com/community/CompizStandalone](https://help.ubuntu.com/community/CompizStandalone)

This is the tutorial I followed.

There are many spinoffs, so I don't want to be redundant, but it's not as difficult as you think to look good with fake-transparency. Some Macs just can't do compositing whatsoever, so it isn't an option to do 'lightweight' compositing. Then again, maybe openbox has a way around this and that's why it's so successful?

Either way, I'll be making it for at least my friend's old iMac. This is what I liked about gOS's first incarnation- didn't use compositing, just had a lot of lightweight stuff. I think Wbar and a sexy white, even ivory-looking LXDE or IceWM theme would look very nice on those old computers.

I may base it off of Debian, now that I think about it. Is there really that much difference between Debian and an Ubuntu Minimal Install? With the latest kernel, does it really matter what I use as a base? Won't they all react the same speed with the same modules and WMs/libraries?

Haha, I have a little more research to do. I just hate using 2.4 kernels due to the lack of modern features.

---

### Post by earthpigg on 2009-12-20
> I may base it off of Debian, now that I think about it. Is there really that much difference between Debian and an Ubuntu Minimal Install? With the latest kernel, does it really matter what I use as a base? Won't they all react the same speed with the same modules and WMs/libraries?

1. default stuff installed
2. package manager
3. repositories

that is pretty much all that defines a distro. repositories are the only way in which ubuntu minimal is drastically different than debian.

---

### Post by MooPi on 2009-12-20
I'm constantly tinkering as I have multiple computers to test with. I didn't keep track of all the gnome dependencies that came along for the ride, but they were as few as I could get away with. Here are my results: [http://s559.photobucket.com/albums/ss36/MooPii/COMPIZ/?albumview=slideshow](http://s559.photobucket.com/albums/ss36/MooPii/COMPIZ/?albumview=slideshow)
It loads light wieght for a compositing rig and is very quick and functional. I've actually only used full compiz function once before and mostly use Openbox. My conclusion is I didn't give compiz it's due on a minimal install. I like it enough to keep it around for extended testing. My test machine is no wimp but it's the cheapest components I could get for this build. single core Athlon 2.7GHZ, 1gig ram, integrated nvidia gforce 6100 graphics. The computer is very nimble for such lightweight specs and cost ($265)

---

### Post by murderslastcrow on 2009-12-20
Brilliant previews! I think it would be cool to have a compiz setup with an xfce4 panel with xfapplet for gnome applets. Would that basically consume as much as Xfce with Compiz, or would it be much lighter?

Either way, I guess I should check- it'd be great to have some comprehensive benchmarking so I can compare it to Ubuntu/Kubuntu/Xubuntu with compiz enabled. I'll probably be doing that after Christmas and will present the results here. I'll be using Karmic since it's stable. I'll include how long it takes to bring up the desktop from GDM.

Also, Cairo-Dock can use fake transparency, without the need for a compositing manager. This would be ideal for the Macs with nVidia graphics cards that only have access to open source drivers on Power PC architecture. I know for a fact that Cairo dock is much lighter than AWN as well.

If I can get Cairo working with 128 MB of RAM and IceWM, I think I'll be just fine making two different versions of the distro. ACTUALLY, I'll just use some different startup scripts you can choose from GDM, one being Compiz, the other IceWM. That shouldn't wrap in too many dependencies, and if I include lightweight applications, we could definitely fit it onto one CD.

So, how does that sound?

---

### Post by Xbehave on 2009-12-20
> **MooPi said:**
> Everything works but there are to many dependencies pulled in from gnome for Ubuntu to just use compiz as the sole windowing manager. So I'm going to wipe the drive and and install a gnome-core set-up 
The whole point of package management is that you can just remove gnome and it's dependencies will follow
```
sudo aptitude install gnome-core && sudo aptitude remove gnome
```

---

### Post by glnerd on 2009-12-20
> **abyrne said:**
> That's Debatable...
:)
no i agree with murderlastcrow, and i think it would be an awesome idea. when do we get started?

---

### Post by murderslastcrow on 2009-12-21
Don't worry guys, I'm going to test this on two different Macs (including a much older one) to see if Cairo can run on the older models. Panther is about as far as you can advance unless you switch it up with Linux.

Of course, Kdenlive may be too heavy as a video editor, but I guess we could put in PiTiVi, JOkosher, F-Spot, and a few other programs to make up the iLife Suite. Again, I'll have to test all of this stuff to make sure it's not too heavy, and if it is I'll be picking alternatives.

After the holidays I'll have more time to put this together, and once I come to a good balance I'll just make a PPC and 32-bit ISO so we can get a torrent going. Also, the website shouldn't take more than a day to design a reasonable one. Possibly with a preview video encoded, along with a short guide on how to enable compositing for the full experience on video-accelerated computers.

It would probably be nice to have a 64-bit version, too, but I think I'll wait until later. People with 64-bit compatible processors aren't really so much in need of a compiz-WM environment.

---

### Post by murderslastcrow on 2009-12-21
P.S. I'll make the alternate install the default, since these older computers can't handle a LiveCD. The whole point is to give people with old macs a modern alternative.

---

### Post by Frak on 2009-12-22
So... how would this be *useful*.

---

### Post by murderslastcrow on 2009-12-22
Like I said- its primary appeal is to allow older Mac users to upgrade to a more modern incarnation of a unix-like system, while keeping the eye candy and improving functionality based on what OS X usually comes with.

This is my target, and that is it's use. Besides, of course, finding the best of the lightweight eyecandy that improves usability (Kupfer, Cairo/wbar, conky) and bringing it all into a nice package you can operate on older hardware. As a sort of last resort next to buying a new PC.

---

