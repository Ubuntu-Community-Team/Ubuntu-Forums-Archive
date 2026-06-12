---
title: "GNOME Do/Docky split."
date: 2009-11-24
forum: The Cafe
---

### Post by Cam42 on 2009-11-24
[SIZE=1][I]Pardon me if there's a thread already, but I went 4 pages back and didn't see one.

[/I][/SIZE]
Has anyone tried the Alpha of Docky? How is it?
Will Docky work on the same hardware/distro that Do worked on?

---

### Post by Tibuda on 2009-11-24
If Gnome Do works on your system, I think Docky will work too.

This is the PPA: [https://launchpad.net/~docky-core/+archive/ppa](https://launchpad.net/~docky-core/+archive/ppa)

---

### Post by V for Vincent on 2009-11-24
Been using it for a week or so. Works very well. There are a few open bugs, but it's updated every day and I actually notice significant improvements every few days. Plus the bugs that are on launchpad don't seem to affect me - or at least, they don't bother me. I've got Do set to glass for now.

---

### Post by DJAltair on 2009-11-24
Do you have to have desktop effects/compiz enabled to get Docky to work correctly?

Whenever I don't have desktop effects enabled, I get this giant black area above the Docky tray.

I'd rather not enabled desktop effects because there's some really annoying issues with it when I'm using full screen applications (or terminals) and switching workspaces.

---

### Post by Tibuda on 2009-11-24
> **DJAltair said:**
> Do you have to have desktop effects/compiz enabled to get Docky to work correctly?

Whenever I don't have desktop effects enabled, I get this giant black area above the Docky tray.

I'd rather not enabled desktop effects because there's some really annoying issues with it when I'm using full screen applications (or terminals) and switching workspaces.

Yeah, it needs compositing. (I have tested it with Compiz, Metacity and Xcompmgr)

---

### Post by DJAltair on 2009-11-24
Bah. That's annoying.

The stupid thing is that everything else works fine (zoomed icons, etc.), it's only that black bar that mucks things up. I'm assuming that has something to do with transparencies?

---

### Post by Tipped OuT on 2009-11-24
> **DJAltair said:**
> Bah. That's annoying.

The stupid thing is that everything else works fine (zoomed icons, etc.), it's only that black bar that mucks things up. I'm assuming that has something to do with transparencies?

Just use Compiz and disable all of it's features. Problem solved.

---

### Post by DJAltair on 2009-11-24
That's... Actually a good idea.

---

### Post by Cam42 on 2009-11-24
> **DJAltair said:**
> That's... Actually a good idea.
Or use metacity compositing... that's what I've been doing.

---

### Post by Cam42 on 2009-11-24
Excuse me if this is a stupid question but...
Will Docky work on UNR? I am not familiar with UNR in the slightest, but I'm most likely getting a netbook soon, and would love to dual boot UNR+win7. Does docky work on UNR?

---

### Post by DJAltair on 2009-11-24
> **Cam42 said:**
> Or use metacity compositing... that's what I've been doing.

You sir, are a genius. Completely avoids all the garbage that is Compiz when it comes to window management. Sure some of the WM stuff is useful, but I always end up switching back to Metacity because of a few niggling annoyances.

Thanks.

---

### Post by Psumi on 2009-11-24
> **Cam42 said:**
> Or use metacity compositing... that's what I've been doing.

Metacity Compositing is extremely SLOW on my machine (only when switching workspaces). Even though it's 3 GHz dual core and a high end 1 GB nvidia card.

Also, does docky provide gnome menu access now?

---

### Post by DJAltair on 2009-11-24
It's already been working wonders for me. Everything is so much smoother than it was with Compiz, even with a bunch of stuff disabled.

Plus, my fullscreen apps don't get clobbered by the panels when I switch workspaces. I could avoid that in Compiz by setting Always On Top, but that's an annoying step I shouldn't have to do. For some reason I couldn't bind fullscreen apps to be always on top. Then again I didn't really look into it extensively.

Meh, I'm enjoying Metacity much more.

---

### Post by joey-elijah on 2009-11-25
> **Cam42 said:**
> [SIZE=1]*Pardon me if there's a thread already, but I went 4 pages back and didn't see one.*[/SIZE][B]
Has anyone tried the Alpha of Docky? How is it?[/B]
Will Docky work on the same hardware/distro that Do worked on?

Docky runs okay for an Alpha - it has a few performance issues/memory leaks now and again, but is really getting there. 

I'll be said to see Docky leave GNOME Do (i still use GNOME Do Docky atm) but it's happening for all the right reasons. 

(Shamless plug, but i interviewed Docky creator Jason Smith back when i broke this news, about why the split happened etc so if anyone's interested you can read it @ [http://www.omgubuntu.co.uk/2009/10/future-of-docky-interview-with-docky.html](http://www.omgubuntu.co.uk/2009/10/future-of-docky-interview-with-docky.html)

---

### Post by Cam42 on 2009-11-25
> (Shamless plug, but i interviewed Docky creator Jason Smith back when i broke this news, about why the split happened etc so if anyone's interested you can read it @ [http://www.omgubuntu.co.uk/2009/10/f...ith-docky.html]("http://www.omgubuntu.co.uk/2009/10/future-of-docky-interview-with-docky.html") Yeah, that's where I heard about it. (Well, after a link from Lifehacker)[]("http://www.omgubuntu.co.uk/2009/10/future-of-docky-interview-with-docky.html")

---

### Post by NCLI on 2009-11-25
> **Cam42 said:**
> Excuse me if this is a stupid question but...
Will Docky work on UNR? I am not familiar with UNR in the slightest, but I'm most likely getting a netbook soon, and would love to dual boot UNR+win7. Does docky work on UNR?

It works, yes, but not very well. Clicking on it minimizes all open windows and shows the Netbook-launcher, before doing what you asked it to. If you disable the netbook-interface, it works just like normal.

I really don't find I have a need for Docky with UNR(Soon to be UNE) though, the netbook interface works great for me.

---

### Post by Psumi on 2009-11-25
I still have not gotten an answer to my question: Does docky now have GNOME Menu as a widget or something?

---

### Post by Cam42 on 2009-11-25
> **NCLI said:**
> It works, yes, but not very well. Clicking on it minimizes all open windows and shows the Netbook-launcher, before doing what you asked it to. If you disable the netbook-interface, it works just like normal.

I really don't find I have a need for Docky with UNR(Soon to be UNE) though, the netbook interface works great for me.
UNE? Ubuntu Netbook.......Experience?
Also, is there a support forum for UNR? I see one for Ubuntu Moblin Remix, but none for Netbook Remix.

---

### Post by Psumi on 2009-11-25
> **Cam42 said:**
> UNE? Ubuntu Netbook.......Experience?
Also, is there a support forum for UNR? I see one for Ubuntu Moblin Remix, but none for Netbook Remix.

Use other support forums and choose the netbook remix prefix. x86_64 also died because of this prefix thing.

---

### Post by ElSlunko on 2009-11-25
No, no menu widget (yet). Once this thing get's that + tray icons like AWN (might want to give AWN a shot if you want those features) I'll be getting rid of panels all together!

---

### Post by Psumi on 2009-11-25
> **ElSlunko said:**
> No, no menu widget (yet). Once this thing get's that + tray icons like AWN (might want to give AWN a shot if you want those features) I'll be getting rid of panels all together!

GNOME Shell gets rid of panels, and you cannot drag menu items from GNOME Shell to a dock, hence why we need GNOME Menu for docky/etc.

---

