---
title: "When will Wayland come to Ubuntu?"
date: 2012-06-30
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by prenuk on 2012-06-30
Just wondering. It looks very cool and was wondering what latest ETA to Wayland being incorporated into Ubuntu. Even experimental. Would really like to try it out.

---

### Post by Mathor on 2012-06-30
I don't imagine it will be until after 14.04, but that's speculation.

---

### Post by Dlambert on 2012-06-30
The real question for me is: Do I want it to come? Knowing no Proprietary drivers from Nvidia will be available.

---

### Post by Dlambert on 2012-06-30
But I just read about a neat feature called xwayland: > A rather cool feature on Weston compositor is xwayland, to support  X11 native applications on Wayland. It&#8217;s a quite important feature  because gives the compatibility with the &#8220;old&#8221; windowing system, so say  you have an application written on Motif/Xt or even something more  &#8220;fancy&#8221; like a Web browser all tied with GTK2 and whatever dependency,  then you better not bother yourself re-writing it to native Wayland or  porting to a modern toolkit &#8212; it should just work seamlessly on it.  Hence, X on Wayland fits pretty well with our overall transition plan.
 The architecture behind and the mechanisms are a little tricky though, let&#8217;s take a look.
 &#8212;
 [[IMG]http://vignatti.files.wordpress.com/2012/06/xwayland.png?w=450&h=233[/IMG]]("http://vignatti.files.wordpress.com/2012/06/xwayland.png")
 Once Weston is started, it launches the **xwayland module**  which creates an X socket, adds it to the main Weston loop and waits  for X clients to be connected into. When the first client gets  connected, it triggers Weston to fork and exec one X server. Weston  continues its normal execution but unregister itself that socket.
 The X server, with the **Wayland backend** on it (xwayland), keeps listening Weston via a special **Wayland protocol interface**. Weston binds such interface and announces back the socket that X clients will be connecting to (xserver_send_listen_socket event) and the first X client that was just connected (xserver_send_client event).  The idea is to give now to X the responsibility of clients trying to be  connected, naturally. Worth to mention that this lazy initialization  method was intentionally designed in order to avoid extra lags at Weston  start up and memory overhead when X11 applications are not being used.  So the X server is started on demand, only when actually needed.
 At this point now, Weston also starts its **own X Window Manager**.  In short, the main task of it is to proxy X applications built based on  those old WM standards, such as EWMH and the jurassic ICCCM, and plumb  them into the shiny Wayland desktop shell interface. In other words, the  idea is to map different type of X windows on Wayland surfaces (xserver_set_window_id request),  and specially give some meaningful user-interface policies on X Windows  to the desktop shell, for instance making a surface to get maximized,  or say to resize/move it around.
 Other tasks the Weston X window manager performs are embed a pretty  decoration frame around windows and also make sure the client-to-client  communication such as copy and paste (selection) and eventually drag and  drop work nicely. Remark that the X protocol doesn&#8217;t define policy but  the WMs, and this is a challenge for Wayland, that does define. So the  Weston X WM has to come up with the right amount of salt to fit  perfectly the policies that were already straighten up by Wayland&#8217;s  desktop shell&#8230; hmm way too philosophical.
 All X windows created from now on will be redirected to offscreen pixmap and stored on a DRM buffer (via the **xwayland video driver**);  that&#8217;s how compositing works on Wayland. The idea is that a X client  will behave very likely as a regular Wayland client. Therefore, there&#8217;s  no protocol calls or any major task involved on xwayland and all happens  seamlessly, with the protocol &#8220;conversion&#8221; penalty close to nil.
 The architecture for input handling looks good already as well. At X  init time, it&#8217;s created fake devices, the keyboard and the pointer, and  the concept goes the other way around of window creation: it gives the  input devices capabilities from Weston to Xorg. We&#8217;re still shaping the  cursor settings, the complex logic of client and surface grabbing, among  other features, but the basics are most definitely in place already.
  So the video is there for demoing what we&#8217;ve got until now. You can  see in practice all these rather cool building blocks I mentioned. It&#8217;s  rather cool.. specially for developers; one has to have the know-how on  X11 and Wayland protocols, Xorg and Weston internals, X Window Manager  standards, etc. Lot of fun!!!
 

Source: [http://vignatti.wordpress.com/](http://vignatti.wordpress.com/)

---

### Post by alphacrucis2 on 2012-07-01
As far as I know it's been part of the Wayland plan from very early on to provide support for X11 apps as a transition mechanism. How well it will work is another question. Also we still don't know if AMD and NVIDIA will ever provide Wayland support via their proprietary drivers. I notice a thread in the community cafe by Nerdopolis' experimenting with Wayland. It already has come a long way but is still quite a way from ready for prime.

I just remembered reading a Phoronix article recently which mentioned that Ubuntu devs had uploaded a number of patches to Wayland so they must be doing something with it.

[http://www.phoronix.com/scan.php?page=news_item&px=MTEyMDE]("http://www.phoronix.com/scan.php?page=news_item&px=MTEyMDE")

---

### Post by glococo on 2012-07-01
I saw this transition mechanism and I dont like it. The OS will be full of bloatlibs and slowing the computer even more.

For me, I preffer to switch on or Off, no transition. This/that app work or not. 

In this way will be a very short migration period, full of mad people and full of migration processes.

If they release a dual mechanism,im sure that will be apps in X for ever. (2020?)


cheers

---

### Post by jbicha on 2012-07-01
I believe X on Wayland is [planned]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-q-system-compositor") to be used by default for 12.10 for those using open source 3D graphics drivers. I was told there wasn't really a performance penalty.

This new feature hasn't landed in Quantal yet.

---

### Post by Starks on 2012-07-01
That would be pretty bold considering that there are only a dozen or people in the world that have booted a Wayland environment and done anything useful with it.

---

### Post by dnewkirk on 2012-07-03
> **glococo said:**
> I saw this transition mechanism and I dont like it. The OS will be full of bloatlibs and slowing the computer even more.

For me, I preffer to switch on or Off, no transition. This/that app work or not. 

In this way will be a very short migration period, full of mad people and full of migration processes.

If they release a dual mechanism,im sure that will be apps in X for ever. (2020?)


cheers

Many of the most common applications will work, particularly for Ubuntu; the remainder will have to be ported over time. While it would be ideal to completely switch over all at once to avoid unnecessary problems, it's a little unrealistic.

---

### Post by lolpenguin on 2012-07-05
Most distros will probably stay on X for some time, as Mutter and GTK+ are not ready for wayland. Clutter is, though.

---

### Post by dino99 on 2012-07-05
get more chance soon, as xorg 1.13 will be out next week

---

### Post by cariboo on 2012-07-05
If you want to give Wayland a try now, one of our forum community members has come up with a [Wayland Live CD]("http://ubuntuforums.org/showthread.php?t=1906762")

---

### Post by Dlambert on 2012-07-05
> **cariboo907 said:**
> If you want to give Wayland a try now, one of our forum community members has come up with a [Wayland Live CD]("http://ubuntuforums.org/showthread.php?t=1906762")

+1 Looks promising...PLEASE Nvidia....Please... :confused:

---

### Post by cecilpierce on 2012-07-06
After what Linus said, I wonder  :lolflag:

---

### Post by Dlambert on 2012-07-06
> **cecilpierce said:**
> After what Linus said, I wonder  :lolflag:

Actually Nvidia is now stepping up their support because of that! :p

---

### Post by ScislaC on 2012-07-06
> **Dlambert said:**
> Actually Nvidia is now stepping up their support because of that! :p

Any citation for that? I haven't seen them indicate they'd be stepping up on anything other than PR in response.

---

### Post by cecilpierce on 2012-07-06
Yep, PR & BS !

Would be nice and fun for somrthig new to play around with.
                        :p

---

### Post by Dlambert on 2012-07-06
> **ScislaC said:**
> Any citation for that? I haven't seen them indicate they'd be stepping up on anything other than PR in response.

> Within the constraints I have, what should I and perhaps other NVIDIA employees be contributing to in the kernel? In a Google+ comment, Linus noted that we have mainly been contributing patches for Tegra SoC infra-structure details. I'm curious what other areas people might expect me/NVIDIA to contribute to. I assume the issue is mainly the lack of open support for the graphics-related parts of our HW, but perhaps there's some expectation that we'd also start helping out some core area of the kernel too? Would that kind of thing help our image even if we didn't open up our HW?
And:
Are there any new/novel ideas I could take back to NVIDIA to help persuade any kind of opening up? I'd be happy to feed anything interesting up the chain.

Source: [http://www.phoronix.com/scan.php?page=news_item&px=MTEyNTk](http://www.phoronix.com/scan.php?page=news_item&px=MTEyNTk)

Nothing new has been done as far as I know.

---

### Post by Dlambert on 2012-07-06
> While there's still more than one month until the Ubuntu 12.10 feature freeze, Canonical/Ubuntu developers continue to work towards their concept of having Wayland serve as a system compositor for this next Ubuntu Linux release due out in October, but will they make it? 

For Ubuntu 12.10 at the UDS Oakland event the developers at Canonical set out with some ambitious plans for Wayland. 

Canonical's plans involve using a Wayland-based compositor to control display outputs from boot to shutdown. Their intention with this system compositor is to provide smooth transitions during the boot process and for session switching and other operations, avoiding traditional VT switching, providing a consistent monitor layout, using the greeter as the lock screen, ensuring that locked sessions are actually secure from displaying, and showing the greeter while the session loads. 

As I wrote back in May, "For Ubuntu 12.04 LTS they tried for a Wayland preview and weren't even able to achieve that for the Precise Pangolin. As someone that's been monitoring Wayland for the past five years and the first person to publicly write about Wayland when it was still a very young and experimental project by Kristian, I just don't see this system compositor goal coming close to fruition with Ubuntu 12.10. I've been saying for a while now that it will probably not be until Ubuntu 13.04 that Wayland takes on any really usable form." 

We're now past Ubuntu 12.10 Alpha 2 and there's no integration of Wayland by default within Ubuntu "Quantal Quetzal", but the developers are still working on it. 

There remains the system compositor blueprint where the item is a "high" priority that's been "started" and followed by many individuals. The work items that are still open on this Launchpad Blueprint include talking with the kernel team about VT switching, updating LightDM, using the greeter as a lock screen, implementing an Xserver signal hook to fake VT switch for input drivers, patching XWayland to use regiular input DDX drivers, figuring out how to minimize the changes between the different boot systems, talking with QA about testing, writing a Wayland back-end for Plymouth, and documenting the display manager / system compositor interactions. There's still a lot TODO in a very short amount of time. 

The only completed tasks from this system compositor blueprint is evaluating whether to fork Wayland's Weston or provide additional functionality via a Weston plug-in and providing XWayland support for Nouveau. 

While the XWayland support for Nouveau is marked as "DONE", that support isn't yet merged to mainline and just on Wednesday there was a v2 patch by Canonical's Christopher James Halse Rogers still working on the XWayland Nouveau support. 

They're dedicated towards migrating in the direction of Wayland, but I still don't see this becoming a reality in Ubuntu 12.10. They may finally have Wayland as a technical preview, which they tried (but failed) to do for Ubuntu 12.04 LTS, except their goals probably won't be realized in full until 2013. 

Whenever the Wayland system compositor for Ubuntu does materialize, there will still be fall-backs as the AMD Catalyst and NVIDIA binary Linux graphics drivers will not work. The initial implementation also won't rely upon desktop applications running directly on the Wayland compositor but rather via XWayland until the desktop environments and key applications fully support this new display technology. 

While Ubuntu wants to be the first major distribution shipping a Wayland environment, they still aren't a main contributor to upstream Wayland/Weston. The current Ubuntu compositor work can be found in the separate RAOF/weston repository.


Source: [http://www.phoronix.com/scan.php?page=news_item&px=MTEzNDY](http://www.phoronix.com/scan.php?page=news_item&px=MTEzNDY)


So wayland is PLANNED for 12.10 :confused:

---

### Post by cecilpierce on 2012-07-07
It is been in the repo's for awhile now but just a sample of what it can do.

---

