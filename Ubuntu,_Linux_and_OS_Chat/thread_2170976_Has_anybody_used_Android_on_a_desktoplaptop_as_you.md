---
title: "Has anybody used Android on a desktop/laptop as your primary OS?"
date: 2013-08-28
forum: Ubuntu, Linux and OS Chat
---

### Post by Roasted on 2013-08-28
Recently I was starting to wonder about a few things. I kept looking at my Nexus tablet thinking, dang, this thing is nice - but the ergonomics behind it don't really make it an all-day all-purpose device, but moreso just a supplement device to my desktop and laptop. That got me wondering if I could use it full time, so I downloaded Android 4.3 for x86 and am currently tinkering with it in a VM. In a short while I'm going to install it to a spare laptop I have and see how long I can last.

Several thoughts come to mind. First off, Exchange support in Linux is pretty bad. Evolution is the only mail client I know of that works with Exchange at all, and it does a half decent job. But the UI is somewhat meh and often times I have to xkill Evolution and restart it. Overall, it works pretty decently, but with a few snags. Meanwhile, the "email" client for Android is flipping sweet and very user friendly.

With Android being touch driven, I do wonder about keyboard shortcuts to speed up the usability of the UI. For example, it'd be nice to hit a hot key to bring up the apps menu, along with the notification bar, etc.

Hardware support is a bit of a concern, unless I want to buy a Nexus tablet with HDMI out and hook up to an HD monitor. This isn't entirely a bad idea (sounds logical to me... desktop mode for , but with a newborn at home, buying a tablet for this kind of tinkering when I have spare laptops available is kind of a stretch. I do wonder how I can get my wifi working on this one laptop, for example, as it flat out does not work...

EDIT - Looks like it's the same deal as Linux. Broadcom chip? Too bad. Intel chip? Wifi amazingness. Die Broadcom.

Those are just some initial thoughts and questions on the table for now. I have heard some users who use Android as their full time OS and quite enjoy it. This intrigues me, as I've always been the "why would I want a mobile OS on my computer" type. But hey, if it gets the job done, hard to argue with that.

---

### Post by mJayk on 2013-08-28
Have a look at the asus transformer config files there is alot of support there fore keyboard mapping.

---

### Post by Roasted on 2013-08-28
> **mJayk said:**
> Have a look at the asus transformer config files there is alot of support there fore keyboard mapping.

I haven't found anything in my searches thus far, but I'll keep it in mind.

Some thoughts:

- Multiple monitors seems to be a bust, something I'd consider to be a deal breaker.
- Multitouch with my touchpad fails to scroll, so two finger/edge scrolling is non-existent. 
- Seemingly no way to adjust the pointer sensitivity. Currently it feels sluggish, like I have to keep swiping over and over across the touchpad to move the cursor from one edge to another.

So far, this doesn't appear to be a really awesome way to do my full time computing. If these hurdles can be crossed they could substantially change my opinion, though.

---

### Post by sanderj on 2013-08-28
Have you checked [https://code.google.com/p/android-x86/downloads/list](https://code.google.com/p/android-x86/downloads/list) ? I'm trying the android-x86-4.3-20130725.iso image now in a VirtualBox VM on my Ubuntu ... it starts, I can navigate through the setup using the cursor keys and the ENTER button, but after that it seems you indeed need a touch screen; I can't use the mouse as it disappears as soon as I get in the VM window.

---

### Post by MadmanRB on 2013-08-28
> **sanderj said:**
> Have you checked [https://code.google.com/p/android-x86/downloads/list](https://code.google.com/p/android-x86/downloads/list) ? I'm trying the android-x86-4.3-20130725.iso image now in a VirtualBox VM on my Ubuntu ... it starts, I can navigate through the setup using the cursor keys and the ENTER button, but after that it seems you indeed need a touch screen; I can't use the mouse as it disappears as soon as I get in the VM window.

Turn off mouse intergration, its under the menus under machine> disable mouse integration

---

### Post by sanderj on 2013-08-28
> **MadmanRB said:**
> Turn off mouse intergration, its under the menus under machine> disable mouse integration

Wow, that works! Android-x86 in the VM is very usable with a mouse. Cool.

No network, however, as it only wants Wifi (which VirtualBox does not provide).

---

### Post by lah7 on 2013-08-28
> **Roasted said:**
> I have heard some users who use Android as their full time OS and quite enjoy it. This intrigues me, as I've always been the "why would I want a mobile OS on my computer" type. But hey, if it gets the job done, hard to argue with that.

I triple-boot my Dell Inspiron Duo netbook with Android 4.0 x86, Ubuntu 13.04 and Windows 7. Consider Windows out of the window since I never boot that bloated thing again! :D Whenever I do use it, I use Ubuntu for the 'serious' work and Android for the general 'tablet' tasks when I'm on the go. It would be awesome if it was possible to run both OSs at the same time with a simple flip (since it's a convertible) switching between the two but I've yet to see anything that offers anything like that. But no, I couldn't really use it full-time, I rely on Linux programs to get my jobs done and even so, I use my Ubuntu desktop.

Whilst Android can be good at adapting to different screen sizes, it is still designed for phone/tablet/touch use... my hardware's good for that, maybe not so on a regular desktop... if touch was really incorporated onto non-touch desktops... it might just turn out like Windows 8 did! :P

Android x86's a good project, but it really does vary depending on your hardware. On my system, older versions supports more apps, whilst newer versions work with the keyboard better, and all so far doesn't seem to like wallpaper on mine. (except live ones) :-?

The project's always evolving, so if it was your full time OS, it'll only continue to be optimised as time goes on. It really depends what you use the computers for -- for me, work (& play)

Just my thoughts on the subject.

> **sanderj said:**
> No network, however, as it only wants Wifi (which VirtualBox does not provide).
Depending on the version of Android you're running, Ethernet does work (or should)!

---

### Post by dhunt84971 on 2013-08-28
I also was dual-booting a Dell Inspirion Duo into Ubuntu 12.04 and Android x86 4.0.  This worked rather well and like others have mentioned I would find myself using the Android boot when I wanted to consume data like a tablet user and the Ubuntu boot when I wanted to actually do something (i.e. the dreaded budget).

I eventually dropped the whole tablet interface.  It didn't really work for me.  I ended up handing the small netbook off to my 12yr old daughter who still dual boots into Android 4.0 and now Ubuntu 13.04.  The only time I see her boot into Android is when she wants to play a specific Android game or when she wants to watch something on YouTube in bed (tablet style).  Most of the time it is still booted into Ubuntu.

With all that said, I just don't see how you could use a tablet to do creative work or at least anything that required a lot of typing.  IMHO the tablet is a fad.  It will eventually lose its appeal and people will return to the desktop (or laptop) as manufacturers put some of the innovative resources back into these neglected, but oh-so-useful, platforms.

I will close by saying, as far as a quality tablet user experience is concerned, Android on the Duo is pretty sweet.

---

### Post by dermot-swampgum on 2013-08-30
I was using Android X86 on an old EeePC 1000H which worked fine after I fixed up some issues wirth screen rotation.  In recent times, I have found another use for that machine and it really wasn't doing much for me running Android.  

It was really only used as a big organiser when running from meeting to meeting at work.  These days I have less meetings and a 10" tablet that does the trick.

---

### Post by SpazCool on 2013-09-10
I've been carrying an Android equipped flashdrive on my keychain for a few months now. I don't think I'd ever want to use it as my primary OS, but for an on the go option, especially when you just want to plug it in and go online, it's not too bad.

---

