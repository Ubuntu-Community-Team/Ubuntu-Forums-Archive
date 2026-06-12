---
title: "MicroXwin superlight alternative to X windowing system"
date: 2010-04-22
forum: The Cafe
---

### Post by sonnet on 2010-04-22
From their website:
[http://www.microxwin.com/](http://www.microxwin.com/)
*MicroXwin is binary compatible to the Xlib API. However it is neither client server nor network oriented. Graphics operations are implemented in the linux kernel via a kernel module. An open source Xlib library sends graphics commands to the kernel. There is no network overhead and no context switch from X client to X server. This makes our solution smaller and faster than traditional X Windows.*

It seems that this implementation would boost considerably the performance (they claim):
[I]An improvement of 62% for asynchronous display or 384% for synchronous display of images of a 100x100 size.
Scrolling a web page under MicroXwin is much faster and smoother.
There are only about 300 Kbytes of kernel memory in use by the kernel module. X.Org server, however, has a run-time memory usage of 12MB.
The smallest MicroXwin distribution can fit within 1 megabyte of disk space in contrast to the X.Org Server, which has a disk footprint of 1.8MB.[/I]

What I don't understand is: it seems all good and perfect, but apart from the fact that is a proprietary module, what are the big cons?
I mean if a distribution is going to use it, what would be the limitations for a Home user? (3D and 2D missing funcionality, or impossibility to use some open or closed drivers etc etc, application incompatibility?)
Is out there any distribution implementing that?

---

### Post by bornagainpenguin on 2010-05-25
/BUMP for also interested.  Saw this in an article in Linux Format magazine and wondered if there were any releases for Lucid.  Unfortunately there aren't.  :(

--bornagainpenguin

---

### Post by kevin11951 on 2010-05-25
I hope this doesnt take off.  If it does, you can wave goodbye to LTSP, and X-over-SSH tunneling.

---

### Post by gandalf2000 on 2010-07-06
I have just found this and was wondering about it.  Has anyone successfully installed this on Lucid?

---

### Post by earthpigg on 2010-07-07
> the fact that is a proprietary module

Burn it with Fire.

Heaven forbid that mainstream Linux distributions ever rely on proprietary software *just to put an image on the screen*.

---

### Post by imgx64 on 2010-07-07
> **kevin11951 said:**
> I hope this doesnt take off.  If it does, you can wave goodbye to LTSP, and X-over-SSH tunneling.

Having an alternative to X is not mutually exclusive to having X on other machines. X is simply too general, too complicated, and you can break it by changing a single line in one of the zillion config files it uses. :roll:

While MicroXwin is proprietary and thus being unattractive to most Linux users, I don't mind the general idea. A lightweight alternative to X that isn't network-capable would be much easier to develop and maintain, and faster too.

---

### Post by jwbrase on 2010-07-07
> **sonnet said:**
> From their website:
[http://www.microxwin.com/](http://www.microxwin.com/)
*MicroXwin is binary compatible to the Xlib API. However it is neither client server nor network oriented. Graphics operations are implemented in the linux kernel via a kernel module. An open source Xlib library sends graphics commands to the kernel. There is no network overhead and no context switch from X client to X server. This makes our solution smaller and faster than traditional X Windows.*

It seems that this implementation would boost considerably the performance (they claim):
[I]An improvement of 62% for asynchronous display or 384% for synchronous display of images of a 100x100 size.
Scrolling a web page under MicroXwin is much faster and smoother.
There are only about 300 Kbytes of kernel memory in use by the kernel module. X.Org server, however, has a run-time memory usage of 12MB.
The smallest MicroXwin distribution can fit within 1 megabyte of disk space in contrast to the X.Org Server, which has a disk footprint of 1.8MB.[/I]

What I don't understand is: it seems all good and perfect, but apart from the fact that is a proprietary module, what are the big cons?
I mean if a distribution is going to use it, what would be the limitations for a Home user? (3D and 2D missing funcionality, or impossibility to use some open or closed drivers etc etc, application incompatibility?)
Is out there any distribution implementing that?

Well, there's the fact that the networked client/server architecture is useful. 

Then there's the fact that they're implementing it as a kernel module, which makes it all the more likely that X going berserk will necessitate a reboot. I find X to be a bit less stable than I'd like (In fact, because of it, I'd say the whole Linux + X package is actually a bit less stable, as the desktop user sees it, than WinXP), but unlike the Windows GUI, when it crashes, you don't have to restart the whole system, just the X-Server (So that the Linux + X package is as stable or more stable, as the non-graphical application sees it, than WinXP, and takes seconds to recover from most crashes, rather than minutes). I have the feeling that with X implemented in a kernel module, the system will become really flaky.

---

### Post by RiceMonster on 2010-07-07
Even more stuff running in-kernel? I really don't know about that.

---

### Post by nrs on 2010-07-07
> **earthpigg said:**
> Burn it with Fire.

Heaven forbid that mainstream Linux distributions ever rely on proprietary software *just to put an image on the screen*.
That's simplifying it to an absurd extent. X is the foundation which all our pretty desktop environments  and window managers operate on. 

Making them dependent on a piece of software whose developers can change licensing costs, distribution terms, etc. on a whim is lunacy. 

It has some hefty technical drawbacks too. 

I very much doubt X.Org is going anywhere. It is definitely not as robust as Windows or OS X but it gets the job done and has shown an ability to evolve.

---

### Post by imgx64 on 2010-07-07
> **nrs said:**
> I very much doubt X.Org is going anywhere. It is definitely not as robust as Windows or OS X but it gets the job done and has shown an ability to evolve.

Correct me if I'm wrong, but isn't OS X's pretty interface built on top of X.Org?

---

### Post by nrs on 2010-07-07
> **imgx64 said:**
> Correct me if I'm wrong, but isn't OS X's pretty interface built on top of X.Org?
Unfortunately / Fortunately not. [http://en.wikipedia.org/wiki/Quartz_Compositor](http://en.wikipedia.org/wiki/Quartz_Compositor)

---

### Post by Helkaluin on 2010-07-07
> **nrs said:**
> Unfortunately / Fortunately not. [http://en.wikipedia.org/wiki/Quartz_Compositor](http://en.wikipedia.org/wiki/Quartz_Compositor)

Actually they do: [https://secure.wikimedia.org/wikipedia/en/wiki/X11.app](https://secure.wikimedia.org/wikipedia/en/wiki/X11.app)

---

### Post by nrs on 2010-07-07
> **Helkaluin said:**
> Actually they do: [https://secure.wikimedia.org/wikipedia/en/wiki/X11.app](https://secure.wikimedia.org/wikipedia/en/wiki/X11.app)
It's available for OS X. OS X doesn't depend on it in any way.

---

### Post by imgx64 on 2010-07-07
> **nrs said:**
> It's available for OS X. OS X doesn't depend on it in any way.

Ah, that explains it. I was sure OS X had an X server, but I didn't know it's not used for everything.

---

### Post by YeOK on 2010-07-07
Being closed source means distro's like Fedora and Debain wouldn't touch this at all, so I can't see it finding a huge following. 

I pretty sure, if mainstream Linux really wanted to migrate away from X, something like [wayland]("http://groups.google.com/group/wayland-display-server") would be the preferred choice. 

This may be a great library for smaller Linux powered devices though, maybe we'll see it on future mobile phones.

---

### Post by Starlight on 2010-07-07
Even though it's not open source, it shows that it's possible to make something that's much faster than X.org, so maybe some developers could try to make an open source clone. :)

---

### Post by Mr. Picklesworth on 2010-07-07
> **kevin11951 said:**
> I hope this doesnt take off.  If it does, you can wave goodbye to LTSP, and X-over-SSH tunneling.

First off, I'm not all that clueful on the graphics end of things, so please do correct me if I'm totally incorrect on something. (And add a grain of salt to anything I write that sounds like a statement of fact).

As much as I am a fan of ssh -X, I think we should be moving away from a network oriented graphics system *anyway*. It doesn't work perfectly and it hasn't for a good while, if ever. Graphical apps use a lot more than just X to do their jobs, and with some newer components, parts of them break when they are squeezed through SSH. (Most usually, anything that involves dbus). It &#8220;works,&#8221; but success should never be *expected* of X-over-SSH.

Of course, people could move back down the thorny, hellishly painful route where everything uses X again and that would (mostly) fix it.

The option I prefer, though, is considering that it's a lost cause *anyway* and saving a lot of time. The best platform for networked graphical applications is the web. It's built for them. It's fast, it's easy, there's caching, it's really light-weight, All The Graphics Work Happens On The Client, there are lots of powerful options for accessing it, and a web app isn't locked to X.

If an application expects to be used over a network, that application should implement its own network functionality in a way that suits it properly. (Trivial example: Transmission).

---

### Post by Crunchy the Headcrab on 2010-07-07
> **Mr. Picklesworth said:**
> 
The option I prefer, though, is considering that it's a lost cause *anyway* and saving a lot of time. The best platform for networked graphical applications is the web. It's built for them. It's fast, it's easy, there's caching, it's really light-weight, All The Graphics Work Happens On The Client, and there are options for accessing it.

If an application expects to be used over a network, that application should implement its own network functionality in a way that suits it properly. (Trivial example: Transmission).
Agreed.

---

### Post by bornagainpenguin on 2010-08-01
So, anyone have any luck in getting this to work on a Lucid Lynx machine?  According to the site (which hasn't been updated since January of this year, the only modules available for Ubuntu are for Jaunty and for Karmic.

--bornagainpenguin

---

### Post by Legendary_Bibo on 2010-08-01
I have no idea what any of this stuff means. Can someone explain to me in laymen terms what's so bad about X?

---

### Post by forrestcupp on 2010-08-01
> **earthpigg said:**
> Burn it with Fire.

Heaven forbid that mainstream Linux distributions ever rely on proprietary software *just to put an image on the screen*.

While I normally strongly disagree with people who strongly object anything proprietary, in this case, I wholeheartedly agree with this statement.

---

### Post by nerdopolis on 2010-08-01
What *IS *wrong with X? 

X forwarding is something I wish I  could have while supporting Windows boxes  (instead of resorting to  bothering the user to allow me to get in to configure or run  something)... 

Not to mention that corporations use Citrix to  forward normal apps (instead of custom made web apps, stuck with a  clunky web interface) from a server to run seamless in a desktop client.  X11 is already superior (or at least equal) to that because it already  does that native and not trying to hack around what the OS or apps were  not designed to do.

I think the more Kernel Mode Setting drivers appear, (and Gallium3d?) the more stable the X experience should be? right? 

And  if toolkits use XCB [http://xcb.freedesktop.org/](http://xcb.freedesktop.org/) instead of XLib, it  seems the 'slowness' resizing a window would improve... (can't prove it  though, there is no way to test the theory yet)

Sure X might have  a few flaws... but I don't think its good to throw away all away all  the functionality of it, and totally replace it, instead of simply  trying to improve them, because X11 can do some pretty sweet stuff!

---

### Post by Xianath on 2010-08-02
Correct me if I'm wrong, but the main objectives seem to be:
[LIST]
[*]Stability due to kernel dependencies
[*]Relying on proprietary software for functionality
[*]Lack of a network transport
[/LIST]

How do the first two differ from using DRI and binary drivers, respectively? In 15 years, the only kernel panics I've seen (short of a K6 mobo with some cracked tracks that would OOPS if the box was nudged) came from X and DRI. We are already at a stage where we can't use our computers to their full (half, in ATI's case) potential without proprietary software.

As of network transport -- come on, X11 tunneling and LTSP? Is that what "Linux for human beings" is supposed to mean? :) Besides, they obviously support the Xlib interface, I see no technical reason why they can't implement a network wrapper around it, given enough demand. To push it further, with enough support from commercial distros, it is quite possible they dual-license it for personal use. Trolltech did, and we have KDE thanks for that. Should it have never be born simply because it has a commercial background, as GNOME advocates used to preach some ten years ago?

---

### Post by nerdopolis on 2010-08-02
Reguarding X's network capabilities, yes, there are human interfaces for using remote x servers.

[http://www.google.com/imgres?imgurl=http://www.linux-tip.net/cms/images/stories/documents/freenx/knx.gif&imgrefurl=http://www.linux-tip.net/cms/content/view/206/26/1/4/&usg=__PVysQjjZuXC1hPPGXkWslaOpCUw=&h=307&w=355&sz=16&hl=en&start=74&tbnid=kLQHEtwwTicEsM:&tbnh=123&tbnw=142&prev=/images%3Fq%3Dfreenx%26um%3D1%26hl%3Den%26sa%3DN%26biw%3D1024%26bih%3D570%26tbs%3Disch:10%2C2337&um=1&itbs=1&iact=hc&vpx=433&vpy=164&dur=2545&hovh=209&hovw=241&tx=125&ty=126&ei=dSdXTLazKJCRnwer6KmWAw&page=6&ndsp=15&ved=1t:429,r:7,s:74&biw=1024&bih=570](http://www.google.com/imgres?imgurl=http://www.linux-tip.net/cms/images/stories/documents/freenx/knx.gif&imgrefurl=http://www.linux-tip.net/cms/content/view/206/26/1/4/&usg=__PVysQjjZuXC1hPPGXkWslaOpCUw=&h=307&w=355&sz=16&hl=en&start=74&tbnid=kLQHEtwwTicEsM:&tbnh=123&tbnw=142&prev=/images%3Fq%3Dfreenx%26um%3D1%26hl%3Den%26sa%3DN%26biw%3D1024%26bih%3D570%26tbs%3Disch:10%2C2337&um=1&itbs=1&iact=hc&vpx=433&vpy=164&dur=2545&hovh=209&hovw=241&tx=125&ty=126&ei=dSdXTLazKJCRnwer6KmWAw&page=6&ndsp=15&ved=1t:429,r:7,s:74&biw=1024&bih=570)

As far as this kernel mode xlib thing goes, I don't think a *core* technology should be closed source in Linux Desktops. It also should not remove good features that already competes well with what other OSes have.

---

### Post by bornagainpenguin on 2010-10-18
Looks like they've updated their demo page to be able to run on "MicroXwin on Ubuntu 10.04 with Linux 2.6.32-21-generic kernel" shortly after the last post in this thread.  (August 8th of this year, if I'm reading the file dates of the archive correctly.)  Has anyone felt brave enough to give this a try on their Lucid install?  I'd give it a try myself but right now I'm running a PAE kernel to allow my wireless to run on the netbook and am uncomfortable with the idea of having to do another reinstall now that I've got everything working so nicely.

Yeah I'm sure there is a way to fix any issues if I have them without a reinstall, but generally it is easier for me to do the reinstall than to count on getting help with stuff like this in a timely enough fashion to make it worth the headaches.

So anyone feeling brave?  :)

--bornagainpenguin

---

