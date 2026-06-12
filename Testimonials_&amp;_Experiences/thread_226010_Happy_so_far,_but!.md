---
title: "Happy so far, but!"
date: 2006-07-30
forum: Testimonials &amp; Experiences
---

### Post by wayward on 2006-07-30
I am a long-time Linux user, since 1995, back in the ol' days when Slackware was all the rage.  I've used several major distributions (Slackware, SuSE, Gentoo, Debian) and I ended up with Ubuntu.  Why?  Well, as a long-time Linux tinkerer, I was happy to hit upon a distribution that strikes a good balance between user-friendliness and hackish habits.  I use GNOME because:

a) it's simple and nice to the eyes -- I prefer elegance;
b) I'm a programmer and I find GLib/GTK+/GNOME stack much more robust and wholesome than Qt;
c) GNOME seems to have some of the best designers and programmers around.

Being a hackish type, I really don't mind if I have to make something work by hand.  I even find it much more serviceable than Windows.  For instance, I've installed Ubuntu on my girlfriend's laptop.  She's doing her PhD thesis in England (far, far away) and someone would expect that she would have problems galore, her being your typical "I-just-want-it-to-work" user.  Not so.  She seldom runs into trouble (mostly when installing some software from source or adding new hardware), and when she does, I write a little bash script to collect all the information on her laptop, zip it and e-mail it to me -- she just runs the script and it does all the rest.  When I get the information, I write another script that puts things where they belong; voila.

Now for some downsides.  Linux/X/GNOME still has a long way to go before becoming a mainstream desktop.  Here are some things that frustrate me at times:

  * Some programs (Evolution anyone?) get stuck and start eating up memory.  No big deal, huh?  Just kill it?  Hardly, if you notice that your computer has started to swap extensively and your X server is getting sluggish.  Uh-oh -- better kill that darned Evolution!  Well, if you manage.  X is an application as any other and it will not get enough processor time, let alone memory, to display xterm window even if you manage to click it (and it does load up).  Switching VTs is also subject to the same problem.  Ergo, sometimes it *is* possible for one application to crash the entire system -- well, not exactly crash it, but make it unresponsive to the point where you heave a deep, deep sigh and reach for the Power button.
  * Similarly: X is only a user-space application; that means your mouse and keyboard can (and will) "skip" while the system is under heavy stress.  This happens even on my AMD64 1GB-laptop running Dapper x64.  Truth be told, I still haven't played around with the kernel to increase scheduling frequency, but my point is: GUI should be an integral part of an OS (see OS X), regardless on whether it is running in kernel-space or user-space.  Users must never see their mouse "skip" or have to wait until the cursor starts blinking again.
  * GNOME-related: menus are not responsive enough, nor do applications load up quite as fast as one would expect.  I understand that such is the price to pay if you want to have a multi-layered set of libraries, rendering engines and textual gtkrc files, but this is not a thing that can be ignored forever.

All in all, Linux is moving in some very interesting directions, but it hardly stops to reconsider itself and solidify its grip on territories already conquered.  Commercial OSes have a development cycle which starts with a set of user- and platform-side requirements and ends when those requirements are met (well, most of the OSes do).  Linux never had such a specification nor has ever moved to meet them.  That is the job of distributions.  But a distro team can not just sit and (re)write portions of kernel, X, libraries and applications to make them more streamlined and interdependency.  First, that is an overwhelming job poorly suited for a group of loosely-connected individuals; second, all of those components are fast-moving targets, impossible to "hit" and maintain a stable tightly-integrated environment throughout their separate development cycles.

However, I'm not a pessimist: while Linux and GNOME are currently perhaps at the peak of their prolific lifecycles, I hope that some time soon in the future we will witness a gradual decline in the number and scope of changes pertaining to the major components and their API/ABIs.  If we end up with a solid set of standards (dbus as a great example), at that point some big software company (Novell?) might actually step up and start patching those gaps between all the separate bits and pieces that comprise a modern Linux system.  Perhaps we won't even need a big company; but we do need a place to stop for a while, rest, look around us and decide whether we want Linux to be a fully-fledged desktop OS, or just a playground for us hackers.

---

