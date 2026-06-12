---
title: "Fast distro for my Dell 3000 desktop"
date: 2011-11-29
forum: The Cafe
---

### Post by rmcellig on 2011-11-29
I have been looking for a fast distro I can use on my computer. I only have 1gb of ram. At the moment I have Zorin 5.1 but find it a bit slow for my needs.

My needs:

I use Audacity to edit my radio shows
I need the ability to put quick launch icons on a panel or something similar that is low resource
Quick access to audio settings
Easy installation of dropbox

That's all I can think of at the moment. I thought of using puppy Linux but I find it kind of confusing to use and it looks like you are limited to using pets to het things done.

Looking forward to advice on which distros I can try out that will work for me.

Thanks!! :)

Randy

---

### Post by BC59 on 2011-11-29
My opinion is that you will not notice much of a difference on an old computer, between distros.

You need only a flavor consuming less of the video card.

In that sector everybody is in favor of Xubuntu which uses a lightweight desktop.

---

### Post by jjex22 on 2011-11-29
Hi there, I'd go Lubuntu personally - it finds a really good balance of speed and features - sounds like you don't want to skimp too much on those, but is a low footprint - around 130mb for me just after boot, 260 runnning a few chromium pages, then back to 200 once chromium is closed.

The lightest I've used for a while is crunchbang, but this isn't going to have the things you're looking for.

What's really worth remembering is that linux is linux - it's just mostly the same packages around the same selection of kernels - what most lightweight distro's do is just use a lightweight desktop enviroment like flux/openbox, icewm, jwm, xfce, lxde, e17, etc. Depending on the distro, you get a few cut resource apps - abi word instead of libre/open office for example, but they don't go too far - midori instead of chromium for example - it's lighter, but it's less stable. There are those built from scratch to be tiny - puppy etc, but again these are low on features - linux is efficent, the smaller, the less in it.

As I say, I recommend LXDE at the moment - E17 is awesome, but not quite as light on my hardware, and since this is really about ram/cpu usage to features, I think try LXDE, and I'd say first just try adding it to zorin. Not used it in a while, but go to Zorin's software centre look for lubuntu (you may get lucky) if not LXDE Desktop - install, sign out and sign in with the new Desktop Environment - no install of a new OS needed, instant perfomrance boost - on linux mint I have a massive amount of DE's - I get boared easily- to give you an idea this is the effect on ram on my machine:
KDE -420mb
MGSE -282MB
MATE -252MB
Unity - 241MB
Gnome fallback 218MB
E17 - 200MB
LXDE (Lubuntu) - 132MB
Fluxbox -118MB

all taken straight after login on the same OS yesterday - effects cost ram. hope this helps :)

Edit just updated them with current levels - kde and gnome shell's were significantly lower today - I restarted the machine before hopping in and out and didn't run anything other than htop in virtual terminal 1, signed in as root, to be fair to all.

---

### Post by snowpine on 2011-11-29
+1 to the suggestion to add LXDE or Fluxbox to your existing install, you don't need to change distros.

---

### Post by rmcellig on 2011-11-29
Good  point! Never thought of that. I guess I thought it would make my computer slower.

---

### Post by kio_http on 2011-11-30
> **rmcellig said:**
> I have been looking for a fast distro I can use on my computer. I only have 1gb of ram. At the moment I have Zorin 5.1 but find it a bit slow for my needs.

My needs:

I use Audacity to edit my radio shows
I need the ability to put quick launch icons on a panel or something similar that is low resource
Quick access to audio settings
Easy installation of dropbox

That's all I can think of at the moment. I thought of using puppy Linux but I find it kind of confusing to use and it looks like you are limited to using pets to het things done.

Looking forward to advice on which distros I can try out that will work for me.

Thanks!! :)

Randy

People won't agree on this one but here is my advice.

Kubuntu 11.10. I have used it on an old Pentium 3 with 600Mhz and 512 MB RAM and its fine.

Just install the package "kubuntu-low-fat-settings"

On my netbook 1.6 Ghz Intel Atom Kubuntu idles with a 1-2 % CPU. The current release is much lighter than Ubuntu Unity and is able to run desktop effects perfectly. Also I don't see the issue here 1 GB RAM is resonable enough. What other components does it have ... CPU etc

---

### Post by jjex22 on 2011-11-30
> People won't agree on this one but here is my advice.


Kubuntu 11.10. I have used it on an old Pentium 3 with 600Mhz and 512 MB RAM and its fine.

Just install the package "kubuntu-low-fat-settings"

