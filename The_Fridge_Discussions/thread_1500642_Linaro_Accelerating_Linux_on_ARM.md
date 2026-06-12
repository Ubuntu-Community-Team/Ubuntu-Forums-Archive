---
title: "Linaro: Accelerating Linux on ARM"
date: 2010-06-03
forum: The Fridge Discussions
---

### Post by TheFridge on 2010-06-03
At our last UDS in Belgium it was notable how many people were interested in the ARM architecture. There have always been sessions at UDS about lightweight environments for the consumer electronics and embedded community, but this felt tangibly different. I saw questions being asked about ARM in server and cloud tracks, for example, and in desktop tracks. That&#8217;s new.

 So I&#8217;m very excited at [today&#8217;s announcement of Linaro]("http://www.linaro.org/"), an initiative by the [ARM partner ecosystem]("http://www.linaro.org/commercial-sponsors/") including Freescale, IBM, Samsung, ST-Ericsson and TI, to accelerate and unify the field of Linux on ARM. That is going to make it much easier for developers to target ARM generally, and build solutions that can work with the amazing diversity of ARM hardware that exists today.

 The ARM platform has historically been superspecialized and hence fragmented &#8211; multiple different ARM-based CPU&#8217;s from multiple different ARM silicon partners all behaved differently enough that one needed to develop different software for each of them. Boot loaders, toolchains, kernels, drivers and middleware are all fragmented today, and of course there&#8217;s additional fragmentation associated with Android vs mainline on ARM, but Linaro will go a long way towards cleaning this up and making it possible to deliver a consistent platform experience across all of the major ARM hardware providers.

 Having played with a prototype ARM netbook, I was amazed at how cool it felt. Even though it was just a prototype it was super-thin, and ran completely cool. It felt like a radical leap forward for the state of the art in netbooks. So I&#8217;m a fan of fanless computing, and can&#8217;t wait to get one off the shelf [IMG]http://www.markshuttleworth.com/wp-includes/images/smilies/icon_smile.gif[/IMG] 

 For product developers, the big benefit from Linaro will be reduced time to market and increased choice of hardware. If you can develop your software for &#8220;linux on ARM&#8221;, rather than a specific CPU, you can choose the right hardware for your project later in the development cycle, and reduce the time required for enablement of that hardware. Consumer electronics product development cycles should drop significantly as a result. That means that all of us get better gadgets, sooner, and great software can spread faster through the ecosystem.

 Linaro is impressively open: [www.linaro.org](www.linaro.org) has details of open engineering summits, an open wiki, mailing lists etc. The teams behind the work are committed to upstreaming their output so it will appear in all the distributions, sooner or later. The images produced will all be royalty free. And we&#8217;re working closely with the Linaro team, so the cadence of the releases will be rigorous, with a six month cycle that enables Linaro to include all work that happens in Ubuntu in each release of Linaro. There isn&#8217;t a &#8220;whole new distribution&#8221;, because a lot of the work will happen upstream, and where bits are needed, they will be derived from Ubuntu and Debian, which is quite familiar to many developers.

 The nature of the work seems to break down into four different areas.

 First, there are teams focused on enabling specific new hardware from each of the participating vendors. Over time, we&#8217;ll see real convergence in the kernel used, with work like Grant Likely&#8217;s device tree forming the fabric by which differences can be accommodated in a unified kernel. As an aside, we think we can harness the same effort in Ubuntu on other architectures as well as ARM to solve many of the thorny problems in linux audio support. 

 Second, there are teams focused on the middleware which is common to all platforms: choosing APIs and ensuring that those are properly maintained and documented so that people can deliver any different user experience with best-of-breed open tools.

 Third, there are teams focused on advancing the state of the art. For example, these teams might accelerate the evolution of the compiler technology, or the graphics subsystem, or provide new APIs for multitouch gestures, or geolocation. That work benefits the entire ecosystem equally.

 And finally, there are teams aimed at providing out of the box &#8220;heads&#8221; for different user experiences. By &#8220;head&#8221; we mean a particular user experience, which might range from the minimalist (console, for developers) to the sophisticated (like KDE for a netbook). Over time, as more partners join, the set of supported &#8220;heads&#8221; will grow &#8211; ideally in future you&#8217;ll be able to bring up a Gnome head, or a KDE head, or a Chrome OS head, or an Android head, or a MeeGo head, trivially. We already have goot precedent for this in Ubuntu with support for KDE, Gnome, LXE and server heads, so everyone&#8217;s confident this will work well.

 The diversity in the Linux ecosystem is fantastic. In part, Linaro grows that diversity: there&#8217;s a new name that folks need to be aware of and think about. But importantly, Linaro also serves to simplify and unify pieces of the ecosystem that have historically been hard to bring together. If you know Ubuntu, then you&#8217;ll find Linaro instantly familiar: we&#8217;ll share repositories to a very large extent, so things that &#8220;just work&#8221; in Ubuntu will &#8220;just work&#8221; with Linaro too.

 Originally posted on [Mark Shuttleworth&#8217;s Blog]("http://www.markshuttleworth.com/archives/427") by Mark Shuttleworth on Thursday, June 3rd, 2010

 

[More...](http://fridge.ubuntu.com/node/2055)

---

### Post by frncz on 2010-06-04
This is an interesting blog.
What I thought was of particular interest to Ubuntu adopters is the statement that Linux has problems with audio, presumably because of the non-standard software/hardware in the myriad of computers around.

Ubuntu is great, but obviously it is difficult to make all hardware combinations work out of the box, and in combination. And there are lots of add-ons that new users expect to be able to use immediately:
audio cards, video cards,tablets, wifi routers/modems, printers, scanners, cameras, phones, music players etc..

And this is besides CPUs, graphic chips, storage devices, RAID arrays, networks and BIOS.

In a way, what I am missing, is a commentary about the real-life difficulties that Ubuntu programmers are facing. what are the bottle necks? Is it a lack of interaction between Ubuntu and manufacturers?

Is there a strategy to overcome the bottle-necks?

From what I can gather, the new Ubuntu versions are responses to complaints by users, and fixes to overcome these, but is there a strategy? Linaro seems to be one direction, but perhaps limited to ARM?

---

### Post by Nick_Jinn on 2010-06-04
I am thinking about buying an Entourage Edge, which has two touch screens (a black and white e-ink that doubles as a tablet keyboard, and a LCD full color screen on the other side). I would be thrilled to do this as it would be my first real 'computer' that didnt come pre-installed with Windows....a big deal to me.

What is holding me back is worry about the range of applications that would be availble and whether I could eventually install Linux on it....It has the hardware for it, decent ARM processor and 4gb of ram (Unless they meant HD).....Would this hardware be able to run Linux? It might have special needs as its a one of a kind device.



I think its pretty awesome that we are starting to see ARM processors and Linux based operating systems sold on budget netbook like computers for the average person.....some real competition for Microsoft finally, exactly what they have been dreading.


Still, I would much prefer to see some regular Linux based operating systems shipped out on ARM based laptop like devices, perhaps running the Enlightenment desktop (Enlightenment just seems like it was made for a touch screen more than for a mouse and keyboard, whether that was the intention or not).

---

### Post by frncz on 2010-06-04
what do you think of this:
[http://chinagrabber.com/buy-cheap-wifi-3g-touch-e-book-readers-smartq-r7.aspx](http://chinagrabber.com/buy-cheap-wifi-3g-touch-e-book-readers-smartq-r7.aspx)

---

### Post by Nick_Jinn on 2010-06-04
Wow. That is exactly what I was hoping for before I was told about the edge. That one I can afford without selling the laptop.


The downside of course is the LCD screen. The whole point of an ereader is to save your eyes with the e-ink technology. This is essentially just a really cheap tablet computer. If I wanted to stare at a LCD screen I would just use my laptop or get an EEE PC that folds over into a 10 inch tablet.....or I would just use a smartphone.

There is definitely a market for these cheap PC tablets though. I just think that it would be more accurate to call it a tablet than an E-reader....its not really the bargain that it appears to be when you consider its a regular LCD screen rather than a color-e-ink one.

---

