---
title: "Xubuntu or Ubuntu install"
date: 2006-09-26
forum: The Cafe
---

### Post by ClarkePeters on 2006-09-26
When I was looking to make a choice between Xubuntu and Ubuntu, I found little information, although I did gleen that Xubuntu is good for outdated/smaller systems. But what about medium/larger systems? Here's my two cents on this:

First, I'm running GenuineIntell, pentiumIII, 800mhz, 256kb cache, 386mg RAM (was actually 512 on ram but I guess some of my memory died, so I'm not sure if I was running 512 or 386 at the time of my testing). Installed the operating system on a 20 gig hard drive dedicated as an operating system disk (keep my data/music/videos on a secondary hard disk or usb drive).

I read a thread a while back that suggested that Xubuntu, seeing that it runs fast on small machines compared to other Operating Systems, that it should really rock on a larger machine, i.e one that would run a full Ubuntu without troubles. However, .....

It is my experience on my computer that Xubuntu does not outperform a regular Ubuntu install, in fact, Xubuntu has quite a lag time when opening programs in my system, especially firefox and openoffice; so I'd say my Ubuntu responds faster to my demands. (abiword was Ok, a little slow at open, but to make a valid comparison, I used OpenOffice since its standard with Ubuntu). Other than the lag in opening programs, can't tell much difference (I know at the engine level maybe there's a difference, but as a user, I can't tell)  My suggestion, unless you have an outdated/smaller machine, or just want to play around with the Xubuntu install, stick with Ubuntu.

Maybe not the case for all systems, but it's true for me. 

That being said, I decided I'd had enough playing around with installs (did about 12 on a few different disks, dual boot with windows etc.. just to experiment). 
I settled on an initial Xubuntu install that I updated and then went and did an ubuntu-desktop install on top of that. I pretty much stay in Ubuntu and put up with the little bit of lag time. But I always have the choice at boot time.

I would like to know what others think--and maybe some explanations of what the true difference is, either in performance or in the desktop use (besides just saying that one is gnome and the other xfce--that's pretty obvious and doesn't mean much to a non-techie user)

---

### Post by PapaWiskas on 2006-09-26
I run Both Ubuntu and Xubuntu and Openbox on my Sony Vaio laptop. 1.4 GHZ centrino, with 1 gig of RAM.

To be honest, I just like the feel of Xubuntu over Ubuntu, it just seems more snappy.  But for the last 2 months or so, I have been using Openbox and it is even way faster for me.

Its really going to come down to choice and how you install it.  I do know I did get a pretty good performance boost for Ubuntu when I compiled a custome kernel for my laptop, some of the default service Ubuntu installs I dont need, bluetooth being one of them.

I think in the end its just going to come down to your preference.

I am not sure why Xubuntu didnt perform better for you than Ubuntu, on all the sytems I have installed "Xu" on it was just faster.

---

### Post by Kindred on 2006-09-26
Yeah, I have always found xfce snappier than gnome also on my AMD 64 3000+, mostly in a general sense rather than speed of applications opening though.  But like the above, I also prefer it over gnome and was a happy user of it until I found Openbox - which is much faster than both. 

I have to say i've never performed a Xubuntu install though, preferring to install vanilla xfce and go from there.

---

### Post by K.Mandla on 2006-09-26
Same here. I started with Xubuntu because I generally work with <1Ghz machines, and XFCE is the way to go with those. But I also use it on higher-end systems now, because it's all the faster with those.

You should see it on my dual 2.8Ghz Xeon + UltraSCSI! Yikes!

---

### Post by ClarkePeters on 2006-09-27
Seems that for me, it's the initial opening of an app that's slow. After that, they'll open a bit faster, assuming I even need to open them a second time in a session.

I'd still like to know what features help others to choose Xubuntu over Ubuntu, or vice versa. Let's give those non-techies out there some advice so that they don't have to waste time like I did searching and getting nothing. :) 

again, just saying one is gnome and the other is xfce doesn't help the not-techie.

---

### Post by mips on 2006-09-27
You could alwasy try and optimise things with stuff like prelink , preload etc.

Theres a thread here somewhere about that.

---

### Post by ClarkePeters on 2006-09-27
I'll see what I can find on that, thanks.

---

### Post by zek725 on 2006-10-11
i've already installed ubuntu on my PIII 600MHz box. how do i switch to xubuntu without the cd?

sudo apt-get remove ubuntu-desktop 

then

sudo apt-get install xubuntu-desktop ?

or just install the xubuntu-desktop?

---

### Post by Cartwheels4amile on 2006-10-12
I would just install the xubuntu-desktop. That way you still have GNOME there if you really want it.

I use GNOME on my PIII 500mhz system, with only 192mb of RAM. It's honestly not that bad.

I'm a little upset though that my second laptop's hard drive just kicked the bucket... I was planning to mess with KDE on that machine. Sigh.

---

### Post by ClarkePeters on 2006-10-15
You've probably already figured this out. But if you really want to remove Ubuntu, make sure you do the Xubuntu install first.

---

### Post by mips on 2006-10-15
Another option is to use a light WM like Fluxbox or IceWM. If I had a slower PC I would probably use fluxbox.

---

### Post by Lin-X on 2006-10-15
the September issue of LinuxFormat magazine has a dvd with a special Ubuntu distro that has all three Ubuntu, Kubuntu, and Xubuntu. I have installed it on my computer and I love it. Right now I've been playing with Kubuntu a lot; next week it will be all Xubuntu. If you want the choice, this could be a great way to go.

---

### Post by zek725 on 2006-10-15
> **ClarkePeters said:**
> You've probably already figured this out. But if you really want to remove Ubuntu, make sure you do the Xubuntu install first.

as in 

sudo apt-get install xubuntu-desktop 

then

sudo apt-get remove ubuntu-desktop ?

---

### Post by zek725 on 2006-10-15
> **mips said:**
> Another option is to use a light WM like Fluxbox or IceWM. If I had a slower PC I would probably use fluxbox.

How? Do the ubuntu repository have that?

---

### Post by NeoLithium on 2006-10-15
> **zek725 said:**
> as in 

sudo apt-get install xubuntu-desktop 

then

sudo apt-get remove ubuntu-desktop ?

You bet, that way you're not stuck fiddling around in the command line without a window manager.  xubuntu-desktop will give you the starting point to begin your customizing to make xfce nice and well suited to your own needs.

Or you can still keep both, and go between them; it's totally up to you. Should you want both, at the login screen, click on sessions and choose the WM that you would like to load for that session; and you can even choose a default if you want to keep gnome, but automatically start xfce for when you login.

---