On my netbook 1.6 Ghz Intel Atom Kubuntu idles with a 1-2 % CPU. _The current release is much lighter than Ubuntu Unity and is able to run desktop effects perfectly_. Also I don't see the issue here 1 GB RAM is resonable enough. What other components does it have ... CPU etc

Hi there, just want to say I'm a KDE user - use it on all my distro's, but afraid I don't agree lol! :)

I also have no problem running KDE on a netbook, however low fat settings only reduce ram usage by 22% and it's still heavier than unity at 332MB on my hardware. It is also worth pointing out that this package does impact effects as the main thing it does is turn off compositing. 

However that said if you did want to add KDE then the Low Fat package would be the way to go - can't say I'd install Kubuntu though - just download the KDE Plasma and Kubuntu Low Fat Settings packages from the software Centre, (as before why reinstall your OS?), but for the OP, this is likely to be using more resources than they are now - Zorin still uses Gnome 2 with compiz, and the 2.6 Linux kernel instead of 3 - so it's a lot more stable than Kubuntu 11.10 also.

I'll stick with my previous suggestion of LXDE - almost a third the RAM usage of KDE with KLFS. If you wanted more prettiness I'd recommend E17, though it is a PITA to set up first time.

---

### Post by kio_http on 2011-11-30
> **jjex22 said:**
> Hi there, just want to say I'm a KDE user - use it on all my distro's, but afraid I don't agree lol! :)

I also have no problem running KDE on a netbook, however low fat settings only reduce ram usage by 22% and it's still heavier than unity at 332MB on my hardware. It is also worth pointing out that this package does impact effects as the main thing it does is turn off compositing. 

However that said if you did want to add KDE then the Low Fat package would be the way to go - can't say I'd install Kubuntu though - just download the KDE Plasma and Kubuntu Low Fat Settings packages from the software Centre, (as before why reinstall your OS?), but for the OP, this is likely to be using more resources than they are now - Zorin still uses Gnome 2 with compiz, and the 2.6 Linux kernel instead of 3 - so it's a lot more stable than Kubuntu 11.10 also.

I'll stick with my previous suggestion of LXDE - almost a third the RAM usage of KDE with KLFS. If you wanted more prettiness I'd recommend E17, though it is a PITA to set up first time.

I agree, however RAM usage is not everything when it comes to performance. For me Unity (Actually the whole Ubuntu environment with GTK3 and all) has a habit of high disk usage when running. Also at times the UI can lag on my netbook.E.g Hovering on a button the visual change appears seconds later.

1GB Ram is definitely more then enough to Run KDE (or kubuntu-desktop or any KDE system). I assume the CPU of such a PC will be OK too. If the graphic card is decent enought desktop effects will work fine, if not you have to compromise on that.

Actually (provided you have enough memory), when more (not excess) is loaded into the RAM the application can run much faster than when it keeps reading from disk. This is the idea behind Windows 7 and Vista actually.

---

### Post by jjex22 on 2011-11-30
Completely agree with you kio_http -especially regarding KDE Vs Gnome 3 - it's actually the thing that lead to me giving KDE 4 another shot (I started using Linux  the year KDE 4 came out, so as I'm sure you remember it was basically the same as now, except the other way round - KDE 4 was being forced on us whilst still buggy as hell and distro's were dropping kde3 like a rock - hence I began in Gnome as a noob) 

We'll probably have a good Gnome 3 in a few releases, but that's what keeps it all interesting! 

Sorry I didn't mean any offence kio_http, was solely aiming my comments as advice for the OP - KDE has had me sold all year, but if they're having speed issues with gnome 2 & kernel 2.6, I felt it was best to sell LXDE as I just can't see KDE improving the speed anywhere near as much, (it's barely usable on my emac - 1.42ghz ppc g4(OC'd) 1gb ram & an impressive 32MB ati) and I have been really impressed by how much LXDE implementation has come on in the last 18 months - I used to use xfce for my basic environment, but these days it's always LXDE... though I miss the mouse logo!

---

### Post by wolfen69 on 2011-11-30
> **jjex22 said:**
> hi there, i'd go lubuntu personally

+1

---

### Post by digithal on 2011-12-02
> **wolfen69 said:**
> +1
This. Another vote for [**Lubuntu**]("http://lubuntu.net/").

---

### Post by wolfen69 on 2011-12-02
> **snowpine said:**
> +1 to the suggestion to add LXDE or Fluxbox to your existing install, you don't need to change distros.
+2 and turn off any unneeded services.

---

### Post by john_spiral on 2011-12-04
another vote for Lubuntu 11.10

---

